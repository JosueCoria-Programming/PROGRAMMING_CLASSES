# Súper Desafíos — Profesor (Resueltos con código completo) (C++)
**Materia:** INTRODUCCIÓN A LA PROGRAMACIÓN  
**Profesor:** Josue Coria  
**Institución:** UNITEC  
**Lenguaje:** C++ (Consola)

> Aquí viene **el código completo** de ambos súper desafíos, listo para copiar a `src/main.cpp`.  
> Nombres de variables/funciones en **inglés**. README/commits pueden ir en español según empresa.

---

# Parcial 1 — Console Game Core (CÓDIGO COMPLETO)

## Qué incluye
- Loop de menú principal
- Stats (HP / Coins)
- Combate (normal / crítico)
- Tienda (compra de ítems simples)
- Curación
- Dificultad (Easy / Normal / Hard)
- Resumen final al salir
- **Sin archivos, sin structs, sin vectors**

## `src/main.cpp`
```cpp
#include <iostream>

// ---------------------------
// Constants / Config
// ---------------------------
const int MAX_HP = 100;

const int POTION_PRICE = 20;
const int POTION_HEAL = 20;

const int ARMOR_PRICE = 35;     // reduces damage by flat amount
const int ARMOR_REDUCE = 3;

const int CRIT_MULTIPLIER = 2;

// Difficulty multipliers (int math: percent style)
const int EASY_DAMAGE_PERCENT = 80;
const int NORMAL_DAMAGE_PERCENT = 100;
const int HARD_DAMAGE_PERCENT = 125;

// ---------------------------
// Utility
// ---------------------------
int clamp_int(int value, int min_value, int max_value) {
    if (value < min_value) return min_value;
    if (value > max_value) return max_value;
    return value;
}

void print_separator() {
    std::cout << "----------------------------------------\n";
}

void print_title() {
    print_separator();
    std::cout << "           CONSOLE GAME CORE\n";
    print_separator();
}

void print_stats(int hp, int coins, int has_armor, int difficulty) {
    std::cout << "HP: " << hp << "/" << MAX_HP
              << " | Coins: " << coins
              << " | Armor: " << (has_armor ? "YES" : "NO")
              << " | Difficulty: ";

    if (difficulty == 1) std::cout << "EASY";
    else if (difficulty == 2) std::cout << "NORMAL";
    else if (difficulty == 3) std::cout << "HARD";
    else std::cout << "UNKNOWN";

    std::cout << "\n";
}

void print_menu() {
    print_separator();
    std::cout << "1) Show stats\n";
    std::cout << "2) Fight\n";
    std::cout << "3) Shop\n";
    std::cout << "4) Heal (use potion if you have one)\n";
    std::cout << "5) Change difficulty\n";
    std::cout << "6) Exit\n";
    print_separator();
    std::cout << "Choose: ";
}

int damage_percent_for_difficulty(int difficulty) {
    if (difficulty == 1) return EASY_DAMAGE_PERCENT;
    if (difficulty == 2) return NORMAL_DAMAGE_PERCENT;
    return HARD_DAMAGE_PERCENT; // default hard if invalid
}

int apply_difficulty_to_damage(int raw_damage, int difficulty) {
    int percent = damage_percent_for_difficulty(difficulty);
    // Example: raw 10, hard 125 -> 12 (int math)
    int scaled = (raw_damage * percent) / 100;
    if (scaled < 1) scaled = 1;
    return scaled;
}

// ---------------------------
// Systems
// ---------------------------
void system_fight(int& hp, int& coins, int has_armor, int difficulty, int& total_hits, int& total_damage_taken) {
    print_separator();
    std::cout << "FIGHT\n";
    std::cout << "Choose attack type:\n";
    std::cout << "1) Normal hit\n";
    std::cout << "2) Critical hit (x2)\n";
    std::cout << "Choose: ";

    int attack_type = 0;
    std::cin >> attack_type;

    int base_damage = 0;
    std::cout << "Enter enemy base damage: ";
    std::cin >> base_damage;

    int final_damage = base_damage;
    if (attack_type == 2) final_damage = base_damage * CRIT_MULTIPLIER;

    final_damage = apply_difficulty_to_damage(final_damage, difficulty);

    if (has_armor) {
        final_damage -= ARMOR_REDUCE;
        if (final_damage < 1) final_damage = 1;
    }

    hp -= final_damage;
    hp = clamp_int(hp, 0, MAX_HP);

    total_hits += 1;
    total_damage_taken += final_damage;

    std::cout << "You took " << final_damage << " damage.\n";

    // Reward coins if still alive
    if (hp > 0) {
        int reward = 10;
        coins += reward;
        std::cout << "You survived the fight. +" << reward << " coins.\n";
    } else {
        std::cout << "GAME OVER (HP reached 0).\n";
    }
}

void system_shop(int& coins, int& potions, int& has_armor, int& total_spent) {
    int option = 0;
    while (option != 4) {
        print_separator();
        std::cout << "SHOP\n";
        std::cout << "Coins: " << coins << "\n";
        std::cout << "1) Buy Potion (+" << POTION_HEAL << " HP) - " << POTION_PRICE << " coins\n";
        std::cout << "2) Buy Armor (reduce damage by " << ARMOR_REDUCE << ") - " << ARMOR_PRICE << " coins\n";
        std::cout << "3) Show inventory\n";
        std::cout << "4) Back\n";
        print_separator();
        std::cout << "Choose: ";

        std::cin >> option;

        if (option == 1) {
            if (coins >= POTION_PRICE) {
                coins -= POTION_PRICE;
                potions += 1;
                total_spent += POTION_PRICE;
                std::cout << "Purchased potion. Potions: " << potions << "\n";
            } else {
                std::cout << "Not enough coins.\n";
            }
        } else if (option == 2) {
            if (has_armor) {
                std::cout << "You already have armor.\n";
            } else if (coins >= ARMOR_PRICE) {
                coins -= ARMOR_PRICE;
                has_armor = 1;
                total_spent += ARMOR_PRICE;
                std::cout << "Purchased armor.\n";
            } else {
                std::cout << "Not enough coins.\n";
            }
        } else if (option == 3) {
            std::cout << "Inventory:\n";
            std::cout << "- Potions: " << potions << "\n";
            std::cout << "- Armor  : " << (has_armor ? "YES" : "NO") << "\n";
        } else if (option == 4) {
            std::cout << "Leaving shop...\n";
        } else {
            std::cout << "Invalid option.\n";
        }
    }
}

void system_heal(int& hp, int& potions, int& total_healed) {
    print_separator();
    std::cout << "HEAL\n";

    if (potions <= 0) {
        std::cout << "You have no potions.\n";
        return;
    }

    if (hp >= MAX_HP) {
        std::cout << "HP is already full.\n";
        return;
    }

    potions -= 1;
    int before = hp;
    hp = clamp_int(hp + POTION_HEAL, 0, MAX_HP);
    int healed = hp - before;

    total_healed += healed;

    std::cout << "Used potion. +" << healed << " HP. (Potions left: " << potions << ")\n";
}

void system_change_difficulty(int& difficulty) {
    print_separator();
    std::cout << "DIFFICULTY\n";
    std::cout << "1) Easy\n";
    std::cout << "2) Normal\n";
    std::cout << "3) Hard\n";
    std::cout << "Choose: ";

    int d = 0;
    std::cin >> d;

    if (d < 1 || d > 3) {
        std::cout << "Invalid difficulty. Keeping current.\n";
        return;
    }

    difficulty = d;
    std::cout << "Difficulty updated.\n";
}

// ---------------------------
// Main
// ---------------------------
int main() {
    // Core stats
    int hp = 100;
    int coins = 30;

    // Inventory (simple)
    int potions = 1;
    int has_armor = 0;

    // Difficulty: 1 easy, 2 normal, 3 hard
    int difficulty = 2;

    // Session summary
    int total_hits = 0;
    int total_damage_taken = 0;
    int total_healed = 0;
    int total_spent = 0;

    print_title();

    int option = 0;
    while (option != 6 && hp > 0) {
        print_menu();
        std::cin >> option;

        if (option == 1) {
            print_stats(hp, coins, has_armor, difficulty);
        } else if (option == 2) {
            system_fight(hp, coins, has_armor, difficulty, total_hits, total_damage_taken);
        } else if (option == 3) {
            system_shop(coins, potions, has_armor, total_spent);
        } else if (option == 4) {
            system_heal(hp, potions, total_healed);
        } else if (option == 5) {
            system_change_difficulty(difficulty);
        } else if (option == 6) {
            std::cout << "Exiting...\n";
        } else {
            std::cout << "Invalid option.\n";
        }
    }

    print_separator();
    std::cout << "SESSION SUMMARY\n";
    std::cout << "- Final HP   : " << hp << "/" << MAX_HP << "\n";
    std::cout << "- Final Coins: " << coins << "\n";
    std::cout << "- Hits taken : " << total_hits << "\n";
    std::cout << "- Damage taken: " << total_damage_taken << "\n";
    std::cout << "- Total healed: " << total_healed << "\n";
    std::cout << "- Coins spent : " << total_spent << "\n";
    print_separator();

    return 0;
}
```

