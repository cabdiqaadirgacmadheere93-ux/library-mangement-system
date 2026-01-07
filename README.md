## Nidaamka Maamulka Maktabadda (PHP + MySQL)

Nidaam fudud oo loogu talagalay maktabad jaamacadeed oo leh doorar `Admin`, `Librarian` iyo `Member`, oo lagu dhisay PHP, MySQL, HTML, CSS, Bootstrap.

### 1. Habka Rakibidda (XAMPP)
- **Tallaabo 1**: Fur `phpMyAdmin` (`http://localhost/phpmyadmin`).
- **Tallaabo 2**: Abuuro database cusub oo la yiraahdo `library_system`.
- **Tallaabo 3**: Import garee faylka `database.sql` (kala dooro oo upload).
- **Tallaabo 4**: Geli faylasha mashruuca gudaha:
  - `C:\xampp\htdocs\library-system\` (ama magac kale).
- **Tallaabo 5**: Hubi faylka `config/config.php`:
  - `DB_HOST = 'localhost'`
  - `DB_NAME = 'library_system'`
  - `DB_USER = 'root'`
  - `DB_PASS = ''` (ama haddii aad bedeshay root password, geli halkan).
- **Tallaabo 6**: Fur browser oo geli:
  - `http://localhost/library-system/public/index.php`

### 2. Abuurista Isticmaalayaasha Hore
Database-ka waxa ku yaal jadwalka `users`, balse si fudud waxaad ku dari kartaa:
- **Admin**, **Librarian** iyo **Member** adigoo isticmaalaya shaashadda `Maamulka Isticmaalayaasha` (`users.php`).
- Eray sirka waxaa lagu kaydiyaa `password_hash` iyadoo la isticmaalayo `password_hash()` ee PHP.

Tusaale ahaan, si aad u geliso admin manual:
1. Tag `phpMyAdmin` → `library_system` → `users` → `Insert`.
2. Geli:
   - `full_name`: `Maamule Guud`
   - `email`: `admin@example.com`
   - `password_hash`: isticmaal PHP si aad u hesho hash (tusaale code hoose).
   - `role_id`: `1` (admin)
   - `status`: `active`

```php
<?php
echo password_hash('123456', PASSWORD_DEFAULT);
```

Copy hash-ka oo ku dheji `password_hash` gudaha `phpMyAdmin`.

### 3. Qaab-dhismeedka Faylasha
- **config/**
  - `config.php` – dejinta database, sessions, constants (roles, FINE_PER_DAY).
  - `db.php` – isku xidhka PDO ee MySQL (prepared statements).
- **includes/**
  - `header.php` – Bootstrap, navbar, furitaanka `<body>`.
  - `footer.php` – scripts iyo xiritaanka `</body></html>`.
- **public/**
  - `index.php` – login (Somali labels).
  - `logout.php` – session destroy.
  - `dashboard.php` – stats guud.
  - `users.php` – maamulka isticmaalayaasha (Admin kaliya).
  - `books.php` – maamulka buugaagta (Admin + Librarian).
  - `issues.php` – amaah & celin, xisaabinta ganaax.
  - `fines.php` – deymaha ganaaxyada, calaamadaynta in la bixiyay.
  - `catalog.php` – aragtida buugaagta (search + filter ee Somali).
  - `reports.php` – warbixino (most borrowed, late, daily).

### 4. Amniga
- **Password hashing**: `password_hash()` iyo `password_verify()`.
- **Prepared statements (PDO)**: dhammaan SQL queries waxay isticmaalaan `->prepare()` iyo `->execute()`.
- **Sessions**: lagu maareeyay `config/config.php` (session_start), login iyo logout.
- **Role-based access**:
  - Admin: users + dhammaan maamulka.
  - Librarian: books, issues, fines, catalog, reports.
  - Member: catalog + akhrinta xogtiisa.

### 5. Qaybaha Ugu Muhiimsan (Sharax Kooban)
- **Maamulka Buugaagta**:
  - Ciwaan buug oo **kaliya Somali ah** (`title_somali`).
  - Qoraa Somali ah (`author_somali`).
  - Qeybo Somali ah (`categories`).
  - Wadarta iyo nuqullada la heli karo.
  - Raadin: by Somali title, filter by category + status.
- **Amaah & Celin**:
  - Marka buug la amaahiyo: `available_copies` waa laga jaraa `1`.
  - Marka la soo celiyo: `available_copies` waa lagu daraa `1`.
  - Haddii la soo celiyo ka dib `due_date`, waxaa si toos ah loo abuuraa ganaax (`fines`) iyadoo la adeegsanayo `FINE_PER_DAY`.
- **Ganaax**:
  - Lagu kaydiyaa table `fines` oo leh `amount`, `is_paid`.
  - Librarian/Admin ayaa calaamadin kara in la bixiyay.

### 6. Dukumiintiga Mashruuca (Outline)
Waxaad ka qori kartaa report-ka final year project-kaaga adigoo adeegsanaya:

- **Hordhac**: Sharax waxa uu yahay nidaamka maamulka maktabad jaamacadeed iyo muhiimaddiisa.
- **Problem Statement**: Dhibaatooyinka nidaamka buug-gacmeedka (paper-based) – luminta buugaagta, diiwaan aan dhamaystirnayn, iwm.
- **Ujeeddooyinka**:
  - In la fududeeyo maamulka buugaagta.
  - In la helo diiwaan sax ah oo buuxda oo amaah iyo celin ah.
  - In la maareeyo ganaaxyada iyo isticmaalayaasha.
- **System Analysis**:
  - Noocyada isticmaalayaasha (Admin, Librarian, Member).
  - Functional requirements (login, book management, issue/return, fines, reports).
  - Non-functional (amni, fudayd isticmaal, waxqabad).
- **System Design**:
  - Use case diagrams (login, issue, return, manage books).
  - Architecture: 3-layer (presentation – PHP views, logic – PHP code, data – MySQL).
- **Database Design**:
  - ER Diagram: `users`, `roles`, `books`, `categories`, `book_issues`, `fines`, `logs`.
  - Sharax xiriirrada 1–N (role → users, category → books, book → issues, issue → fines).
- **Implementation**:
  - Faahfaahin kooban oo ku saabsan faylasha muhiimka ah (`index.php`, `dashboard.php`, `books.php`, iwm.).
  - Tusaalooyin yar oo code ah (login, issue book, calculate fine).
- **Testing**:
  - Tijaabooyin: login sax/khalad, amaah buug, soo celin wakhti sax ah, soo celin daahsan, warbixinno.
- **Gunaanad**:
  - Sida nidaamku u xalliyo dhibaatooyinkii la sheegay.
  - Fursadaha mustaqbalka (barcode, email notifications, iwm.).


