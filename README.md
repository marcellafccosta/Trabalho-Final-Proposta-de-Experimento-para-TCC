# Plano de Experimento – Scoping e Planejamento

## 1. Identificação básica

### 1.1 Título do experimento
Impacto de Code Review obrigatório na qualidade de PRs em projetos acadêmicos

### 1.2 ID / código
EXP-ACAD-2025

### 1.3 Versão do documento e histórico de revisão

| Versão | Data       | Alterações                                                  | Autor          |
|--------|------------|-------------------------------------------------------------|----------------|
| v1.0   | 21/11/2025 | Criação Inicial: Identificação Básica (Seções 1-2), Contexto e Problema | Marcella Costa |
| v1.1   | 25/11/2025 | Escopo e Contexto (Seção 4), Objetivos e Questões GQM (Seção 3), Stakeholders e Impacto (Seção 5), Riscos e Critérios de Sucesso (Seção 6) | Marcella Costa |
| v1.2   | 28/11/2025 |  Modelo Conceitual e Hipóteses (Seção 7), Variáveis e Tratamentos (Seção 8), Desenho Experimental (Seção 9) | Marcella Costa |
| v1.3   | 02/12/2025 | População e Amostragem (Seção 10), Instrumentação (Seção 11), Plano de Análise (Seção 12), Avaliação de Validade (Seção 13) Detalhamento de variáveis de confusão (Seção 8.7) | Marcella Costa |
### 1.4 Datas (criação, última atualização)
- **Criação:** 21/11/2025  
- **Última atualização:** 02/12/2025

### 1.5 Autores (nome, área, contato)
- **Marcella Ferreira Chaves Costa** – Engenharia de Software, PUC Minas  
  E-mail: marcellafccosta@gmail.com

### 1.6 Responsável principal (PI / dono do experimento)
Marcella Ferreira Chaves Costa  
Estudante de Engenharia de Software – TCC  
Responsável por todas as decisões metodológicas, coleta de dados, análise e publicação dos resultados.

### 1.7 Projeto / produto / iniciativa relacionada
Este experimento está conectado a projetos acadêmicos desenvolvidos ao longo do semestre em equipes de estudantes, utilizando versionamento no GitHub e envolvendo a implementação de funcionalidades por meio de Pull Requests. O contexto abrange trabalhos práticos de disciplinas do curso de Engenharia de Software, projetos integradores ou módulos específicos desenvolvidos em repositórios institucionais, onde equipes colaborativas trabalham em ciclos de desenvolvimento incremental com entregas periódicas.

---

## 2. Contexto e problema

### 2.1 Descrição do problema / oportunidade
Em projetos acadêmicos, é comum que Pull Requests sejam integrados rapidamente sem revisão formal, especialmente por pressão de prazos e falta de maturidade no processo. Isso pode resultar na inclusão de **defeitos**, inconsistências de padrão, decisões arquiteturais inadequadas e maior retrabalho após o merge. Ao mesmo tempo, exigir Code Review obrigatório pode **aumentar o tempo de integração** e gerar custo adicional de organização.

**Oportunidade:** avaliar empiricamente se a obrigatoriedade de Code Review **melhora a qualidade dos PRs em projetos acadêmicos** e se o benefício supera o custo em tempo e esforço. A hipótese é que a obrigatoriedade eleva a Qualidade do Código (menos defeitos e maior adesão a padrões) e, potencialmente, a Eficiência do Processo (melhor comunicação e aprendizado). Em outras palavras, o problema central que o experimento tenta responder é: **“vale a pena mesmo obrigar Code Review em contexto acadêmico, ou isso vira só burocracia?”**.

### 2.2 Contexto organizacional e técnico
O experimento será conduzido em ambiente acadêmico universitário, especificamente com equipes compostas por estudantes de Engenharia de Software que trabalham colaborativamente em repositórios hospedados na plataforma GitHub. 

- **Equipe:** grupos de 3–6 alunos desenvolvendo software em ciclos semanais/sprints.  
- **Domínio:** projetos acadêmicos de desenvolvimento de software em linguagem comum (por exemplo, Python, Java, JavaScript).  

**Tecnologias e Ferramentas:**
- Controle de Versão: Git (padrão).  
- Plataforma de Colaboração: GitHub (essencial para configurar a regra de Code Review obrigatório via *branch protection rules* e para extrair métricas de PRs, como comentários e tempo de merge).  
- Processo de desenvolvimento: integração via PRs, com divisão de tarefas, commits frequentes e entregas incrementais.  
- Ferramentas relevantes: Pull Requests, Reviews, Branch Protection Rules, Issues e Actions do GitHub.

### 2.3 Trabalhos e evidências prévias
Evidências internas coletadas através de observação sistemática no curso de Engenharia de Software revelam que, em várias disciplinas e projetos desenvolvidos, os Pull Requests são frequentemente aceitos e integrados **sem passar por um processo sistemático de revisão**. Como resultado desta prática, **bugs e defeitos são detectados apenas nas fases finais** de testes ou mesmo após a entrega do projeto, gerando **retrabalho significativo** e comprometendo a qualidade final do software produzido.

No âmbito externo, tanto a literatura científica quanto a prática na indústria de software estabelecem o Code Review como uma prática consolidada na engenharia de software moderna. Esta prática tem demonstrado efetividade na redução de defeitos, padronização de código, compartilhamento de conhecimento entre membros da equipe e prevenção de regressões no sistema. Resultados empíricos de diversos estudos apontam para um impacto positivo significativo na qualidade do software, embora estes benefícios sejam dependentes de fatores contextuais, como a experiência do time, o volume de mudanças em cada revisão e a cultura organizacional estabelecida.

Entre os trabalhos científicos relevantes, destaca-se o estudo de McIntosh et al. de 2016, intitulado "The impact of code review coverage and code review participation on software quality", que analisou projetos de código aberto, demonstrando correlação entre **Code Review e redução de 14% a 28% nos bugs pós-release**. Bacchelli e Bird, em 2013, publicaram "Expectations, outcomes, and challenges of modern code review", identificando que os principais benefícios reportados são encontrar defeitos, representando 14% dos casos, e transferência de conhecimento, correspondendo a 41% dos benefícios percebidos. No contexto pedagógico específico, Hundhausen et al., em 2013, através do trabalho "Talking about code: Integrating pedagogical code reviews into early computing courses", demonstraram que **Code Review pedagógico melhora significativamente a compreensão de código por parte dos estudantes em cursos iniciais de computação**.

### 2.4 Referencial teórico e empírico essencial
O referencial teórico que fundamenta este experimento baseia-se em três conceitos centrais da Engenharia de Software moderna:

1. **Code Review (Revisão de Código):** processo de inspeção colaborativa do código-fonte realizado por membros da equipe antes que as mudanças sejam integradas ao branch principal do repositório. Este processo visa identificar defeitos, garantir aderência a padrões estabelecidos, promover compartilhamento de conhecimento e melhorar aspectos de design e arquitetura do software.

2. **Pull Request (PR):** proposta formal de mudança em repositórios Git, seguindo o fluxo de criação de um branch com as alterações desejadas, submissão para revisão por outros membros da equipe, processo de aprovação baseado em critérios estabelecidos e, finalmente, integração ao branch principal através do merge. Os Pull Requests facilitam a discussão assíncrona sobre as mudanças propostas, permitem revisão sistemática do código e são centrais no workflow de equipes de desenvolvimento modernas.

3. **Qualidade de Software:** neste estudo é fundamentado no modelo internacional ISO/IEC 25010. Este modelo estabelece dimensões de qualidade que incluem funcionalidade, abrangendo corretude e completude das funcionalidades implementadas; confiabilidade, relacionada à maturidade do sistema, disponibilidade e tolerância a falhas; segurança, contemplando confidencialidade e integridade dos dados; manutenibilidade, que engloba modularidade, reusabilidade e analisabilidade do código; e eficiência de desempenho do sistema. Para os propósitos deste experimento específico, o foco concentra-se em três dimensões principais: **manutenibilidade**, avaliada através de métricas de complexidade e duplicação de código; **confiabilidade**, medida através da quantidade de bugs detectados; e **segurança**, analisada através da identificação de vulnerabilidades no código produzido.

Na prática, o experimento está sempre cruzando essas três ideias: como o PR é usado, que tipo de Code Review é feito e como isso reflete em indicadores concretos de qualidade.

---

## 3. Objetivos e questões (Goal / Question / Metric)

### 3.1 Objetivo geral (Goal template)
Analisar Pull Requests (PRs) de projetos acadêmicos de Engenharia de Software com o propósito de **comparar a qualidade e o custo de integração do ponto de vista de desenvolvedores e revisores** (alunos) no contexto de equipes acadêmicas que utilizam GitHub para desenvolvimento colaborativo, contrastando PRs com Code Review obrigatórios vs. PRs sem obrigatoriedade de review. Ou seja, o foco é entender o trade-off entre “melhor qualidade” e “mais custo/atraso” quando se torna a revisão uma exigência formal.

### 3.2 Objetivos específicos
- **O1:** Quantificar a diferença na qualidade do código introduzido através de PRs entre os grupos com e sem a política obrigatória de Code Review.  
- **O2:** Identificar a relação entre a obrigatoriedade da revisão e a densidade de defeitos reportados após o merge do PR.  
- **O3:** Avaliar a eficiência do fluxo de trabalho de integração, focando na velocidade de merge dos PRs e na carga de trabalho de revisão.  
- **O4:** Determinar a percepção dos participantes sobre o valor e o custo do Code Review obrigatório (aprendizado vs. burocracia).

### 3.3 Questões de pesquisa / de negócio

Relacionadas a **O1 (Qualidade do Código):**
- **Q1.1** – Existe diferença significativa na complexidade ciclomática do código submetido via PRs entre os grupos com e sem Code Review obrigatório?  
- **Q1.2** – A obrigatoriedade de Code Review resulta em maior conformidade com padrões de codificação estabelecidos?  
- **Q1.3** – PRs com Code Review obrigatório apresentam melhor manutenibilidade do código medida por índices automatizados?

Relacionadas a **O2 (Densidade de Defeitos):**
- **Q2.1** – A densidade de defeitos detectados após o merge é menor em PRs que passaram por Code Review obrigatório?  
- **Q2.2** – Code Review obrigatório reduz especificamente a ocorrência de bugs críticos e de alta severidade?  
- **Q2.3** – Há diferença na quantidade de vulnerabilidades de segurança introduzidas entre os grupos?

Relacionadas a **O3 (Eficiência do Fluxo):**
- **Q3.1** – Qual o impacto do Code Review obrigatório no tempo decorrido entre abertura e merge dos Pull Requests?  
- **Q3.2** – Qual a carga de trabalho adicional imposta aos revisores em termos de tempo e esforço de revisão?  
- **Q3.3** – O Code Review obrigatório afeta a produtividade geral das equipes medida por throughput de PRs e entregas?

Relacionadas a **O4 (Percepção dos Participantes):**
- **Q4.1** – Os participantes do grupo experimental percebem valor educacional e de aprendizado no processo de Code Review?  
- **Q4.2** – Como os participantes avaliam a relação custo-benefício do Code Review obrigatório em termos de tempo investido versus qualidade obtida?  
- **Q4.3** – Os comentários de revisão são percebidos como construtivos, úteis e respeitosos pelos autores dos PRs?

### 3.4 Métricas associadas (GQM)

#### Tabela GQM Completa

