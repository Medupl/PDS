# PDS — Processamento Digital de Sinais

Material da disciplina de Processamento Digital de Sinais: notebooks de laboratório, slides das aulas e os projetos da disciplina.

**Autor:** Marcos Eduardo Araújo (Mat.: 121210541)
**UFCG — Campina Grande, Paraíba** · 2026

---

## Estrutura

```
.
├── Aulas_Slides/              # Slides das aulas (PDF)
├── laboratorios/              # Notebooks dos laboratórios
├── Projeto - DFT_FFT/         # Projeto 1: implementação e benchmark de DFT/FFT
└── Projeto - Filtros Digitais/# Projeto 2: seleção de canal em SDR
```

### `laboratorios/`

Notebooks das práticas da disciplina — amostragem, quantização PCM, alteração de
taxa, introdução à DFT e análise espectral.

### `Projeto - DFT_FFT/`

Implementações da Transformada Discreta de Fourier e comparação de desempenho
entre elas:

| Notebook | Conteúdo |
|---|---|
| `DFT_Basica.ipynb` | DFT direta, por somatório |
| `DFT_Matricial.ipynb` | DFT via multiplicação matricial |
| `FFT_geral.ipynb` | FFT para caso geral |
| `FFT_polinomio_2.ipynb` | FFT para tamanhos potência de 2 (radix-2) |
| `Benchmark.ipynb` | Comparação de tempo entre as implementações e o `numpy.fft` |

Os arquivos `*_metrics.json` guardam os tempos medidos por cada implementação e
são consumidos pelo `Benchmark.ipynb`.

### `Projeto - Filtros Digitais/`

Projeto de um filtro FIR passa-baixas para **seleção de canal em um receptor SDR**
(*Software-Defined Radio*).

O receptor digitaliza uma banda de 1,92 MHz com vários canais lado a lado. Após o
DDC, o canal de interesse fica em banda base ocupando ±100 kHz, mas os vizinhos
continuam presentes — um canal adjacente em 200 kHz e um interferente forte em
450 kHz. Um único filtro precisa então fazer duas coisas ao mesmo tempo: **selecionar
o canal** e servir de **anti-aliasing** para uma decimação de fator M = 4.

O filtro foi projetado por janelamento de Kaiser, resultando em 93 coeficientes.

| Arquivo | Conteúdo |
|---|---|
| `projeto.ipynb` | Desenvolvimento completo: projeto, filtragem, decimação e validação |
| `PJ_9_selecao_canal_sdr.pdf` | Enunciado do projeto |
| `Overleaf_Latex/` | Fonte LaTeX do relatório |

O relatório em `Overleaf_Latex/` é compilado a partir de `main.tex`, que inclui os
capítulos de `textos/` e as figuras de `Imagens/` (geradas pelo notebook).

---

## Requisitos

Os notebooks usam Python 3 com:

```
numpy  scipy  matplotlib  jupyter
```

O ambiente virtual (`venv/`) não faz parte do repositório. Para recriá-lo:

```bash
python3 -m venv venv
source venv/bin/activate
pip install numpy scipy matplotlib jupyter
```
