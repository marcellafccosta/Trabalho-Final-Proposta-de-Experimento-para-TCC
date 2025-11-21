# Plano de Experimento – Scoping e Planejamento

## 1. Identificação básica

### 1.1 Título do experimento

Impacto de Code Review obrigatório na qualidade de PRs em projetos acadêmicos

### 1.2 ID / código

EXP-ACAD-2025

### 1.3 Versão do documento e histórico de revisão

| Versão | Data | Alterações | Autor |
|--------|------|------------|-------|
| v1.0 | 21/11/2025 | Criação Inicial do Documento (Identificação Básica, Contexto e Problema) | Marcella Costa |

### 1.4 Datas (criação, última atualização)

- **Criação:** 21/11/2025
- **Última atualização:** 21/11/2025

### 1.5 Autores (nome, área, contato)

Marcella Ferreira Chaves Costa - Engenharia de Software, PUC Minas - marcellafccosta@gmail.com

### 1.6 Responsável principal (PI / dono do experimento)

**Marcella Ferreira Chaves Costa**

Estudante de Engenharia de Software - TCC

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

**Equipe:** grupos de 3–6 alunos desenvolvendo software em ciclos semanais/sprints.

**Domínio:** Projetos acadêmicos de desenvolvimento de software em linguagem comum (e.g., Python, Java, JavaScript).

**Tecnologias e Ferramentas:**
- **Controle de Versão:** Git (padrão).
- **Plataforma de Colaboração:** GitHub (essencial para configurar a regra de Code Review Obrigatório via branch protection rules e para extrair métricas de PRs, como comentários e tempo de merge).
- **Processo de desenvolvimento:** integração via PRs, com divisão de tarefas, commits frequentes e entregas incrementais.
- **Ferramentas relevantes:** Pull Requests, Reviews, Branch Protection Rules, Issues e Actions do GitHub.

### 2.3 Trabalhos e evidências prévias (internos e externos)

Evidências internas coletadas através de observação sistemática no curso de Engenharia de Software revelam que, em várias disciplinas e projetos desenvolvidos, os Pull Requests são frequentemente aceitos e integrados sem passar por um processo sistemático de revisão. Como resultado desta prática, bugs e defeitos são detectados apenas nas fases finais de testes ou mesmo após a entrega do projeto, gerando retrabalho significativo e comprometendo a qualidade final do software produzido.

No âmbito externo, tanto a literatura científica quanto a prática na indústria de software estabelecem o Code Review como uma prática consolidada na engenharia de software moderna. Esta prática tem demonstrado efetividade na redução de defeitos, padronização de código, compartilhamento de conhecimento entre membros da equipe e prevenção de regressões no sistema. Resultados empíricos de diversos estudos apontam para um impacto positivo significativo na qualidade do software, embora estes benefícios sejam dependentes de fatores contextuais, como a experiência do time, o volume de mudanças em cada revisão e a cultura organizacional estabelecida.

Entre os trabalhos científicos relevantes, destaca-se o estudo de **McIntosh et al. de 2016**, intitulado *"The impact of code review coverage and code review participation on software quality"*, que analisou projetos de código aberto como Qt, VTK e ITK, demonstrando correlação entre Code Review e redução de 14% a 28% nos bugs pós-release. **Bacchelli e Bird, em 2013**, publicaram *"Expectations, outcomes, and challenges of modern code review"*, identificando que os principais benefícios reportados são encontrar defeitos, representando 14% dos casos, e transferência de conhecimento, correspondendo a 41% dos benefícios percebidos. No contexto pedagógico específico, **Hundhausen et al., em 2013**, através do trabalho *"Talking about code: Integrating pedagogical code reviews into early computing courses"*, demonstraram que Code Review pedagógico melhora significativamente a compreensão de código por parte dos estudantes em cursos iniciais de computação.

### 2.4 Referencial teórico e empírico essencial

O referencial teórico que fundamenta este experimento baseia-se em três conceitos centrais da Engenharia de Software moderna.

**1. Code Review (Revisão de Código):** processo de inspeção colaborativa do código-fonte realizado por membros da equipe antes que as mudanças sejam integradas ao branch principal do repositório. Este processo visa identificar defeitos, garantir aderência a padrões estabelecidos, promover compartilhamento de conhecimento e melhorar aspectos de design e arquitetura do software.

**2. Pull Request (PR):** proposta formal de mudança em repositórios Git, seguindo o fluxo de criação de um branch com as alterações desejadas, submissão para revisão por outros membros da equipe, processo de aprovação baseado em critérios estabelecidos e, finalmente, integração ao branch principal através do merge. Os Pull Requests facilitam a discussão assíncrona sobre as mudanças propostas, permitem revisão sistemática do código e são centrais no workflow de equipes de desenvolvimento modernas.

**3. Qualidade de Software:** neste estudo é fundamentado no modelo internacional ISO/IEC 25010. Este modelo estabelece dimensões de qualidade que incluem funcionalidade, abrangendo corretude e completude das funcionalidades implementadas; confiabilidade, relacionada à maturidade do sistema, disponibilidade e tolerância a falhas; segurança, contemplando confidencialidade e integridade dos dados; manutenibilidade, que engloba modularidade, reusabilidade e analisabilidade do código; e eficiência de desempenho do sistema. Para os propósitos deste experimento específico, o foco concentra-se em três dimensões principais: manutenibilidade, avaliada através de métricas de complexidade e duplicação de código; confiabilidade, medida através da quantidade de bugs detectados; e segurança, analisada através da identificação de vulnerabilidades no código produzido.