| Objetivo              | Pergunta                                | Métricas Associadas                                  |
|-----------------------|-----------------------------------------|------------------------------------------------------|
| O1 – Qualidade do Código | Q1.1 – Diferença na complexidade ciclomática? | M01 – Complexidade ciclomática média; M02 – Distribuição de complexidade por função |
| O1 – Qualidade do Código | Q1.2 – Maior conformidade com padrões?       | M03 – Taxa de violações de padrão de código; M04 – Número de code smells |
| O1 – Qualidade do Código | Q1.3 – Melhor manutenibilidade?             | M05 – Índice de manutenibilidade; M06 – Taxa de duplicação de código |
| O2 – Densidade de Defeitos | Q2.1 – Menor densidade de defeitos?       | M07 – Densidade de defeitos pós-merge; M08 – Número absoluto de bugs reportados |
| O2 – Densidade de Defeitos | Q2.2 – Redução de bugs críticos?          | M08 – Número absoluto de bugs reportados; M09 – Proporção de bugs críticos/severos |
| O2 – Densidade de Defeitos | Q2.3 – Diferença em vulnerabilidades?     | M10 – Vulnerabilidades de segurança detectadas; M07 – Densidade de defeitos pós-merge |
| O3 – Eficiência do Fluxo   | Q3.1 – Impacto no tempo de merge?         | M11 – Tempo médio até merge do PR; M12 – Tempo de ciclo de feedback |
| O3 – Eficiência do Fluxo   | Q3.2 – Carga de trabalho de revisão?      | M13 – Número de comentários por PR; M14 – Tempo médio de revisão por PR |
| O3 – Eficiência do Fluxo   | Q3.3 – Impacto na produtividade?          | M15 – Throughput de PRs por semana; M16 – Tamanho médio dos PRs |
| O4 – Percepção             | Q4.1 – Percepção de valor educacional?    | M17 – Percepção de aprendizado; M18 – Percepção de melhoria de código |
| O4 – Percepção             | Q4.2 – Avaliação custo-benefício?         | M19 – Percepção de sobrecarga de trabalho; M18 – Percepção de melhoria de código |
| O4 – Percepção             | Q4.3 – Comentários construtivos e úteis?  | M20 – Qualidade percebida dos comentários; M21 – Taxa de comentários acionáveis |

#### Tabela de Definição de Métricas

| ID   | Métrica                           | Descrição                                                                                       | Unidade               | Fonte de Dados                         |
|------|-----------------------------------|-------------------------------------------------------------------------------------------------|-----------------------|----------------------------------------|
| M01  | Complexidade ciclomática média    | Média da complexidade ciclomática (McCabe) de todas as funções/métodos modificados no PR       | valor numérico        | SonarQube / Radon / Lizard             |
| M02  | Distribuição de complexidade      | Percentual de funções com complexidade > 10 (considerada alta)                                 | percentual (%)        | SonarQube / Radon / Lizard             |
| M03  | Taxa de violações de padrão       | Número de violações de linting e style guide por 1000 linhas de código                         | violações/1000 LoC    | ESLint / Pylint / Checkstyle           |
| M04  | Número de code smells             | Quantidade absoluta de *code smells* detectados (código duplicado, métodos longos, acoplamento)| quantidade absoluta   | SonarQube                              |
| M05  | Índice de manutenibilidade        | Score de manutenibilidade baseado em complexidade, volume e comentários (0–100)                | índice (0–100)        | SonarQube Maintainability Index        |
| M06  | Taxa de duplicação de código      | Percentual de linhas de código duplicadas no PR                                                | percentual (%)        | SonarQube / Copy-Paste Detector        |
| M07  | Densidade de defeitos pós-merge   | Número de bugs reportados após merge dividido pelo tamanho do PR                               | defeitos/1000 LoC     | GitHub Issues + análise de commits     |
| M08  | Número absoluto de bugs reportados| Quantidade total de issues marcadas como "bug" relacionadas ao PR nas 2 semanas seguintes      | quantidade absoluta   | GitHub Issues API                      |
| M09  | Proporção de bugs críticos/severos| Percentual de bugs classificados como críticos ou severos em relação ao total de bugs          | percentual (%)        | GitHub Issues (labels de severidade)   |
| M10  | Vulnerabilidades de segurança     | Número de vulnerabilidades de segurança identificadas por análise estática no código do PR     | quantidade absoluta   | SonarQube Security / Snyk / Bandit     |
| M11  | Tempo médio até merge do PR       | Tempo decorrido entre a abertura do PR e seu merge final ao branch principal                   | horas                 | GitHub API (created_at – merged_at)    |
| M12  | Tempo de ciclo de feedback        | Tempo entre solicitação de review e primeiro comentário ou aprovação                            | horas                 | GitHub API (review_requested_at – first_review_at) |
| M13  | Número de comentários por PR      | Quantidade média de comentários de revisão feitos em cada PR                                   | comentários/PR        | GitHub API (review_comments count)     |
| M14  | Tempo médio de revisão por PR     | Tempo total estimado gasto por revisores em cada PR (com base em timestamps)                   | minutos/PR            | GitHub API + análise de eventos        |
| M15  | Throughput de PRs por semana      | Número de Pull Requests completados (merged) por semana de trabalho                            | PRs/semana            | GitHub API (agregação temporal)        |
| M16  | Tamanho médio dos PRs             | Média de linhas adicionadas + removidas por Pull Request                                       | linhas de código (LoC)| GitHub API (additions + deletions)     |
| M17  | Percepção de aprendizado          | Grau de concordância com "Code Review contribuiu para meu aprendizado"                         | escala Likert (1–5)   | Questionário pós-experimento           |
| M18  | Percepção de melhoria de código   | Grau de concordância com "Code Review melhorou a qualidade do código do projeto"               | escala Likert (1–5)   | Questionário pós-experimento           |
| M19  | Percepção de sobrecarga de trabalho| Grau de concordância com "Code Review representou sobrecarga excessiva de trabalho"            | escala Likert (1–5)   | Questionário pós-experimento           |
| M20  | Qualidade percebida dos comentários| Avaliação sobre utilidade, clareza e respeito dos comentários recebidos                        | escala Likert (1–5)   | Questionário pós-experimento           |
| M21  | Taxa de comentários acionáveis    | Proporção de comentários de review que resultaram em mudanças no código                        | percentual (%)        | Análise de review comments + commits   |

---

## 4. Escopo e contexto do experimento

### 4.1 Escopo funcional / de processo (incluído e excluído)

Analisar Pull Requests (PRs) em projetos acadêmicos de Engenharia de Software, **com o propósito de comparar e avaliar**  
- **Com respeito à** qualidade do código introduzido, densidade de defeitos pós-integração, eficiência do fluxo de trabalho e percepção dos participantes  
- **Do ponto de vista de** estudantes (desenvolvedores e revisores) e educadores  
- **No contexto de** equipes acadêmicas que utilizam GitHub para desenvolvimento colaborativo, contrastando projetos com Code Review obrigatório versus projetos sem obrigatoriedade de revisão.

Em resumo, o escopo olha só para o que acontece dentro do fluxo de PRs e revisão, e não para todo o ciclo de vida do projeto.

#### INCLUÍDO no experimento

| Categoria              | Detalhamento                                                                                                                                               |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Atividades Cobertas    | Desenvolvimento de código em feature branches; criação e submissão de PRs; processo de Code Review por pares (no Grupo B); discussão técnica nos PRs; aprovação/reprovação de PRs; merge de PRs aprovados; correções e ajustes solicitados durante a revisão; acompanhamento de bugs reportados após o merge. |
| Artefatos Analisados   | Código-fonte de todas as funcionalidades desenvolvidas; Pull Requests completos (incluindo metadados e *diff* de código); comentários de revisão; commits individuais; relatórios de análise estática (linters); logs de atividade do GitHub; respostas aos questionários pré e pós-experimento. |
| Módulos/Funcionalidades| Funcionalidades de backend e frontend (APIs, lógica, interfaces, componentes); implementação de testes unitários e de integração; correções de bugs e refatorações. |

#### EXCLUÍDO do experimento

| Categoria              | Detalhamento                                                                                                                                               |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Atividades Não Cobertas| Commits diretos ao branch principal (bloqueados); processos de planejamento de sprints e cerimônias ágeis; atividades de levantamento de requisitos e definição de escopo; processos de deploy, CI/CD e operação do sistema; comunicação externa ao GitHub (WhatsApp, e-mail etc.). |
| Artefatos Não Analisados| Documentação externa ao repositório (wikis, documentos de requisitos); artefatos de design e arquitetura (diagramas UML); planos de projeto e relatórios de entrega. |
| Tipos de Código Excluídos| Configurações de infraestrutura (Dockerfiles, configs de CI/CD); arquivos de dados estáticos; dependências de terceiros; código gerado automaticamente por ferramentas. |
| Medições Não Realizadas| Performance em runtime da aplicação; experiência de usuários finais; impacto financeiro; segurança em ambiente de produção real; escalabilidade do sistema. |

### 4.2 Contexto do estudo (tipo de organização, projeto, experiência)
- **Tipo de Organização:** Instituição de Ensino Superior em nível de Graduação.  
- **Tipo de Projeto:** projeto de software de médio porte e complexidade (por exemplo, sistema web ou aplicativo móvel), com foco em desenvolvimento de funcionalidades e trabalho em equipe, com duração típica de um semestre acadêmico.  
- **Criticidade:** Baixa – o projeto é didático; falhas afetam nota, não causam danos financeiros ou operacionais a clientes externos.  
- **Perfil de Experiência dos Participantes:** desenvolvedores juniores (estudantes com 1–2 anos de programação, familiaridade básica com Git e PRs no GitHub, pouca experiência formal em Code Review ou TDD).

### 4.3 Premissas
**P1 – Aprovação ética e consentimento voluntário:**  
O Comitê de Ética em Pesquisa (CEP) da PUC Minas aprovará o protocolo de pesquisa e todos os participantes concordarão voluntariamente em participar após serem informados detalhadamente. O Termo de Consentimento Livre e Esclarecido (TCLE) será assinado antes da coleta de dados, garantindo direito de retirada sem penalidades.

**P2 – Infraestrutura técnica disponível e funcional:**  
Todos terão acesso contínuo à internet, computadores adequados e contas ativas no GitHub; ferramentas de análise estática (SonarQube Community, ESLint/Pylint) estarão configuradas e scripts de coleta via GitHub API funcionarão sem interrupções críticas.

**P3 – Conhecimento técnico mínimo dos participantes:**  
Estudantes possuem conhecimento funcional de Git e domínio intermediário da linguagem escolhida (JavaScript, Python ou Java), não sendo necessário treinamento técnico extensivo além do workshop de 2 horas sobre Code Review.

**P4 – Comparabilidade inicial dos grupos:**  
Grupos controle e experimental terão distribuição similar de habilidades técnicas, experiência prévia e tamanho de equipes. Diferenças pré-existentes serão identificadas via questionário inicial e tratadas como covariáveis.

### 4.4 Restrições
- **R1 – Restrição temporal:** limitado a um semestre letivo de 16 semanas (fevereiro a junho de 2026), incluindo preparação, coleta, análise e consolidação.  
- **R2 – Restrição de tamanho amostral:** número de participantes limitado pelas turmas disponíveis; não há recrutamento externo.  
- **R3 – Restrição orçamentária e de ferramentas:** uso apenas de ferramentas gratuitas ou já integradas à plataforma (sem aquisição de ferramentas pagas).  
- **R4 – Restrição de acesso a dados:** coleta restrita ao que é público via GitHub API e ferramentas integradas; não inclui comunicações privadas (WhatsApp, Discord etc.) ou atividades fora do GitHub.

### 4.5 Limitações previstas
- **L1 – Efeito Hawthorne:** Participantes sabem que **estão sendo observados** e que seus dados estão sendo coletados para pesquisa. Este conhecimento pode **alterar comportamento**, levando a: (a) maior cuidado ao escrever código (independente do Code Review), (b) revisões mais superficiais para "parecer que está fazendo", (c) respostas em questionários influenciadas pelo desejo de "ajudar a pesquisa" ou agradar o pesquisador.

- **L2 – Maturação dos participantes:** Ao longo do semestre, estudantes naturalmente **melhoram suas habilidades de programação** por exposição contínua, prática deliberada, feedback dos professores e aprendizado com erros. Esta maturação pode ser **confundida com o efeito do Code Review**, especialmente se o grupo experimental tiver aprendizado acelerado por outros fatores (ex: professores mais envolvidos, projetos mais desafiadores).

- **L3 – Heterogeneidade das equipes e projetos:** Diferenças substanciais entre equipes incluem: (a) experiência prévia variando de zero a 2 anos profissionais, (b) projetos com domínios e complexidades diferentes (gestão de biblioteca vs. sistema financeiro), (c) tecnologias diversas (JavaScript vs. Python vs. Java), (d) dinâmicas interpessoais únicas (equipes coesas vs. conflituosas), (e) distribuição desigual de habilidades dentro da equipe (uma pessoa muito experiente vs. equipe homogênea).

- **L4 – Tamanho e complexidade variável dos PRs:** Nem todos os PRs são iguais: alguns adicionam uma linha de configuração, outros implementam funcionalidades complexas de 800 linhas. Esta variabilidade: (a) dificulta comparações diretas (PR pequeno naturalmente tem menos bugs), (b) pode enviesar médias se distribuição for diferente entre grupos, (c) requer normalização e análises de sensibilidade.

