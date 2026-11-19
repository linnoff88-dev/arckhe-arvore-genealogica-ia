# ðŸŒ³ Ãrvore genealÃ³gica com IA

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


**ðŸ‡§ðŸ‡· [PortuguÃªs](README.md) Â· ðŸ‡ºðŸ‡¸ [English](README.en.md) Â· ðŸ‡ªðŸ‡¸ [EspaÃ±ol](README.es.md)**

[![Sua Ã¡rvore com IA](guia/assets/banner.jpg)](https://inematds.github.io/arvore-genealogica-ia/guia/)

## O que Ã©

Este Ã© um guia gratuito para montar a Ã¡rvore genealÃ³gica da sua famÃ­lia usando um chat de IA (ChatGPT, Claude, Gemini) do jeito certo. Ele explica o que o vÃ­deo viral "o ChatGPT acha seus parentes" acerta e onde a IA inventa pessoas. Traz 8 prompts prontos que obrigam a IA a mostrar a prova, a lista de acervos onde pesquisar de verdade e um checklist para conferir cada nome. Para usar, basta um chat de IA e, se quiser a Ã¡rvore desenhada, Python 3.

## ðŸ“– Guia de uso

Guia completo (landing + passo a passo): **https://inematds.github.io/arvore-genealogica-ia/guia/**

ðŸŽ¬ VÃ­deo (o que funciona e onde a IA inventa parentes): **https://inematds.github.io/arvore-genealogica-ia/videos/**

## A regra

> **A IA nÃ£o Ã© o detetive. Ã‰ a sua assistente. Quem confirma Ã© o documento.**

Toda pessoa nova na Ã¡rvore precisa de um registro com **nome + data + local** que vocÃª mesmo abriu. O resto fica marcado como **HIPÃ“TESE**.

## O que tem aqui

| Pasta | O que Ã© |
|---|---|
| [`docs/mito-verdade.md`](docs/mito-verdade.md) | Os 4 pedidos do vÃ­deo viral, um por um: o que funciona e por que a IA inventa parentes. |
| [`prompts/`](prompts/) | 8 prompts prontos: entrevista, tabela, ler documento antigo, onde procurar, pesquisa com prova, auditar resposta, cidadania, Ã¡rvore visual. |
| [`docs/onde-pesquisar.md`](docs/onde-pesquisar.md) | Acervos de verdade: FamilySearch, cartÃ³rio (inteiro teor), parÃ³quias, arquivos, Museu da ImigraÃ§Ã£o, Hemeroteca, Antenati, Digitarq, Matricula, DNA. |
| [`docs/checklist-conferencia.md`](docs/checklist-conferencia.md) | O que conferir antes de pÃ´r alguÃ©m na Ã¡rvore, e os sinais de invenÃ§Ã£o. |
| [`scripts/arvore.py`](scripts/arvore.py) | Transforma a tabela CSV em Ã¡rvore visual (HTML), com conferÃªncia automÃ¡tica. |
| [`modelos/pessoas.csv`](modelos/pessoas.csv) | Tabela de exemplo (famÃ­lia fictÃ­cia). |

## O processo, do inÃ­cio ao fim

| # | Passo | Comando / arquivo | Quem |
|---|---|---|---|
| 1 | Entrevistar a famÃ­lia e juntar os papÃ©is da casa | [`prompts/01-entrevista-familia.md`](prompts/01-entrevista-familia.md) | ðŸ§  vocÃª + chat de IA |
| 2 | Organizar tudo numa tabela com `fonte` e `status` | [`prompts/02-organizar-arvore.md`](prompts/02-organizar-arvore.md) â†’ `minha-familia.csv` | ðŸ§  vocÃª + chat de IA |
| 3 | Transcrever e traduzir documentos antigos (foto) | [`prompts/03-ler-documento-antigo.md`](prompts/03-ler-documento-antigo.md) | ðŸ§  vocÃª + chat de IA |
| 4 | Descobrir onde procurar e abrir cada link | [`prompts/04-onde-procurar.md`](prompts/04-onde-procurar.md) + [`docs/onde-pesquisar.md`](docs/onde-pesquisar.md) | ðŸ§  vocÃª |
| 5 | Pesquisar com prova (link direto, ou HIPÃ“TESE) | [`prompts/05-pesquisa-com-prova.md`](prompts/05-pesquisa-com-prova.md) | ðŸ§  vocÃª + chat com navegaÃ§Ã£o |
| 6 | Auditar listas que a IA jÃ¡ deu (chat novo) | [`prompts/06-auditar-resposta.md`](prompts/06-auditar-resposta.md) | ðŸ§  vocÃª + chat de IA |
| 7 | Conferir cada pessoa nova | [`docs/checklist-conferencia.md`](docs/checklist-conferencia.md) | ðŸ§  vocÃª |
| 8 | (Se quiser) lista de documentos para cidadania | [`prompts/07-cidadania-documentos.md`](prompts/07-cidadania-documentos.md) â†’ consulado | ðŸ§  vocÃª |
| 9 | Desenhar a Ã¡rvore com conferÃªncia automÃ¡tica | `python3 scripts/arvore.py minha-familia.csv --saida minha-arvore.html` | âš™ï¸ script |

## Rodar o script

```bash
git clone https://github.com/inematds/arvore-genealogica-ia
cd arvore-genealogica-ia
python3 scripts/arvore.py modelos/pessoas.csv --saida exemplo.html        # famÃ­lia fictÃ­cia
python3 scripts/arvore.py minha-familia.csv --so-confirmados --saida so-provas.html
python3 -m unittest discover tests                                        # 15 testes
py scripts\arvore.py minha-familia.csv --saida minha-arvore.html      # Windows (PowerShell)
```

O script nÃ£o tem dependÃªncias (sÃ³ Python 3); o HTML gerado precisa de internet para desenhar. Ele avisa quando:
- uma pessoa estÃ¡ **CONFIRMADO sem fonte**, ou com fonte genÃ©rica (sÃ³ o endereÃ§o do site), e a rebaixa para HIPÃ“TESE;
- um `pai_id`/`mae_id` nÃ£o existe na tabela;
- o pai ou a mÃ£e teria menos de 12 ou mais de 70 anos no nascimento do filho.

## Cidadania: atenÃ§Ã£o

As regras mudaram. A ItÃ¡lia limitou a cidadania por descendÃªncia em 2025 (Decreto-Lei 36/2025, convertido na Lei 74/2025), e Portugal mudou a Lei da Nacionalidade em 2025â€“2026, com partes questionadas no Tribunal Constitucional (informaÃ§Ã£o conferida em novembro de 2026). Este guia nÃ£o dÃ¡ parecer jurÃ­dico: confirme no consulado ou com um advogado especialista.

---

ConteÃºdo aberto e gratuito Â· [INEMA.CLUB](https://inema.club)

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>