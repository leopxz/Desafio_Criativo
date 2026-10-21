# Desafio Criativo: Planejando Automações com N8N Usando Apenas Bons Prompts

**Automação escolhida:** Monitor de incidentes críticos no ServiceNow com alerta automático para a equipe de suporte.

---

## 🧱 Passo 1: Definição da automação

```text
Quero criar uma automação no N8N para monitorar novos incidentes de prioridade alta abertos no ServiceNow e alertar automaticamente a equipe responsável.

Público ou responsável:
Equipe de suporte da central de atendimento interno e a supervisão do time.

Resultado esperado:
Sempre que surgir um incidente novo de prioridade 1 (Crítica) ou 2 (Alta), a equipe recebe uma notificação imediata no Microsoft Teams com os dados do chamado. Os incidentes críticos também geram um e-mail para a supervisão. Todo alerta enviado é registrado em uma planilha de histórico, sem notificações duplicadas.
```

---

## 🧩 Passo 2: Contexto e regras

```text
Ferramentas envolvidas:
- ServiceNow (Table API REST, tabela "incident")
- N8N (orquestração do fluxo)
- Microsoft Teams (canal da equipe de suporte)
- Outlook / SMTP (e-mail para a supervisão)
- Google Sheets (planilha de controle e histórico de alertas)

Fluxo desejado:
1. Disparar o workflow a cada 10 minutos.
2. Consultar a API do ServiceNow buscando incidentes com prioridade 1 ou 2, em estado "Novo" ou "Em andamento", abertos nos últimos 15 minutos.
3. Comparar os números dos incidentes retornados com a planilha de controle, mantendo apenas os que ainda não foram notificados.
4. Para cada incidente novo, montar a mensagem com: número, descrição curta, prioridade, grupo de atendimento, data de abertura e link direto para o chamado.
5. Enviar a mensagem no canal do Microsoft Teams.
6. Se a prioridade for 1 (Crítica), enviar também um e-mail para a supervisão.
7. Registrar na planilha o número do incidente, a prioridade e a data/hora do alerta.

Regras importantes:
- Nunca notificar o mesmo incidente mais de uma vez.
- Se a consulta não retornar incidentes novos, encerrar o fluxo sem enviar nada.
- Fora do horário comercial (segunda a sexta, 7h às 19h), notificar apenas incidentes de prioridade 1.
- Se a API do ServiceNow falhar (timeout ou erro de autenticação), tentar novamente até 3 vezes e, persistindo o erro, enviar um alerta de falha ao responsável técnico pela automação.
- Credenciais devem ficar armazenadas no gerenciador de Credentials do N8N, nunca escritas diretamente nos nós.
- Datas no fuso America/Sao_Paulo, no formato dd/MM/yyyy HH:mm.
```

---

## 🚀 Passo 3: Prompt final

```text
Atue como um especialista em N8N e em integrações com a API REST do ServiceNow.

Crie uma automação para monitorar novos incidentes de prioridade alta abertos no ServiceNow e alertar automaticamente a equipe responsável.

Público:
Equipe de suporte da central de atendimento interno e a supervisão do time.

Ferramentas envolvidas:
ServiceNow (Table API REST, tabela "incident"), Microsoft Teams, Outlook/SMTP e Google Sheets.

Fluxo:
1. Disparar o workflow a cada 10 minutos.
2. Consultar a API do ServiceNow buscando incidentes com prioridade 1 ou 2, em estado "Novo" ou "Em andamento", abertos nos últimos 15 minutos.
3. Comparar os números retornados com a planilha de controle no Google Sheets e manter apenas os incidentes ainda não notificados.
4. Para cada incidente novo, montar uma mensagem com número, descrição curta, prioridade, grupo de atendimento, data de abertura e link direto para o chamado.
5. Enviar a mensagem no canal da equipe no Microsoft Teams.
6. Se a prioridade for 1 (Crítica), enviar também um e-mail para a supervisão.
7. Registrar na planilha o número do incidente, a prioridade e a data/hora do alerta.

Regras:
- Nunca notificar o mesmo incidente mais de uma vez.
- Se não houver incidentes novos, encerrar o fluxo sem enviar nada.
- Fora do horário comercial (segunda a sexta, 7h às 19h), notificar apenas incidentes de prioridade 1.
- Em caso de falha na API do ServiceNow, tentar novamente até 3 vezes e, persistindo o erro, alertar o responsável técnico.
- Credenciais armazenadas no gerenciador de Credentials do N8N, nunca diretamente nos nós.
- Datas no fuso America/Sao_Paulo, no formato dd/MM/yyyy HH:mm.

Explique quais nós do N8N devem ser utilizados e a lógica de funcionamento do workflow. Para cada nó, informe:
- a finalidade dele no fluxo;
- as principais configurações (incluindo a query sysparm_query usada na chamada à API);
- as expressões necessárias (filtros, comparação com a planilha, formatação de datas com Luxon e verificação de horário comercial).

Ao final, descreva como tratar os erros (Retry On Fail e Error Workflow) e sugira como testar o workflow antes de ativá-lo em produção.
```
