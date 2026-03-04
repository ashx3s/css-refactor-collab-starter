# The Aristocats Fan Page — CSS Audit & Git Collaboration Lab

## Team Members

- [Autum Darrell](https://github.com/BreezyAutum)
- [Ashlyn Knox](https://github.com/ashx3s/)

---

## Lab Instructions

### Learning Objectives

By the end of this lab you should be able to:

- Set up a shared GitHub repository and collaborate with teammates using push and pull workflows.
- Read and evaluate CSS critically, identifying common problems like duplication, poor formatting, and fragile patterns.
- Write clear GitHub Issues with a definition of done.
- Make targeted improvements to CSS across a multi-file codebase.

---

### Part 1: Repository Setup

**One team member** (the repo owner) completes Steps 1–3. Everyone else waits until Step 4.

1. Create a new **public** repository on GitHub. Do **not** initialize it with a README (we are providing one).
2. Download and unzip the starter files. Initialize the folder as a git repo, commit the starter files, and push them to your new repository.
3. Add your teammates as **Collaborators** under the repository's **Settings** tab.
4. **Everyone** clones the repository and opens it in VS Code.

---

### Part 2: The README Round-Robin

Before touching any code, your team is going to practice the push/pull cycle with a low-stakes task: adding your names to the README.

#### How This Works

You will go **one at a time**. Agree on an order before starting.

**The person whose turn it is:**

1. Open `README.md`.
2. Delete the example line and add your name as a Markdown link to your GitHub profile:
   ```markdown
   - [Your Name](https://github.com/your-username)
   ```
3. Save, stage, commit with a message like `Add [your name] to README`, and push.

**Everyone else on the team:**

1. Pull the latest changes.
2. Open `README.md` and confirm the new name is there.
3. Once everyone has confirmed, the **next person** takes their turn.

Repeat until every team member's name is in the README.

> **Why are we doing this?** This exercise builds the muscle memory of the push → pull → verify cycle. It also confirms that everyone's access and setup is working before you start editing CSS.

---

### Part 3: The CSS Audit

Now open the project and spend time reading through the code together. Open `index.html` and `contact.html` in a browser (right-click the file → **Open with Live Server** if you have the extension, or just double-click to open in your browser).

Look at the site. Then look at the code. Your goal is to find problems.

#### What to Look For

Here are the categories of problems hiding in this codebase. You don't need to find every single one, but you should find issues in most of these categories:

**Incomplete implementations** — Look for `TODO` and `FIXME` comments in the CSS files. These mark things that were left unfinished. Read them carefully; they tell you what needs to be done.

**Overly verbose or redundant CSS** — Are there rules that could be combined? Properties repeated across multiple selectors that are doing the same thing? Look for copy-paste patterns.

**Duplicate rules across files** — The same class name can be defined in more than one CSS file. This isn't always wrong, but it can cause confusion and unexpected results depending on which file loads last. When you find a class defined in two places, talk with your team: should they be merged? Does one definition belong in a different file? What should be kept and what should go?

**AI-generated code smell** — Comments that just restate what the CSS already says add noise and make the code harder to read. A comment like `/* removes bullet points */` above `list-style: none` isn't helping anyone.

**Student-style mistakes** — Inconsistent indentation, messy formatting, selectors that are more specific than they need to be, and styles that are fragile (like fixed pixel heights on containers with dynamic content).

**Accessibility and usability gaps** — Is the text easy to read against its background? Do interactive elements look and behave like interactive elements? Can you tell what's clickable?

**Responsive design gaps** — Open the site on a narrow browser window or use your browser's device emulation (DevTools → toggle device toolbar). Does the layout break? Are there grids that stay in multiple columns when they shouldn't? Text or elements that overflow the screen? Fixing these usually means adding a media query — but first you have to notice the problem.

**Design system disconnects** — Are colours hardcoded throughout the files when they could be defined once as a CSS custom property? Look for the same hex value appearing over and over. Centralising these makes future changes much easier.

#### Tips

- Open each CSS file and read it top to bottom. Don't skim.
- Have the site open in the browser beside your editor so you can see what each rule is doing.
- Use your browser's developer tools (right-click → **Inspect**) to experiment with changes before committing to them.
- Talk to your teammates. "Does this look right to you?" is a great question.
- You are welcome to ask AI to help you understand what a piece of CSS is doing or to clarify your thinking about an issue. But the audit itself — the reading, the evaluating, the deciding what matters — that's your work.

---

### Part 4: Writing Issues

For each problem your team identifies, create a **GitHub Issue** in your repository.

1. Go to the **Issues** tab on your repository's GitHub page.
2. Click **New issue**.
3. Give it a clear, specific title (e.g., "Replace hardcoded colours with CSS custom properties in theme.css").
4. In the description, include:
   - **What the problem is** — describe it in your own words.
   - **Where it is** — which file(s) and what section of the file.
   - **Definition of done** — how will you know this issue is resolved? Be specific. For example: "All colour values in `components.css` reference custom properties from `:root` instead of hex codes."
5. **Assign** the issue to the team member who will work on it.

#### How Many Issues?

Aim for at least **one issue per team member**, but your audit will likely turn up more than that. Prioritize the ones that make the biggest difference to code quality. If you have time, tackle more.

> **A note on scope:** The HTML content should remain untouched. You may add structural elements like wrapper `<div>`s or new classes to support your CSS changes, but don't change the text, headings, or page structure.

---

### Part 5: Making Changes

Now that your issues are documented and assigned, start working.

#### The Workflow

1. **Pull** before you start working to make sure you have the latest code.
2. Work on **your assigned file(s)**. Because the CSS is split across multiple files, you and your teammates should be able to work in parallel most of the time.
3. When you've completed a fix, stage, commit, and push. Reference the issue number in your commit message: e.g., `Fix form input duplication (closes #3)`.
4. Let your team know you've pushed. Everyone should **pull** and verify.
5. Once an issue is resolved, **close it** on GitHub.

#### Writing Good Commit Messages

A good commit message is short and says _what changed and why_:

- ✅ `Group heading selectors in fonts.css`
- ✅ `Add hover and focus states to buttons (closes #5)`
- ✅ `Replace hardcoded hex colours with custom properties`
- ❌ `Fixed stuff`
- ❌ `Update components.css`
- ❌ `asdfasdf`

#### Communicate With Your Team

Before you start editing, tell your teammates which file you're working in. A quick "I'm in `components.css`" goes a long way toward avoiding conflicts.

---

### When You Hit a Merge Conflict

If you push and get an error, or if you pull and VS Code shows you a file with conflict markers, don't panic. This is normal and expected when multiple people edit the same file.

#### What a Conflict Looks Like

You'll see something like this in the file:

```
<<<<<<< HEAD
Your version of the code
=======
Your teammate's version of the code
>>>>>>> abc123
```

#### What to Do

1. **Read both versions.** Understand what you changed and what your teammate changed.
2. **Decide what the final version should be.** Sometimes you keep yours, sometimes theirs, sometimes you combine both. Talk to your teammate if you're unsure.
3. **Delete the conflict markers** (`<<<<<<<`, `=======`, `>>>>>>>`) and leave only the code you want to keep.
4. Stage, commit, and push with a message like `Resolve merge conflict in components.css`.

> **Instructor tip:** If you get stuck on a conflict, raise your hand. Conflicts are a normal part of collaboration and working through them is part of the learning.

---

### Self-Assessment Checklist

Before you wrap up, go through this checklist individually. Be honest with yourself — this isn't graded, it's for you.

#### Collaboration

- [ ] I pulled changes from my teammates before starting my own work.
- [ ] I communicated with my team about which files I was working in.
- [ ] I wrote clear, descriptive commit messages.
- [ ] I pushed my work and confirmed my teammates could pull it.
- [ ] If I encountered a merge conflict, I worked through it rather than avoiding it.

#### Code Audit

- [ ] I read through the CSS files carefully rather than skimming.
- [ ] I identified at least one problem that wasn't flagged by a `TODO` or `FIXME` comment.
- [ ] I used the browser's developer tools to test or investigate at least one issue.
- [ ] I could explain _why_ something was a problem, not just that it looked wrong.

#### GitHub Issues

- [ ] I contributed to writing at least one issue.
- [ ] My issues had a clear, specific title.
- [ ] My issues included a definition of done that someone else could understand.

#### Implementation

- [ ] I completed at least one fix and pushed it to the repository.
- [ ] My fix addressed the issue I was assigned without introducing new problems.
- [ ] I tested my changes in the browser to confirm they worked.

#### Reflection

- [ ] I learned something new about CSS that I didn't know before this lab.
- [ ] I feel more comfortable with the push/pull workflow than I did at the start.
- [ ] I could explain to someone outside my team what makes "bad" CSS bad.

---

### Debrief Conversation

- Sit down with 1 other group and discuss the issues that you flagged
  - Why did you flag it as a problem?
  - How did the code benefit from your changes?
  - What did you learn from this issue?
  - Were there any challenges that trying to fix this brought up? how did you handle them?
- Give each person a change to talk about a change they made

---

## Project File Structure

```
├── index.html          ← Home page
├── contact.html        ← Contact page
├── README.md           ← This file
└── css/
    ├── fonts.css       ← Typography styles
    ├── layout.css      ← Page structure, containers, sections
    └── components.css  ← Buttons, cards, forms, and other UI components
```

---

> **Note:** This starter codebase was developed in collaboration with [Claude Code](https://claude.ai/claude-code) and intentionally contains simulated errors and problems for audit practice.

Hello everyone :)