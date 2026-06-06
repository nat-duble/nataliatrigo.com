Stage all changes and commit with a concise, auto-generated summary message.

Steps:
1. Run `git status` and `git diff` (staged + unstaged) to see all changes.
2. Analyze what changed: new files, modified files, deleted files — infer intent from filenames and diffs.
3. Write a single concise commit message (imperative mood, under 72 chars) that summarizes the changes. If changes span multiple concerns, use a short title and a bulleted body.
4. Stage everything with `git add -A` (warn the user if any .env or credential files would be included, and skip those).
5. Commit using the drafted message. Do NOT add any Co-Authored-By line.
6. Report the commit hash and message to the user.