---

## 5. Stakeholders e impacto esperado

### 5.1 Stakeholders principais
- **Desenvolvedores (alunos):** responsáveis por abrir e revisar PRs.  
- **Professores / orientadores:** responsáveis por acompanhamento e validação do experimento.  
- **Pesquisador:** investigador principal, coordenador do experimento, responsável por coleta e análise.  
- **Coordenação do curso de ES:** aprovação institucional, suporte administrativo, decisão sobre adoção futura.

### 5.2 Interesses e expectativas dos stakeholders

- **Alunos:**  
  - Esperam: aprender boas práticas de revisão, reduzir bugs, produzir código de maior qualidade.  
  - Temem: aumento de burocracia, atrasos no merge e julgamento negativo pelos pares.

- **Professores / Orientadores:**  
  - Esperam: evidências quantificáveis de que Code Review obrigatório melhora a qualidade do código entregue, facilitando correção e avaliação.  
  - Buscam: insights para otimizar metodologias de ensino.

- **Coordenação do Curso:**  
  - Espera: dados para justificar padronização de práticas industriais (Code Review) no currículo, aumentando a empregabilidade dos formandos.

- **Pesquisador:**  
  - Busca: obter resultados estatisticamente significativos para responder às hipóteses e fornecer recomendações baseadas em evidências.

### 5.3 Impactos potenciais no processo / produto

**Durante o experimento:**
- Aumento do tempo médio de merge para PRs com review obrigatório.  
- Maior carga cognitiva e responsabilidade para revisores.  
- Discussões técnicas mais frequentes no repositório.

**Após o experimento:**
- Maior consistência e manutenibilidade do código integrado.  
- Redução de bugs encontrados tardiamente.  
- Disseminação de conhecimento técnico dentro das equipes.

---

## 6. Riscos de alto nível, premissas e critérios de sucesso

### 6.1 Riscos de alto nível
- **R1 (Técnico):** baixa adesão ao processo de revisão.  
- **R2 (Logístico):** volume de PRs inferior ao necessário para análise.  
- **R3 (Técnico):** falhas no ambiente GitHub ou indisponibilidade de métricas.  
- **R4 (Processo):** participantes ignoram o protocolo (merge direto sem review obrigatório).  
- **R5 (Organizacional):** participantes veem o experimento como sobrecarga e não colaboram.

### 6.2 Critérios de sucesso globais (go / no-go)
O experimento será considerado **viável e útil** se:

- For possível coletar **pelo menos 60 PRs analisáveis no total**, com meta de **60–80 PRs**  
  - **Distribuição mínima:** 30 PRs por grupo (controle e experimental).

- **Critério mínimo de viabilidade (plano B):**  
  - Coleta de **30 PRs no total** (15 por grupo).  
  - Nesse cenário, a análise focará **exclusivamente em tamanho de efeito** e será considerada **exploratória**, com **recomendação de replicação futura**.

- Os participantes **aderirem aos protocolos**, incluindo:
  - Obrigatoriedade de review (no grupo experimental).
  - Preenchimento dos formulários.
  - Vinculação adequada de issues.

- Pelo menos **uma métrica de qualidade** indicar **melhora com review obrigatório**, **sem custo proibitivo de tempo**.

### 6.3 Critérios de parada antecipada (pré-execução)
O experimento deve ser suspenso ou adiado se:

- Não houver pelo menos 2 equipes com PRs ativos no período planejado.  
- Não for possível configurar ou aplicar a *branch protection rule* no grupo tratamento.  
- Houver quebra no cronograma da disciplina, inviabilizando entregas ou revisões.  
- Algum erro técnico impedir acesso ou exportação de dados do GitHub.  
- A maioria dos PRs não puder ser rastreada com clareza (sem vínculo com tarefas reais ou sem autores identificados).

---

## 7. Modelo conceitual e hipóteses

### 7.1 Modelo conceitual do experimento
O modelo conceitual deste experimento parte da ideia de que a política de Code Review adotada pela equipe é o principal fator capaz de influenciar a qualidade do código integrado, a ocorrência de defeitos pós-merge, a eficiência do fluxo de trabalho e a percepção dos participantes sobre o processo.

São definidos dois cenários principais:

- **Grupo A – Sem Code Review obrigatório:** PRs podem ser integrados diretamente à branch principal sem exigência formal de aprovação prévia. A revisão, quando ocorre, depende da **iniciativa espontânea** dos membros da equipe.  
- **Grupo B – Com Code Review obrigatório:** PRs só podem ser integrados após **pelo menos uma aprovação formal de revisão**. A branch principal é protegida por regras de *branch protection* no GitHub, forçando a passagem do PR por pelo menos um revisor.

O raciocínio conceitual é:

- A obrigatoriedade de Code Review tende a **aumentar a quantidade** e a profundidade dos comentários de revisão, gerar mais ciclos de retrabalho pré-merge e forçar autores a preparar PRs mais organizados, legíveis e aderentes a padrões.  
- Esse aumento de inspeção e retrabalho pré-merge é esperado reduzir problemas estruturais (complexidade excessiva, duplicação, *smells*), diminuir a quantidade e a densidade de defeitos pós-merge (especialmente bugs severos) e melhorar indicadores de manutenibilidade e conformidade a padrões.  
- Como efeito colateral, Code Review obrigatório pode **aumentar o tempo entre abertura e merge**, elevar a carga de trabalho dos revisores e ser percebido como burocrático, ao mesmo tempo em que é visto como mecanismo de aprendizado e melhoria.

Assim, o experimento busca verificar empiricamente se o aumento de esforço e tempo decorrente da obrigatoriedade do Code Review (fator) se traduz, de fato, em melhoria mensurável de qualidade e redução de defeitos (respostas), e como esse trade-off é percebido pelos estudantes envolvidos.

<img width="382" height="534" alt="diagrmamedicao" src="https://github.com/user-attachments/assets/442b9d1f-9f34-4833-9c55-87e279b45dc2" />


### 7.2 Hipóteses formais (H0, H1)

| Questão                         | Hipótese Nula (H0)                                                    | Hipótese Alternativa (H1)                                                                 |
|---------------------------------|------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| Q1.1 – Complexidade ciclomática | A complexidade ciclomática média dos PRs é igual nos grupos A e B.    | A complexidade ciclomática média dos PRs é menor no grupo B do que no grupo A.           |
| Q1.2 – Conformidade com padrões | A conformidade com padrões de codificação é igual nos grupos A e B.   | A conformidade com padrões é maior no grupo B, com menos violações e *code smells*.      |
| Q1.3 – Manutenibilidade         | A manutenibilidade do código é igual entre os grupos A e B.           | A manutenibilidade é melhor no grupo B (índice mais alto e/ou menor duplicação).         |
| Q2.1 – Densidade de defeitos    | A densidade de defeitos após merge é igual entre A e B.               | A densidade de defeitos é menor no grupo B do que no grupo A.                            |
| Q2.2 – Bugs críticos/severos    | A proporção de bugs críticos é igual entre os grupos.                 | A proporção de bugs críticos é menor no grupo B do que no grupo A.                       |
| Q2.3 – Vulnerabilidades         | A quantidade de vulnerabilidades é igual entre os grupos.             | O grupo B introduz menos vulnerabilidades de segurança que o grupo A.                    |
| Q3.1 – Tempo até o merge        | O tempo médio entre abertura e merge é igual entre os grupos.         | O tempo médio é maior no grupo B do que no grupo A.                                      |
| Q3.2 – Carga de trabalho        | A carga de revisão é igual entre os grupos.                           | O grupo B tem maior carga de revisão (mais comentários e/ou tempo).                      |
| Q3.3 – Produtividade            | A produtividade (throughput e tamanho médio de PRs) é igual nos grupos.| O Code Review obrigatório afeta a produtividade (reduz throughput e/ou muda tamanho médio). |
| Q4.1 – Valor educacional        | A percepção de aprendizado é igual nos grupos.                         | O grupo B percebe maior valor educacional no Code Review do que o grupo A.              |
| Q4.2 – Custo-benefício          | A percepção de custo-benefício é igual entre os grupos.               | O grupo B percebe mais sobrecarga/burocracia, mas maior benefício em qualidade.         |
| Q4.3 – Qualidade dos comentários| A qualidade dos comentários é igual nos grupos.                        | Comentários do grupo B são percebidos como mais úteis, construtivos e respeitosos.      |

Em síntese, as hipóteses alternativas convergem para a ideia de que o Code Review obrigatório deve trazer melhor qualidade e menos defeitos no Grupo B, à custa de maior tempo até o merge e maior carga de trabalho de revisão.

### 7.3 Nível de significância e considerações de poder

O nível de significância (α) adotado será de **0,05** para todos os testes. Assim, as hipóteses nulas serão rejeitadas quando o valor de **p < 0,05**, aceitando-se até 5% de risco de concluir que existe um efeito quando, na realidade, ele não existe (Erro Tipo I). Os testes serão predominantemente **bicaudais**, de modo a acomodar achados exploratórios em que o efeito possa surgir em qualquer direção.

O **poder estatístico (1 − β)** é limitado pelo tamanho amostral previsto: aproximadamente 4–6 equipes, 20–30 participantes e 60–80 PRs no total (30–40 por grupo). Esse cenário é adequado para detectar **efeitos moderados a grandes** (por exemplo, **Cohen’s d ≥ 0,5**), mas tem baixa capacidade para identificar **efeitos pequenos**. Além disso, a dependência entre observações dentro da mesma equipe reduz o “n efetivo”, o que reforça a necessidade de interpretar os resultados com cautela.

Como o plano inclui **cerca de 12 testes de hipóteses**, há risco de **inflação do Erro Tipo I** devido a múltiplas comparações. Por esse motivo, os valores de *p* não serão interpretados de forma isolada: será dada ênfase à **consistência entre métricas relacionadas** (por exemplo, diferentes medidas de qualidade ou de defeitos) e ao padrão geral dos resultados, e não apenas a significâncias pontuais.

Para mitigar o risco de **Erro Tipo II** (não detectar efeitos que realmente existem), os resultados serão sempre acompanhados de **tamanhos de efeito** (por exemplo, **Cohen’s d**) e de uma discussão sobre a **relevância prática** das diferenças observadas, além dos p-values. Em termos práticos, a interpretação final privilegiará a combinação entre **significância estatística**, **magnitude do efeito** e **importância prática** no contexto de projetos acadêmicos com Code Review obrigatório.

---

## 8. Variáveis, fatores, tratamentos e objetos de estudo

### 8.1 Objetos de estudo
Os principais objetos de estudo deste experimento são os **Pull Requests (PRs)** produzidos pelas equipes durante o desenvolvimento dos projetos acadêmicos. Cada PR será tratado como uma unidade de análise, incluindo: o código-fonte modificado (arquivos alterados, funções/métodos novos ou refatorados), o diff entre o branch de origem e a branch principal, os metadados do PR (autor, data de abertura, data de merge, tamanho em linhas adicionadas/removidas), os comentários de revisão associados (quando houver), os eventos de aprovação/reprovação e o histórico de commits vinculados a esse PR.

Além dos PRs em si, serão analisadas as **issues de bug** relacionadas a esses PRs (especialmente aquelas abertas após o merge), usadas para medir defeitos pós-integração e severidade dos problemas reportados. Para complementar a análise quantitativa, também serão considerados como objetos de estudo os relatórios de análise estática de código (métricas de complexidade, duplicação, code smells, vulnerabilidades) e as **respostas aos questionários aplicados aos participantes**, que capturam percepções de aprendizado, sobrecarga e qualidade das revisões.

### 8.2 Sujeitos / participantes (visão geral)
Os sujeitos deste experimento serão estudantes de graduação em Engenharia de Software matriculados em disciplinas de desenvolvimento de software que utilizam projetos em equipe com versionamento no GitHub. Esses estudantes atuarão principalmente como desenvolvedores (autores de Pull Requests) e revisores de código (avaliando PRs de colegas), acumulando, na prática, ambos os papéis ao longo do semestre.

De forma geral, trata-se de participantes com perfil de desenvolvedores juniores, com cerca de 1 a 2 anos de experiência em programação (disciplinas anteriores, projetos acadêmicos e, eventualmente, estágios), familiaridade básica com controle de versão em Git e uso de PRs no GitHub, mas pouca ou nenhuma experiência formal em processos estruturados de Code Review.

