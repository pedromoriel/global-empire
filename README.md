# global-empire
Virtual Economy income to real life

## Concepto
App/juego móvil (Android + iPhone) estilo *Atlas Earth* donde el jugador compra terrenos virtuales y genera renta por segundo en una economía sustentada por criptomoneda (ejemplo: **PEPE coin**).

## Loop principal del juego
1. Usuario se registra e inicia sesión.
2. Compra terrenos virtuales por parcelas.
3. Cada parcela genera renta automática por segundo según su rareza.
4. Usuario puede reinvertir ganancias o solicitar retiro (wallet externa).
5. Usuario puede ver anuncios para desbloquear boosts y mantener la economía de la app.

## Tipos de tierra y renta base por segundo
| Tipo de tierra | Rareza | Renta base (PEPE/seg) | Costo relativo |
|---|---|---:|---:|
| Regular | Común | 0.10 | 1x |
| Rara | Poco común | 0.35 | 3x |
| Premium | Alta | 1.00 | 8x |
| Ultra | Épica | 2.50 | 20x |

> Nota: Valores iniciales sugeridos para balance. Ajustar con telemetría en producción.

## Fórmula de ganancias
`ganancia_por_segundo = suma(renta_base_de_cada_parcela) * multiplicadores_activos`

Ejemplos de multiplicadores:
- Boost por anuncio: +20% durante 30 minutos.
- Eventos temporales: +10% a +50%.
- Bonus por colección de zonas completas.

## Economía cripto (PEPE coin)
- **Wallet interna** para saldo del juego.
- **Conversión clara** entre moneda del juego y PEPE.
- **Retiros** a wallet externa con:
  - mínimo de retiro,
  - comisión de red,
  - validaciones antifraude/KYC (*Know Your Customer*: verificación de identidad) según jurisdicción.
- Registro auditable de transacciones (depósitos, compras, recompensas, retiros).

## Monetización con anuncios
- Recompensados (rewarded ads): boosts temporales, cofres, tickets de ruleta.
- Intersticiales moderados entre pantallas no críticas.
- Límite de frecuencia para no afectar retención.
- Segmentación por país/plataforma para optimizar eCPM.

## Arquitectura funcional (MVP)
- **Cliente móvil**: recomendado **Flutter** para MVP por velocidad de desarrollo cross-platform. Alternativas: Unity (si se prioriza experiencia 3D) o React Native (si se prioriza ecosistema web/JS).
- **Backend**:
  - gestión de usuario/inventario,
  - cálculo de renta en tiempo real o por intervalos,
  - ledger de economía,
  - módulo de anuncios y recompensas.
- **Servicios blockchain**:
  - integración de wallet,
  - orquestación de transferencias,
  - monitoreo de estado de red.

## Roadmap sugerido
1. **MVP**: compra de parcelas, renta por segundo, saldo y anuncios recompensados.
2. **Beta**: marketplace entre usuarios, mapas por zonas, misiones diarias.
3. **v1**: retiros en cripto, eventos en vivo, sistema social (clanes/rankings).

## Riesgos y cumplimiento
- Cumplimiento legal (cripto, premios, impuestos) por país.
- Prevención de bots y granjas de anuncios.
- Balance económico para evitar inflación de recompensas.
