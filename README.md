# Siwa Oasis Backend 🌴

## Project Structure
```
siwa-oasis-backend/
├── .env
├── package.json
└── Src/
    ├── index.js                        ← Entry point
    ├── app.controller.js               ← Main router (bootstrap)
    ├── DB/
    │   ├── connection.js               ← Sequelize instance + connectDB()
    │   └── Models/
    │       ├── User.model.js
    │       ├── ChatHistory.model.js
    │       ├── Place.model.js
    │       ├── MapLocation.model.js
    │       ├── TripPlan.model.js
    │       ├── PlanPlace.model.js      ← Junction (Many-to-Many)
    │       ├── BusBooking.model.js
    │       └── ContentUpdate.model.js
    ├── Middlewares/
    │   └── auth.middleware.js          ← protect + adminOnly
    └── Modules/
        ├── Auth/
        │   ├── auth.controller.js      ← Routes: /auth/register, /auth/login
        │   └── auth.services.js
        ├── Users/
        │   ├── user.controller.js      ← Routes: /users/me
        │   └── user.services.js
        ├── Places/
        │   ├── places.controller.js    ← Routes: /places
        │   └── places.services.js
        ├── TripPlan/
        │   ├── tripPlan.controller.js  ← Routes: /trip-plans
        │   └── tripPlan.services.js
        ├── BusBooking/
        │   ├── busBooking.controller.js ← Routes: /bus-booking
        │   └── busBooking.services.js
        ├── Chatbot/
        │   ├── chatbot.controller.js   ← Routes: /chatbot
        │   └── chatbot.services.js
        └── Admin/
            ├── admin.controller.js     ← Routes: /admin
            └── admin.services.js
```

## Setup
```bash
npm install
# Edit .env with your DB credentials
npm run dev
```

## API Endpoints

### Auth
| Method | Route | Auth |
|--------|-------|------|
| POST | /auth/register | Public |
| POST | /auth/login | Public |

### Users
| Method | Route | Auth |
|--------|-------|------|
| GET | /users/me | User |
| PUT | /users/me | User |

### Places
| Method | Route | Auth |
|--------|-------|------|
| GET | /places | Public |
| GET | /places/:id | Public |
| POST | /places | Admin |
| PUT | /places/:id | Admin |
| DELETE | /places/:id | Admin |

### Trip Plans
| Method | Route | Auth |
|--------|-------|------|
| POST | /trip-plans | User |
| GET | /trip-plans | User |
| GET | /trip-plans/:id | User |
| DELETE | /trip-plans/:id | User |

### Bus Booking
| Method | Route | Auth |
|--------|-------|------|
| POST | /bus-booking | User |
| GET | /bus-booking/my | User |
| PUT | /bus-booking/:id/cancel | User |
| GET | /bus-booking/all | Admin |
| PUT | /bus-booking/:id/confirm | Admin |

### Chatbot
| Method | Route | Auth |
|--------|-------|------|
| POST | /chatbot/ask | User |
| GET | /chatbot/history | User |

### Admin
| Method | Route | Auth |
|--------|-------|------|
| GET | /admin/users | Admin |
| GET | /admin/logs | Admin |
| GET | /admin/reports | Admin |
