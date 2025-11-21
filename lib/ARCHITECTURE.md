# Project Architecture - By Dependency Flow

This project follows a **dependency-flow** architecture where layers are organized by their dependencies, creating a clear, unidirectional data flow from lowest to highest dependencies.

## 📁 Directory Structure

```txt
lib/
├── 01_common/       # No dependencies
├── 02_domain/       # Depends on common
├── 03_data/         # Depends on common + domain
├── 04_presentation/ # Depends on common + domain + data
└── 05_app/          # Depends on everything
```

## 🏗️ Layer Overview

### [01_common/](01_common/README.md) - Foundation Layer

- **Purpose**: Zero-dependency utilities and constants
- **Dependencies**: None (only external packages)
- **Contains**: `constants/`, `utils/`, `themes/`, `extensions/`

### [02_domain/](02_domain/README.md) - Business Logic  

- **Purpose**: Core business rules and entities
- **Dependencies**: `01_common/`
- **Contains**: `entities/`, `repositories/`, `use_cases/`

### [03_data/](03_data/README.md) - Data Layer

- **Purpose**: Data implementation and external APIs
- **Dependencies**: `01_common/` + `02_domain/`
- **Contains**: `models/`, `repositories_impl/`, `data_sources/`

### [04_presentation/](04_presentation/README.md) - UI Layer

- **Purpose**: User interface and presentation logic
- **Dependencies**: `01_common/` + `02_domain/` + `03_data/`
- **Contains**: `pages/`, `widgets/`, `controllers/`, `views/`

### [05_app/](05_app/README.md) - App Configuration

- **Purpose**: App composition and startup
- **Dependencies**: Everything
- **Contains**: App widget, routing, dependency injection

## 🚀 Getting Started

1. **Start with** `01_common/` for basic utilities
2. **Define business logic** in `02_domain/`
3. **Implement data sources** in `03_data/`
4. **Build UI** in `04_presentation/`
5. **Wire everything** in `05_app/`

## 📚 Further Reading

- Each layer has its own [README.md](01_common/README.md) with detailed documentation
- See [CONTRIBUTING.md](../CONTRIBUTING.md) for development guidelines

 ---

<sub>This document was AI-generated but refined by a human.</sub>
