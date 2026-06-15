# ShopLedger

> Closed-source business management tool built for a real end-user — currently in active use.

ShopLedger is a modular management system designed to handle **client credit/debt tracking** and **weekly/monthly cash flow reporting** for a small business. Requirements were gathered directly from the end-user, with continuous iterative delivery throughout development.

What makes it architecturally interesting is that it ships **two fully independent presentation layers** — a WPF desktop app and a .NET MAUI mobile app — both powered by the exact same business logic, thanks to Onion Architecture.

---

## Tech Stack

| Layer        | Technology                                               |
| ------------ | -------------------------------------------------------- |
| Architecture | Onion Architecture                                       |
| Language     | C# / .NET                                                |
| ORM          | Entity Framework Core (Code First)                       |
| Database     | SQLite                                                   |
| Desktop UI   | WPF + MVVM                                               |
| Mobile UI    | .NET MAUI + MVVM                                         |
| Mapping      | AutoMapper                                               |
| Patterns     | Generic Repositories, Generic Services, DTOs, ViewModels |
| Validation   | Field-level validation across all input forms            |

---

## Features

- **Client Management** — Register clients and log credit/payment movements
- **Account Balance** — Per-client history with running balance
- **Daily Sales** — Record daily revenue alongside eventual expenses
- **Fixed Expenses** — Manage recurring monthly obligations (rent, utilities, etc.)
- **Weekly Profit Report** — Auto-calculated from sales minus eventual expenses
- **Monthly Profit Report** — Derived from weekly net profits minus fixed expenses

---

## Screenshots

### Desktop (WPF)

**Client Overview — credit and payment management**
![Client Overview](https://raw.githubusercontent.com/MintKurisu/ShopLedger-Showcase/main/assets/desktop/desktop-clients-overview.png)

---

**Client History & Management**
![Client History](https://raw.githubusercontent.com/MintKurisu/ShopLedger-Showcase/main/assets/desktop/desktop-client-history.png)

---

**Daily Sales Module — calendar view + weekly summary**
![Daily Sales](https://raw.githubusercontent.com/MintKurisu/ShopLedger-Showcase/main/assets/desktop/desktop-daily-sales.png)

---

**Fixed Expenses**
![Fixed Expenses](https://raw.githubusercontent.com/MintKurisu/ShopLedger-Showcase/main/assets/desktop/desktop-fixed-expenses.png)

---

**Monthly Summary**
![Monthly Summary](https://raw.githubusercontent.com/MintKurisu/ShopLedger-Showcase/main/assets/desktop/desktop-monthly-summary.png)

---

### Mobile (.NET MAUI)

**Client Overview**
![Client Overview Mobile](https://raw.githubusercontent.com/MintKurisu/ShopLedger-Showcase/main/assets/mobile/mobile-clients-overview.png)

---

**Client History & Management**
![Client History Mobile](https://raw.githubusercontent.com/MintKurisu/ShopLedger-Showcase/main/assets/mobile/mobile-client-history.png)

---

**Daily Sales Module**
![Daily Sales Mobile](https://raw.githubusercontent.com/MintKurisu/ShopLedger-Showcase/main/assets/mobile/mobile-daily-sales.png)

---

**Fixed Expenses**
![Fixed Expenses Mobile](https://raw.githubusercontent.com/MintKurisu/ShopLedger-Showcase/main/assets/mobile/mobile-fixed-expenses.png)

---

**Monthly Summary** — supports flexible week ranges; a full monthly report can be generated regardless of how many weeks were recorded
![Monthly Summary Mobile](https://raw.githubusercontent.com/MintKurisu/ShopLedger-Showcase/main/assets/mobile/mobile-monthly-summary.png)

---

## Architecture Overview

```
ShopLedger/
├── ShopLedger.Domain/          # Entities, interfaces
├── ShopLedger.Application/     # Services, DTOs, AutoMapper profiles
├── ShopLedger.Persistence/     # EF Core DbContext, repositories, migrations
├── ShopLedger.WPF/             # Desktop presentation layer (WPF + MVVM)
└── ShopLedger.MAUI/            # Mobile presentation layer (.NET MAUI + MVVM)
```

The Domain and Application layers are fully UI-agnostic. Both presentation layers depend inward — neither the WPF nor the MAUI project influences business logic.

---

## Status

Currently in active use by the end-user. Source code is closed-source; this repository serves as a project showcase.
