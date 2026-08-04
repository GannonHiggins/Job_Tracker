# Supabase Setup Instructions

## Step 1: Create a Supabase Account

1. Go to [https://supabase.com](https://supabase.com)
2. Click "Start your project"
3. Sign up with GitHub or email

## Step 2: Create a New Project

1. Click "New Project"
2. Fill in:
   - **Name**: Job Tracker (or your preferred name)
   - **Database Password**: Choose a strong password (save it somewhere safe!)
   - **Region**: Choose the closest region to you
3. Click "Create new project"
4. Wait 2-3 minutes for project to be created

## Step 3: Get Your API Credentials

1. Go to your project dashboard
2. Click on **Settings** (gear icon in sidebar)
3. Click on **API**
4. Copy the following:
   - **Project URL** (under "Project URL")
   - **anon public** key (under "Project API keys")

## Step 4: Add Credentials to Your Project

1. Open the `.env` file in your project root
2. Replace the placeholder values:
   ```
   VITE_SUPABASE_URL=your_project_url_here
   VITE_SUPABASE_ANON_KEY=your_anon_key_here
   ```
3. Save the file

## Step 5: Create Database Tables

1. In your Supabase dashboard, click **SQL Editor** in the sidebar
2. Click **New Query**
3. Copy and paste this SQL to create a jobs table:

```sql
-- Create jobs table
CREATE TABLE jobs (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT TIMEZONE('utc'::text, NOW()) NOT NULL,
  company_name TEXT NOT NULL,
  position_title TEXT NOT NULL,
  status TEXT NOT NULL DEFAULT 'applied',
  application_date DATE,
  job_url TEXT,
  notes TEXT,
  salary_range TEXT,
  location TEXT,
  contact_name TEXT,
  contact_email TEXT
);

-- Enable Row Level Security
ALTER TABLE jobs ENABLE ROW LEVEL SECURITY;

-- Create a policy that allows all operations for now (you can make this more restrictive later)
CREATE POLICY "Allow all operations for now" ON jobs
  FOR ALL
  USING (true)
  WITH CHECK (true);
```

4. Click **Run** to execute the SQL

## Step 6: Restart Your Dev Server

1. Stop your dev server (Ctrl+C in terminal)
2. Run `npm run dev` again
3. Your app is now connected to Supabase!

## Verify Connection

You can verify the connection is working by importing the supabase client in your React components:

```javascript
import { supabase } from './supabaseClient'

// Example: Fetch all jobs
const { data, error } = await supabase
  .from('jobs')
  .select('*')
```

## Security Note

- **NEVER** commit your `.env` file to git (it's already in `.gitignore`)
- The **anon key** is safe to use in your frontend
- For production, set up proper Row Level Security policies
