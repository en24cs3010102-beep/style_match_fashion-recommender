<div align="center">

# 👗 StyleMatch

### A Personalized Fashion Item Recommendation Web Application

*Stop scrolling through thousands of items. Let your own taste do the filtering.*

![Version](https://img.shields.io/badge/version-1.0-blueviolet?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-REST%20API-000000?style=for-the-badge&logo=flask&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)
![Status](https://img.shields.io/badge/status-in%20development-orange?style=for-the-badge)
![Course](https://img.shields.io/badge/Software%20Engineering-Lab%20Project-success?style=for-the-badge)

[Overview](#-overview) •
[Features](#-features) •
[Architecture](#-architecture) •
[Tech Stack](#-tech-stack) •
[Getting Started](#-getting-started) •
[Roadmap](#-roadmap) •
[Team](#-team)

</div>

---

## ✨ Overview

Browsing a huge online fashion catalog causes **decision fatigue**. Manual filtering rarely surfaces the pieces that truly match your style, leading to missed finds and mismatched purchases.

**StyleMatch** learns your taste from *implicit feedback*, the items you like or save, and uses that signal to rank and surface catalog items you're more likely to love.

> 🎯 **Goal:** demonstrate a complete, testable recommender system built with **classical (non-deep-learning) machine learning**, integrated end-to-end into a working web app.

Built as the semester project for the **Software Engineering Lab**, developed incrementally across the course's eight lab experiments.

---

## 🚀 Features

| | Feature | What it does | Priority |
|---|---|---|---|
| 💖 | **Personalized "For You"** | Collaborative filtering over your likes/saves ranks items just for you | 🔴 High |
| 🔥 | **Trending Now** | Cold-start fallback showing the most-liked items catalog-wide for new/guest users | 🔴 High |
| 🛍️ | **Catalog & Liking** | Paginated catalog, category filters, one-tap Like/Save | 🔴 High |
| 🔍 | **Similar Items** | Content-based similarity (category, color, product type) on every product page | 🟡 Medium |
| 🔐 | **Register & Login** | Persistent identity so likes carry across sessions | 🟡 Medium |
| 👔 | **Outfit Bundling** | Suggests 2–3 complementary items to form an outfit *(stretch goal)* | 🟢 Low |

### How it feels to use

```text
 New visitor ──► sees "Trending Now" ──► likes a few items
                                             │
                                             ▼
                          "For You" unlocks with personalized picks
                                             │
                                             ▼
               Open any product ──► "Similar Items" panel for more ideas
```

---

## 🏗️ Architecture

StyleMatch is a **three-tier web application** with loosely coupled layers so each teammate can work in parallel.

```text
┌─────────────────────────┐
│   🖥️  FRONTEND           │   HTML / CSS / JavaScript
│   Catalog · Product ·    │   Responsive across desktop & mobile
│   For You · Login        │
└────────────┬────────────┘
             │  REST API (HTTP + JSON)
┌────────────▼────────────┐
│   ⚙️  BACKEND            │   Python · Flask
│   Auth · Catalog ·       │   Likes/saves persistence
│   Likes · Recs endpoints │   Serves model output
└─────┬───────────────┬───┘
      │               │
┌─────▼──────┐  ┌─────▼──────────────────┐
│ 🗄️ DATA    │  │ 🧠 MODEL LAYER          │
│ STORE      │  │ Collaborative filtering │
│ SQLite /   │  │ + content-based         │
│ flat files │  │ similarity (offline)    │
└────────────┘  └─────────────────────────┘
```

---

## 🧰 Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | HTML, CSS, JavaScript |
| **Backend** | Python 3.x, Flask, REST/JSON |
| **ML / Data** | pandas, scikit-learn, `implicit` or `Surprise` |
| **Storage** | SQLite or flat files *(final choice TBD)* |
| **Dataset** | Public Kaggle fashion dataset (a manageable subset) |

> ⚠️ **Deliberate constraint:** no computer vision or deep learning. Recommendations come from tabular data, user interactions and item metadata only.

---

## 🏁 Getting Started

> 📝 Exact setup commands will be finalized as the backend and model are built. The steps below are a template to fill in.

### Prerequisites

- Python 3.x
- A modern browser (Chrome, Firefox or Edge)
- A subset of the chosen public Kaggle dataset

### Installation

```bash
# 1. Clone the repository
git clone <your-repo-url>
cd stylematch

# 2. Create and activate a virtual environment
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Train the recommendation model (offline step)
python model/train.py

# 5. Start the Flask server
python app.py
```

Then open **http://localhost:5000** in your browser.

---

## 🔒 Security & Quality

- 🔑 Passwords are **hashed**, never stored in plain text
- 🙈 Users can only access **their own** likes and recommendations
- 📂 Only **publicly licensed** data, no real customer information
- 🧱 Code organized by role boundaries for independent maintenance
- ⚡ Core actions (browse, like, view recs) reachable within **two clicks** from home
- 🧊 Handles both **zero-like** and **many-like** users without errors
- 💻 Runs on any machine with no OS-specific dependencies

---

## 🗺️ Roadmap

Work follows the eight lab experiments:

| # | Experiment | Owner | Status |
|---|---|---|---|
| 1 | Problem statement & requirements | Whole team | ✅ Complete |
| 2 | Software Requirements Specification | Whole team (compiled by Amisha) | 🔄 In progress |
| 3 | Architecture & database design | Akshita | ⬜ Not started |
| 4 | UI wireframes & screen design | Hiti | ⬜ Not started |
| 5 | Dataset preparation & EDA | Amisha | ⬜ Not started |
| 6 | Recommendation model (CF + content-based) | Amisha | ⬜ Not started |
| 7 | Backend API & frontend integration | Akshita, Hiti | ⬜ Not started |
| 8 | Testing, bug fixing & final demo | Whole team | ⬜ Not started |

### Open decisions (TBD)

- [ ] Hosting: local vs. free-tier host
- [ ] Database: SQLite vs. alternative
- [ ] Dataset subset size
- [ ] REST endpoint definitions
- [ ] Items shown on "For You" and "Similar Items"
- [ ] Likes threshold that ends cold-start
- [ ] Refresh schedule for recommendations and trending
- [ ] Password-hashing approach
- [ ] Dated week-by-week schedule

---

## 👥 Team

<div align="center">

| | Name | Role | Owns |
|:---:|---|---|---|
| 🧠 | **Amisha Philip** | Data & Modeling | Dataset prep, EDA, collaborative filtering, content-based similarity, cold-start logic |
| ⚙️ | **Akshita Kose** | Backend | Flask REST API, auth/sessions, likes persistence, serving model output |
| 🎨 | **Hiti Khatod** | Frontend | Catalog, product detail, "For You" and login/register UI |

</div>

---

## 📚 Glossary

<details>
<summary><b>Click to expand</b></summary>

- **Collaborative Filtering:** predicts a user's interests from the preferences of similar users.
- **Content-Based Filtering:** suggests items similar to ones a user liked, based on item attributes.
- **Cold Start:** making recommendations for a user or item with little or no history.
- **Implicit Feedback:** preference signals inferred from behavior (likes, saves, clicks) instead of ratings.
- **MVP:** the smallest feature set that delivers the core value of the product.

</details>

---

<div align="center">

**Prepared for the Software Engineering Lab** · Version 1.0 · September 14, 2026

Made with 💜 by Amisha, Akshita & Hiti

</div>
