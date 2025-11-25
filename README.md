# Plano de Experimento – Scoping e Planejamento

## 1. Identificação básica

### 1.1 Título do experimento
**Impacto de Code Review obrigatório na qualidade de PRs em projetos acadêmicos**

### 1.2 ID / código
**EXP-ACAD-2025**

### 1.3 Versão do documento e histórico de revisão

| Versão | Data       | Alterações                                                                 | Autor          |
|-------:|------------|----------------------------------------------------------------------------|----------------|
| v1.0   | 21/11/2025 | Criação Inicial do Documento (Identificação Básica, Contexto e Problema) | Marcella Costa |

### 1.4 Datas (criação, última atualização)
- **Criação:** 21/11/2025  
- **Última atualização:** 21/11/2025

### 1.5 Autores (nome, área, contato)
- **Marcella Ferreira Chaves Costa** – Engenharia de Software, PUC Minas – marcellafccosta@gmail.com

### 1.6 Responsável principal (PI / dono do experimento)
**Marcella Ferreira Chaves Costa**  
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
- **Domínio:** Projetos acadêmicos de desenvolvimento de software em linguagem comum (e.g., Python, Java, JavaScript).  
- **Tecnologias e Ferramentas:**
  - Controle de Versão: Git (padrão).  
  - Plataforma de Colaboração: GitHub (essencial para configurar a regra de Code Review Obrigatório via branch protection rules e para extrair métricas de PRs, como comentários e tempo de merge).  
  - Processo de desenvolvimento: integração via PRs, com divisão de tarefas, commits frequentes e entregas incrementais.  
  - Ferramentas relevantes: Pull Requests, Reviews, Branch Protection Rules, Issues e Actions do GitHub.

### 2.3 Trabalhos e evidências prévias (internos e externos)
Evidências internas coletadas através de observação sistemática no curso de Engenharia de Software revelam que, em várias disciplinas e projetos desenvolvidos, os Pull Requests são frequentemente aceitos e integrados sem passar por um processo sistemático de revisão. Como resultado desta prática, bugs e defeitos são detectados apenas nas fases finais de testes ou mesmo após a entrega do projeto, gerando retrabalho significativo e comprometendo a qualidade final do software produzido.

No âmbito externo, tanto a literatura científica quanto a prática na indústria de software estabelecem o Code Review como uma prática consolidada na engenharia de software moderna. Esta prática tem demonstrado efetividade na redução de defeitos, padronização de código, compartilhamento de conhecimento entre membros da equipe e prevenção de regressões no sistema. Resultados empíricos de diversos estudos apontam para um impacto positivo significativo na qualidade do software, embora estes benefícios sejam dependentes de fatores contextuais, como a experiência do time, o volume de mudanças em cada revisão e a cultura organizacional estabelecida.

Entre os trabalhos científicos relevantes, destaca-se o estudo de McIntosh et al. de 2016, intitulado *"The impact of code review coverage and code review participation on software quality"*, que analisou projetos de código aberto como Qt, VTK e ITK, demonstrando correlação entre Code Review e redução de 14% a 28% nos bugs pós-release. Bacchelli e Bird, em 2013, publicaram *"Expectations, outcomes, and challenges of modern code review"*, identificando que os principais benefícios reportados são encontrar defeitos, representando 14% dos casos, e transferência de conhecimento, correspondendo a 41% dos benefícios percebidos. No contexto pedagógico específico, Hundhausen et al., em 2013, através do trabalho *"Talking about code: Integrating pedagogical code reviews into early computing courses"*, demonstraram que Code Review pedagógico melhora significativamente a compreensão de código por parte dos estudantes em cursos iniciais de computação.

### 2.4 Referencial teórico e empírico essencial
O referencial teórico que fundamenta este experimento baseia-se em três conceitos centrais da Engenharia de Software moderna.

1. **Code Review (Revisão de Código):** processo de inspeção colaborativa do código-fonte realizado por membros da equipe antes que as mudanças sejam integradas ao branch principal do repositório. Este processo visa identificar defeitos, garantir aderência a padrões estabelecidos, promover compartilhamento de conhecimento e melhorar aspectos de design e arquitetura do software.

