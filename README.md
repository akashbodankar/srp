# SRP Machinery & Spares Solution — Website

## Start locally

This is a multi-page Vite site. Install a current Node.js LTS version, then run:

```bash
npm install
npm run start
```

For hosting, run `npm run build` and upload the contents of the generated `dist` folder to GoDaddy cPanel **File Manager** (normally `public_html`). Configure your domain to point to that hosting package and enable SSL in GoDaddy.

## Pages

| URL | Purpose |
| --- | --- |
| `index.html` | Home, full-screen hero slider, statistics, scrolling reviews |
| `about.html` | Company story and two partner messages |
| `products.html` | Five categories and all products |
| `product.html?id=moulding-001` | Reusable individual product layout |
| `updates.html` | Events, exhibitions and news |
| `career.html` | Job listings |
| `catalogs.html` | Tracked catalogue-download gate |
| `contact.html` | Contact form and thank-you state |
| `services.html` | Five SRP services |
| `service.html?id=installation` | Reusable individual service detail page |
| `admin.html` | Demo admin dashboard for local enquiry/chat/click records |

## Where to place your real assets

Create the following folders inside `assets/` and add files with these names:

```text
assets/
  logo-mark.svg                 # replace with your final logo if desired
  images/
    hero-01.jpg                 # moulding / factory hero
    hero-02.jpg                 # preformer / extruder hero
    hero-03.jpg                 # automation hero
    about-company.jpg           # company/factory image
    owner-1.jpg                 # first partner portrait
    owner-2.jpg                 # second partner portrait
    services/
      service-installation.jpg
      service-maintenance.jpg
      service-automation.jpg
      service-repair.jpg
      service-retrofitting.jpg
    products/
      moulding-001.jpg
      preformer-001.jpg
      deflashing-001.jpg
      automation-001.jpg
      spares-001.jpg
  catalogs/
    moulding-machines.pdf
    preformer-extruder.pdf
    cut-trim-deflash.pdf
    automation.pdf
    spare-parts.pdf
  videos/
    moulding-001.mp4
```

Then update the matching image/PDF/video URLs in `src/data.js` and `src/main.js`. `src/data.js` is the single place that controls the 5 categories and their 10/10/10/10/100 generated product entries.

## Tracking catalogue downloads, enquiries and AI chat

The supplied frontend demonstrates each tracking action and stores test records in the visitor’s browser. That is useful for testing only; it is **not** a shared lead database. Before launching, connect the `record()` function in `src/main.js` to a secure backend (Supabase, Firebase, Zoho CRM, HubSpot, or a custom API) and save these fields:

- event type: `catalogue-download`, `contact-enquiry`, `ai-chat`, or `ai-chat-lead`
- name, company, email, phone, selected catalogue/product, message, date/time and page URL

For a real AI agent, connect the chat submit handler to your chosen provider (for example OpenAI via a secure server-side API) and retain the user’s consent and contact details in that same CRM/database. Never put an AI API key in this public website.

## Important security note about Admin

`admin.html` is a **local demonstration only**. It provides the requested default login in browser code and shows records saved in that same browser. It is not safe for a live website: anyone could inspect the public code and see the password. Before GoDaddy launch, move login, form records and AI-agent keys into a protected server/database (for example Supabase Auth + database, Firebase Auth + Firestore, or a custom backend). Change the default password before that step.

For visitor-source tracking, add Google Analytics 4 (GA4) to every page and configure events for `catalogue-download`, `generate_lead` and `chat_lead`. Link GA4 with Google Search Console; this shows search traffic and queries. Add the Google Business Profile review link/embed after you claim the business profile—do not invent reviews.

## GoDaddy launch checklist

1. Buy/attach hosting, connect the domain and turn on SSL.
2. Add final product photos, brochures, partner messages, event details and legal/privacy pages.
3. Set up form/CRM storage and email notifications before uploading the build.
4. Add GA4 and Google Search Console verification.
5. Upload `dist`, test every enquiry/download and test mobile view.