Os estudantes estarão organizados em equipes de 3 a 6 integrantes (2-3 equipes por grupo, totalizando 4-6 equipes), distribuídas entre um grupo controle (sem Code Review obrigatório) e um grupo experimental (com Code Review obrigatório). Professores e orientadores terão participação indireta como facilitadores e monitores do experimento, mas não como sujeitos principais de medição.

### 8.3 Variáveis independentes (fatores) e seus níveis

| Fator               | Descrição                                        | Níveis                                                        |
|---------------------|--------------------------------------------------|---------------------------------------------------------------|
| Política de Code Review | Política de revisão antes do merge no branch principal | Nível 0: Sem Code Review obrigatório (Controle) <br> Nível 1: Com Code Review obrigatório (Experimental) |

### 8.4 Tratamentos (condições experimentais)

| Tratamento | Grupo              | Descrição Completa                                                                                                           | N Esperado                          |
|-----------|--------------------|------------------------------------------------------------------------------------------------------------------------------|-------------------------------------|
| T0 – Controle    | Grupo A (Controle)    | Equipes desenvolvem usando GitHub Flow (branches → PR → merge) **sem** exigência de Code Review. PRs podem ser mergeados pelo próprio autor ou qualquer membro sem aprovação formal. | 2–3 equipes; 10–15 participantes; 30–40 PRs |
| T1 – Experimental | Grupo B (Experimental) | Equipes desenvolvem usando GitHub Flow **com** Code Review obrigatório. *Branch protection* exige mínimo de 1 aprovação antes do merge.            | 2–3 equipes; 10–15 participantes; 30–40 PRs |

### 8.5 Variáveis dependentes (respostas)

| ID   | Variável Dependente                | Categoria            | Tipo de Dado          |
|------|------------------------------------|----------------------|-----------------------|
| M01  | Complexidade ciclomática média     | Qualidade Técnica    | Quantitativa contínua |
| M03  | Taxa de violações de padrão de código | Qualidade Técnica | Quantitativa contínua |
| M07  | Densidade de defeitos pós-merge    | Confiabilidade       | Quantitativa contínua |
| M08  | Número absoluto de bugs reportados | Confiabilidade       | Quantitativa discreta |
| M11  | Tempo médio até merge do PR        | Eficiência de Processo | Quantitativa contínua |
| M13  | Número de comentários por PR       | Interação/Esforço    | Quantitativa discreta |
| M15  | Throughput de PRs por semana       | Produtividade        | Quantitativa contínua |
| M17  | Percepção de aprendizado           | Percepção Subjetiva  | Ordinal               |
| M19  | Percepção de sobrecarga de trabalho| Percepção Subjetiva  | Ordinal               |
| M20  | Qualidade percebida dos comentários| Percepção Subjetiva  | Ordinal               |

### 8.6 Variáveis de controle / bloqueio

| Variável de Controle          | Descrição                               | Como será controlada                 | Justificativa                                        |
|-------------------------------|-----------------------------------------|--------------------------------------|------------------------------------------------------|
| Experiência em programação    | Anos de prática, projetos anteriores    | Questionário inicial                 | Experiência pode confundir efeito do tratamento      |
| Familiaridade com Git/GitHub  | Conhecimento de controle de versão      | Questionário inicial, estratificação | Influencia facilidade de usar GitHub Reviews         |
| Tamanho da equipe             | Número de membros (3–6)                 | Balanceamento entre grupos           | Equipes maiores têm dinâmicas e produtividade distintas |
| Complexidade do projeto       | Escopo e dificuldade do domínio         | Avaliação docente, uso como covariável| Projetos mais complexos tendem a gerar mais bugs     |

### 8.7 Possíveis variáveis de confusão conhecidas

| Variável de Confusão                         | Como Pode Distorcer o Resultado                                                                                                                                                     | Estratégia de Mitigação no Plano                                                                                                                                                                                                 |
|---------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Contaminação entre Grupos (Diffusion of treatment) | O grupo controle (A) pode adotar o Code Review voluntariamente após aprender sobre sua importância no treinamento (10.6) ou observar o grupo experimental (B).                      | **Monitoramento:** Coleta de dados via API para rastrear a taxa de aprovações formais no Grupo A. **Análise:** Uso de análise *as-treated* (o que foi realmente feito) se a contaminação for significativa.                      |
| Maturação dos Participantes (Maturation)     | Estudantes melhoram naturalmente suas habilidades de programação e Git ao longo do semestre (L2), confundindo o efeito natural com o efeito do CR.                                 | **Controle:** Uso do Grupo Controle (A) como baseline para a melhoria natural. **Modelagem:** Inclusão da covariável “semana do semestre” nos Modelos Mistos (LMM) para controlar a tendência temporal de melhoria.              |
| Efeito Hawthorne                            | Participantes alteram o comportamento (melhor qualidade ou revisões mais superficiais) por saberem que estão sendo observados (L1).                                                 | **Mitigação:** Não é eliminável, mas é atenuado, pois ambos os grupos são observados igualmente. **Blind parcial:** Os participantes não conhecem todas as hipóteses específicas da pesquisa (apenas o objetivo geral de qualidade). |
| Complexidade do Projeto                     | Diferenças na complexidade inerente dos projetos (L3) podem causar mais defeitos, independentemente da política de CR.                                                              | **Controle:** Coleta de avaliação docente da complexidade do projeto (escala 1–5) e inclusão como covariável fixa nos modelos de análise (LMM) para ajustar os resultados.                                                       |
| Experiência Desigual entre Grupos (Selection) | Se o Grupo B tiver, por acaso, desenvolvedores mais experientes, qualquer melhoria na qualidade pode ser atribuída à experiência, e não ao Code Review (P4).                      | **Controle:** Os dados do questionário inicial sobre experiência serão usados em ANCOVA ou como covariável fixa nos LMM, ajustando estatisticamente o efeito da experiência.                                                   |
| Tamanho Variável do PR                      | PRs muito grandes (que naturalmente têm mais defeitos) ou muito pequenos (L4) distorcem as comparações diretas de contagem de bugs.                                                | **Normalização:** Calcular métricas relativas (ex.: Densidade de Defeitos = bugs/1000 LoC). **Modelagem:** Incluir o tamanho do PR (M16) como covariável nos modelos.                                                            |

---

## 9. Desenho experimental

### 9.1 Tipo de desenho
O desenho escolhido é um **quasi-experimento de campo**, com **grupo controle não equivalente**, em arranjo **between-subjects** e **randomização ao nível de equipe**.

O arranjo *between-subjects* é adotado porque cada equipe ficará exposta a **apenas uma condição** ao longo de todo o semestre: ou **Code Review obrigatório** (Grupo B) ou **Code Review opcional/não obrigatório** (Grupo A). Em outras palavras, cada equipe “vive em um único cenário” durante o experimento. Se a mesma equipe passasse pelos dois tratamentos (*within-subjects*), haveria um efeito de aprendizado irreversível: uma vez que os alunos aprendem a revisar código de forma estruturada, é praticamente impossível “desaprender” a prática. Além disso, em uma disciplina semestral, não há um período de *washout* viável, e os efeitos de ordem (primeiro A depois B, ou o contrário) se tornariam confundidores sérios.

Trata-se de um **quasi-experimento** porque, embora exista randomização, ela não é feita sobre indivíduos isolados, e sim sobre **grupos intactos** já formados pela disciplina (equipes de projeto). Há restrições institucionais importantes: as equipes já estão constituídas, horários são fixos e as turmas são pré-estabelecidas. Por isso, a randomização ocorre no nível da equipe, o que exige **controle estatístico cuidadoso** de variáveis preexistentes, como experiência em programação, familiaridade com Git/GitHub, tamanho da equipe e complexidade do projeto.

A presença de um **grupo controle** é essencial para isolar o efeito específico da política de Code Review em relação a outros fatores que também podem influenciar a qualidade do código e o processo, como **maturação dos estudantes ao longo do semestre**, **efeito Hawthorne** e **eventos externos da disciplina**. Sem um grupo controle trabalhando em condições semelhantes, mas sem a obrigatoriedade de revisão, seria muito mais difícil atribuir qualquer melhoria observada diretamente ao tratamento (Code Review obrigatório).

### 9.2 Randomização e alocação
A randomização será feita no nível das equipes, e não dos indivíduos. Equipes completas de desenvolvimento serão aleatoriamente alocadas ao grupo controle (A) ou ao grupo experimental (B). A unidade de randomização, portanto, é a própria equipe, que será exposta a apenas um dos dois níveis de tratamento: Code Review obrigatório ou Code Review opcional.

No contexto deste estudo, as equipes não são formadas especificamente para o experimento, mas aproveitam a organização já existente nas disciplinas de desenvolvimento de software da graduação. Em cada turma participante, os estudantes são distribuídos em equipes de 3 a 6 integrantes (seja por alocação do professor, seja por autoformação dos alunos) para desenvolver um projeto colaborativo ao longo do semestre, utilizando um repositório no GitHub por equipe. Esses times de projeto, já constituídos por razões pedagógicas, são então utilizados como unidades de randomização: cada equipe inteira é sorteada para o grupo controle ou experimental, preservando a forma natural de trabalho da disciplina.

Na prática, o procedimento seguirá três passos: primeiro, listar todas as equipes elegíveis para o experimento; em seguida, aplicar um método de alocação aleatória (por exemplo, sorteio simples ou uso de um gerador de números aleatórios) para designar cada equipe ao Grupo A (controle) ou ao Grupo B (experimental), buscando manter o balanceamento numérico entre eles (cerca de 2–3 equipes por grupo); por fim, verificar o resultado dessa alocação por meio de uma análise estatística inicial das variáveis de controle (como experiência prévia em programação e tamanho da equipe), de modo a avaliar se os grupos ficaram razoavelmente equilibrados. Caso se observem assimetrias relevantes, essas variáveis serão posteriormente consideradas como covariáveis na análise dos resultados.

### 9.3 Balanceamento e contrabalanço
O balanceamento é crucial para garantir que as diferenças observadas no final sejam causadas pelo tratamento (Code Review) e não por diferenças iniciais.
O balanceamento será checado comparando as médias das Variáveis de Controle (experiência prévia, familiaridade com Git/GitHub, tamanho da equipe) entre o Grupo A e o Grupo B, utilizando os dados do questionário inicial. Se a randomização inicial resultar em grupos desequilibrados (ex: Grupo B significativamente mais experiente que o Grupo A), as variáveis de controle serão utilizadas como covariáveis na análise estatística, ajustando matematicamente os resultados ao remover o impacto da diferença inicial de experiência.
O Contrabalanço não é aplicável neste desenho, pois ele é usado em desenhos Within-Subjects (onde a mesma equipe passa por A e depois B) para mitigar o efeito de ordem e aprendizado. Como o tratamento é fixo (Between-Subjects), essa técnica não é necessária.

### 9.4 Número de grupos e sessões
- Haverá **dois grupos** distintos:
  - Grupo A (Controle): Code Review opcional.  
  - Grupo B (Experimental): Code Review obrigatório.  

O experimento será executado ao longo de um único período contínuo de 16 semanas (Restrição R1), que engloba o semestre letivo completo. Dentro desse intervalo, a intervenção propriamente dita, isto é, a aplicação da regra de branch protection no grupo experimental, permanecerá ativa durante todo o período de desenvolvimento efetivo, estimado em aproximadamente 12 a 14 semanas. As “sessões” de trabalho são os ciclos de desenvolvimento (sprints semanais ou quinzenais) nos quais as equipes criam e fazem merge de Pull Requests. O número de PRs gerados ao longo desses ciclos (estimado entre 60 e 80 PRs no total) é o que definirá, na prática, o tamanho amostral disponível para análise estatística. A coleta contínua durante todo o semestre permite capturar a dinâmica completa de desenvolvimento das equipes e o efeito da maturação dos participantes (L2) em ambos os grupos, produzindo um retrato mais realista do impacto do Code Review na qualidade do software em um contexto de projeto acadêmico de médio prazo.


## 10. População, Sujeitos e Amostragem

### 10.1 População-alvo

A população-alvo deste experimento compreende **desenvolvedores juniores** em estágios iniciais de carreira ou equipes com **baixa maturidade de processo**, atuando em contextos colaborativos com foco em qualidade e compartilhamento de conhecimento entre pares.  
Mais especificamente, **estudantes de graduação** em Engenharia de Software ou Ciência da Computação, envolvidos em **projetos colaborativos de médio prazo com uso de versionamento distribuído**.

