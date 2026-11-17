# RELATÓRIO TÉCNICO DE AUDITORIA DE SEGURANÇA

**Projeto:** Auditoria de Autenticação com Medusa  
**Ambiente:** Laboratório controlado VirtualBox  
**Analista:** Alex Nogueira  
**Ferramenta principal:** Medusa 2.3  
**Alvo:** Metasploitable 2 — 192.168.56.101

## 1. Objetivo

Avaliar a segurança dos mecanismos de autenticação dos serviços FTP, SMB e aplicação web DVWA, utilizando testes controlados de credenciais em ambiente isolado.

## 2. Escopo

- Serviço FTP — porta 21.
- Serviço SMB — portas 139 e 445.
- Aplicação DVWA — HTTP, porta 80.
- Enumeração inicial com Nmap.
- Testes de autenticação com Medusa.

## 3. Resultados

### 3.1 FTP

Foi identificada uma credencial fraca no serviço FTP.

**Resultado:** autenticação bem-sucedida com credencial previsível.

**Risco:** Alto.

### 3.2 SMB

Foi identificada reutilização da mesma credencial no serviço SMB.

O módulo informou acesso permitido ao compartilhamento administrativo ADMIN$.

Também foram identificados SMBv1 habilitado e assinatura SMB desabilitada.

**Risco:** Alto.

### 3.3 DVWA

O módulo web-form do Medusa identificou uma credencial válida na aplicação DVWA, configurada com nível de segurança Low.

**Resultado:** ACCOUNT FOUND — SUCCESS.

**Risco:** Alto no contexto do laboratório.

## 4. Principais vulnerabilidades

- Senhas fracas ou padrão.
- Reutilização de credenciais entre serviços.
- Exposição de compartilhamentos SMB.
- Protocolo SMBv1 habilitado.
- Assinatura SMB desabilitada.
- Ausência de proteção suficiente contra tentativas automatizadas no formulário DVWA.

## 5. Recomendações

1. Adotar senhas fortes e exclusivas.
2. Implementar autenticação multifator.
3. Restringir o acesso aos serviços FTP e SMB.
4. Desabilitar SMBv1.
5. Habilitar assinatura SMB conforme compatibilidade.
6. Desabilitar acessos anônimos desnecessários.
7. Implementar limitação de tentativas de autenticação.
8. Monitorar falhas e sucessos de login.
9. Utilizar protocolos seguros, como SFTP.

## 6. Conclusão

Os testes demonstraram riscos relevantes relacionados ao gerenciamento de credenciais e à configuração dos serviços analisados.

O laboratório permitiu praticar reconhecimento de serviços, auditoria de autenticação, análise de resultados e elaboração de recomendações técnicas.

**Observação:** os resultados são restritos ao ambiente de laboratório e não representam uma avaliação de sistemas em produção.

**Alex Nogueira**  
Analista de Segurança da Informação
