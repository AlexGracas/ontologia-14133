# Consultas SPARQL — Perguntas de Competência

Este diretório contém uma consulta SPARQL (`.rq`) para cada uma das 20 perguntas de
competência definidas em [`../requisitos/perguntas-competencia.md`](../requisitos/perguntas-competencia.md),
construídas a partir do OWL exportado em `../Licitacao14133-2026-08-25.ttl`.

## Como usar

Cada arquivo `QCxx_*.rq` traz, em sequência, dois a quatro blocos de consulta,
separados por um cabeçalho comentado (`# ====...`). Copie um bloco de cada vez para
seu endpoint/ferramenta SPARQL (ex.: um triple store carregado com o `.ttl`, ou
`rdflib` em Python).

Cada arquivo segue o mesmo padrão:

1. **Definição** — rótulo (`rdfs:label`) e descrição (`rdfs:comment`) da(s) classe(s)
   central(is) da pergunta. Sempre retorna resultado, pois consulta o próprio
   esquema (TBox) da ontologia.
2. **Hierarquia** — subclasses ou superclasses relevantes (ex.: as modalidades de
   licitação, os tipos de resposta a risco), via `rdfs:subClassOf+`.
3. **Propriedades relacionadas** — todas as propriedades de objeto/dados cujo
   domínio ou range é a classe em questão, revelando de que elementos ela é
   composta ou a que outras classes se conecta.
4. **Consulta de instâncias** — o padrão de consulta que responde à pergunta sobre
   dados reais (licitações, agentes, riscos concretos etc.). Algumas perguntas usam
   um marcador `<X>` (ex. QC5, QC12), a ser substituído pelo valor concreto (número
   do processo, nome do serviço) na hora do uso.

## Por que as consultas de instâncias retornam vazio hoje

O arquivo `Licitacao14133-2026-08-25.ttl` contém apenas a **TBox** — 126 classes e
suas propriedades — sem indivíduos (ABox). Todas as consultas foram validadas
(sintaxe SPARQL 1.1 correta) e executadas contra o arquivo atual:

- Os blocos de **definição**, **hierarquia** e **propriedades relacionadas**
  retornam resultados reais agora mesmo.
- Os blocos de **instâncias** retornam 0 linhas hoje, por design — eles descrevem o
  padrão de consulta correto para quando dados concretos (licitações, agentes,
  propostas, riscos etc.) forem carregados na mesma base.

## Observações sobre lacunas identificadas no esquema

- **QC1/QC3**: não há uma propriedade explícita que ligue diretamente
  `AgenteDeContratacao`/`ComissaoDeContratacao` a uma `Licitacao` conduzida, nem uma
  propriedade que modele a substituição do agente pela comissão — a resposta hoje
  depende do texto em `rdfs:comment` das classes (ver `QC01` bloco 3 e `QC03`).
- **QC12**: `CriterioJulgamento` só está formalmente ligado a um processo via
  `:leilaoHasCriterioJulgamento` (domínio `Leilao`); não existe ainda uma
  propriedade genérica `Licitacao -> CriterioJulgamento`, nem um atributo de
  nome/identificação em `ObjetoLicitado` para filtrar por serviço `<X>` — a consulta
  usa o campo `:attribute` como aproximação e está comentada em `QC12`.
- **QC16**: não há uma propriedade de dados para o limite de valor da dispensa; o
  valor atualizado (R$ 250.902.323,87) está registrado como texto livre em
  `rdfs:comment` de `:DispensaDeLicitacao`.

## Arquivos

| Arquivo | Pergunta de competência |
|---|---|
| `QC01_agente_de_contratacao.rq` | QC1 — Agente de contratação |
| `QC02_equipe_apoio.rq` | QC2 — Função da equipe de apoio |
| `QC03_substituicao_comissao_contratacao.rq` | QC3 — Substituição por comissão |
| `QC04_fiscal_contrato.rq` | QC4 — Atribuições do fiscal do contrato |
| `QC05_licitante_no_processo.rq` | QC5 — Licitante no processo `<X>` |
| `QC06_documento_formalizacao_demanda.rq` | QC6 — Utilidade do DFD |
| `QC07_estudo_tecnico_preliminar.rq` | QC7 — Elementos mínimos do ETP |
| `QC08_termo_de_referencia_objeto.rq` | QC8 — Definição do objeto no TR |
| `QC09_contratacoes_dependentes_correlatas_similares.rq` | QC9 — Contratações dependentes/correlatas/similares |
| `QC10_plano_contratacao_anual.rq` | QC10 — Parâmetros do PCA |
| `QC11_modalidades_licitacao.rq` | QC11 — Modalidades de licitação |
| `QC12_criterio_julgamento_tecnica_e_preco.rq` | QC12 — Critérios de julgamento (Técnica e Preço) |
| `QC13_fases_processo_licitatorio.rq` | QC13 — Fases do processo licitatório |
| `QC14_documentos_contratacao_direta.rq` | QC14 — Documentos da contratação direta |
| `QC15_motivos_inexigibilidade.rq` | QC15 — Motivos de inexigibilidade |
| `QC16_dispensa_de_licitacao.rq` | QC16 — Situações e limites da dispensa |
| `QC17_matriz_de_riscos.rq` | QC17 — Elementos da matriz de riscos |
| `QC18_probabilidade_gravidade_impacto.rq` | QC18 — Probabilidade e gravidade de impacto |
| `QC19_tipos_resposta_risco.rq` | QC19 — Tipos de resposta a risco |
| `QC20_objeto_em_risco_vs_habilitador_de_risco.rq` | QC20 — Objeto em risco vs. habilitador de risco |
