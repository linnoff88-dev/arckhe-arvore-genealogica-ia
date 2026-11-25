# ê°Å¸ÅÂ³ êÂrbol genealêÂ³gico con IA

**ê°Å¸â¡Â§ê°Å¸â¡Â· [PortuguêÂªs](README.md) êÂ· ê°Å¸â¡Âºê°Å¸â¡Â¸ [English](README.en.md) êÂ· ê°Å¸â¡Âªê°Å¸â¡Â¸ [EspaêÂ±ol](README.es.md)**

[![Tu êÂ¡rbol con IA](guia/assets/banner-es.jpg)](https://linnoff88-dev.github.io/

## QuêÂ© es

Esta es una guêÂ­a gratuita para armar el êÂ¡rbol genealêÂ³gico de tu familia usando correctamente un chat de IA (ChatGPT, Claude, Gemini). Explica quêÂ© acierta el video viral êÂ«ChatGPT encuentra a tus familiaresêÂ» y dêÂ³nde la IA inventa personas. Incluye 8 prompts listos para usar que obligan a la IA a mostrar las pruebas, una lista de archivos donde investigar de verdad y una lista de verificaciêÂ³n para confirmar cada nombre. Para usarla, solo necesitas un chat de IA y, si quieres dibujar el êÂ¡rbol, Python 3.

## ê°Å¸ââ GuêÂ­a de uso

GuêÂ­a completa (pêÂ¡gina de presentaciêÂ³n + paso a paso): **https://linnoff88-dev.github.io/

ê°Å¸Å½Â¬ Video (quêÂ© funciona y dêÂ³nde la IA inventa parientes, en portuguêÂ©s): **https://linnoff88-dev.github.io/

## La regla

> **La IA no es la detective. Es tu asistente. Quien confirma es el documento.**

Toda persona nueva en el êÂ¡rbol necesita un registro con **nombre + fecha + lugar** que têÂº mismo hayas abierto. Lo demêÂ¡s queda marcado como **HIPêâTESIS**.

## QuêÂ© incluye

> Los prompts y documentos de `prompts/` y `docs/` estêÂ¡n en portuguêÂ©s (la pêÂ¡gina de la guêÂ­a trae todos los prompts en espaêÂ±ol).

| Carpeta | QuêÂ© es |
|---|---|
| [`docs/mito-verdade.md`](docs/mito-verdade.md) | Las 4 solicitudes del video viral, una por una: quêÂ© funciona y por quêÂ© la IA inventa familiares. |
| [`prompts/`](prompts/) | 8 prompts listos para usar: entrevista, tabla, leer un documento antiguo, dêÂ³nde buscar, investigaciêÂ³n con pruebas, auditar una respuesta, ciudadanêÂ­a, êÂ¡rbol visual. |
| [`docs/onde-pesquisar.md`](docs/onde-pesquisar.md) | Archivos reales: FamilySearch, registro civil (copia êÂ­ntegra), parroquias, archivos, Museu da ImigraêÂ§êÂ£o, Hemeroteca, Antenati, Digitarq, Matricula, ADN. |
| [`docs/checklist-conferencia.md`](docs/checklist-conferencia.md) | QuêÂ© confirmar antes de incluir a alguien en el êÂ¡rbol y las seêÂ±ales de invenciêÂ³n. |
| [`scripts/arvore.py`](scripts/arvore.py) | Transforma la tabla CSV en un êÂ¡rbol visual (HTML), con verificaciêÂ³n automêÂ¡tica. |
| [`modelos/personas.csv`](modelos/personas.csv) | Tabla de ejemplo en espaêÂ±ol (familia ficticia); PT: `pessoas.csv`, EN: `people.csv`. |

## El proceso, de principio a fin

| # | Paso | Comando / archivo | QuiêÂ©n |
|---|---|---|---|
| 1 | Entrevistar a la familia y reunir los documentos de la casa | [`prompts/01-entrevista-familia.md`](prompts/01-entrevista-familia.md) | ê°Å¸Â§Â  têÂº + chat de IA |
| 2 | Organizar todo en una tabla con `fuente` y `estado` | prompt 2 de la [guêÂ­a](https://linnoff88-dev.github.io/ ê¢â â `mi-familia.csv` | ê°Å¸Â§Â  têÂº + chat de IA |
| 3 | Transcribir y traducir documentos antiguos (foto) | [`prompts/03-ler-documento-antigo.md`](prompts/03-ler-documento-antigo.md) | ê°Å¸Â§Â  têÂº + chat de IA |
| 4 | Descubrir dêÂ³nde buscar y abrir cada enlace | [`prompts/04-onde-procurar.md`](prompts/04-onde-procurar.md) + [`docs/onde-pesquisar.md`](docs/onde-pesquisar.md) | ê°Å¸Â§Â  têÂº |
| 5 | Investigar con pruebas (enlace directo o HIPêâTESIS) | [`prompts/05-pesquisa-com-prova.md`](prompts/05-pesquisa-com-prova.md) | ê°Å¸Â§Â  têÂº + chat con navegaciêÂ³n |
| 6 | Auditar listas que la IA ya proporcionêÂ³ (chat nuevo) | [`prompts/06-auditar-resposta.md`](prompts/06-auditar-resposta.md) | ê°Å¸Â§Â  têÂº + chat de IA |
| 7 | Confirmar cada persona nueva | [`docs/checklist-conferencia.md`](docs/checklist-conferencia.md) | ê°Å¸Â§Â  têÂº |
| 8 | (Si quieres) lista de documentos para la ciudadanêÂ­a | [`prompts/07-cidadania-documentos.md`](prompts/07-cidadania-documentos.md) ê¢â â consulado | ê°Å¸Â§Â  têÂº |
| 9 | Dibujar el êÂ¡rbol con verificaciêÂ³n automêÂ¡tica | `python3 scripts/arvore.py mi-familia.csv --salida mi-arbol.html` | ê¢Å¡â¢ê¯Â¸Â script |

## Ejecutar el script

```bash
git clone https://github.com/linnoff88-dev/arvore-genealogica-ia
cd arvore-genealogica-ia
python3 scripts/arvore.py modelos/personas.csv --salida ejemplo.html       # familia ficticia
python3 scripts/arvore.py mi-familia.csv --solo-confirmados --salida solo-pruebas.html
python3 -m unittest discover tests                                        # 15 pruebas
py scripts\arvore.py mi-familia.csv --salida mi-arbol.html               # Windows (PowerShell)
```

El script tambiêÂ©n lee columnas en espaêÂ±ol (`id,nombre,nacimiento,lugar_nacimiento,padre_id,madre_id,fuente,estado,nota`, `CONFIRMADO`/`HIPêâTESIS`) y responde en espaêÂ±ol ê¢â¬â ver `modelos/personas.csv`.

El script no tiene dependencias (solo Python 3); el HTML generado necesita internet para dibujarse. Avisa cuando:
- una persona estêÂ¡ **CONFIRMADO sin fuente**, o con una fuente genêÂ©rica (solo la direcciêÂ³n del sitio), y la degrada a HIPêâTESIS;
- un `padre_id`/`madre_id` no existe en la tabla;
- el padre o la madre tendrêÂ­a menos de 12 o mêÂ¡s de 70 aêÂ±os cuando naciêÂ³ el hijo.

## CiudadanêÂ­a: atenciêÂ³n

Las reglas cambiaron. Italia limitêÂ³ la ciudadanêÂ­a por descendencia en 2025 (Decreto-Ley 36/2025, convertido en Ley 74/2025), y Portugal cambiêÂ³ la Ley de Nacionalidad en 2025ê¢â¬â2026, con partes cuestionadas ante el Tribunal Constitucional (informaciêÂ³n verificada en noviembre de 2026). Esta guêÂ­a no ofrece asesorêÂ­a legal: confirma la informaciêÂ³n en el consulado o con un abogado especialista.

---

Contenido abierto y gratuito êÂ· [ARCKHê AI](https://ARCKHê AI)
