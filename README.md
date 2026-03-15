# Digital Ink Recognition

A cross-platform educational app that uses on-device handwriting recognition to help children learn Arabic/Urdu and English scripts through interactive ink-based practice.

## Repository Structure

| Directory | Stack | Role |
|---|---|---|
| `digital_ink_frontend/` | Flutter 3 (Dart) | Mobile app — Android & iOS |
| `digital_ink_backend/` | Laravel 11 (PHP) | REST API server |

## Features

- **On-device Ink Recognition** — powered by Google ML Kit Digital Ink Recognition; no network call for recognition
- **Multi-script Support** — Arabic/Urdu alphabet (Haroof), Urdu numerals (Ginti), English alphabet, numbers, and vowels
- **Imla (Dictation)** — spoken word prompt with canvas ink input, auto-graded by ML Kit
- **Quiz Module** — multiple question types across all script categories
- **Progress Tracking** — per-child progress summaries synced to the backend
- **Multi-child Profiles** — a parent account manages multiple child profiles independently
- **Dark Mode** — full light/dark theme with persistence

## Tech Stack

### Frontend (Flutter)
- `google_mlkit_digital_ink_recognition` — on-device ink recognition
- `flutter_tts` — text-to-speech for audio prompts
- `http` — REST API communication
- `shared_preferences` — local session and theme persistence

### Backend (Laravel 11)
- Laravel Sanctum — token-based API authentication
- Eloquent ORM with MySQL / PostgreSQL
- Nixpacks deployment config

## Getting Started

### Backend
```bash
cd digital_ink_backend
cp .env.example .env
composer install
php artisan key:generate
php artisan migrate --seed
php artisan serve
```

### Frontend
```bash
cd digital_ink_frontend
flutter pub get
flutter run
```

## API Reference

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/register` | Register a parent account |
| POST | `/api/login` | Authenticate and receive bearer token |
| POST | `/api/logout` | Revoke current token |
| GET | `/api/me` | Authenticated user with children list |
| GET/POST | `/api/children` | List / create child profiles |
| PUT/DELETE | `/api/children/{id}` | Update / delete a child profile |
| GET | `/api/lessons` | Fetch available lessons |
| GET | `/api/quizzes` | Fetch quiz questions |
| POST | `/api/quiz-attempts` | Submit a quiz attempt |
| GET | `/api/quiz-attempts/child/{id}` | Quiz history for a child |
| POST | `/api/imla/attempts` | Submit a dictation (imla) attempt |
| GET | `/api/imla/attempts/{child_id}` | Imla history for a child |
| POST | `/api/progress` | Record a progress entry |
| GET | `/api/progress/{child_id}/summary` | Progress summary for a child |

## License

MIT
