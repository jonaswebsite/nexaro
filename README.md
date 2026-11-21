# NEXARO — Create · Play · Explore

A lightweight browser-based 2D game editor. Built with plain HTML, CSS and Canvas 2D to stay usable on older computers and browsers without WebGL 2.

## First version
- Place and move balls, platforms and goals
- Test mode, object list, grid toggle
- Save/load in the current browser
- Export scene as standalone HTML
- Guest mode
- Supabase email/password registration and login
- Google OAuth after provider setup

## Run locally
Open `index.html` in a modern browser. No build command or package installation is required.

## Supabase setup
1. Create a separate Supabase project for Nexaro (recommended; avoid sharing another app's user pool).
2. In **Authentication → Providers**, enable Email and configure Google OAuth. Create Google OAuth credentials in Google Cloud and enter the client ID/secret in Supabase. Do not put the Google client secret in this repository.
3. Enable anonymous sign-ins for Supabase-backed guest accounts. Local guest mode works even if anonymous auth is off.
4. In **Authentication → URL Configuration**, set the Site URL to the deployed Nexaro URL and add it to the redirect allow-list.
5. In `index.html`, replace empty `SUPABASE_URL` and `SUPABASE_ANON_KEY` constants with the project URL and publishable/legacy anon key.
   - A publishable/anon key is intended for browser use with proper Auth settings and RLS.
   - Never use a `service_role` or secret key in frontend code.

Supabase's standard email/password signup requires email (or phone) as the login identifier. This version stores username as profile metadata and authenticates with email+password. Username-only password login needs a separate secure server-side auth endpoint; never store passwords in a public database.

## Render deployment
Static site settings:
- Repository: `https://github.com/jonaswebsite/nexaro`
- Branch: `main`
- Build command: empty
- Publish directory: `.`

After deployment, add the Render URL to Supabase Auth's Site URL and redirect allow-list. Configure the Google OAuth redirect URI exactly as shown in the Supabase Google provider settings.

## MVP limitations
Physics, multiple scenes, cloud project saves and username-only auth are not implemented yet.
