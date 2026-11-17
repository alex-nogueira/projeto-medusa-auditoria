# 🔐 Medusa Authentication Security Audit

**Security Assessment | SOC Analyst Portfolio**

A practical security auditing project conducted in an isolated VirtualBox laboratory using Kali Linux, Metasploitable 2, Medusa and DVWA.

# 🇧🇷 Português

## Sobre o projeto

Este projeto demonstra testes controlados de autenticação e identificação de configurações inseguras em serviços de rede e aplicações web.

## Ambiente de laboratório

| Componente | Configuração |
|---|---|
| Sistema de auditoria | Kali Linux |
| Sistema alvo | Metasploitable 2 |
| Aplicação web | DVWA |
| Ferramenta principal | Medusa 2.3 |
| Reconhecimento | Nmap |
| Virtualização | VirtualBox |
| Rede | Host-only |

## Atividades realizadas

- Reconhecimento de serviços com Nmap.
- Auditoria de autenticação FTP.
- Auditoria de autenticação SMB.
- Identificação de reutilização de credenciais.
- Teste controlado de formulário web DVWA.
- Análise de resultados e recomendações.

## Principais descobertas

- Credenciais fracas em FTP.
- Reutilização de credenciais entre serviços.
- SMBv1 habilitado.
- Assinatura SMB desabilitada.
- Identificação automatizada de credencial no DVWA.

## Estrutura

```text
projeto-medusa/
├── evidencias/
├── relatorios/
│   ├── auditoria-dvwa.md
│   ├── auditoria-ftp.md
│   ├── auditoria-smb.md
│   └── relatorio-final.md
└── README.md
```

## Aviso

Todos os testes foram realizados exclusivamente em ambiente próprio, isolado e autorizado para fins educacionais.

# 🇺🇸 English

## About

A practical authentication security assessment performed in an isolated VirtualBox laboratory.

## Tools

- Kali Linux
- Metasploitable 2
- DVWA
- Medusa 2.3
- Nmap
- VirtualBox

## Activities

- Network service discovery.
- FTP authentication assessment.
- SMB authentication assessment.
- Credential reuse identification.
- Web form authentication testing.
- Security findings and remediation recommendations.

## Disclaimer

All activities were conducted in an isolated and authorized educational environment.

---

**Author:** Alex Nogueira  
**Focus:** Information Security | SOC Analyst | Threat Intelligence
