# Programa de AppSec (Step-by-Step)

## Resumo
Este repositório reúne minhas anotações e experiências sobre a estruturação básica de um programa de AppSec. Ele sugere ferramentas open-source para cada fase do processo e combina automação com verificações manuais. O objetivo é expandir esse modelo para um guia prático, servindo como ponto de partida para quem deseja iniciar na área. O resumo abaixo não abordará processos específicos de **Cloud Security**.

---
## Índice

1. **Avaliação da Maturidade da Empresa**
2. **Treinamento e conscientização** 
3. **Levantamento de requisitos e Threat Modeling** 
4. **Análise Automatizada de Código** 
5. **Segurança de Infraestrutura como Código** 
6. **Monitoramento de APIs** 
7. **Análise Dinâmica de Segurança** 
8. **Code Review e Testes Manuais** 
9. **Monitoramento Contínuo e Resposta a Incidentes** 
10. **Pipelines e Relatórios de Vulnerabilidades** 
11. **Acordo de Níveis de Serviço (SLA)**
---

![app-sec](https://github.com/user-attachments/assets/941a2ec7-7bb1-4409-9a6f-980c592872f4)

## Esteira de Segurança no Desenvolvimento de Software

**⚡ Antes de iniciar o processo, é fundamental avaliar a criticidade do que está sendo desenvolvido. Isso permite determinar o nível de dedicação e energia necessários para os próximos passos, de acordo com essa avaliação.**

### 1. Avaliação da Maturidade da Empresa

- Antes de iniciar a implementação do programa, é fundamental avaliar o nível de maturidade da empresa em segurança.
- O **OWASP SAMM** é um framework que ajuda a medir o estágio atual da empresa e acompanhar sua evolução após a adoção do programa. Mais informações estão disponíveis em: [OWASP SAMM](https://owasp.org/www-project-samm/).

### 2. Treinamento e Conscientização

- Após a avaliação, é essencial capacitar as equipes sobre segurança em aplicações. Treinamentos contínuos aumentam a maturidade coletiva da equipe em relação às principais vulnerabilidades.
- O **OWASP Top Ten** fornece uma lista das vulnerabilidades mais exploradas a cada ano, sendo um excelente material de referência: [OWASP Top Ten](https://owasp.org/www-project-top-ten/).

### 3. Levantamento de Requisitos e Threat Modeling  

#### **Levantamento de Requisitos**
Na fase de construção de novas aplicações ou funcionalidades, é crucial definir os requisitos de segurança com base nos riscos envolvidos. Isso inclui identificar quais informações críticas precisam ser protegidas.

- O **ASVS (Application Security Verification Standard)** pode ser utilizado como um checklist para garantir que os principais controles de segurança sejam implementados desde o início do desenvolvimento.
- A documentação está disponível em: [ASVS OWASP](https://cheatsheetseries.owasp.org/IndexASVS.html).

#### **Threat Modeling**
O **Threat Modeling** permite identificar e mitigar ameaças antes que elas sejam exploradas, aplicando a abordagem **"Shift-Left"**, ou seja, integrando a segurança desde o início do desenvolvimento.

O processo segue estas etapas:

1. **Definir o escopo** e mapear os componentes e fluxos de dados do sistema.
2. **Identificar possíveis ameaças**, avaliando quais são mais críticas com base no impacto e na probabilidade.
3. **Pensar como um atacante**, explorando possíveis vulnerabilidades e fraquezas.
4. **Implementar medidas de segurança** para reduzir os riscos levantados, como autenticação forte, CAPTCHA, entre outras ações.
5. **Revisar e atualizar constantemente** o processo para acompanhar novas ameaças e mudanças no sistema.

### 4. Análise Automatizada de Código

#### **SAST (Static Application Security Testing) - Análise Estática de Código**
- O SAST é essencial para detectar vulnerabilidades no código antes da execução, prevenindo falhas de segurança e reduzindo custos com correções tardias. No entanto, é preciso atenção aos falsos positivos, que podem travar a pipeline de forma indevida, comprometendo a eficiência do processo.
- Além disso, a priorização das correções deve considerar o impacto no negócio, pois uma aplicação com poucas vulnerabilidades, mas essencial para a empresa, pode demandar mais atenção do que outra com um grande volume de falhas menos críticas.

- **Ferramentas utilizadas:**
  - **GitLeaks**: Detecção de credenciais e segredos expostos. (opensource)
  - **TruffleHog**: Busca por informações sensíveis em repositórios. (opensource)
  - **Semgrep**: Análise de padrões de código para vulnerabilidades. (opensource)

- **Integração com pipelines CI/CD para verificação contínua.**

### 5. Segurança de Infraestrutura como Código (IaC)
Com o crescimento da utilização da Infraestrutura como Código para automatizar a criação, configuração e gerenciamento de infraestrutura, algumas ferramentas ajudam a analisar as configurações de infraestrutura para identificar e corrigir vulnerabilidades, garantindo ambientes de execução e nuvem mais seguros.

- **Checkov**: Avaliação de configurações de infraestrutura para evitar vulnerabilidades. (opensource)
- **Trivy**: Scanner de segurança que analisa imagens de contêiner, repositórios de código e pacotes do sistema. (opensource)

### 6. Monitoramento de APIs
O monitoramento de APIs é essencial para detectar vulnerabilidades, analisar tráfego e garantir a segurança das comunicações entre serviços.

- **Ferramenta utilizada:**
  - **Metlo**: Segurança contínua e análise de tráfego de APIs. (opensource)

### 7. Análise Dinâmica de Segurança (DAST)
O **DAST** é uma abordagem essencial para identificar vulnerabilidades em aplicações enquanto estão em execução, simulando ataques reais para detectar falhas de segurança que não seriam visíveis apenas com análise estática.

- **DAST Automatizado:**
  - Testes dinâmicos para identificação de vulnerabilidades em execução.
  - **Ferramentas utilizadas:**
    - **OpenVAS**: Análises automatizadas de segurança.
    - **OWASP ZAP**: Teste de segurança web dinâmico.
    - **Nuclei**: Scanner baseado em templates para identificação de vulnerabilidades.

### 8. Code Review e Testes Manuais
Além dos processos automatizados nos passos anteriores, a revisão manual do código e os testes manuais desempenham um papel fundamental no programa de AppSec. Muitas vulnerabilidades podem passar despercebidas pelas ferramentas automatizadas, tornando essencial a análise humana para uma segurança mais robusta.

- **Code Review:** Revisão de código manual para identificar falhas não detectadas por ferramentas.
- **Pentest:** Testes de penetração para simular ataques reais. Algumas ferramentas open-source ou disponíveis na versão community usadas nesses contextos:
  - **API Pentesting**: Postman, Insomnia
  - **Web App Pentesting**: Burp Suite, Nmap, Wfuzz, Amass, Nikto
  - **Mobile App Pentesting**: Frida, MobSF, JADX, Objection, APKTool, adb

### 9. Monitoramento e Resposta a Incidentes
Identifica padrões recorrentes de falhas, como erros de autenticação, acessos suspeitos, execuções inesperadas de código e exceções frequentes na aplicação, ajudando a responder incidentes e minimizando o tempo de detecção e mitigação. Embora o **Wazuh** seja uma excelente opção baseada em experiência prática, outras ferramentas podem ser utilizadas conforme as necessidades do ambiente.

- **Ferramenta Utilizada:**
  - **Wazuh**: Monitoramento contínuo de logs e resposta a incidentes via CSIRT (Computer Security Incident Response Team). (opensource)

### 10. Pipelines e Relatórios de Vulnerabilidades
Integrar as ferramentas ao máximo dentro de um processo automatizado de verificação via CI/CD, para evitar que algumas dessas fases sejam cumpridas apenas quando o desenvolvedor as acionar manualmente.

- **Geração de relatórios detalhados de vulnerabilidades.**
- **Priorização de correções, evitando falsos positivos.**

### 11. Acordo de Níveis de Serviço (SLA)
Acompanhar a correções das vulnerabilidades identificadas a partir de seu grau de prioridade.

- **Definição de prazos para tratamento de vulnerabilidades.**
- **Estabelecimento de políticas de mitigação conforme criticidade.**


---

**Última Atualização:** 17/02/2025


