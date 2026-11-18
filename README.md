# 🔐 Medusa Authentication Security Audit

![Status](https://img.shields.io/badge/status-conclu%C3%ADdo-brightgreen)
![Focus](https://img.shields.io/badge/focus-authentication%20security-red)
![Environment](https://img.shields.io/badge/environment-isolated%20lab-blue)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

**Security Assessment | SOC Analyst Portfolio | Information Security**

Projeto prático de auditoria de segurança desenvolvido em laboratório virtual isolado, utilizando **Kali Linux**, **Metasploitable 2**, **DVWA**, **Nmap** e **Medusa**.

O objetivo foi avaliar mecanismos de autenticação, identificar credenciais fracas, verificar configurações inseguras e documentar vulnerabilidades em serviços de rede e aplicações web.

---

## 📑 Índice

- [🇧🇷 Português](#-português)
  - [Sobre o projeto](#-sobre-o-projeto)
  - [Objetivos](#-objetivos)
  - [Ambiente de laboratório](#-ambiente-de-laboratório)
  - [Ferramentas utilizadas](#️-ferramentas-utilizadas)
  - [Metodologia de auditoria](#-metodologia-de-auditoria)
  - [Comandos utilizados](#-comandos-utilizados)
  - [Principais descobertas](#-principais-descobertas)
  - [Recomendações de segurança](#️-recomendações-de-segurança)
  - [Principais aprendizados](#-principais-aprendizados)
  - [Estrutura do projeto](#-estrutura-do-projeto)
  - [Segurança e responsabilidade](#-segurança-e-responsabilidade)
- [🇺🇸 English](#-english)
- [👨‍💻 Author](#-author)
- [📄 .gitignore recomendado](#-gitignore-recomendado)

---

## 🇧🇷 Português

### 📌 Sobre o projeto

Este projeto demonstra a execução de testes controlados de autenticação em um ambiente de laboratório, com foco na identificação de falhas de segurança em serviços **FTP**, **SMB** e aplicações web.

A atividade foi desenvolvida com finalidade educacional, permitindo praticar técnicas de reconhecimento, enumeração, auditoria de autenticação, análise de vulnerabilidades e elaboração de relatórios técnicos.

### 🎯 Objetivos

- Identificar serviços e portas disponíveis no sistema-alvo.
- Avaliar a segurança da autenticação FTP.
- Identificar configurações inseguras no protocolo SMB.
- Verificar a reutilização de credenciais entre serviços.
- Avaliar a proteção de autenticação de uma aplicação web.
- Documentar os resultados e propor medidas corretivas.

### 🧪 Ambiente de laboratório

| Componente | Configuração |
|---|---|
| Sistema de auditoria | Kali Linux |
| Sistema-alvo | Metasploitable 2 |
| Aplicação web | DVWA |
| Ferramenta de auditoria | Medusa 2.3 |
| Reconhecimento | Nmap |
| Enumeração SMB | SMBClient |
| Virtualização | Oracle VirtualBox |
| Rede | Host-only |
| IP do sistema-alvo | `192.168.56.101` |
| IP do sistema de auditoria | `192.168.56.102` |

**Topologia:** ambiente virtual isolado, com comunicação entre as máquinas pela rede Host-only.

### 🛠️ Ferramentas utilizadas

- **Kali Linux:** sistema operacional utilizado para os testes.
- **Nmap:** reconhecimento de portas e serviços.
- **Medusa:** auditoria controlada de autenticação.
- **SMBClient:** enumeração de compartilhamentos SMB.
- **Metasploitable 2:** máquina virtual vulnerável utilizada como alvo.
- **DVWA:** aplicação web vulnerável para testes educacionais.
- **VirtualBox:** plataforma de virtualização.

### 🔎 Metodologia de auditoria

O projeto foi desenvolvido em cinco etapas:

#### 1. Reconhecimento

Identificação dos serviços e portas disponíveis no sistema-alvo utilizando Nmap.

#### 2. Auditoria FTP

Verificação controlada da segurança da autenticação FTP utilizando Medusa.

> **Resultado:** identificação de credencial fraca e autenticação bem-sucedida.

#### 3. Auditoria SMB

Enumeração de compartilhamentos, identificação de configurações inseguras e teste controlado de autenticação SMB.

> **Resultado:** identificação de SMBv1 habilitado, assinatura SMB desabilitada, acesso anônimo à listagem de compartilhamentos e acesso permitido ao compartilhamento administrativo `ADMIN$` mediante autenticação.

#### 4. Auditoria Web — DVWA

Teste controlado do formulário **Brute Force** da aplicação DVWA, configurada com nível de segurança **Low**.

> **Resultado:** identificação automatizada de credencial válida no formulário de autenticação.

#### 5. Análise e documentação

Registro dos resultados, avaliação dos riscos e elaboração de recomendações técnicas.

### 💻 Comandos utilizados

**Reconhecimento SMB com Nmap**

```bash
nmap -p139,445 --script smb-protocols,smb-security-mode,smb-enum-shares 192.168.56.101
```

**Enumeração de compartilhamentos SMB**

```bash
smbclient -L //192.168.56.101 -N
```

Os testes de autenticação FTP, SMB e DVWA foram executados com **Medusa 2.3**, utilizando os módulos correspondentes e listas controladas para o laboratório.

> ⚠️ Por segurança, os comandos contendo credenciais e os arquivos brutos de execução não são disponibilizados publicamente.

### 📊 Principais descobertas

#### FTP

- Identificação de credencial fraca.
- Autenticação bem-sucedida durante o teste controlado.
- Risco de acesso não autorizado em caso de exposição do serviço.
- **Classificação:** Alto no contexto do laboratório.

#### SMB

- Portas `139` e `445` abertas.
- SMBv1 habilitado.
- Assinatura SMB desabilitada.
- Acesso anônimo à listagem de compartilhamentos.
- Reutilização de credencial identificada entre FTP e SMB.
- Acesso permitido ao compartilhamento administrativo `ADMIN$` mediante autenticação.
- **Classificação:** Alto no contexto do laboratório.

#### DVWA

- Aplicação configurada com nível de segurança **Low**.
- Identificação automatizada de credencial válida.
- Demonstração de risco associado a tentativas automatizadas de autenticação.
- **Classificação:** Alto no contexto do laboratório.

> As classificações representam os resultados observados no ambiente educacional e não substituem uma avaliação formal de risco em ambiente de produção.

### 🛡️ Recomendações de segurança

Com base nos resultados encontrados, foram propostas as seguintes medidas:

- Utilizar senhas fortes e exclusivas para cada serviço.
- Implementar autenticação multifator sempre que possível.
- Desabilitar protocolos SMB obsoletos, como SMBv1.
- Habilitar assinatura SMB conforme compatibilidade do ambiente.
- Restringir acessos anônimos aos compartilhamentos.
- Revisar permissões administrativas e privilégios de usuários.
- Implementar limitação de tentativas de autenticação.
- Monitorar eventos de autenticação bem-sucedidos e malsucedidos.
- Preferir protocolos seguros, como SFTP, em substituição ao FTP tradicional.

### 📚 Principais aprendizados

- Reconhecimento de serviços de rede com Nmap.
- Auditoria de autenticação utilizando Medusa.
- Enumeração de compartilhamentos SMB.
- Identificação de credenciais fracas e reutilizadas.
- Análise de configurações inseguras.
- Avaliação de riscos de autenticação web.
- Elaboração de relatórios técnicos.
- Aplicação de boas práticas de segurança da informação.

### 📁 Estrutura do projeto

```text
projeto-medusa-auditoria/
│
├── README.md
├── .gitignore
├── LICENSE
│
├── images/
│   └── (prints do laboratório)
│
└── relatorios/
    ├── auditoria-dvwa.md
    ├── auditoria-ftp.md
    ├── auditoria-smb.md
    └── relatorio-final.md
```

> Os arquivos brutos de execução e as listas de teste foram mantidos fora do repositório público por segurança.

### 🔐 Segurança e responsabilidade

Todos os testes foram executados exclusivamente em ambiente virtual próprio, isolado e autorizado, com finalidade educacional.

- Não foram realizados testes contra sistemas de terceiros.
- Credenciais, cookies, sessões e arquivos brutos contendo informações sensíveis foram mantidos fora do repositório público.

---

## 🇺🇸 English

### 📌 About the project

This project demonstrates a practical authentication security assessment conducted in an isolated VirtualBox laboratory.

The assessment focused on identifying weak credentials, credential reuse, insecure SMB configurations and authentication weaknesses in a web application.

### 🎯 Objectives

- Identify network services and open ports.
- Assess FTP authentication security.
- Identify insecure SMB configurations.
- Detect credential reuse between services.
- Evaluate web application authentication.
- Document findings and recommend security improvements.

### 🧪 Laboratory environment

| Component | Configuration |
|---|---|
| Audit system | Kali Linux |
| Target system | Metasploitable 2 |
| Web application | DVWA |
| Main audit tool | Medusa 2.3 |
| Network discovery | Nmap |
| SMB enumeration | SMBClient |
| Virtualization | Oracle VirtualBox |
| Network | Host-only |

### 🛠️ Tools

- Kali Linux
- Nmap
- Medusa 2.3
- SMBClient
- Metasploitable 2
- DVWA
- Oracle VirtualBox

### 🔎 Audit methodology

The project was conducted in five stages:

1. **Reconnaissance:** identification of available network services and ports using Nmap.
2. **FTP assessment:** controlled authentication testing using Medusa.
3. **SMB assessment:** share enumeration, security configuration analysis and authentication testing.
4. **Web assessment:** controlled Brute Force module testing against DVWA configured at Low security level.
5. **Analysis and documentation:** review of findings, risk assessment and technical recommendations.

### 📊 Key findings

#### FTP

- Weak credentials identified.
- Successful authentication during controlled testing.

#### SMB

- SMBv1 enabled.
- SMB signing disabled.
- Anonymous share listing identified.
- Credential reuse between FTP and SMB confirmed.
- Authenticated access to the administrative `ADMIN$` share confirmed.

#### DVWA

- Application configured at Low security level.
- Valid credentials identified through controlled automated authentication testing.

### 🛡️ Security recommendations

- Enforce strong and unique passwords.
- Implement multi-factor authentication.
- Disable obsolete protocols such as SMBv1.
- Enable SMB signing where supported.
- Restrict anonymous access to network shares.
- Review administrative privileges.
- Implement authentication rate limiting.
- Monitor authentication events.
- Prefer secure protocols such as SFTP.

### 📚 Key learning outcomes

- Network reconnaissance and service enumeration.
- Authentication security assessment.
- SMB share enumeration.
- Weak password and credential reuse identification.
- Vulnerability analysis and risk assessment.
- Technical report writing.
- Security best practices.

### 🔐 Ethical disclaimer

All tests were conducted exclusively in an isolated and authorized educational laboratory.

No third-party systems were targeted. Sensitive credentials, session cookies and raw execution files were excluded from the public repository.

---

## 👨‍💻 Author

**Alex Nogueira**

Information Security | SOC Analyst | Threat Intelligence

- **GitHub Repository:** [projeto-medusa-auditoria](https://github.com/alex-nogueira/projeto-medusa-auditoria)

**Project focus:** Authentication Security Assessment | Network Security | Vulnerability Analysis

> Educational project developed for practical learning and professional portfolio purposes.

---

⭐ Se este projeto foi útil para seus estudos, considere dar uma estrela no repositório!
