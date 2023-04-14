# Genômica Clínica

## Risco de Score Poligênico

O risco de score poligênico (PRS) é uma medida genética que avalia a predisposição de um indivíduo a desenvolver uma determinada condição ou doença com base em múltiplos fatores genéticos. Essa abordagem utiliza uma análise de polimorfismos de nucleotídeo único (SNPs) em diferentes regiões do genoma para calcular um escore que reflete o grau de suscetibilidade do indivíduo.

A transferência de um PRS de uma população para outra pode ser uma tarefa difícil devido às diferenças genéticas e ambientais entre essas populações. As variações genéticas entre populações podem resultar em diferentes frequências alélicas, diferentes tamanhos de efeito, diferentes variantes em desequilíbrio de ligação dos SNPs incluídos no PRS. Além disso, as diferenças ambientais podem influenciar a expressão de genes e interações gene-ambiente, o que pode levar a uma variação ainda maior nos efeitos genéticos. Portanto, é importante avaliar cuidadosamente a transferência de um PRS entre populações e considerar as limitações e incertezas envolvidas nesse processo.

REFERÊNCIAS:

- [Tutorial: a guide to performing polygenic risk score analyses](https://doi.org/10.1038/s41596-020-0353-1)

## PRS Hipertensão

O PRS tem sido utilizado para estudar a predisposição genética à hipertensão, uma das principais causas de morbidade e mortalidade no mundo. O PRS tem sido capaz de prever o risco de hipertensão em indivíduos e pode ser útil na prevenção e tratamento dessa doença. No entanto, é importante lembrar que o PRS é apenas uma ferramenta e deve ser interpretado juntamente com outros fatores de risco, como o histórico familiar e o estilo de vida, para uma avaliação mais completa do risco individual.

REFERÊNCIAS:

- [Dissecting the Polygenic Basis of Primary Hypertension: Identification of Key Pathway-Specific Components.](https://doi.org/10.3389/fcvm.2022.814502)

## Sugestão de Projetos

O objetivo final do projeto é aprimorar um classificador de indivíduos hipertensos e não hipertensos utilizando como componente genético o PRS.

Embora o objetivo final seja o aprimoramento do modelo, as etapas intermediárias também serão levadas em conta nos critérios de avaliacão.

## Datasets

Para o desenvolvimento deste datathon estão disponibilizados os seguintes conjuntos de dados:

### Genótipos da coorte alvo
Disponibilizados no arquivo target_cohort.vcf.gz (genoma de referência - hg38). Contém os seguintes campos:

| Variável         | Descrição | 
|--------------|:-----|
| CHROM |  O cromossomo no qual a variante está localizada.  |
| POS      |  Posição (baseada em 1) da variante na sequência especificada. |
| ID      |  O identificador da variação com base no rsID do dbSNP. |
| REF      |  A base encontrada no genoma de referência em determinada posição. |
| ALT      |  Alelos alternativos naquela posição. |
| QUAL      |  Escore de qualidade dos alelos |
| FILTER      |  Uma flag indicando "PASS" para variantes que passaram em filtros de qualidade ou indicando qual conjunto de filtros a variante falhou. |
| INFO      |  Uma lista de pares chave-valor (campos) descrevendo a variante. |
| SAMPLES      |  Genótipo das amostras. Há uma coluna para cada amostra |


### Variáveis Genéticas

- Arquivo tabular de pesos do modelo de PRS (PGS002296_hmPOS_GRCh38.tsv) com as seguintes colunas:

| Variável         | Tipo | Descrição |
|--------------|:-----:|:-----------|
| SNPID |  character |       Identificador único do SNP alvo (rsid com base no banco dbsnp) |
| CHROMOSOME      |  character |          Cromossomo no qual o SNP está localizado |
| POS      |  int |         Posição do SNP no cromossomo |
| EFFECT_ALLELE      |  character |          Alelo que possivelmente atribuí o risco, indicado pelo estudo de GWAS |
| NON_EFFECT_ALLELE      |  character |          Alelo que não foi associado ao risco |
| P-VALUE      |  float |          P-valor da associação entre o alelo efetor e o fenótipo |
| BETA      |  float |          Tamanho de efeito do SNP |


- Arquivo tabular com a anotação funcional dos SNPs (functional-snps.tsv)
- Arquivo tabular contendo SNPs em desequilíbrio de ligação com os SNPs contidos no arquivo de pesos do modelo (ld-snps.tsv) 

A descrição dos arquivos com a anotação funcional e os SNPs em LD estão no seguinte [dicionário de dados]()

### Variáveis Clínicas
Arquivo datathon-pheno.tsv

| Variável         | Tipo | Descrição |
|--------------|:-----:|:-----------|
| target_phenotype |  int |        1 para casos e 0 para controles |
| bmi      |  float |          IMC do indivíduo |
| age      |  int |          Idade do indivíduo |
| sex      |  character |          M para homens, F para mulheres |

