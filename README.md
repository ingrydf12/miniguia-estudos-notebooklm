## Contexto e Objetivos

**Assunto escolhido:** CWE na prática: como vulnerabilidades surgem e como preveni-las

### Objetivos de estudo:

- Identificar e mitigar as fraquezas mais perigosas, tomando como base o CWE Top 25 para destacar as fraquezas de software mais comuns e impactantes, servindo como um guia para que desenvolvedores e arquitetos eliminem defeitos antes da implantação, quando é mais barato e fácil fazê-lo.
- Conscientizar os riscos críticos de aplicações pelo OWASP Top 10, representando um consenso global sobre o que deve ser priorizado
- Fornecer Orientações Técnicas Práticas e Concisas: O notebook inclui a Série de Cheat Sheets da OWASP, que visa fornecer coleções de informações de alto valor e fácil leitura sobre tópicos específicos de segurança de aplicações, criadas por especialistas no assunto
- Framework de recuperação e prevenção, utilizando o framework do NIST, o notebook define práticas fundamentais de segurança (como "Preparar a Organização", "Proteger o Software", "Produzir Software Bem Protegido" e "Responder a Vulnerabilidades") que devem ser integradas ao ciclo de vida de desenvolvimento de software (SDLC)

## Validação do Notebook

O foco deste projeto não foi apenas extrair respostas do NotebookLM, mas avaliar sua confiabilidade como ferramenta de estudo. Para isso, adotamos um fluxo de validação cruzada entre modelos:

- Pergunta ao NotebookLM — com base nas fontes curadas
- Verificação das fontes citadas — checando se a resposta reflete o conteúdo real das fontes ou extrapola
- Comparação com ChatGPT — para identificar divergências, vieses e lacunas
- Revisão técnica com Claude — para filtrar pedantismo e distinguir detalhes irrelevantes de correções legítimas
- Consolidação do aprendizado — registrado no Contexto & Aprendizagem de cada teste
Objetivo: reduzir alucinações, identificar vieses de fonte e distinguir erros factuais de diferenças de perspectiva.


## Curadoria de Fontes

| Fonte | Descrição | Link |
|---|---|---|
| **CWE - CWE Top 25 Most Dangerous Software Weaknesses** | Lista das fraquezas de software mais comuns e impactantes da atualidade, servindo como guia para investimentos e práticas que visam prevenir vulnerabilidades. | https://cwe.mitre.org/top25/ |
| **CWE - Common Weakness Enumeration** | Lista desenvolvida pela comunidade que cataloga fraquezas de software (SW) e hardware (HW) que podem se tornar vulnerabilidades exploráveis. | https://cwe.mitre.org/index.html |
| **Introduction - OWASP Cheat Sheet Series** | Coleção concisa de informações de alto valor sobre tópicos específicos de segurança de aplicações, criada por profissionais experientes para fornecer orientações de fácil leitura. | https://cheatsheetseries.owasp.org/index.html |
| **OWASP Top 10: 2025** | Documento padrão de conscientização para desenvolvedores e segurança de aplicações web, representando o consenso global sobre os riscos de segurança mais críticos. | https://owasp.org/Top10/2025/ |
| **Secure Software Development Framework (SSDF) \| NIST** | Conjunto de práticas fundamentais de desenvolvimento de software seguro, baseado em documentos de organizações como BSA, OWASP e SAFECode, focado na redução de vulnerabilidades em softwares lançados. | https://csrc.nist.gov/projects/ssdf |

## Testes e Cicatrizes

### 1. Prompt 001: Explique como são as CWE para quem está iniciando a estudar engenharia de software

**Contexto**

É importante antes mesmo de saber como deixar suas aplicações mais seguras, entender o que são as CWE e como isso pode guiar na questão de prioridades dentro da engenharia e gestão do software por fatores de potenciais riscos de segurança.

**Resposta obtida**:

