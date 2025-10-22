# Configuración del Sistema - Settings

Panel de configuración avanzada para CotareloManage

## Configuración General

El módulo de configuración permite personalizar todos los aspectos del sistema educativo según las necesidades específicas de cada institución.

## Información del Centro

| Campo     | Valor Actual              | Tipo     | Requerido |
|-----------|---------------------------|----------|-----------|
| Nombre    | IES Armando Cotarelo      | Texto    | ✅        |
| Código    | 28001234                  | Numérico | ✅        |
| Dirección | C/ Educación, 123         | Texto    | ✅        |
| Teléfono  | +34 91 123 4567           | Tel      | ✅        |
| Email     | info@iestecmadrid.edu.es  | Email    | ✅        |
| Web       | www.iestecmadrid.edu.es   | URL      | ❌        |

## Configuración Académica

Sistema de Calificaciones

El sistema utiliza múltiples escalas de evaluación:

**Escala Numérica (Por defecto):**

- 📊 0-10 con decimales
- 🎯 Mínimo aprobado: 5.0
- ⭐ Excelente: 9.0+

**Escala Alfabética (Opcional):**

- 🅰️ A (Sobresaliente): 9-10
- 🅱️ B (Notable): 7-8.9
- 🅲️ C (Bien): 6-6.9
- 🅳️ D (Suficiente): 5-5.9
- 🅵 F (Insuficiente): 0-4.9

## Cálculo de Promedios 🧮

La nota final se calcula usando la fórmula ponderada (en bloque de código para máxima compatibilidad):

```
NF = (E1*P1 + E2*P2 + ... + En*Pn) / (P1 + P2 + ... + Pn)
```

Donde:
- NF: Nota Final
- E1, E2, ..., En: Evaluaciones
- P1, P2, ..., Pn: Peso de cada evaluación (la suma debe ser 1 o 100%)

**Ejemplo práctico:**
```
Evaluaciones: P1 = 6, P2 = 8, PF = 7
Pesos: 0.3, 0.3, 0.4
NF = (6*0.3 + 8*0.3 + 7*0.4) / (0.3+0.3+0.4) = 7.0
```

### Evaluación Continua 📈

Para asignaturas con evaluación continua:
```
NC = 0.4*P1 + 0.4*P2 + 0.2*PF
```

**Ejemplo:**
```
P1 = 7, P2 = 8, PF = 9
NC = 0.4*7 + 0.4*8 + 0.2*9 = 7.8
```

### Conversión a Escala Alfabética 🅰️🅱️

```
9-10 -> A (Sobresaliente)
7-8.9 -> B (Notable)
6-6.9 -> C (Bien)
5-5.9 -> D (Suficiente)
0-4.9 -> F (Insuficiente)
```

⚠️ Notas Importantes:
- Redondea las notas finales a 2 decimales.
- Reinicia el sistema después de cambios críticos en la configuración.