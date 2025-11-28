# Plano de Experimento – Scoping e Planejamento

## 1. Identificação básica

### 1.1 Título do experimento
Impacto de Code Review obrigatório na qualidade de PRs em projetos acadêmicos

### 1.2 ID / código
EXP-ACAD-2025

### 1.3 Versão do documento e histórico de revisão

| Versão | Data       | Alterações                                                  | Autor          |
|--------|------------|-------------------------------------------------------------|----------------|
| v1.0   | 21/11/2025 | Criação Inicial do Documento (Identificação Básica, Contexto e Problema) | Marcella Costa |

### 1.4 Datas (criação, última atualização)
- **Criação:** 21/11/2025  
- **Última atualização:** 28/11/2025

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
Em projetos acadêmicos, é comum que Pull Requests sejam integrados rapidamente sem revisão formal, especialmente por pressão de prazos e falta de maturidade no processo. Isso pode resultar na inclusão de defeitos, inconsistências de padrão, decisões arquiteturais inadequadas e maior retrabalho após o merge. Ao mesmo tempo, exigir Code Review obrigatório pode aumentar o tempo de integração e gerar custo adicional de organização.

**Oportunidade:** avaliar empiricamente se a obrigatoriedade de Code Review melhora a qualidade dos PRs em projetos acadêmicos e se o benefício supera o custo em tempo e esforço. A hipótese é que a obrigatoriedade eleva a Qualidade do Código (menos defeitos e maior adesão a padrões) e, potencialmente, a Eficiência do Processo (melhor comunicação e aprendizado).

### 2.2 Contexto organizacional e técnico
O experimento será conduzido em ambiente acadêmico universitário, especificamente com equipes compostas por estudantes de Engenharia de Software que trabalham colaborativamente em repositórios hospedados na plataforma GitHub. 

- **Equipe:** grupos de 3–6 alunos desenvolvendo software em ciclos semanais/sprints.  
- **Domínio:** projetos acadêmicos de desenvolvimento de software em linguagem comum (por exemplo, Python, Java, JavaScript).  

**Tecnologias e Ferramentas:**
- Controle de Versão: Git (padrão).  
- Plataforma de Colaboração: GitHub (essencial para configurar a regra de Code Review obrigatório via *branch protection rules* e para extrair métricas de PRs, como comentários e tempo de merge).  
- Processo de desenvolvimento: integração via PRs, com divisão de tarefas, commits frequentes e entregas incrementais.  
- Ferramentas relevantes: Pull Requests, Reviews, Branch Protection Rules, Issues e Actions do GitHub.

### 2.3 Trabalhos e evidências prévias (internos e externos)
Evidências internas coletadas através de observação sistemática no curso de Engenharia de Software revelam que, em várias disciplinas e projetos desenvolvidos, os Pull Requests são frequentemente aceitos e integrados sem passar por um processo sistemático de revisão. Como resultado desta prática, bugs e defeitos são detectados apenas nas fases finais de testes ou mesmo após a entrega do projeto, gerando retrabalho significativo e comprometendo a qualidade final do software produzido.

No âmbito externo, tanto a literatura científica quanto a prática na indústria de software estabelecem o Code Review como uma prática consolidada na engenharia de software moderna. Esta prática tem demonstrado efetividade na redução de defeitos, padronização de código, compartilhamento de conhecimento entre membros da equipe e prevenção de regressões no sistema. Resultados empíricos de diversos estudos apontam para um impacto positivo significativo na qualidade do software, embora estes benefícios sejam dependentes de fatores contextuais, como a experiência do time, o volume de mudanças em cada revisão e a cultura organizacional estabelecida.

Entre os trabalhos científicos relevantes, destaca-se o estudo de McIntosh et al. de 2016, intitulado "The impact of code review coverage and code review participation on software quality", que analisou projetos de código aberto como Qt, VTK e ITK, demonstrando correlação entre Code Review e redução de 14% a 28% nos bugs pós-release. Bacchelli e Bird, em 2013, publicaram "Expectations, outcomes, and challenges of modern code review", identificando que os principais benefícios reportados são encontrar defeitos, representando 14% dos casos, e transferência de conhecimento, correspondendo a 41% dos benefícios percebidos. No contexto pedagógico específico, Hundhausen et al., em 2013, através do trabalho "Talking about code: Integrating pedagogical code reviews into early computing courses", demonstraram que Code Review pedagógico melhora significativamente a compreensão de código por parte dos estudantes em cursos iniciais de computação.

