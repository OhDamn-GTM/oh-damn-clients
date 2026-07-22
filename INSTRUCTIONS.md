# How to use it


- **`main`** = the blank starter template (do not fill this in for a real client)
- **A client branch** = a copy of that template for one client (e.g. `acme`, `fortay`)
- **Commit** = save a snapshot of your changes
- **Push** = upload your saves to the shared remote (GitHub / GitLab / etc.)

Open **Terminal** (Mac) or **Command Prompt / PowerShell** (Windows), then go into this project:

```bash
cd path/to/oh-damn-clients
```

Replace `path/to/oh-damn-clients` with the real folder location on your computer.

---

## 1. First time setup (once)

After someone shares the remote URL with you:

```bash
git clone YOUR-REMOTE-URL oh-damn-clients
cd oh-damn-clients
```

If the folder already exists on your machine and Git is already set up, you can skip cloning and just `cd` into it.

---

## 2. Start a new client

Always start from the clean template (`main`), then create a branch named after the client.

```bash
git checkout main
git pull
git checkout -b client-name
```

**Examples:**
- `git checkout -b acme`
- `git checkout -b fortay-connect`

Use lowercase letters and hyphens. Avoid spaces in the branch name.

Then fill in `README.md` and the folders for that client.

---

## 3. Switch to an existing client

```bash
git checkout client-name
git pull
```

**Example:** `git checkout acme`

---

## 4. See which client you are on

```bash
git branch
```

The line with a `*` is your current branch.

---

## 5. Save your work (commit)

After you edit files:

```bash
git status
git add .
git commit -m "Short note about what you changed"
```

**Tips:**
- `git status` shows what changed — run it anytime you feel unsure
- Write a clear message, e.g. `"Add POC contacts"` or `"Upload logo assets"`

---

## 6. Upload your work (push)

**First time pushing a new client branch:**

```bash
git push -u origin client-name
```

**Later saves on that same client:**

```bash
git push
```

---

## 7. Get the latest changes from others

```bash
git pull
```

Do this when you start work, especially if teammates edit the same client.

---

## 8. Go back to the blank template

```bash
git checkout main
```

Only create new clients from `main`. Do not put real client files on `main`.

---

## Cheat sheet

| What you want | Command |
| --- | --- |
| Open the project | `cd path/to/oh-damn-clients` |
| See current client | `git branch` |
| Use blank template | `git checkout main` |
| New client | `git checkout main` then `git checkout -b client-name` |
| Open existing client | `git checkout client-name` |
| What changed? | `git status` |
| Save work | `git add .` then `git commit -m "your note"` |
| Upload | `git push` (first time: `git push -u origin client-name`) |
| Download latest | `git pull` |

---

## Common mistakes

1. **Editing on `main`** — switch to a client branch first (`git checkout client-name` or create one).
2. **Forgetting to save** — changes are only shared after `commit` and `push`.
3. **Spaces in branch names** — use `acme-corp`, not `acme corp`.
4. **Wrong folder** — run commands inside `oh-damn-clients`, not a parent folder.

---

## Need help?

If a command errors, copy the full message and send it to whoever manages this archive. Also run `git status` and `git branch` and share that output — it shows where you are and what is unfinished.
