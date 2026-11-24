# ðŸŒ³ Ãrbol genealÃ³gico con IA

**ðŸ‡§ðŸ‡· [PortuguÃªs](README.md) Â· ðŸ‡ºðŸ‡¸ [English](README.en.md) Â· ðŸ‡ªðŸ‡¸ [EspaÃ±ol](README.es.md)**

[![Tu Ã¡rbol con IA](guia/assets/banner-es.jpg)](https://linnoff88-dev.github.io/

## QuÃ© es

Esta es una guÃ­a gratuita para armar el Ã¡rbol genealÃ³gico de tu familia usando correctamente un chat de IA (ChatGPT, Claude, Gemini). Explica quÃ© acierta el video viral Â«ChatGPT encuentra a tus familiaresÂ» y dÃ³nde la IA inventa personas. Incluye 8 prompts listos para usar que obligan a la IA a mostrar las pruebas, una lista de archivos donde investigar de verdad y una lista de verificaciÃ³n para confirmar cada nombre. Para usarla, solo necesitas un chat de IA y, si quieres dibujar el Ã¡rbol, Python 3.

## ðŸ“– GuÃ­a de uso

GuÃ­a completa (pÃ¡gina de presentaciÃ³n + paso a paso): **https://linnoff88-dev.github.io/

ðŸŽ¬ Video (quÃ© funciona y dÃ³nde la IA inventa parientes, en portuguÃ©s): **https://linnoff88-dev.github.io/

## La regla

> **La IA no es la detective. Es tu asistente. Quien confirma es el documento.**

Toda persona nueva en el Ã¡rbol necesita un registro con **nombre + fecha + lugar** que tÃº mismo hayas abierto. Lo demÃ¡s queda marcado como **HIPÃ“TESIS**.

## QuÃ© incluye

> Los prompts y documentos de `prompts/` y `docs/` estÃ¡n en portuguÃ©s (la pÃ¡gina de la guÃ­a trae todos los prompts en espaÃ±ol).

| Carpeta | QuÃ© es |
|---|---|
| [`docs/mito-verdade.md`](docs/mito-verdade.md) | Las 4 solicitudes del video viral, una por una: quÃ© funciona y por quÃ© la IA inventa familiares. |
| [`prompts/`](prompts/) | 8 prompts listos para usar: entrevista, tabla, leer un documento antiguo, dÃ³nde buscar, investigaciÃ³n con pruebas, auditar una respuesta, ciudadanÃ­a, Ã¡rbol visual. |
| [`docs/onde-pesquisar.md`](docs/onde-pesquisar.md) | Archivos reales: FamilySearch, registro civil (copia Ã­ntegra), parroquias, archivos, Museu da ImigraÃ§Ã£o, Hemeroteca, Antenati, Digitarq, Matricula, ADN. |
| [`docs/checklist-conferencia.md`](docs/checklist-conferencia.md) | QuÃ© confirmar antes de incluir a alguien en el Ã¡rbol y las seÃ±ales de invenciÃ³n. |
| [`scripts/arvore.py`](scripts/arvore.py) | Transforma la tabla CSV en un Ã¡rbol visual (HTML), con verificaciÃ³n automÃ¡tica. |
| [`modelos/personas.csv`](modelos/personas.csv) | Tabla de ejemplo en espaÃ±ol (familia ficticia); PT: `pessoas.csv`, EN: `people.csv`. |

## El proceso, de principio a fin

| # | Paso | Comando / archivo | QuiÃ©n |
|---|---|---|---|
| 1 | Entrevistar a la familia y reunir los documentos de la casa | [`prompts/01-entrevista-familia.md`](prompts/01-entrevista-familia.md) | ðŸ§  tÃº + chat de IA |
| 2 | Organizar todo en una tabla con `fuente` y `estado` | prompt 2 de la [guÃ­a](https://linnoff88-dev.github.io/ â†’ `mi-familia.csv` | ðŸ§  tÃº + chat de IA |
| 3 | Transcribir y traducir documentos antiguos (foto) | [`prompts/03-ler-documento-antigo.md`](prompts/03-ler-documento-antigo.md) | ðŸ§  tÃº + chat de IA |
| 4 | Descubrir dÃ³nde buscar y abrir cada enlace | [`prompts/04-onde-procurar.md`](prompts/04-onde-procurar.md) + [`docs/onde-pesquisar.md`](docs/onde-pesquisar.md) | ðŸ§  tÃº |
| 5 | Investigar con pruebas (enlace directo o HIPÃ“TESIS) | [`prompts/05-pesquisa-com-prova.md`](prompts/05-pesquisa-com-prova.md) | ðŸ§  tÃº + chat con navegaciÃ³n |
| 6 | Auditar listas que la IA ya proporcionÃ³ (chat nuevo) | [`prompts/06-auditar-resposta.md`](prompts/06-auditar-resposta.md) | ðŸ§  tÃº + chat de IA |
| 7 | Confirmar cada persona nueva | [`docs/checklist-conferencia.md`](docs/checklist-conferencia.md) | ðŸ§  tÃº |
| 8 | (Si quieres) lista de documentos para la ciudadanÃ­a | [`prompts/07-cidadania-documentos.md`](prompts/07-cidadania-documentos.md) â†’ consulado | ðŸ§  tÃº |
| 9 | Dibujar el Ã¡rbol con verificaciÃ³n automÃ¡tica | `python3 scripts/arvore.py mi-familia.csv --salida mi-arbol.html` | âš™ï¸ script |

## Ejecutar el script

```bash
git clone https://github.com/linnoff88-dev/arvore-genealogica-ia
cd arvore-genealogica-ia
python3 scripts/arvore.py modelos/personas.csv --salida ejemplo.html       # familia ficticia
python3 scripts/arvore.py mi-familia.csv --solo-confirmados --salida solo-pruebas.html
python3 -m unittest discover tests                                        # 15 pruebas
py scripts\arvore.py mi-familia.csv --salida mi-arbol.html               # Windows (PowerShell)
```

El script tambiÃ©n lee columnas en espaÃ±ol (`id,nombre,nacimiento,lugar_nacimiento,padre_id,madre_id,fuente,estado,nota`, `CONFIRMADO`/`HIPÃ“TESIS`) y responde en espaÃ±ol â€” ver `modelos/personas.csv`.

El script no tiene dependencias (solo Python 3); el HTML generado necesita internet para dibujarse. Avisa cuando:
- una persona estÃ¡ **CONFIRMADO sin fuente**, o con una fuente genÃ©rica (solo la direcciÃ³n del sitio), y la degrada a HIPÃ“TESIS;
- un `padre_id`/`madre_id` no existe en la tabla;
- el padre o la madre tendrÃ­a menos de 12 o mÃ¡s de 70 aÃ±os cuando naciÃ³ el hijo.

## CiudadanÃ­a: atenciÃ³n

Las reglas cambiaron. Italia limitÃ³ la ciudadanÃ­a por descendencia en 2025 (Decreto-Ley 36/2025, convertido en Ley 74/2025), y Portugal cambiÃ³ la Ley de Nacionalidad en 2025â€“2026, con partes cuestionadas ante el Tribunal Constitucional (informaciÃ³n verificada en noviembre de 2026). Esta guÃ­a no ofrece asesorÃ­a legal: confirma la informaciÃ³n en el consulado o con un abogado especialista.

---

Contenido abierto y gratuito Â· [ARCKHÉ AI](https://ARCKHÉ AI)