2. **Pull Request (PR):** proposta formal de mudança em repositórios Git, seguindo o fluxo de criação de um branch com as alterações desejadas, submissão para revisão por outros membros da equipe, processo de aprovação baseado em critérios estabelecidos e, finalmente, integração ao branch principal através do merge. Os Pull Requests facilitam a discussão assíncrona sobre as mudanças propostas, permitem revisão sistemática do código e são centrais no workflow de equipes de desenvolvimento modernas.

3. **Qualidade de Software:** neste estudo é fundamentado no modelo internacional ISO/IEC 25010. Este modelo estabelece dimensões de qualidade que incluem funcionalidade, abrangendo corretude e completude das funcionalidades implementadas; confiabilidade, relacionada à maturidade do sistema, disponibilidade e tolerância a falhas; segurança, contemplando confidencialidade e integridade dos dados; manutenibilidade, que engloba modularidade, reusabilidade e analisabilidade do código; e eficiência de desempenho do sistema. Para os propósitos deste experimento específico, o foco concentra-se em três dimensões principais: manutenibilidade (métricas de complexidade e duplicação de código), confiabilidade (quantidade de bugs detectados) e segurança (identificação de vulnerabilidades no código produzido).

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

**Relacionadas a O1 (Qualidade do Código):**
- **Q1.1** – Existe diferença significativa na complexidade ciclomática do código submetido via PRs entre os grupos com e sem Code Review obrigatório?  
- **Q1.2** – A obrigatoriedade de Code Review resulta em maior conformidade com padrões de codificação estabelecidos?  
- **Q1.3** – PRs com Code Review obrigatório apresentam melhor manutenibilidade do código medida por índices automatizados?

**Relacionadas a O2 (Densidade de Defeitos):**
- **Q2.1** – A densidade de defeitos detectados após o merge é menor em PRs que passaram por Code Review obrigatório?  
- **Q2.2** – Code Review obrigatório reduz especificamente a ocorrência de bugs críticos e de alta severidade?  
- **Q2.3** – Há diferença na quantidade de vulnerabilidades de segurança introduzidas entre os grupos?

**Relacionadas a O3 (Eficiência do Fluxo):**
- **Q3.1** – Qual o impacto do Code Review obrigatório no tempo decorrido entre abertura e merge dos Pull Requests?  
- **Q3.2** – Qual a carga de trabalho adicional imposta aos revisores em termos de tempo e esforço de revisão?  
- **Q3.3** – O Code Review obrigatório afeta a produtividade geral das equipes medida por throughput de PRs e entregas?

**Relacionadas a O4 (Percepção dos Participantes):**
- **Q4.1** – Os participantes do grupo experimental percebem valor educacional e de aprendizado no processo de Code Review?  
- **Q4.2** – Como os participantes avaliam a relação custo-benefício do Code Review obrigatório em termos de tempo investido versus qualidade obtida?  
- **Q4.3** – Os comentários de revisão são percebidos como construtivos, úteis e respeitosos pelos autores dos PRs?

### 3.4 Métricas associadas (GQM)

**Tabela GQM Completa**

| Objetivo | Pergunta | Métricas Associadas |
|---------|----------|---------------------|
| O1 - Qualidade do Código | Q1.1 - Diferença na complexidade ciclomática? | M01 - Complexidade ciclomática média; M02 - Distribuição de complexidade por função |
| O1 - Qualidade do Código | Q1.2 - Maior conformidade com padrões? | M03 - Taxa de violações de padrão de código; M04 - Número de code smells |
| O1 - Qualidade do Código | Q1.3 - Melhor manutenibilidade? | M05 - Índice de manutenibilidade; M06 - Taxa de duplicação de código |
| O2 - Densidade de Defeitos | Q2.1 - Menor densidade de defeitos? | M07 - Densidade de defeitos pós-merge; M08 - Número absoluto de bugs reportados |
| O2 - Densidade de Defeitos | Q2.2 - Redução de bugs críticos? | M08 - Número absoluto de bugs reportados; M09 - Proporção de bugs críticos/severos |
| O2 - Densidade de Defeitos | Q2.3 - Diferença em vulnerabilidades? | M10 - Vulnerabilidades de segurança detectadas; M07 - Densidade de defeitos pós-merge |
| O3 - Eficiência do Fluxo | Q3.1 - Impacto no tempo de merge? | M11 - Tempo médio até merge do PR; M12 - Tempo de ciclo de feedback |
| O3 - Eficiência do Fluxo | Q3.2 - Carga de trabalho de revisão? | M13 - Número de comentários por PR; M14 - Tempo médio de revisão por PR |
| O3 - Eficiência do Fluxo | Q3.3 - Impacto na produtividade? | M15 - Throughput de PRs por semana; M16 - Tamanho médio dos PRs |
| O4 - Percepção | Q4.1 - Percepção de valor educacional? | M17 - Percepção de aprendizado; M18 - Percepção de melhoria de código |
| O4 - Percepção | Q4.2 - Avaliação custo-benefício? | M19 - Percepção de sobrecarga de trabalho; M18 - Percepção de melhoria de código |
| O4 - Percepção | Q4.3 - Comentários construtivos e úteis? | M20 - Qualidade percebida dos comentários; M21 - Taxa de comentários acionáveis |

