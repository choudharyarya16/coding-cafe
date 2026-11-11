`pwd` printed my home folder, `C:\Users\ARYA`, which is where PowerShell opens by default. It's an absolute path — the full location from the drive letter down
`ls -Force` also showed hidden items — files and folders whose names start with a dot or have the hidden attribute set — that plain `ls` skips by default.
The Mode column shows attribute flags for the item — for example `d-----` means it's a directory, and `-a----` means it's a regular file marked as archive (i.e. modified since last backup).
`coding-cafe\week02` is a **relative** path — it works because the shell resolves it from wherever you're currently standing (your home folder), and `coding-cafe` sits directly inside it, so no full drive path is needed.
First it **moved** `README-backup.md` into the `week01\` folder, then it **renamed** it from `README-backup.md` to `old-readme.md` — both done with the same `mv` command because moving and renaming are the same operation under the hood.
There are 11 folders on my PATH
 C:\Users\ARYA\AppData\Local\Python\bin...
 Our paths were different because Python can be installed in multiple ways — from python.org, the Microsoft Store, or Anaconda — and each installer puts Python in a different location on the machine.
 The shell said `pyton : The term 'pyton' is not recognized as the name of a cmdlet, function, script file, or operable program`. In my own words: the shell searched every folder listed on my PATH, found nothing named `pyton`, and gave up — it doesn't correct typos.4
 `.venv` starts with a dot, which marks it as hidden, so plain `ls` skips it by default — you need `ls -Force` to reveal hidden items, as we saw back in section 1.
 `(.venv)` appeared at the front of my prompt, indicating that the virtual environment is now active and any Python commands will use the version inside it.
 It's a different path — python now points inside `.venv\Scripts\` instead of the system Python. `Activate.ps1` prepended the venv's `Scripts` folder to the front of my PATH, so the shell finds that Python first and uses it instead of the global one.
 `requests` and its dependencies (`certifi`, `charset-normalizer`, `idna`, `urllib3`) appeared in the second list — these were installed by `pip install requests` and didn't exist in the clean venv before.
 Python points back to the same system path I wrote down in question 7 — `deactivate` removed `.venv\Scripts\` from the front of my PATH, so the shell goes back to finding the original system Python.
 `-Recurse` makes the command descend into all subfolders and act on their contents too, not just the top-level folder it was pointed at.
 Ctrl+C **interrupted and forcefully killed** the running process immediately, while Ctrl+Z signalled **end-of-input**, causing Python to exit cleanly on its own as if it reached the end of a file.