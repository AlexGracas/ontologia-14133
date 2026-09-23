# Ontologia da Lei 14.133/2021 (Nova Lei de Licitações)

Ontologia de domínio para o processo de **licitações e contratações públicas**
brasileiro, modelada a partir da **Lei nº 14.133, de 1º de abril de 2021**, com
apoio da ontologia de fundamentação **UFO** (*Unified Foundational Ontology*),
proposta por Giancarlo Guizzardi em sua tese seminal *Ontological Foundations
for Structural Conceptual Models* (Guizzardi, 2005) e consolidada em Guizzardi
et al., *Towards ontological foundations for conceptual modeling: the unified
foundational ontology (UFO) story* (Applied Ontology, 2015). O arquivo OWL usa
concretamente a **gUFO**, a implementação de UFO em OWL/RDF para a Web
Semântica.

O modelo cobre, entre outros temas, os atores do processo (agente de
contratação, equipe de apoio, comissão de contratação, pregoeiro, licitante),
os documentos de planejamento (DFD, ETP, Termo de Referência, PCA), as
modalidades e fases da licitação, a contratação direta (dispensa e
inexigibilidade) e a gestão de riscos (matriz de riscos, probabilidade,
gravidade de impacto, respostas a risco).

Este trabalho está sendo produzido para submissão de um **pôster na OntoBras
2026** (Ontology Brasil), apresentando o modelo conceitual e a abordagem de
verificação por perguntas de competência descrita abaixo.

## Estrutura do repositório

| Caminho | Conteúdo |
|---|---|
| `Licitacao14133.vpp` | Modelo-fonte no Visual Paradigm (diagramas de classes, notas, etc.) |
| `Licitacao14133.ttl` | Exportação mais recente da ontologia em OWL/Turtle |
| `pictures/` | Diagramas de classes exportados (visão geral, ETP, riscos, processo licitatório/autoridade) |
| `requisitos/` | Requisitos da ontologia — perguntas de competência (Markdown) |
| `Queries/` | Consultas SPARQL que respondem às perguntas de competência |
| `poster/` | Pôster em produção para a **OntoBras 2026** |

## Requisitos e verificação (perguntas de competência)

Os requisitos de escopo da ontologia estão formalizados como **perguntas de
competência (QC1–QC20)** em
[`requisitos/perguntas-competencia.md`](requisitos/perguntas-competencia.md),
organizadas em cinco blocos temáticos: atores e responsabilidades,
planejamento e documentos, modalidades e fases da licitação, contratação
direta, e gestão de riscos.

Cada pergunta possui uma consulta SPARQL correspondente em
[`Queries/`](Queries/), construída diretamente sobre as classes e
propriedades da ontologia exportada. Veja [`Queries/README.md`](Queries/README.md)
para o detalhamento de cada consulta e as lacunas de esquema identificadas
durante essa verificação.

## Pôster — OntoBras 2026

O pôster que apresenta este trabalho na OntoBras 2026 está em
[`poster/Template_PosterOntobras2026_A02.pdf`](poster/Template_PosterOntobras2026_A02.pdf)
(formato A0, versão em PDF pronta para impressão).

## Ferramentas

O modelo é editado no **Visual Paradigm** (`Licitacao14133.vpp`) e exportado
para OWL/Turtle. A ontologia de fundamentação teórica é a **UFO** (Guizzardi),
importada no arquivo `.ttl` por meio de sua implementação em OWL, a **gUFO**
(`http://purl.org/nemo/gufo#`).

## Referências

- GUIZZARDI, G. *Ontological Foundations for Structural Conceptual Models*.
  2005. Tese (Doutorado) — University of Twente, Enschede, The Netherlands.
- GUIZZARDI, G.; WAGNER, G.; ALMEIDA, J. P. A.; GUIZZARDI, R. S. S. *Towards
  ontological foundations for conceptual modeling: the unified foundational
  ontology (UFO) story*. Applied Ontology, v. 10, n. 3-4, p. 259-271, 2015.
- LEI Nº 14.133, DE 1º DE ABRIL DE 2021 —
  https://www.planalto.gov.br/ccivil_03/_ato2019-2022/2021/lei/l14133.htm
