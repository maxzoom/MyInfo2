# Guestbook Feature Implementation Plan

## Goal
Add a "Guestbook" page where visitors can:
1.  View a list of messages left by others.
2.  Write and submit their own message (Name, Message).

## Architecture
Since your site is hosted on **Vercel**, we can easily add a backend without a separate server using **Vercel Serverless Functions**. For storage, we will use **Supabase** (PostgreSQL) as it is free, fast, and easy to use.

### 1. Database (Supabase)
We need a simple table to store messages.

**Table Schema:** `guestbook`
- `id`: int8 (Primary Key, Auto increment)
- `created_at`: timestamptz (Default: now())
- `name`: text (The writer's name)
- `message`: text (The content)

### 2. Backend (Vercel Functions)
We will create an API that the frontend can talk to.
File: `api/guestbook.js`

- **GET /api/guestbook**: Fetches the last 20 messages.
- **POST /api/guestbook**: Saves a new message to Supabase.

### 3. Frontend (UI)
We will create a new file `guestbook.html` (or add a section to `index.html`).

**UI Components:**
- **Form:** Input fields for "Name" and "Message", and a "Submit" button.
- **List:** A container (`<div id="messages">`) to display loaded messages.
- **Logic:** JavaScript to call the API using `fetch()`.

## Step-by-Step Implementation Guide

### Step 1: Supabase Setup
1.  Create a Supabase project.
2.  Run the SQL query to create the table.
3.  Get the `SUPABASE_URL` and `SUPABASE_KEY`.

### Step 2: Vercel Configuration
1.  Install the Supabase client: `npm install @supabase/supabase-js`.
2.  Create `api/guestbook.js` with the server logic.
3.  Add environment variables to Vercel (Settings -> Environment Variables).

### Step 3: Frontend Development
1.  Create the HTML structure for the form and list.
2.  Write the JavaScript to:
    - Load messages on page load.
    - Send data when the form is submitted.

### Step 4: Deploy
1.  `git push` to deploy.
2.  Verify the connection.
