# 🌐 Personal Portfolio Website

<p align="center">
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5 Badge"/>
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3 Badge"/>
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript Badge"/>
  <img src="https://img.shields.io/badge/GitHub%20Pages-222222?style=for-the-badge&logo=github&logoColor=white" alt="GitHub Pages Badge"/>
  <img src="https://img.shields.io/badge/Web3Forms-002E4E?style=for-the-badge&logo=webauthn&logoColor=white" alt="Web3Forms Badge"/>
</p>

An attractive, high-performance, and responsive static portfolio website engineered for **Bhushan Todkar** (Electronics & Computer Engineering Student). The site functions as a digital CV and interactive archive showcasing academic coursework, professional experiences, certifications, and technical projects.

🔗 **Live Portfolio:** [bhushantodkar.me](https://bhushantodkar.me)

---

## 🗺️ Interactive Directory (Table of Contents)
- [✨ Key Features](#-key-features)
- [🛠️ Tech Stack & Architecture](#%EF%B8%8F-tech-stack--architecture)
- [📩 Contact Form Integration (Web3Forms)](#-contact-form-integration-web3forms)
- [🌐 Hosting & Custom Domain Deployment](#-hosting--custom-domain-deployment)
  - [1. GitHub Pages Hosting](#1-github-pages-hosting)
  - [2. Namecheap .me TLD Configuration](#2-namecheap-me-tld-configuration)
- [📂 Project Directory Structure](#-project-directory-structure)
- [💻 Getting Started Locally](#-getting-started-locally)

---

## ✨ Key Features

- **Responsive Mobile Layout:** Complete media query system tailored for mobile, tablet, laptop, and ultrawide screens.
- **CSS-Only Hamburg Menu Toggle:** An interactive mobile navbar built using a hidden checkbox hack (`#menu-toggle`) to enable side-drawer toggles without relying on heavy JavaScript event listeners.
- **Polished Glassmorphism & Aesthetics:** A modern, dark-themed interface built using subtle gradient borders, backdrop filters, and custom CSS variables for design consistency.
- **Academics & Certifications Tracker:** Visual cards displaying CGPA breakdown, relevant coursework (DSA, OOP, DBMS, Embedded Systems), and certified coursework.
- **Embedded Systems & Software Project Showcase:** Grid layout featuring flagship projects like the *Smart File Organizer* and *Off-Grid LoRa Emergency Alert System*.
- **AJAX-Powered Contact Form:** Captcha-protected communication interface integrated directly with Web3Forms API.

---

## 🛠️ Tech Stack & Architecture

- **Markup:** `HTML5` for semantic structure.
- **Styles:** `CSS3` utilizing a highly scalable **Modular CSS** structure.
- **Scripts:** `Vanilla JavaScript` (AJAX contact form pipeline with visual feedback, loading spinner, and success toast timeouts).

### Modular CSS Organization
Instead of managing a monolithic stylesheet, the styles are segregated into logically separated modules inside [CSS/](file:///d:/Portfolio/CSS):

| Stylesheet | Responsibility |
| :--- | :--- |
| `reset.css` | Standardized box sizing, typography resets, and scroll behavior |
| `variables.css` | Core tokens (colors, gradients, transition curves, line-heights) |
| `navbar.css` | Desktop/Mobile headers and checkbox-based toggle |
| `hero.css` | Profile photo, taglines, layout grid |
| `education.css` | Academic cards, coursework listings, certification layouts |
| `experience.css` | Internship metrics, key outcomes, timeline layouts |
| `projects.css` | Portfolios, tech tags, action buttons |
| `skills.css` | Card layouts, technical taxonomy grids |
| `contact.css` | Structured inputs, captcha containers, and validation toasts |
| `footer.css` | Copyright details and social anchor links |
| `responsive.css` | Container constraints and layout adaptations for mobile breakpoints |
| `styles.css` | Master stylesheet that imports all other modules |

---

## 📩 Contact Form Integration (Web3Forms)

The form utilizes **Web3Forms** to transmit form submissions directly to email without requiring a backend server. 

### Implementation Highlights
1. **Asynchronous JS Submission:** Uses the `fetch` API to post JSON-formatted payloads, handling errors gracefully and showing loading spinners without page reloads.
2. **Spam & Abuse Defense:** 
   - **Honeypot:** A hidden checkbox field (`name="botcheck"`) is implemented. Automated spam scripts fill this out, triggering immediate API rejection, while real users never see it.
   - **hCaptcha:** An interactive robot-check challenge block is validated client-side before sending data.
3. **Responsive feedback:** An interactive toast notification fades into view upon submission and automatically times out after 5 seconds.

<details>
<summary><b>🔍 View JavaScript Submission Pipeline</b></summary>

```javascript
fetch('https://api.web3forms.com/submit', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'Accept': 'application/json'
  },
  body: JSON.stringify(object)
})
.then(async (response) => {
  if (response.status == 200) {
    // Success Toast Notification
    contactForm.reset();
  }
})
```
</details>

---

## 🌐 Hosting & Custom Domain Deployment

This project is deployed to production using **GitHub Pages** and mapped to a custom **`.me`** TLD purchased via **Namecheap**.

### 1. GitHub Pages Hosting
- Configured via the repository's settings panel.
- Pointed to build/deploy directly from the root of the `main` branch.
- HTTPS is enforced to encrypt traffic.

### 2. Namecheap .me TLD Configuration
To link the custom domain `bhushantodkar.me` with GitHub Pages, the following steps were implemented:

1. **CNAME Document:** Created a [CNAME](file:///d:/Portfolio/CNAME) file containing exactly one line at the root of the repository:
   ```text
   bhushantodkar.me
   ```
2. **Namecheap DNS Records:** Logged into the Namecheap Dashboard and navigated to the **Advanced DNS** tab for `bhushantodkar.me`. Added the following records:

| Record Type | Host | Value (Target) | TTL | Purpose |
| :--- | :--- | :--- | :--- | :--- |
| **A Record** | `@` | `185.199.108.153` | Automatic | Map apex domain to GitHub Pages server |
| **A Record** | `@` | `185.199.109.153` | Automatic | Map apex domain to GitHub Pages server (Backup) |
| **A Record** | `@` | `185.199.110.153` | Automatic | Map apex domain to GitHub Pages server (Backup) |
| **A Record** | `@` | `185.199.111.153` | Automatic | Map apex domain to GitHub Pages server (Backup) |
| **CNAME Record** | `www` | `bhushan191105.github.io.` | Automatic | Redirect WWW subdomain requests |

---

## 📂 Project Directory Structure

```text
Portfolio/
├── .gitignore
├── CNAME                  # Maps GitHub Pages to bhushantodkar.me
├── index.html             # Core semantic layout & script container
├── README.md              # Project documentation
├── ASSETS/
│   ├── Resume.pdf         # Downloadable CV
│   └── Images/            # Graphic assets and project cover previews
└── CSS/
    ├── variables.css      # Core styles tokens
    ├── reset.css          # Element defaults
    ├── navbar.css         # Navigation responsive components
    ├── hero.css           # Header introductions
    ├── education.css      # Academic grids
    ├── experience.css     # Internship logs
    ├── projects.css       # Project cards
    ├── skills.css         # Technical taxonomy grids
    ├── contact.css        # Interactive form layouts
    ├── footer.css         # Social anchors
    ├── responsive.css     # Responsive viewport queries
    └── styles.css         # Imports and links stylesheets
```

---

## 💻 Getting Started Locally

You don't need any complex compilers, preprocessors, or package runners to run this site locally.

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/bhushan191105/My-Portfolio-Website.git
   ```
2. **Navigate into Directory:**
   ```bash
   cd My-Portfolio-Website
   ```
3. **Run Locally:**
   - Simply double-click [index.html](file:///d:/Portfolio/index.html) to open it in any web browser.
   - Alternatively, use the **Live Server** extension in VS Code for live-reloading.

---

<p align="center">
  Developed by <a href="https://linkedin.com/in/bhushan-s-todkar19">Bhushan Todkar</a>. Engineered with precision.
</p>