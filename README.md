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
