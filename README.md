# PccBay

PccBay is a PHP/MySQL web app branded as "The eBay for PCC". It serves a marketplace-style experience with item listings, user sessions, and supporting content pages.

**Project layout**
- `PccBay/`: Web root (Apache docroot) with PHP entry points and assets.
- `PccBay/MasterPages/`: Shared templates (head, header, footer, menus).
- `PccBay/includes/`: Core PHP helpers, CSS/JS, plugins, JSON, and SQL.
- `PccBay/includes/sql/PccBay.sql`: Database schema and seed data.
- `PccBay/images/`: Image assets.
- `gitFtpPush.sh`: Git-FTP deployment script.
- ` gitFtpInit.sh`: Git-FTP init script (note the leading space in the filename).
- `Domain.md`: Notes the test domain.

**Key entry points**
- `PccBay/index.php`: Main feed and app shell.
- `PccBay/item.php`: Item detail page (requires login).
- `PccBay/faq.php`, `PccBay/downloads.php`, `PccBay/privacypolicy.php`: Content pages.
- `PccBay/404.php`: Custom error page.

**Requirements**
- PHP with `mysqli` enabled.
- MySQL/MariaDB.
- Apache with `mod_rewrite` and `AllowOverride All` (uses `PccBay/.htaccess`).

**Local setup**
1. Point your web server docroot to `PccBay/`.
2. Ensure `mod_rewrite` is enabled and `.htaccess` files are honored.
3. Create a local database and import the schema:
```bash
mysql -u root -p -e "CREATE DATABASE PccBay;"
mysql -u root -p PccBay < PccBay/includes/sql/PccBay.sql
```
4. Review `PccBay/includes/php/_db-config.php` and adjust DB credentials for your environment.
5. Use a local host name that resolves to `127.0.0.1` (for example `localhost` or `pccbay.localhost`) so the local DB branch is used in `_db-config.php`.

**Configuration notes**
- `PccBay/MasterPages/overhead.php` switches behavior based on `HTTP_HOST` for local/test/production and defines `DOCUMENT_ROOT_EXT`.
- `PccBay/includes/php/_db-config.php` currently includes credentials and app secrets. Replace these with your own values for local or production use.

**Deployment**
- FTP deployment uses `git-ftp`. See `gitftp.howto.txt` and the scripts:
  - `gitFtpPush.sh`
  - ` gitFtpInit.sh` (leading space in filename)

**License**
- No license is specified. Add one if you plan to distribute or reuse the code.