### 10.2 Critérios de Inclusão

Os participantes devem atender aos seguintes critérios mínimos:

- **Vínculo Acadêmico:** Estar regularmente matriculado em disciplinas da IES parceira que envolvam projetos colaborativos.
- **Papel:** Estar alocado em uma equipe de desenvolvimento (3 a 6 alunos).
- **Conhecimento Técnico (P3):** Possuir conhecimento funcional de Git (commit, push, pull, branch, merge).
- **Consentimento Ético (P1):** Concordar com a participação voluntária e assinar o **Termo de Consentimento Livre e Esclarecido (TCLE)**.
- **Disponibilidade:** Participar ativamente durante o semestre (16 semanas – R1).

### 10.3 Critérios de Exclusão

- Recusa em assinar o TCLE.
- Experiência profissional **sênior** ou mais de **5 anos de experiência na indústria**.
- Conflito de interesses (ex.: monitor da disciplina com papel avaliativo).

### 10.4 Tamanho da Amostra Planejado (por Grupo)

O tamanho da amostra é uma limitação (R2) definida principalmente pela quantidade de turmas e equipes disponíveis no semestre. A ideia é **trabalhar com o máximo de PRs possível dentro da realidade da disciplina**, sem propor um número irrealista para o contexto acadêmico.

- **Unidade de Análise (PRs):**  
  Pretende-se obter um mínimo de **60 a 80 Pull Requests no total** (aproximadamente 30–40 por grupo). Esse volume é considerado suficiente para alcançar um **poder estatístico razoável** para detectar efeitos de magnitude moderada (Cohen’s d ≥ 0,5), mesmo levando em conta que os dados estão agrupados por equipe.

- **Unidade de Alocação (Equipes):**  
  As equipes são a unidade em que o tratamento é aplicado. Estima-se trabalhar com **4 a 6 equipes no total**, distribuídas em **2–3 equipes por grupo** (controle e experimental). Em termos práticos, cada time contribui com vários PRs ao longo do semestre, o que ajuda a compor o número total de observações.

- **Participantes (Sujeitos):**  
  Considerando equipes de 3 a 6 integrantes, espera-se ter entre **12 e 18 sujeitos por grupo**, totalizando aproximadamente **24 a 36 participantes** no experimento. Esse número reflete a realidade das turmas e é suficiente para observar padrões de comportamento e percepção entre grupos com e sem Code Review obrigatório.

> Em resumo, a decisão de amostra equilibra **viabilidade prática** (R2) e a busca por um número de PRs que permita analisar diferenças entre os grupos com algum grau de confiança, **maximizando o número de observações dentro das restrições temporais e logísticas do semestre.**


### 10.5 Método de Seleção / Recrutamento

A seleção será feita por **amostragem por conveniência** (não probabilística).

Os participantes serão recrutados a partir de turmas de disciplinas específicas do curso de Engenharia de Software da IES parceira que realizam projetos colaborativos obrigatórios. O Pesquisador Principal fará o convite formal, com o apoio do(s) professor(es) da disciplina. A alocação das equipes aos grupos (Controle vs. Experimental) será feita por randomização (Seção 9.2).


### 10.6 Treinamento e Preparação dos Sujeitos

Para garantir nivelamento e reduzir viés técnico:

- Todos os participantes (Grupos A e B) participarão de um **workshop inicial padronizado** (P3).
- **Duração:** 1–2 horas.
- **Conteúdo:**
  - Fluxo de trabalho de **Pull Request no GitHub**.
  - Princípios de **Code Review Pedagógico**: foco em manutenibilidade, padrões e feedback construtivo (Q4.3).
  - Regras de codificação e boas práticas (P3).

> Objetivo: Garantir que o Grupo Controle (A), mesmo sem obrigatoriedade, siga boas práticas ao realizar revisões espontâneas. Assim, isola-se o efeito da **obrigatoriedade via branch protection**, e não apenas da prática em si.


---

## 11. Instrumentação e Protocolo Operacional

### 11.1 Instrumentos de Coleta (questionários, logs, planilhas, etc.)

| Instrumento                 | Categoria de Dados                 | Variáveis / Métricas (Ex.)                                      | Fonte de Dados                              |
|----------------------------|------------------------------------|------------------------------------------------------------------|---------------------------------------------|
| GitHub API (Scripts)       | Eficiência / Interação / Produtividade | M11 (Tempo Merge), M13 (Comentários), M15 (Throughput)          | Extração Automatizada (P2)                  |
| Análise Estática de Código | Qualidade Técnica / Segurança      | M01 (Complexidade), M05 (Manutenibilidade), M10 (Vulnerabilidades) | SonarQube / ESLint / Pylint (R3)           |
| Questionário Inicial       | Variáveis de Controle              | Experiência, Familiaridade com Git/GitHub                        | Formulário Digital (Google Forms)          |
| Questionário Pós-Experimento | Percepção Subjetiva             | M17 (Aprendizado), M19 (Sobrecarga), M20 (Qualidade Comentários) | Formulário Digital (Google Forms)          |
| Rastreamento de Issues     | Confiabilidade / Defeitos          | M07 (Densidade Defeitos), M09 (Severidade Crítica)               | Análise e Classificação de Issues do GitHub |



### 11.2 Materiais de Suporte 

- **TCLE:** Documento de consentimento (P1).
- **Guia de Workflow e Regras:** Instruções detalhando o fluxo de desenvolvimento do projeto e as convenções de código (P3).
- **Manual da Regra de Merge:** Especificação clara da diferença entre:
  - Processo do **Grupo A** (opcional).
  - Processo do **Grupo B** (obrigatoriedade de 1 aprovação).

---

### 11.3 Procedimento Experimental

O experimento será dividido em fases operacionais ao longo das 16 semanas.

**Pré-Execução (Semanas 1–2)**  
- Obtenção da Aprovação Ética (CEP) e TCLE (P1).  
- Aplicação do Questionário Inicial (Variáveis de Controle).  
- Randomização das Equipes em Grupo A e B (Seção 9.2).  
- Treinamento Padrão de 1–2h (Seção 10.6).  
- Configuração dos Repositórios: aplicação da **Branch Protection Rule** no Grupo B (P2).

**Execução (Semanas 3–15)**  
- Desenvolvimento de features e submissão de PRs.  
- **Grupo A (Controle):** PRs mergeados livremente.  
- **Grupo B (Tratamento):** PRs bloqueados sem pelo menos 1 aprovação de par.  
- **Coleta Contínua Automatizada:** scripts extraem dados da API e das ferramentas estáticas a cada merge ou período definido.

**Pós-Execução (Semana 16)**  
- Aplicação do Questionário Pós-Experimento (Percepção M17–M20).  
- Classificação manual dos bugs (M09) e consolidação final de todos os dados.  
- Análise estatística (Seção 12).

<img width="364" height="1072" alt="diagramamedicaoooo" src="https://github.com/user-attachments/assets/5b8a6922-4d8d-413a-9abc-b246c4aea1d5" />



### 11.4 Plano de Piloto 

Será realizado um piloto de curta duração (1–2 semanas), envolvendo uma amostra muito pequena de equipes ou alunos de uma turma anterior (se possível), ou nas primeiras semanas do semestre.

**Objetivos do Piloto:**
- Testar a operacionalização da **Branch Protection Rule** (P2), garantindo que ela não seja contornada.  
- Validar o funcionamento dos scripts de coleta e a integração com as ferramentas de análise estática (R3).  
- Avaliar a clareza e o tempo de preenchimento dos questionários (M17–M20).

**Critérios de Ajuste:** O protocolo será ajustado se a taxa de falha na coleta automatizada for superior a 5%, ou se o treinamento não for suficiente para que os alunos do Grupo B entendam suas responsabilidades como revisores.

---

## 12. Plano de Análise de Dados

### 12.1 Estratégia Geral de Análise

A estratégia central é a **comparação estatística** das métricas de resultado entre o **Grupo A** e o **Grupo B** para validar as hipóteses direcionais (H1).

Os dados coletados serão usados para responder aos objetivos da seguinte forma:

| Objetivo     | Resposta                                                                                                  |
|-------------|-----------------------------------------------------------------------------------------------------------|
| Qualidade (O1)  | Comparar média/mediana do **Índice de Manutenibilidade (M05)** e da **Complexidade Ciclomática (M01)** para verificar se o Grupo B é superior/inferior. |
| Defeitos (O2)   | Comparar a **Densidade de Defeitos (M07)** e a **Proporção de Bugs Críticos (M09)** para verificar se o Code Review obrigatório reduz bugs. |
| Eficiência (O3) | Comparar o **Tempo Médio até Merge (M11)** e a **Carga de Revisão (M13, M14)** para medir o custo do processo. |
| Percepção (O4)  | Comparar as **medianas das escalas Likert (M17, M19)** para entender o trade-off percebido entre aprendizado e sobrecarga. |


### 12.2 Métodos estatísticos planejados

Dado que o desenho experimental envolve **randomização por cluster (equipes)** e que os Pull Requests (PRs) estão **agrupados dentro dessas equipes** (*nested structure*), a análise considerará explicitamente a **estrutura hierárquica dos dados**. Ignorar essa dependência comprometeria a validade de conclusão do estudo.

Será adotada uma **abordagem multinível**, com três estratégias complementares para garantir a robustez dos resultados:

#### 12.2.1 Análise primária: Modelos Lineares Mistos (LMM)

A análise primária será feita com **Modelos Lineares Mistos (LMM)**, que são mais adequados para **dados agrupados por equipe**, como é o caso deste experimento. Em vez de fingir que cada PR é totalmente independente, o LMM leva em conta que PRs da mesma equipe tendem a se parecer mais entre si do que com PRs de outras equipes.  
> Em outras palavras, é aqui que eu mostro que não vou “enganar” a estatística tratando PR de um mesmo time como se fosse de pessoas totalmente independentes.

- **Estrutura do modelo:**  
  - Serão utilizados **LMMs** para as métricas contínuas mais importantes (por exemplo, M01 – Complexidade, M05 – Manutenibilidade, M07 – Densidade de Defeitos, M11 – Tempo até o Merge).  
  - A **Equipe** será incluída como **efeito aleatório (random intercept)**, justamente para capturar essa variação “entre equipes” e controlar a não-independência das observações dentro de cada cluster.

- **Controle de covariáveis:**  
  - Variáveis de controle coletadas no início, como **experiência prévia em programação** e **tamanho da equipe**, serão incluídas no modelo como **efeitos fixos**.  
  - Isso permite **ajustar o efeito do tratamento** (Code Review obrigatório) caso os grupos não fiquem perfeitamente balanceados após a randomização (por exemplo, se um grupo acabar com equipes mais experientes).

- **Requisito de uso:**  
  - Essa abordagem será utilizada como **análise primária** desde que:
    - o **número total de PRs** seja de pelo menos **60 PRs**; e  
    - cada equipe contribua com uma quantidade mínima de dados, idealmente **10 PRs ou mais por equipe**.  
  - Se esses requisitos não forem atendidos, os LMMs ainda podem ser utilizados de forma exploratória, mas os resultados serão interpretados com maior cautela.
 
  
#### 12.2.2 Análise de sensibilidade: agregação por equipe
Como forma de **verificar e validar** os resultados obtidos pelos modelos multinível, será realizada uma **análise de sensibilidade** baseada na **agregação por equipe**. Essa estratégia funciona como um “segundo olhar”, mais conservador, para checar se as conclusões se mantêm mesmo com uma suposição bem mais rígida de independência.  

- **Unidade de análise:**  
  - Em vez de analisar PR a PR, as métricas serão **agregadas ao nível da equipe**, produzindo um valor resumo por time.  
  - Isso resulta em um **N bem pequeno (≈ 4–6 equipes)**, mas com **independência completa entre observações**, já que cada equipe passa a ser uma unidade isolada.

- **Teste estatístico:**  
  - Para comparar as métricas agregadas entre o **Grupo A (controle)** e o **Grupo B (experimental)**, será utilizado o **Teste de Mann-Whitney U**, que é **não-paramétrico** e não depende da suposição de normalidade dos dados.  
  - Esse teste será aplicado sobre as **médias ou medianas por equipe** das métricas de maior interesse, como qualidade, defeitos e tempo até o merge.

