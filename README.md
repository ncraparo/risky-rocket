# Risky Rocket: host it on GitHub Pages (free)

Three files: `index.html` (the game), `config.js` (your database link), `README.md` (this).

## 1. Make the free multiplayer database (Firebase, about 5 minutes)
1. Go to https://console.firebase.google.com and sign in with a Google account.
2. **Create a project** (any name, turn Google Analytics off).
3. In the left menu: **Build > Realtime Database > Create Database**. Pick a location. Choose **Start in test mode**.
4. Open the **Rules** tab, replace everything with the text below, then **Publish**. (This stops test mode from expiring after 30 days.)

```
{
  "rules": {
    "rr": { ".read": true, ".write": true }
  }
}
```

5. Back on the **Data** tab, copy the database URL at the top. It looks like
   `https://your-project-default-rtdb.firebaseio.com`

## 2. Put the URL in config.js
Open `config.js` and replace `PASTE_YOUR_DATABASE_URL_HERE` with that URL (keep the quotes). Save.

## 3. Put it on GitHub
1. github.com > **New repository**. Name it `risky-rocket`. Make it **Public** (free Pages needs public).
2. **Add file > Upload files**, add all three files, **Commit changes**.
3. **Settings > Pages > Build and deployment**: Source = **Deploy from a branch**, Branch = **main** and **/ (root)**, then **Save**.
4. After about a minute your game is live at `https://YOUR-USERNAME.github.io/risky-rocket/`

Edit `config.js` later by opening it in the repo and tapping the pencil icon.

## How friends join
Everyone opens your link, types a name, picks credits, and enters the **same TABLE CODE**.
Different codes are separate games. The deposit screen shows an invite link ending in `#CODE`
that pre-fills the code for whoever opens it.

## Notes
- Up to 5 players per table; a 6th person watches.
- Credits are play money saved only in each person's browser. No real money.
- The database rules above are open on purpose (it is a friends game). Anyone who knows your
  database URL could write to it, so do not store anything private there.
- The Firebase free plan is far more than this game needs.
- If the red "SOLO ONLY" note shows on the title screen, `config.js` still has the placeholder
  or the URL is mistyped. If the game says OFFLINE, the browser can't reach Firebase.
