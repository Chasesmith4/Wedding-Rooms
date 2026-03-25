# Room Booking — Charlotte & Chase · August 22, 2026

A real-time room reservation page for Hill Farm Inn guests.

---

## Setup (one time, ~15 minutes)

### Step 1 — Create a Firebase project

1. Go to [console.firebase.google.com](https://console.firebase.google.com)
2. Click **Add project**, name it something like `cc-wedding-rooms`
3. Disable Google Analytics (not needed), click **Create project**

### Step 2 — Enable Firestore

1. In the left sidebar, click **Firestore Database**
2. Click **Create database**
3. Choose **Start in test mode** (allows reads/writes without auth — fine for this use case)
4. Select a region (us-east1 is fine), click **Enable**

### Step 3 — Get your Firebase config

1. In the left sidebar, click the gear icon → **Project settings**
2. Scroll down to **Your apps** → click the `</>` (Web) icon
3. Register the app (any nickname is fine), skip "Also set up Firebase Hosting"
4. Copy the `firebaseConfig` object shown — it looks like:

```js
const firebaseConfig = {
  apiKey: "AIza...",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project",
  storageBucket: "your-project.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

### Step 4 — Paste config into index.html

Open `index.html` and find the section near the bottom labeled:

```
// FIREBASE CONFIG
// Replace these values with your own from the Firebase Console.
```

Replace all the `REPLACE_WITH_YOUR_...` placeholders with your actual values.

---

## Hosting on GitHub Pages (free)

1. Create a new GitHub repository (e.g. `cc-wedding-rooms`) — set it to **Public**
2. Upload all files to the repo:
   - `index.html`
   - All room photos (keep filenames exactly as-is)
3. Go to **Settings → Pages**
4. Under **Source**, select `main` branch, `/ (root)` folder
5. Click **Save** — your site will be live at `https://yourusername.github.io/cc-wedding-rooms`

Share that link on your Knot website's "Reserve a Room" section.

---

## Viewing Bookings

All submissions are stored in Firebase Firestore in real time.

To see who booked what:
1. Go to [console.firebase.google.com](https://console.firebase.google.com)
2. Click your project → **Firestore Database**
3. Click the `rooms` collection
4. Click any room document to see guest name, email, phone, and booking timestamp

To export all bookings at once, you can use the Firebase console's export feature or simply read them from the Firestore UI.

---

## Room Types & Pricing

All rooms are booked for **2 nights (Friday Aug 21 + Saturday Aug 22)**.

| Room | Type | Per Night | 2-Night Total |
|------|------|-----------|---------------|
| Grafton | Queen Room | $375 | $750 |
| Battenkill | King Room | $430 | $860 |
| Equinox | Queen Room | $375 | $750 |
| Saratoga Spring | Queen Room | $375 | $750 |
| Wilcox | Queen Room | $375 | $750 |
| Landgrove | Queen Room | $375 | $750 |
| Sandgate | King Room | $430 | $860 |
| Emerald Lake | King Room | $430 | $860 |
| Hill Farm Suite | Suite | $475 | $950 |
| Honeybee Suite | Suite | $475 | $950 |
| Dorset Suite | Suite | $500 | $1,000 |

If any room type/price needs to be adjusted, update the `ROOMS` array in `index.html`.
To mark a room as pre-reserved on first load, set `preReserved: true` on that room in the array (Emerald Lake is already set this way).

---

## Questions

Reach out to Chase directly — this was built to be simple and low-maintenance.