- **Função na análise geral:**  
  - Embora essa abordagem **reduza bastante o poder estatístico** (porque o número de equipes é pequeno), ela:
    - garante **independência total** entre as unidades analisadas; e  
    - fornece uma visão **mais conservadora** dos resultados, servindo como checagem: se o padrão observado nos LMMs também aparece aqui, a confiança nas conclusões aumenta.


#### 12.2.3 Análise de confirmação: ajuste robusto de erro-padrão

Além dos modelos mistos e da agregação por equipe, será conduzida uma **análise de confirmação** utilizando **testes t simples** com **ajuste de erros-padrão robustos por cluster**.  

- **Objetivo principal:**  
  - Verificar se as conclusões sobre diferenças entre **Grupo A** e **Grupo B** se mantêm mesmo quando usamos uma estrutura de teste mais simples, porém ajustada para clustering.

- **Estratégia técnica:**  
  - Serão ajustados **testes t para comparação de médias** entre os grupos, porém com **erros-padrão corrigidos por cluster de equipe**.  
  - Essa correção robusta compensa o fato de que os PRs do mesmo time são mais parecidos entre si do que com PRs de outros times, evitando subestimação artificial da variabilidade.

- **Papel na robustez geral:**  
  - Se os resultados dos LMMs e dos testes t com erro-padrão robusto convergirem para a mesma interpretação (mesmo sinal de efeito e mesma direção de diferença entre grupos), isso **reforça a confiança** nas conclusões.  
  - Em outras palavras, essa etapa funciona como um **“segundo carimbo de conferência”**: um método mais simples, mas estatisticamente cuidadoso, confirmando o padrão observado na análise principal.

#### 12.2.4 Resumo dos métodos por tipo de métrica

| Categoria de Métrica                        | Distribuição         | Método Primário (poder ótimo)                                                           | Método Secundário (conservador)                                       |
|--------------------------------------------|----------------------|-----------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| Quantitativa contínua (M01, M05, M07, M11) | Normal / Desconhecida | **LMM** com efeito aleatório de Equipe (ou **GLMM** com transformação logarítmica)     | Agregação por Equipe + **Mann-Whitney U**                             |
| Ordinal (Likert) (M17, M19, M20)           | Não-paramétrica      | Agregação por Equipe + **Mann-Whitney U**                                              | Modelo **ordinal misto**, se a distribuição permitir estabilidade     |
| Ajuste de covariáveis                      | —                    | **LMM** incluindo Experiência e Tamanho da Equipe como variáveis fixas                 | **ANCOVA** após a agregação dos dados por equipe                      |

#### 12.2.5 Critério de decisão em caso de divergência

Em caso de **resultados divergentes** entre:

- a análise **multinível** (LMM), e  
- a análise **agregada por equipe**,  

a interpretação irá:

- **priorizar a análise multinível (LMM)**, por:
  - ter **maior poder estatístico**, aproveitando melhor o conjunto total de PRs; e  
  - tratar corretamente a **estrutura hierárquica dos dados** (PRs dentro de equipes), que é a forma como os dados são realmente gerados no experimento.

Ao mesmo tempo, a análise agregada por equipe será usada como um **piso conservador**: seus resultados também serão sempre reportados, funcionando como uma checagem de robustez.  

Em outras palavras, se os dois métodos “contarem a mesma história”, isso reforça a confiança nas conclusões; se divergirem, o LMM será tomado como análise principal, mas as limitações e diferenças observadas serão explicitamente discutidas no texto.


#### 12.2.6 Nota sobre múltiplas comparações e tamanho do efeito

- **Erro Tipo I (falso positivo):**  
  Dado o total de **≈12 testes de hipóteses**, há risco de **inflação do Erro Tipo I**. Assim:
  - os **valores de p serão interpretados com cautela**;  
  - será priorizada a **consistência dos resultados** entre métricas relacionadas, em vez de foco exclusivo em significância isolada.

- **Erro Tipo II (falso negativo):**  
  Para mitigar o risco de não detectar efeitos relevantes:
  - serão reportados **tamanhos de efeito** (por exemplo, **Cohen’s d** ou **Cliff’s Delta**);  
  - será destacada a **relevância prática** das descobertas, complementando os testes de significância estatística.


### 12.3 Tratamento de Dados Faltantes e Outliers

- **Dados Faltantes (PRs):** PRs que não puderem ser vinculados a uma issue ou que não tenham dados completos de merge serão excluídos por caso da análise específica daquela métrica. A porcentagem de exclusão será rigorosamente documentada.

- **Outliers:** Valores extremos (ex: PRs com tempo de merge de 3 meses, M11) serão identificados. Em vez de excluir, será priorizada a transformação logarítmica ou o uso de testes não-paramétricos (Mann-Whitney U), que são menos sensíveis a outliers, mitigando a perda de poder.

### 12.4 Plano de Análise para Dados Qualitativos

Os comentários de revisão (M13) e as respostas abertas do questionário serão tratados como **dados qualitativos** para contextualizar os achados quantitativos.

- **Técnica:** Análise de Conteúdo Temática.  
- **Procedimento:**  Os comentários serão lidos e codificados indutivamente em categorias (ex: "Problema de Padrão", "Sugestão de Design", "Bug Funcional") para verificar se o foco das revisões difere entre o Grupo A e o Grupo B.

---

## 13. Avaliação de validade (ameaças e mitigação)

### 13.1 Validade de conclusão

Refere-se à capacidade de inferir corretamente se o **Code Review obrigatório** e as **métricas de Qualidade/Eficiência** estão relacionados, sem erro.

