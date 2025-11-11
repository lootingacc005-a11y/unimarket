UniMarket
=========

UniMarket is a student marketplace Android app (Java, MVVM) built as an example/demo. It uses Firebase (Auth, Firestore, Storage) and includes a simple AI client template for integrating with a REST-based AI provider.

Quick start
-----------
1. Install Android Studio and Java 11.
2. Open this folder in Android Studio: root of the project.
3. Add your Firebase configuration:
   - Create a Firebase project and enable Email/Password authentication and Firestore and Storage.
   - Download `google-services.json` and place it in `app/`.
4. (Optional) Place your AI API key in an environment variable `AI_API_KEY` or add to `local.properties` as `aiApiKey=YOUR_KEY` and wire it into BuildConfig (see TODOs in `AIClient.java`).

Build
-----
From the project root (Windows):

```cmd
cd C:\Users\HP\AndroidStudioProjects\UniMarket
.\gradlew.bat assembleDebug
```

Run unit tests:

```cmd
.\gradlew.bat test
```

CI
--
A GitHub Actions workflow is included at `.github/workflows/android-ci.yml` which runs `./gradlew build` and unit tests on push to `main`/`master`.

Files added or updated by assistant
----------------------------------
- `app/src/main/java/com/unimaid/unimarket/util/AIClient.java` – simple OkHttp-based AI client template.
- `app/src/main/java/com/unimaid/unimarket/repository/StorageRepository.java` – Firebase Storage upload helper.
- `app/src/main/java/com/unimaid/unimarket/repository/ItemsRepository.java` – Firestore items helper (minimal).
- `app/src/main/java/com/unimaid/unimarket/repository/UserRepository.java` – Auth wrapper.
- `app/src/main/java/com/unimaid/unimarket/model/Item.java` – Item model.
- `app/src/main/java/com/unimaid/unimarket/viewmodel/*` – AuthViewModel, ItemsViewModel, ChatViewModel (stubs).
- `app/src/main/java/com/unimaid/unimarket/adapter/ItemsAdapter.java` – RecyclerView ListAdapter.
- Several layout XMLs were repaired/created: `activity_chat.xml`, `activity_item_detail.xml`, `activity_login.xml`, `activity_post_item.xml`, `activity_splash.xml`, `activity_settings.xml`, `activity_signup.xml`, `item_card.xml`.
- `app/src/main/res/drawable/gradient_background.xml` – splash background.
- `firestore.rules` and `storage.rules` – example Firebase rules (dev defaults; tighten for prod).
- `.github/workflows/android-ci.yml` – CI workflow file.
- `app/src/test/java/.../CurrencyUtilsTest.java` – small unit test.

Current status (local checks performed)
--------------------------------------
- Gradle assembleDebug: PASS (local run completed successfully).
- Unit tests: PASS (local `test` task completed successfully, CurrencyUtils test ran).
- Basic resource/manifest issues: FIXED. Several malformed/missing XML resources were corrected.

Feature coverage (what's implemented vs deferred)
-------------------------------------------------
Done (implemented or added stubs):
- Project skeleton, themes, and Material 3 dependencies in `app/build.gradle` (existing file edited earlier).
- Core Activities and many layouts repaired/created so the project builds.
- Firebase client stubs: `StorageRepository`, `ItemsRepository`, `UserRepository`.
- MVVM ViewModel stubs: `AuthViewModel`, `ItemsViewModel`, `ChatViewModel`.
- `AIClient` (OkHttp template) — placeholder endpoint and environment-key usage documented.
- `ItemsAdapter` + `item_card.xml` and other UI helpers.
- Example Firestore and Storage rules (`firestore.rules`, `storage.rules`).
- README and CI workflow.

Deferred / Next steps (recommendations I can implement next):
- Full PostItem Flow: image compression, WorkManager-based upload workers, resumable uploads with retry/backoff.
- Full Chat UX and adapter, pagination, seen states.
- AI responses parsing tuned to your AI provider (Gemini) and integrating secure key flow (Cloud Function proxy recommended).
- Complete offline sync behavior and more unit/instrumentation tests for Activities/ViewModels.
- Add onboarding flow, micro-interactions, shimmer placeholders, and more polished Material animations.

Notes / TODOs
-------------
- Do NOT commit `google-services.json` or API keys to source control.
- Replace `AIClient.ENDPOINT_URL` and wire `AI_API_KEY` securely (use a server-side proxy for production).
- Tighten `firestore.rules` and `storage.rules` before deploying to production; the included rules are examples only.

If you'd like, I'll continue implementing one of the deferred items above now — pick any of these or say "continue" and I'll begin implementing the PostItem WorkManager upload (recommended next step).
"# unimarket" 
"# unimarket" 
"# unimarket" 