**Tabela de Definição de Métricas**

| ID  | Métrica | Descrição | Unidade | Fonte de Dados |
|-----|---------|-----------|---------|----------------|
| M01 | Complexidade ciclomática média | Média da complexidade ciclomática (McCabe) de todas as funções/métodos modificados no PR | valor numérico | SonarQube / Radon / Lizard |
| M02 | Distribuição de complexidade por função | Percentual de funções com complexidade > 10 (considerada alta) | percentual (%) | SonarQube / Radon / Lizard |
| M03 | Taxa de violações de padrão de código | Número de violações de linting e style guide por 1000 linhas de código | violações/1000 LoC | ESLint / Pylint / Checkstyle |
| M04 | Número de code smells | Quantidade absoluta de code smells detectados (código duplicado, métodos longos, acoplamento excessivo) | quantidade absoluta | SonarQube |
| M05 | Índice de manutenibilidade | Score de manutenibilidade do código baseado em complexidade, volume e comentários (0-100, onde > 85 é bom) | índice (0-100) | SonarQube Maintainability Index |
| M06 | Taxa de duplicação de código | Percentual de linhas de código duplicadas no PR | percentual (%) | SonarQube / Copy-Paste Detector |
| M07 | Densidade de defeitos pós-merge | Número de bugs reportados após merge dividido pelo tamanho do PR | defeitos/1000 LoC | Issues GitHub + análise de commits |
| M08 | Número absoluto de bugs reportados | Quantidade total de issues marcadas como "bug" relacionadas ao PR nas 2 semanas seguintes ao merge | quantidade absoluta | GitHub Issues API |
| M09 | Proporção de bugs críticos/severos | Percentual de bugs reportados classificados como críticos ou severos em relação ao total de bugs | percentual (%) | GitHub Issues (labels de severidade) |
| M10 | Vulnerabilidades de segurança detectadas | Número de vulnerabilidades de segurança identificadas por análise estática no código do PR | quantidade absoluta | SonarQube Security / Snyk / Bandit |
| M11 | Tempo médio até merge do PR | Tempo decorrido entre a abertura do PR e seu merge final ao branch principal | horas | GitHub API (created_at - merged_at) |
| M12 | Tempo de ciclo de feedback | Tempo entre solicitação de review e primeiro comentário ou aprovação do revisor | horas | GitHub API (review_requested_at - first_review_at) |
| M13 | Número de comentários por PR | Quantidade média de comentários de revisão (review comments) feitos em cada PR | comentários/PR | GitHub API (review_comments count) |
| M14 | Tempo médio de revisão por PR | Tempo total estimado gasto por revisores em cada PR (baseado em timestamps de atividade) | minutos/PR | GitHub API + análise de eventos |
| M15 | Throughput de PRs por semana | Número de Pull Requests completados (merged) por semana de trabalho | PRs/semana | GitHub API (agregação temporal) |
| M16 | Tamanho médio dos PRs | Média de linhas adicionadas + removidas por Pull Request | linhas de código (LoC) | GitHub API (additions + deletions) |
| M17 | Percepção de aprendizado | Grau de concordância com afirmação "Code Review contribuiu para meu aprendizado" | escala Likert (1-5) | Questionário pós-experimento |
| M18 | Percepção de melhoria de código | Grau de concordância com "Code Review melhorou a qualidade do código do projeto" | escala Likert (1-5) | Questionário pós-experimento |
| M19 | Percepção de sobrecarga de trabalho | Grau de concordância com "Code Review representou sobrecarga excessiva de trabalho" | escala Likert (1-5) | Questionário pós-experimento |
| M20 | Qualidade percebida dos comentários | Avaliação sobre utilidade, clareza e respeito dos comentários recebidos | escala Likert (1-5) | Questionário pós-experimento |
| M21 | Taxa de comentários acionáveis | Proporção de comentários de review que resultaram em mudanças no código (commits subsequentes) | percentual (%) | Análise de review comments + commits |

