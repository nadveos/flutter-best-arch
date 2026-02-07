---
name: flutter-best-arch
description: Arquitectura Flutter real con Riverpod, Clean Architecture y soporte multiplataforma
---

# Skill: Flutter App Real Architecture (Riverpod)

## Objetivo
Desarrollar aplicaciones Flutter reales, escalables y multiplataforma
siguiendo Clean Architecture adaptada a Flutter.

---

## Estructura obligatoria

lib/
 ├── config/
 │    ├── router/
 │    ├── themes/
 │    ├── environment/
 │    ├── platform/
 │
 ├── domain/
 │    ├── datasources/        # Contratos (abstract)
 │    ├── models/             # Modelos de negocio PUROS
 │    ├── repositories/       # Interfaces
 │
 ├── infrastructure/
 │    ├── datasources/        # Firebase / API / DB
 │    ├── entities/           # DTOs / modelos persistencia
 │    ├── mappers/            # Entity <-> Domain
 │    ├── repositories/       # Implementaciones
 │
 ├── presentation/
 │    ├── screens/
 │    ├── widgets/
 │    ├── providers/          # Riverpod
 │    ├── services/           # Helpers UI (NO lógica negocio)
 │
 └── l10n/
      ├── app_en.arb
      ├── app_es.arb

---

## State Management
- Riverpod obligatorio
- Providers por feature
- UI reactiva, sin lógica de negocio

---

## Reglas de dependencias
- presentation → domain
- infrastructure → domain
- domain NO depende de nadie
- Widgets NO llaman repositorios

---

## Backend
- Repositorios abstractos en domain
- Implementaciones intercambiables:
  - Firebase
  - PocketBase
  - REST API

---

## Multiplataforma
- NO usar dart:io directamente
- Usar adaptadores de plataforma
- Responsive obligatorio (mobile/web/desktop)

---

## Errores
- Failure / Result pattern
- Nunca lanzar excepciones a la UI

---

## Testing
- Unit tests en domain
- Widget tests para pantallas críticas
