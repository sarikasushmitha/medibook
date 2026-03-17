# 🏥 MediBook — Doctor Appointment Booking System

<div align="center">

![MediBook Banner](https://img.shields.io/badge/MediBook-Doctor%20Appointment%20System-0d9488?style=for-the-badge&logo=health&logoColor=white)

[![.NET](https://img.shields.io/badge/.NET-8.0-512BD4?style=flat-square&logo=dotnet)](https://dotnet.microsoft.com/)
[![Angular](https://img.shields.io/badge/Angular-17-DD0031?style=flat-square&logo=angular)](https://angular.io/)
[![SQLite](https://img.shields.io/badge/SQLite-EF%20Core-003B57?style=flat-square&logo=sqlite)](https://www.sqlite.org/)
[![Angular Material](https://img.shields.io/badge/Angular-Material-757575?style=flat-square&logo=material-design)](https://material.angular.io/)
[![Swagger](https://img.shields.io/badge/Swagger-Docs-85EA2D?style=flat-square&logo=swagger)](https://swagger.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)

**A full-stack doctor appointment booking system built with ASP.NET Core 8 and Angular 17.**  
Patients can register, browse doctors, book time slots, and manage their appointments.

[Live Demo](#) · [API Docs](#api-documentation) · [Report Bug](issues) · [Request Feature](issues)

</div>

---

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Backend Setup](#backend-setup)
  - [Frontend Setup](#frontend-setup)
- [API Documentation](#-api-documentation)
- [Database Schema](#-database-schema)
- [Screenshots](#-screenshots)
- [Deployment](#-deployment)
- [Contributing](#-contributing)
- [License](#-license)

---

## ✨ Features

### 👤 Patient
- Register and log in to a personal account
- Browse all available doctors with specialty info
- View doctor profiles and available time slots
- Book an appointment with a single click
- View all upcoming and past appointments
- Cancel scheduled appointments

### 🩺 Doctor
- View upcoming appointment schedule
- Patient details per appointment

### 🔧 System
- Auto-seeded database with 5 doctors and weekly slots
- Swagger UI for API exploration and testing
- Clean Architecture with Repository + Service pattern
- CORS configured for local and production environments

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| **Backend** | ASP.NET Core 8 Web API |
| **Frontend** | Angular 17 (Standalone Components) |
| **UI Library** | Angular Material |
| **Database** | SQLite via Entity Framework Core |
| **Architecture** | Clean Architecture, Repository + Service Pattern |
| **API Docs** | Swagger / OpenAPI |
| **Auth** | BCrypt password hashing + token-based session |
| **Deployment** | Netlify (frontend) + Render (backend) |

---

## 📁 Project Structure

```
medibook/
├── Backend/                          # ASP.NET Core 8 Web API
│   ├── Controllers/
│   │   ├── AuthController.cs         # Register & Login
│   │   ├── DoctorsController.cs      # List, detail, slots
│   │   └── AppointmentsController.cs # Book, list, cancel
│   ├── Models/
│   │   ├── Patient.cs
│   │   ├── Doctor.cs
│   │   ├── TimeSlot.cs
│   │   └── Appointment.cs
│   ├── DTOs/
│   │   ├── AuthDTOs.cs
│   │   ├── DoctorDTOs.cs
│   │   └── AppointmentDTOs.cs
│   ├── Repositories/
│   │   ├── Interfaces/
│   │   │   ├── IPatientRepository.cs
│   │   │   ├── IDoctorRepository.cs
│   │   │   └── IAppointmentRepository.cs
│   │   └── Implementations/
│   │       ├── PatientRepository.cs
│   │       ├── DoctorRepository.cs
│   │       └── AppointmentRepository.cs
│   ├── Services/
│   │   ├── Interfaces/
│   │   │   ├── IAuthService.cs
│   │   │   └── IAppointmentService.cs
│   │   └── Implementations/
│   │       ├── AuthService.cs
│   │       └── AppointmentService.cs
│   ├── Data/
│   │   ├── AppDbContext.cs
│   │   └── DbSeeder.cs               # Seeds 5 doctors + weekly slots
│   ├── Migrations/
│   ├── Program.cs
│   ├── appsettings.json
│   ├── appsettings.Development.json
│   └── MediBook.API.csproj
│
├── Frontend/                         # Angular 17 Application
│   ├── src/
│   │   ├── app/
│   │   │   ├── components/
│   │   │   │   ├── navbar/
│   │   │   │   │   ├── navbar.component.ts
│   │   │   │   │   └── navbar.component.scss
│   │   │   │   └── appointment-card/
│   │   │   │       ├── appointment-card.component.ts
│   │   │   │       └── appointment-card.component.scss
│   │   │   ├── pages/
│   │   │   │   ├── login/
│   │   │   │   │   └── login.component.ts
│   │   │   │   ├── register/
│   │   │   │   │   └── register.component.ts
│   │   │   │   ├── doctors/
│   │   │   │   │   └── doctors.component.ts
│   │   │   │   ├── doctor-details/
│   │   │   │   │   └── doctor-details.component.ts
│   │   │   │   ├── book-appointment/
│   │   │   │   │   └── book-appointment.component.ts
│   │   │   │   └── my-appointments/
│   │   │   │       └── my-appointments.component.ts
│   │   │   ├── services/
│   │   │   │   ├── auth.service.ts
│   │   │   │   ├── doctor.service.ts
│   │   │   │   └── appointment.service.ts
│   │   │   ├── models/
│   │   │   │   ├── auth.model.ts
│   │   │   │   ├── doctor.model.ts
│   │   │   │   └── appointment.model.ts
│   │   │   ├── guards/
│   │   │   │   └── auth.guard.ts
│   │   │   ├── app.component.ts
│   │   │   ├── app.config.ts
│   │   │   └── app.routes.ts
│   │   ├── environments/
│   │   │   ├── environment.ts          # Local: localhost:5000
│   │   │   └── environment.prod.ts     # Production: Render URL
│   │   ├── styles.scss
│   │   └── index.html
│   ├── angular.json
│   ├── package.json
│   └── tsconfig.json
│
├── .gitignore
├── LICENSE
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:

| Tool | Version | Download |
|---|---|---|
| .NET SDK | 8.0+ | [dotnet.microsoft.com](https://dotnet.microsoft.com/download) |
| Node.js | 18.0+ | [nodejs.org](https://nodejs.org/) |
| Angular CLI | 17.0+ | `npm install -g @angular/cli` |
| EF Core Tools | Latest | `dotnet tool install --global dotnet-ef` |

---

### Backend Setup

```bash
# 1. Clone the repository
git clone https://github.com/your-username/medibook.git
cd medibook/Backend

# 2. Restore NuGet packages
dotnet restore

# 3. Apply database migrations (creates medibook.db)
dotnet ef migrations add InitialCreate
dotnet ef database update

# 4. Run the API
dotnet run
```

> **API running at:** `http://localhost:5000`  
> **Swagger UI at:** `http://localhost:5000/swagger`

The database is **auto-seeded** on first run with:
- 5 specialist doctors
- Available time slots for the next 7 weekdays (6 slots/day per doctor)

---

### Frontend Setup

```bash
# 1. Navigate to frontend
cd medibook/Frontend

# 2. Install dependencies
npm install

# 3. Start the dev server
ng serve
```

> **App running at:** `http://localhost:4200`

The Angular app is pre-configured to call `http://localhost:5000/api`.  
Make sure the backend is running before opening the frontend.

---

## 📖 API Documentation

Full Swagger docs available at `http://localhost:5000/swagger` when running locally.

### Endpoints

#### Auth
| Method | Endpoint | Description | Auth Required |
|---|---|---|---|
| `POST` | `/api/auth/register` | Register a new patient | No |
| `POST` | `/api/auth/login` | Login and receive token | No |

#### Doctors
| Method | Endpoint | Description | Auth Required |
|---|---|---|---|
| `GET` | `/api/doctors` | Get all doctors | No |
| `GET` | `/api/doctors/{id}` | Get doctor by ID | No |
| `GET` | `/api/doctors/{id}/slots` | Get available time slots | No |

#### Appointments
| Method | Endpoint | Description | Auth Required |
|---|---|---|---|
| `POST` | `/api/appointments/book` | Book an appointment | Yes |
| `GET` | `/api/appointments/patient/{patientId}` | Get patient's appointments | Yes |
| `DELETE` | `/api/appointments/{id}` | Cancel an appointment | Yes |

### Example Requests

**Register**
```json
POST /api/auth/register
{
  "name": "Jane Smith",
  "email": "jane@example.com",
  "password": "securepassword123"
}
```

**Book Appointment**
```json
POST /api/appointments/book
{
  "patientId": 1,
  "doctorId": 2,
  "timeSlotId": 15
}
```

---

## 🗃 Database Schema

```
┌─────────────┐       ┌─────────────┐
│   Patient   │       │   Doctor    │
├─────────────┤       ├─────────────┤
│ Id (PK)     │       │ Id (PK)     │
│ Name        │       │ Name        │
│ Email       │       │ Specialty   │
│ PasswordHash│       │ Description │
└──────┬──────┘       └──────┬──────┘
       │                     │
       │    ┌─────────────┐  │
       │    │ Appointment │  │
       │    ├─────────────┤  │
       └───►│ PatientId   │◄─┘
            │ DoctorId    │
            │ TimeSlotId ─┼──────┐
            │ Status      │      │
            │ CreatedAt   │  ┌───▼──────┐
            └─────────────┘  │ TimeSlot │
                             ├──────────┤
                             │ Id (PK)  │
                             │ DoctorId │
                             │ StartTime│
                             │ EndTime  │
                             │IsAvailable│
                             └──────────┘
```

---

## 🌐 Deployment

### Frontend → Netlify (Free)

```bash
# Build for production
cd Frontend
ng build --configuration production

# Deploy
# 1. Go to netlify.com
# 2. Drag & drop the dist/medibook-frontend/browser folder
# OR connect your GitHub repo with:
#    Build command:   ng build --configuration production
#    Publish dir:     dist/medibook-frontend/browser
```

Add a `_redirects` file to your publish directory:
```
/* /index.html 200
```

### Backend → Render (Free)

1. Push to GitHub
2. Go to [render.com](https://render.com) → New Web Service
3. Connect your repo and set:
   - **Build Command:** `dotnet publish -c Release -o out`
   - **Start Command:** `dotnet out/MediBook.API.dll`
   - **Environment Var:** `ASPNETCORE_URLS=http://0.0.0.0:10000`

Update `environment.prod.ts` with your Render URL before building the frontend:
```typescript
export const environment = {
  production: true,
  apiUrl: 'https://your-app.onrender.com/api'
};
```

> ⚠️ **Note:** SQLite on Render's free tier uses an ephemeral filesystem. For persistent data, use [Supabase PostgreSQL](https://supabase.com) (free tier available) and swap the SQLite provider for `Npgsql` in `Program.cs`.

---

## 🔮 Roadmap

- [ ] JWT Bearer token authentication
- [ ] Doctor login and schedule management
- [ ] Email confirmation via SendGrid
- [ ] Search and filter doctors by specialty
- [ ] Pagination for doctor/appointment lists
- [ ] PostgreSQL support for production
- [ ] Unit tests (xUnit + Jasmine/Karma)
- [ ] GitHub Actions CI/CD pipeline
- [ ] Appointment reminders (SMS via Twilio)

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a Pull Request

Please make sure your code follows the existing style and all existing functionality still works.

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [Angular Material](https://material.angular.io/) for the UI component library
- [Entity Framework Core](https://docs.microsoft.com/en-us/ef/core/) for database management
- [BCrypt.Net](https://github.com/BcryptNet/bcrypt.net) for password hashing
- [Swagger / Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) for API documentation

---

<div align="center">
Made with ❤️ using ASP.NET Core + Angular
</div>