---

## 4. Escopo e contexto do experimento

### 4.1 Escopo funcional / de processo (incluído e excluído)

Este experimento foca na fase de integração e validação do código no fluxo de desenvolvimento, utilizando a criação e o tratamento de Pull Requests (PRs) como evento central.

**INCLUÍDO no experimento:**

- **Atividades cobertas:**
  - Desenvolvimento de código em branches feature separados do branch principal  
  - Criação e submissão de Pull Requests para integração de funcionalidades  
  - Processo de Code Review por pares (apenas no grupo experimental)  
  - Discussão técnica através de comentários nos PRs  
  - Aprovação/reprovação de PRs com base em critérios estabelecidos  
  - Merge de PRs aprovados ao branch principal (main/master)  
  - Correções e ajustes solicitados durante a revisão  
  - Acompanhamento de bugs reportados após o merge  

- **Artefatos analisados:**
  - Código-fonte de todas as funcionalidades desenvolvidas durante o experimento  
  - Pull Requests completos (título, descrição, diff de código, metadados)  
  - Comentários de revisão (review comments, sugestões, aprovações)  
  - Commits individuais associados aos PRs  
  - Issues do GitHub relacionadas aos PRs (bugs, melhorias)  
  - Relatórios de análise estática de código (SonarQube, linters)  
  - Logs de atividade do GitHub (timestamps, participantes)  
  - Respostas aos questionários pré e pós-experimento  

- **Equipes participantes:**
  - Equipes de 4 a 6 estudantes de Engenharia de Software  
  - Projetos desenvolvidos em disciplinas de desenvolvimento colaborativo  
  - Total estimado de 8 a 12 equipes (40 a 60 participantes)  
  - Estudantes do 6º ao 8º período do curso  
  - Equipes já formadas no início do semestre pela disciplina  

- **Módulos/Funcionalidades:**
  - Todas as funcionalidades de backend desenvolvidas (APIs, lógica de negócio, acesso a dados)  
  - Todas as funcionalidades de frontend desenvolvidas (interfaces, componentes, integração)  
  - Correções de bugs implementadas durante o semestre  
  - Refatorações de código realizadas após entregas iniciais  
  - Implementação de testes unitários e de integração  

**EXCLUÍDO do experimento:**

- **Atividades não cobertas:**
  - Commits diretos ao branch principal (serão tecnicamente bloqueados por branch protection)  
  - Processos de planejamento de sprints, reuniões de equipe e cerimônias ágeis  
  - Atividades de levantamento de requisitos e definição de escopo  
  - Configuração inicial de ambiente de desenvolvimento  
  - Processos de deploy, CI/CD e operação do sistema  
  - Atividades de design de interface (Figma, protótipos) não relacionadas ao código  
  - Comunicação externa ao GitHub (mensagens em WhatsApp, Discord, e-mail)  

- **Artefatos não analisados:**
  - Documentação externa ao repositório (Google Docs, wikis separadas)  
  - Artefatos de design e arquitetura (diagramas UML, modelos conceituais)  
  - Planos de projeto e cronogramas  
  - Relatórios de entregas para os professores  
  - Apresentações e slides de defesa dos projetos  
  - Contratos e acordos de equipe  

- **Tipos de código excluídos:**
  - Configurações de infraestrutura (Dockerfiles, CI/CD configs) – análise simplificada  
  - Arquivos de dados estáticos (JSONs de mock, fixtures)  
  - Dependências de terceiros (node_modules, venv)  
  - Código gerado automaticamente por ferramentas  

- **Participantes excluídos:**
  - Alunos que desistirem da disciplina antes da semana 4  
  - Equipes que desenvolverem projetos individuais ao invés de colaborativos  
  - Projetos de outras instituições ou cursos  
  - Estudantes que não concordarem com o Termo de Consentimento  

