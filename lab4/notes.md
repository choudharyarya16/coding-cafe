# Lab 4 — Git & GitHub

## Question 1
`--global` saves the setting in my user-wide config file (`~/.gitconfig`), so it applies to every repository on this computer. Without it, Git writes to the current repository's own `.git/config`, so the setting only applies to that one repo. Outside a repo, that command fails.

## Question 2
A hidden folder called `.git` appeared. It is the repository itself: it holds `HEAD`, `config`, `description`, `hooks`, `info`, `objects` and `refs`, which together store every commit, branch and setting. That's why you must never edit or delete it.

## Question 3
Git offered only about five top-level items: `README.md` and my lab folders. It shows each untracked folder as one line, not every file inside it. `.venv` (about 900 files of other people's code) was not listed, because Python 3.13's `venv` creates its own `.gitignore` inside `.venv`. With an older Python, `.venv/` would have shown up there.

## Question 4
For me nothing disappeared, because Python had already hidden `.venv`. The only change was that `.gitignore` itself appeared as a new untracked file. On a setup where `.venv/` was listed, that line would vanish once `.gitignore` existed.

## Question 5
It should be committed. That way the ignore rules are saved in the history and shared with anyone who clones the repo. If it were ignored, other people's copies would not know to leave out `.venv`, `__pycache__` and so on.

## Question 6
`README.md` moved from **Untracked files** to **Changes to be committed**. In the three-places model it went from the working directory into the staging area (the index). It is now queued for the next commit but not saved in history yet.

## Question 7
Git printed a summary line with the branch, `(root-commit)`, the short hash and the message. Then it printed `6 files changed, 1702 insertions(+)` and one `create mode 100644 …` line per new file. So 6 files changed.

## Question 8
They are the short (abbreviated) commit hash, e.g. `19b93cb`. The full hash is a unique ID worked out from the commit's contents. The first seven characters are almost always enough to point to one exact commit, for example in `git show 19b93cb`.

## Question 9
1. Edit files in the working directory.
2. Check what changed with `git status`.
3. Stage the changes with `git add`.
4. Save them to history with `git commit`.

## Question 10
`README.md` is the name that people and tools look for first. GitHub automatically renders the README in the top folder on the repository's front page. Keeping it at the root means it describes the whole project, not just one lab.

## Question 11
`gh auth login` signed me in through the browser and stored an access token on my computer. It also set up Git to use `gh` as its credential helper. When I push over HTTPS, Git gets that token automatically instead of asking for a password.

## Question 12
The file list and, under it, the rendered `README.md` with my name and the contents list. GitHub always shows the root README on a repo's front page, because it's the project's introduction and the first thing a visitor should read.

## Question 13
No. `git log --oneline` shows the same commits with the same hashes as before. Pushing only copies commits to GitHub and updates my local note of where `origin/main` is. It does not create or change any commits.

## Question 14
A private repository really exists on GitHub, with its files and full history. Only the owner and invited collaborators (like the TAs) can see it, and to everyone else it looks like a 404. A repository that doesn't exist has nothing to share at all: no files, no history, and no one can be invited to it.