1. O que é o CWE?
O CWE é uma lista desenvolvida pela comunidade que identifica e classifica fraquezas de software e hardware que podem se tornar vulnerabilidades exploráveis
. Ele não foca em uma falha específica de um programa (isso seria um CVE), mas sim no tipo de erro que o desenvolvedor cometeu, como uma falha na validação de dados ou um erro de gerenciamento de memória
.
2. Fraquezas vs. Vulnerabilidades
Um ponto crucial para iniciantes é entender que o CWE trata da causa raiz
.
Fraqueza (CWE): É o erro técnico ou a falha de design no código (ex: não verificar o tamanho de um arquivo antes de carregá-lo).
Vulnerabilidade: É quando essa fraqueza pode ser explorada por um atacante para causar danos. Identificar fraquezas via CWE permite que os desenvolvedores corrijam o problema antes da implantação, quando é muito mais barato e fácil de resolver do que remediar uma vulnerabilidade já exposta
.
3. O "CWE Top 25"
Como existem quase mil tipos de fraquezas catalogadas (944 no total), o projeto publica anualmente o CWE Top 25 Most Dangerous Software Weaknesses
. Esta lista destaca as falhas mais comuns e impactantes da atualidade, que são frequentemente fáceis de encontrar e explorar
. Elas podem permitir que atacantes:
Assumam o controle total de um sistema
.
Roubem dados sensíveis
.
Impeçam o funcionamento de aplicações (ataques de negação de serviço)
.
4. Por que usar o CWE?
Para um estudante ou profissional de segurança, o CWE serve como um guia estratégico para:
Planejamento de Segurança: Ajuda a eliminar classes inteiras de defeitos (como falhas de injeção) durante o ciclo de desenvolvimento (SDLC)
.
Economia de Recursos: Reduzir vulnerabilidades durante a criação do software economiza dinheiro que seria gasto em correções pós-implantação
.
Priorização de Riscos: Permite focar os esforços de defesa nas fraquezas que mais atraem a atenção de adversários
.
Linguagem Comum: Facilita a comunicação entre desenvolvedores, profissionais de segurança e compradores de software ao usar termos padronizados
.
5. Quem mantém o projeto?
O CWE é gerenciado pela The MITRE Corporation e conta com o patrocínio da CISA (Cybersecurity and Infrastructure Security Agency) do Departamento de Segurança Interna dos EUA
. Ele é um padrão aberto usado globalmente por organizações para melhorar a segurança de seus produtos
.

### 2. Prompt 2 - Com base exclusivamente nas fontes fornecidas, explique o conceito de CWE. Estruture a resposta em: definição; finalidade; estrutura de uma CWE; exemplos; relação com vulnerabilidades; relação com CVE. Não utilize informações que não possam ser sustentadas pelas fontes.

**Contexto** 

Para evitar que o Notebook extraia informações externas, foi interessante colocar esse parâmetro, além de fazer ele buscar mais profundamente nas fontes inseridas, trazendo exemplos para relacionar as vulnerabilidades ao contexto real e por quê estão relacionadas as fontes.

**Resposta obtida**

- Definição

A CWE é uma lista desenvolvida pela comunidade que cataloga fraquezas de software (SW) e hardware (HW). 
Essas fraquezas são tipos de erros ou falhas técnicas que têm o potencial de se tornarem vulnerabilidades exploráveis caso não sejam corrigidas. Atualmente, o catálogo abrange um total de 944 fraquezas identificadas.

2. Finalidade

O propósito central da CWE é servir como um guia para que desenvolvedores, designers de hardware e arquitetos de segurança possam eliminar falhas antes da implantação, momento em que a correção é mais fácil e econômica. Seus objetivos específicos incluem:
- Redução de Vulnerabilidades: Fornecer insights sobre as causas raiz para eliminar classes inteiras de defeitos, como problemas de injeção ou segurança de memória
- Economia de Custos: Reduzir o número de problemas que precisam ser gerenciados após o lançamento do software
- Gestão de Riscos: Auxiliar organizações a priorizar esforços de segurança com base em tendências de dados e na atratividade de certas fraquezas para adversários
- Padronização: Oferecer uma linguagem comum para descrever práticas de segurança e facilitar a comunicação entre produtores e compradores de tecnologia

3. Estrutura de uma CWE

Embora as fontes não detalhem todos os campos individuais de um registro, elas indicam que a estrutura do catálogo permite:
- Busca por ID: Cada fraqueza possui um identificador único para consulta.
Categorização: As fraquezas são organizadas em visões específicas, como Desenvolvimento de Software ou Design de Hardware
- Mapeamento de Causa Raiz: A estrutura permite identificar a falha subjacente que originou uma vulnerabilidade
- Hierarquização: Existem listas derivadas, como o CWE Top 25, que classificam as fraquezas mais perigosas e impactantes com base em sua prevalência e severidade

4. Exemplos
As fontes mencionam diversas classes e exemplos de fraquezas catalogadas, tais como:
- Injeção (Injection), incluindo especificamente a Injeção de Comando
- Falhas de Segurança de Memória (Memory Safety)
- Leitura Fora dos Limites (Out-of-Bounds Read)

5. Relação com Vulnerabilidades

A CWE foca na causa raiz do problema. Uma fraqueza é o erro técnico no código ou no design; quando essa fraqueza é passível de exploração, ela se manifesta como uma vulnerabilidade. Ao tratar a fraqueza listada no CWE durante o ciclo de desenvolvimento (SDLC), impede-se que a vulnerabilidade venha a existir no produto final


6. Relação com CVE

Existe uma distinção clara e uma conexão direta entre o CWE e o CVE (Common Vulnerabilities and Exposures):

- O CWE identifica os tipos de erros (fraquezas), enquanto o CVE identifica vulnerabilidades específicas encontradas em produtos reais.
- O CWE é utilizado para descobrir quais fraquezas são as causas fundamentais por trás dos milhares de registros CVE existentes.
- A comunidade trabalha no mapeamento de registros CVE para CWEs para que se possa entender as tendências de quais falhas de desenvolvimento estão gerando mais vulnerabilidades no mercado.

