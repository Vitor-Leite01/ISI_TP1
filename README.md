# 🏎️ ETL Formula 1 (2016–2024)

Projeto desenvolvido no âmbito da unidade curricular **Integração de Sistemas de Informação (ISI)** — ano letivo **2025/2026**.  
O objetivo é construir um processo **ETL (Extract, Transform, Load)** em **Pentaho Data Integration (PDI / Spoon)** para transformar e analisar dados da Fórmula 1 entre os anos **2016 e 2024**.

---

## 📊 Objetivo do Projeto

Extrair dados de várias fontes CSV (Drivers, Constructors, Races e Results),  
realizar junções e transformações no Pentaho e gerar estatísticas consolidadas dos pilotos no período de 2016–2024.  
Os resultados são exportados automaticamente em **Excel**, **TXT** e **JSON**, podendo ainda ser enviados por e-mail.

---

## 🧱 Estrutura do Projeto

```
F1_ETL/
│
├── data/                  # Ficheiros de entrada (datasets originais)
│   ├── drivers.csv
│   ├── constructors.csv
│   ├── races.csv
│   └── results.csv
│
├── transformations/       # Ficheiros do Pentaho (.ktr)
│   └── F1_ETL_Main.ktr
│
├── output/                # Ficheiros gerados automaticamente
│   ├── Estatisticas_F1_2016_2024.xlsx
│   ├── Estatisticas_F1_2016_2024.txt
│   └── Estatisticas_F1_2016_2024.json
│
└── README.md
```

---

## ⚙️ Processo ETL no Pentaho

O fluxo criado no Pentaho realiza as seguintes etapas:

1. **Extração**
   - Importação dos ficheiros `drivers.csv`, `constructors.csv`, `races.csv`, `results.csv`.
   - Cada dataset é carregado através de um passo “CSV Input”.

2. **Transformação**
   - Junções entre datasets através de *Merge Join* (por `driverId`, `constructorId`, `raceId`).
   - Filtragem dos anos entre **2016 e 2024**.
   - Limpeza de campos e criação de um campo `Clean_FullName` (nome completo do piloto).
   - Agregação dos dados:
     - Total de corridas (`Number of Values`)
     - Total de pontos (`Sum`)
     - Média da posição final (`Average (Mean)`)
     - Média da posição de arranque (`Average (Mean)`)

3. **Ordenação**
   - Ordenação final dos pilotos por **Total Points** (descendente).

4. **Carregamento (Load)**
   - Exportação dos resultados:
     - `Estatisticas_F1_2016_2024.xlsx`
     - `Estatisticas_F1_2016_2024.txt`
     - `Estatisticas_F1_2016_2024.json`
   - (Opcional) Envio por **e-mail automático** através do passo “Mail”.

---

## 📬 Envio por E-mail (Opcional)

O fluxo inclui um passo final “Mail” que envia o ficheiro Excel para um destinatário configurado.  
Basta preencher no Pentaho:
- **Destination address:** endereço do destinatário  
- **Sender address:** e-mail de envio  
- **SMTP server:** servidor de envio (ex: `smtp.gmail.com`)  
- **Attached Files:** caminho para `C:\F1_ETL\output\Estatisticas_F1_2016_2024.xlsx`

---

## 🧠 Tecnologias Utilizadas

| Tecnologia | Finalidade |
|-------------|-------------|
| **Pentaho Data Integration (Spoon)** | Criação e execução do fluxo ETL |
| **Microsoft Excel** | Geração do ficheiro .xlsx final |
| **JSON / TXT** | Exportação de resultados em formatos alternativos |
| **Git & GitHub** | Controlo de versões e partilha do projeto |

---

## 📈 Resultados Esperados

O processo produz estatísticas por piloto, incluindo:

| Piloto | Nacionalidade | Total Corridas | Total Pontos | Média Posição Final | Média Posição de Partida |
|--------|----------------|----------------|---------------|----------------------|---------------------------|
| Max Verstappen | Dutch | 140 | 2580 | 2.3 | 2.1 |
| Lewis Hamilton | British | 138 | 2420 | 3.1 | 2.8 |
| Charles Leclerc | Monegasque | 96 | 1002 | 4.5 | 3.8 |

*(Valores exemplificativos)*

---

## 🚀 Execução

1. Abrir o ficheiro `F1_ETL_Main.ktr` no Pentaho Spoon.  
2. Confirmar os caminhos das pastas `data/` e `output/`.  
3. Executar a transformação (`Run` ou F9).  
4. Verificar os ficheiros gerados em `C:\F1_ETL\output`.

---

## 👨‍💻 Autor

**Vítor Leite**  
💼 Instituto Superior de Engenharia  
📅 Ano letivo 2025/2026  
📧 (coloca aqui o teu e-mail académico, se quiseres)

---

## 🧾 Licença

Projeto académico. Uso livre para fins educacionais.
