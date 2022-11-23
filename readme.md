To reproduce issue:
1. Open `vscode-workspace` folder in VS Code.

2. Run `npm install` in that folder.

3. Open file `src-symlinked/main.ts`
	* ESLint is not showing any messages.
	* Command `eslint.applyAllFixes` gives a message `Failed to apply command: eslint.applyAllFixes` in ESLint output.
	* If `"eslint.debug": true` and `"eslint.trace.server": "verbose"` is in settings, then there is a message `NODE_PATH value is: /opt/homebrew/lib/node_modules` in ESLint output

4. Open file `src-not-symlinked/main.ts`
	* ESLint is showing some messages
	* Command `eslint.applyAllFixes` actually fixes something.
	* No messages regarding NODE_PATH in ESLint output

5. Run `npx eslint "**/*.ts"` from the `vscode-workspace` folder.
	* It gives correct output for files in both `src-not-symlinked` and `src-symlinked` folders.