### 3. Prompt 3 - Compare CWE, CVE e CVSS.
Explique:
- o que cada um representa;
- qual problema cada um resolve;
- como eles se relacionam;
- um exemplo hipotético mostrando os três conceitos.

Apresente a resposta em uma tabela.

**Resposta obtida**

Com base nos documentos fornecidos e em informações complementares de conhecimento geral (necessárias para o conceito de CVSS, que não é detalhado nas fontes), aqui está a comparação entre CWE, CVE e CVSS:

| Característica | **CWE** (Common Weakness Enumeration) | **CVE** (Common Vulnerabilities and Exposures) | **CVSS** (Common Vulnerability Scoring System)* |
| :--- | :--- | :--- | :--- |
| **O que representa** | Um catálogo universal de **tipos de falhas** ou "fraquezas" de software e hardware. | Um registro de uma **vulnerabilidade específica** encontrada em um produto ou sistema real. | Um sistema de pontuação para medir a **severidade** de uma vulnerabilidade. |
| **Problema que resolve** | Identifica a **causa raiz** dos erros para que desenvolvedores possam eliminá-los durante a criação do código. | Fornece um identificador único para rastrear e comunicar falhas conhecidas em softwares lançados. | Ajuda organizações a **priorizar** quais vulnerabilidades devem ser corrigidas primeiro com base no risco. |
| **Como se relacionam** | É o "tipo de doença". O CWE ajuda a entender qual falha de design gerou o CVE. | É o "caso clínico". Cada registro CVE é mapeado para um CWE para identificar sua origem técnica. | É a "gravidade da febre". O CVSS atribui uma nota à vulnerabilidade (CVE) para indicar o impacto. |
| **Exemplo Hipotético** | **CWE-89:** Fraqueza de Injeção de SQL (o erro genérico de não validar comandos). | **CVE-2024-1234:** Uma falha específica de Injeção de SQL encontrada no "Banco de Dados X" versão 2.0. | **Nota 9.8 (Crítica):** Indica que a falha CVE-2024-1234 é muito fácil de explorar e tem alto impacto. |

*\*Nota: As fontes fornecidas mencionam o termo **CWSS** (Common Weakness Scoring System) como uma marca registrada da MITRE, mas não detalham o funcionamento do **CVSS**. As informações sobre CVSS na tabela acima foram incluídas para atender à sua solicitação e devem ser verificadas de forma independente, pois não constam integralmente nos documentos originais.*

### Entendendo a Conexão
De acordo com as fontes, o **CWE** serve como um guia estratégico para investimentos e políticas de segurança, pois ao descobrir as causas raízes (CWEs) de milhares de registros **CVE**, as organizações podem prevenir que essas falhas ocorram em primeiro lugar. O framework **SSDF** do NIST também recomenda que as organizações respondam a vulnerabilidades identificando suas causas raízes para prevenir recorrências.

### 4. Prompt 4 - Analise as fontes e identifique possíveis confusões
que um estudante iniciante poderia fazer entre CWE,
CVE, CVSS e OWASP Top 10.

Para cada confusão:
- explique o erro;
- explique o conceito correto;
- indique qual fonte sustenta a explicação.
- explore um exemplo

**Contexto**

Pode ser interessante fazer o Notebook pensar de forma mais crítica para entender que alguns conceitos podem ficar confusos, deixando uma resposta que explicaria de forma mais direta esses fundamentos pra entender a temática e explorando um exemplo para entender a identificação e a mitigação do problema.

**Resposta obtida**

Com base na análise das fontes fornecidas, um estudante iniciante pode enfrentar confusões conceituais devido à sopa de letrinhas e às sobreposições entre os padrões. Abaixo, detalho as quatro confusões mais comuns:

### 1. CWE vs. CVE (O erro de especificidade)

*   **Explicação do Erro:** O estudante pode achar que o **CWE** identifica uma falha específica encontrada em um programa famoso (como um bug no Windows ou no Chrome).
*   **Conceito Correto:** O **CWE** (Common Weakness Enumeration) é um catálogo de **tipos ou classes de falhas** (fraquezas), enquanto o **CVE** (Common Vulnerabilities and Exposures) registra **instâncias reais e específicas** de vulnerabilidades em produtos de software. O CWE foca na **causa raiz** técnica para evitar que o erro se repita.
*   **Fonte:** "CWE Top 25 Most Dangerous Software Weaknesses".
*   **Exemplo:** O **CWE-89** representa o conceito genérico de "Injeção de SQL". Já um **CVE** seria o registro de uma falha de Injeção de SQL específica encontrada no plugin "WP-Statistics" do WordPress na versão 1.0.

### 2. CWE Top 25 vs. OWASP Top 10 (O erro de escopo)

