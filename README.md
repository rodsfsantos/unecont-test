
# Teste Técnico – Product Owner

Este repositório contém a resolução completa do teste técnico para a posição de **Product Owner**, incluindo protótipo de tela, definição de User Stories, planejamento de sprint e resolução de desafios de produto.

O objetivo do material é demonstrar capacidade de **pensamento de produto**, **organização**, **clareza na escrita**, **visão técnica** e **abordagem estruturada para resolução de problemas**.

---

## Visão geral do conteúdo

- Protótipo de tela do sistema financeiro (HTML/CSS estático com dados mock)
- User Stories alinhadas ao comportamento do protótipo atual (front-end, sem backend)
- Planejamento de sprint
- Resolução do desafio de monetização do WhatsApp
- Resolução do desafio de cancelamento de corridas na Uber

---

## Protótipo – Sistema Financeiro

O protótipo representa a tela de controle financeiro utilizada para acompanhamento de notas fiscais emitidas no ano corrente.

🔗 **Acesso ao protótipo:**  
https://courageous-dieffenbachia-aa051d.netlify.app/

### Observações
- Protótipo desenvolvido em **HTML/CSS estático** com dados mock definidos em `window.mockData`
- Objetivo exclusivamente visual (layout e UX)
- Não há regras de negócio nem integração real com backend
- Campos de filtro existem em tela, mas não recalculam indicadores nem gráficos; as tabelas são filtradas apenas no front-end

---

## User Stories separadas por Front e Backend (API fake)

### US01-FE – Exibir indicadores no dashboard

**Como** analista financeiro  
**Quero** visualizar no dashboard os quatro indicadores principais  
**Para** acompanhar rapidamente a saúde financeira

**Critérios de Aceite (tela)**
- Renderizar quatro cards: Total Emitido, Inadimplência, A Vencer e Total Pago
- Exibir textos auxiliares conforme layout (ex.: “↑ 12% do mês anterior”, “⚠ Requer atenção”)
- Manter selects de Período e Mês visíveis e esteticamente funcionais; submissão deve disparar requisição para a API fake
- Usar os valores retornados da API fake; fallback local apenas se a API estiver indisponível

### US01-BE – API fake de indicadores do dashboard

**Como** desenvolvedor front-end  
**Quero** consumir uma API de resumo financeiro  
**Para** preencher os cards do dashboard

**Critérios de Aceite (API)**
- Disponibilizar endpoint GET `/api/dashboard/summary` que aceita `periodType` (month|quarter|year), `year` e `month` (quando aplicável)
- Retornar objeto com `totalIssued`, `totalOverdue`, `totalPending`, `totalPaid`
- Entregar payload coerente com o layout atual (ex.: valores de dez/2025), permitindo evoluir os dados depois
- Endpoint pode ser servido via mock (ex.: JSON estático/HTMX server-sent ou middleware); contrato deve permanecer estável

### US02-FE – Exibir gráficos de evolução

**Como** analista financeiro  
**Quero** ver os gráficos de inadimplência e receita no dashboard  
**Para** acompanhar a evolução recente

**Critérios de Aceite (tela)**
- Renderizar dois gráficos (linha/área para inadimplência, barras para receita) responsivos
- Consumir dados da API fake e popular labels e valores; manter aparência atual (Out, Nov, Dez) como default
- Filtros de período podem reconsultar a API; se não houver dados adicionais, exibir default sem erro

### US02-BE – API fake de evolução financeira

**Como** desenvolvedor front-end  
**Quero** uma API que devolva séries de receita e inadimplência  
**Para** alimentar os gráficos do dashboard

**Critérios de Aceite (API)**
- Endpoint GET `/api/dashboard/evolution` aceita `startDate`, `endDate` ou `periodType`
- Retorna duas séries: `revenue[]` e `overdue[]` com `month` (YYYY-MM) e `value`
- Valores default refletem o que está no protótipo (Out, Nov, Dez) para manter consistência visual
- API fake pode ser servida por arquivo JSON estático; contrato preparado para expansão de 12 meses

### US03-FE – Listar notas fiscais

**Como** analista financeiro  
**Quero** ver a lista de notas fiscais na tabela  
**Para** consultar rapidamente dados de cobrança

**Critérios de Aceite (tela)**
- Renderizar colunas: ID, Pagador, Data Emissão, Data Cobrança, Data Pagamento, Valor, Status, NF, Boleto
- Aplicar badges de status com cores diferentes; botões de NF/Boleto devem acionar download ou simulação
- Exibir contador de resultados e atualizar após filtros
- Consumir a API fake para carregar a tabela; se indisponível, usar mock local como contingência

### US03-BE – API fake de listagem de notas fiscais

**Como** desenvolvedor front-end  
**Quero** uma API de listagem de notas com filtros  
**Para** preencher a tabela de notas fiscais

**Critérios de Aceite (API)**
- Endpoint GET `/api/nf/list` com parâmetros: `page`, `limit`, `issueMonth`, `chargeMonth`, `paymentMonth`, `status` (array), `sortBy`, `sortOrder`
- Resposta contém `data[]` (id, client, value, issueDate, chargeDate, paymentDate, status, invoiceDoc, boletoDoc) e `pagination` (total, page, limit, totalPages)
- Garantir que o contrato cubra os campos exibidos na tabela atual
- API pode ser implementada como JSON estático ou service worker de mock, mantendo o contrato para futura troca por backend real

### US04-FE – Filtrar notas fiscais

**Como** analista financeiro  
**Quero** filtrar notas por mês e status  
**Para** encontrar rapidamente os registros relevantes

**Critérios de Aceite (tela)**
- Filtros disponíveis: mês de emissão, mês de cobrança, mês de pagamento e status
- Ao aplicar filtros, chamar a API fake com os parâmetros selecionados e re-renderizar a tabela
- Botão “Limpar Filtros” remove parâmetros e recarrega a lista completa

### US04-BE – API fake para filtros de notas

**Como** desenvolvedor front-end  
**Quero** que a API de notas aceite filtros  
**Para** devolver apenas os registros solicitados

**Critérios de Aceite (API)**
- Reutilizar o endpoint `/api/nf/list` para aplicar filtros recebidos
- Garantir que filtros não enviados não afetem o resultado
- Retornar contagem total coerente com os registros filtrados
- Manter consistência de status e datas com o que é exibido na tela

### Observações sobre as APIs fake
- Podem ser servidas via JSON local, middleware mock ou service worker; o importante é manter o contrato estável
- Dados iniciais devem refletir o que já aparece no protótipo, permitindo evolução incremental sem quebrar o front

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