### 2.4 Referencial teórico e empírico essencial
O referencial teórico que fundamenta este experimento baseia-se em três conceitos centrais da Engenharia de Software moderna:

1. **Code Review (Revisão de Código):** processo de inspeção colaborativa do código-fonte realizado por membros da equipe antes que as mudanças sejam integradas ao branch principal do repositório. Este processo visa identificar defeitos, garantir aderência a padrões estabelecidos, promover compartilhamento de conhecimento e melhorar aspectos de design e arquitetura do software.

2. **Pull Request (PR):** proposta formal de mudança em repositórios Git, seguindo o fluxo de criação de um branch com as alterações desejadas, submissão para revisão por outros membros da equipe, processo de aprovação baseado em critérios estabelecidos e, finalmente, integração ao branch principal através do merge. Os Pull Requests facilitam a discussão assíncrona sobre as mudanças propostas, permitem revisão sistemática do código e são centrais no workflow de equipes de desenvolvimento modernas.

3. **Qualidade de Software:** neste estudo é fundamentado no modelo internacional ISO/IEC 25010. Este modelo estabelece dimensões de qualidade que incluem funcionalidade, abrangendo corretude e completude das funcionalidades implementadas; confiabilidade, relacionada à maturidade do sistema, disponibilidade e tolerância a falhas; segurança, contemplando confidencialidade e integridade dos dados; manutenibilidade, que engloba modularidade, reusabilidade e analisabilidade do código; e eficiência de desempenho do sistema. Para os propósitos deste experimento específico, o foco concentra-se em três dimensões principais: manutenibilidade, avaliada através de métricas de complexidade e duplicação de código; confiabilidade, medida através da quantidade de bugs detectados; e segurança, analisada através da identificação de vulnerabilidades no código produzido.

---

## 3. Objetivos e questões (Goal / Question / Metric)

### 3.1 Objetivo geral (Goal template)
Analisar Pull Requests (PRs) de projetos acadêmicos de Engenharia de Software com o propósito de comparar a qualidade e o custo de integração do ponto de vista de desenvolvedores e revisores (alunos) no contexto de equipes acadêmicas que utilizam GitHub para desenvolvimento colaborativo, contrastando PRs com Code Review obrigatórios vs. PRs sem obrigatoriedade de review.

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
- **Tipo de Organização:** Instituição de Ensino Superior (IES) em nível de Graduação.  
- **Tipo de Projeto:** projeto de software de médio porte e complexidade (por exemplo, sistema web ou aplicativo móvel), com foco em desenvolvimento de funcionalidades e trabalho em equipe, com duração típica de um semestre acadêmico.  
- **Criticidade:** Baixa – o projeto é didático; falhas afetam nota, não causam danos financeiros ou operacionais a clientes externos.  
- **Perfil de Experiência dos Participantes:** desenvolvedores juniores (estudantes com 1–2 anos de programação, familiaridade básica com Git e PRs no GitHub, pouca experiência formal em Code Review ou TDD).

### 4.3 Premissas
- A alocação aleatória das equipes para os Grupos A e B resultará em grupos de experiência e habilidade comparáveis.  
- A plataforma GitHub e suas APIs estarão estáveis e acessíveis durante todo o experimento.  
- As regras de desenvolvimento (convenções de codificação e padrões) serão formalmente documentadas e conhecidas por ambos os grupos antes do início.  
- O treinamento inicial de 1–2 horas sobre Code Review é suficiente para garantir compreensão adequada da tarefa pelos revisores do Grupo B.

