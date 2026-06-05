# 🇵🇪 Peruvian Payroll Calculation Engine

<p align="center">
  <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js" />
  <img src="https://img.shields.io/badge/Vitest-6E9F18?style=for-the-badge&logo=vitest&logoColor=white" alt="Vitest" />
  <img src="https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white" alt="Arch Linux" />
</p>

An architecture-first, decoupled, and strongly-typed mathematical engine built to automate complex payroll processing and statutory benefits under Peruvian labor regulations.

> 💡 **Architectural Origin:** This engine was originally developed as part of a monolithic payroll system. To eliminate technical debt and maximize reusability, the entire computational core was successfully refactored and isolated into this infrastructure-agnostic library.

---

## 🛠️ Key Features

The engine abstracts complex, shifting legal frameworks into deterministic mathematical models:

* **Multi-Regime Support:** Tailored compliance computation logic for **General**, **MYPE (Micro/Small Enterprise)**, **Agrarian (Law 31110)**, and **Civil Construction (CAPECO agreements)** labor regimes.
* **Pure Mathematical Core:** Zero side-effects. Zero database roundtrips. Functions are structured as strict black boxes that process raw data inputs and map out detailed payload itemizations.
* **Statutory Benefits Automated:** Native calculations for Compensación por Tiempo de Servicios (CTS), Gratificaciones, Vacaciones, and Liquidaciones.
* **Tax & Deductions Processing:** Built-in computation for 5th Category Income Tax (Quinta Categoría), ONP, and private pension systems (AFP insurance, commissions, and contributions).

---

## 📐 Architecture & Pattern Design

The engine adheres to a **Parametric Design Pattern** utilizing purely declarative data layers:

```
  [ Consumer App / API / ERP ]
               │
               ▼ (CalcularPlanillaInput)
   ┌───────────────────────────────────────┐
   │         Central Engine Router         │
   │      (src/lib/calculations/index.ts)  │
   └───────────┬───────────┬───────────────┘
               │           │
      ┌────────┴────┐     ┌┴────────────┐
      │ MYPE/General│     │ Civil Const.│  ... (Other Regimes)
      └────────┬────┘     └┬────────────┘
               │           │
               ▼           ▼
   ┌───────────────────────────────────────┐
   │     Isolated Mathematical Core        │
   │  - Revenue  - Deductions  - Benefits  │
   └───────────────────────────────────────┘
               │
               ▼ (ResultadoPlanilla)
```

### Pure Function Signature Example

```typescript
// Deterministic design: Same input parameters will always produce the exact same outcome.
export function calcularAsignacionFamiliar(
  sueldoBase: number, 
  tieneHijos: boolean
): number {
  if (!tieneHijos) return 0;
  return sueldoBase * ASIGNACION_FAMILIAR_PORCENTAJE; // 10% statutory constant
}
```

---

## 🧪 Robust Testing Layer

Quality assurance is enforced via exhaustive mathematical unit test suites. The calculations are verified against official regulatory scenarios provided by SUNAT and MTPE.

```bash
# Run the calculation test suites
npm run test
```

* `*.test.ts` files map real-world payroll spreadsheets into software assertions to ensure arithmetic integrity across edge cases.

---

## 📦 Tech Stack

* **Language:** TypeScript (Strongly-typed data contracts)
* **Runtime Environment:** Node.js
* **Testing Framework:** Vitest (Fast unit assertion testing)

---

## 👔 Portfolio Case Study Metrics

* **Dependencies:** 0 (Zero external runtime dependencies; pure algorithmic execution).
* **Test Coverage:** Over 95% statement coverage across core financial modules.
* **Coupling Factor:** 0% infrastructure binding (Completely detached from ORMs, routers, or database connections).
