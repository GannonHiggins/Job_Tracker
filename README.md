# Job Tracker

A modern job application tracking system built with React and Vite.

## Tech Stack

- **React 18** - UI library
- **Vite** - Build tool and dev server
- **JavaScript (JSX)** - Programming language

## Prerequisites

- [Node.js](https://nodejs.org/) (v16 or higher)
- npm (comes with Node.js)

## Installation

1. Clone the repository
2. Install dependencies:

```bash
npm install
```

### Windows PowerShell Note

If you encounter a "scripts disabled" error when running npm commands, you need to change PowerShell's execution policy:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

## Running the Application

Start the development server:

```bash
npm run dev
```

The app will be available at `http://localhost:5173/`

The dev server includes Hot Module Replacement (HMR) - your changes will automatically refresh in the browser as you save files.

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build locally

## Project Structure

```
Job_Tracker/
├── src/
│   ├── App.jsx          # Main App component
│   ├── App.css          # App styles
│   ├── main.jsx         # Application entry point
│   └── index.css        # Global styles
├── public/              # Static assets
├── index.html           # HTML template
├── package.json         # Dependencies and scripts
└── vite.config.js       # Vite configuration
```

## Development

This project uses Vite for fast development with instant hot reload. Simply run `npm run dev` and start coding - changes will appear in your browser immediately.
