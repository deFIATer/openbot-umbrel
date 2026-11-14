# OpenBot for Umbrel (Community App Store)

[![Umbrel App Store](https://img.shields.io/badge/Umbrel-Community_App_Store-blue)](https://github.com/getumbrel/umbrel-community-app-store)
[![OpenBot](https://img.shields.io/badge/OpenBot-nightly--labs-orange)](https://github.com/nightly-labs/openbot)

Ten projekt umożliwia 1-klikową instalację **[OpenBot](https://github.com/nightly-labs/openbot)** bezpośrednio na Twoim serwerze **UmbrelOS** za pośrednictwem funkcji *Community App Store*.

---

## 🚀 Jak zainstalować na Umbrel (Instrukcja krok po kroku)

### 1. Dodaj ten App Store do Umbrel
1. Otwórz panel swojego Umbrel (np. `http://umbrel.local`).
2. Wejdź w **App Store**.
3. Kliknij ikonę trzech kropek (**...**) w prawym górnym rogu.
4. Wybierz **Community App Stores** (Społecznościowe sklepy z aplikacjami).
5. Wklej adres URL tego repozytorium GitHub:
   ```text
   https://github.com/deFIATer/openbot-umbrel
   ```
   *(lub URL swojego forka)*
6. Kliknij **Add** (Dodaj).

### 2. Zainstaluj OpenBot
1. Po odświeżeniu listy aplikacji pojawi się kafelek **OpenBot**.
2. Kliknij **Install** (Zainstaluj).
3. Umbrel pobierze oficjalny obraz Docker `ghcr.io/nightly-labs/openbot:latest`, skonfiguruje profil bezpieczeństwa seccomp oraz wolumen danych i uruchomi aplikację.

### 3. Połącz serwer ze swoim kontem OpenBot
OpenBot działa jako bezpieczny demon w tle (self-hosted server). Aby powiązać go ze swoim kontem:

1. Otwórz **Umbrel Terminal** (zainstalowany z App Store) lub połącz się przez SSH z Umbrel.
2. Uruchom polecenie logowania:
   ```bash
   sudo docker exec -it openbot-app_openbot_1 openbot login
   ```
   *Alternatywnie za pomocą Umbrel CLI:*
   ```bash
   umbrel app compose openbot-app exec openbot openbot login
   ```
3. Wpisz swój adres e-mail i kod weryfikacyjny, który otrzymasz na pocztę.

### 4. Korzystaj z OpenBota!
- Otwórz aplikację webową: **[openbot.run/app](https://openbot.run/app)**
- Albo pobierz oficjalną aplikację desktopową (macOS / Windows / Linux) lub aplikację na telefon (iOS / Android) z [GitHub Releases](https://github.com/nightly-labs/openbot/releases).
- Twój serwer Umbrel pojawi się na liście serwerów!

---

## 📱 Parowanie aplikacji mobilnej (iOS / Android)

Aby wygenerować kod QR do sparowania aplikacji mobilnej w terminalu Umbrel, uruchom:
```bash
sudo docker exec -it openbot-app_openbot_1 openbot mobile-connect
```
Zeskanuj kod QR aparatem w aplikacji OpenBot na telefonie.

---

## 🔍 Status i diagnostyka

Sprawdzenie statusu działania kontenera OpenBot:
```bash
sudo docker exec -it openbot-app_openbot_1 openbot status
```

---

## 🛠️ Zawartość repozytorium

- `umbrel-app-store.yml` – konfiguracja sklepu aplikacji Umbrel.
- `openbot-app/`
  - `umbrel-app.yml` – manifest aplikacji (metadane, opis, kategoria, ikony, wersja).
  - `docker-compose.yml` – konfiguracja Docker Compose zoptymalizowana pod umbrelOS.
  - `seccomp.json` – oficjalny profil seccomp wymagany przez Electron sandbox w kontenerze OpenBota.
  - `data/` – katalog na dane i przestrzeń roboczą agentów (`/data`).
  - `www/` – lokalny portal webowy z instrukcjami i bezpośrednimi linkami, wyświetlany po kliknięciu ikony w Umbrel.

---

## 📄 Licencja & Podziękowania

- OpenBot: Copyright (c) Synthetify Labs / [nightly-labs/openbot](https://github.com/nightly-labs/openbot)
- Umbrel Community App Store: [getumbrel/umbrel-community-app-store](https://github.com/getumbrel/umbrel-community-app-store)