**P1 – Aprovação ética e consentimento voluntário:**  
O Comitê de Ética em Pesquisa (CEP) da PUC Minas aprovará o protocolo de pesquisa e todos os participantes concordarão voluntariamente em participar após serem informados detalhadamente. O TCLE será assinado antes da coleta de dados, garantindo direito de retirada sem penalidades.

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
- **L1 – Efeito Hawthorne:** Participantes sabem que estão sendo observados e que seus dados estão sendo coletados para pesquisa. Este conhecimento pode alterar comportamento, levando a: (a) maior cuidado ao escrever código (independente do Code Review), (b) revisões mais superficiais para "parecer que está fazendo", (c) respostas em questionários influenciadas pelo desejo de "ajudar a pesquisa" ou agradar o pesquisador.
- **L2 – Maturação dos participantes:** Ao longo do semestre, estudantes naturalmente melhoram suas habilidades de programação por exposição contínua, prática deliberada, feedback dos professores e aprendizado com erros. Esta maturação pode ser confundida com o efeito do Code Review, especialmente se o grupo experimental tiver aprendizado acelerado por outros fatores (ex: professores mais envolvidos, projetos mais desafiadores). 
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

### 6.1 Riscos de alto nível (negócio, técnicos, etc.)
- **R1 (Técnico):** baixa adesão ao processo de revisão (review feito “pro forma”).  
- **R2 (Logístico):** volume de PRs inferior ao necessário para análise.  
- **R3 (Técnico):** falhas no ambiente GitHub ou indisponibilidade de métricas.  
- **R4 (Processo):** participantes ignoram o protocolo (merge direto sem review obrigatório).  
- **R5 (Organizacional):** participantes veem o experimento como sobrecarga e não colaboram.

### 6.2 Critérios de sucesso globais (go / no-go)
O experimento será considerado viável e útil se:

- For possível coletar pelo menos **30 PRs analisáveis no total** (mínimo de 15 PRs por grupo).  
- Os participantes aderirem aos protocolos (obrigatoriedade de review, preenchimento de formulários, vinculação de issues).  
- Pelo menos uma métrica de qualidade (por exemplo, bugs, score percebido) indicar melhora com review obrigatório sem custo proibitivo de tempo (aumento de tempo ≤ 25%).

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

- **Grupo A – Sem Code Review obrigatório:** PRs podem ser integrados diretamente à branch principal sem exigência formal de aprovação prévia. A revisão, quando ocorre, depende da iniciativa espontânea dos membros da equipe.  
- **Grupo B – Com Code Review obrigatório:** PRs só podem ser integrados após pelo menos uma aprovação formal de revisão. A branch principal é protegida por regras de *branch protection* no GitHub, forçando a passagem do PR por pelo menos um revisor.

O raciocínio conceitual é:

- A obrigatoriedade de Code Review tende a aumentar a quantidade e a profundidade dos comentários de revisão, gerar mais ciclos de retrabalho pré-merge e forçar autores a preparar PRs mais organizados, legíveis e aderentes a padrões.  
- Esse aumento de inspeção e retrabalho pré-merge é esperado reduzir problemas estruturais (complexidade excessiva, duplicação, *smells*), diminuir a quantidade e a densidade de defeitos pós-merge (especialmente bugs severos) e melhorar indicadores de manutenibilidade e conformidade a padrões.  
- Como efeito colateral, Code Review obrigatório pode aumentar o tempo entre abertura e merge, elevar a carga de trabalho dos revisores e ser percebido como burocrático, ao mesmo tempo em que é visto como mecanismo de aprendizado e melhoria.

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

### 7.3 Nível de significância e considerações de poder
O nível de significância (α) será de **0,05** para todos os testes. Hipóteses nulas serão rejeitadas quando **p < 0,05**. Os testes serão predominantemente bicaudais para acomodar achados exploratórios e inesperados.

O poder estatístico (1 − β) é limitado pelo tamanho amostral planejado: aproximadamente 4–6 equipes, 20–30 participantes e 60–80 PRs no total (30–40 PRs por grupo). Esse tamanho é suficiente para detectar efeitos moderados a grandes (Cohen’s d ≥ 0,5), mas com baixo poder para efeitos pequenos. A dependência dos dados por equipe reduz o “n efetivo”.

Dado o número de testes de hipóteses (12 no total), será considerado o risco de erro Tipo I inflacionado por múltiplas comparações, e os valores de p serão interpretados com cautela, priorizando consistência entre métricas relacionadas. Para mitigar risco de erro Tipo II (falso negativo), serão reportados tamanhos de efeito (Cohen’s d, Cliff’s Delta) e relevância prática das descobertas, além dos p-values.

