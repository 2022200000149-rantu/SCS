# 🎭 Southeast Cultural Society (SCS) Web Portal

> An interactive, serverless web platform designed to streamline cultural society operations, event announcements, membership management, creative article publications, and digital identity tracking.

![Live Web Page](https://img.shields.io/badge/Status-Live-success?style=for-the-badge)
![GitHub Pages](https://img.shields.io/badge/Hosting-GitHub%20Pages-blue?style=for-the-badge&logo=github)
![Google Apps Script](https://img.shields.io/badge/Backend-Google%20Apps%20Script-4285F4?style=for-the-badge&logo=google)
![Google Sheets DB](https://img.shields.io/badge/Database-Google%20Sheets-34A853?style=for-the-badge&logo=googlesheets)

---

## 🔗 Live Preview

- **Official Website:** [Southeast Cultural Society Live](https://2022200000149-rantu.github.io/SCS/)
- **Digital Member Portal:** [Member ID Verification](https://southeastculturalsociety.github.io/member/)

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Tech Stack](#-tech-stack)
- [System Architecture](#-system-architecture)
- [Database Schema (Google Sheets)](#-database-schema-google-sheets)
- [API Documentation](#-api-documentation)
- [Installation & Local Setup](#-installation--local-setup)
- [Academic Information & Team](#-academic-information--team)

---

## 📖 Overview

The **Southeast Cultural Society (SCS)** portal serves as a unified digital platform for managing the society’s cultural events, executive committee, recruitment, photo gallery, and member articles.

Built with a **serverless backend architecture**, the project utilizes **Google Apps Script** as a middleware REST API and **Google Sheets** as a database engine. This allows real-time dynamic data rendering on a responsive HTML5/CSS3 frontend without requiring traditional server infrastructure or database hosting fees.

---

## ✨ Key Features

### 🎨 Frontend & User Interface
- **Dynamic HTML5 Canvas Particle Background:** Ambient visual background with interactive particle physics.
- **News Ticker Wheel:** Live ticker bar pulling active notices and announcements dynamically.
- **Dual Infinite Auto-scrolling Gallery:** Seamless horizontal scrolling gallery combining local images (`gallery.json`) and live uploaded images from Google Sheets, complete with a full-screen modal viewer.
- **Responsive Theme:** Custom CSS tokens, oxblood/brass gold cultural aesthetics, and mobile-responsive layout.

### 👥 Membership & Verification
- **Online Application System:** Students can apply for membership with auto-generated timestamps.
- **Real-time Status Check:** Applicants can query their application status (`Pending`, `Approved`, `Rejected`) using their Student ID.
- **Digital ID Allocation:** Approved members automatically receive a formatted Digital ID (e.g., `SCS-2026-0002`).
- **Approved Member Directory:** Filterable registry displaying official society members.

### 🔐 Auth & Role-Based Access Control (RBAC)
- **Unified Login Portal:** Single login form handling both Admin and Member credentials.
- **Token-Based Cache Authentication:** Uses Google Apps Script `CacheService` with UUID session tokens (6-hour TTL).
- **Member Dashboard:** Approved members can submit, edit, and delete their own published or pending articles.
- **Admin Dashboard:** Executive panel with tabbed navigation to manage Notices, Memberships, Committee Members, Gallery Photos, and Article Approvals.

---

## 🛠 Tech Stack

| Domain | Tech / Tool | Usage |
| :--- | :--- | :--- |
| **Frontend** | HTML5, CSS3, JavaScript (ES6+) | Core web layout, interactivity, and design |
| **Animations** | HTML5 Canvas API | Dynamic floating particle background |
| **Backend / API** | Google Apps Script (GAS) | Serverless REST-like JSON API endpoints (`doGet`, `doPost`) |
| **Database** | Google Sheets | Cloud spreadsheet serving as a relational database |
| **Session Cache** | GAS `CacheService` | Server-side token storage for session authentication |
| **Hosting** | GitHub Pages | Static frontend hosting |

---

## 🏗 System Architecture

```mermaid
graph TD
    User([User / Browser])
    Admin([Executive Admin])
    
    subgraph Frontend - GitHub Pages
        UI[HTML5 / CSS3 / JavaScript]
        Canvas[Canvas Particle Engine]
        Gallery[Gallery & Modal Engine]
    end

    subgraph Backend - Google Cloud Environment
        GAS[Google Apps Script REST API]
        Cache[CacheService - Session Tokens]
    end

    subgraph Database Layer
        GS[(Google Sheets DB)]
    end

    User -->|View Notices, Gallery & Apply| UI
    Admin -->|Manage Approvals & Content| UI
    UI <-->|Fetch / Post JSON Data| GAS
    GAS <-->|Session Verification| Cache
    GAS <-->|CRUD Operations| GS