*   **Explicação do Erro:** Achar que as duas listas são intercambiáveis ou que cobrem o mesmo universo de problemas.
*   **Conceito Correto:** O **CWE Top 25** foca em **fraquezas técnicas** de software e hardware em geral, sendo um guia para desenvolvedores e arquitetos eliminarem defeitos no nível do código. O **OWASP Top 10** é um documento de conscientização focado em **riscos críticos para aplicações web**, representando um consenso global sobre o que é mais perigoso nesse ecossistema específico.
*   **Fonte:** "CWE - Common Weakness Enumeration" e "OWASP Top 10:2025".
*   **Exemplo:** O CWE inclui falhas de baixo nível como "Leitura Fora dos Limites" (CWE-125). O OWASP Top 10 agrupa problemas em categorias de risco mais amplas, como "Falhas Criptográficas" (A04:2025).

### 3. Identificadores (CWE/CVE) vs. Sistemas de Pontuação (CVSS/CWSS)

*   **Explicação do Erro:** O estudante pode pensar que o número do ID (ex: CWE-20) indica o quão grave é a falha.
*   **Conceito Correto:** CWE e CVE são apenas identificadores (nomes em um catálogo). Para medir a **severidade e o impacto**, utilizam-se sistemas de pontuação. As fontes mencionam o **CWSS** (Common Weakness Scoring System) como o sistema voltado para fraquezas. O CVSS (Common Vulnerability Scoring System), embora não detalhado tecnicamente nas fontes, é o padrão de mercado para pontuar o risco de CVEs.
*   **Fonte:** "CWE - CWE Top 25 Most Dangerous Software Weaknesses".
*   **Exemplo:** Duas vulnerabilidades diferentes podem ser do tipo **CWE-79** (Cross-site Scripting), mas uma pode receber uma nota de severidade alta (via CWSS/CVSS) por estar em uma página de login, enquanto a outra recebe uma nota baixa por estar em uma área restrita e inofensiva.

### 4. Fraqueza (CWE) vs. Risco de Aplicação (OWASP)

*   **Explicação do Erro:** Confundir a falha técnica "bruta" com o cenário de risco organizacional.
*   **Conceito Correto:** Uma **fraqueza (CWE)** é o erro técnico cometido pelo desenvolvedor (ex: não validar um campo de entrada). Um **risco (OWASP Top 10)** considera a probabilidade de exploração e o impacto no negócio. O framework **SSDF** do NIST reforça que tratar as fraquezas (causas raízes) é o que permite mitigar os riscos e prevenir recorrências.
*   **Fonte:** "OWASP Top 10:2025" e "Secure Software Development Framework (SSDF)".
*   **Exemplo:** Uma falha técnica de "Mishandling of Exceptional Conditions" (CWE-755) é a fraqueza. No contexto do OWASP Top 10, isso se traduz no risco de uma aplicação vazar informações sensíveis em mensagens de erro para o usuário final (A10:2025).

#### Cicatrizes

No item 4, o texto atribui à CWE-755 o nome "Mishandling of Exceptional Conditions". Isso está ligeiramente incorreto: o nome oficial da CWE-755 no catálogo MITRE é "Improper Handling of Exceptional Conditions". "Mishandling of Exceptional Conditions" é, na verdade, o nome da categoria OWASP A10:2025 (que reúne 24 CWEs relacionadas, incluindo provavelmente a 755, mas não é o nome oficial da CWE em si). Ou seja, houve uma pequena confusão entre o nome da fraqueza individual (CWE) e o nome da categoria de risco (OWASP) — que ironicamente é exatamente o tipo de erro conceitual que o próprio documento tenta ensinar a evitar no item 4.

### 5. Prompt 5 - Como o SSDF previne vulnerabilidades?

**Contexto**

Seria interessante não somente saber acerca das vulnerabilidades, dos tipos de fraquezas listadas pelo CWE, mas como também previnir elas. 

**Resposta obtida**

O **Secure Software Development Framework (SSDF)**, desenvolvido pelo NIST, previne vulnerabilidades ao integrar práticas de segurança fundamentais e comprovadas em todas as fases do Ciclo de Vida de Desenvolvimento de Software (SDLC). 

A prevenção ocorre através de quatro frentes principais, organizadas em grupos de práticas:

*   **Preparar a Organização (PO):** Garante que as pessoas, processos e tecnologias estejam prontos para realizar o desenvolvimento seguro em nível organizacional. Isso inclui a documentação de requisitos de segurança que o software deve atender.
*   **Proteger o Software (PS):** Foca em proteger todos os componentes do software contra adulterações e acessos não autorizados, inclusive coletando dados de procedência de todos os componentes das versões lançadas.
*   **Produzir Software Bem Protegido (PW):** Visa produzir software com o mínimo de vulnerabilidades de segurança em seus lançamentos. Isso é feito através do rastreamento de requisitos de segurança, riscos e decisões de design durante o desenvolvimento.
*   **Responder a Vulnerabilidades (RV):** Identifica vulnerabilidades residuais e as trata adequadamente para **prevenir que falhas semelhantes ocorram no futuro**, atacando a causa raiz.

