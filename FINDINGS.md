# OUROBOROS LAB — Findings (2026-02-15)

**Estado:** GREEN (Ciclo límite confirmado)  
**Repositorio:** Gahenax/Calculo2  
**Run:** results/ouroboros_official_green  
**Seed:** 42

## 1) Resumen ejecutivo
OUROBOROS LAB demuestra un mecanismo general en sistemas de optimización gobernada: la interacción entre **optimización local (Ω)** y **costo global (H)** induce una dinámica de **ciclo límite** bajo retroalimentación negativa y disipación finita.  
Conclusión: la gobernanza no es solo restricción; es un motor de estabilidad de largo plazo.

> Nota de honestidad científica: este experimento es un **toy model** mecanístico. No prueba una ley física universal ni contradice termodinámica clásica. Su propósito es mostrar un mecanismo de sistemas complejos reproducible y falsable.

## 2) Comportamiento del sistema (fases)
### A. Arranque (Transient)
Ω crece inicialmente (tipo logístico). Cada incremento de orden produce H (costo global).  
En control sin gobernanza, la dinámica converge a estasis (cristalización) o pierde capacidad de exploración.

### B. Acoplamiento (Governance feedback)
Al superar el umbral de gobernanza, H penaliza el progreso de Ω mediante incremento de ruido/errores (probabilidad de movimiento aleatorio proporcional a H).  
La disipación reduce H gradualmente, evitando crecimiento explosivo del costo.

### C. Ciclo límite (Steady state)
El sistema entra en oscilación autosostenida: **Ω sube → H sube → ruido sube → Ω cae → H cae por disipación → Ω se recupera**.  
**Score de autocorrelación:** 0.7115 (estructura periódica fuerte; 1.0 sería onda perfecta).

## 3) Parámetros (nomenclatura auditada)
Para evitar colisión con el código del laboratorio, se reportan parámetros con nombres no ambiguos:

| Parámetro | Valor | Rol |
|---|---:|---|
| alpha_opt | 0.5 | Impulso de optimización local (regla del demonio) |
| kappa (g_strength) | 0.2 | Fuerza de gobernanza: retroalimentación negativa (acopla H → ruido) |
| beta_heat | 0.1 | Generación de costo/entropía por avance (H por éxito) |
| gamma_diss | 0.05 | Disipación del costo (enfriamiento) |
| steps | 2000 | Ventana temporal |
| seed | 42 | Reproducibilidad |

## 4) Criterios de falsación y resultados
### Control (RED esperado)
**Configuración:** kappa = 0  
**Resultado:** estasis (Ω se estabiliza sin dinámica respiratoria).  
**Interpretación:** sin costo acoplado no emerge ciclo límite.

### Caos (colapso por gobernanza excesiva)
**Configuración:** kappa alto sin disipación proporcional  
**Resultado:** colapso (ruido domina, Ω no se sostiene).  
**Interpretación:** gobernanza excesiva sin capacidad de disipación es tan letal como la ausencia de gobernanza.

## 5) Conclusión para la tesis (Aprendizaje gobernado)
Los datos apoyan que el aprendizaje sostenible requiere ciclos de “enfriamiento” (disipación de entropía/costo). La estabilidad surge como **equilibrio dinámico**, no como cierre estático.

## 6) Artefactos de verificación
- `results/ouroboros_official_green/verdict.json`
- `results/ouroboros_official_green/omega_ouroboros.npy`
- `OUROBOROS_HYPOTHESIS.md`
