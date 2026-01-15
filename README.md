
# Teste Técnico – Product Owner

Este repositório contém a resolução completa do teste técnico para a posição de **Product Owner**, incluindo protótipo de tela, definição de User Stories, planejamento de sprint e resolução de desafios de produto.

O objetivo do material é demonstrar capacidade de **pensamento de produto**, **organização**, **clareza na escrita**, **visão técnica** e **abordagem estruturada para resolução de problemas**.

---

## Visão geral do conteúdo

- Protótipo de tela do sistema financeiro (HTML/CSS)
- User Stories com critérios de aceite e endpoints fake
- Planejamento de sprint
- Resolução do desafio de monetização do WhatsApp
- Resolução do desafio de cancelamento de corridas na Uber

---

## Protótipo – Sistema Financeiro

O protótipo representa a tela de controle financeiro utilizada para acompanhamento de notas fiscais emitidas no ano corrente.

🔗 **Acesso ao protótipo:**  
https://courageous-dieffenbachia-aa051d.netlify.app/

### Observações
- Protótipo desenvolvido em **HTML/CSS estático**
- Objetivo exclusivamente visual (layout e UX)
- Não há regras de negócio nem integração real com backend

---

## User Stories

### US01 – Visualizar indicadores financeiros no dashboard

**Como** analista financeiro  
**Quero** visualizar indicadores consolidados das notas fiscais  
**Para** acompanhar a saúde financeira da empresa

**Critérios de Aceite**
- Exibir valor total das notas emitidas
- Exibir valor total das notas pagas
- Exibir valor total das notas vencidas
- Exibir valor total das notas a vencer
- Permitir filtro por mês, trimestre e ano

**Endpoint**
```
GET /finance/dashboard/summary
```

**Request**
```json
{
  "periodType": "month",
  "year": 2023,
  "month": 8
}
```

**Response**
```json
{
  "totalIssued": 350000,
  "totalPaid": 220000,
  "totalOverdue": 80000,
  "totalToExpire": 50000
}
```

---

### US02 – Visualizar gráficos de evolução financeira

**Como** analista financeiro  
**Quero** visualizar a evolução mensal da inadimplência e da receita  
**Para** identificar tendências financeiras

**Endpoint**
```
GET /finance/dashboard/evolution
```

---

### US03 – Visualizar lista de notas fiscais

**Como** analista financeiro  
**Quero** visualizar a lista de notas fiscais  
**Para** acompanhar cobranças e pagamentos

**Endpoint**
```
GET /nf/list
```

---

### US04 – Filtrar notas fiscais

**Como** analista financeiro  
**Quero** filtrar notas fiscais por período e status  
**Para** localizar informações específicas com agilidade

**Endpoint**
```
GET /nf/list
```

---

## Planejamento da Sprint

### Objetivo da Sprint
Entregar a primeira versão da tela de controle financeiro, com dashboard e listagem de notas fiscais.

### Etapas
1. Refinamento das histórias com o time
2. Alinhamento de regras de negócio
3. Quebra das histórias em tarefas técnicas
4. Estimativa de esforço
5. Execução e acompanhamento diário
6. Sprint Review
7. Retrospectiva

---

## Desafio de Produto – Monetização do WhatsApp

### Problema
O WhatsApp possui uma base massiva de usuários gratuitos. O desafio é definir se e como monetizar sem comprometer a experiência.

### Abordagem
- Análise de dados de uso e segmentação
- Avaliação de impacto em churn e retenção
- Identificação de usuários com maior valor percebido

### Solução proposta
- Manter uso básico gratuito
- Introduzir modelo freemium para usuários profissionais
- Funcionalidades avançadas como diferencial pago

📄 Detalhamento completo disponível em:  
[whatsapp_monetization_case.md](./whatsapp_monetization_case.md)

---

## Desafio de Produto – Cancelamento de corridas na Uber

### Problema
Motoristas cancelam corridas após aceitá-las, impactando a experiência do passageiro.

### Abordagem
1. Análise de dados de cancelamento
2. Identificação de padrões (valor, distância, região)
3. Validação de hipóteses
4. Proposição de soluções

### Possíveis soluções
- Mais transparência antes do aceite
- Incentivos para corridas críticas
- Penalidades progressivas
- Testes A/B para validação

### Métricas de sucesso
- Redução da taxa de cancelamento
- Melhoria no tempo de espera
- Aumento do NPS

---

## Considerações finais

Este repositório apresenta uma solução conceitual, focada em clareza de produto, visão estratégica e organização técnica, sem implementação real de backend ou regras complexas.

---

## Autor

Rodrigo Santos  
Product Owner
