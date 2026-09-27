# Woordjes Leren — Android app

Een kant-en-klaar Android-projectje dat de woordjes-leerapp (`app/src/main/assets/www/index.html`)
in een simpele WebView-app verpakt, plus een GitHub Actions-workflow die automatisch een APK bouwt.

## Zo bouw je de APK via GitHub

1. Maak een nieuwe (lege) repository op GitHub, bijvoorbeeld `woordjes-leren`.
2. Push deze hele map naar die repository:
   ```bash
   cd woordjes-android
   git init
   git add .
   git commit -m "Eerste versie"
   git branch -M main
   git remote add origin https://github.com/<jouw-gebruikersnaam>/woordjes-leren.git
   git push -u origin main
   ```
3. Ga op GitHub naar het tabblad **Actions** van de repo. De workflow "Build APK" start
   automatisch en duurt meestal een paar minuten.
4. Klik de voltooide run open en download onderaan bij **Artifacts** het bestand
   `woordjes-leren-debug-apk` (een .zip met de .apk erin).
5. Zet de .apk op je telefoon en installeer hem (zet eventueel eerst "Installeren uit
   onbekende bronnen" aan voor de app waarmee je hem opent).

Je kunt de workflow ook handmatig starten via **Actions → Build APK → Run workflow**.

## Belangrijk om te weten

- Dit is een debug-APK, bedoeld om zelf te installeren (sideloaden) — niet voor de Play Store.
- De automatische fotoherkenning (Claude die woorden uit een foto haalt) werkt alleen in de
  webversie binnen Claude zelf, niet in deze losse app — die verbinding bestaat alleen daar.
  In de app kun je nog wel handmatig woordparen toevoegen, en met "📷 Foto" een foto maken of
  kiezen als naslag terwijl je typt.
- Al je lijsten en voortgang worden lokaal op het toestel bewaard (in de opslag van de app),
  niet gedeeld of gesynchroniseerd.
- Wil je een ander app-icoon of andere naam? Pas `app/src/main/res/values/strings.xml`
  (naam) aan, of vervang `android:icon` in `AndroidManifest.xml` door je eigen mipmap-icoon.
- Om de inhoud van de app te updaten: vervang `app/src/main/assets/www/index.html` door een
  nieuwe versie en push opnieuw — de Action bouwt dan automatisch een nieuwe APK.
