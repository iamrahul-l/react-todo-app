# Keeper App Documentation

Welcome to the **Keeper App** project! This app is inspired by Google Keep and allows users to create, display, and delete notes. It is built using **React** and leverages **Material-UI** for styling and interactivity.

---

## Table of Contents
1. [Overview](#overview)
2. [Features](#features)
3. [Components](#components)
   - [App](#app-component)
   - [Header](#header-component)
   - [Footer](#footer-component)
   - [CreateArea](#createarea-component)
   - [Note](#note-component)
4. [Dependencies](#dependencies)
5. [Setup Instructions](#setup-instructions)
6. [Project Structure](#project-structure)
7. [How to Contribute](#how-to-contribute)
8. [License](#license)

---

## Overview

The **Keeper App** is a simple note-taking application where users can:
- Add a note with a title and content.
- View all saved notes.
- Delete notes they no longer need.

This project is a beginner-friendly demonstration of state management in React and dynamic UI updates.

---

## Features

- **Dynamic Note Addition**: Users can add notes with a title and content.
- **Delete Notes**: Each note can be individually deleted.
- **Interactive Animations**: Material-UI is used for enhanced user experience with animations and icons.
- **Responsive Design**: The app dynamically adjusts the UI based on user interaction.

---

## Components

### App Component

**Location**: `App.js`

The `App` component manages the state of the notes and renders the main layout of the app. It passes state management functions (`addNote` and `deleteNote`) as props to child components.

---

### Header Component

**Location**: `Header.js`

The `Header` component displays the app's title with an icon for visual appeal.

```jsx
<HighlightIcon />Keeper
```

---

### Footer Component

**Location**: `Footer.js`

The `Footer` component displays the current year dynamically.

---

### CreateArea Component

**Location**: `CreateArea.js`

The `CreateArea` component provides a form for users to create a new note. It includes:
- An expanding textarea when clicked.
- A floating action button (FAB) to submit the note.

---

### Note Component

**Location**: `Note.js`

The `Note` component renders individual notes with a title, content, and delete button. Each note has a unique `id` used for deletion.

---

## Dependencies

- **React**: For building the UI.
- **Material-UI**: For icons and interactive UI elements.
  - `@mui/icons-material`
  - `@mui/material`

---

## Setup Instructions

1. **Clone the repository**:
   ```bash
   git clone https://github.com/iamrahul-l/react-todo-app.git
   cd keeper-app
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Run the application**:
   ```bash
   npm start
   ```

4. **Open the app**:
   The app will be available at `http://localhost:5173`.

---

## Project Structure

```plaintext
keeper-app/
├── public/
│   └── index.html
├── src/
│   ├── components/
│   │   ├── App.js
│   │   ├── Header.js
│   │   ├── Footer.js
│   │   ├── CreateArea.js
│   │   └── Note.js
│   ├── index.js
│   └── styles.css
├── package.json
└── README.md
```

---

## How to Contribute

1. **Fork the repository**.
2. **Clone your fork**:
   ```bash
   git clone  https://github.com/iamrahul-l/react-todo-app.git
   ```
