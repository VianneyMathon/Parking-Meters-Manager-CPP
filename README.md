# Québec City Street Furniture Registry (C++)

Object-oriented C++ library, console app and Qt GUI that manage a registry of fire hydrants and parking meters, modelled on Québec City's open data. Course project, Université Laval, 2024.

## Features

- **Class hierarchy:** abstract `Borne` base class with two subclasses, `BorneFontaine` (fire hydrant: city, borough) and `BorneStationnement` (parking meter: meter number, street side).
- **Registry:** `RegistreBorne` stores polymorphic objects through `std::unique_ptr`, with deep copy (copy constructor and assignment) via `clone()`.
- **Design by contract:** preconditions, postconditions and class invariants checked at runtime.
- **Error handling:** custom exceptions for duplicate entries and missing IDs.
- **Data validation:** checks that a CSV file follows the city's parking meter format (header, required fields, street side, coordinates within Québec City).
- **Interfaces:** an interactive console program and a Qt 5 desktop app to add and remove entries.

## Tests

26 unit tests with Google Test, covering every class (`source/tests/`).

## Structure

All code is in `tp3-integration-equipe-212/TP3/`:

| Path | Content |
|---|---|
| `source/` | Library, CSV validation and unit tests |
| `utilisation/` | Console application |
| `BorneInterface/` | Qt 5 graphical interface |

## Build

The projects were built with NetBeans on Linux; the GUI requires Qt 5 (`qmake`). To compile the library and the console app directly:

```bash
cd tp3-integration-equipe-212/TP3
clang++ -std=c++14 -Isource source/*.cpp utilisation/BorneUtilisation.cpp -o utilisation_app
./utilisation_app
```

The design-by-contract framework (`ContratException`) was provided by the course.
