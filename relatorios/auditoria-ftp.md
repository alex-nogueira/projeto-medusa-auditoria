# Auditoria FTP — Metasploitable 2

## Identificação
- Alvo: 192.168.56.101
- Serviço: FTP
- Porta: 21
- Servidor: vsFTPd 2.3.4

## Ferramenta
- Medusa 2.3
- Módulo: ftp
- Execução controlada com lista de 3 usuários e 4 senhas.

## Resultado
- Status: ACCOUNT FOUND
- Usuário: msfadmin
- Senha: [REDACTED]
- Resultado: SUCCESS

## Análise
Foi identificada uma credencial fraca, com senha igual ao nome
da conta. A situação demonstra risco de acesso não autorizado.

## Recomendações
- Utilizar senhas fortes e exclusivas.
- Desabilitar contas desnecessárias.
- Restringir o acesso ao FTP.
- Preferir SFTP ou FTPS conforme a necessidade.
- Monitorar tentativas de autenticação.
- Implementar bloqueio ou limitação de tentativas.

## Observação
Teste realizado exclusivamente em laboratório isolado.
