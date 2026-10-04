# Repository instructions

## Project and validation

- The quiz is a dependency-free static page. Open `index.html` directly in a browser or the integrated browser; no server or build step is required.
- There is no package manifest, build/lint configuration, or automated test suite, so there are no repository-defined build, lint, or single-test commands.
- For a focused manual smoke test, open `index.html`, use Tab and Enter to answer a question correctly and another incorrectly, check the score, answer through question 10, then restart from the results screen. Check both light and dark system color schemes when changing styles.

## Architecture

- `index.html` contains the entire app: semantic page markup, inline CSS, the question dataset, and the quiz controller. Keep the app self-contained and avoid adding runtime or asset dependencies unless the project direction changes.
- The `questions` array is the source of quiz content. Each entry contains a category, question, four options, a zero-based correct `answer` index, and an explanatory `fact`.
- The controller maintains `currentQuestion`, `score`, and `answered`. `renderQuestion()` updates the question and progress; `chooseAnswer()` locks choices, scores the response, and displays feedback; `showResults()` presents the final score and reaction; `restart()` resets the quiz.
- CSS custom properties in `:root` define the light palette. The `prefers-color-scheme: dark` rule overrides those tokens; responsive and reduced-motion behavior is handled in media queries in the same stylesheet.

## Codebase conventions

- Keep markup, styles, data, and controller code in `index.html`; follow its two-space indentation and existing selector/function naming patterns.
- Preserve the question data shape and zero-based answer indexing when editing or adding quiz content. The displayed progress value is one-based, while score counts correct answers.
- Keep interactive choices and controls as native buttons. Maintain visible keyboard focus, move focus to the next action after an answer and to the first answer after advancing, and retain the live feedback and progress-bar semantics.
- Use the existing CSS custom properties for theme-sensitive colors and provide corresponding dark-theme values for any new palette tokens. Keep animations compatible with the reduced-motion media query.
