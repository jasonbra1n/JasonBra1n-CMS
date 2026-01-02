# Scratchpad

This file is for temporary notes, plans, and brainstorming. It is not part of the final project build or documentation.

---

# 🏗️ Architecture & Design

## Directory Structure (Planned)
We are moving towards a stricter MVC-like structure for the CMS.
```text
public/
  index.php        # Front Controller
  admin/           # Admin entry point
src/
  Core/            # Router, Database, Request, Response
  Controllers/     # PageController, AdminController, ApiController
  Models/          # User, Post, Setting
  Views/           # Templates
config.php         # Environment variables
```

## Routing Strategy
*   **Goal**: Route all requests through `public/index.php` (or `public/admin/index.php` for backend).
*   **Implementation**:
    *   Use `.htaccess` to rewrite URLs to `index.php?route=...`.
    *   `Router` class to parse the URL and dispatch to the correct Controller.

---

# 🗄️ Database Infrastructure

**Server Details**: MariaDB 10.11 (cPanel)
**Connection**: PDO via `src/Database.php`

## Current Schema
*   **`users`**: Admin credentials (`username`, `email`, `password_hash`).
*   **`settings`**: Key-value store for site config (`site_name`, `maintenance_mode`, `gemini_api_key`).
*   **`auth_tokens`**: "Remember Me" functionality.

## Planned Schema Changes
*   **`pages`**: To store dynamic page content (`id`, `slug`, `title`, `content`, `template`).
*   **`posts`**: For the blog (`id`, `title`, `content`, `author_id`, `created_at`).

---

# 🔐 Authentication & Security

## Current Status
*   Basic login system implemented (`src/User.php`, `src/Session.php`).
*   "Remember Me" token system active.
*   **To Do**:
    *   Implement CSRF protection on all forms.
    *   Add rate limiting to login attempts.

---

# 🤖 Gemini API Integration

**Goal**: Enable server-side AI features to enhance the CMS.

## Phase 1: Foundation (Done)
*   [x] API Key in `config.php` / Database.
*   [x] `GeminiService` class created.

## Phase 2: CMS Features (Planned)
*   **Content Assistant**: Generate drafts for blog posts.
*   **SEO Helper**: Auto-generate meta descriptions.

---

# 🔮 Vision: AI-Powered Site Builder

**Concept**: A "self-administering" CMS where the admin uses natural language to generate structure and content.

1.  **Prompt**: "Create a landing page for a new 'Summer Event'."
2.  **Generation**: CMS uses Gemini to scaffold the DB entry and initial content.
3.  **Refinement**: Admin tweaks content via the dashboard.
4.  **Publish**: Content goes live.