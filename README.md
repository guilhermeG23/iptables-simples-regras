# iptables-simples-regras
Aprender o simples de iptables

### Iptables simples

### Três politicas
* INPUT -> O que entra, oque acessa o host
* FORWARD -> Meio do caminho, um meio de acesso
* OUTPUT -> O que sai, acesso do host a algum alvo

### Policy
* É a permissão, essa deve ser a ultima alteração a ser feita no sistema, ela é aplicada sobre as três politicas acima

### Conceito de loopback
* Permitir comunicação com os serviços internos

### Conceito de níveis
* Regras mais gerais devem ser prioridade e depois seguir para regras mais especificas, isso evita custo de processamento em maioria dos cenários, claro que se deve configurar conforme a necessidade

### Conceito de estado
* O iptables se zera toda vez que o sistema se reinicia, assim é necessário manter essas regras criadas 

### Salvar as regras atuais
iptables-save > saida

### Restaurar as regras
iptables-restore < saida

### Listar o estado das regras do iptables
iptables -L

### Mostra em detalhes as pliticas listadas
iptables -L -n

### Mostra o estado das conexões com cada politica
iptables -L -v

### Limpar o iptables
iptables -F

### Deletar regra em especifico
iptables -D <politica> <numero da politica = nivel>
### Ex:
iptables -D INPUT 1

### Criar uma regra
iptables -A <politica> -p <protocolo> -d <rede ou ip> -dport <porta> -j <tipo de resposta>
### Ex:
iptables -A INPUT -p tcp --dport 80 -j ACCEPT

### Criar uma regra para ser colocada em derterminado nivel
iptables -I INPUT 1 -p tcp --dport 80 -j DROP
