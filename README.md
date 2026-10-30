# 🚀 DevSuite Pro

<div align="center">

### The Ultimate Next-Generation Local Development Environment & Database Studio for Windows

**DevSuite Pro** is a modern, high-performance, and fully portable all-in-one local development suite engineered specifically for **Windows 10 & 11 (64-bit)**. It delivers a native desktop experience with 13+ integrated services, sub-100ms multi-version switching, a multi-engine database client, sandboxed local email testing, automatic local wildcard DNS, self-healing port conflict resolution, and background auto-updating.

[![Platform](https://img.shields.io/badge/Platform-Windows%2010%20%7C%2011%20(x64)-0a84ff?style=for-the-badge&logo=windows&logoColor=white)](#system-requirements)
[![Release](https://img.shields.io/badge/Download-Windows%20Installer%20(.exe)-0078D4?style=for-the-badge&logo=windows11&logoColor=white)](https://github.com/arsalbytes/devsuite-pro-releases/releases/latest)
[![Architecture](https://img.shields.io/badge/Architecture-Zero--Copy%20NTFS%20Junctions-blueviolet?style=for-the-badge)](#1-sub-100ms-multi-version-runtime-management)
[![Auto--Update](https://img.shields.io/badge/Auto--Update-Silent%20Atomic%20Swapping-success?style=for-the-badge)](#14-silent-background-auto-updater)
[![License](https://img.shields.io/badge/License-Freeware-orange?style=for-the-badge)](#license)

[Download .exe](#-download--installation) • [Key Features](#-complete-features-guide) • [Services & Matrix](#-integrated-stack--service-matrix) • [Database Studio](#6-native-multi-engine-database-explorer) • [Quick Connect (.env)](#-framework-quick-connect-examples) • [Documentation Guides](#-comprehensive-documentation--guides)

</div>

---

## 💡 What is DevSuite Pro?

Traditional local web development on Windows has forced developers to compromise: either wrestle with heavy virtual container systems (Docker Desktop consuming 4GB+ RAM at idle, slow file I/O, complex WSL2 setups) or rely on outdated legacy stacks (XAMPP, Laragon, WAMP) that lack modern services, break during port conflicts, and require manual configuration edits.

**DevSuite Pro provides a unified, zero-compromise solution:**
- **Native Windows Speed**: Runs directly on bare-metal Win32 APIs with **0% idle CPU usage** and minimal memory footprint.
- **Zero Configuration Friction**: Automatic wildcard DNS (`*.devsuite`), automatic trusted SSL padlocks, and self-healing port negotiation.
- **100% Portable**: Install to `C:`, `D:`, `E:`, or carry your entire development stack on a high-speed portable SSD.
- **Self-Updating Executable**: Distributed as a standalone Windows executable (`.exe`) that silently receives updates directly from GitHub Releases.

---

## 📥 Download & Installation

DevSuite Pro is distributed as a pre-compiled, optimized Windows 64-bit executable. No compilation, compiler setup, or source-code builds are needed.

### 1. Download Options
Head to the [Official GitHub Releases](https://github.com/arsalbytes/devsuite-pro-releases/releases/latest) and download:
- **`DevSuite-Pro-Setup.exe`** — The standard Windows installer (registers shortcuts and installs cleanly).
- **`DevSuite-Pro-Portable.zip`** — The portable edition (extract anywhere and run immediately).

### 2. First Launch & Setup
1. Launch **DevSuite Pro**.
2. DevSuite Pro will auto-detect your stack components. If you installed your bundle to a custom location, select the directory containing your runtimes.
3. DevSuite Pro automatically injects all runtime binaries (`php`, `node`, `python`, `composer`, `mysql`, `psql`, `redis-cli`, `mongod`, `minio`) directly into your current Windows session environment so they work everywhere instantly.

### 3. Silent Background Updates
DevSuite Pro features a built-in silent background updater. When a new version is released on GitHub:
- The executable automatically detects the update and downloads the binary delta in the background.
- It validates the SHA-256 cryptographic checksum.
- It stages the binary using atomic self-updating (`minio/selfupdate`).
- A minimal **`[ ↺ Restart ]`** indicator appears cleanly in the titlebar.
- Clicking restart gracefully reboots the application into the latest version with zero manual re-installation.

---

## 🧰 Integrated Stack & Service Matrix

DevSuite Pro orchestrates and monitors 13+ modern developer services out of the box:

| Service | Category | Default Port | Auto-Fallback Ports | Default Credentials | Management GUI / Tool |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Apache HTTPD** | Web Server | `80` (HTTP)<br>`443` (HTTPS) | `8080`, `8081`<br>`8443`, `9443` | — | VirtualHosts, SSL Engine, `.htaccess` |
| **PHP** | Runtime | Per Apache / CLI | — | — | Version Manager, `php.ini` Editor, Xdebug 3 |
| **Node.js** | Runtime | Per Project / CLI | — | — | Multi-Version Manager (`npm`, `npx`, `yarn`, `pnpm`, `bun`) |
| **Python** | Runtime | Per Project / CLI | — | — | Isolated Embeddable Python + `pip` & `Scripts` |
| **Composer** | Dependency Tool | CLI | — | — | Pre-configured Windows batch wrapper |
| **MariaDB** | SQL Database | `3306` | `3308`, `3309` | User: `root`<br>Pass: *(none)* | Native DB Explorer & Schema Designer |
| **MySQL** | SQL Database | `3307` | `3308`, `3310` | User: `root`<br>Pass: *(none)* | Native DB Explorer & User Account Manager |
| **PostgreSQL** | Relational DB | `5432` | `5433`, `5434` | User: `postgres`<br>Pass: *(none)* | Native PostgreSQL DB Studio & Table Editor |
| **MongoDB** | NoSQL Database | `27017` | `27018`, `27019` | User: *(none)*<br>Auth: Disabled (Dev) | Native Document Browser, Indexes & Shell |
| **Redis** | In-Memory Cache | `6379` | `6380`, `6381` | Pass: *(none)* | `redis-cli`, Native Log Streaming |
| **RabbitMQ** | Message Broker | `5672` (AMQP)<br>`15672` (HTTP) | `5673`, `5674` | User: `guest`<br>Pass: `guest` | Web Dashboard: `http://localhost:15672` |
| **Meilisearch** | Search Engine | `7700` | `7701`, `7702` | Master Key:<br>`devsuite-master-key` | Dashboard: `http://localhost:7700` |
| **MinIO** | S3 Object Store | `9000` (S3 API)<br>`9001` (Console) | `9002`, `9004`<br>`9003`, `9005` | User: `devsuiteadmin`<br>Pass: `devsuitepassword` | Web Console: `http://localhost:9001` |
| **DevMail** | Sandboxed SMTP | `1025` (SMTP) | `1026`, `1027` | User: `devsuite`<br>Pass: *(any)* | Built-in Split-Pane GUI & Email Reader |
| **Local DNS** | Name Resolver | `53` (UDP) | — | — | Resolves `*.devsuite`, `*.test`, `*.local` |

---

## 🔑 Default Credentials & Quick Reference

Use these credentials when setting up local environment variables (`.env`) or connecting third-party tools:

```text
├── MariaDB:        Host: 127.0.0.1  | Port: 3306  | User: root            | Pass: (empty)
├── MySQL:          Host: 127.0.0.1  | Port: 3307  | User: root            | Pass: (empty)
├── PostgreSQL:     Host: 127.0.0.1  | Port: 5432  | User: postgres        | Pass: (empty)
├── MongoDB:        Host: 127.0.0.1  | Port: 27017 | URI:  mongodb://127.0.0.1:27017
├── Redis:          Host: 127.0.0.1  | Port: 6379  | Pass: (none)
├── RabbitMQ:       Host: 127.0.0.1  | Port: 5672  | User: guest           | Pass: guest (Web: 15672)
├── Meilisearch:    Host: 127.0.0.1  | Port: 7700  | Key:  devsuite-master-key
├── MinIO S3:       Host: 127.0.0.1  | Port: 9000  | User: devsuiteadmin   | Pass: devsuitepassword (Console: 9001)
├── DevMail SMTP:   Host: 127.0.0.1  | Port: 1025  | User: devsuite        | Pass: (any)
└── Local DNS:      Host: 127.0.0.1  | Port: 53    | Domains: *.devsuite, *.test, *.local -> 127.0.0.1
```

---

## 🌟 Complete Features Guide

Every feature in DevSuite Pro is engineered for maximum developer velocity and zero maintenance overhead:

### 1. 🔀 Sub-100ms Multi-Version Runtime Management
- **NTFS Zero-Copy Junctions**: DevSuite Pro does not waste disk space or time copying large folders. It links versions instantaneously using Windows NTFS directory junctions.
- **Upstream Version Discovery**: Scrapes official upstream servers in real time (`windows.php.net`, `nodejs.org`, Python embeddable distributions, etc.) to list all available versions.
- **1-Click Download & Extraction**: Downloads standalone runtimes with live progress indicators and extracts them directly into `<stackPath>/<bundle>_versions/`.
- **System PATH Synchronization**: Automatically registers active binary directories into your Windows User Registry (`HKCU\Environment`) and broadcasts a `WM_SETTINGCHANGE` message so all open terminal sessions, IDEs, and PowerShell windows recognize newly active runtimes without a PC reboot.

### 2. 🎯 Per-Project Isolated PHP Runtime
- **Mix & Match Legacy and Modern Projects**: Run a legacy project requiring **PHP 7.4** right alongside a modern app requiring **PHP 8.3** or **PHP 8.4** simultaneously.
- **Automated Apache FastCGI Aliases**: DevSuite Pro writes project-specific `ScriptAlias` and `Action` directives into `httpd-vhosts.conf`, assigning each virtual host its own dedicated `php-cgi.exe` instance.

### 3. 🌐 Local Wildcard DNS (`*.devsuite`) & 1-Click Adapter Setup
- **Zero Hosts File Editing**: Stop opening Notepad as Administrator to edit `C:\Windows\System32\drivers\etc\hosts`.
- **Embedded DNS Server**: Listens on `127.0.0.1:53` (UDP) and immediately resolves any domain ending in `.devsuite`, `.test`, or `.local` directly to `127.0.0.1`.
- **Upstream Forwarding**: Standard external domains (like `google.com` or `packagist.org`) are smoothly forwarded to upstream Cloudflare DNS (`1.1.1.1:53`).
- **Automated Network Adapter DNS**: Sets `127.0.0.1` as your active network adapter's primary DNS server with a single click.

### 4. 🔒 Automated SSL Engine & Windows Root CA Trust
- **Local Certificate Authority (CA)**: Automatically generates a persistent OpenSSL Root CA stored in `<stackPath>/ssl/`.
- **Wildcard SAN Certificates**: Creates SSL certificates featuring Subject Alternative Names covering `localhost`, `127.0.0.1`, `*.devsuite`, `*.test`, and `*.local`.
- **Windows Trust Store Auto-Install**: Adds the Root CA to Windows Trusted Root Certification Authorities (`certutil -addstore -f "ROOT" ...`). Chrome, Edge, Brave, and Firefox show a genuine green padlock with zero SSL warnings.

### 5. 🩺 Self-Healing Port Collision Resolution
- **Proactive Conflict Detection**: Checks whether ports 80, 443, 3306, 3307, 5432, 27017, 7700, or 9000 are occupied by third-party software (such as Skype, VMware, or Windows IIS).
- **Automated Fallback Negotiation**: If a port is blocked, DevSuite Pro automatically reserves the next available port from its fallback pool (e.g. `80 -> 8080`, `443 -> 8443`, `3306 -> 3308`).
- **Automatic Configuration File Rewriting**: Updates `httpd.conf`, `httpd-ssl.conf`, `my.ini`, `mongod.cfg`, `rabbitmq.conf`, `postgresql.conf`, and `minio.env` automatically with zero manual editing required.
- **Port Manager Dashboard**: Dedicated visual page to inspect all active ports, test port statuses, and reset all services back to default ports.

### 6. 🗄️ Native Multi-Engine Database Explorer
A complete, high-performance database management studio built directly into the desktop UI:

#### Relational Databases (MySQL, MariaDB, PostgreSQL)
- **Interactive Data Grid**: Virtualized high-speed table browsing with inline cell editing, multi-row selection, sorting, pagination, and instant row deletion.
- **Visual Table Schema Designer**: Add/edit columns, configure data types, character sets, collations, default values, auto-increment, and primary keys with a real-time SQL DDL preview modal.
- **Multi-Tab SQL Console**: Execute raw queries, view execution timers in milliseconds, inspect error output, and export query result sets to CSV or JSON.
- **Multi-File Bulk Import**: Drag-and-drop multiple `.sql` or `.sql.gz` dump files. Features individual progress percentage bars, background queuing, and cancellation.
- **User & Privileges Management**: Create database users, define allowed host patterns (`%`, `localhost`), grant granular privileges, and modify passwords.
- **Automated Daily Backups**: Configure scheduled daily SQL backups with custom execution time, database multi-selection, automated cleanup of old dumps, and missed-backup recovery alerts on startup.

#### Document Store (MongoDB)
- **Document Browser**: Syntax-highlighted JSON viewer with expandable BSON trees, complex JSON filter queries, and sort/skip/limit pagination.
- **Document CRUD**: Insert new JSON documents, perform inline updates, and delete documents individually or in bulk by `_id`.
- **Collection Management**: Create collections, rename collections, clone collections, wipe documents, and drop collections.
- **Index Studio**: Inspect all collection indexes, create custom indexes (with `unique` and `sparse` flags), and drop indexes.
- **Collection Stats & URI Generator**: View collection storage size, index count, and generate copy-paste connection strings (`mongodb://127.0.0.1:27017/<dbname>`).
- **Raw Command Runner**: Run native JSON MongoDB database commands directly from the UI.

### 7. 📬 DevMail — Sandboxed Local Email Testing
- **Local SMTP Server**: Listens on `127.0.0.1:1025` using RFC-compliant Go SMTP.
- **Zero Leak Guarantee**: Catches every outbound email from your local web applications; test emails will never accidentally reach real customer inboxes.
- **Split-Pane Inbox**: Browse caught emails with unread badges, sender, recipient, subject, and timestamp.
- **Sandboxed HTML Rendering**: Safely previews responsive HTML transactional emails inside a sandboxed iframe without executing remote JavaScript.
- **Inspection Tabs**: Inspect plain-text fallbacks, MIME structures, raw RFC822 headers, and download email attachments.

### 8. ☁️ Cloudflare 1-Click Public Tunnels & Mobile Testing
- **Instant Public URLs**: Automatically provisions `cloudflared` to expose any local project or Apache virtual host over a secure `https://*.trycloudflare.com` tunnel.
- **Zero Port Forwarding**: Works seamlessly behind NATs, firewalls, and mobile hotspots without opening router ports.
- **Mobile QR Code Modal**: Scan the generated QR code with your smartphone camera to immediately preview your website on physical mobile devices over local Wi-Fi or public tunnels.

### 9. ⏰ Native Background Cron Task Scheduler
- **Job Types**: Supports Raw CLI Commands, Script Files (`.bat`, `.cmd`, `.ps1`, `.php`, `.py`, `.js`), and HTTP Webhooks (GET / POST).
- **Flexible Scheduling**: Standard 5-field cron syntax (`* * * * *`) or 1-click presets (Every minute, Every 5 minutes, Hourly, Daily at midnight, Weekly).
- **Per-Job Runtime Environment**: Specify the exact PHP, Node.js, or Python version needed for each task.
- **Execution Safeguards**: Overlap prevention locks, customizable execution timeouts, fail notifications, manual "Run Now" triggers, and persistent execution log history with exit codes and stdout/stderr output.

### 10. 🐞 1-Click Xdebug 3 Integration
- **Automatic Environment Detection**: Detects active PHP version and architecture (Thread Safe vs Non-Thread Safe).
- **Official Mirror Download**: Automatically fetches the exact matching `php_xdebug.dll` from `xdebug.org`.
- **Automated Configuration**: Injects `zend_extension`, `xdebug.mode = debug,develop`, and `xdebug.client_port = 9003` into `php.ini`.
- **IDE Ready**: Pre-configured for VS Code (`PHP Debug` extension) and PhpStorm with a 1-click toggle button.

### 11. 📁 Smart Project Manager & Framework Auto-Detection
- **Intelligent Framework Detection**: Select a folder and DevSuite Pro instantly detects:
  - Frameworks: **Laravel**, **WordPress**, **React**, **Next.js**, **Vue**, **Nuxt**, **Svelte**, **SvelteKit**, or **Standard PHP**.
  - Package Managers: **npm**, **pnpm**, **yarn**, or **bun**.
  - Dev Scripts: Automatically identifies `npm run dev`, `pnpm dev`, `php artisan serve`, etc.
  - Environment Parsing: Automatically parses `.env` to retrieve `DB_DATABASE` and `APP_NAME`.
  - PHP Requirements: Reads `composer.json` to suggest matching PHP runtimes.
- **Custom Project Groups**: Organize projects into custom categories (e.g. Clients, Personal, Work, APIs).
- **Drag-and-Drop Ordering**: Reorder projects easily with instant state persistence.
- **Direct IDE Launchers**: 1-click button to open projects in VS Code, Cursor, PhpStorm, Sublime Text, WebStorm, or Windows Explorer.
- **Live Clickable Links**: Active projects transform into clickable links that launch in your default browser.

### 12. 💻 Integrated Terminal & Real-Time Logs
- **Multi-Tab Process Viewer**: View live stdout and stderr output for all active projects and background stack processes.
- **Live Log Streaming**: Real-time log broadcasting with auto-scroll and ANSI color rendering.
- **Deep Process Tree Kill**: Stopping a project terminates all child processes (Vite watchers, Node workers, PHP servers) without leaving zombie processes.
- **Direct Log File Access**: 1-click shortcuts to open Apache access logs, Apache error logs, PHP error logs, MariaDB/MySQL logs, and Redis logs.

### 13. 📝 Developer Productivity Tools
- **Developer Scratchpad (Notes)**: Built-in note-taking workspace with instant search, pinned cards, copy-to-clipboard, timestamps, and markdown formatting.
- **Session Productivity Timer**: Track daily development hours and coding sessions with start/pause/stop timers.
- **Cryptographic Hash Studio**: Client-side hashing utility supporting MD5, SHA-1, SHA-256, and bcrypt for rapid password generation and verification.

### 14. 🔄 Silent Background Auto-Updater
- **Zero Disruptions**: Operates quietly in the background without intrusive popups or setup wizards.
- **GitHub Releases Integration**: Queries official release feeds (`arsalbytes/devsuite-pro-releases`) for new executable builds.
- **Atomic Binary Replacement**: Uses `minio/selfupdate` to stage the update cleanly while the current application is active.
- **Minimal Restart Pill**: A subtle `[ ↺ Restart ]` button appears in the titlebar. Clicking it gracefully closes background services, releases file locks, and relaunches the updated executable.
- **UAC Elevation Support**: If installed in protected Windows folders (e.g. `C:\Program Files`), the updater smoothly handles privilege elevation.

### 15. 🎨 Windows 11 Native Mica UI & Zero-WMI Optimization
- **Mica & Acrylic Translucency**: Native Windows 11 Desktop Window Manager (DWM) glass materials with subtle borders.
- **Dark, Light & System Themes**: Full appearance customization with automatic system theme synchronization.
- **Frameless Modern Titlebar**: Custom draggable header with integrated window controls and status pills.
- **System Tray Integration**: Minimize DevSuite Pro to the Windows System Tray to keep services running quietly in the background.
- **Zero-WMI Win32 Architecture**: Replaces heavy `tasklist.exe` and WMI queries with direct Win32 API calls (`Toolhelp32Snapshot`). Results in **0% CPU usage at idle**!

### 16. ☁️ Portability & Cloud Sync
- **Completely Portable**: Runs cleanly from any drive letter or USB drive without hardcoded absolute paths.
- **Arsal Bytes Cloud Sync**: Link your account to backup and restore project lists, custom groups, and developer notes across multiple machines.
- **Local JSON Export / Import**: Easily export your entire configuration to a `settings.json` file.

---

## 📂 Portable Directory Architecture

DevSuite Pro maintains a clean, modular structure on your system:

```text
E:\DevSuite\  (or C:\DevSuite\)
├── apache/                    # Active Apache HTTPD binaries & conf/ssl
│   └── conf/extra/            # httpd-vhosts.conf (auto-generated)
├── php/                       # Active PHP runtime (NTFS Junction)
│   └── php.ini                # Active PHP configuration file
├── php_versions/              # Downloaded PHP version archives
│   ├── php-7.4.33/            # Isolated PHP 7.4 build
│   ├── php-8.2.27/            # Isolated PHP 8.2 build
│   └── php-8.3.16/            # Isolated PHP 8.3 build
├── node/                      # Active Node.js runtime (NTFS Junction)
├── node_versions/             # Downloaded Node.js releases
├── python/                    # Active Embeddable Python runtime
├── composer/                  # Composer CLI binary & batch wrappers
├── mariadb/                   # Active MariaDB database engine
├── mysql/                     # Active MySQL database engine
├── postgresql/                # Active PostgreSQL binaries
├── mongodb/                   # Active MongoDB server binaries
├── redis/                     # Redis cache server
├── rabbitmq/                  # RabbitMQ broker & isolated Erlang OTP
├── meilisearch/               # Meilisearch binary & config.toml
├── minio/                     # MinIO S3 binary & minio.env
├── ssl/                       # Persistent Root CA and wildcard certificates
├── data/                      # Centralized persistent database storage
│   ├── mariadb/               # MariaDB table files
│   ├── mysql/                 # MySQL table files
│   ├── postgresql/            # PostgreSQL cluster data directory
│   ├── mongodb/               # MongoDB collection data files
│   ├── meilisearch/           # Meilisearch indexes
│   └── minio/                 # Local S3 storage buckets
└── projects/                  # Default web root directory for web apps
```

### User Configuration Directory (`%APPDATA%\DevSuitePro`)
- `%APPDATA%\DevSuitePro\settings.json`: Configuration settings, projects list, notes, and cloud sync status.
- `%APPDATA%\DevSuitePro\cron\`: Cron job configurations and stdout/stderr execution log files.
- `%APPDATA%\DevSuitePro\logs\`: Main application and service operational logs.
- `%APPDATA%\DevSuitePro\pids\`: Process tracking records for graceful shutdown management.

---

## ⚡ Framework Quick-Connect Examples

Connect your favorite web frameworks to DevSuite Pro's integrated services in seconds:

### 1. Laravel (`.env`)
```env
APP_NAME=MyProject
APP_URL=http://myproject.devsuite

# Database (MariaDB / MySQL)
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=myproject_db
DB_USERNAME=root
DB_PASSWORD=

# Cache & Queues (Redis)
CACHE_STORE=redis
QUEUE_CONNECTION=redis
REDIS_HOST=127.0.0.1
REDIS_PORT=6379

# Local Email Testing (DevMail)
MAIL_MAILER=smtp
MAIL_HOST=127.0.0.1
MAIL_PORT=1025
MAIL_USERNAME=devsuite
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS="test@myproject.devsuite"

# Local S3 File Storage (MinIO)
AWS_ACCESS_KEY_ID=devsuiteadmin
AWS_SECRET_ACCESS_KEY=devsuitepassword
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=local-uploads
AWS_ENDPOINT=http://127.0.0.1:9000
AWS_USE_PATH_STYLE_ENDPOINT=true

# Full-Text Search (Meilisearch)
SCOUT_DRIVER=meilisearch
MEILISEARCH_HOST=http://127.0.0.1:7700
MEILISEARCH_KEY=devsuite-master-key
```

### 2. Node.js / Express
```javascript
// Database Connection (MongoDB)
const mongoose = require('mongoose');
mongoose.connect('mongodb://127.0.0.1:27017/my_app');

// Local Email Sending (DevMail via Nodemailer)
const nodemailer = require('nodemailer');
const transporter = nodemailer.createTransport({
    host: '127.0.0.1',
    port: 1025,
    secure: false,
    auth: { user: 'devsuite', pass: 'any' }
});
```

### 3. Python / Django (`settings.py`)
```python
# Database Connection (PostgreSQL)
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'my_django_db',
        'USER': 'postgres',
        'PASSWORD': '',
        'HOST': '127.0.0.1',
        'PORT': '5432',
    }
}

# Local Email Backend (DevMail)
EMAIL_HOST = '127.0.0.1'
EMAIL_PORT = 1025
EMAIL_HOST_USER = 'devsuite'
EMAIL_HOST_PASSWORD = ''
EMAIL_USE_TLS = False
```

---

## 📖 Comprehensive Documentation & Guides

Detailed guides with code snippets, configuration tricks, and operational steps are available in the [guide/](guide/) directory:

| Guide | Description |
| :--- | :--- |
| 🗄️ **[MongoDB Guide](guide/mongodb-guide.md)** | Connection strings, GUI explorer, collection cloning, index optimization, and Mongoose integration. |
| 🐘 **[PostgreSQL Guide](guide/postgresql-guide.md)** | Cluster initialization, `psql` usage, relational schema design, and Laravel/Node.js connections. |
| 🪣 **[MinIO Local S3 Guide](guide/minio-guide.md)** | S3 credentials, AWS SDK integration, local bucket management, and Laravel Filesystem configuration. |
| 🔍 **[Meilisearch Guide](guide/meilisearch-guide.md)** | Master keys, search index configuration, typo tolerance, and Laravel Scout integration. |
| 📬 **[DevMail Testing Guide](guide/devmail-local-testing.md)** | Local SMTP setup, `.env` configurations, MIME header analysis, and sandboxed HTML previewing. |
| ⏰ **[Cron Jobs Guide](guide/cron-jobs-guide.md)** | 5-field cron syntax, script runners, webhook pings, overlap locks, and execution logging. |
| 🔀 **[Multi-Version Guide](guide/multi_version_management.md)** | Upstream downloading, NTFS junction mechanics, project version overrides, and CLI path sync. |
| 📁 **[Project Management Guide](guide/project_management.md)** | Custom project grouping, terminal auto-run scripts, drag-and-drop ordering, and editor shortcuts. |
| 🔒 **[SSL Certificates Guide](guide/ssl-certificates.md)** | OpenSSL Root CA trust, SAN wildcard domains, Apache HTTPS virtual hosts, and browser verification. |
| 💻 **[Terminal & Logs Guide](guide/terminal-and-logs-guide.md)** | Multi-tab live process logs, stdout streaming, PID tracking, and log file locations. |
| 🐞 **[Xdebug 3 Guide](guide/xdebug-guide.md)** | One-click installation, VS Code `launch.json` setup, PhpStorm listening, and profiling modes. |
| ⏱️ **[Session Timer Guide](guide/session_timer.md)** | Productivity time tracker, session history, and development workflow logging. |

---

## 🩺 Troubleshooting & FAQ

<details>
<summary><b>Port 80 or 443 is busy. Will Apache fail to start?</b></summary>
<br>
No! DevSuite Pro includes a self-healing port collision engine. If port 80 or 443 is blocked by Windows IIS or another service, DevSuite Pro automatically switches Apache to port 8080 (or 8443) and updates all virtual host files on the fly.
</details>

<details>
<summary><b>My browser displays "Your connection is not private" for .devsuite domains.</b></summary>
<br>
In DevSuite Pro, go to <b>Settings</b> &rarr; <b>SSL Certificates</b> and click <b>Regenerate & Trust Certificates</b>. DevSuite Pro will generate fresh certificates and install the Root CA into the Windows Trusted Root Certification Authorities store. Then completely restart your browser.
</details>

<details>
<summary><b>How does per-project PHP version isolation work without Docker?</b></summary>
<br>
DevSuite Pro uses native FastCGI / CGI action handlers in Apache. Each project with a custom PHP version is mapped via `ScriptAlias` directly to that specific version's `php-cgi.exe`. This allows unlimited concurrent PHP versions with zero container overhead.
</details>

<details>
<summary><b>How do updates work? Will my projects or databases be overwritten?</b></summary>
<br>
Never. DevSuite Pro separates the executable binary from your project and database directories. The silent updater only replaces the application executable (`.exe`). Your databases in `data/`, project files in `projects/`, and settings in `%APPDATA%` remain completely untouched.
</details>

---

## 💻 System Requirements

- **Operating System:** Windows 10 (Build 19041+) or Windows 11 (64-bit).
- **Architecture:** x64 / AMD64.
- **Privileges:** Standard User (Administrative elevation is only requested once when installing the local Root CA into the Windows Certificate Store or configuring network adapter DNS).
- **Disk Space:** 500 MB minimum (varies based on downloaded runtime versions).

---

## 📜 License

DevSuite Pro is distributed as **Freeware** by **Arsal Bytes**. It is free to use for personal, educational, and commercial software development. For details, refer to the [LICENSE](LICENSE) file.

Third-party bundled services and tools are subject to their respective open-source licenses as documented in [THIRD_PARTY_LICENSES.md](THIRD_PARTY_LICENSES.md).

---

<div align="center">

**Built with ❤️ by [Arsal Bytes](https://github.com/arsalbytes)**  
*Modern tools for modern developers. Make local development stupidly easy.*

</div>
