
# Clinic Booking System Database Schema

# Patients Table
CREATE TABLE Patients (
    patient_id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    date_of_birth DATE,
    phone_number VARCHAR(20),
    email VARCHAR(100) UNIQUE
);

# Doctors Table
CREATE TABLE Doctors (
    doctor_id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    specialty VARCHAR(50)
);

# Appointments Table
CREATE TABLE Appointments (
    appointment_id INT PRIMARY KEY AUTO_INCREMENT,
    patient_id INT,
    doctor_id INT,
    appointment_date DATE NOT NULL,
    appointment_time TIME NOT NULL,
    reason_for_visit TEXT,
    room_id INT,
    FOREIGN KEY (patient_id) REFERENCES Patients(patient_id),
    FOREIGN KEY (doctor_id) REFERENCES Doctors(doctor_id),
    FOREIGN KEY (room_id) REFERENCES Rooms(room_id)
);

# Rooms Table
CREATE TABLE Rooms (
    room_id INT PRIMARY KEY AUTO_INCREMENT,
    room_number VARCHAR(10) UNIQUE,
    room_type VARCHAR(50)
);

# Resources Table
CREATE TABLE Resources (
    resource_id INT PRIMARY KEY AUTO_INCREMENT,
    resource_name VARCHAR(100),
    resource_type VARCHAR(50)
);

# Room_Resources Table (Many-to-Many relationship between Rooms and Resources)
CREATE TABLE Room_Resources (
    room_id INT,
    resource_id INT,
    PRIMARY KEY (room_id, resource_id),
    FOREIGN KEY (room_id) REFERENCES Rooms(room_id),
    FOREIGN KEY (resource_id) REFERENCES Resources(resource_id)
);

# Services Table
CREATE TABLE Services (
    service_id INT PRIMARY KEY AUTO_INCREMENT,
    service_name VARCHAR(100) NOT NULL,
    description TEXT
);

# Appointment_Services Table (Many-to-Many relationship between Appointments and Services)
CREATE TABLE Appointment_Services (
    appointment_id INT,
    service_id INT,
    PRIMARY KEY (appointment_id, service_id),
    FOREIGN KEY (appointment_id) REFERENCES Appointments(appointment_id),
    FOREIGN KEY (service_id) REFERENCES Services(service_id)
 
 
 
 ## Clinic Booking System

 ## Overview:

A relational database for managing clinic operations, including patient records and appointment scheduling.

 ## Setup:

1.  **Install MySQL.**
2.  **Create Database:`CREATE DATABASE clinic_db;`**
3.  **Import Schema: `mysql -u root -p clinic_db < clinic_booking_system.sql**

 ## Schema:

Key tables: Patients, Doctors, Appointments.

 ## ERD:

[Include ERD Image or Link Here]

 ## Technologies:

*   MySQL
*   SQL

 ## Author

[ALABA JIMOH]
