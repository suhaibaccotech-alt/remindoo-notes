You're helping me set up a private GitHub repo for my Obsidian notes vault on a Windows work PC, so that Claude's scheduled runs for Remindoo PM can read my notes without my PC being on. Walk me through it one step at a time: give me one step, wait until I say "done" or paste an error, then give the next. Keep each step short, with exact clicks and commands.

My setup
- Windows work PC with NO admin rights. Nothing can be installed system-wide; everything goes in my user folder.
- Vault folder: <VAULT PATH, e.g. C:\Users\<me>\Desktop\Notes>
- Obsidian is already installed. The Obsidian Git plugin may already be installed.
- The company-provisioned Google account is used for everything. My GitHub account uses my company email: <COMPANY EMAIL>.
- Repo: a private repo in the company GitHub org, created by the org admin (Sami): <REPO URL, e.g. https://github.com/remindoo-org/remindoo-notes-<name>>. If it doesn't exist yet, stop at that step and give me a short message to send to Sami asking for it: private, empty, no README, me with write access.

Rules
- Never ask me to paste passwords, tokens or the contents of credential notes into chat.
- Nothing is pushed until we've checked the exact file list together and I've confirmed there are no credentials or personal notes in it.
- If anything that shouldn't be there was already pushed to GitHub, stop and tell me: it needs the history rewritten and the exposed credentials changed.

Steps, in this order
1. Clean the vault first. Credential notes (passwords, test logins, API keys) go into Google Password Manager on the company account and are deleted from the vault. Notes that aren't about Remindoo leave the vault. Anything private that has to stay goes in a "Private" folder at the vault root.
2. Portable Git. Download the 64-bit "Portable (thumbdrive edition)" from the Windows download page on git-scm.com, run it, and extract it to %USERPROFILE%\PortableGit. Check it: open PortableGit\git-bash.exe and run git --version.
3. In git-bash, set my identity: git config --global user.name "<NAME>", git config --global user.email "<COMPANY EMAIL>", and git config --global core.autocrlf true.
4. Check for an existing repo. If <VAULT>\.git exists, show me how to check what was committed and whether it was pushed (git log --oneline, git remote -v). No remote: delete the .git folder (View → Show → Hidden items in File Explorer) and start fresh. A remote that was pushed to: stop (see Rules).
5. Create <VAULT>\.gitignore with exactly this content (skip it if one already exists with the same content):

   # Remindoo PM notes repo: what stays on this PC.
   # This file is pushed too, so never list a private note by name here.
   Private/
   Obsidian/
   .obsidian/workspace.json
   .obsidian/workspace-mobile.json
   .obsidian/cache/
   .trash/
   Notes/.obsidian/
   Notes/Backups/
   Notes/Pic Storage/
   *.png
   *.jpg
   *.jpeg
   *.gif
   *.webp
   Thumbs.db
   desktop.ini
   Joplin/locks/
   Joplin/temp/

6. Initialize and review. In git-bash, cd into the vault (the /c/Users/... form of the path), then run git init -b main, git add . and git status --short. Help me scan the list: no Private/, no Obsidian/ program files, no images, nothing that looks like a password or login note. Show me how to unstage a file (git rm --cached <file>) and add it to .gitignore if something slipped in. Only then commit: git commit -m "Initial vault import".
7. Connect GitHub: git remote add origin <REPO URL>, then git push -u origin main. Git Credential Manager, which comes with Portable Git, opens a browser sign-in on the first push; I sign in with my company GitHub account. Then we check the file list on GitHub in the browser.
8. Obsidian Git plugin. If it's missing, install "Git" by Vinzent03 from Settings → Community plugins. In its settings: Custom Git binary path = C:\Users\<me>\PortableGit\cmd\git.exe (write it out with my real user name), auto commit-and-sync interval 10 minutes, pull on startup on, commit message "vault backup: {{date}}". Restart Obsidian.
9. Joplin, only if I use it for handwritten notes: in Joplin, go to Tools → Options → Synchronisation, set the target to "File system" and the directory to <VAULT>\Joplin, then run Synchronise once. Check with git status that the Joplin folder's notes and drawings appear, and that nothing private is in them.
10. Test: edit a note, wait for the next auto commit-and-sync (or run "Git: Commit-and-sync" from Ctrl+P), and confirm the change shows on GitHub.
11. Hand-off: give me a short message to send to the PM (dev1@remindoo.co) with the repo URL and the date it went live, so the sweeps can be pointed at it.

Have fixes ready for: "git not found" in Obsidian (wrong binary path), no browser sign-in appearing (company proxy or pop-up blocked), push rejected because the GitHub repo isn't empty, merge conflicts after editing on two devices, and line-ending warnings.