**Destaques sobre como o SSDF atua na prevenção:**

*   **Abordagem baseada em riscos:** O framework ajuda a priorizar atividades de segurança de acordo com as necessidades de negócio, tolerância a riscos e recursos disponíveis, em vez de ser apenas uma lista de verificação estática.
*   **Foco na Causa Raiz:** Ao analisar por que uma vulnerabilidade ocorreu, o SSDF permite que a organização mude seus processos para evitar que aquela classe inteira de erro se repita.
*   **Redução de Impacto:** Além de evitar que a falha exista, o SSDF implementa práticas que reduzem o dano potencial caso uma vulnerabilidade não detectada venha a ser explorada.
*   **Linguagem Comum:** Facilita a comunicação entre produtores e compradores de software, garantindo que as expectativas de segurança sejam claras e verificáveis desde a aquisição.

### 6. Prompt 6 - Como as Cheat Sheets da OWASP ajudam na prática?

**Resposta obtida**

As **Cheat Sheets da OWASP** auxiliam na prática fornecendo uma coleção concisa de informações de **alto valor** sobre tópicos específicos de segurança de aplicações. Elas são desenvolvidas por profissionais de segurança que possuem **especialização** em temas específicos, garantindo que o conteúdo seja tecnicamente robusto.

Abaixo estão as principais formas como elas ajudam no dia a dia:

*   **Orientações Técnicas Diretas:** Em vez de manuais extensos, elas oferecem orientações em um formato de **fácil leitura**, permitindo que desenvolvedores e profissionais de segurança encontrem rapidamente soluções para problemas comuns.
*   **Cobertura Ampla de Tecnologias e Conceitos:** Existem guias práticos para uma vasta gama de tópicos, desde segurança em **Docker, GraphQL e Microserviços** até defesas contra ataques específicos como **Injeção de SQL, Cross-Site Scripting (XSS)** e **Clickjacking**.
*   **Suporte ao OWASP Top 10:** Elas servem como um complemento prático ao documento de conscientização do Top 10, fornecendo o "como fazer" para mitigar os riscos ali listados, como falhas de autenticação e controle de acesso.
*   **Implementação do SSDF:** Práticas de frameworks como o **SSDF (NIST)** utilizam documentos da OWASP como referência para ajudar as organizações a produzir software bem protegido e a reduzir a causa raiz de vulnerabilidades.
*   **Acessibilidade:** Os guias podem ser baixados para consulta offline, facilitando o acesso à informação em diferentes ambientes de trabalho.
*   **Alinhamento com Padrões de Verificação:** As cheat sheets são frequentemente indexadas por outros padrões da OWASP, como o **ASVS** (Application Security Verification Standard) e o **MASVS** (Mobile Application Security Verification Standard), ajudando a manter a consistência entre o desenvolvimento e a auditoria de segurança.

## Glossário

| Conceito        | Explicação                                                 | Relação                                       |
| --------------- | ---------------------------------------------------------- | --------------------------------------------- |
| CWE             | Classificação de fraquezas de software                     | Pode descrever a causa de uma vulnerabilidade |
| CVE             | Identificador de uma vulnerabilidade específica            | Pode estar associada a uma CWE                |
| CVSS            | Sistema para avaliar severidade                            | Pode ser utilizado para avaliar uma CVE       |
| Vulnerabilidade | Falha que pode ser explorada                               | Pode resultar de uma CWE                      |
| Exploit         | Técnica/código utilizado para explorar uma vulnerabilidade | Explora uma vulnerabilidade                   |
| Mitigação       | Medida para reduzir ou eliminar o risco                    | Pode impedir uma CWE                          |
| SSDF   | Práticas para desenvolvimento seguro                       | Ajuda a prevenir CWEs                         |

## Pergunta norteadora

Como o conhecimento sobre CWE pode ajudar um desenvolvedor a identificar, compreender e prevenir fraquezas de segurança durante o desenvolvimento de software?

## Mini-guia de estudos
### Resumos estruturados

# Miniguia de Estudo — Segurança de Software e CWE

## 1. Fundamentos de Segurança de Software

### Vulnerabilidade

Uma vulnerabilidade é uma falha ou condição em um sistema que pode ser explorada para comprometer propriedades como confidencialidade, integridade ou disponibilidade.

### Fraqueza (Weakness)

Uma fraqueza representa uma condição ou erro no software que pode contribuir para o surgimento de uma vulnerabilidade. O **CWE (Common Weakness Enumeration)** é utilizado para catalogar e organizar essas fraquezas.

### Exploit

Um exploit é uma técnica, código ou procedimento utilizado para explorar uma vulnerabilidade existente em um sistema.

