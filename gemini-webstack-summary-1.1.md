# REVMA Hub Webstack Summary v1.1

This document provides a comprehensive breakdown of the technologies, libraries, and tools used to build and maintain the REVMA Hub website.

---

## Core Frameworks & Language

### **Next.js (v15.2.4)**
**Basic Description:** The "brain" of the website. It manages how pages are built, how users move between them, and how the site connects to the internet.
**Technical Description:** A React-based framework that enables features like Server-Side Rendering (SSR), Static Site Generation (SSG), and the modern App Router architecture. It handles routing, image optimization, and API routes within a single unified project structure.
**Role in the Website:** Acts as the primary application server and frontend framework. It renders the HTML, CSS, and JavaScript that users see and interact with.

### **React (v19)**
**Basic Description:** A library for building the visual parts of the website using reusable "bricks" called components.
**Technical Description:** A JavaScript library for building user interfaces based on a component architecture. Version 19 introduces improved performance and better handling of asynchronous data loading.
**Role in the Website:** Powering every visual element, from the navigation bar to the resource cards. It manages the "state" of the site (e.g., which menu is open or which language is selected).

### **TypeScript (v5)**
**Basic Description:** An "editor's assistant" that helps developers write code with fewer mistakes by checking for errors as they type.
**Technical Description:** A strongly typed superset of JavaScript that adds static typing. It allows developers to define the "shape" of data, making the codebase more predictable, easier to debug, and more maintainable.
**Role in the Website:** The primary language used for all logic and component development. It ensures that data coming from WordPress matches what the website expects.

---

## Content Management & Data Fetching

### **WordPress (Headless CMS)**
**Basic Description:** The "digital warehouse" where all the articles, resources, and testimonials are stored and edited by the REVMA team.
**Technical Description:** Used in a "Headless" capacity, meaning its built-in visual editor is ignored in favor of its data-storage capabilities. It exposes content via a GraphQL API rather than traditional web pages.
**Role in the Website:** Serves as the backend administrative interface where non-technical staff can add educational resources or update teacher testimonials without touching any code.

### **GraphQL**
**Basic Description:** A "smart ordering system" that allows the website to ask the warehouse for exactly what it needs and nothing more.
**Technical Description:** A query language for APIs that provides a complete and understandable description of the data in your API. It allows the frontend to request specific fields (like just the 'title' and 'image_url') in a single request.
**Role in the Website:** The language used to communicate between the Next.js frontend and the WordPress backend.

### **Apollo Client**
**Basic Description:** The "delivery truck" that carries the GraphQL orders to the warehouse and brings the data back to the website.
**Technical Description:** A comprehensive state management library for JavaScript that enables you to manage both local and remote data with GraphQL. It handles data fetching, caching, and updating the UI automatically.
**Role in the Website:** Configured in `lib/apollo.ts`, it manages all requests to the WordPress API and makes that data available to the React components.

---

## Styling & User Experience

### **Tailwind CSS (v4)**
**Basic Description:** A "styling toolkit" that allows developers to design the website directly in the code using pre-set rules for colors, spacing, and fonts.
**Technical Description:** A utility-first CSS framework that provides low-level utility classes to build custom designs without leaving your HTML/component files. It uses a "Just-in-Time" compiler to keep the final CSS file as small as possible.
**Role in the Website:** Handles the entire visual layout, responsiveness (mobile vs. desktop views), and styling of every component.

### **PostCSS**
**Basic Description:** A tool that "cleans up" and optimizes the website's styling code so it works perfectly in all web browsers.
**Technical Description:** A tool for transforming CSS with JavaScript plugins. It handles tasks like adding vendor prefixes and optimizing CSS for production.
**Role in the Website:** Works behind the scenes to process the Tailwind CSS and ensure browser compatibility.

### **Embla Carousel**
**Basic Description:** A tool used to create smooth, sliding image galleries (carousels).
**Technical Description:** A lightweight, "bare-bones" carousel library with a focus on performance and accessibility. It provides the physics and logic for sliding elements without forcing a specific look.
**Role in the Website:** Used on the homepage and other sections to display sliding images and testimonials.

### **Headless UI**
**Basic Description:** A set of "invisible components" that handle complex interactions like pop-up windows (modals) while letting the developer choose the look.
**Technical Description:** A set of completely unstyled, fully accessible UI components designed to integrate beautifully with Tailwind CSS.
**Role in the Website:** Used for accessible interactive elements like the `ContactModal.tsx`.

### **React Icons**
**Basic Description:** A massive library of icons (like mail icons, phone icons, or social media logos).
**Technical Description:** A library that allows you to include popular icons from different sets (Font Awesome, Material Design, etc.) as React components.
**Role in the Website:** Provides the small visual symbols used in the footer, navigation, and contact forms.

---

## Localization & Translation

### **next-intl / Custom Translation Context**
**Basic Description:** The system that allows the website to switch instantly between Greek and English.
**Technical Description:** While `next-intl` is in the dependencies, the project uses a `TranslationContext.tsx` and `translations/` JSON files to manage text strings in different languages. It uses the URL and browser storage to remember the user's preference.
**Role in the Website:** Ensures that every piece of text on the site can be displayed in either Greek or English based on the user's choice.

---

## Communication & Emailing

### **Nodemailer**
**Basic Description:** A tool that allows the website's server to "write" and send emails.
**Technical Description:** A module for Node.js applications to allow easy email sending. It supports SMTP, file attachments, and HTML content.
**Role in the Website:** Used in the `api/` routes to send contact form submissions and resource-sharing emails from the server side.

### **EmailJS**
**Basic Description:** A service that can send emails directly from the website without needing a complex server setup.
**Technical Description:** A service that helps send emails using only client-side technologies. It connects your email service (like Gmail or Outlook) to your web app.
**Role in the Website:** Provides an alternative or supporting method for sending emails directly from the browser context.

---

## Infrastructure & Tooling

### **Vercel**
**Basic Description:** The "home" of the website on the internet. It hosts the code and makes sure the site is fast and always online.
**Technical Description:** A cloud platform for static sites and Frontend Frameworks, optimized for Next.js. It provides Global Edge Network delivery and automatic deployments.
**Role in the Website:** The hosting provider where the Next.js application is deployed and served to the world.

### **Turbopack**
**Basic Description:** An "engine booster" for developers that makes the website build and update incredibly fast during development.
**Technical Description:** An incremental bundler optimized for JavaScript and TypeScript, written in Rust. It is the successor to Webpack for Next.js projects.
**Role in the Website:** Speeds up the development process, allowing the team to see their changes instantly.

### **ESLint**
**Basic Description:** A "code inspector" that points out messy code or potential bugs.
**Technical Description:** A static code analysis tool for identifying problematic patterns found in JavaScript/TypeScript code.
**Role in the Website:** Ensures that all developers follow the same coding standards and avoid common mistakes.
