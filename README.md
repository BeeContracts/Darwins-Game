# Neon Arena

Neon Arena is an Android-only Kotlin + Jetpack Compose MVP for a dark-neon survival battler inspired by high-stakes anime death games.

## MVP Highlights
- **Compose-first Android app** with a polished cyber-anime dark theme
- **No login flow**; boots straight into a mock matchmaking / battle experience
- **6 ultimates** with **2-hour cooldowns** and distance-limited activation
- **NFC tap attack abstraction** for physical proximity attacks
- **Online multiplayer-ready architecture** with a mock gateway and backend notes
- **Last player alive wins** battle-state model

## Project Structure
- `app/src/main/java/com/neonarena/app/MainActivity.kt` – single-activity entry point
- `app/src/main/java/com/neonarena/app/ui/` – Compose screens, components, theme
- `app/src/main/java/com/neonarena/app/domain/` – core game models and rules
- `app/src/main/java/com/neonarena/app/data/` – repository + mock multiplayer feed
- `docs/ARCHITECTURE.md` – backend / NFC integration notes

## Core Game Systems Included
- Player and battle state models
- Ultimate catalog with cooldown timestamps
- Range checks based on player coordinates
- Mock attack / ultimate execution pipeline
- NFC service contract for future Android NFC integration
- Simulated multiplayer updates for nearby opponents

## Build Requirements
- Android Studio Iguana+ / Koala+ recommended
- Android SDK 34
- JDK 17
- Gradle 8.7+ (Android Studio will offer to sync/install)

## Build APK
1. Open `darwins-neon-arena` in Android Studio.
2. Let Gradle sync and install missing SDK components.
3. Build debug APK:
   - **Android Studio:** `Build > Build Bundle(s) / APK(s) > Build APK(s)`
   - **CLI (if Gradle is installed):** `gradle assembleDebug`
4. APK output will be under `app/build/outputs/apk/debug/`.

## Notes
- A Gradle wrapper is **not included** in this environment because the wrapper JAR could not be generated without local Gradle tooling. Android Studio can regenerate it with `gradle wrapper` once opened locally.
- Backend config uses placeholders only; nothing sensitive is committed.
- NFC is modeled as an interface + simulated implementation path, ready for `NfcAdapter` wiring.

## Next Steps for Production
- Replace `MockBattleRepository` with WebSocket/Firebase/Supabase real-time transport
- Persist cooldowns server-side to prevent client cheating
- Add Android NFC foreground dispatch + signed payload validation
- Add anti-spoofing location validation and rate limiting