### Risco

O risco representa a possibilidade de um evento de segurança causar impacto em um sistema. Ele está relacionado à combinação entre probabilidade e impacto.

### Mitigação

São medidas utilizadas para reduzir a probabilidade ou o impacto de uma vulnerabilidade ou fraqueza.

---

## 2. O que é CWE?

**CWE (Common Weakness Enumeration)** é uma classificação desenvolvida pela comunidade para catalogar fraquezas comuns encontradas em software e hardware.

O objetivo principal é fornecer uma linguagem comum para descrever, identificar e discutir problemas de segurança.

De forma simplificada:

```text
Erro ou condição insegura
        ↓
Fraqueza
        ↓
CWE
        ↓
Pode contribuir para uma vulnerabilidade
        ↓
Possível exploração
```

A CWE não representa necessariamente uma vulnerabilidade específica. Ela representa uma **categoria ou tipo de fraqueza**.

---

## 3. CWE, CVE e CVSS

Esses conceitos podem ser confundidos, mas possuem funções diferentes.

| Conceito       | Função                                                                                        |
| -------------- | --------------------------------------------------------------------------------------------- |
| **CWE**        | Classifica tipos de fraquezas de software e hardware                                          |
| **CVE**        | Identifica vulnerabilidades específicas                                                       |
| **CVSS**       | Avalia a severidade de uma vulnerabilidade                                                    |
| **CWE Top 25** | Destaca as fraquezas consideradas mais perigosas com base em critérios definidos pelo projeto |

Uma forma simples de visualizar:

```text
CWE
 ↓
Tipo de fraqueza

CVE
 ↓
Vulnerabilidade específica

CVSS
 ↓
Severidade da vulnerabilidade
```

---

## 4. CWE e OWASP Top 10

CWE e OWASP Top 10 não são a mesma coisa.

O **CWE** possui uma abordagem de classificação de fraquezas, enquanto o **OWASP Top 10** apresenta uma visão dos principais riscos de segurança relacionados a aplicações web.

Eles podem ser utilizados em conjunto:

```text
CWE
 ↓
Identificação/classificação da fraqueza

OWASP Top 10
 ↓
Contextualização do risco em aplicações web

Secure Coding
 ↓
Prevenção e mitigação
```

---

## 5. CWE Top 25

O **CWE Top 25 Most Dangerous Software Weaknesses** apresenta uma lista das fraquezas de software consideradas mais comuns e impactantes.

Seu objetivo é ajudar organizações e desenvolvedores a priorizar esforços de segurança.

O Top 25 pode ser utilizado como ponto de partida para estudar:

* quais fraquezas aparecem com maior frequência;
* quais apresentam maior impacto;
* como essas fraquezas surgem;
* como identificá-las;
* como preveni-las.

---

## 6. Análise de uma Fraqueza

Ao estudar uma CWE, é importante não memorizar apenas seu nome.

Uma análise completa deve responder:

1. **O que é a fraqueza?**
2. **Como ela surge?**
3. **Como pode ser identificada?**
4. **Qual é seu impacto?**
5. **Qual tipo de vulnerabilidade pode resultar dela?**
6. **Como pode ser explorada?**
7. **Como pode ser mitigada?**
8. **Como evitar que ela seja introduzida durante o desenvolvimento?**

Um modelo mental útil:

```text
Causa
 ↓
Fraqueza
 ↓
Vulnerabilidade
 ↓
Impacto
 ↓
Exploração
 ↓
Mitigação
 ↓
Prevenção
```

---

## 7. Segurança no Desenvolvimento

A segurança não deve ser considerada apenas depois que uma vulnerabilidade é encontrada.

O **Secure Software Development Framework (SSDF)** apresenta práticas que podem ser incorporadas ao processo de desenvolvimento para reduzir a quantidade de vulnerabilidades introduzidas no software.

Alguns princípios importantes são:

* preparar o ambiente para desenvolvimento seguro;
* proteger o software durante o desenvolvimento;
* produzir software com práticas de desenvolvimento seguro;
* responder adequadamente às vulnerabilidades encontradas.

A ideia central é incorporar segurança ao processo de desenvolvimento, em vez de tratá-la somente como uma etapa posterior.

---

## 8. Análise de Código

Uma maneira prática de aplicar o conhecimento sobre CWE é analisar código procurando comportamentos inseguros.

Exemplo:

```python
query = "SELECT * FROM users WHERE name = '" + username + "'"
```

O ponto importante da análise não é apenas identificar que o código é "inseguro", mas entender:

```text
Entrada controlada pelo usuário
        ↓
Concatenação direta
        ↓
Construção insegura da consulta
        ↓
Possível SQL Injection
        ↓
CWE relacionada
        ↓
Impacto
        ↓
Mitigação
```

A análise deve então buscar uma implementação mais segura, como consultas parametrizadas.

Esse processo pode ser repetido para diferentes classes de fraquezas.

