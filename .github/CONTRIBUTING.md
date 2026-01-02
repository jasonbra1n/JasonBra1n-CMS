# Contributing to JasonBra1n CMS

Thank you for your interest in contributing!

## Development Workflow

1.  **Setup**: Copy `config-sample.php` to `config.php` and update it with your local database credentials.
2.  **Dependencies**: Run `composer install` to get the necessary dependencies.
3.  **Branching**: Create a new branch for your feature or fix (`git checkout -b feat/new-thing`).
4.  **Coding**: Adhere to PSR-12 coding standards.
5.  **Committing**: Use Conventional Commits format (`feat:`, `fix:`, `docs:`, etc.).
6.  **Pull Request**: Submit a PR with a clear description of your changes.

## Directory Structure

- **`public/`**: The Web Root. Contains `index.php`, assets (CSS/JS/Images), and the `admin/` dashboard. Only files in this directory are accessible via the browser.
- **`src/`**: Application Core. Contains PHP classes, models, and logic. This sits *outside* the `public/` directory to prevent direct access.
- **`config.php`**: Configuration file. Sits at the project root (outside `public/`).

## Core Principles

- **Modularity**: Build components that are decoupled and reusable.
- **Security First**: Sanitize all inputs, use prepared statements, and follow security best practices.
- **Clarity**: Write clean, well-documented code.