# Zabbix-Jira

Integração Zabbix > JIRA

Link referência: Browse Zabbix / Zabbix - ZABBIX GIT

1°:

 Ativar a mídia JIRA Service Desk que encontra-se na aba “Administração" - "Mídia” no front-end ZABBIX - tipos de mídia”


2°:

 Configurando webhook no Zabbix
 
1. Antes de configurar um Webhook do Jira Service Desk, é recomendável configurar uma macro global "{$ZABBIX.URL}" contendo uma URL para o frontend do Zabbix.
Por exemplo, esta macro pode ser usada para preencher o campo personalizado do Jira Service Desk com um URL para informações ou gráfico do evento.

2. Na seção "Administração -> Tipos de mídia", importe o arquivo media_jira_servicedesk.xml

3. Abra o tipo de mídia do Jira Service Desk recém-adicionado e substitua todos pelos seus valores. Os seguintes parâmetros são necessários:

jira_url - URL real da sua instância do Jira Service Desk,
jira_user - Login do usuário do Jira Service Desk,
jira_password - senha ou token de API (para instalações do Jira Service Desk Cloud, um token de API pode ser obtido em https://id.atlassian.com/manage/api-tokens),
jira_servicedesk_id - ID numérico do seu Jira Service Desk (não confundir com um ID de projeto ou uma chave do Service Desk!),
jira_request_type_id - ID numérico do seu RequestType do Jira Service Desk.

Criar a variável criada: jira_request_key; -  Esta variável permite ao Zabbix conhecer o número de chamado


Observação: Por padrão, o webhook não usa os campos personalizados do Jira Service Desk. Para exportar informações para o campo personalizado do Jira Service Desk, adicione um parâmetro com o ID do campo personalizado como uma chave (se precisar de ajuda para encontrar o ID do campo personalizado, consulte esta página na documentação do Jira Service Desk).

Perspectiva JIRA:


A variável jira_servicedesk_id; foi atribuído em x (De acordo com seu Projeto no Jira)

A variável jira_request_type_id; foi atribuído em XX (é a "Report a System Problem")

jira_url, foi atribuído o valor: https://URL.atlassian.net

jira_user, foi atribuído o valor:  sdcoreteam@seudominio.com.br 

jira_password, token gerado desde o Api do Jira.

jira_request_key, foi atribuído a macro: {EVENT.TAGS.INC}


3°:

Ativar o uso da mídia JIRA Service Desk para um usuário na aba "Users" - Mídia" no ZABBIX

4°:

 Criar e ativar uma ação de notificação na aba configuração - ações
 - Selecione o user atrelado a mídia Jira Service Desk

5°:

Seguir na opção açõs e configurar os grupos que farão parte do registro automático


6°:

 Categorizar os registros que serão encaminhados para JIRA

Acessar o front-end Zabbix;

Selecionar a opção Administração;

Selecionar a opção Mídia;

Selecionar a mídia “Jira ServiceDesk”

Criar o parâmetro {TRIGGER.HOSTGROUP.NAME} 

Observação: Lembrando que para funcionalidade do parâmetro {TRIGGER.HOSTGROUP.NAME} , é necessário a criação do customfield na ferramenta JIRA

7°:

 Definir o intervalo que os registros serão encaminhados para o JIRA

Acessar o front-end;

Selecionar a opção “configuração”;

Selecionar a opção ações;

Criar um intervalo na opção ação;