---

## 9. Checklist de Estudo de uma CWE

Ao estudar uma nova CWE, utilizar o seguinte checklist:

* [ ] Entender a definição.
* [ ] Identificar a causa da fraqueza.
* [ ] Entender como ela aparece no código.
* [ ] Identificar possíveis consequências.
* [ ] Encontrar exemplos práticos.
* [ ] Relacionar a CWE com vulnerabilidades reais quando aplicável.
* [ ] Estudar métodos de detecção.
* [ ] Estudar técnicas de mitigação.
* [ ] Identificar boas práticas de prevenção.
* [ ] Comparar com outras CWEs semelhantes.
* [ ] Testar o conhecimento utilizando perguntas ou análise de código.

---

# Glossário

| Conceito                         | Definição resumida                                                                                              |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| **CWE**                          | Classificação de fraquezas comuns em software e hardware.                                                       |
| **CVE**                          | Identificador de uma vulnerabilidade específica.                                                                |
| **CVSS**                         | Sistema utilizado para avaliar a severidade de vulnerabilidades.                                                |
| **Vulnerabilidade**              | Falha ou condição que pode ser explorada e gerar impacto de segurança.                                          |
| **Fraqueza**                     | Condição ou erro que pode contribuir para uma vulnerabilidade.                                                  |
| **Exploit**                      | Técnica ou código utilizado para explorar uma vulnerabilidade.                                                  |
| **Mitigação**                    | Medida utilizada para reduzir ou eliminar o risco associado a uma fraqueza ou vulnerabilidade.                  |
| **Secure Coding**                | Práticas de desenvolvimento utilizadas para reduzir a introdução de problemas de segurança.                     |
| **OWASP**                        | Organização que produz materiais e projetos relacionados à segurança de aplicações.                             |
| **OWASP Top 10**                 | Documento que apresenta os principais riscos de segurança em aplicações web.                                    |
| **CWE Top 25**                   | Lista das principais fraquezas de software destacadas pelo projeto CWE.                                         |
| **SSDF**                         | Framework do NIST com práticas para desenvolvimento seguro de software.                                         |
| **SQL Injection**                | Tipo de ataque no qual entradas controladas pelo usuário podem interferir na execução de consultas SQL.         |
| **XSS**                          | Vulnerabilidade relacionada à execução de conteúdo controlado por um atacante no contexto de uma aplicação web. |
| **Input Validation**             | Processo de verificar e restringir entradas recebidas por uma aplicação.                                        |
| **Secure Development Lifecycle** | Abordagem que incorpora segurança ao longo do ciclo de desenvolvimento de software.                             |


## Prompts Reutilizáveis — Segurança de Software e CWE

Os prompts abaixo foram desenvolvidos para apoiar futuras sessões de estudo, revisão e análise de segurança utilizando as fontes disponíveis no NotebookLM.

---

## 1. Aprender um novo conceito

```text
Explique [CONCEITO] utilizando prioritariamente as fontes
disponíveis neste notebook.

Estruture a resposta em:

1. definição;
2. objetivo;
3. como funciona;
4. exemplo prático;
5. possíveis consequências;
6. relação com outros conceitos;
7. erros comuns de interpretação.

Utilize linguagem adequada para alguém que está estudando
segurança de software e indique as fontes utilizadas.
```

---

## 2. Estudar uma CWE específica

```text
Analise a CWE [NÚMERO/NOME] com base nas fontes disponíveis.

Explique:

1. o que é;
2. por que acontece;
3. como aparece em código;
4. quais são suas consequências;
5. como pode ser identificada;
6. como pode ser explorada;
7. como pode ser mitigada;
8. como evitar sua introdução durante o desenvolvimento.

Finalize com um exemplo simples de código vulnerável e
uma versão corrigida.
```

---

## 3. Comparar conceitos

```text
Compare [CONCEITO A], [CONCEITO B] e [CONCEITO C].

Apresente:

- definição;
- finalidade;
- diferenças;
- semelhanças;
- relação entre eles;
- exemplo prático.

Finalize com uma explicação curta que facilite a memorização
das diferenças.
```

---

## 4. CWE vs CVE vs CVSS

```text
Explique a diferença entre CWE, CVE e CVSS.

Utilize um único cenário hipotético para demonstrar
como os três conceitos poderiam aparecer no mesmo caso.

Explique:

- qual representa a fraqueza;
- qual representa a vulnerabilidade;
- qual representa a avaliação de severidade;
- como os conceitos se relacionam.
```

---

## 5. Análise de código

```text
Analise o código abaixo sob a perspectiva de segurança.

Para cada possível problema encontrado, informe:

1. trecho problemático;
2. comportamento inseguro;
3. CWE relacionada, se aplicável;
4. justificativa da classificação;
5. possível impacto;
6. estratégia de mitigação;
7. exemplo de implementação mais segura.

Não classifique um problema como CWE sem justificar
a relação com a definição da CWE.

Código:

[INSIRA O CÓDIGO AQUI]
```

