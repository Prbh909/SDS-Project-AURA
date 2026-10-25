# SDS Project AURA — Advanced Unified Ride Assistance

A polished, responsive front-end prototype for school transport visibility and camera-assisted attendance. Built as a single-page HTML/CSS/JavaScript app for a school project demonstration.

## Included features

- Responsive dashboard with animated visual design, DM Sans + Manrope typography, and motion that respects reduced-motion preferences.
- Role-based demo sign-in for students, teachers, and administrator.
- Bus letter selection from **A to Z** (not numeric-only bus IDs).
- **GPS-first flow:** browser geolocation is requested only after a user presses a location button. One-time location and continuous browser GPS watch are supported.
- Google Maps embed updates to the device's latest coordinates and includes an external Google Maps link.
- Camera permission is requested only when staff starts the camera.
- Face detection using face-api.js Tiny Face Detector (CDN/model required), with a manual staff visual-verification fallback if the model cannot load.
- Attendance confirmation and review queue for staff; students see only their own attendance view.
- Student directory with search, class/bus filters, add/edit/delete demo records.
- CSV exports, JSON backup, local browser storage, activity log, reset controls, and a detailed guide for every tab.

## Demo credentials

- Student: Bus `A`, Admission `SDS1001`, Password `Aura@123`
- Student: Bus `B`, Admission `SDS1003`, Password `Aura@123`
- Student: Bus `C`, Admission `SDS1006`, Password `Aura@123`
- Administrator: `admin` / `Admin@123`
- Teacher: `teacher` / `Teach@123`

Other fictional student IDs: `SDS1002`, `SDS1004`, `SDS1005`, `SDS1007`, `SDS1008`. Use each student's assigned letter shown in the directory.

## How to run / publish

1. Upload `index.html`, `README.md`, and `package.json` to the root of a GitHub repository.
2. Open **Settings → Pages**.
3. Choose **Deploy from a branch**, branch `main`, folder `/(root)`, then Save.
4. Open the Pages URL GitHub provides. Allow a few minutes for the first deployment.
5. Use HTTPS or `localhost` for camera and geolocation permissions. A static `file://` open may not provide these permissions reliably.

The page uses external internet resources for Google Maps embeds, Google Fonts, and face-api.js/model files. The map starts with a Dehradun-area placeholder until the user explicitly requests GPS.

## Important technical limits — please read

- **This is a front-end prototype, not a production school transport system.** Login checks run in client-side JavaScript; demo passwords are visible in source. Do not use real student accounts or private records.
- **GPS is real for the device that grants permission, but it is not shared across phones.** The browser watch updates the map and local browser data. Live bus tracking for parents/students across separate devices needs an authenticated backend and real-time data transport, plus an authorized GPS-enabled driver device.
- The Google Maps iframe is centered on the current device coordinates after GPS permission is granted. A Google Maps Platform API key and billing may be required for more advanced custom map features, routing, ETA, geofencing, and custom markers.
- The computer-vision model detects whether a face is visible. **It does not identify whose face it is.** Authorized staff must visually verify the student before confirming attendance. No face templates or camera images are stored by this app. A real biometric identification system for minors would need school approval, a privacy/security review, consent/notice, careful access controls, retention limits, and a reliable anti-spoofing process.
- All demo data is stored in the current browser's `localStorage`. It does not sync across devices. Use only fictional sample data in a public GitHub repository.
- The JavaScript syntax is checked, but the site still needs end-to-end testing in the target browser, device, and school network. CDN/model availability, GPS permissions, camera permissions, and embedded Maps depend on the environment.

## Suggested next engineering phase

For real multi-device operation, add a secure backend (for example, a school-managed Firebase or Supabase project), server-side role-based authentication, real-time bus coordinate updates, audit logs, encrypted transport, and a school-approved privacy policy. Do not add real student data until authorized by the school.
