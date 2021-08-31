# dalene
Monitorar arquivo/diretórios gerando logs, com respostas a incidentes
https://youtu.be/XdkSRb1cmIY

Objetivo principal é trazer maior facilidade de implementação e monitoramento de eventos e incidentes de segurança da informação nos servidores
Utiliza inode do kernel do linux, ou seja, monitora em tempo real, capaz de realizar resposta e gerar log da ação.
<br>
Utiliza inode do kernel do linux, ou seja, monitora em tempo real, capaz de realizar resposta e gerar log da ação.
<br>
Simples configuração
Setar o host(ou hosts)
Setar porta ssh
Setar usuário
Você configura qual servidor irá ser monitorado, o sistema o acessa via ssh, é possível selecionar vários servidores desde que seja mesma porta e usuário.
# Dalene

Aqui você diz onde quer salvar os logs que serão gerados.
Logs de monitoramento serão todos que você configurar para monitorar e suas ações.
Logs eventos são todos logs que o sistema suspeita ser malicioso ou não esperado(você pode inserir sua própria lista de eventos não esperados/aprovados no servidor).

Aqui você adiciona os caminhos e arquivos que deseja monitorar.(pode adicionar um arquivo contendo vários caminhos e arquivos). Esses arquivos serão monitorados e qualquer ação que você selecionou for feita neles, será ativado e acionado registro de log e ação. (imagine um ataque hacker dentro do servidor, no momento que ele visualizar,editar,apagar,criar um arquivo ou diretório será gerado um log e realizado uma resposta em tempo real.
Você seleciona os eventos que deseja monitorar ex: se arquivo for modificado, for acessado, data e hora, acessado por quem, movido, deletado, se próprio apagou, etc… Veja documentação.
Também é possível adicionar uma lista pronta para poupar tempo.
Você pode adicionar suas próprias váriaveis de evento, selecione “sim” caso deseje.

Setado variáveis suspeitas. Aquivos com final ou nome (php5, pHp,elf,aspx,webshell..) são padrões em ataques hackers, então monitorar esses arquivos quando forem criados/editados/adicionados/modificados é uma ação inteligente.

Neste exemplo, o hacker ou colaborador mal intencionado consegue acesso ao servidor, sendo assim baixa uma WEBshell PHP, e após alguns instantes o acessa via web.
Nos log como podemos ver foi capturado o momento exato que o arquivo foi criado e depois o momento que foi acessado. Gerado log no log de eventos, e como resposta bloqueado acesso via ssh e encaminhado alarme para e-mail para o responsável.

Com estas ideias é possível criar vários cenários fortalecendo a importância deste monitoramento.

# Descrição de eventos

IN_ACCESS Arquivo foi acessado (leitura) (*)
IN_ATTRIB Metadados alterados (permissões, carimbos de data / hora, atributos estendidos, etc.) (*)
IN_CLOSE_WRITE O arquivo aberto para gravação foi fechado (*)
IN_CLOSE_NOWRITE Arquivo não aberto para escrita foi fechado (*)
IN_CREATE Arquivo / diretório criado no diretório monitorado (*)
IN_DELETE Arquivo / diretório excluído do diretório monitorado (*)
IN_DELETE_SELF O monitorado arquivo / diretório foi excluído
O IN_MODIFY arquivo foi modificado (*)
IN_MOVE_SELF O observado arquivo / diretório foi movido
IN_MOVED_FROM Arquivo movido para fora do diretório monitorado (*)
IN_MOVED_TO Arquivo movido para o diretório monitorado (*)
IN_OPEN Arquivo foi aberto (*) 

O IN_ALL_EVENTS símbolo é definido como uma máscara de bits de todos os eventos acima. Dois símbolos de conveniência adicionais são IN_MOVE , que é um combinação de IN_MOVED_FROM e IN_MOVED_TO e IN_CLOSE que combina IN_CLOSE_WRITE e IN_CLOSE_NOWRITE
