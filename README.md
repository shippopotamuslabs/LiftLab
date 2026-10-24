# Lift Lab

My first Android app. A workout tracker, started in May 2023, built while I
was learning native Android development.

Status: archived. This repo stays as a record of where the work started. It
gets no new features, no fixes, and no support. The apps that came after it
live in their own repos (Stratum is the current workout app). Default branch
here is `master`, a leftover of its age.

## What it does

- Logs lifts and workouts, with a history of past sessions.
- Syncs across devices through Firebase (Auth + Firestore), so a workout
  logged on one device shows up on the other.
- Shares a workout summary as an image.
- Crash reporting through Firebase Crashlytics.

## Stack

| Area | Choice |
| --- | --- |
| Language and UI | Kotlin, Jetpack Compose |
| Backend | Firebase: Auth, Firestore, Crashlytics, App Check, Firebase AI |
| Local data | Room (schemas in `app/schemas/`) |
| Code generation | Two small KSP modules of its own, `annotations/` and `annotation_generator/`: a hand-rolled annotation processor experiment |
| Modules | `:app`, `:annotations`, `:annotation_generator` |

The directories `.Jules/` and `.jules/` hold notes from sessions with
Google's Jules coding agent, which did some of the later work in this repo.

## Build notes (cold clone, honest version)

- AGP 8.12.1, Kotlin 2.2.10, compileSdk 36, minSdk 34, targetSdk 36.
  Gradle wrapper is in the repo.
- The `:app` module applies the `google-services` plugin, and
  `google-services.json` is not in the repo (it is gitignored). A build
  needs one from the Firebase project, and the sync features need that
  project to still exist and accept the app. Expect to supply your own
  Firebase config to get past configuration.
- `app/release/app-release.aab` is a built release bundle that was
  committed to the repo. It is part of the archive, not a build input.

## License

See `LICENSE`. Copyright (C) 2026 sean-brown-dev, permissive terms as written
in that file.