---

## 6. Revisão de conhecimento

```text
Faça uma revisão sobre [TEMA] utilizando as fontes
disponíveis neste notebook.

Primeiro apresente um resumo dos conceitos essenciais.

Depois faça 5 perguntas de revisão, começando pelas
mais fáceis e aumentando progressivamente a dificuldade.

Não apresente as respostas imediatamente.
Aguarde minha resposta antes de corrigir cada questão.
```

---

## 7. Aprendizado ativo

```text
Atue como um professor de segurança de software.

Quero estudar [TEMA].

Faça uma pergunta por vez e adapte a dificuldade de acordo
com minhas respostas.

Quando eu responder:

1. avalie minha resposta;
2. indique o que está correto;
3. indique o que está incorreto ou incompleto;
4. explique o conceito necessário;
5. faça a próxima pergunta.

Priorize compreensão e raciocínio em vez de memorização.
```

---

## 8. Entrevista técnica

```text
Atue como um entrevistador técnico especializado
em segurança de software.

Realize uma entrevista sobre CWE e desenvolvimento seguro.

Comece com perguntas básicas e aumente gradualmente
a dificuldade.

Inclua perguntas sobre:

- CWE;
- CVE;
- CVSS;
- OWASP;
- vulnerabilidades;
- análise de código;
- mitigação;
- secure coding.

Não forneça a resposta antes da minha tentativa.

Após cada resposta, avalie meu conhecimento e explique
como eu poderia responder melhor em uma entrevista real.
```

---

## 9. Identificar lacunas de conhecimento

```text
Com base nas minhas respostas anteriores sobre [TEMA],
identifique possíveis lacunas no meu conhecimento.

Classifique cada lacuna como:

- básica;
- intermediária;
- avançada.

Para cada uma:

1. explique o que parece estar faltando;
2. indique quais conceitos devo revisar;
3. proponha uma pergunta ou exercício para verificar
   se realmente compreendi o assunto.
```

---

## 10. Análise crítica das fontes

```text
Analise as fontes disponíveis neste notebook sobre [TEMA].

Identifique:

- pontos de concordância;
- diferenças de abordagem;
- conceitos que aparecem com maior frequência;
- possíveis ambiguidades;
- informações que podem ser facilmente confundidas;
- quais fontes são mais adequadas para cada tipo de informação.

Não invente informações que não estejam sustentadas
pelas fontes.
```

---

## 11. Criar mapa de relacionamento

```text
Explique como os seguintes conceitos se relacionam:

CWE
CVE
CVSS
OWASP Top 10
Vulnerabilidade
Exploit
Mitigação
Secure Coding
SSDF

Organize a explicação como uma cadeia de causa e efeito
e destaque quais conceitos não devem ser confundidos.
```

---

## 12. Revisão rápida antes de uma prova ou entrevista

```text
Faça uma revisão rápida sobre [TEMA].

Apresente:

- 5 conceitos essenciais;
- 5 diferenças que preciso saber;
- 5 erros comuns;
- 5 perguntas rápidas;
- 3 exemplos práticos;
- 1 resumo final de até 10 linhas.

Priorize os conceitos mais importantes para compreender
o assunto em vez de simplesmente memorizar definições.
```

---

## 13. Transformar teoria em prática

```text
Escolha uma CWE relevante e crie um pequeno exercício
prático para estudá-la.

O exercício deve conter:

1. contexto;
2. código ou cenário vulnerável;
3. tarefa de identificação;
4. CWE esperada;
5. perguntas sobre impacto;
6. tarefa de correção;
7. critérios para avaliar minha solução.

Não apresente a solução inicialmente.
```

---

## 14. Prompt de revisão final

```text
Com base em tudo que foi estudado sobre [TEMA],
crie uma revisão final.

Estruture em:

1. conceitos fundamentais;
2. conceitos intermediários;
3. relações entre conceitos;
4. principais CWEs relacionadas;
5. exemplos práticos;
6. estratégias de prevenção;
7. erros comuns;
8. perguntas para testar conhecimento.

Finalize indicando quais pontos eu deveria revisar
novamente antes de considerar o assunto dominado.
```

---

## Estratégia de utilização

Os prompts podem ser utilizados em diferentes etapas:

```text
Exploração
    ↓
"Explique [CONCEITO]"
    ↓
Aprofundamento
    ↓
"Compare [A] vs [B]"
    ↓
Aplicação
    ↓
"Analise este código"
    ↓
Revisão
    ↓
"Faça perguntas sobre [TEMA]"
    ↓
Avaliação
    ↓
"Identifique minhas lacunas"
    ↓
Revisão final
```

O objetivo não é utilizar a IA apenas para obter respostas,
mas utilizá-la como ferramenta de investigação, revisão,
questionamento e validação do conhecimento adquirido.
