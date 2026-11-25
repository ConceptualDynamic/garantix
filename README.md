# Garantix

**Pagos garantizados por instrucción legal, custodiados por el banco y gobernados por tecnología.**

Garantix es una legaltech venezolana que gobierna un sistema de escrow (pago en garantía): el dinero de una operación queda custodiado en un fideicomiso del banco y solo se libera cuando se cumplen las condiciones que las partes firmaron. Garantix define las reglas, emite las instrucciones y deja todo trazable; el banco custodia y ejecuta; los clientes y los aliados ven cada paso.

> Este es el repositorio público del proyecto. Explica qué es Garantix, cómo funciona y cómo está organizada la solución. La información sensible (contratos, condiciones comerciales, datos de clientes y configuración) vive en repositorios privados.

---

## Índice

1. [El problema](#el-problema)
2. [Cómo funciona](#cómo-funciona)
3. [Quién hace qué](#quién-hace-qué)
4. [Powered by Garantix](#powered-by-garantix)
5. [Para qué sirve](#para-qué-sirve)
6. [Red de aliados](#red-de-aliados)
7. [Transparencia](#transparencia)
8. [Arquitectura](#arquitectura)
9. [Módulos y repositorios](#módulos-y-repositorios)
10. [Seguridad y continuidad](#seguridad-y-continuidad)
11. [Hoja de ruta](#hoja-de-ruta)
12. [Marco legal](#marco-legal)
13. [Contacto](#contacto)

---

## El problema

En una compraventa, una obra, una importación o la compra de una empresa, alguien tiene que confiar primero: el que paga antes de recibir, o el que entrega antes de cobrar. Esa desconfianza frena negocios, encarece el crédito y termina en disputas.

Garantix elimina ese riesgo: el comprador deposita, el dinero queda protegido en el banco y el vendedor sabe que cobrará en cuanto cumpla.

## Cómo funciona

```
 1. Se crea la operación          El vendedor, un aliado o el ejecutivo del banco registra la operación
                                  y elige el tipo de uso (inmueble, vehículo, obra, importación...).
 2. Firma digital por correo      Las partes reciben por correo los documentos y los firman con firma
                                  electrónica certificada.
 3. Fondeo                        El comprador deposita en el fideicomiso del banco con una referencia única.
 4. Cumplimiento                  Se registran los hitos y las evidencias; si el contrato lo exige,
                                  un verificador independiente los certifica.
 5. Liberación por split          Garantix instruye al banco y, en un solo movimiento, el banco paga
                                  al beneficiario, cobra su comisión y abona la tarifa de Garantix.
 6. Factura y cierre              Se emite la factura digital y la operación queda cerrada y trazable.
```

Si la operación se cancela o hay una disputa, el contrato define qué pasa con el dinero, y Garantix publica para cada contrato las vías de resolución disponibles.

## Quién hace qué

| Actor | Rol |
|---|---|
| **Garantix** | Gobierna el sistema: reglas de cada tipo de operación, documentos, instrucciones al banco, trazabilidad y facturación de su tarifa. Responde ante el banco por el servicio. |
| **Banco aliado** | Fiduciario: custodia los fondos en un fideicomiso, verifica la identidad de sus clientes y ejecuta las instrucciones de liberación o devolución. |
| **Comprador / quien paga** | Deposita los fondos y confirma el cumplimiento. |
| **Vendedor / beneficiario** | Cumple lo pactado y cobra con la garantía de que el dinero ya existe. |
| **Verificador** | Un tercero independiente (por ejemplo, una de las Big Four u otro definido en el contrato) que certifica hitos en obras, proyectos, agro, energía y operaciones complejas. |
| **Aliados** | Profesionales y empresas que originan y acompañan operaciones. |

Ninguna empresa relacionada con los fundadores participa como verificador, piloto ni canal en las operaciones.

## Powered by Garantix

Los bancos venden el servicio con su propia marca, **Powered by Garantix**. El cliente ve a su banco; Garantix pone las reglas, la tecnología y la trazabilidad.

El primer banco aliado es **Bancamiga**. Garantix estará disponible en la **banca en línea de Bancamiga para personas y empresas**, en sus agencias y a través de la red de aliados.

¿Por qué le conviene al banco? Los fondos en fideicomiso forman un patrimonio separado y se registran en cuentas de orden, fuera de las obligaciones sobre las que se calcula el encaje legal. El banco custodia sin inmovilizar fondos y cobra su comisión fiduciaria.

## Para qué sirve

El modelo cubre más de 70 usos, agrupados así:

- **Inmobiliario:** compraventa, preventa y construcción; alquileres (fase 2).
- **Vehículos, maquinaria y bienes de alto valor.**
- **Comercio B2B y suministros.**
- **Comercio exterior:** importación y exportación contra documentos verificados.
- **Obras, proyectos y EPC:** telecomunicaciones, energía, infraestructura; pagos por hito certificado.
- **Agro y agroindustria.**
- **Contratación corporativa de gran escala** entre empresas privadas, pagada por hitos certificados. La contratación pública queda en evaluación, sujeta al marco de sanciones aplicable.
- **Compra de empresas (M&A) y activos.**
- **Fondos multilaterales y financiamiento de proyectos.**
- **Servicios profesionales, freelance y economía digital.**
- **Seguros y reaseguros.**
- **Propiedad intelectual y tecnología.**
- **Operaciones transfronterizas.**

## Red de aliados

La red de aliados es de Garantix y funciona con todos los bancos aliados. Pueden ser aliados corredores inmobiliarios y de seguros, abogados, contadores, ingenieros, peritos y verificadores, gremios y cámaras, marketplaces, constructoras, agentes de aduana, concesionarios, consultoras, fintechs y clientes que ya operaron con Garantix.

- Cada tipo de aliado tiene su propio módulo, donde ve en tiempo real el estado de las operaciones que refirió.
- Las recompensas son siempre bienes y beneficios (viajes, tecnología, financiamiento, formación, equipamiento), **nunca efectivo**.
- El cliente sabe quién refirió su operación y que ese aliado recibe una recompensa de Garantix. La recompensa no aumenta lo que paga el cliente.

## Transparencia

- Cada operación tiene una línea de tiempo con todos sus eventos: firmas, fondeo, hitos, instrucciones al banco y factura.
- Cada parte ve lo que le corresponde: el cliente su operación, el aliado sus referidos, el banco su cartera.
- Los documentos firmados quedan sellados con su huella digital (hash) y fecha, de modo que cualquier alteración se detecta.
- Este repositorio es público para que bancos, aliados e inversionistas conozcan cómo funciona el sistema.

## Arquitectura

```
                     ┌─────────────────────────────────────────────┐
  Clientes ─────────▶│  Banca en línea del banco · portales:       │
  Aliados  ─────────▶│  cliente · aliados · verificador · banco    │
  Banco    ─────────▶└──────────────────────┬──────────────────────┘
                                            │
                     ┌──────────────────────▼──────────────────────┐
                     │              Garantix Core (API)             │
                     │ operaciones · reglas por uso · documentos ·  │
                     │ instrucciones · split · auditoría · eventos  │
                     └───┬───────────┬───────────┬───────────┬─────┘
                         │           │           │           │
               ┌─────────▼──┐ ┌──────▼─────┐ ┌───▼───────┐ ┌─▼──────────────┐
               │  Conector  │ │ Firma y    │ │   Odoo    │ │ Verificación   │
               │  bancario  │ │ documentos │ │ facturas, │ │ de listas de   │
               │ (Bancamiga)│ │ (correo +  │ │ fiscal,   │ │ sancionados    │
               │            │ │ firma cert.)│ │ aliados   │ │                │
               └────────────┘ └────────────┘ └───────────┘ └────────────────┘
```

- El dinero nunca pasa por Garantix: está siempre en el fideicomiso del banco.
- El servicio se presta por API, con alta disponibilidad.
- La facturación y la separación fiscal se hacen en Odoo, con una imprenta digital autorizada por el SENIAT.
- Los documentos se firman con firma electrónica certificada por un proveedor acreditado ante SUSCERTE.

## Módulos y repositorios

| Repositorio | Contenido | Acceso |
|---|---|---|
| `garantix` | Este README: presentación pública del proyecto | Público |
| `garantix-docs` | Bases y decisiones, documento técnico, plan de 90 días, plan comercial, requerimientos al banco | Privado |
| `garantix-platform` | Garantix Core: API, motor de operaciones, reglas por uso, auditoría | Privado |
| `garantix-portals` | Módulo para la banca en línea (personas y empresas), portal de clientes, módulos de aliados (uno por tipo), verificador y backoffice del banco | Privado |
| `garantix-odoo` | Módulos de Odoo 20: facturación, separación fiscal, aliados y recompensas | Privado |
| `garantix-bank-connectors` | Conectores bancarios, empezando por Bancamiga | Privado |
| `garantix-signing` | Generación de documentos, envío por correo y firma electrónica | Privado |
| `garantix-legal` | Plantillas y borradores legales | Privado |

Los repositorios están hoy bajo la organización de Conceptual Dynamic, que desarrolla la tecnología, y se trasladarán a una organización propia de Garantix con acceso para sus miembros.

## Seguridad y continuidad

- Fondos siempre en el fideicomiso del banco; Garantix solo emite instrucciones.
- Exportación diaria al banco de cada operación y procedimiento manual de liberación previsto en el fideicomiso: si la plataforma se detiene, el banco puede seguir ejecutando.
- Alta disponibilidad, cifrado en tránsito y en reposo, y registro de auditoría inmutable.
- Verificación de todas las partes contra listas de sancionados al darlas de alta y antes de cada liberación.
- Ningún dato de clientes, contrato firmado ni credencial se guarda en repositorios de código.

## Hoja de ruta

| Etapa | Meta |
|---|---|
| **Días 1–30** | Primera operación real con Bancamiga, con firma digital por correo y factura electrónica |
| **Días 31–60** | Integración por API con el banco, módulos de todos los tipos de aliado, lanzamiento comercial en Bancamiga |
| **Días 61–90** | Garantix en la banca en línea de Bancamiga (personas y empresas), operación en todos los segmentos, verificadores, disputas y preparación del segundo banco |
| **Siguiente** | Más bancos en Venezuela, empresa en EE. UU. y expansión a Latinoamérica, EE. UU. y Europa |

Servicios de plataforma adicionales están marcados como **muy pronto**.

## Marco legal

Garantix opera en Venezuela con bancos e instituciones autorizadas como fiduciarios, bajo la Ley de Fideicomisos, las normas de SUDEBAN y del BCV, la Ley sobre Mensajes de Datos y Firmas Electrónicas, y las normas del SENIAT sobre facturación digital. Garantix no capta fondos del público ni custodia dinero de clientes.

## Contacto

Proyecto impulsado en el Venture Studio de Conceptual Group / Conceptual Dynamic.

---

© 2026 Garantix. Todos los derechos reservados.
