# React Todo App Documentation

## View Live : https://react-project-todolist-ashy.vercel.app/

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Folder Structure](#folder-structure)
- [Components](#components)
- [Dependencies](#dependencies)
- [License](#license)

---

## Overview
This is a React-based "Todo App" that allows users to create, view, and delete notes. It mimics a simplified version of Google Keep, using Material-UI for icons and design components.

---

## Features
- **Add Notes**: Users can input a title and content to create a note.
- **Dynamic Notes Display**: Displays a list of notes with unique content and titles.
- **Delete Notes**: Each note can be deleted individually.
- **Responsive UI**: Smooth transitions with Material-UI components.

---

## Installation
### Prerequisites
Ensure you have the following installed on your system:
- [Node.js](https://nodejs.org/)
- [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/)

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/iamrahul-l/react-todo-app.git
   cd react-todo-app
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Start the development server:
   ```bash
   npm start
   ```
4. Open your browser and navigate to `http://localhost:3000`.

---

## Usage
1. On the homepage, click inside the input area to expand it.
2. Enter a title and content for your note.
3. Click the `+` button to add the note.
4. View all added notes displayed below the input area.
5. Click the delete icon on any note to remove it.

---

## Folder Structure
```
react-todo-app/
├── public/
│   ├── index.html
│   ├── manifest.json
│   └── favicon.ico
├── src/
│   ├── components/
│   │   ├── App.jsx
│   │   ├── CreateArea.jsx
│   │   ├── Footer.jsx
│   │   ├── Header.jsx
│   │   └── Note.jsx
│   ├── index.css
│   ├── index.js
│   └── styles.css
├── .gitignore
├── package.json
└── README.md
```

---

## Components
### `App`
- Manages the state of the notes and handles the addition and deletion logic.
- Renders `Header`, `CreateArea`, `Note`, and `Footer` components.

### `CreateArea`
- Contains input fields for creating a note.
- Expands the input field when clicked.
- Triggers `onAdd` to add a new note.

### `Note`
- Displays the title and content of a note.
- Contains a delete button to trigger `onDelete`.

### `Header`
- Displays the application title with a highlight icon.

### `Footer`
- Shows the current year in the footer.

---

## Dependencies
The project uses the following dependencies:
- **React**: Core library for building the UI.
- **Material-UI**: Provides icons and design components.
- **React-DOM**: Integration of React with the browser DOM.

Install these dependencies with:
```bash
npm install @mui/material @mui/icons-material react react-dom
```

---

## License
This project is licensed under the MIT License. See the LICENSE file for details.

---

For more details, visit the GitHub repository: [React Todo App](https://github.com/iamrahul-l/react-todo-app) Here’s a detailed explanation of the code in the project, section by section:

---

### 1. **App Component**

```javascript
import React, { useState } from "react";
import Header from "./Header";
import Footer from "./Footer";
import Note from "./Note";
import CreateArea from "./CreateArea";

function App() {
  const [notes, setNotes] = useState([]);

  function addNote(newNote) {
    setNotes(prevNotes => {
      return [...prevNotes, newNote];
    });
  }

  function deleteNote(id) {
    setNotes(prevNotes => {
      return prevNotes.filter((noteItem, index) => {
        return index !== id;
      });
    });
  }

  return (
    <div>
      <Header />
      <CreateArea onAdd={addNote} />
      {notes.map((noteItem, index) => {
        return (
          <Note
            key={index}
            id={index}
            title={noteItem.title}
            content={noteItem.content}
            onDelete={deleteNote}
          />
        );
      })}
      <Footer />
    </div>
  );
}

export default App;
```

#### Explanation:
- **`useState([])`**: A state hook initializes an empty array to store the notes.
- **`addNote` Function**: Adds a new note to the array using the spread operator.
- **`deleteNote` Function**: Removes a note by filtering out the one with the matching `id`.
- **Rendering Notes**: The `notes` array is mapped to render a `Note` component for each item, passing `id`, `title`, and `content` as props.
- **Components**: Includes `Header`, `Footer`, `CreateArea` (for input), and `Note` (for displaying each note).

---

### 2. **CreateArea Component**

```javascript
import React, { useState } from "react";
import AddIcon from "@mui/icons-material/Add";
import { Fab } from "@mui/material";
import { Zoom } from "@mui/material";

function CreateArea(props) {
  const [zoom, zoomout] = useState(false)

  const [note, setNote] = useState({
    title: "",
    content: ""
  });

  function handleChange(event) {
    const { name, value } = event.target;

    setNote(prevNote => {
      return {
        ...prevNote,
        [name]: value
      };
    });
  }

  function submitNote(event) {
    props.onAdd(note);
    setNote({
      title: "",
      content: ""
    });
    event.preventDefault();
  }

  function zoomer() {
    zoomout(true);
  }

  return (
    <div>
      <form className="create-note">
        {zoom && (<input
          name="title"
          onChange={handleChange}
          value={note.title}
          placeholder="Title"
        />)}

        <textarea
          name="content"
          onChange={handleChange}
          value={note.content}
          placeholder="Take a note..."
          rows={zoom ? 3 : 1}
          onClick={zoomer}
        />
        <Zoom in={zoom}>
          <Fab onClick={submitNote}><AddIcon /></Fab>
        </Zoom>
      </form>
    </div>
  );
}

export default CreateArea;
```

#### Explanation:
- **State Management**:
  - `zoom`: Tracks whether the input area should expand.
  - `note`: Stores the title and content of the current note.
- **`handleChange` Function**:
  - Dynamically updates the `note` state based on the input field that triggered the event.
  - Uses destructuring to access `name` and `value`.
- **`submitNote` Function**:
  - Sends the `note` to the `onAdd` prop (from `App`).
  - Resets the `note` state to empty.
- **Zoom and FAB (Floating Action Button)**:
  - Expands the input field when clicked and enables the submit button.
  - `Zoom` and `Fab` are Material-UI components for animations and buttons.

---

### 3. **Header Component**

```javascript
import React from "react";
import HighlightIcon from "@mui/icons-material/Highlight";

function Header() {
  return (
    <header>
      <h1><HighlightIcon />Keeper</h1>
    </header>
  );
}

export default Header;
```

#### Explanation:
- Displays the app's header with a title and an icon (`HighlightIcon` from Material-UI).
- Uses `<header>` to semantically indicate the top section of the page.

---

### 4. **Footer Component**

```javascript
import React from "react";

function Footer() {
  const year = new Date().getFullYear();
  return (
    <footer>
      <p>Copyright ⓒ {year}</p>
    </footer>
  );
}

export default Footer;
```

#### Explanation:
- Dynamically displays the current year using JavaScript’s `Date` object.
- Renders a simple copyright footer.

---

### 5. **Note Component**

```javascript
import React from "react";
import DeleteIcon from "@mui/icons-material/Delete";
import { Fab } from "@mui/material";

function Note(props) {
  function handleClick() {
    props.onDelete(props.id);
  }

  return (
    <div className="note">
      <h1>{props.title}</h1>
      <p>{props.content}</p>
      <Fab onClick={handleClick}><DeleteIcon /></Fab>
    </div>
  );
}

export default Note;
```

#### Explanation:
- Accepts `title`, `content`, `id`, and `onDelete` as props.
- Displays the note content and includes a delete button.
- **`handleClick` Function**:
  - Calls the `onDelete` function with the note's `id`, triggering the deletion in the parent (`App`).

---

### 6. **Index.js**

```javascript
import React from "react";
import ReactDOM from "react-dom";
import App from "./components/App";

ReactDOM.render(<App />, document.getElementById("root"));
```

#### Explanation:
- The entry point of the application.
- Renders the `App` component inside the `div` with an ID of `root` (defined in `public/index.html`).

---

### 7. **Styling**
The project uses CSS for styling:
- **`index.css`**: Includes global styles.
- **`styles.css`**: Adds custom styles for specific components (e.g., `.create-note`, `.note`).

---

This modular structure ensures that the app is easy to maintain and scale. Each component handles a specific task, and all state management is centralized in the `App` component.
