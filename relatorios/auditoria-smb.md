# Auditoria SMB — Metasploitable 2

## Identificação
- Alvo: 192.168.56.101
- Portas: 139 e 445
- Serviço: Samba 3.0.20-Debian

## Reconhecimento
- SMBv1 habilitado
- Assinatura SMB desabilitada
- Compartilhamento tmp com acesso anônimo de leitura/escrita
- IPC$ com acesso anônimo identificado pelo Nmap

## Teste de autenticação
- Ferramenta: Medusa 2.3
- Módulo: smbnt
- Teste de reutilização de credencial identificada no FTP: realizado.
- Resultado: autenticação SMB bem-sucedida.
- Acesso ao compartilhamento administrativo ADMIN$: permitido.

## Recomendações
- Desabilitar SMBv1.
- Habilitar assinatura SMB conforme suporte do ambiente.
- Restringir acesso anônimo.
- Remover permissões desnecessárias de escrita.
- Revisar contas, senhas e privilégios.
- Monitorar eventos de autenticação.

## Ambiente
Teste realizado em laboratório isolado.

## Resultado da enumeração anônima

- Autenticação anônima: SUCCESS
- Listagem de compartilhamentos: SUCCESS
- Compartilhamentos identificados: tmp, opt, print$, IPC$ e ADMIN$
- Acesso anônimo confirmado para listagem.
- Permissões de leitura e escrita: aguardando validação específica.

## Resultado do teste de autenticação SMB

- Ferramenta: Medusa 2.3
- Módulo: smbnt
- Usuário: msfadmin
- Senha: [REDACTED]
- Autenticação: SUCCESS
- Acesso ao ADMIN$: Access Allowed

## Análise de segurança

Foi confirmada a reutilização da credencial identificada
na auditoria FTP.

A conta também possui acesso administrativo ao compartilhamento
ADMIN$, aumentando o impacto potencial do comprometimento.

## Classificação

Risco: ALTO

## Recomendações

- Utilizar senhas exclusivas para cada serviço.
- Remover privilégios administrativos desnecessários.
- Restringir o acesso ao compartilhamento ADMIN$.
- Desabilitar SMBv1.
- Habilitar assinatura SMB.
- Monitorar tentativas de autenticação e acessos administrativos.
