SakhiRoute — Safety & Companionship App 👋
SakhiRoute is a cross‑platform Expo React Native mobile app with a companion React/Vite web MVP, powered by Firebase. It focuses on nearby discovery, SOS safety features, and secure communication.

Features at a Glance
Nearby Sakhi discovery with demo preview and safe location sharing
SOS shortcut: instant SMS draft to emergency contacts
Optional live video session with verified contacts (LiveKit integration)
Sakhi Circle matching based on age‑band preferences
Secure chat with short‑term photo evidence policy
Web MVP for admin/reviewer workflows and account management

--Mobile App (Expo)

Install dependencies:
bash
npm install
Start the app:
bash
npx expo start

Options: run in development build, Android emulator, iOS simulator, or Expo Go.

Firebase Android config is wired via google-services.json and Expo’s android.googleServicesFile.
Requires a fresh development/production build (not Expo Go).
API key is client‑side only; never commit service‑account credentials.

--Web MVP (React/Vite)

Setup:
powershell
npm ci --prefix web
Copy-Item web/.env.example web/.env.local
npm run dev --prefix web

Fill in VITE_FIREBASE_* values in web/.env.local from a Firebase Web app registered in the same project.
Enable Email/Password sign‑in in Firebase Console → Authentication.
Restart Vite server after changing environment values.

Deploy web app:

powershell
npm run build --prefix web
npx firebase-tools@latest deploy --only hosting



Backend (Firebase)

Functions: server logic for nearby presence, SOS, and cleanup jobs
Firestore rules & indexes: enforce security and TTL policies
Storage rules: manage evidence retention
Deployment:

bash
cd functions
npm install
cd ..
firebase deploy --only firestore:rules,firestore:indexes,storage,functions


Privacy & Safety Notes
Demo flows (Aadhaar, police status, face verification) are fictional and device‑local.
SOS video requires LiveKit Cloud credentials set via Firebase Functions secrets.
Evidence copies are short‑lived and purged automatically.
TTL policies remove expired chat and location records.
Never commit .env.local or service‑account JSON files.


Development Checklist
npm run lint → lint code
npm run typecheck → TypeScript check
npm run test → run tests
npm run build → build web app


Learn More
Expo documentation
Expo Router (docs.expo.dev in Bing)
Firebase documentation
LiveKit Cloud