| Ameaça                   | Descrição do Risco                                                                                                                                             | Estratégia de Mitigação                                                                                                                                               |
|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Baixo Poder Estatístico  | O tamanho amostral limitado (R2) de 60–80 PRs no total pode não ser suficiente para detectar efeitos reais de magnitude pequena ou moderada.                    | **Mitigação principal:** Focar a análise no **tamanho do efeito** (ex.: Cohen's d) e não apenas no valor de *p*, conforme definido na Seção 7.3.     |
| Violação de Suposições   | Os dados de processo (Tempo de Merge, Densidade de Defeitos) e os dados de código geralmente não seguem uma distribuição normal.                                | **Estratégia:** Priorizar **testes não-paramétricos** (ex.: Mann-Whitney U) e usar **transformação logarítmica** em métricas de tempo.                               |
| Pesca e Taxa de Erro     | Múltiplos testes de hipóteses (12 no total) aumentam a chance de encontrar um resultado falso-positivo por acaso (inflação do Erro Tipo I).                    | **Mitigação:** Interpretar os valores de *p* com cautela e exigir **consistência de resultados entre métricas relacionadas** (ex.: Q1.1 e Q1.3).                      |

### 13.2 Validade interna

Refere-se à **confiança de que o tratamento (CR obrigatório)** foi a principal causa das mudanças nas respostas, controlando causas alternativas.

| Ameaça                           | Descrição do Risco                                                                                                                                     | Estratégia de Mitigação                                                                                                                                                                           |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Maturação (L2)                   | A melhoria das habilidades dos estudantes ao longo do semestre (aprendizado natural) pode ser confundida com o efeito do Code Review.                 | Uso do **Grupo Controle (A)** para estabelecer a **baseline de melhoria natural**.                                                                                                                |
| Seleção (L3)                     | Diferenças pré-existentes (experiência, coesão da equipe) entre o Grupo A e o Grupo B.                                                                | **Estratégia principal:** Randomização das equipes (Seção 9.2) e uso de **ANCOVA** para ajustar os resultados com base nas variáveis de controle (Experiência) coletadas no questionário inicial. |
| Difusão / Imitação do Tratamento | O Grupo Controle (A) adota o Code Review obrigatório por iniciativa própria, após aprender sobre ele no treinamento (10.6) ou observar o Grupo B.     | **Tática:** Monitoramento via API para rastrear a taxa de aprovação formal de PRs no Grupo A. Análise usando abordagem **as-treated** (o que foi feito) se a contaminação for alta.               |
| Instrumentação                   | Mudanças no método de coleta de dados ao longo do tempo (ex.: o linter muda de versão, alterando as métricas de qualidade).                           | **Controle:** Utilizar **versões fixas das ferramentas de análise estática** (P2) e garantir a **estabilidade dos scripts de coleta** via GitHub API.                                             |

### 13.3 Validade de constructo

Refere-se à certeza de que as **métricas escolhidas** representam adequadamente os **conceitos teóricos** subjacentes (Qualidade, Eficiência, Aprendizado).

| Ameaça                                          | Descrição do Risco                                                                                                             | Estratégia de Mitigação                                                                                                                                                     |
|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Explicação Pré-Operacional Inadequada dos Construtos | O conceito de “Qualidade” pode ser mal representado se considerado apenas pela complexidade ciclomática.                    | **Mitigação:** Uso de **triangulação** e **modelagem multimétrica**: Qualidade é medida por (M01, M05, M07, M18). Manutenibilidade (M05) é um índice mais robusto.           |
| Viés de Mono-Operação                          | Confiar em apenas uma fonte de dados (ex.: apenas GitHub API).                                                                | **Estratégia:** Uso de **múltiplas operações** para medir Qualidade: Dados do GitHub API (processo) + Análise estática (código) + Questionários (percepção).               |
| Suposição de Hipótese                          | Participantes tentam adivinhar o resultado esperado (melhoria da qualidade com CR) e ajustam seu comportamento (Efeito Hawthorne L1). | **Mitigação:** Uso de **Grupo Controle (A)**, que também sabe que está sendo observado. Foco no processo (revisão formal) e não apenas no resultado.                        |
| Expectativa do Experimentador                  | O pesquisador pode influenciar sutilmente os resultados ou a classificação manual (ex.: classificação de bugs M09).          | **Controle:** Padronização rigorosa na **classificação de Issues (M09)** e uso de **métricas automatizadas (M01–M11)** para a maioria dos resultados, reduzindo subjetividade. |

### 13.4 Validade externa

Discute a **aplicabilidade dos resultados** a outros contextos, populações e cenários.

| Contexto de Limitação                    | Descrição do Risco                                                                                       | Generalização e Limitação                                                                                                     |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Interação da Seleção e do Tratamento    | Os resultados obtidos com desenvolvedores juniores (população selecionada) podem não se aplicar a sêniores. | **Limitação:** Achados mais fortes para **equipes iniciantes/juniores** e contextos de aprendizado.                           |
| Interação da Situação e do Tratamento   | O experimento ocorre em contexto didático (baixa criticidade), não em ambiente de produção real.         | **Limitação:** Resultados podem não se estender a projetos de **alta criticidade** ou com forte **pressão comercial**.        |
| Interação da História e do Tratamento   | Os resultados podem ser específicos do ano acadêmico/currículo atual.                                   | **Generalização:** Aplica-se a ambientes que usam **Git Flow, Pull Request e metodologias ágeis** em projetos de médio porte. |

---

### 13.5 Resumo das principais ameaças e estratégias de mitigação

A tabela a seguir consolida as **ameaças mais críticas** e as **ações primárias de controle**.

| Ameaça Crítica                 | Tipo de Validade Afetada | Estratégia Principal de Mitigação                                                                                 |
|--------------------------------|---------------------------|--------------------------------------------------------------------------------------------------------------------|
| Baixo Poder Estatístico        | Conclusão                | Relatório do **tamanho do efeito** e da **relevância prática** (Seção 7.3).                                      |
| Seleção / Desbalanceamento     | Interna                  | **Randomização das equipes** e uso de **ANCOVA** para controle da Experiência.                                   |
| Maturação                      | Interna                  | Uso do **Grupo Controle** como baseline para melhoria natural (L2).                                              |
| Difusão do Tratamento (Contaminação) | Interna          | Monitoramento **as-treated** (análise do que foi realmente revisado).                                            |
| Ambiguidade de Construto       | Construto                | **Triangulação** entre métricas de código (M05) e dados de percepção (M18).                                      |
| População Júnior               | Externa                  | Qualificação dos resultados para **equipes de baixa maturidade** (desenvolvedores juniores e contextos didáticos). |

---

## 14. Ética, privacidade e conformidade

### 14.1 Questões éticas (uso de sujeitos, incentivos, etc.)

O experimento, por envolver estudantes em um contexto de avaliação acadêmica, apresenta questões éticas que exigem tratamento rigoroso. A principal preocupação é a **pressão indevida para participar**.

Será garantido que:

- A decisão do estudante em **não participar** ou em **se retirar a qualquer momento** **não afetará**:
  - sua **nota** na disciplina; nem
  - seu **relacionamento** com professores e orientadores.

Outra questão crítica é a **confusão de papéis**:

- O **Pesquisador Principal** **não será** o professor avaliador direto da disciplina, evitando que os estudantes sintam que os dados da pesquisa serão usados para fins de **avaliação acadêmica**.

Sobre incentivos:

- Não serão oferecidos **incentivos financeiros diretos**.
- O benefício será focado no **valor educacional** do workshop de Code Review e no **aprendizado prático** de um processo de desenvolvimento maduro.

Risco de sobrecarga:

- O risco de **sobrecarga de trabalho (R5)**, embora inerente ao Grupo B, será **mitigado pelo monitoramento** da **Percepção de Sobrecarga (M19)**.


### 14.2 Consentimento informado

Os participantes serão informados de forma **detalhada e transparente** por meio do **Termo de Consentimento Livre e Esclarecido (TCLE)**.

- **Informações Essenciais:**  
  O TCLE cobrirá explicitamente:
  - os **objetivos** (comparar Code Review obrigatório vs. opcional);
  - os **procedimentos** (uso da Branch Protection Rule no Grupo B);
  - os **riscos** (mínimos, principalmente sobrecarga de tempo); e
  - os **benefícios** (aprendizado de *soft skills* e *hard skills*).

- **Voluntariedade e Retirada:**  
  Será enfatizado que:
  - a participação é **voluntária**; e
  - o participante tem o **direito incondicional** de se retirar do estudo a qualquer momento,  
    - sem necessidade de justificativa;  
    - sem qualquer penalidade.

- **Registro do Consentimento:**  
  - O consentimento será registrado **digitalmente** (por exemplo, via formulário eletrônico seguro da IES).
  - A coleta de dados **só começará** após o registro do TCLE (**P1**).


### 14.3 Privacidade e proteção de dados

A pesquisa adotará o princípio da **pseudonimização** para proteger a identidade dos participantes.

**Dados Coletados e Tratamento:**

- **Identificação Pessoal (PII):**  
  - Nomes e e-mails dos participantes (coletados para o TCLE e vínculo com o GitHub) serão armazenados em um **repositório separado e criptografado**.

- **Dados de Percepção (M17–M20):**  
  - Serão coletados de forma **anônima** ou vinculados apenas ao **ID da equipe/participante**,  
    sem ligação direta com a identidade no momento da análise.

- **Dados Técnicos (PRs / Métricas):**  
  - Commits, métricas de código (M01–M16) e comentários serão vinculados a um **ID alfanumérico (pseudônimo)**,  
    garantindo que os resultados publicados **não exponham o código ou o desempenho individual** a terceiros.

- **Proteção e Acesso:**  
  - O acesso aos **dados brutos** e à **chave de pseudonimização** será restrito ao:
    - Pesquisador Principal; e
    - Orientador.  
  - Todos os dados serão armazenados em **servidores seguros da IES (P2)**.

- **Tempo de Retenção:**  
  - Os dados brutos e as chaves de pseudonimização serão mantidos por um período máximo de **5 anos** após a publicação do trabalho (conforme diretrizes do CEP).  
  - Após esse período, serão **permanentemente destruídos**.


### 14.4 Aprovações necessárias (comitê de ética, jurídico, DPO, etc.)

O experimento está condicionado à obtenção de **aprovações formais** de diversos órgãos:

- **Comitê de Ética em Pesquisa (CEP) da PUC Minas:**  
  - Aprovação **obrigatória** para qualquer pesquisa envolvendo seres humanos (**P1**).  
  - O protocolo completo deve ser submetido ao CEP para garantir conformidade com as normas éticas.

- **Coordenação do Curso / Departamento:**  
  - Aprovação institucional para utilizar:
    - as **turmas**; e
    - os **repositórios acadêmicos**  
    como ambiente para a pesquisa.

- **Orientador(a):**  
  - Aprovação **metodológica e científica** do Plano de Experimento,  
    endossando o **rigor da pesquisa**.

---

## 15. Recursos, infraestrutura e orçamento

### 15.1 Recursos humanos e papéis

Os recursos humanos envolvidos no experimento têm papéis definidos para garantir a execução metodológica, a coleta de dados e a supervisão.

**Responsável Principal (PI / Dono do Experimento)**  
- **Papel:** Investigador principal, responsável pela gestão de todo o ciclo de vida do experimento.  
- **Responsabilidades:**
  - Desenho metodológico final.
  - Randomização das equipes.
  - Configuração inicial dos repositórios.
  - Coleta de dados automatizada (scripts).
  - Classificação manual de dados (ex.: severidade de bugs).
  - Análise estatística dos resultados.
  - Redação do TCC.

**Orientador(a) do TCC**  
- **Papel:** Supervisão metodológica e científica.  
- **Responsabilidades:**
  - Validação do Plano de Experimento.
  - Apoio na resolução de dilemas éticos/metodológicos.
  - Acompanhamento da análise estatística.
  - Garantia da qualidade científica da pesquisa.

**Professores das Disciplinas (Facilitadores)**  
- **Papel:** Suporte logístico e institucional.  
- **Responsabilidades:**
  - Facilitar o acesso às turmas elegíveis.
  - Apoiar a comunicação com os estudantes.
  - Garantir que o experimento não interfira no cronograma de avaliação da disciplina.

### 15.2 Infraestrutura técnica necessária

A infraestrutura é predominantemente baseada em ferramentas **open source** e na plataforma de colaboração já utilizada (**R3: Restrição Orçamentária**).

- **Plataforma de Colaboração e Controle de Versão: GitHub**  
  - **Função:** Repositórios de código, gestão dos Pull Requests (PRs), configuração das **Branch Protection Rules** (fator de tratamento) e fonte principal para a extração de métricas de processo e interação (M11–M16).

- **Ferramentas de Análise Estática de Código:**  
  - *SonarQube Community Edition, ESLint/Pylint/Checkstyle (dependendo da linguagem)*  
  - **Função:** Medição objetiva da **qualidade do código** (M01, M05) e identificação de **defeitos/vulnerabilidades** (M03, M04, M10).

- **Ambiente de Coleta e Processamento:**  
  - *Servidor/Máquina Virtual ou ambiente cloud gratuito (se aplicável)*  
  - **Função:**  
    - Hospedagem do SonarQube (se necessário).  
    - Execução dos scripts de coleta de dados (web scraping ou API).  
    - Armazenamento dos dados brutos e pseudonimizados.

- **Linguagem/API: Python e GitHub API**  
  - **Função:** Desenvolvimento dos scripts para a **coleta automatizada** de metadados dos PRs.


### 15.3 Materiais e insumos

Os materiais são majoritariamente **digitais**:

- **Documentação Ética e Legal:**
  - Termo de Consentimento Livre e Esclarecido (TCLE) – formulário digital para assinatura.
  - Protocolo de Pesquisa – o próprio Plano de Experimento.

- **Instrumentos de Medição:**
  - Questionário Inicial (Google Forms ou plataforma similar).
  - Questionário Pós-Experimento (Google Forms ou plataforma similar).

- **Material de Treinamento:**
  - Slides e material de apoio para o **workshop de Code Review** (Seção 10.6).


### 15.4 Orçamento e custos estimados

O orçamento é classificado como **baixo**, dado o contexto acadêmico e o uso de **software open source (R3)**.

| Categoria de Custo          | Estimativa de Custo            | Fonte de Financiamento / Observação                                                                                 |
|----------------------------|---------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Recursos Humanos           | Horas do Investigador Principal | Não remunerado (trabalho de TCC).                                                                                   |
| Infraestrutura / Licenças  | R$ 0,00                         | Uso de ferramentas gratuitas (open source: GitHub, SonarQube Community, Python) e recursos de infraestrutura da IES. |
| Comunicação / Disseminação | Baixo                           | Custos limitados à impressão da monografia e taxas de publicação/conferências (se aplicável após o experimento).     |
| **Total Estimado**         | **Mínimo**                      | Financiado por recursos próprios do estudante / projeto de TCC.                                                     |

O experimento será financiado inteiramente por **recursos próprios do Investigador Principal** e por **recursos de infraestrutura institucional** (acesso à internet, laboratórios de informática, se necessário).

---

## 16. Cronograma, marcos e riscos operacionais

### 16.1 Macrocronograma (até o início da execução)

O cronograma operacional está rigidamente limitado ao **ciclo acadêmico de 16 semanas (fevereiro a junho de 2026)**. As datas-chave antes e durante a execução são:

| Fase        | Período Estimado        | Marcos                                                                                                                | Duração    |
|------------|--------------------------|-----------------------------------------------------------------------------------------------------------------------|-----------|
| Planejamento | Nov/2025 – Dez/2025    | Plano de Experimento (v2.0) concluído e aprovado pelo Orientador.                                                    | 4 semanas |
| Ética e Piloto | Dez/2025 – Jan/2026 | Submissão e aprovação do CEP (P1). Teste piloto (1–2 semanas) concluído.                                             | 6 semanas |
| Preparação | Fev/2026 (início do semestre) | Recrutamento / TCLE coletado. Randomização das equipes (Seção 9.2). Configuração de repositórios (Branch Protection, P2). | 2 semanas |
| Execução   | Fev/2026 – Jun/2026     | Início da coleta contínua de dados (a partir da 3ª semana da disciplina).                                            | 14 semanas |


### 16.2 Dependências entre atividades

As atividades do experimento seguem um **fluxo sequencial**, em que o início de uma depende da conclusão de outra.

| Atividade Dependente                      | Dependência Obrigatória        | Justificativa                                                                                                      |
|-------------------------------------------|--------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Recrutamento e Coleta do TCLE            | Aprovação do CEP (P1)          | Essencial por razões éticas. O TCLE deve ser aprovado antes de qualquer interação com o participante.              |
| Randomização das Equipes (Seção 9.2)     | Coleta de Dados do Questionário Inicial | Os dados de experiência (variáveis de controle) são necessários para verificar o balanceamento da randomização.    |
| Configuração do Branch Protection (Grupo B) | Randomização concluída       | A regra só pode ser aplicada após a equipe ser formalmente alocada ao grupo experimental.                         |
| Treinamento e Workshop (Seção 10.6)      | Coleta do TCLE                 | Os participantes só podem receber instruções detalhadas do protocolo após formalizarem o consentimento.           |
| Início da Coleta Contínua                | Configuração final dos repositórios (P2) | As ferramentas de análise estática e os scripts da API devem estar operacionais antes que o desenvolvimento comece.|


### 16.3 Riscos operacionais e plano de contingência

Os riscos operacionais estão ligados principalmente a **restrições logísticas (R1, R2)** e **técnicas (R3, R4)**.

| Risco Operacional                        | Descrição do Risco                                                                                                                                          | Plano de Contingência (Ações)                                                                                                                                                                                                   |
|-----------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Quebra de Protocolo (R4)               | Equipes do Grupo B encontram bypass para a Branch Protection e fazem merge sem revisão, ou o processo é feito “pro forma” (R1).                              | **Técnica:** Monitoramento semanal do status de merge via API. **Metodológica:** Aplicar análise **as-treated** (analisar PRs do Grupo B que realmente receberam revisão e PRs do Grupo A que não receberam).                    |
| Baixo Volume de PRs (R2 / Logístico)   | O throughput das equipes é menor que o esperado (ex.: \< 60 PRs no total), comprometendo o poder estatístico.                                               | **Recurso:** Focar a análise em **tamanho do efeito** (Cohen's d) em vez de apenas no valor de *p*. **Metodológica:** Se a diferença for grande, buscar **replicação do estudo** em semestre futuro para aumentar o *N*.        |
| Atraso no Cronograma (R1 / Temporal)   | A disciplina atrasa a entrega do projeto ou a fase de desenvolvimento é encurtada.                                                                           | **Ação:** Reajustar o período de coleta de dados, priorizando as métricas mais críticas (M07, M11). **Escopo:** Se necessário, negociar com a coordenação um **grace period** para rastreamento de bugs pós-entrega (M07, M08). |
| Falha na Coleta Automatizada (R3 / Técnico) | O GitHub API ou o SonarQube apresenta instabilidade ou falha nos scripts de extração.                                                                      | **Backup:** Planejar **coleta manual parcial** para as métricas críticas (M11 – Tempo de Merge) e usar análise estática em **localhost** como alternativa se o servidor principal falhar.                                       |


---


## 17. Governança do experimento

### 17.1 Papéis e responsabilidades formais

O fluxo de responsabilidade é claro, assegurando que decisões críticas e execução sejam controladas.

| Papel Formal                         | Responsabilidade Principal                                                                                                      | Fluxo de Responsabilidade                                                                                                  |
|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| Dono / Investigador Principal (PI)  | Estudante                                                                                                                       | **DECIDE** sobre a execução operacional; **EXECUTA** todas as atividades de coleta e análise; **INFORMA** o Orientador.   |
| Aprovador Metodológico / Científico | Orientador(a) do TCC                                                                                                            | **DECIDE / REVISA** alterações no desenho e na análise estatística; **REVISA** e aprova os *milestones*.                  |
| Unidade Executora                   | Participantes (alunos)                                                                                                          | **EXECUTAM** o processo de desenvolvimento e Code Review conforme o grupo alocado; **INFORMAM** o pesquisador via logs e questionários. |
| Aprovador Ético                     | Comitê de Ética em Pesquisa (CEP)                                                                                               | **APROVA** o protocolo ético (requerido antes da execução).                                                               |


### 17.2 Ritos de acompanhamento pré-execução

Os checkpoints visam garantir que o experimento esteja pronto para começar com rigor metodológico e ético.

**Reuniões de Revisão do Plano (com Orientador)**  
- **Frequência:** Semanal, durante a fase de planejamento (Novembro / Dezembro de 2025).  
- **Participantes:** PI e Orientador.  
- **Foco:** Refinar as Seções 10 a 13 (Amostragem, Instrumentação, Validade) e preparar a submissão ao CEP.

**Checkpoint Ético e Institucional**  
- **Frequência:** Única, após a conclusão do Plano (Dezembro/2025 – Janeiro/2026).  
- **Participantes:** PI, Orientador e CEP.  
- **Foco:** Obter a **Aprovação Formal do CEP (P1)**.

**Revisão Final da Prontidão Operacional (Piloto)**  
- **Frequência:** Única, após o piloto e antes do início da Semana 3 da disciplina.  
- **Participantes:** PI e Orientador.  
- **Foco:** Garantir o *checklist* da Seção 20 (Branch Protection aplicada, scripts de coleta funcionando) e **aprovar o início da execução**.


### 17.3 Processo de controle de mudanças no plano

Qualquer alteração no desenho experimental que possa afetar a **Validade Interna/Externa** ou as **condições dos participantes** (Seção 13) deve seguir um processo formal:

1. **Proposição**  
   - O PI propõe a mudança necessária  
     - Ex.: ajustar a métrica M04, modificar o tempo de merge analisado devido a outliers, etc.

2. **Análise e Impacto**  
   - O PI e o Orientador analisam:
     - o impacto da mudança nas hipóteses (H1);  
     - as implicações na Validade (Seção 13).

3. **Aprovação**
   - **Mudanças metodológicas (desenho / análise):**  
     - Requerem **aprovação formal do Orientador**.  
   - **Mudanças éticas (risco / TCLE):**  
     - Requerem **reavaliação e aprovação do CEP**.

4. **Registro**
   - Toda mudança aprovada deve ser registrada no **Histórico de Revisão (Seção 1.3)** do Plano de Experimento, garantindo:
     - **rastreabilidade**,  
     - **transparência** das modificações ao longo do tempo.


---

## 18. Plano de documentação e reprodutibilidade

### 18.1 Repositórios e convenções de nomeação

O armazenamento e a organização dos artefatos serão realizados em **repositórios controlados**, garantindo segurança e rastreabilidade.

- **Repositório Principal (GitHub privado)**  
  - **Função:** Hub de controle do experimento, acessível apenas pelo Pesquisador e pelo Orientador.  
  - **Conteúdo:**  
    - Plano de Experimento  
    - Scripts de Coleta  
    - Scripts de Análise (R/Python)  
    - Arquivos de configuração (linters, Branch Protection)  
    - Data set final pseudonimizado

- **Repositório de Dados Sensíveis (armazenamento criptografado da IES)**  
  - **Função:** Local seguro, separado do código, para armazenar:  
    - Chave de pseudonimização  
    - TCLE (Termos de Consentimento) assinados  
  - **Conformidade:** Em alinhamento com as exigências do CEP.


### 18.2 Templates e artefatos padrão

Todos os modelos e instrumentos serão armazenados em uma pasta dedicada (`/Instrumentos`) no Repositório Principal.

| Template / Artefato      | Descrição                                                         | Uso Principal                                                        |
|--------------------------|-------------------------------------------------------------------|----------------------------------------------------------------------|
| Questionário Inicial     | Coleta dados de experiência e variáveis de controle (Seção 8.6). | Formulário digital (Google Forms).                                  |
| Questionário Pós-Experimento | Coleta dados de percepção subjetiva (M17 a M20).           | Formulário digital (Google Forms).                                  |
| Template de PR           | Modelo padronizado para submissão de Pull Requests pelas equipes.| Garante que cada PR vincule a issue correta para rastreamento (M07).|
| Guia de Regras de Codificação | Padrões de estilo e qualidade exigidos (P3).              | Material de suporte para o treinamento (Seção 10.6) e revisões do Grupo B. |
| Template TCLE            | Documento ético de consentimento informado.                       | Registro do consentimento (P1).                                     |


### 18.3 Plano de empacotamento para replicação futura

A **reprodutibilidade** é essencial para a ciência. Ao final do TCC, será criado um **Pacote de Replicação**, contendo os elementos necessários para que outro pesquisador possa replicar ou estender o experimento.

O Pacote de Replicação incluirá:

- **Documentação metodológica:**  
  - Plano de Experimento final.  
  - Documentação completa dos critérios de inclusão e exclusão (Seção 10).

- **Scripts de Coleta:**  
  - Código-fonte dos scripts Python/API, com documentação detalhada:  
    - bibliotecas utilizadas;  
    - instruções para configuração de acesso (sem incluir chaves de API).

- **Scripts de Análise:**  
  - Scripts estatísticos (R ou Python) utilizados para responder às hipóteses (H1),  
    permitindo auditoria e repetição do processo de análise.

- **Data set final:**  
  - Arquivo de dados pseudonimizado (CSV ou JSON) utilizado na análise estatística, contendo:  
    - métricas M01–M21;  
    - variáveis de controle (Experiência, Tamanho da Equipe).

- **Instruções de setup:**  
  - Arquivo `README` detalhando como configurar as ferramentas open source:  
    - setup do SonarQube;  
    - linters;  
    - demais dependências,  
    de modo que o ambiente de medição possa ser recriado.

---

## 19. Plano de comunicação

### 19.1 Públicos e mensagens-chave pré-execução

| Público                  | Objetivo da Comunicação                                             | Mensagens-Chave Essenciais                                                                                                                                                                               |
|--------------------------|---------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Participantes (Alunos)   | Engajamento, garantia de voluntariedade (P1), esclarecimento do papel. | “Sua participação é voluntária e não afetará sua nota. O Code Review obrigatório é uma variável de pesquisa para estudar a qualidade do código. Seu papel é atuar como desenvolvedor júnior.”             |
| Orientador(a) do TCC     | Alinhamento metodológico, aprovação e suporte.                     | “O Plano de Experimento (v2.0) está finalizado. Iremos proceder com a submissão ao CEP e a configuração dos repositórios conforme o cronograma (Seção 16).”                                               |
| Professores das Disciplinas | Coordenação logística, suporte ao protocolo (R4).              | “O experimento utilizará a regra de Branch Protection em X repositórios. Solicitamos apoio para reforçar o uso do fluxo de Pull Request e para evitar que o Code Review seja um fator de estresse para os alunos.” |
| Comitê de Ética (CEP)    | Aprovação institucional.                                            | “O protocolo garante a anonimização/pseudonimização dos dados e a voluntariedade da participação. Buscamos a aprovação para iniciar a coleta conforme P1.”                                                |
| Coordenação do Curso     | Conscientização estratégica, potencial impacto curricular.         | “Os resultados do estudo fornecerão evidências sobre a eficácia de práticas de Code Review no currículo e na formação profissional dos alunos.”                                                           |


### 19.2 Canais e frequência de comunicação

| Público                  | Canal de Comunicação                                               | Frequência                                                                                                  |
|--------------------------|---------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| Participantes (Alunos)   | Apresentação em aula; e-mail; avisos na plataforma da disciplina (Teams). | No início (para TCLE e treinamento) e em pontos obrigatórios (Seção 19.3).                                 |
| Orientador(a) do TCC     | Reuniões formais (online ou presenciais); e-mail.                  | Semanal (fase de planejamento e análise); mensal (fase de execução).                                       |
| Professores / Coordenação| E-mail formal; reunião de alinhamento pré-execução.                | No início e no final da execução, e em pontos obrigatórios (Seção 19.3).                                   |


### 19.3 Pontos de comunicação obrigatórios

A comunicação formal é mandatória nos seguintes eventos, garantindo **rastreabilidade** e **transparência** (Governança):

1. **Aprovação do Plano:**  
   - Comunicação ao Orientador, Professores e Coordenação (marcando o marco da Seção 16.1).

2. **Aprovação Ética (P1):**  
   - Comunicação formal a todos os stakeholders antes do recrutamento (libera a execução).

3. **Início da Coleta de Dados:**  
   - Notificação aos Professores e Participantes (marco de início definido na Seção 16.1).

4. **Mudanças Relevantes no Protocolo:**  
   - Qualquer alteração que afete:
     - o risco,  
     - o escopo (ex.: mudança de métricas), ou  
     - o cronograma,  
   deve ser comunicada imediatamente após a aprovação do Orientador (conforme Seção 17.3).

5. **Decisão de Parada Antecipada (Seção 6.3):**  
   - Comunicação imediata e formal a todos os stakeholders envolvidos.

6. **Resultados Finais:**  
   - Apresentação formal ao Orientador, Professores e Coordenação do Curso, após a análise de dados.

---

## 20. Critérios de prontidão para execução (Definition of Ready)

### 20.1 Checklist de prontidão (itens que devem estar completos)

Para que o Investigador Principal (PI) receba autorização para iniciar a execução do experimento, **todos os itens abaixo devem ser verificados e concluídos**, garantindo que as premissas (P1, P2, P3) e as restrições (R1–R4) foram mitigadas.

**I. Governança e Ética**

- **Aprovação do Plano de Experimento:**  
  - O Plano (versão 2.0) está finalizado e formalmente aprovado pelo Orientador.
- **Aprovação do CEP (P1):**  
  - O protocolo de pesquisa foi submetido e recebeu a **Aprovação Formal** do Comitê de Ética em Pesquisa (CEP).
- **Instrumentos finalizados:**  
  - O TCLE e os questionários (Inicial e Pós-Experimento) estão prontos para uso e validados.
- **Treinamento concluído:**  
  - O material do workshop de Code Review está pronto para ser ministrado aos participantes (Seção 10.6).

**II. Logística e Amostragem**

- **Identificação das Turmas:**  
  - Turmas e disciplinas elegíveis foram confirmadas com os Professores / Coordenação.
- **Recrutamento imediato:**  
  - O convite aos participantes foi realizado e o processo de coleta do TCLE está ativo.
- **Cronograma alinhado (R1):**  
  - O cronograma do experimento está totalmente alinhado com o calendário do semestre letivo (fevereiro–junho de 2026).

**III. Infraestrutura e Tecnologia (P2, R3)**

- **Scripts validados:**  
  - Scripts de coleta (GitHub API) e de análise (conexão com SonarQube / linters) foram testados com sucesso durante o piloto.
- **Regras configuradas:**  
  - A Branch Protection Rule foi configurada nos repositórios de teste e está pronta para ser aplicada no Grupo B (experimental).
- **Ambiente de armazenamento:**  
  - Ambiente seguro para armazenamento dos dados pseudonimizados e dos documentos éticos está configurado e acessível (P2).


### 20.2 Aprovações finais para iniciar a operação

O início da execução do experimento (marcando o começo da **Semana 3 da disciplina**) deve ser autorizado formalmente pelo responsável metodológico.

- **Aprovação metodológica:**  
  - O(a) Orientador(a) do TCC é o principal responsável por conceder o **“OK final”** para iniciar a execução.

- **Registro do aceite:**  
  - O aceite será registrado por meio de um **e-mail formal** do Orientador para o PI (Marcella Costa), confirmando que todos os itens do Checklist 20.1 foram concluídos.  
  - Este e-mail será anexado ao **Histórico de Revisão do Plano**.
