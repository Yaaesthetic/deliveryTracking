# PacketTracer - Pharmaceutical Distribution Tracking System

A comprehensive package tracking solution developed for SOREMED (Société de Répartition de Médicaments), consisting of desktop and mobile applications with a centralized backend system.

## 📋 Project Overview

This project addresses the inefficiencies in SOREMED's current pharmaceutical and parapharmaceutical product management system by providing:
- **Desktop Application**: User-friendly interface for entrepreneurs and administrators
- **Mobile Application**: Intuitive interface for delivery drivers  
- **Centralized Backend**: Data management and synchronization

## 🏗️ Architecture

The solution follows a three-tier architecture:

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Desktop App   │    │      Backend    │    │  Mobile App     │
│    (JavaFX)     │◄──►│  (Spring Boot)  │◄──►│   (Android)     │
│                 │    │                 │    │                 │
└─────────────────┘    └─────────────────┘    └─────────────────┘
                                 │                    │
                                 ▼                    ▼
                        ┌─────────────────┐    ┌─────────────────┐
                        │     MySQL       │sync│     SQLite      │
                        │   Database      │◄──►│    Database     │
                        └─────────────────┘    └─────────────────┘
```

## 🗂️ Project Structure

```
├── DesktopApp/              # JavaFX Desktop Application
│   ├── src/main/java/
│   │   └── com/example/packet_tracer/
│   │       ├── admin/       # Admin controllers
│   │       ├── expediteur/  # Sender controllers  
│   │       └── models/      # Data models
│   └── src/main/resources/  # FXML files and assets
│
├── PacketTracer/            # Android Mobile Application
│   └── app/src/main/java/
│       └── com/example/packettracer/
│           ├── model/       # Data models
│           └── utils/       # Utilities and adapters
│
└── packetTracerBase/        # Spring Boot Backend
    └── src/main/java/
        └── com/example/packettracerbase/
            ├── controller/  # REST API controllers
            ├── dto/         # Data Transfer Objects
            ├── model/       # Entity models
            ├── repository/  # Data access layer
            └── service/     # Business logic
```

## 🛠️ Technologies Used

### Backend
- **Framework**: Spring Boot
- **Database**: MySQL
- **ORM**: Hibernate
- **API**: RESTful services
- **Build Tool**: Maven

### Desktop Application  
- **Framework**: JavaFX
- **Language**: Java
- **Build Tool**: Maven

### Mobile Application
- **Platform**: Android
- **Language**: Java/Kotlin
- **Build Tool**: Gradle
- **HTTP Client**: Retrofit + OkHttp
- **Database**: Room (SQLite)
- **JSON Parsing**: Gson
- **Barcode Scanning**: ZXing

## ✨ Key Features

### For Administrators & Entrepreneurs
- Secure authentication with role-based access
- Product and inventory management
- Real-time package tracking
- Comprehensive reporting system
- Driver and client management
- Delivery route optimization

### For Delivery Drivers
- Mobile-optimized interface
- Barcode/QR code scanning
- GPS navigation and route optimization
- Real-time delivery status updates
- Offline functionality with data synchronization
- Digital delivery confirmations

### System Features
- Centralized data management
- Real-time synchronization between applications
- Role-based access control
- Comprehensive audit trails

## 🚀 Getting Started

### Prerequisites
- Java 11 or higher
- MySQL 8.0+
- Android Studio (for mobile app)
- Maven 3.6+

### Backend Setup
1. Clone the repository
2. Navigate to `packetTracerBase/`
3. Configure database connection in `application.properties`
4. Run the application:
   ```bash
   mvn spring-boot:run
   ```

### Desktop Application Setup
1. Navigate to `DesktopApp/`
2. Build and run:
   ```bash
   mvn javafx:run
   ```

### Mobile Application Setup
1. Open `PacketTracer/` in Android Studio
2. Sync project with Gradle files
3. Run on device or emulator

## 🔧 Development Tools

- **IDEs**: IntelliJ IDEA, Android Studio
- **API Testing**: Postman
- **Database Management**: XAMPP/phpMyAdmin
- **Version Control**: Git
- **UML Modeling**: Astah UML Community
- **Project Management**: Agile/SCRUM methodology

## 🏢 About SOREMED

SOREMED (Société de Répartition de Médicaments) is a pharmaceutical distribution company based in Agadir, Morocco, specializing in the distribution and supply of pharmaceutical and parapharmaceutical products to pharmacies across the region[1].

## 📱 API Endpoints

The backend provides comprehensive RESTful APIs for:
- `/api/admins` - Administrator management
- `/api/bordoreaux` - Delivery slip management  
- `/api/clients` - Client management
- `/api/drivers` - Driver management
- `/api/packets` - Package management
- `/api/secteurs` - Sector management
- `/api/transferts` - Transfer management
