# ê°Å¸ÅÂ³ êÂrvore genealêÂ³gica com IA

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


**ê°Å¸â¡Â§ê°Å¸â¡Â· [PortuguêÂªs](README.md) êÂ· ê°Å¸â¡Âºê°Å¸â¡Â¸ [English](README.en.md) êÂ· ê°Å¸â¡Âªê°Å¸â¡Â¸ [EspaêÂ±ol](README.es.md)**

[![Sua êÂ¡rvore com IA](guia/assets/banner.jpg)](https://linnoff88-dev.github.io/

## O que êÂ©

Este êÂ© um guia gratuito para montar a êÂ¡rvore genealêÂ³gica da sua famêÂ­lia usando um chat de IA (ChatGPT, Claude, Gemini) do jeito certo. Ele explica o que o vêÂ­deo viral "o ChatGPT acha seus parentes" acerta e onde a IA inventa pessoas. Traz 8 prompts prontos que obrigam a IA a mostrar a prova, a lista de acervos onde pesquisar de verdade e um checklist para conferir cada nome. Para usar, basta um chat de IA e, se quiser a êÂ¡rvore desenhada, Python 3.

## ê°Å¸ââ Guia de uso

Guia completo (landing + passo a passo): **https://linnoff88-dev.github.io/

ê°Å¸Å½Â¬ VêÂ­deo (o que funciona e onde a IA inventa parentes): **https://linnoff88-dev.github.io/

## A regra

> **A IA nêÂ£o êÂ© o detetive. êâ° a sua assistente. Quem confirma êÂ© o documento.**

Toda pessoa nova na êÂ¡rvore precisa de um registro com **nome + data + local** que vocêÂª mesmo abriu. O resto fica marcado como **HIPêâTESE**.

## O que tem aqui

| Pasta | O que êÂ© |
|---|---|
| [`docs/mito-verdade.md`](docs/mito-verdade.md) | Os 4 pedidos do vêÂ­deo viral, um por um: o que funciona e por que a IA inventa parentes. |
| [`prompts/`](prompts/) | 8 prompts prontos: entrevista, tabela, ler documento antigo, onde procurar, pesquisa com prova, auditar resposta, cidadania, êÂ¡rvore visual. |
| [`docs/onde-pesquisar.md`](docs/onde-pesquisar.md) | Acervos de verdade: FamilySearch, cartêÂ³rio (inteiro teor), parêÂ³quias, arquivos, Museu da ImigraêÂ§êÂ£o, Hemeroteca, Antenati, Digitarq, Matricula, DNA. |
| [`docs/checklist-conferencia.md`](docs/checklist-conferencia.md) | O que conferir antes de pêÂ´r alguêÂ©m na êÂ¡rvore, e os sinais de invenêÂ§êÂ£o. |
| [`scripts/arvore.py`](scripts/arvore.py) | Transforma a tabela CSV em êÂ¡rvore visual (HTML), com conferêÂªncia automêÂ¡tica. |
| [`modelos/pessoas.csv`](modelos/pessoas.csv) | Tabela de exemplo (famêÂ­lia fictêÂ­cia). |

## O processo, do inêÂ­cio ao fim

| # | Passo | Comando / arquivo | Quem |
|---|---|---|---|
| 1 | Entrevistar a famêÂ­lia e juntar os papêÂ©is da casa | [`prompts/01-entrevista-familia.md`](prompts/01-entrevista-familia.md) | ê°Å¸Â§Â  vocêÂª + chat de IA |
| 2 | Organizar tudo numa tabela com `fonte` e `status` | [`prompts/02-organizar-arvore.md`](prompts/02-organizar-arvore.md) ê¢â â `minha-familia.csv` | ê°Å¸Â§Â  vocêÂª + chat de IA |
| 3 | Transcrever e traduzir documentos antigos (foto) | [`prompts/03-ler-documento-antigo.md`](prompts/03-ler-documento-antigo.md) | ê°Å¸Â§Â  vocêÂª + chat de IA |
| 4 | Descobrir onde procurar e abrir cada link | [`prompts/04-onde-procurar.md`](prompts/04-onde-procurar.md) + [`docs/onde-pesquisar.md`](docs/onde-pesquisar.md) | ê°Å¸Â§Â  vocêÂª |
| 5 | Pesquisar com prova (link direto, ou HIPêâTESE) | [`prompts/05-pesquisa-com-prova.md`](prompts/05-pesquisa-com-prova.md) | ê°Å¸Â§Â  vocêÂª + chat com navegaêÂ§êÂ£o |
| 6 | Auditar listas que a IA jêÂ¡ deu (chat novo) | [`prompts/06-auditar-resposta.md`](prompts/06-auditar-resposta.md) | ê°Å¸Â§Â  vocêÂª + chat de IA |
| 7 | Conferir cada pessoa nova | [`docs/checklist-conferencia.md`](docs/checklist-conferencia.md) | ê°Å¸Â§Â  vocêÂª |
| 8 | (Se quiser) lista de documentos para cidadania | [`prompts/07-cidadania-documentos.md`](prompts/07-cidadania-documentos.md) ê¢â â consulado | ê°Å¸Â§Â  vocêÂª |
| 9 | Desenhar a êÂ¡rvore com conferêÂªncia automêÂ¡tica | `python3 scripts/arvore.py minha-familia.csv --saida minha-arvore.html` | ê¢Å¡â¢ê¯Â¸Â script |

## Rodar o script

```bash
git clone https://github.com/linnoff88-dev/arvore-genealogica-ia
cd arvore-genealogica-ia
python3 scripts/arvore.py modelos/pessoas.csv --saida exemplo.html        # famêÂ­lia fictêÂ­cia
python3 scripts/arvore.py minha-familia.csv --so-confirmados --saida so-provas.html
python3 -m unittest discover tests                                        # 15 testes
py scripts\arvore.py minha-familia.csv --saida minha-arvore.html      # Windows (PowerShell)
```

O script nêÂ£o tem dependêÂªncias (sêÂ³ Python 3); o HTML gerado precisa de internet para desenhar. Ele avisa quando:
- uma pessoa estêÂ¡ **CONFIRMADO sem fonte**, ou com fonte genêÂ©rica (sêÂ³ o endereêÂ§o do site), e a rebaixa para HIPêâTESE;
- um `pai_id`/`mae_id` nêÂ£o existe na tabela;
- o pai ou a mêÂ£e teria menos de 12 ou mais de 70 anos no nascimento do filho.

## Cidadania: atenêÂ§êÂ£o

As regras mudaram. A ItêÂ¡lia limitou a cidadania por descendêÂªncia em 2025 (Decreto-Lei 36/2025, convertido na Lei 74/2025), e Portugal mudou a Lei da Nacionalidade em 2025ê¢â¬â2026, com partes questionadas no Tribunal Constitucional (informaêÂ§êÂ£o conferida em novembro de 2026). Este guia nêÂ£o dêÂ¡ parecer jurêÂ­dico: confirme no consulado ou com um advogado especialista.

---

ConteêÂºdo aberto e gratuito êÂ· [ARCKHê AI](https://ARCKHê AI)

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>