# NSBE UNL Website

> **University of Nebraska–Lincoln Chapter of the National Society of Black Engineers**

This repository powers the NSBE UNL website. It's built so a technically-inclined student can maintain the code, while non-technical board members can manage content (photos, leadership, events) through a simple web dashboard — **no coding required**.

---

## 📁 Repository Structure

```
nsbe-unl/
├── index.html              ← Main website (single page)
├── _data/
│   ├── site.json           ← Email, social links, stats, calendar ID (EDIT VIA CMS)
│   ├── leadership.json     ← Board members & photos (EDIT VIA CMS)
│   └── gallery.json        ← Photo gallery (EDIT VIA CMS)
├── admin/
│   ├── index.html          ← Decap CMS admin interface
│   └── config.yml          ← CMS configuration (edit carefully)
├── uploads/
│   └── gallery/            ← All uploaded images go here
└── README.md
```

---

## 🚀 Initial Setup (Done Once by the Technical Student)

### Step 1: GitHub Repository

1. Create a new GitHub repository: `YOUR_ORG/nsbe-unl` (or whatever you want)
2. Push all these files to the `main` branch
3. Go to **Settings → Pages** → Source: `Deploy from branch` → `main` → `/ (root)`
4. Your site will be live at `https://YOUR_ORG.github.io/nsbe-unl`

### Step 2: Connect Your Custom Domain

1. In GitHub Pages settings, add your custom domain (e.g. `nsbeunl.org`)
2. Add a `CNAME` file in the root with just: `nsbeunl.org`
3. Update your domain registrar's DNS:
   - Add 4 A records pointing to GitHub's IPs: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Add a CNAME record: `www` → `YOUR_ORG.github.io`

### Step 3: Set Up Decap CMS (Content Manager)

Non-technical admins use `yoursite.com/admin` to update content. This requires one-time GitHub OAuth setup:

