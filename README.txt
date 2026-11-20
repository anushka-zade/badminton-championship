FRIENDS BADMINTON CHAMPIONSHIP — UPDATED PHONE-FIRST WEBSITE

FILES
- index.html: responsive website, Firebase Authentication and Firestore live sync
- firestore.rules: Firestore security rules
- firebase.json: Firebase CLI rules configuration

WHAT'S INCLUDED
- Phone-first responsive layout with compact cards and touch-friendly controls
- Six official teams and all 15 round-robin league fixtures
- Admin-only score entry and official team-name editing
- Automatic League Points dashboard (2 points per win, 0 per loss)
- Automatic semifinal seeding (Rank 1 vs Rank 4; Rank 2 vs Rank 3)
- Automatic Grand Final pairing from semifinal winners
- Public team-name suggestion form; admin-only request review/approval
- Rules: one game to 15; rally scoring; at 14–14 golden point; no deuce or advantage
- No clock-based schedule or time fields

IMPORTANT FIREBASE SETUP
1. In Firebase Console, open Authentication > Sign-in method and enable Email/Password.
2. Create the admin user using zadejanushka@gmail.com and set its password.
3. Verify the admin email address.
4. Open Firestore Database > Rules and publish the included firestore.rules.
5. Deploy the website to Firebase Hosting, Netlify, GitHub Pages or another static host.
6. Share the deployed website URL with the players.

FIREBASE HOSTING (OPTIONAL)
Install Firebase CLI, sign in, then from this folder run:
  firebase deploy --only hosting,firestore:rules

The included firebase.json expects this folder to be the Hosting public directory.
If using another host, upload index.html as the site entry point and publish firestore.rules manually in Firebase Console.

SECURITY NOTES
- The Firebase web API key in index.html is a public client identifier, not an admin secret.
- Firestore rules enforce that only a signed-in, email-verified account whose email is zadejanushka@gmail.com can write official tournament data or review/delete name requests.
- Anyone can read the public tournament scoreboard and submit a team-name request.
- Never place a Firebase service-account private key in index.html.

TOURNAMENT DATA
The site uses Firestore path:
  tournaments/friends-badminton
Name requests use:
  tournaments/friends-badminton/nameRequests/{requestId}

The tournament document is created when the admin first signs in and the app connects, provided the rules have been published.