---

# Parcial 2 — Console Game Extended (CÓDIGO COMPLETO)

## Qué incluye
- `struct` para Player, Item, Quest, Enemy
- `vector` para inventario y quests
- Save / Load con archivos:
  - `player.txt`
  - `inventory.txt`
  - `quests.txt`
- Strings con `getline` para nombre y quests
- Menús: Stats / Fight / Shop / Inventory / Quests / Difficulty / Save / Load / Exit

## Formato de archivos (simple y estable)
- `player.txt`
  - name (línea completa)
  - hp
  - coins
  - difficulty
- `inventory.txt`
  - N
  - por item: name (línea completa), price, heal_amount
- `quests.txt`
  - N
  - por quest: title (línea completa), is_completed (0/1)

## `src/main.cpp`
```cpp
#include <iostream>
#include <fstream>
#include <string>
#include <vector>

// ---------------------------
// Constants
// ---------------------------
const int MAX_HP = 100;

// ---------------------------
// Data Models
// ---------------------------
struct Player {
    std::string name;
    int hp;
    int coins;
    int difficulty; // 1 easy, 2 normal, 3 hard
};

struct Item {
    std::string name;
    int price;
    int heal_amount; // 0 if not a potion
};

struct Quest {
    std::string title;
    int is_completed; // 0/1 to keep it simple
};

struct Enemy {
    std::string name;
    int hp;
    int base_damage;
};

// ---------------------------
// Utility
// ---------------------------
int clamp_int(int value, int min_value, int max_value) {
    if (value < min_value) return min_value;
    if (value > max_value) return max_value;
    return value;
}

void print_separator() {
    std::cout << "----------------------------------------\n";
}

void print_title() {
    print_separator();
    std::cout << "        CONSOLE GAME EXTENDED\n";
    print_separator();
}

int damage_percent_for_difficulty(int difficulty) {
    if (difficulty == 1) return 80;
    if (difficulty == 2) return 100;
    return 125;
}

int apply_difficulty_to_damage(int raw_damage, int difficulty) {
    int scaled = (raw_damage * damage_percent_for_difficulty(difficulty)) / 100;
    if (scaled < 1) scaled = 1;
    return scaled;
}

void safe_getline(std::string& out_line) {
    std::getline(std::cin >> std::ws, out_line);
}

// ---------------------------
// Save / Load
// ---------------------------
bool save_player(const Player& player) {
    std::ofstream out("player.txt");
    if (!out.is_open()) return false;

    out << player.name << "\n";
    out << player.hp << "\n";
    out << player.coins << "\n";
    out << player.difficulty << "\n";
    return true;
}

bool load_player(Player& player) {
    std::ifstream in("player.txt");
    if (!in.is_open()) return false;

    std::getline(in, player.name);
    in >> player.hp;
    in >> player.coins;
    in >> player.difficulty;

    player.hp = clamp_int(player.hp, 0, MAX_HP);
    if (player.difficulty < 1 || player.difficulty > 3) player.difficulty = 2;
    return true;
}

bool save_inventory(const std::vector<Item>& inventory) {
    std::ofstream out("inventory.txt");
    if (!out.is_open()) return false;

    out << (int)inventory.size() << "\n";
    for (int i = 0; i < (int)inventory.size(); i++) {
        out << inventory[i].name << "\n";
        out << inventory[i].price << "\n";
        out << inventory[i].heal_amount << "\n";
    }
    return true;
}

bool load_inventory(std::vector<Item>& inventory) {
    std::ifstream in("inventory.txt");
    if (!in.is_open()) return false;

    int n = 0;
    in >> n;
    inventory.clear();

    // consume endline after reading n
    in.ignore(1, '\n');

    for (int i = 0; i < n; i++) {
        Item it;
        std::getline(in, it.name);
        in >> it.price;
        in >> it.heal_amount;
        in.ignore(1, '\n');
        inventory.push_back(it);
    }
    return true;
}

bool save_quests(const std::vector<Quest>& quests) {
    std::ofstream out("quests.txt");
    if (!out.is_open()) return false;

    out << (int)quests.size() << "\n";
    for (int i = 0; i < (int)quests.size(); i++) {
        out << quests[i].title << "\n";
        out << quests[i].is_completed << "\n";
    }
    return true;
}

bool load_quests(std::vector<Quest>& quests) {
    std::ifstream in("quests.txt");
    if (!in.is_open()) return false;

    int n = 0;
    in >> n;
    quests.clear();

    // consume endline after reading n
    in.ignore(1, '\n');

    for (int i = 0; i < n; i++) {
        Quest q;
        std::getline(in, q.title);
        in >> q.is_completed;
        in.ignore(1, '\n');
        quests.push_back(q);
    }
    return true;
}

bool save_game(const Player& player, const std::vector<Item>& inventory, const std::vector<Quest>& quests) {
    bool ok_player = save_player(player);
    bool ok_inv = save_inventory(inventory);
    bool ok_quests = save_quests(quests);
    return ok_player && ok_inv && ok_quests;
}

bool load_game(Player& player, std::vector<Item>& inventory, std::vector<Quest>& quests) {
    bool ok_player = load_player(player);
    bool ok_inv = load_inventory(inventory);
    bool ok_quests = load_quests(quests);
    return ok_player && ok_inv && ok_quests;
}

// ---------------------------
// Systems
// ---------------------------
void print_stats(const Player& player) {
    std::cout << "Player: " << player.name
              << " | HP: " << player.hp << "/" << MAX_HP
              << " | Coins: " << player.coins
              << " | Difficulty: ";
    if (player.difficulty == 1) std::cout << "EASY";
    else if (player.difficulty == 2) std::cout << "NORMAL";
    else std::cout << "HARD";
    std::cout << "\n";
}

void change_difficulty(Player& player) {
    print_separator();
    std::cout << "DIFFICULTY\n";
    std::cout << "1) Easy\n2) Normal\n3) Hard\nChoose: ";
    int d = 0;
    std::cin >> d;
    if (d >= 1 && d <= 3) {
        player.difficulty = d;
        std::cout << "Difficulty updated.\n";
    } else {
        std::cout << "Invalid difficulty.\n";
    }
}

void list_inventory(const std::vector<Item>& inventory) {
    print_separator();
    std::cout << "INVENTORY\n";
    if (inventory.empty()) {
        std::cout << "(empty)\n";
        return;
    }
    for (int i = 0; i < (int)inventory.size(); i++) {
        std::cout << (i + 1) << ") " << inventory[i].name
                  << " | price=" << inventory[i].price
                  << " | heal=" << inventory[i].heal_amount << "\n";
    }
}

void use_heal_item(Player& player, std::vector<Item>& inventory) {
    int idx = -1;
    for (int i = 0; i < (int)inventory.size(); i++) {
        if (inventory[i].heal_amount > 0) {
            idx = i;
            break;
        }
    }

    print_separator();
    std::cout << "HEAL\n";
    if (idx == -1) {
        std::cout << "No healing items in inventory.\n";
        return;
    }
    if (player.hp >= MAX_HP) {
        std::cout << "HP already full.\n";
        return;
    }

    int before = player.hp;
    player.hp = clamp_int(player.hp + inventory[idx].heal_amount, 0, MAX_HP);
    int healed = player.hp - before;

    std::cout << "Used: " << inventory[idx].name << " (+" << healed << " HP)\n";

    // remove used item: swap with last and pop
    inventory[idx] = inventory.back();
    inventory.pop_back();
}

Enemy build_enemy_by_choice(int choice) {
    if (choice == 1) return Enemy{ "Slime", 25, 6 };
    if (choice == 2) return Enemy{ "Goblin", 40, 10 };
    return Enemy{ "Knight", 60, 14 };
}

void fight_enemy(Player& player, std::vector<Item>& inventory, int& total_fights_won) {
    if (player.hp <= 0) {
        std::cout << "You cannot fight. HP is 0.\n";
        return;
    }

    print_separator();
    std::cout << "FIGHT\n";
    std::cout << "Choose enemy:\n";
    std::cout << "1) Slime\n2) Goblin\n3) Knight\nChoose: ";
    int choice = 0;
    std::cin >> choice;
    if (choice < 1 || choice > 3) choice = 1;

    Enemy enemy = build_enemy_by_choice(choice);

    std::cout << "Enemy: " << enemy.name << " HP=" << enemy.hp << " DMG=" << enemy.base_damage << "\n";
    std::cout << "Combat is turn-based (simple).\n";

    while (player.hp > 0 && enemy.hp > 0) {
        print_separator();
        std::cout << "Player HP=" << player.hp << " | Enemy HP=" << enemy.hp << "\n";
        std::cout << "1) Attack\n2) Critical Attack\n3) Heal (use item)\nChoose: ";
        int opt = 0;
        std::cin >> opt;

        if (opt == 3) {
            use_heal_item(player, inventory);
        } else {
            int base_damage = 10;
            int damage = base_damage;
            if (opt == 2) damage = base_damage * 2;

            enemy.hp -= damage;
            if (enemy.hp < 0) enemy.hp = 0;

            std::cout << "You dealt " << damage << " damage.\n";
        }

        if (enemy.hp <= 0) break;

        int enemy_damage = apply_difficulty_to_damage(enemy.base_damage, player.difficulty);
        player.hp -= enemy_damage;
        player.hp = clamp_int(player.hp, 0, MAX_HP);
        std::cout << enemy.name << " hits you for " << enemy_damage << ".\n";
    }

    if (player.hp > 0 && enemy.hp <= 0) {
        int reward = 20;
        player.coins += reward;
        total_fights_won += 1;
        std::cout << "You won! +" << reward << " coins.\n";
    } else if (player.hp <= 0) {
        std::cout << "GAME OVER.\n";
    }
}

void shop(Player& player, std::vector<Item>& inventory, int& total_spent) {
    int option = 0;

    Item potion{ "Healing Potion", 20, 25 };
    Item mega_potion{ "Mega Potion", 45, 50 };
    Item map{ "Dungeon Map", 15, 0 };

    while (option != 5) {
        print_separator();
        std::cout << "SHOP\n";
        std::cout << "Coins: " << player.coins << "\n";
        std::cout << "1) Buy " << potion.name << " (" << potion.price << ")\n";
        std::cout << "2) Buy " << mega_potion.name << " (" << mega_potion.price << ")\n";
        std::cout << "3) Buy " << map.name << " (" << map.price << ")\n";
        std::cout << "4) View inventory\n";
        std::cout << "5) Back\n";
        print_separator();
        std::cout << "Choose: ";
        std::cin >> option;

        if (option == 1) {
            if (player.coins >= potion.price) {
                player.coins -= potion.price;
                inventory.push_back(potion);
                total_spent += potion.price;
                std::cout << "Purchased.\n";
            } else std::cout << "Not enough coins.\n";
        } else if (option == 2) {
            if (player.coins >= mega_potion.price) {
                player.coins -= mega_potion.price;
                inventory.push_back(mega_potion);
                total_spent += mega_potion.price;
                std::cout << "Purchased.\n";
            } else std::cout << "Not enough coins.\n";
        } else if (option == 3) {
            if (player.coins >= map.price) {
                player.coins -= map.price;
                inventory.push_back(map);
                total_spent += map.price;
                std::cout << "Purchased.\n";
            } else std::cout << "Not enough coins.\n";
        } else if (option == 4) {
            list_inventory(inventory);
        } else if (option == 5) {
            std::cout << "Leaving shop...\n";
        } else {
            std::cout << "Invalid option.\n";
        }
    }
}

void list_quests(const std::vector<Quest>& quests) {
    print_separator();
    std::cout << "QUESTS\n";
    if (quests.empty()) {
        std::cout << "(no quests)\n";
        return;
    }
    for (int i = 0; i < (int)quests.size(); i++) {
        std::cout << (i + 1) << ") " << quests[i].title
                  << " [" << (quests[i].is_completed ? "DONE" : "TODO") << "]\n";
    }
}

void add_quest(std::vector<Quest>& quests) {
    print_separator();
    std::cout << "ADD QUEST\n";
    std::cout << "Title: ";
    std::string title;
    safe_getline(title);

    Quest q;
    q.title = title;
    q.is_completed = 0;
    quests.push_back(q);

    std::cout << "Quest added.\n";
}

void complete_quest(std::vector<Quest>& quests, Player& player) {
    if (quests.empty()) {
        std::cout << "No quests to complete.\n";
        return;
    }
    list_quests(quests);
    std::cout << "Complete which quest (number): ";
    int idx = 0;
    std::cin >> idx;

    idx -= 1;
    if (idx < 0 || idx >= (int)quests.size()) {
        std::cout << "Invalid quest.\n";
        return;
    }

    if (quests[idx].is_completed) {
        std::cout << "Already completed.\n";
        return;
    }

    quests[idx].is_completed = 1;
    int reward = 15;
    player.coins += reward;
    std::cout << "Quest completed! +" << reward << " coins.\n";
}

void quests_menu(std::vector<Quest>& quests, Player& player) {
    int option = 0;
    while (option != 4) {
        print_separator();
        std::cout << "QUEST MENU\n";
        std::cout << "1) List quests\n";
        std::cout << "2) Add quest\n";
        std::cout << "3) Complete quest\n";
        std::cout << "4) Back\n";
        print_separator();
        std::cout << "Choose: ";
        std::cin >> option;

        if (option == 1) list_quests(quests);
        else if (option == 2) add_quest(quests);
        else if (option == 3) complete_quest(quests, player);
        else if (option == 4) std::cout << "Back...\n";
        else std::cout << "Invalid option.\n";
    }
}

void print_main_menu() {
    print_separator();
    std::cout << "1) Show stats\n";
    std::cout << "2) Fight\n";
    std::cout << "3) Shop\n";
    std::cout << "4) Inventory\n";
    std::cout << "5) Quests\n";
    std::cout << "6) Difficulty\n";
    std::cout << "7) Save game\n";
    std::cout << "8) Load game\n";
    std::cout << "9) Exit\n";
    print_separator();
    std::cout << "Choose: ";
}

// ---------------------------
// Main
// ---------------------------
int main() {
    Player player;
    player.name = "Player";
    player.hp = 100;
    player.coins = 30;
    player.difficulty = 2;

    std::vector<Item> inventory;
    std::vector<Quest> quests;

    inventory.push_back(Item{ "Healing Potion", 20, 25 });

    int total_spent = 0;
    int total_fights_won = 0;

    print_title();

    std::cout << "Enter player name: ";
    safe_getline(player.name);

    int option = 0;
    while (option != 9) {
        if (player.hp <= 0) {
            std::cout << "HP is 0. You can still Load game or Exit.\n";
        }

        print_main_menu();
        std::cin >> option;

        if (option == 1) {
            print_stats(player);
        } else if (option == 2) {
            fight_enemy(player, inventory, total_fights_won);
        } else if (option == 3) {
            shop(player, inventory, total_spent);
        } else if (option == 4) {
            list_inventory(inventory);
        } else if (option == 5) {
            quests_menu(quests, player);
        } else if (option == 6) {
            change_difficulty(player);
        } else if (option == 7) {
            bool ok = save_game(player, inventory, quests);
            std::cout << (ok ? "Saved.\n" : "Save failed.\n");
        } else if (option == 8) {
            bool ok = load_game(player, inventory, quests);
            std::cout << (ok ? "Loaded.\n" : "Load failed (missing files?).\n");
        } else if (option == 9) {
            std::cout << "Exit.\n";
        } else {
            std::cout << "Invalid option.\n";
        }
    }

    print_separator();
    std::cout << "SESSION SUMMARY\n";
    std::cout << "- Player: " << player.name << "\n";
    std::cout << "- Final HP: " << player.hp << "/" << MAX_HP << "\n";
    std::cout << "- Coins: " << player.coins << "\n";
    std::cout << "- Inventory size: " << (int)inventory.size() << "\n";
    std::cout << "- Quests: " << (int)quests.size() << "\n";
    std::cout << "- Fights won: " << total_fights_won << "\n";
    std::cout << "- Coins spent: " << total_spent << "\n";
    print_separator();

    return 0;
}
```

---

## Nota de defensa (rápida)
Durante la revisión guiada, pide que el alumno:
- Cambie el daño base del enemigo y lo pruebe
- Agregue un item nuevo en la tienda
- Explique formato de archivos (líneas y conteos)
- Muestre Save/Load funcionando (cerrar y volver a ejecutar)
