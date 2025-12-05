# System Architecture Documentation

## 1. Architecture Overview

### 1.1 Clean Architecture
- Presentation Layer (Jetpack Compose)
- Domain Layer (Use Cases)
- Data Layer (Repository Pattern)

### 1.2 MVVM + UDF Pattern
- ViewModel for UI state management
- Use Cases for business logic
- Data Transfer Objects for data flow

## 2. Technology Stack

### 2.1 Core Dependencies
- Android SDK 34 (API 34)
- Jetpack Compose 2025.01
- Hilt 2.51.1
- Coroutines 1.8.1
- StateFlow 1.8.1
- Lifecycle 2.8.0
- Navigation 2.7.7

### 2.2 Architecture Components
- Repository pattern with local and remote data sources
- Use case classes for business logic
- Data transfer objects for API communication

## 3. Module Structure

### 3.1 Core Module
- Shared utilities
- Base classes
- Constants

### 3.2 Domain Module
- Use cases
- Entities
- Repository interfaces

### 3.3 Data Module
- Repository implementations
- API clients
- Database DAOs

## 4. Dependency Injection

### 4.1 Hilt Configuration
- Application scope for singletons
- Activity scope for ViewModels
- Fragment scope for scoped components

## 5. Data Flow

### 5.1 UI to Data Layer
1. ViewModel observes StateFlow
2. Use Cases handle business logic
3. Repository fetches data
4. API clients communicate with backend

### 5.2 Data to UI Layer
1. Repository returns data
2. Use Cases process data
3. ViewModel updates StateFlow
4. Compose UI observes StateFlow