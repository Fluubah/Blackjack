# Putting The Reshuffle Room on your iPhone as a real app (free)

This turns the game into a **native iOS app** using [Capacitor](https://capacitorjs.com/)
(a thin native shell around the web app). Everything here is **free** — you only need
your Mac, a free Apple ID, and your iPhone. No paid Apple Developer account.

> **The one catch:** apps installed with a free Apple ID **stop opening after 7 days**.
> Just re-run step 6 to renew (30 seconds), or use [AltStore](https://altstore.io) to
> auto-renew over WiFi. The $99/yr Apple Developer Program removes the 7-day limit and
> is the only thing that costs money — you don't need it.

## One-time setup on your Mac

1. **Install Xcode** — free from the Mac App Store. Open it once and let it finish
   installing components. Then install the command-line tools:
   ```bash
   xcode-select --install
   ```

2. **Install [Node.js](https://nodejs.org)** (LTS) and **CocoaPods**:
   ```bash
   sudo gem install cocoapods
   ```

3. **Get this repo onto your Mac** and open a terminal in it:
   ```bash
   git clone https://github.com/Fluubah/Blackjack.git
   cd Blackjack
   git checkout claude/blackjack-strategy-guide-9oi3v0
   ```

## Build it

4. **Install dependencies and create the iOS project:**
   ```bash
   npm install
   npm run copy          # bundles the web app into www/
   npx cap add ios       # creates the native Xcode project (first time only)
   npm run icons         # generates the app icon + splash from /assets
   npx cap sync ios
   ```

5. **Open it in Xcode:**
   ```bash
   npm run open
   ```

6. **Install to your iPhone:**
   - Plug your iPhone into the Mac (tap **Trust** if asked).
   - In Xcode's top bar, pick your iPhone as the run destination.
   - Click the project name in the left sidebar → **Signing & Capabilities** tab →
     check **Automatically manage signing** → under **Team**, choose **Add an Account…**
     and sign in with your Apple ID (this is free). Xcode picks a signing certificate for you.
   - If it complains the bundle ID is taken, change **Bundle Identifier** to something
     unique like `com.yourname.reshuffle`.
   - Press the **▶ Run** button. The app builds and installs onto your phone.

7. **First launch:** on the iPhone go to **Settings → General → VPN & Device Management**,
   tap your Apple ID under *Developer App*, and tap **Trust**. Now open the app from your
   home screen — full native app, your icon, no browser.

## Updating the app later

Whenever the game changes, on your Mac:
```bash
git pull
npm run sync
npm run open   # then hit Run again
```

## Keep it from expiring (optional)

Install [AltStore](https://altstore.io) on the Mac and your iPhone. It refreshes the
app's 7-day signature automatically whenever both are on the same WiFi, so you never
have to manually rebuild.
