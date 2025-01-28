# Contributing to Our WordPress Themes or Plugins

Thank you for considering contributing to our WordPress themes or plugins! This document outlines our conventions and best practices for a smooth and collaborative development process.

---

## Git Workflow

We use a **main/dev branch workflow** to ensure clean and organized collaboration. Here’s an overview of how we manage our branches and commits:

### **Branches**

- **`main`**:
  - This is the production-ready branch.
  - Only stable and thoroughly tested code is merged into this branch.
  - Avoid direct commits to `main`.

- **`dev`**:
  - This branch is used for active development.
  - All feature branches and bug fixes are merged into `dev` after review.

- **Feature Branches**:
  - Used for developing new features.
  - Always branch off `dev` using the naming convention `feature/<feature-name>`.
  - Example: `feature/add-theme-options`

- **Bug Fix Branches**:
  - Used for fixing bugs or issues.
  - Always branch off `dev` using the naming convention `fix/<bug-name>`.
  - Example: `fix/header-alignment`

- **Hotfix Branches**:
  - Used for urgent fixes on the production code.
  - Always branch off `main` using the naming convention `hotfix/<bug-name>`.
  - Example: `hotfix/fix-404-error`

---

### **Workflow for Contributors**

1. **Start with a Branch for Each Task**:
   - Create a feature or fix branch off `dev`:
     ```bash
     git checkout dev
     git pull origin dev
     git checkout -b feature/add-custom-footer
     ```

2. **Make Incremental Commits**:
   - Commit changes frequently with meaningful messages:
     ```bash
     git add .
     git commit -m "feat(footer): add support for custom footer text"
     ```

3. **Push Changes and Open a Pull Request**:
   - Push your branch to the remote repository:
     ```bash
     git push origin feature/add-custom-footer
     ```
   - Open a pull request (PR) to merge your branch into `dev`.

4. **Code Review**:
   - At least one team member must review the pull request.
   - Address any requested changes before merging.

5. **Merge into `dev`**:
   - Once approved, merge your branch into `dev` and delete the branch:
     ```bash
     git checkout dev
     git merge feature/add-custom-footer
     git push origin dev
     git branch -d feature/add-custom-footer
     git push origin --delete feature/add-custom-footer
     ```

6. **Test on Staging**:
   - The `dev` branch is deployed to staging or development for testing.

7. **Deploy to Production**:
   - Once the changes are tested and approved, merge `dev` into `main`:
     ```bash
     git checkout main
     git merge dev
     git push origin main
     ```

---

## File Header and Versioning

Every file must include the following header, with an incremented version after updates:

```php
/**
 * File: <file-name>.php
 * Version: 1.0.0
 * Description: Short description of the file functionality.
 */
```

### Example
For a login branding file:
```php
/**
 * File: login-branding.php
 * Version: 1.0.18
 * Description: Adds custom branding to the WordPress login page.
 */
```

### Versioning System
We follow semantic versioning (`MAJOR.MINOR.PATCH`):
- **MAJOR**: Incompatible API changes.
- **MINOR**: Backward-compatible functionality additions.
- **PATCH**: Backward-compatible bug fixes.

Example:
- `1.0.0`: Initial release.
- `1.1.0`: Adds a new feature.
- `1.1.1`: Fixes a minor bug.

Remember to update the version number after every change to the file.

---

## Table of Contents (TOC) for Larger Files

For larger `.php` or `.css` files, a Table of Contents (TOC) should be included at the beginning of the file to provide a clear overview of the sections and improve maintainability. The TOC helps contributors navigate the file quickly and ensures consistency across the codebase.

### When to Use a TOC
- Include a TOC for files exceeding **150 lines** or files containing **multiple sections** (e.g., grouped functions, styles, or logic).
- Avoid using a TOC for short or single-purpose files.

### TOC Format
The TOC should use numbered sections for better readability and reference. Each section should have a descriptive title matching the in-file section headers.

### Example TOC for `.php` Files
```php
/**
 * Table of Contents
 * 1. Initialization Functions
 * 2. Custom Hooks and Filters
 * 3. Helper Functions
 * 4. AJAX Handlers
 */
```

### Example TOC for `.css` Files
```css
/* ============================================
 * Table of Contents
 * ============================================
 * 1. General Styles
 * 2. Header Styles
 * 3. Footer Styles
 * 4. Component-Specific Styles
 */
```

### Guidelines for Section Headers
Each section in the file should correspond to an entry in the TOC. Use consistent and descriptive headers to mark sections.

