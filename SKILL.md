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
 │    ├── router/             # Rutas y navegación
 │    ├── themes/             # Temas claros/oscuro/contraste alto nunca utlizar estilos en línea
 │    ├── environment/
 │    ├── platform/           # Adaptadores de plataforma (ej: FilePicker, Camera)
 │
 ├── domain/
 │    ├── datasources/        # Contratos (abstract)
 │    ├── models/             # Modelos de negocio PUROS
 │    ├── repositories/       # Interfaces
 │
 ├── infrastructure/
 │    ├── datasources/        # Implementaciones de contratos Firebase / API / DB
 │    ├── entities/           # DTOs / modelos persistencia
 │    ├── mappers/            # Entity <-> Domain
 │    ├── repositories/       # Implementaciones de repositorios (Firebase / API / DB)
 │
 ├── presentation/
 │    ├── screens/
 │    ├── widgets/            # Widgets reutilizables puros sin lógica de negocio
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
- Codigo listo para implementaciones intercambiables:
  - Firebase
  - PocketBase
  - REST API

---
## Internacionalización
- Soporte obligatorio para múltiples idiomas
- Uso de .arb files y Flutter Intl

## Accesibilidad
- Soporte obligatorio para lectores de pantalla
- Contraste de colores adecuado
- Etiquetas semánticas en widgets
- Navegación accesible (teclado, screen readers)
- Widgets adaptativos para diferentes tamaños y orientaciónes de pantalla

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
