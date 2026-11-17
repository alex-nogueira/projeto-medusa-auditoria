
# Relatório de Auditoria — DVWA Brute Force

## 1. Identificação
- Alvo: 192.168.56.101
- Aplicação: Damn Vulnerable Web Application (DVWA)
- Módulo: Brute Force
- Nível de segurança: Low
- Ferramenta: Medusa 2.3

## 2. Metodologia
Foi realizado teste controlado de autenticação utilizando o módulo web-form do Medusa, com método HTTP GET e lista reduzida de senhas.

## 3. Evidência
- Usuário identificado: admin
- Senha: [REDACTED]
- Resultado: SUCCESS
- Resposta: ACCOUNT FOUND

## 4. Vulnerabilidade identificada
A aplicação permitiu a identificação automatizada de uma credencial válida por meio de tentativas de autenticação.

## 5. Riscos
- Acesso não autorizado a contas.
- Uso de senhas padrão ou fracas.
- Ausência ou insuficiência de mecanismos contra tentativas automatizadas.

## 6. Recomendações
- Utilizar senhas fortes e exclusivas.
- Implementar limitação de tentativas.
- Adotar bloqueio temporário e monitoramento.
- Implementar MFA.
- Utilizar mecanismos de proteção contra automação.
- Evitar credenciais padrão.

## 7. Conclusão
O teste demonstrou que o formulário de autenticação do DVWA, configurado em nível Low, é suscetível à identificação automatizada de credenciais.
