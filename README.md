# Tarefa 18 – Teste de Performance com JMeter (YouTube)

Este repositório contém um script de teste de performance com **Apache JMeter** que realiza buscas no YouTube usando massa de dados externa (CSV), conforme a especificação do exercício.

## ✅ Especificação do exercício
- **Endpoint:** `https://www.youtube.com`
- **Recurso testado:** `/results?search_query=${palavra}`
- **Massa de dados:** `dados.csv` com **10 palavras** (uma por linha)
- **Usuários (threads):** 20
- **Ramp‑up:** 60 segundos
- **Duração:** 3 minutos (180s)

## 🗂 Arquivos do repositório
- `teste_youtube.jmx` — Plano de teste do JMeter.
- `dados.csv` — Massa de dados usada no parâmetro `search_query`.
- (Opcional) `README.md` — Este arquivo com instruções de uso.

> **Importante:** mantenha `teste_youtube.jmx` e `dados.csv` na **mesma pasta** ao executar o teste, pois o plano referencia o CSV por nome relativo.

## 🧰 Pré‑requisitos
- **Java** instalado e no PATH (verifique com `java -version`).
- **Apache JMeter** 5.x (verifique com `jmeter -v` ou abra via GUI).

## ▶️ Como executar (GUI)
1. Abra o JMeter e carregue `teste_youtube.jmx` (**File → Open**).
2. Garanta que o elemento **CSV Data Set Config** aponte para `dados.csv`.
3. Execute o teste (**Run → Start**).  
   - Inclui listeners como **Summary Report**, **View Results in Table** e **Graph Results** para acompanhar as métricas.

## 🖥️ Como executar (CLI – opcional)
Para execução sem interface gráfica e salvando resultados em `results.jtl`:
```bash
jmeter -n -t teste_youtube.jmx -l results.jtl
```
> No Windows, se o comando `jmeter` não existir no PATH, execute `bin\jmeter.bat` a partir da pasta de instalação do JMeter.

## 🧪 O que o teste faz
- Envia requisições **GET** para `https://www.youtube.com/results` com o parâmetro `search_query`.
- A cada execução, a variável `${palavra}` é lida do `dados.csv`, simulando diferentes buscas.
- Executa com **20 usuários**, subindo em **60s**, durante **3 minutos**.

## 📁 Estrutura sugerida
```
.
├── dados.csv
├── teste_youtube.jmx
└── README.md
```

## ✅ Validação rápida
- **Threads / Ramp-up / Duração** conforme especificado.
- **HTTP Request Defaults** com `Protocol=https` e `Server Name=www.youtube.com`.
- **CSV Data Set Config** com `filename=dados.csv` e `variableNames=palavra`.

---

Feito com ♥ para a Tarefa 18.
