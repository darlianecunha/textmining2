# PDFTerms — Busca dirigida de termos para VOSviewer

**Ferramenta de busca dirigida por vocabulário controlado: você define os termos, o app conta as ocorrências e co-ocorrências nos PDFs e gera o arquivo JSON para o VOSviewer.**

Complementa o [PDFWords](../textminingprojeto1), que faz a extração aberta de todas as palavras. Aqui a lógica é invertida: o vocabulário é controlado por você, ideal para avaliar relatórios de sustentabilidade e revisões sistemáticas.

---

## Diferença para o PDFWords

| | PDFWords | PDFTerms |
|---|---|---|
| Abordagem | Aberta, orientada a dados | Dirigida, orientada a teoria |
| Quem escolhe os termos | O algoritmo | Você |
| Uso típico | Exploração inicial | Avaliação de relatórios, revisão sistemática |

---

## Funcionalidades

- Carregamento de múltiplos PDFs por drag & drop (extração 100% local)
- Você digita um termo por linha; o app expande os sinônimos automaticamente
- Biblioteca de termos de sustentabilidade portuária embutida (PT-BR + EN)
- Agrupamento manual de sinônimos com `=` (modo avançado, tem prioridade)
- Categorias temáticas com `[ ]` que viram clusters coloridos no VOSviewer
- Busca por termos compostos (ex.: `shore power`) e curinga (`emission*`)
- Correspondência sem distinção de maiúsculas e acentos
- Contagem binária por documento ou co-ocorrência por frase
- Diagnóstico de cobertura: lista os termos com zero ocorrências
- Exportações: JSON VOSviewer, matriz termo × documento (CSV), frequências (CSV)
- Salvar e carregar listas de termos (.txt)

---

## Biblioteca de termos

Curada a partir de fontes consagradas da área:

- **ESPO / EcoPorts** — Top-10 prioridades ambientais dos portos europeus (clima, qualidade do ar, eficiência energética, água, ruído, dragagem, resíduos, desenvolvimento portuário)
- **IMO / MARPOL** — sulphur cap, EEXI, CII, monitoramento de emissões
- **GRI / CSRD / ESG** — materialidade, partes interessadas, transparência, relatório de sustentabilidade
- **ODS / Agenda 2030**

A biblioteca é extensível: novos termos e sinônimos podem ser adicionados ao objeto `THESAURUS` no `index.html`.

---

## Como usar

1. Carregue um ou mais PDFs (relatórios de sustentabilidade dos portos)
2. Digite seus termos de busca, um por linha
3. Mantenha "Expandir sinônimos automaticamente" ligado para usar a biblioteca
4. Ajuste o escopo de co-ocorrência e os mínimos
5. Clique em **Contar termos e gerar rede**
6. Baixe o JSON e abra em [app.vosviewer.com](https://app.vosviewer.com) → Open → VOSviewer JSON file

> PDFs digitalizados (só imagem) precisam de OCR antes do processamento.

---

## Formato dos termos

```
CO2                              # expande pela biblioteca
água de lastro                   # termo composto, expande sozinho
[Energia] hidrogênio = H2; green hydrogen   # manual, com categoria
govern*                          # curinga
```

---

## Tecnologias

| Tecnologia | Uso |
|---|---|
| HTML / CSS / JavaScript | Interface e lógica |
| PDF.js (v3.11) | Extração de texto dos PDFs |
| VOSviewer | Visualização da rede |
| Vercel | Hospedagem |

---

## Privacidade

Todo o processamento ocorre no navegador. Nenhum arquivo é enviado a servidores.

---

## Autora

**Darliane Ribeiro Cunha, PhD**
Pesquisadora em governança de sustentabilidade, analytics ambiental e ODS
[ORCID: 0000-0003-2548-1237](https://orcid.org/0000-0003-2548-1237)
