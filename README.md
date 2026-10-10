# Vista Connect DataManager

## Internship Overview

This project was developed during my software engineering internship. The primary objective was to design and implement an ETL (Extract, Transform, Load) module and data management platform for Vista Connect.

The application bridges legacy data sources and modern relational schema standards, automating database schema initialization, raw CSV data ingestion, and structural JSON data exportation.

## Key Features

* Automated Schema Initialization:
  - Executes PostgreSQL SQL schema (`vista_connect_target_schema.sql`) dynamically via Laravel's `AppServiceProvider`.
  - Custom parser handles complex PostgreSQL `$$` procedural blocks, string literals, and comment removal.
  - Idempotent execution prevents table duplication and handles dynamic migrations gracefully.

* CSV Data Extraction & Transformation (Import):
  - Processes multi-entity legacy CSV files with dynamic column mapping configurations (`config/import.php`).
  - Relational mapping across multiple schemas/tables (`branches`, `customers`, `identity_documents`, `kyc_reviews`, `accounts`, `beneficiaries`, `transactions`).
  - Automatic data cleaning, normalization, and relational key resolution using `updateOrInsert`.

* Structural Data Export (JSON):
  - Generates real-time, aggregated JSON exports using streamed responses (`StreamedResponse`).
  - Relational join queries retrieve comprehensive customer portfolios and transaction histories.

* Modern Responsive UI:
  - Built with React and Bootstrap for a clean user experience.
  - Asynchronous file uploads with real-time feedback and state management.
  - Secure CSRF token handling integrated with Laravel backend endpoints.

## Tech Stack

* Frontend: React.js, Bootstrap 5, Bootstrap Icons
* Backend: Laravel (PHP)
* Database: PostgreSQL (`vc_core` schema)
* Architecture: REST API, Service Provider, Custom SQL Parser

## Architecture & Database Schema

The system ingests legacy transactional records and normalizes them into the `vc_core` PostgreSQL schema:

```
vc_core/
 |-- branches
 |-- customers
 |-- identity_documents
 |-- kyc_reviews
 |-- accounts
 |-- beneficiaries
 `-- transactions
```

## Project Structure Highlights

* `app/Providers/AppServiceProvider.php` - Custom SQL parser and automated database bootstrap logic.
* `app/Http/Controllers/ImportExportController.php` - Ingestion, transformation, and JSON export streaming algorithms.
* `resources/js/components/App.jsx` - Main React DataManager user interface.
* `config/import.php` - Key-value column mapping configuration for legacy CSV files.

## License

This project was created for educational and internship demonstration purposes.
