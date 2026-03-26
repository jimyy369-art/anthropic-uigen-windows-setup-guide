# Windows Setup Notes for Anthropic UI Project  
*A beginner‑friendly guide to running the Anthropic UI Generator project on Windows without errors.*

This guide exists because the original course does not explain Windows‑specific issues, and many students run into problems with OneDrive, Prisma, Node, and environment variables. These notes walk you through the correct setup and explain why each step matters.

---

## 1. Move the project OUT of OneDrive (critical)
Do **not** run the project from Desktop, Documents, or OneDrive.  
These folders sync files and break tools like Prisma and Next.js.

Move the unzipped project to a safe folder such as:

```
C:\Users\<yourname>\Projects\uigen
```

---

## 2. Confirm Node and npm are installed correctly
Open Command Prompt or PowerShell and run:

```
node -v
npm -v
```

If both show version numbers, you're good.  
If not, install Node LTS from the official website.

---

## 3. Install dependencies
Inside the `uigen` folder, run:

```
npm run setup
```

If this fails, run these manually:

```
npm install
npx prisma generate
```

This installs everything and generates the Prisma client.

---

## 4. Fix Prisma errors (if they appear)
If you see errors like:

> Cannot resolve '@/generated/prisma'

Run:

```
npx prisma generate
```

Then restart the dev server.

---

## 5. Configure the `.env` file correctly
You have two options depending on whether you want real AI or static fake components.

### Option A — Static Mode (FREE)
Use this if you don’t have Anthropic credits:

```
ANTHROPIC_API_KEY=
```

Leave it empty.  
The app will generate **fake placeholder components**, which is enough for the course.

### Option B — Real AI Mode (requires credits)
If you *do* have credits:

```
ANTHROPIC_API_KEY=sk-ant-api03-...your-real-key...
```

Rules:
- No quotes  
- No spaces  
- No comments on the same line  
- Restart the dev server after editing

---

## 6. Restart the dev server
Stop the server:

```
CTRL + C
```

Start it again:

```
npm run dev
```

Then open:

```
http://localhost:3000
```

---

## 7. Understanding the two modes

### Static Mode (no key or no credits)
- App returns pre-written fake components  
- Works instantly  
- No Anthropic account needed  
- Perfect for following the course  

### Real AI Mode (valid key + credits)
- App sends real prompts to Anthropic  
- Generates real React components  
- Requires paid credits  
- If you have no credits, server logs show:  
  > "Your credit balance is too low"

---

## 8. Common Windows issues and why they happen

### OneDrive breaks file access  
It locks files and interferes with Prisma/Next.js.

### Prisma fails to generate  
Running `npx prisma generate` fixes it.

### `.env` formatting issues  
Windows treats `#` as a comment, so keys get ignored.

### Next.js file watchers struggle in synced folders  
Another reason to avoid OneDrive.

---

Useful commands:

```
claude read src/app/page.tsx
claude explain this file
claude edit src/components/Button.jsx
claude fix "preview not updating"
```

---

## End of Guide
This page covers everything needed to avoid the common Windows issues and get the Anthropic UI project running smoothly.# anthropic-uigen-windows-setup-guide
A clear, beginner-friendly guide for running the Anthropic UI Generator project on Windows 
