# casehitz-keepalive

A tiny scheduled GitHub Actions job that pings **https://casehitz.com/healthz** every ~10 minutes
to keep the Render free-tier web service warm, so storefront visitors never hit a cold start
(a slept Render service takes ~30–60s to wake, during which images/pages can fail to load).

- **No code, no secrets, no data.** It only sends an unauthenticated HTTP GET to a public health URL.
- **Public repo on purpose** — GitHub Actions minutes are free/unlimited on public repos, so the
  keepalive costs nothing. The main casehitz app lives in a separate private repo.
- Runs in GitHub's cloud, so it works even when your computer is off (unlike the ListingManager
  60-second poll, which only keeps casehitz warm while LM is running).

The real fix for cold starts is a paid Render plan (no sleep). This is the free stand-in.