#### Example for `.php` Section Headers
```php
/**
 * 1. Initialization Functions
 */
function initialize_theme() {
    // Initialization logic
}
```

#### Example for `.css` Section Headers
```css
/* ===========================================
 * 2. Header Styles
 * =========================================== */
.site-header {
    background-color: #fff;
}
```

### Updating the TOC
Whenever you add, remove, or significantly modify sections in a file, update the TOC to reflect the changes. This ensures the TOC remains accurate and useful for all contributors.

---

## Code Comment Guidelines

Please use consistent and descriptive comments for functions, classes, and styles. Follow these examples:

### **PHP Function Comments**
Use PHPDoc-style comments for all functions:

```php
/**
 * Short description of the function
 *
 * Longer description if necessary, explaining what the function does,
 * its parameters, and its return value.
 *
 * @param string $param_name Description of the parameter.
 * @return void
 */
function my_custom_function($param_name) {
    // Function logic here
}
```

### **CSS Comments**
Use structured comments to organize styles:

```css
/*
 * Short description of the section
 *
 * Use specific comments for clarity where necessary
 */

/* === Header Styles === */
.site-header {
    background-color: #fff;
    border-bottom: 1px solid #ddd;
}

/* Center the site logo */
.site-header .logo {
    text-align: center;
}
```

### **JavaScript Comments**
Use clear inline and block comments:

```javascript
// Short description of what the function does
function myCustomFunction() {
    // Initialize variables
    let counter = 0;

    /*
     * Loop through items and perform an action
     */
    for (let i = 0; i < items.length; i++) {
        console.log(items[i]);
    }
}
```

---

## Commit Message Guidelines

Follow this structure for consistent and meaningful commit messages:

### **Format**
```
<type>(<scope>): <short description>
```

### **Types**
- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Changes to documentation
- `style`: Code style changes (e.g., formatting)
- `refactor`: Code restructuring without changing functionality
- `perf`: Performance improvements.
- `test`: Adding or fixing tests
- `chore`: Maintenance or non-functional updates

### **Examples**
```bash
git commit -m "feat(theme-options): add support for custom header images"
git commit -m "fix(navbar): resolve mobile menu alignment issue"
git commit -m "docs(readme): add installation instructions"
```

---

## Branching Strategy

We use the **Feature Branch Workflow**:

### **Branch Types**
- `main`: Production-ready code.
- `develop`: In-progress work or testing.
- `feature/<feature-name>`: New features.
- `fix/<bug-name>`: Bug fixes.
- `release/<version>`: Preparing production-ready code.
- `hotfix/<bug-name>`: Urgent fixes applied to production.

### **Examples**
```bash
git checkout -b feature/add-theme-options
git checkout -b fix/footer-alignment
```

---

## Pull Request Guidelines

1. **Work in a Branch:** Ensure all changes are made in a branch (e.g., `feature/add-sidebar`).
2. **Write a Clear Description:** Provide a concise explanation of the changes in the PR description.
3. **Assign Reviewers:** Tag at least one team member to review your pull request.
4. **Ensure Tests Pass:** Run tests locally before submitting a pull request.

---

## Coding Standards

Adhere to the following coding standards:
- **PHP:** Use [WordPress PHP Coding Standards](https://developer.wordpress.org/coding-standards/wordpress-coding-standards/). Run PHP CodeSniffer:
  ```bash
  phpcs --standard=WordPress wp-content/themes/your-theme
  ```
- **CSS:** Follow the [CSS Coding Standards](https://developer.wordpress.org/coding-standards/wordpress-coding-standards/css/).
- **JavaScript:** Use [WordPress JavaScript Standards](https://developer.wordpress.org/coding-standards/wordpress-coding-standards/javascript/).

---

## File and Folder Structure

Ensure files are placed in the appropriate directories:

- **PHP:** Place all theme functionality in `functions.php` or separated into `inc/` for modularity.
- **CSS/SCSS:** Keep all styles in the `css/` or `scss/` folder.
- **JavaScript:** Store scripts in the `js/` folder.
- **Images:** Save all theme images in the `img/` folder.  
  - **Use modern formats:** Prefer `.svg`, `.webp`, or other next-gen image formats.
  - Optimize images before uploading to the repository.
  - Avoid using large, unoptimized `.jpg` or `.png` files.

---

## Suggestions for Collaboration

- **Communication:** Use GitHub Issues to discuss new features or bugs before starting work.
- **Documentation:** Update the `README.md` or create a new `docs/` file when introducing significant changes.
- **Consistency:** Follow the agreed conventions for naming files, branches, and functions.

---

Thank you for your contributions! Let’s build something amazing together.
