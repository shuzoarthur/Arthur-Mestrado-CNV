---

# Projeto de Mestrado: Detecção e Interpretação de CNVs em Dados de Exoma

Este repositório contém os arquivos, scripts e documentos relacionados ao projeto de mestrado

## Objetivo do Projeto

O objetivo principal é estabelecer um pipeline para detecção de Variações no Número de Cópias (CNVs) em dados de exoma, utilizando o GATK-gCNV, e interpretar as variantes identificadas com base em diretrizes padronizadas da ACMG/ClinGen.

---

## Estrutura do Repositório

A estrutura do repositório é organizada em diferentes diretórios para facilitar a navegação e reutilização dos arquivos:

```
.
├── data/
│   ├── raw/              # Dados brutos de entrada (BAMs, arquivos de intervalos, etc.)
│   ├── processed/        # Dados processados (arquivos intermediários e resultados finais)
│   └── metadata/         # Metadados das amostras
│
├── scripts/
│   ├── preprocessing/    # Scripts para pré-processamento (ex.: coleta de cobertura)
│   ├── gatk-gcnv/        # Scripts para execução do pipeline GATK-gCNV
│   ├── filtering/        # Scripts para aplicação de filtros de alta confiança
│   └── interpretation/   # Scripts para interpretação e classificação de CNVs
│
├── results/
│   ├── cnv_calls/        # Resultados das chamadas de variantes de CNV
│   └── interpretation/   # Relatórios de classificação e interpretação de CNVs
│
├── docs/
│   ├── methodology.md    # Descrição detalhada do pipeline e metodologia aplicada
│   ├── references.md     # Artigos e diretrizes utilizados no projeto
│   └── presentation/     # Arquivos para apresentações e relatórios
│
├── environment/          # Arquivos para configuração do ambiente (conda, requirements.txt, etc.)
└── README.md             # Este arquivo
```

---

## Configuração do Ambiente

1. Clone este repositório:
   ```bash
   git clone https://github.com/username/projeto-mestrado.git
   cd projeto-mestrado
   ```

2. Configure o ambiente:
   - Utilize o arquivo `environment/requirements.txt` para instalar as dependências do Python:
     ```bash
     pip install -r environment/requirements.txt
     ```
   - Instale o `BEDTools` (versão ≥ 2.27.1) e outros utilitários necessários.

3. Verifique a configuração dos bancos de dados usados pelo *ClassifyCNV*.

---

## Guia de Uso

### 1. Execução do Pipeline GATK-gCNV
Os scripts no diretório `scripts/gatk-gcnv` devem ser executados em ordem para realizar o processamento de cobertura, filtragem de intervalos e chamadas de CNVs.

```bash
bash scripts/gatk-gcnv/run_pipeline.sh
```

### 2. Filtragem de Variantes de Alta Confiança
Aplique os filtros definidos no projeto para gerar variantes de alta confiança:

```bash
python scripts/filtering/apply_filters.py --input results/cnv_calls/raw_calls.vcf
```

### 3. Interpretação e Classificação de CNVs
Use os scripts no diretório `scripts/interpretation/` para interpretar as CNVs identificadas:

```bash
python scripts/interpretation/classify_cnv.py --input results/cnv_calls/high_confidence.vcf
```

---

## Resultados Esperados

Os principais resultados do pipeline incluem:
- Arquivos VCF contendo as CNVs chamadas e filtradas.
- Relatórios de classificação das variantes (patogênicas, benignas, etc.).
- Listas de genes associados às CNVs identificadas.

---

## Referências

- [Diretrizes ACMG/ClinGen para Interpretação de CNVs](https://pubmed.ncbi.nlm.nih.gov/31045983/)
- [Documentação do GATK-gCNV](https://gatk.broadinstitute.org/)

---

## Contribuição

Contribuições são bem-vindas! Por favor, abra uma *issue* ou envie um *pull request* para sugestões ou melhorias.

---

Se precisar de personalizações, posso ajustar conforme sua necessidade! 😊
