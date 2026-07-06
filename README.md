# Quiz CLI

Quiz CLI is an interactive command-line quiz game built with Node.js and ES modules. It lets players choose a category, answer multiple-choice questions, and review their score at the end of each session.

## Overview

This project is a lightweight educational CLI application designed to demonstrate core JavaScript and Node.js concepts through a playable quiz experience. It includes a simple prompt-driven interface, colorized terminal output, JSON-based question storage, and modular source code that is easy to extend.

## Features

- Interactive command-line quiz flow
- Multiple quiz categories loaded from JSON data
- Configurable question counts based on category size
- Shuffled question order for replayability
- Score summary and answer review after each quiz
- Colorized terminal output with no external runtime dependencies
- ES module-based project structure
- Easy-to-edit question bank in `data/questions.json`

## Requirements

- Node.js 18 or later
- npm (bundled with Node.js)

## Installation

1. Clone the repository:
   - `git clone https://git.epam.com/bhavana_u/test-app.git`
2. Change into the project directory:
   - `cd test-app`
3. Install dependencies:
   - `npm install`

## Setup Instructions

This project does not require environment variables or external services.

To prepare the application:

1. Ensure Node.js 18+ is installed.
2. Run `npm install` to initialize the project.
3. Confirm that `data/questions.json` is present and contains at least one category with questions.

## Usage

Start the quiz from the project root:

- `npm start`

Alternatively, run the entry point directly:

- `node index.js`

During execution, you can:

1. Select a quiz category.
2. Choose how many questions to answer.
3. Enter the number corresponding to your selected answer.
4. Review your final score and incorrect answers.
5. Choose whether to play again.

## Example Interaction

```text
$ npm start

Choose a category:
  1. JavaScript Basics
  2. Node.js Fundamentals
  3. General Programming

Your choice (enter number): 2

How many questions?
  1. All questions
  2. 3 questions
  3. 5 questions

Your choice (enter number): 2

Starting quiz...

Question 1 of 3
What is the Node.js event loop?
  1. A for loop
  2. A mechanism for handling async operations
  3. A debugging tool
  4. A package manager

Your choice (enter number): 2
✓ Correct!
```

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
├── package.json
└── README.md
```

## Data Format and How to Add Questions

Questions are stored in `data/questions.json` using category-based JSON objects.

Each category contains:

- `name`: display name shown in the CLI
- `questions`: array of question objects

Each question object should include:

- `question`: the prompt shown to the player
- `options`: an array of answer choices
- `answer`: the zero-based index of the correct option
- `explanation`: optional explanation displayed after answering

Example structure:

```json
{
  "categories": {
    "javascript": {
      "name": "JavaScript Basics",
      "questions": [
        {
          "question": "What keyword is used to declare a constant in JavaScript?",
          "options": ["var", "let", "const", "define"],
          "answer": 2,
          "explanation": "The 'const' keyword declares a constant."
        }
      ]
    }
  }
}
```

To add new questions:

1. Open `data/questions.json`.
2. Add a new question object to an existing category, or create a new category entry.
3. Ensure the `answer` value matches the correct option index.
4. Save the file and rerun the CLI.

## npm Scripts

- `npm start` — runs the quiz application
- `npm test` — runs the Node.js test command configured for the project

## Notes and Limitations

- The app currently reads questions from a local JSON file only.
- There is no persistence for player history or scores.
- The question count options are currently limited to all questions, 3 questions, or 5 questions when available.
- The application is designed for interactive terminal use and is not intended for browser execution.
- No automated tests are currently included beyond the configured test command.

## Contributing

Contributions are welcome.

Suggested workflow:

1. Fork or branch from the repository.
2. Make focused changes.
3. Test the application locally with `npm start`.
4. Update documentation when behavior or structure changes.
5. Open a pull request for review.

## License

This project is licensed under the MIT License. See `package.json` for the declared license.
