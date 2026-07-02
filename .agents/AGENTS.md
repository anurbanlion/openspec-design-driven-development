# Custom Agent Rules

## Git Guidelines
- Do NOT execute `git add`, `git commit`, `git push`, `git restore`, or any other commands that modify the Git index, staging area, or commit history, unless the user explicitly asks for it in the request.
- Always ask for confirmation or wait for direct instructions before staging or committing changes.
- Non-modifying Git commands (such as `git diff`, `git status`, `git log`, `git show`, etc.) are fully allowed.
- Follow the Conventional Commits pattern (`feat:`, `chore:`, `fix:`, etc.) for all commit messages.


