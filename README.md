# Quiz CLI

## Project Overview

Quiz CLI is a small Node.js command-line application that runs an interactive programming quiz in the terminal. It is designed as a beginner-friendly example of building a CLI app with modern JavaScript and Node.js built-in APIs.

The application loads quiz data from a JSON file, lets the user choose a category and question count, asks multiple-choice questions interactively, tracks progress and score, and shows a final summary with a review of incorrect answers.

This project is best suited for:

- Beginners learning Node.js and ES Modules
- Developers exploring terminal-based application structure
- Learners who want a simple JavaScript-focused quiz game

At a high level, the application consists of:

- An entry point that loads quiz data and manages the replay loop
- Input helpers for terminal prompts and menu selection
- A quiz engine class that handles question flow, scoring, and results
- A JSON dataset containing quiz categories and questions

## Features

- Interactive terminal quiz experience
- Category selection before starting a quiz
- Configurable question count per session
- Multiple-choice questions with numbered answers
- Shuffled question order for replayability
- Progress bar during quiz execution
- Score tracking and percentage-based final summary
- Immediate answer feedback
- Optional explanations shown after each question
- Review section for incorrect answers
- Replay loop to start another quiz without restarting the program
- No external runtime dependencies

## Technologies Used

- Node.js
- JavaScript (ES Modules)
- JSON for quiz data storage
- Built-in Node.js APIs:
  - `node:fs/promises`
  - `node:path`
  - `node:url`
  - `node:readline`
- ANSI escape codes for terminal colors

## Project Structure

```text
.
├── data/
│   └── questions.json
├── src/
│   ├── colors.js
│   ├── input.js
│   └── quiz.js
├── index.js
└── package.json
```

## Prerequisites

- Node.js 18.0.0 or later
- A terminal that supports standard ANSI color output

## Installation

1. Clone the repository:

   ```bash
   git clone https://git.epam.com/bhavana_u/test-app.git
   ```

2. Move into the project directory:

   ```bash
   cd test-app
   ```

3. Install dependencies:

   This project does not use any external npm packages, so there is nothing additional to install after cloning.

## Setup Instructions

No environment variables or external services are required.

Before running the application, ensure that:

- You are using Node.js 18 or newer
- The repository files remain in their expected locations
- `data/questions.json` contains valid JSON

## Configuration

This project has no `.env` file, deployment configuration, or runtime configuration layer.

The main configurable content is the quiz dataset stored in:

- `data/questions.json`

The application reads this file at runtime and uses it to build category menus and question sets.

## Usage

Run the application with:

```bash
npm start
```

This executes:

```bash
node index.js
```

### How it works

1. The application displays a welcome banner.
2. You choose one of the available quiz categories.
3. You select how many questions to answer.
4. The quiz starts and displays one question at a time.
5. You enter the number matching your selected answer.
6. The app immediately tells you whether your answer is correct.
7. If available, an explanation is shown for the question.
8. After all questions are answered, a final results summary is displayed.
9. Incorrect answers are listed again for review.
10. You can choose to play another round.

### Available categories

The current question bank includes 3 categories:

- JavaScript Basics
- Node.js Fundamentals
- General Programming

There are currently 15 total questions in the repository, with 5 questions in each category.

### Example interaction

```text
Choose a category:

  1. JavaScript Basics
  2. Node.js Fundamentals
  3. General Programming

Your choice (enter number): 1

How many questions?

  1. All questions
  2. 3 questions
  3. 5 questions

Your choice (enter number): 3

Starting quiz...
Select your answer by entering the number.

[░░░░░░░░░░░░░░░░░░░░░░░░░░░░] 0%
Question 1 of 5

What keyword is used to declare a constant in JavaScript?

  1. var
  2. let
  3. const
  4. define
```

## Available Scripts

The following npm scripts are defined in `package.json`:

| Script | Command | Description |
| --- | --- | --- |
| `npm start` | `node index.js` | Starts the interactive quiz application |
| `npm test` | `node --test` | Runs Node.js tests if test files are added |

### Note about tests

A `test` script is present, but no visible test files are currently included in the repository tree.

## Data Format / How to Add Questions

Quiz content is stored in `data/questions.json`.

### Current structure

The file contains a top-level `categories` object. Each category entry includes:

- `name`: Display name shown to the user
- `questions`: An array of question objects

Each question object contains:

- `question`: The question text
- `options`: An array of answer choices
- `answer`: Zero-based index of the correct option
- `explanation`: Optional explanatory text displayed after answering

### Example question format

```json
{
  "question": "What does JSON stand for?",
  "options": [
    "JavaScript Object Notation",
    "Java Standard Object Notation",
    "JavaScript Online Notation",
    "Java Serialized Object Notation"
  ],
  "answer": 0,
  "explanation": "JSON (JavaScript Object Notation) is a lightweight data interchange format."
}
```

### Adding a new category

Add a new entry under `categories` using a unique key:

```json
{
  "categories": {
    "your-category-key": {
      "name": "Your Category Name",
      "questions": []
    }
  }
}
```

### Adding new questions safely

When editing `data/questions.json`:

- Keep the file valid JSON
- Ensure `options` is an array of possible answers
- Ensure `answer` matches the correct option index in `options`
- Keep question wording and explanations clear for terminal display
- Add enough questions if you want the `3 questions` and `5 questions` menu options to remain meaningful for a category

## File Structure

### `index.js`

Application entry point. It:

- Resolves the current module directory in an ES Module environment
- Loads `data/questions.json`
- Displays the banner
- Handles category and question-count selection
- Starts the quiz loop
- Repeats the game when the user chooses to play again

### `src/quiz.js`

Contains the `Quiz` class and core quiz logic, including:

- Shuffling questions using the Fisher-Yates algorithm
- Tracking current question index
- Recording answers and score
- Rendering a progress bar
- Showing result summaries and incorrect answer review

### `src/input.js`

Provides terminal input helpers built on Node.js `readline`, including:

- `createInterface()`
- `prompt()`
- `select()`
- `confirm()`
- `pressEnter()`

### `src/colors.js`

Defines ANSI color helpers for styled terminal output without external libraries.

### `data/questions.json`

Stores all quiz categories, questions, answers, and explanations.

### `package.json`

Defines the package metadata, npm scripts, Node.js engine requirement, and project license.

## Relevant Notes and Limitations

- The application is terminal-based only; there is no web UI.
- It currently relies entirely on the local JSON question file.
- The question count menu supports `All questions`, `3 questions`, and `5 questions` based on how many questions exist in the selected category.
- Question order is shuffled when a quiz instance is created.
- No external npm dependencies are used.
- No Docker, CI/CD, environment-variable configuration, or deployment files were found.
- Error handling is present for startup/runtime failures, and the app exits with a non-zero status on fatal errors.

## Contributing

No dedicated contribution guidelines or contributing files were found in the repository.

If you want to contribute, useful areas include:

- Adding more quiz categories
- Expanding the question bank
- Adding automated tests for the quiz logic and input helpers
- Improving terminal UX and accessibility

## License

This project is licensed under the MIT License.
