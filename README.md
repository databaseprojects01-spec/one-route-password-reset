# Hosted password-reset page

This folder is a static site for the link sent by Supabase Auth. It can be hosted on
GitHub Pages, Netlify, Vercel, or any HTTPS static host.

## Deploy with GitHub Pages

1. Copy `config.example.js` to `config.js`.
2. Fill `config.js` with the `SUPABASE_URL` and `SUPABASE_ANON_KEY` from `.env`.
   These two values are safe for a browser. Never add `RESEND_API_KEY` or any
   Supabase service-role/secret key.
3. Create a GitHub repository for these three files (`index.html`, `config.js`, and
   `README.md`), then enable **Settings → Pages → Deploy from a branch → main / root**.
4. GitHub gives the page a URL such as
   `https://your-github-name.github.io/one-route-password-reset/`.
5. Add that exact URL to **Supabase Dashboard → Authentication → URL Configuration → Redirect URLs**.
6. Set the same value in the desktop project's `.env`:

   ```dotenv
   PASSWORD_RESET_REDIRECT_URL=https://your-github-name.github.io/one-route-password-reset/
   ```

7. Restart One Route and request a new reset email.

The page receives the temporary recovery session from the link and calls Supabase Auth
to set the chosen password. It does not send or store passwords itself.
