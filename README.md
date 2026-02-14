# Glassdoor Paywall Remover Update

Readme: [Português](README-ptbr.md)

![License](https://img.shields.io/github/license/sr00t3d/glassdoor-paywall-remover)
![JavaScript](https://img.shields.io/badge/language-javascript-green.svg)

This is a Userscript (user script) developed to remove the login block (paywall), intrusive overlays, and unlock page scrolling on the Glassdoor website.

The script was updated to handle the new Glassdoor implementations (2026), which use dynamic rendering via React/Next.js and aggressive inline CSS blocks on the `<body>` tag.

## 🚀 Features

* **Removes the Unified Login Modal:** Automatically hides the `#unified-user-auth` container and other "Hardsell" overlays that prevent content viewing.
* **Unlocks Scrolling (Scroll):** Monitors the `<body>` tag and instantly removes attributes `style="overflow: hidden; position: fixed;"` that the site tries to apply to prevent page scrolling.
* **Optimized Performance:** Uses `MutationObserver` and CSS injection with `!important` to ensure the unlock occurs even before the element is visually rendered, preventing blocking "flashes."
* **Resilient:** Works even when Glassdoor tries to reapply the block via SPA (Single Page Application) navigation.

## 📦 Installation

### Prerequisites
You need a script manager extension installed in your browser:
* [Tampermonkey](https://www.tampermonkey.net/) (Recommended)
* [Violentmonkey](https://violentmonkey.github.io/)
* [Greasemonkey](https://www.greasespot.net/)

### Installing the Script
1.  Make sure you have Tampermonkey (or similar) installed.
2.  **[Click here to install the script](https://greasyfork.org/pt-BR/scripts/531857-glassdoor-paywall-remover-update)**.
3.  Tampermonkey will open a tab asking for confirmation. Click **Install**.
4.  Access any Glassdoor page (e.g., company reviews) and the content will be unlocked.

## 🛠️ How it Works (Technical)

The script operates on two main fronts to overcome React rendering:

1.  **CSS Force:** Injects global CSS rules that apply `display: none !important` to known IDs and Classes of blocking modals and forces `overflow: auto` on `html` and `body`.
2.  **DOM Watcher:** A `MutationObserver` monitors attributes of the `<body>` tag. As soon as Glassdoor’s JavaScript adds `overflow: hidden`, the script detects the change and removes the entire `style` attribute, returning page control to the user.

## 📝 Changelog

* **v1.2:**
    * Logic update to focus on the `#unified-user-auth` container.
    * Implementation of aggressive attribute cleanup on the `<body>` tag.
    * Translation of comments and descriptions to English (global standard).

## ⚠️ Disclaimer

> [!WARNING]
> This software is provided "as is." Although it has been extensively tested in Dovecot environments, always perform a full backup of your Maildir directories before running any conversion script. The author is not responsible for any data loss.

---

## 🛠️ Requirements

- **OS**: Linux (Debian, Ubuntu, CentOS, RHEL).
- **Dependencies**: `bash`, `curl`, `python3` (for the internal conversion engine).
- **Permissions**: Read access to the source Maildir and write access to the destination.

## 📚 Detailed Tutorial

For a complete step-by-step guide on how to import the generated files into Thunderbird and solve common migration issues, check out the full article on my blog:

👉 [**Remove Paywall from Glassdoor**](https://perciocastelo.com.br/blog/remove-paywall-from-glassdoor.html)

## License 📄

This project is licensed under the **GNU General Public License v3.0**. See the [LICENSE](LICENSE) file for more details.
