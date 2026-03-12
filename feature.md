## Important Rules
- [Git branch and worktree naming convention](./git-branch-worktree-naming-convention.md)
- For everything that needs to be tracked, it should be done so using a JSON state file called state.json
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

## Testing
- *NEVER* remove existing tests, this can create holes and loss in coverage of the codebase and introduce new bugs accidentally.
  - You can only repair or remove tests that are broken in and of themselves by asking the user first and explaining the situation.
- Add a few tests to help verify your functionality as you build the feature, once the feature
is complete according to the spec provided, then you should add more permutations of the tests to make sure you're covering different scenarios.
- Make sure to run all tests before saying you're finished to make sure you didn't break something else.
- Try to use built-in ways of testing and running containers as presented in tools like make (Makefile), npm package.json scripts, etc.

## Operating the codebase
- If there are collisions with running containers on the same ports when attempting to run tests/linting/etc, warn the user and pause and ask how they'd like to proceed, either with you shutting those other ones down to run yours, or waiting.

## Documentation and Reminders
- Make note of high level functionality you're adding in `.specs/`, this isn't detailed technical jargon,
it's higher level and readability should be for the business, not
technical employees. This `.specs/` directory should have multiple Markdown files, with each
one representing a high-level category, choose or add one that makes sense and then add a bullet
point for each feature that was added. DO NOT GO DEEP with the `.specs/`, stay business focused.
  - Example: <example>If you built a feature that adds reminders to users for their calendar events, you might write something in
`.specs/users.md` or `.specs/calendar.md`. You'd include no more than one line for a feature that small.</example>
- If there were notable or important decisions made during planning or building phases, then make note of those in `.specs/` as well
so that future development cycles and team members can be aware of them.
