
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

## User Stories (alinhadas ao protótipo atual)

### US01 – Visualizar indicadores no dashboard (mock)

**Como** analista financeiro  
**Quero** visualizar os indicadores consolidados mostrados no dashboard  
**Para** acompanhar a saúde financeira com os dados mock disponíveis

**Critérios de Aceite (conforme protótipo)**
- Exibir quatro cards com valores fixos: Total Emitido, Inadimplência, A Vencer e Total Pago (dados mock de dezembro/2025)
- Mostrar textos auxiliares (“↑ 12% do mês anterior”, “⚠ Requer atenção”, etc.) conforme layout estático
- Campos de filtro “Período” e “Mês” estão presentes, mas a ação de aplicar não recalcula os indicadores (dados permanecem fixos)
- Dados carregados localmente de `window.mockData.indicators`; não há integração com API ou backend

### US02 – Visualizar gráficos de evolução (mock)

**Como** analista financeiro  
**Quero** ver os gráficos de inadimplência e receita apresentados no dashboard  
**Para** ter uma visão visual dos valores mock disponíveis

**Critérios de Aceite (conforme protótipo)**
- Exibir dois gráficos estáticos em SVG: linha/área para Inadimplência e barras para Receita
- Período fixo de três meses (Out, Nov, Dez) com valores estáticos (R$ 15.200, R$ 22.500, R$ 35.800 na inadimplência; R$ 42.000, R$ 51.500, R$ 60.800 na receita)
- Sem interação, comparação com ano anterior ou filtros funcionais; os dados são fixos no markup
- Responsividade limitada à natureza do SVG/Tailwind; não há carregamento dinâmico de dados

### US03 – Visualizar lista de notas fiscais (mock)

**Como** analista financeiro  
**Quero** visualizar a lista de notas fiscais exibida na tabela  
**Para** consultar rapidamente os dados mock disponíveis

**Critérios de Aceite (conforme protótipo)**
- Tabela exibe as colunas ID, Pagador, Datas (emissão, cobrança, pagamento), Valor, Status, NF e Boleto
- Dados provenientes de `window.mockData.invoices` (6 registros mock renderizados no front-end)
- Badge de status com cores diferentes por status; botões de NF/Boleto disparam apenas um alerta de simulação de download
- Sem paginação ou ordenação; o contador de notas mostra apenas a quantidade renderizada na tabela

### US04 – Filtrar notas fiscais (mock)

**Como** analista financeiro  
**Quero** filtrar as notas fiscais na tabela  
**Para** encontrar rapidamente registros mock por mês e status

**Critérios de Aceite (conforme protótipo)**
- Filtros disponíveis: mês de emissão, mês de cobrança, mês de pagamento e status (selects); botão “Limpar Filtros” restaura a lista original
- Filtragem ocorre apenas no front-end sobre os 6 registros mock; o contador de notas é atualizado conforme o resultado
- Não há filtros por cliente, faixa de valor ou datas livres; não há paginação combinada com filtros
- Nenhum endpoint é chamado; toda lógica ocorre no navegador com dados fixos

### Limitações conhecidas em relação à versão desejada
- Indicadores e gráficos não são recalculados pelos filtros e não consultam backend
- Lista de notas não possui paginação, ordenação, busca por cliente ou faixa de valor
- Botões de download de NF/Boleto são apenas demonstrações (alerta)
- Não há endpoints reais; o protótipo é 100% estático

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
