## Important Rules
- Make a new branch on a worktree in (.worktrees/)
- For everything that needs to be tracked, it should be done so using a JSON state file called state.json.
- Answer the user's question directly, avoiding any elaboration, explanation, introduction, conclusion, or excessive details.
- Do not add additional code explanation summary unless requested by the user.
- You should minimize output tokens as much as possible while maintaining helpfulness, quality, and accuracy. Only
address the specific task at hand, avoiding tangential information unless absolutely critical for completing the request.
If you can answer in 1-3 sentences or a short paragraph, please do.

## Planning
- Understand what the user is requesting by reading the existing codebase and doing research.
- If you do not understand something, ask questions until you do understand it's relation to the codebase.
- Make sure to setup a list of everything you need to do, and track your state in a JSON file.
- Use subagents if you need to speed up the process.
- If the bug is small, don't over plan, that's a waste of time and tokens. Most bug fixes are small enough
that minimal to no planning is acceptable many times.

## Testing
- *NEVER* remove existing tests, this can create holes and loss in coverage of the codebase and introduce new bugs accidentally.
  - You can only repair or remove tests that are broken in and of themselves by asking the user first and explaining the situation.
- Add a few tests to help verify your bug exists, once the bug is fixed according to the spec provided, then you should add more
permutations of the tests to make sure you're covering different scenarios.
- Make sure to run all tests before saying you're finished to make sure you didn't break something else.
- Try to use built-in ways of testing and running containers as presented in tools like make (Makefile), npm package.json scripts, etc.

## Operating the codebase
- If there are collisions with running containers on the same ports when attempting to run tests/linting/etc, warn the user and pause and ask how they'd like to proceed, either with you shutting those other ones down to run yours, or waiting.

## Documentation and Reminders
- If the bug being fixed affects something already in `.specs/` then update it, this isn't
detailed technical jargon, it's higher level and readability should be for the business, not
technical employees. Since you're just fixing a bug, most of the time you may not need to update
or add anything in `.specs/`.
- If there were notable or important decisions made during planning or building phases and it affects
the `.specs/` that are outlined already, add clarification.
- The `.specs/` is not a list of bug fixes, so do not treat it as such.
