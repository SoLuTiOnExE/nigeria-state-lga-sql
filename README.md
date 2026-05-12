# 🇳🇬 Nigeria State & LGA List — SQL · JSON · CSV · XLSX · TXT

A clean, structured, and complete dataset of all **36 Nigerian States + FCT (Abuja)** and their corresponding **Local Government Areas (LGAs)** — ready to plug into any project.

---

## 📦 What's Inside

```
├── files/
│   ├── states.sql       # All 37 states (36 + FCT) INSERT statements
│   ├── lgas.sql         # All LGAs with state_id foreign keys
│   ├── StateSeeder.php  # Laravel seeder for states
│   └── LgaSeeder.php    # Laravel seeder for LGAs
├── index.html           # Interactive browser-based explorer & exporter
├── README.md
└── LICENSE
```

---

## 🗄️ Database Schema

### `states` table
```sql
CREATE TABLE `states` (
  `id`   INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `name` VARCHAR(100) NOT NULL,
  PRIMARY KEY (`id`)
);
```

### `lgas` table
```sql
CREATE TABLE `lgas` (
  `id`       INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `state_id` INT UNSIGNED NOT NULL,
  `name`     VARCHAR(150) NOT NULL,
  PRIMARY KEY (`id`),
  FOREIGN KEY (`state_id`) REFERENCES `states`(`id`) ON DELETE CASCADE
);
```

---

## 🚀 Usage

### Option 1 — Direct SQL Import

```bash
mysql -u root -p your_database < files/states.sql
mysql -u root -p your_database < files/lgas.sql
```

### Option 2 — Interactive Explorer (No install needed)

Open `index.html` in any modern browser, or visit the live version:

**🌐 Live Explorer:** [View Interactive Explorer](https://solutionexe.github.io/nigeria-state-lga-sql/)

You can:
- Browse all states and their LGAs
- Filter states by name
- Export selected state or all data as:
  - `.xlsx` (Excel)
  - `.csv`
  - `.json`
  - `.txt`

### Option 3 — Laravel Seeder Classes (Recommended)

Copy the seeder files to your Laravel project:

```
database/
└── seeders/
    ├── StateSeeder.php
    └── LgaSeeder.php
```

Register them in `database/seeders/DatabaseSeeder.php`:

```php
public function run(): void
{
    $this->call([
        StateSeeder::class,
        LgaSeeder::class,
    ]);
}
```

Then run:

```bash
php artisan db:seed
```

**Alternative:** Direct SQL import in Laravel:

```php
DB::unprepared(file_get_contents(database_path('files/states.sql')));
DB::unprepared(file_get_contents(database_path('files/lgas.sql')));
```

---

### 📌 Best Practice Note

- **Direct SQL** (`.sql` files) → Fast, raw database insert
- **Seeder Classes** → Laravel-friendly, recommended for maintainability and version control

---

## 📊 Data Summary

| Entity | Count |
|--------|-------|
| States | 37 (36 + FCT) |
| LGAs   | 774 |

---

## 🌍 Use Cases

- Address/location forms in Nigerian web & mobile apps
- E-commerce shipping & delivery zone management
- Government & civic tech platforms
- Academic research and data analysis
- Laravel, Django, Node.js, or any backend framework

---

## 🛠️ Built With

- Raw SQL — no ORM dependency
- Vanilla HTML/CSS/JS explorer (zero dependencies for browsing)
- SheetJS (CDN, for Excel export only — optional)

---

## 🤝 Contributing

Found an LGA spelling issue or missing entry? PRs are welcome!

1. Fork the repo
2. Create your branch: `git checkout -b fix/lga-name`
3. Commit your changes: `git commit -m 'fix: correct LGA name in Rivers State'`
4. Push: `git push origin fix/lga-name`
5. Open a Pull Request

---

## 👤 Author

**Fasanya Ayomide Joshua** — [@SoLuTiOnExE](https://github.com/SoLuTiOnExE)

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](./LICENSE) file for details.

---

> If this helped your project, a ⭐ on GitHub goes a long way!
