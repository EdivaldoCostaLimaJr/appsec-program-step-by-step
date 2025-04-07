# Programa de AppSec: Guia Prático e Progressivo

## Resumo

Este repositório reúne minhas anotações e experiências pessoais sobre como estruturar um programa de segurança no ciclo de desenvolvimento de software (AppSec) a partir de artigos e aulas que assisti.

A proposta é oferecer um modelo simples de implementação de um programa de app-sec de forma prática, baseado em ferramentas open-source, combinando automação e análises manuais. O objetivo é evoluir este conteúdo para um guia mais robusto, servindo como ponto de partida para profissionais da área.

**Nota:** Este guia não cobre aspectos específicos de *Cloud Security*.

---

## Índice

1. [Avaliação da Maturidade da Empresa](#1-avaliação-da-maturidade-da-empresa)  
2. [Treinamento e Conscientização](#2-treinamento-e-conscientização)  
3. [Levantamento de Requisitos e Threat Modeling](#3-levantamento-de-requisitos-e-threat-modeling)  
4. [Análise Automatizada de Código](#4-análise-automatizada-de-código)  
5. [Segurança de Infraestrutura como Código](#5-segurança-de-infraestrutura-como-código)  
6. [Monitoramento de APIs](#6-monitoramento-de-apis)  
7. [Análise Dinâmica de Segurança](#7-análise-dinâmica-de-segurança)  
8. [Code Review e Testes Manuais](#8-code-review-e-testes-manuais)  
9. [Monitoramento Contínuo e Resposta a Incidentes](#9-monitoramento-contínuo-e-resposta-a-incidentes)  
10. [Pipelines e Relatórios de Vulnerabilidades](#10-pipelines-e-relatórios-de-vulnerabilidades)  
11. [Acordo de Níveis de Serviço (SLA)](#11-acordo-de-níveis-de-serviço-sla)

---

![app-sec](https://github.com/user-attachments/assets/941a2ec7-7bb1-4409-9a6f-980c592872f4)

## Esteira de Segurança no Desenvolvimento de Software

Antes de iniciar o processo, é fundamental avaliar a criticidade do que está sendo desenvolvido. Isso permite determinar o nível de dedicação e energia necessários para os próximos passos.

### 1. Avaliação da Maturidade da Empresa

- Avaliar o nível atual de maturidade em segurança é essencial para traçar uma estratégia eficaz.
- O [OWASP SAMM](https://owasp.org/www-project-samm/) é um framework útil para essa finalidade, permitindo medições consistentes ao longo do tempo.

### 2. Treinamento e Conscientização

- A capacitação contínua das equipes promove uma cultura de segurança sólida.
- O [OWASP Top Ten](https://owasp.org/www-project-top-ten/) é um excelente ponto de partida para entender as principais vulnerabilidades.

### 3. Levantamento de Requisitos e Threat Modeling

#### Levantamento de Requisitos

- Define os controles necessários com base no risco e nas informações críticas do sistema.
- O [ASVS da OWASP](https://cheatsheetseries.owasp.org/IndexASVS.html) pode ser usado como checklist de segurança.

#### Threat Modeling

Etapas principais:

1. Definir escopo e mapear fluxos de dados.
2. Identificar ameaças e avaliar criticidade.
3. Raciocinar como um atacante.
4. Definir medidas de mitigação.
5. Atualizar o modelo regularmente.

### 4. Análise Automatizada de Código

#### SAST (Static Application Security Testing)

- Permite identificar vulnerabilidades antes da execução do código.
- Deve ser integrado à pipeline CI/CD para feedback contínuo.
- Cuidado com falsos positivos que podem travar processos.

**Ferramentas recomendadas:**

- [GitLeaks](https://github.com/gitleaks/gitleaks)
- [TruffleHog](https://github.com/trufflesecurity/trufflehog)
- [Semgrep](https://semgrep.dev/)

### 5. Segurança de Infraestrutura como Código

Adoção de ferramentas que analisam configurações de infraestrutura para evitar vulnerabilidades desde a fase de provisionamento.

**Ferramentas recomendadas:**

- [Checkov](https://www.checkov.io/)
- [Trivy](https://github.com/aquasecurity/trivy)

### 6. Monitoramento de APIs

Monitorar tráfego e identificar vulnerabilidades em tempo real nas APIs.

**Ferramenta recomendada:**

- [Metlo](https://www.metlo.com/)

### 7. Análise Dinâmica de Segurança (DAST)

Simula ataques em aplicações em execução para identificar vulnerabilidades que não são detectadas na análise estática.

**Ferramentas recomendadas:**

- [OWASP ZAP](https://owasp.org/www-project-zap/)
- [OpenVAS](https://www.openvas.org/)
- [Nuclei](https://github.com/projectdiscovery/nuclei)

### 8. Code Review e Testes Manuais

Complementam a automação ao explorar vulnerabilidades complexas que requerem julgamento humano.

**Práticas recomendadas:**

- Code review manual com foco em segurança.
- Pentests direcionados.

**Ferramentas úteis:**

- API: Postman, Insomnia
- Web: Burp Suite, Nmap, Nikto, Wfuzz, Amass
- Mobile: Frida, MobSF, JADX, Objection, APKTool, adb

### 9. Monitoramento Contínuo e Resposta a Incidentes

Análise contínua de logs e eventos para detectar comportamentos anômalos e responder rapidamente a incidentes.

**Ferramenta recomendada:**

- [Wazuh](https://wazuh.com/): SIEM open-source com capacidades de detecção e resposta.

### 10. Pipelines e Relatórios de Vulnerabilidades

- Integração das ferramentas de segurança às pipelines CI/CD.
- Geração de relatórios com priorização baseada em criticidade.
- Minimizar falsos positivos para garantir fluidez no desenvolvimento.

### 11. Acordo de Níveis de Serviço (SLA)

- Estabelecimento de prazos para correção de vulnerabilidades com base em sua severidade.
- Apoia a governança e a responsabilização dentro do ciclo de vida da aplicação.

---



**Última Atualização:** 07/04/2025