---

## 8. Variáveis, fatores, tratamentos e objetos de estudo

### 8.1 Objetos de estudo
Os principais objetos de estudo deste experimento são os Pull Requests (PRs) produzidos pelas equipes durante o desenvolvimento dos projetos acadêmicos. Cada PR será tratado como uma unidade de análise, incluindo: o código-fonte modificado (arquivos alterados, funções/métodos novos ou refatorados), o diff entre o branch de origem e a branch principal, os metadados do PR (autor, data de abertura, data de merge, tamanho em linhas adicionadas/removidas), os comentários de revisão associados (quando houver), os eventos de aprovação/reprovação e o histórico de commits vinculados a esse PR.

Além dos PRs em si, serão analisadas as issues de bug relacionadas a esses PRs (especialmente aquelas abertas após o merge), usadas para medir defeitos pós-integração e severidade dos problemas reportados. Para complementar a análise quantitativa, também serão considerados como objetos de estudo os relatórios de análise estática de código (métricas de complexidade, duplicação, code smells, vulnerabilidades) e as respostas aos questionários aplicados aos participantes, que capturam percepções de aprendizado, sobrecarga e qualidade das revisões.

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

| Variável de Confusão          | Como pode distorcer                                        | Estratégia de Mitigação                                              |
|-------------------------------|------------------------------------------------------------|------------------------------------------------------------------------|
| Contaminação entre grupos     | Grupo controle adota Code Review voluntariamente           | Monitoramento semanal via API; separação de turmas; análise *as-treated* |
| Maturação dos participantes   | Estudantes melhoram naturalmente ao longo do semestre      | Grupo controle como baseline; análise de tendência temporal           |
| Efeito Hawthorne              | Participantes alteram comportamento por serem observados   | Não eliminável, mas ambos grupos são igualmente observados           |

---

## 9. Desenho experimental

### 9.1 Tipo de desenho (completamente randomizado, blocos, fatorial, etc.)
O desenho escolhido é um **quasi-experimento de campo** com grupo controle não equivalente, em arranjo **between-subjects** e randomização ao nível de equipe (cluster).

Primeiro, o arranjo between-subjects é necessário porque cada equipe ficará exposta apenas a uma condição ao longo de todo o semestre: ou Code Review obrigatório (Grupo B) ou Code Review opcional/não obrigatório (Grupo A). Se o mesmo grupo passasse pelos dois tratamentos (within-subjects), haveria um efeito de aprendizado irreversível: uma vez que a equipe aprende a revisar código de forma estruturada, é praticamente impossível “desaprender” a prática. Além disso, não existe um período de washout viável em disciplina semestral, e os efeitos de ordem (primeiro A depois B, ou o contrário) seriam confundidores críticos.

Segundo, trata-se de um quasi-experimento porque, embora exista randomização, ela não é feita sobre indivíduos isolados, e sim sobre grupos intactos já formados pela disciplina (equipes de projeto). Há restrições institucionais importantes: as equipes já estão constituídas, horários são fixos, as turmas são pré-estabelecidas. A randomização ocorre no nível da equipe (cluster), o que exige controle estatístico cuidadoso de variáveis preexistentes, como experiência em programação, familiaridade com Git/GitHub, tamanho da equipe e complexidade do projeto.

Por fim, a presença de um grupo controle é essencial para isolar o efeito específico da política de Code Review em relação a outros fatores que também podem influenciar a qualidade do código e o processo (maturação dos estudantes ao longo do semestre, efeito Hawthorne, eventos externos do curso). Sem um grupo controle que trabalhe em condições semelhantes, mas sem a obrigatoriedade de revisão, seria muito mais difícil atribuir qualquer melhoria observada diretamente ao tratamento (Code Review obrigatório).


### 9.2 Randomização e alocação
A randomização será feita no nível das equipes, e não dos indivíduos. Equipes completas de desenvolvimento serão aleatoriamente alocadas ao grupo controle (A) ou ao grupo experimental (B). A unidade de randomização, portanto, é a própria equipe, que será exposta a apenas um dos dois níveis de tratamento: Code Review obrigatório ou Code Review opcional.

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