- **Medições não realizadas:**
  - Performance em runtime da aplicação (tempo de resposta, throughput)  
  - Experiência de usuários finais ou stakeholders externos  
  - Impacto financeiro ou de negócio (não aplicável em contexto acadêmico)  
  - Segurança em ambiente de produção real  
  - Escalabilidade do sistema desenvolvido  
  - Métricas de satisfação de cliente (não há cliente real)  

- **Contextos não cobertos:**
  - Projetos de outras disciplinas ou semestres posteriores  
  - Desenvolvimento profissional (estágios, trabalhos) dos participantes  
  - Contribuições open source externas aos projetos da disciplina  

### 4.2 Contexto do estudo (tipo de organização, projeto, experiência)
- **Tipo de Organização:** Instituição de Ensino Superior (IES) em nível de Graduação.  
- **Tipo de Projeto:** Projeto de software de médio porte e complexidade (e.g., um sistema web ou aplicativo móvel), com foco em desenvolvimento de funcionalidades e trabalho em equipe. O projeto tem uma duração limitada (típica de um semestre acadêmico).  
- **Criticidade:** Baixa. O projeto é didático. Falhas afetam a nota, mas não causam danos financeiros ou operacionais a clientes externos.  
- **Perfil de Experiência dos Participantes:** Desenvolvedores Juniores (estudantes com experiência em 1–2 anos de programação e familiaridade básica com o uso de Git). O experimento pressupõe que os participantes, em sua maioria, não têm experiência prévia formal em Code Review ou TDD.

### 4.3 Premissas
**P1 – Aprovação ética e consentimento voluntário:**  
O Comitê de Ética em Pesquisa (CEP) da PUC Minas aprovará o protocolo de pesquisa e todos os participantes concordarão voluntariamente em participar do estudo após serem informados detalhadamente sobre objetivos, procedimentos, riscos, benefícios e direitos. O Termo de Consentimento Livre e Esclarecido (TCLE) será assinado antes da coleta de qualquer dado, e o direito de retirada sem penalidades será garantido.

**P2 – Infraestrutura técnica disponível e funcional:**  
Todos os participantes terão acesso contínuo à internet, computadores adequados para desenvolvimento e contas ativas no GitHub durante todo o período do experimento. As ferramentas de análise estática (SonarQube Community, ESLint/Pylint) estarão configuradas e operacionais desde o início, os scripts de coleta via GitHub API funcionarão sem interrupções críticas, e o pesquisador terá permissões necessárias para configurar branch protection rules nos repositórios do grupo experimental.

**P3 – Conhecimento técnico mínimo dos participantes:**  
Estudantes possuem conhecimento funcional de Git (comandos básicos de commit, push, pull, branch, merge) e domínio intermediário da linguagem de programação escolhida para o projeto (JavaScript, Python ou Java), não sendo necessário treinamento técnico extensivo além do workshop inicial de 2 horas sobre Code Review.

**P4 – Comparabilidade inicial dos grupos:**  
Os grupos de controle e experimental terão distribuição similar de habilidades técnicas, experiência prévia e tamanho de equipes no início do experimento, permitindo comparação justa. Eventuais diferenças pré-existentes serão identificadas através do questionário inicial e tratadas estatisticamente como covariáveis nas análises.

### 4.4 Restrições
- **R1 – Restrição temporal:** o experimento está rigidamente limitado a um único semestre letivo de 16 semanas (fevereiro a junho de 2026), não sendo viável estendê-lo para múltiplos semestres devido ao ciclo natural das disciplinas e à necessidade de conclusão do TCC no prazo regulamentar. Este período inclui todas as fases: preparação, coleta de dados, análises e consolidação de resultados.  
- **R2 – Restrição de tamanho amostral:** o número de participantes é limitado pelas turmas disponíveis no semestre, não sendo possível recrutar participantes externos, de outros cursos ou instituições.  
- **R3 – Restrição orçamentária e de ferramentas:** não há orçamento para aquisição de ferramentas de análise de qualidade de código pagas. Serão utilizadas apenas ferramentas gratuitas (open source) ou as já integradas na plataforma.  
- **R4 – Restrição de acesso a dados:** a coleta de dados está restrita ao que é publicamente disponível via GitHub API e ferramentas integradas. Não é possível acessar comunicações privadas das equipes (WhatsApp, Discord, reuniões presenciais), processos mentais de decisão, ou atividades fora do GitHub.

