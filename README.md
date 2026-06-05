# 🇵🇪 Motor de Cálculo de Planillas

<p align="center">
  <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js" />
  <img src="https://img.shields.io/badge/Vitest-6E9F18?style=for-the-badge&logo=vitest&logoColor=white" alt="Vitest" />
  <img src="https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white" alt="Arch Linux" />
</p>

Un motor matemático fuertemente tipado, desacoplado y diseñado con una arquitectura orientada a dominios, construido para automatizar procesos complejos de planilla y beneficios laborales conforme a la legislación peruana.

> 💡 **Origen Arquitectónico:** Este motor fue desarrollado originalmente como parte de un sistema monolítico de planillas. Con el objetivo de eliminar deuda técnica y maximizar su reutilización, todo el núcleo computacional fue refactorizado y aislado exitosamente en esta librería independiente de cualquier infraestructura.

---

## 🛠️ Características Principales

El motor abstrae marcos normativos complejos y cambiantes en modelos matemáticos determinísticos:

* **Soporte Multi-Régimen:** Lógica de cálculo adaptada para los regímenes **General**, **MYPE (Micro y Pequeña Empresa)**, **Agrario (Ley 31110)** y **Construcción Civil (Convenios CAPECO)**.
* **Núcleo Matemático Puro:** Cero efectos secundarios. Cero consultas a bases de datos. Las funciones operan como cajas negras estrictamente determinísticas que reciben datos de entrada y generan resultados detallados.
* **Automatización de Beneficios Sociales:** Cálculo nativo de Compensación por Tiempo de Servicios (CTS), Gratificaciones, Vacaciones y Liquidaciones.
* **Procesamiento de Impuestos y Descuentos:** Cálculo integrado del Impuesto a la Renta de Quinta Categoría, ONP y sistemas privados de pensiones (AFP: aportes, seguros y comisiones).

---

## 📐 Arquitectura y Diseño de Patrones

El motor sigue un **Patrón de Diseño Paramétrico** basado en capas de datos puramente declarativas:

```
  [ Aplicación Consumidora / API / ERP ]
                  │
                  ▼ (CalcularPlanillaInput)
   ┌───────────────────────────────────────┐
   │      Enrutador Central del Motor      │
   │    (src/lib/calculations/index.ts)    │
   └───────────┬───────────┬───────────────┘
               │           │
      ┌────────┴────┐     ┌┴────────────┐
      │ MYPE/General│     │ Construcción│  ... (Otros Regímenes)
      └────────┬────┘     └┬────────────┘
               │           │
               ▼           ▼
   ┌───────────────────────────────────────┐
   │      Núcleo Matemático Aislado        │
   │ - Ingresos - Descuentos - Beneficios  │
   └───────────────────────────────────────┘
               │
               ▼ (ResultadoPlanilla)
```

### Ejemplo de Firma de Función Pura

```typescript
// Diseño determinístico: Los mismos parámetros de entrada
// siempre producirán exactamente el mismo resultado.
export function calcularAsignacionFamiliar(
  sueldoBase: number,
  tieneHijos: boolean
): number {
  if (!tieneHijos) return 0;
  return sueldoBase * ASIGNACION_FAMILIAR_PORCENTAJE; // Constante legal del 10%
}
```

---

## 🧪 Capa Robusta de Pruebas

La calidad del sistema se garantiza mediante suites exhaustivas de pruebas unitarias matemáticas. Los cálculos son validados contra escenarios regulatorios oficiales definidos por SUNAT y el MTPE.

```bash
# Ejecutar las pruebas de cálculo
npm run test
```

* Los archivos `*.test.ts` convierten escenarios reales de hojas de cálculo de planilla en aserciones de software para garantizar la integridad aritmética incluso en casos límite.

---

## 📦 Stack Tecnológico

* **Lenguaje:** TypeScript (Contratos de datos fuertemente tipados)
* **Entorno de Ejecución:** Node.js
* **Framework de Pruebas:** Vitest (Pruebas unitarias rápidas y eficientes)

---

## 👔 Métricas del Caso de Estudio

* **Dependencias:** 0 (Sin dependencias externas en tiempo de ejecución; ejecución puramente algorítmica).
* **Cobertura de Pruebas:** Más del 95% de cobertura de sentencias en los módulos financieros principales.
* **Factor de Acoplamiento:** 0% de dependencia con infraestructura (completamente desacoplado de ORMs, routers o conexiones a bases de datos).
