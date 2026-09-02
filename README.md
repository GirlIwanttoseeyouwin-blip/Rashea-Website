# Deploying rasheaedmond.com with a working Rae

This folder has everything needed to put your site live on your own domain
with Rae fully working — no coding required, just following the steps.

## What's in this folder
- `index.html` — your website
- `api/rae.js` — the backend function that lets Rae talk (keeps your API key private and secure)
- `vercel.json` — a small config file Vercel needs

## Step 1 — Get an Anthropic API key
1. Go to https://console.anthropic.com and create an account (this is separate
   from your Claude.ai account, and separate from any Claude subscription).
2. Add a small amount of credit (Rae is a lightweight model — a few dollars
   will cover a lot of conversations to start).
3. Go to **API Keys** in the left sidebar, click **Create Key**, and copy it.
   You won't be able to see it again after this, so save it somewhere safe
   for a moment (you'll paste it into Vercel in Step 3).

## Step 2 — Create a free Vercel account
1. Go to https://vercel.com and sign up (you can sign up with just an email).
2. Once logged in, click **Add New… → Project**.
3. You'll be asked to import a Git repository. The easiest path:
   - Create a free GitHub account if you don't have one (https://github.com)
   - Create a new repository, and upload this whole folder's contents to it
     (GitHub's website lets you drag-and-drop files right in the browser —
     no command line needed)
   - Back in Vercel, choose **Import** next to that repository

## Step 3 — Add your API key to Vercel
1. In your new Vercel project, go to **Settings → Environment Variables**.
2. Add a new variable:
   - Name: `ANTHROPIC_API_KEY`
   - Value: (paste the key from Step 1)
3. Click **Save**, then go to the **Deployments** tab and redeploy (or just
   push any change to your GitHub repo — Vercel redeploys automatically).

At this point your site is live at a `your-project.vercel.app` address, and
Rae should be fully working there. Test her before moving to Step 4.

## Step 4 — Connect your GoDaddy domain
1. In Vercel, go to your project's **Settings → Domains**.
2. Type in `rasheaedmond.com` (and `www.rasheaedmond.com` if you want both)
   and click **Add**.
3. Vercel will show you one or two DNS records to add — usually an **A
   record** for the root domain and a **CNAME record** for `www`.
4. Log into GoDaddy, go to **My Products → Domains → DNS** for
   rasheaedmond.com, and add those exact records Vercel gave you.
   (You may need to delete GoDaddy's existing default "Parked" A record
   first — Vercel's instructions will tell you if so.)
5. DNS changes can take anywhere from a few minutes to a few hours to take
   effect. Vercel's Domains page will show a green checkmark once it's
   connected.

## After that
Your domain will point straight at this site, Rae will work live using your
own API key, and any time you want changes made, I can update `index.html`
and you just re-upload it to your GitHub repo — Vercel picks up the change
automatically.

## A note on cost
Unlike Claude.ai, the Anthropic API is pay-as-you-go based on usage. For a
small business site's chat volume this is typically a few dollars a month,
but keep an eye on usage in the Anthropic console if the site gets busy —
you can also set a monthly budget cap there.