1. Go to [github.com/settings/applications/new](https://github.com/settings/applications/new)
2. Fill in:
   - **Application name**: NSBE UNL CMS
   - **Homepage URL**: `https://nsbeunl.org`
   - **Authorization callback URL**: `https://api.netlify.com/auth/done`
3. Copy the **Client ID** and **Client Secret**
4. Go to [app.netlify.com](https://app.netlify.com), create a free account
5. **Identity → Enable Git Gateway** OR use **Netlify OAuth** as the auth provider
   - In Netlify: Site → Access control → OAuth → GitHub → paste the Client ID & Secret
6. Update `admin/config.yml` line 8: change `YOUR_GITHUB_USERNAME/nsbe-unl` to your actual repo path

> **Alternative (simpler)**: Use [Netlify's free tier](https://netlify.com) to host instead of GitHub Pages. Drag-and-drop deploy, built-in CMS auth, free SSL. The `admin/` folder works out of the box.

### Step 4: Set Up the Contact Form (Formspree)

1. Go to [formspree.io](https://formspree.io) and sign up with the NSBE UNL email
2. Create a new form → give it a name → copy the **Form ID** (looks like `xvoeabcd`)
3. Update `_data/site.json` → set `"formspree_id": "xvoeabcd"` (via CMS or direct edit)
4. All contact form submissions will be emailed to the NSBE UNL inbox automatically

### Step 5: Set Up Outlook Calendar (Recommended Primary)

UNL runs on Microsoft 365, so Outlook is the best default choice for your audience.

1. Sign into [outlook.office.com](https://outlook.office.com) with the NSBE UNL Microsoft/Huskers account
2. Open **Calendar** → right-click your NSBE calendar in the left sidebar → **Share** → **Publish calendar**
3. Set the access level to **"Can view all details"**
4. Copy the **HTML** link (not the ICS link)
5. Go to `yoursite.com/admin` → **⚙ Site Settings** → paste it into **"Outlook Calendar URL"** → Publish
6. That's it — events you add in Outlook will appear on the site automatically

### Step 6: Set Up Google Calendar (Optional Secondary)

The site has a toggle so visitors can switch between Outlook and Google. Setting up Google is optional but recommended so members who prefer Google can subscribe too.

1. Create a Google Calendar for NSBE UNL events (use the chapter Google account)
2. Go to **Settings** (⚙) → click your calendar name → scroll to **Integrate calendar**
3. Copy the **Calendar ID** (looks like `abc123@group.calendar.google.com`)
4. Go to `yoursite.com/admin` → **⚙ Site Settings** → paste it into **"Google Calendar ID"** → Publish
5. Make the calendar **public** so the embed works: Settings → **Access permissions** → ✅ Make available to public

### Step 6: Set Up Newsletter (Mailchimp)

1. Go to [mailchimp.com](https://mailchimp.com), create a free account
2. Audience → Signup Forms → Embedded Forms
3. Select **Unstyled** form → copy the **form `action` URL** from the generated HTML
4. Update `_data/site.json` → set `"mailchimp_url"` to that action URL (via CMS)

---

## 📋 Non-Technical Admin Guide — How to Update Content

> Share this section with board members who need to update the site.

### Logging Into the Content Manager

1. Go to `https://yoursite.com/admin`
2. Click **"Login with GitHub"**
3. You'll need a GitHub account — ask the technical student to add you as a collaborator on the repository

---

### 📣 Posting an Announcement Banner

1. Login to `yoursite.com/admin` → **"⚙ Site Settings"** → **"General Settings"**
2. Scroll to **"Announcement Banner"**
3. Flip **"Show Banner?"** to ON
4. Type your message (e.g. *"GBM this Thursday at 6pm in Kiesselbach!"*)
5. Optionally add a **Button Text** (e.g. `Register now →`) and a **Button Link** URL
6. Click **Publish** — live in ~2 minutes

To take it down: same steps, just flip **"Show Banner?"** to OFF and publish. Your message stays saved so you don't have to retype it next time.

---

### 🖼 Updating the Photo Gallery

1. Login to `yoursite.com/admin`
2. Click **"Photo Gallery"** in the left sidebar
3. Click **"Gallery Photos"**
4. Click **"Add Photos +"** to add a new photo
5. Upload your image, add a caption and event name
6. Click **Save** → the site updates automatically within ~2 minutes

---

### 👥 Updating Leadership (Every Year)

1. Login to `yoursite.com/admin`
2. Click **"Leadership Board"** → **"Executive Board"**
3. Update the **Academic Year** field (e.g. `2025-2026`)
4. For each board member:
   - Click their name to edit, or click **"Add Board Members +"** for a new person
   - Fill in: Name, Role, Major & Year, Short Bio
   - Upload their **headshot photo** (square crop works best)
5. To remove a member: click the trash icon next to their entry
6. Click **Publish** → live in ~2 minutes

---

### ⚙ Updating Site Info (Email, Social Links, Stats)

1. Login to `yoursite.com/admin`
2. Click **"⚙ Site Settings"** → **"General Settings"**
3. Update whatever changed: email, Instagram link, member stats, etc.
4. Click **Publish**

---

### 📅 Updating Events (Outlook — Recommended)

No CMS needed — just update Outlook directly!

1. Sign into [outlook.office.com](https://outlook.office.com) with the NSBE UNL account
2. Open **Calendar** and add, edit, or delete events as normal
3. Changes appear on the website **immediately** — it's a live embed

> Tip: Add a description and location to your Outlook events — they show up in the website calendar too.

### 📅 Updating Events (Google Calendar — Optional)

If you set up Google Calendar as a secondary option, the same rule applies — no CMS needed.

1. Open Google Calendar with the NSBE UNL Google account
2. Add, edit, or delete events as normal
3. Changes appear on the website **immediately**

> Note: Visitors can toggle between Outlook and Google on the site. Keep both calendars in sync if you use both, or just stick to Outlook as your primary.

---

### 🦸 Hero Slideshow Photos

1. Login to `yoursite.com/admin` → **"⚙ Site Settings"**
2. Scroll to **"Hero Slideshow Photos"**
3. Click **"Add Hero Slideshow Photos +"** — add as many photos as you want
4. Upload each photo and add a short description (alt text) for each one
5. Click **Publish** — the slideshow updates automatically with a dot for every photo

---

## 🔧 Developer Notes

### Making Code Changes

- The entire site is one `index.html` file — easy to maintain
- Data is loaded client-side via `fetch()` from the `_data/*.json` files
- The CMS writes directly to the JSON files via GitHub commits — no backend needed
- All images are stored in `uploads/gallery/` in the repo

### Committing Style Guide

```
feat: add alumni section to homepage
fix: correct board photo aspect ratio on mobile
content: update leadership board for 2025-2026
style: adjust hero font size breakpoints
chore: update CMS config for new social fields
```

### Adding New CMS Fields

Edit `admin/config.yml` to add new editable fields. After pushing:
- New fields appear in the admin UI automatically
- Add corresponding rendering code in `index.html`'s `loadData()` function

### Local Development

```bash
# Install a simple local server (Python)
python3 -m http.server 8080
# Then visit http://localhost:8080

# Or with Node.js
npx serve .
```

> Note: The CMS (`/admin`) requires GitHub OAuth and won't work fully on localhost. Edit JSON files directly for local testing.

---

## 📞 Support

- **Technical issues**: Open a GitHub Issue in this repository
- **CMS questions**: See [decapcms.org/docs](https://decapcms.org/docs)
- **NSBE National**: [nsbe.org](https://nsbe.org)
- **UNL Engineering**: [engineering.unl.edu](https://engineering.unl.edu)