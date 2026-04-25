# Web-App-Angular

An Angular application for working with test users from public APIs. The project includes login via first and last name, a three-panel dashboard, user list filtering, a profile detail view with enriched data, and a browsing history of opened details.

## Main Features

- Login using the first and last name of a user from `dummyjson.com`.
- Protected application area available only after authentication.
- Left panel with a user list and last-name filtering.
- Center panel with the selected user's profile details.
- Extra profile data from external APIs: gender from `genderize.io` and state from `zippopotam.us`.
- Right panel with the history of opened and closed details.
- Login duration shown after logout.

## Tech Stack

- Angular 20
- TypeScript
- RxJS
- Angular Router
- Angular HttpClient

## Requirements

- Recommended: Node.js 18+
- npm

## Getting Started

1. Install dependencies:

```bash
npm install
```

2. Start the local development server:

```bash
npm start
```

3. Open the app in your browser at:

```bash
http://localhost:4200
```

## Production Build

```bash
npm run build
```

## How the App Works

### Login

On the login screen, you enter a first name and a last name. The app loads the user list from `https://dummyjson.com/users` and compares the entered values with the API data. If no match is found, an error is shown.

### Dashboard

After login, the dashboard is split into three panels:

- The left panel shows all users except the currently logged-in one.
- The center panel shows the selected user's details.
- The right panel shows the history of opened details.

The top bar shows the logged-in user, the login time, the application click count, and a last-name filter input.

### User Detail

When you click a user, the detail view opens with the user's basic data. The app enriches it with:

- test gender from `https://api.genderize.io`
- home state from `https://api.zippopotam.us`

If an extra API request fails, the app falls back to `Unavailable`.

### Browsing History

Each detail open and close is recorded in the history, including the start and end time.

### Logout

Logout clears the authenticated user, resets the application state, and shows the login duration in `HH:MM:SS` format.

## Project Structure

```text
src/
	components/
		app/           - root application component
		dashboard/     - main authenticated screen
		history/       - browsing history panel
		login/         - login screen
		top-bar/       - top bar with info and filter
		user-detail/   - user detail view
		user-list/     - user list
	guards/
		auth.guard.ts  - dashboard route protection
	models/
		user.model.ts  - user and history data types
	services/
		auth.service.ts
		browsing-history.service.ts
		user-detail.service.ts
		user.service.ts
	app.routes.ts
	main.ts
	global_styles.css
```

## Routes

- `/login` - login
- `/app` - dashboard after login
- `/` and unknown routes - redirect to `/login`

## Note

The project relies on public APIs, so an internet connection is required at runtime.