### 4.5 Limitações previstas
- **L1 – Efeito Hawthorne:** participantes sabem que estão sendo observados, o que pode alterar comportamento (maior cuidado no código, revisões “pro forma”, respostas enviesadas).  
- **L2 – Maturação dos participantes:** estudantes melhoram naturalmente ao longo do semestre, podendo confundir o efeito do Code Review.  
- **L3 – Heterogeneidade das equipes e projetos:** variações de experiência, domínio, tecnologia e dinâmica interpessoal podem enviesar resultados.  
- **L4 – Tamanho e complexidade variável dos PRs:** PRs pequenos vs. grandes exigem normalização e análise de sensibilidade.

---

## 5. Stakeholders e impacto esperado

### 5.1 Stakeholders principais
- **Desenvolvedores (alunos):** responsáveis por abrir e revisar PRs.  
- **Professores/orientadores:** responsáveis pelo acompanhamento e validação do experimento.  
- **Pesquisador:** Investigador principal, coordenador do experimento, responsável por coleta e análise.  
- **Coordenação do curso de ES:** Aprovação institucional, suporte administrativo, decisão sobre adoção futura.

### 5.2 Interesses e expectativas dos stakeholders

**Alunos:**
- Esperam: aprender boas práticas de revisão, reduzir bugs e produzir código de maior qualidade.  
- Temem: aumento excessivo da burocracia, atrasos no merge do trabalho e julgamento negativo do código pelos pares.

**Professores/Orientadores:**
- Esperam: evidências quantificáveis de que o Code Review obrigatório melhora a qualidade do código entregue (M1, M3), facilitando a correção e avaliação.  
- Buscam: insights para otimizar as metodologias de ensino.

**Coordenação do Curso:**
- Esperam: dados para justificar a padronização de práticas industriais (Code Review) no currículo, aumentando a empregabilidade dos formandos.

**Pesquisador:**
- Busca: resultados estatisticamente significativos para responder às hipóteses e fornecer recomendações baseadas em evidências.

### 5.3 Impactos potenciais no processo / produto
**Durante o experimento:**
- Aumento do tempo médio de merge para PRs com review obrigatório.  
- Maior carga cognitiva e responsabilidade para os revisores.  
- Discussões técnicas mais frequentes no repositório.

**Após o experimento:**
- Maior consistência e manutenibilidade do código integrado.  
- Redução de bugs encontrados tardiamente.  
- Disseminação de conhecimento técnico dentro da equipe.

---

## 6. Riscos de alto nível, premissas e critérios de sucesso

### 6.1 Riscos de alto nível (negócio, técnicos, etc.)
- **R1 (Técnico):** Baixa adesão ao processo de revisão (review feito “pro forma”).  
- **R2 (Logístico):** Volume de PRs inferior ao necessário para análise.  
- **R3 (Técnico):** Ambiente do GitHub com falhas ou sem acesso às métricas necessárias.  
- **R4 (Processo):** Participantes ignoram o protocolo (merge direto sem review obrigatório).  
- **R5 (Organizacional):** Participantes veem o experimento como uma sobrecarga e não colaboram.

### 6.2 Critérios de sucesso globais (go / no-go)
O experimento será considerado viável e útil se:
- For possível coletar pelo menos **30 PRs** analisáveis, distribuídos entre grupo controle e tratamento.  
- Os participantes aderirem aos protocolos (obrigatoriedade de review, preenchimento de formulários, vinculação de issues).  
- Pelo menos **uma métrica de qualidade** (ex.: bugs, score percebido) indicar melhora com review obrigatório sem custo proibitivo de tempo (**> 25%**).

### 6.3 Critérios de parada antecipada (pré-execução)
O experimento deve ser suspenso ou adiado se:
- Não houver pelo menos **2 equipes com PRs ativos** no período planejado.  
- Não for possível configurar ou aplicar a **branch protection rule** no grupo tratamento.  
- Houver quebra no cronograma da disciplina, inviabilizando entregas ou revisões.  
- Algum erro técnico impedir acesso ou exportação de dados do GitHub.  
- A maioria dos PRs não puder ser rastreada com clareza (sem vínculo com tarefas reais ou sem autores identificados).
