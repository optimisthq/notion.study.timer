# notion.study.timer
The one solution notion timer html version for embedding

# JEE Study Tracker with Automated Notion Sync

A sleek, lightweight, minimalist HTML/JavaScript study timer designed to track intensive preparation sessions. This tracker features a local analytics dashboard and is fully integrated with a cloud-based Notion database via custom webhooks for permanent data storage.

## 🚀 Features

- **Dynamic Timer:** Built-in validation that automatically discards accidental triggers (sessions under 5 seconds).
- **Custom Categorization:** Tracks study sessions across core subjects (Physics, Chemistry, Math) with custom text memos/notes.
- **Local Analytics Dashboard:** Displays current and historical session metrics directly in the browser using `localStorage`.
- **Cloud Database Sync:** Automatically streams log data across the web to a designated Notion workspace workspace in real-time.
- **Independent History Purging:** Includes a local reset utility that wipes browser-cached history without affecting or modifying archived cloud rows.

## 🛠️ Architecture & Workflow

The system operates via a continuous three-tiered data pipeline:

1. **Frontend (Client Side):** The customized HTML structure handles the timer engine and captures session inputs (`subject`, `duration`, `notes`, and real-time `start/end` clock timestamps).
2. **Middleware API (Make.com):** A headless server endpoint listens for incoming network `POST` requests payload transmissions, captures the JSON data stream, and standardizes field configurations.
3. **Backend Database (Notion):** A structured data table receiving real-time logs, utilizing dynamic formulas to parse raw data (e.g., converting runtime minutes into decimal hour increments).

## 💻 Tech Stack

- **Frontend:** Semantic HTML5, CSS3 (Serif Typography Layout), JavaScript (ES6+ Web Fetch API)
- **Automation / Integration:** Make.com Webhook Integration Engine
- **Database System:** Notion API / Relational Database Workspace

## 🔌 Webhook & Notion Integration Guide

This project automatically syncs logged study sessions into a private Notion database using a cloud automation pipeline via **Make.com**. 

To keep your personal database endpoints secure and hidden from the public on GitHub Pages, this tracker utilizes a **local sandbox-friendly configuration panel** that saves your webhook link directly inside your browser's private local cache instead of hardcoding it.

### 📋 Prerequisites

1. A **Notion** account with a target database containing the following property columns:
   - `Date` (Date type $\rightarrow$ Set 'Include Time' to **No**)
   - `Subject` (Select or Text type)
   - `Duration (Min)` (Number type)
   - `Notes` (Text type)
   - `Start Time` (Text type)
   - `End Time` (Text type)
2. A free account on **Make.com** (formerly Integromat).

---

### 🛠️ Configuration Steps

#### Step 1: Set Up the Webhook Engine on Make
1. Log into **Make.com**, navigate to **Scenarios**, and click **Create a new scenario**.
2. Click the large `+` icon, search for **Webhooks**, and select the **Custom Webhook** module.
3. Click **Add** to create a new webhook instance. Give it a descriptive name (e.g., *JEE Tracker Input*) and click **Save**.
4. Make will generate a unique, secure URL string. **Copy this URL address to your clipboard**.
5. Leave the module window open in "Listening" mode (`Status: Stop listening`).

#### Step 2: Link Your Webhook via the Local UI Panel
1. Open your tracker page layout deployment (either locally or via your live GitHub Pages link inside your Notion frame workspace).
2. Scroll to the bottom of the interface and click the tiny link text: **`⚙️ Configure Webhook Link`**.
3. In the custom setup panel that expands open, paste your fresh **Make.com Webhook URL** directly into the input field and click **Save Link**. 
4. *(Your browser will safely memorize this token key locally on your device, keeping your public GitHub repository code completely clean and anonymous).*

#### Step 3: Map the Data Stream Structure
1. On your Make scenario canvas, click **Run Once** in the bottom left corner to force the webhook to listen for an active data sample.
2. Go back to your tracker layout, select a test subject, run a quick **5-second sample timer**, type a test note, and click the **✓ Log** button.
3. Return to Make.com. The Webhook icon wrapper will flash green, indicating it successfully intercepted and parsed the incoming JSON data structure fields (`date`, `subject`, `duration_min`, `note`, `startTime`, `endTime`).

#### Step 4: Link and Configure the Notion Cloud Module
1. Click the **Add another module** extension bubble right next to your Webhook node on the Make canvas and choose **Notion**.
2. Select the **Create a Database Item** action command.
3. Click **Add** under the *Connection* setting to authenticate and link your secure Notion workspace profile. Ensure you grant the integration explicit permission to read/write to your specific Study Tracker database page.
4. Select your **Database ID** from the search directory dropdown selection list.
5. In the field property configurations, map the incoming custom data parameters to your columns exactly as follows:
   - **Name:** Map `1. subject`
   - **Date $\rightarrow$ Start Time:** Map `1. date` *(Leave Date $\rightarrow$ End Time blank and toggle **Include Time** to **No**)*
   - **Start Time (Text column):** Map `1. startTime`
   - **End Time (Text column):** Map `1. endTime`
   - **Duration (min):** Map `1. duration_min`
6. Click **OK** to close the mapping card configuration interface block.

---

### ⚡ Activation and Deployment

1. Click the blue **Save icon (Floppy Disk)** located on the bottom toolbar menu to save your scenario scripts (alternatively, ctrl +S).
2. Flip the scheduling slider toggle in the lower-left corner from **OFF** to **ON**. 
3. Select **Immediately** under the execution parameters window.

The real-time data pipeline is now fully automated! Every session saved on the frontend client page will bypass browser storage limits and log directly to your cloud Notion database layout instantly.

---
*Created as part of an automated workflow setup for tracking core academic milestones.*


Deployed website url : [Timer](https://optimisthq.github.io/notion.study.timer/study_timer.html)

version 2 : [HERE!](https://optimisthq.github.io/notion.study.timer/new.html)
