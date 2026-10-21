# 🤖 Desafio Criativo: Planejando Automações com N8N Usando Apenas Bons Prompts

![N8N](https://img.shields.io/badge/n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)
![ServiceNow](https://img.shields.io/badge/ServiceNow-62D84E?style=for-the-badge&logo=servicenow&logoColor=white)
![Prompt Engineering](https://img.shields.io/badge/Prompt_Engineering-412991?style=for-the-badge&logo=openai&logoColor=white)
![DIO](https://img.shields.io/badge/DIO-Desafio_de_Projeto-E4105D?style=for-the-badge)

Projeto desenvolvido como entrega do **Desafio Criativo** da [DIO](https://www.dio.me/). O objetivo é planejar uma automação no N8N **sem escrever nenhum nó**, usando apenas um prompt bem estruturado. O prompt deve ser claro o bastante para que uma IA consiga explicar como montar o workflow completo.

---

## 🎯 A automação planejada

**Monitor de incidentes críticos no ServiceNow**

Na central de atendimento interno, incidentes de prioridade alta precisam ser percebidos rápido. Acompanhar a fila manualmente é repetitivo e sujeito a atraso.

Para resolver isso, foi planejado um workflow no N8N que funciona assim:

- a cada 10 minutos, consulta a API do ServiceNow em busca de incidentes novos de prioridade 1 ou 2;
- alerta a equipe no **Microsoft Teams** com os dados e o link do chamado;
- envia também um **e-mail para a supervisão** quando o incidente é crítico;
- registra cada alerta em uma **planilha de histórico**, sem notificações duplicadas;
- trata falhas da API com novas tentativas e um alerta para o responsável técnico.

---

## 🧩 Como o prompt foi construído

O desafio propõe montar o prompt em três etapas:

| Etapa | Pergunta-chave | O que define |
|---|---|---|
| **1. Definir a automação** | O que, para quem e com qual resultado? | A intenção |
| **2. Contexto e regras** | Quais ferramentas, em que ordem e com quais exceções? | O contexto |
| **3. Prompt final** | Como unir tudo em um comando claro para a IA? | As instruções |

No prompt final foram incluídas exigências que a IA deve cumprir na resposta, para que ela seja útil na prática:

- definição de papel ("Atue como especialista em N8N e na API REST do ServiceNow");
- fluxo numerado, etapa por etapa;
- regras explícitas: deduplicação, horário comercial, tratamento de erros e segurança de credenciais;
- pedido de detalhamento por nó: finalidade, configurações e expressões;
- pedido de estratégia de testes antes de ativar em produção.

---

## 📂 Estrutura do repositório

```
Desafio_Criativo/
├── README.md                 # Este arquivo
└── desafio-n8n-prompt.md     # Os 3 passos preenchidos + prompt final
```

👉 **[Acesse o prompt completo aqui](./desafio-n8n-prompt.md)**

---

## 💡 Aprendizados

- **Prompt bom é especificação.** Quanto mais claro o objetivo, a ordem das etapas e as exceções, menos a IA precisa "adivinhar".
- **As regras de negócio fazem a diferença.** Deduplicação, horário comercial e tratamento de erros transformam um fluxo de demonstração em algo pronto para produção.
- **Planejar antes de construir economiza tempo.** Com o prompt pronto, o workflow no N8N passa a ser só execução.

---

## 👤 Autor

**Leonardo Paixão**
Especialista em Suporte a Automação · Python, N8N e automação de processos com IA

[![GitHub](https://img.shields.io/badge/GitHub-leopxz-181717?style=flat&logo=github)](https://github.com/leopxz)
