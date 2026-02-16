
Os seguintes elementos compõem um comando Linux:
- **CommandName** (nome do comando): a requisição que o usuário deseja executar;
- **Flag** (opção): serve para modificar a operação do comando. Ele pode ser incluído por meio de um ou dois hífens; e
- **Argument** (argumento): usado para adicionar informações à requisição. Não é obrigatório para todos os comandos.
---
# Gerenciamento de arquivos e diretórios

> **ls** - possibilita a visualização de todos os conteúdos contidos em um diretório. Para visualizar outros repositórios, é preciso escrever ls e incluir o caminho do diretório.
~~~~bash
ls /home/username/documents

# Mostra tudo "super comando"

ls -lah
~~~~
- **-R**: visualiza conteúdos dos subdiretórios
- **-l**: exibe uma lista detalhada (permissões, dono, tamanho e data de modificação)
- **-a**: mostra os arquivos ocultos (arquivos que começam com ponto)
- **-lh**: mostra o tamanho em KB, MB ou GB
- **-lt**: os arquivos modificados mais recentemente aparecem primeiro

> **cd** - usado para navegar entre diretórios e modificá-los.
~~~~bash
cd /home/usuario/documentos
~~~~
- **cd..** : para subir um diretório acima
- **cd ~**: para acessar a pasta do usuário logado
- **cd -**: para retornar para diretórios anteriores

> **pwd** - revela o caminho completo do seu diretório atual.
~~~~bash
pwd -L
~~~~
- **-L**: imprime o conteúdo da variável do ambiente
- **-P**: mostra o caminho real do diretório atual sem links simbólicos

> **mkdir** - para utilizar esse comando é necessário que o usuário tenha permissão para criar novas pastas. É usado para criar um ou mais diretórios abaixo do diretório local.

~~~~bash
mkdir novo_diretorio
~~~~
- **-p**: cria todos os níveis necessários de uma vez
~~~~bash
mkdir -p pasta1/pasta2/pasta3
~~~~
- **-m**: configura a permissão do diretório criado e cria pastas com base nessa permissão
~~~~bash
mkdir -m 700 segredo
~~~~

> **rmdir** - exclui permanentemente um diretório vazio.
- **-p**: utilizado para apagar um diretório e seus subdiretórios
- **-ignore-fail-on-non-empty**: faz com que o comando ignore o erro caso o diretório não esteja vazio
~~~~bash
rmdir [opções]
~~~~

> **rm** - apaga permanentemente todos os arquivos contidos em um diretório.
- **-i**: solicita a confirmação do sistema antes de fazer uma exclusão
- **-f**: permite que o sistema exclua arquivos sem solicitar confirmação
- **-r**: exclui arquivos e diretórios recursivamente
~~~~bash
rm nome_do_arquivo
~~~~

> **cp** - copia arquivos e diretórios, é necessário mencionar os nomes dos conteúdos que você deseja copiar, assim como a pasta para qual eles deverão ser enviados.
~~~~bash
cp arquivo.txt/diretorio_destino
~~~~

> **mv** - move ou renomeia arquivos e diretórios.
~~~~bash
mv arquivo.txt nova pasta/ ou mv antigo.txt novo.txt
~~~~

> **touch** - cria um arquivo vazio ou gera e modifica um registro de data e hora.
~~~~bash
touch novo.txt
~~~~

> **find** - utilizado para encontrar arquivos e diretórios de acordo com um critério específico, como tamanho e tipo.
~~~~bash
find [diretório][opção][ação]

# Encontra um arquivo específico no diretório atual e subpastas
# Use -iname para ignorar diferenças entre maiúsculas e minúsculas

find . -name "arquivo.txt"

# Lista apenas diretório (d) ou arquivos (a)

find /home/usuario -type d
find /home/usuario -type a

# Busca por tamanho

find / -size +100M

# Busca por tempo de modificação

find . -mtime -7

# Busca arquivos .tmp e os remove automaticamente

find . -name "*.tmp" -exec rm -rf {} \;
~~~~

> **stat** - visualiza informações detalhadas sobre os arquivos.
~~~~bash
stat arquivo.txt
~~~~
- **-t**: exibe os dados de forma simplificada

> **locate** - semelhante ao find, pois também localiza arquivos. É menos preciso, pois precisa de um banco de dados que seja atualizado com frequência.
~~~bash
locate arquivo.txt
~~~~

# Leitura e edição de arquivos

> **cat** - Visualiza, cria e relaciona conteúdos de arquivos.
~~~bash
cat texto.txt

# Mescla dois arquivos em um terceiro

cat parte1.txt parte2.txt > arquivo_completo.txt

# Adiciona conteúdo ao final do arquivo

cat arquivo_origem.txt >> arquivo_destino.txt
~~~~
- **-n**: numerar as linhas

> **less** - exibe grandes arquivos página por página, sendo muito utilizado por quem precisa analisar conteúdos grandes.
~~~bash
less arquivo.txt

# Ver a saída de outro comando paginada

ls -la /etc | less
~~~
- **-N**: exibe número de linhas
- **Setas (cima/baixo)**: sobe ou desce uma linha
- **Espaço**: desce uma página inteira
- **b**: volta uma página
- **G**: vai para o final do arquivo
- **g**: volta para o início do arquivo
- **/ + palavra**: pesquisa por um termo (aperta **n** para ir para a próxima ocorrência)
- **q**: sai do comando e volta para o prompt

> **head** - visualiza as primeiras 10 linhas de um arquivo, ou quantas linhas forem necessárias.
~~~~bash
head [opção][arquivo]

head -n 20 arquivo.txt

# Combinado comandos

ls -l | head
~~~~

> **tail** - a requisição tail mostra as 10 últimas linhas de um arquivo.
~~~bash
tail log.txt

tail -n 5 log.txt

# Modo espião (mantém o arquivo aberto e atualiza a tela automaticamente)

tail -f /var/log/syslog

# Mostra tudo a partir da linha 50

tail -n +50 arquivo.txt
~~~~
- **-f**: visualiza alterações em tempo real
- **-F**: monitorar um arquivo que pode ser deletado e recriado pelo sistema (como um log rotacionado). Ele continua tentando ler o arquivo mesmo que ele suma por um instante

> **nano** - permite que o usuário edite e gerencie arquivos por meio de um editor de texto.
~~~bash
nano texto.txt
~~~~
- **Ctrl + O**: salvar as alterações
- **Ctrl + X**: sair do editor
- **Ctrl + W**: buscar um texto
- **Ctrl + K**: recortar uma linha inteira
- **Ctrl + U**: colar uma linha inteira

> **echo** - empregado para exibir um texto no terminal, adicionar ou evitar uma nova linha e para automatizar tarefas por meio de scripts.
~~~bash
echo [opção][argumento]

# Exibir uma mensagem

echo "Olá, mundo!"

# Ver o valor de uma variável de ambiente

echo $USER
echo $PATH

# Criar um arquivo com texto rapidamente

echo "Texto de exemplo" > arquivo.txt

# Adicionar texto ao final de um arquivo

exho "Nova linha de log" >> logs.txt
~~~~
- **-n**: não adiciona uma nova linha após apresentar os argumentos
- **-e**: aciona a interpretação de sequências de escape de barra invertida
- **-E**: apresenta a opção padrão e desativa a interpretação dos escapes de barra invertida

> **wc** - "Word count", serve para contar palavras, linhas, caracteres além de também indicar o comprimento da maior linha de um texto
~~~bash
wc [opção] texto.txt
~~~~
- **-w**: contar a quantidade de palavras
- **-c**: contar a quantidade de caracteres
- **-l**: mostra o número de linhas
- **-m**: mostra o número de caracteres usando o formato Unicode
- **-L**: mostra o comprimento da maior linha do arquivo

> **cut** - extrai caracteres, bytes e seções de cada linha de um arquivo.
~~~bash
cut [opção] arquivo.txt

# Pegar apenas os nomes de usuário no arquivo /etc/passwd
# -d ":" define que os dois pontos são o separador
# -f diz para pegar o primeiro campo

cut -d ":" -f 1 /etc/passwd

# Pega apenas os primeiros 5 caracteres de cada linha

cut -c 1-5 arquivo.txt

# Pega do primeiro ao terceiro campo, usando espaço como separador

cut -d " " -f 1-3 arquivo.txt
~~~
- **-b**: seleciona apenas os bytes de cada linha
- **-c**: seleciona apenas os caracteres de cada linhas
- **-d**: define o delimitador
- **-f**: seleciona campos em cada linha

> **awk** - trata-se de um comando que na verdade é um canivete suíço, é uma linguagem de programação inteira voltada para processamento de dados e geração de relatórios.
~~~bash
awk [ação] arquivo

# Imprime colunas específicas, pegar a primeira e terceira coluna

awk '{print $1, $3}' lista.txt

# Filtrando por conteúdo, msotra apenas as linhas onde a segunda coluna é igual a 'Ativo'

awk '$2 == "Ativo" {print $0}' dados.txt

# Usando o ":" como delimitador específico

awk -F ":" '{print $1} /etc/passwd'

# Somar os valores da primeira coluna e mostrar o total no final

awk '{soma += $1} END {print soma}' valores.txt

# Filtrar pelo tamanho da linha, mostra as linhas que tenham mais de 80 caracteres

awk 'length($0) == 80' arquivo.txt
~~~

> **grep** - comando utilizado para encontrar uma palavra em um determinado conteúdo. Exibe todas as linhas que apresentam o mesmo padrão.
~~~bash
grep [termo] arquivo.txt

grep "erro" log.txt

# Ignora letras maiúsculas e minúsculas

grep -i "python" tutorial.txt

# Utilizado para filtrar a saída de outros comando

ps aux | grep "chrome"

ls -lah | grep ".pdf"
~~~
- **-i**: ignora letras maiúsculas e minúsculas
- **-r**: procura em todos os arquivos de uma pasta
- **-c**: quantas vezes uma palavra aparece
- **-v**: mostra tudo que não contém a palavra, inverter a busca, útil para limpar logs
- **-n**: mostra o número da linha

> **diff** - compara o conteúdo de dosa arquivos diferentes linha por linha.
~~~bash
diff arquivo1.txt arquivo2.txt

diff -r pasta1/ pasta2/
~~~
- **-q**: exibe apenas os arquivos que são diferentes, sem especificar as diferenças
- **-i**: deixa o comando diff indiferente para maiúsculas e minúsculas
- **-b**: passa a ignorar os espaços em branco como possíveis diferenças
- **-y**: mudança lado a lado
- **-r**: comparar diretórios
- Obs.: o comando "colordiff" apresenta as diferenças em verde e vermelho

> **tar** - utilizado para extrair e comprimir arquivos no formato tar.
~~~bash

# Sintaxe básica para comprimir arquivos

tar -cvf arquivo_comprimido.tar.gz arquivo.txt

# Sintaxe básixa para descomprimir arquivos

tar -xzvf
~~~

> **kill** - usado para encerrar (matar) processos.
~~~bash
# Para executar essa requisição, é necessário saber o número de processo (PID) que será interrompido

ps aux | grep nome_do_processo

kill [pid]

kill -15 PID

kill -SIGTERM PID
~~~
- **SIGTERM (15)**: sinal padrão, que solicita o encerramento normal do processo
- **SIGKILL (9)**: força o encerramento imediato, sem dar chance ao processo de se recuperar
- **SIGHUP (1)**: tradicionalmente usado para recarregar configurações
- **SIGSTOP (19)**: pausa a execução do processo
- **SIGCONT (18)**: continua a execução de um processo pausado

> **reboot** - reinicia o computador de maneira imediata.
~~~bash
reboot
~~~
- **-f**: força a reinicialização

> **uptime** - mostra a quanto tempo o sistema está em execução, a carga da CPU e quantos usuários estão logados nele.
~~~bash
uptime
~~~
- **-p**: mostra o tempo de atividade de forma legível
- **-s**: mostra o dia e horário em que o sistema foi ligado

# Gerenciamento de pacotes

> **apt get** - ferramenta que pode ser utilizada para gerenciar, atualizar, pesquisar, instalar e desinstalar pacotes em um sistema. Só disponível nas distribuições Linux derivadas do Debian, como o Ubuntu, por exemplo.
~~~bash
# Atualiza a lista de pacotes disponíveis nos repositórios

sudo apt-get update

# Verifica todos os pacotes do sistema, faz download das atualizações disponíveis e executa a isntalação delas em cada pacote

sudo apt-get upgrade

# Instala um ou mais pacotes

sudo apt-get install pacote1 pacote2

# Remove um ou mais pacotes

sudo apt-get remove
~~~
# Rede

> **ping** - tem como função a verificação da conectividade da rede, mas também pode ser usado para resolver problemas de conexão.
~~~bash
ping [opção] [nome_do_herdeiro_ou_endereço_IP]

# Realiza uma determinada quantidade de pings

ping -c 4 8.8.8.8

# Envia um pacote a cada tempo estabelecido (2 segundos no caso)

ping -i 2 globo.com
~~~

> **curl** - "Cliente URL", pode ser utilizado para verificar a conectividade URL e transferir dados para outros servidores. Suporta vários tipos de protocolos.
~~~bash
curl [opção] [URL]

curl https://www.google.com

# Ver cabeçalho

curl -I https://github.com

# Requisição POST

curl -X POST -d "nome=usuario&senha=123" https://api.site.com

# Download interrompido

curl -C - -O https://exemplo.com
~~~
- **-O**: salva o arquivo no diretório atual usando o mesmo nome do arquivo remoto
- **-o**: permite que o usuário especifique um nome diferente para o arquivo
- **-I**: retorna apenas o cabeçalho
- **-X**: faz uma requisição POST (enviar dados para uma API)
- **-C**: continua um download interrompido

> **wget** - "World Wide Web Get" permite que o usuário faça download de arquivos nos protocolos HTTP, HTTPS e FTP diretamente de linha de comando. Pode funcionar em segundo plano.
~~~bash
wget https://exemplo.com/arquivo.zip

# Salvar com nome diferente

wget -O meu_nome.zip https://exemplo.com

# Espelhar um site inteiro

wget -m https://site-estatico.com

# Baixa todos os arquivos de uma determinada extensão de uma página

wget -r -A.pdf https://site.com
~~~
- **-b**: para realizar o download em segundo plano
- **-O**: faz o download e salva o arquivo com outro nome
- **-m**: cria uma cópia local completa para navegação offline

> **ip address** - Substitui o antigo "ifconfig", exibe informações relacionadas às interfaces de rede do seu computador ou servidor, também permite a manipulação de interfaces, configuração de endereços e alterar tabelas de rotas.
~~~bash
ip a

# Ver apenas interfaces ativas

ip links ls up

# Atribuir um IP manualmente a uma interface

sudo ip addr add 192.168.1.50/24 dev eth0

# Remover um endereço IP

sudo ip addr del 192.168.1.50/24 dev eth0

# Ligar ou desligar uma interface

sudo ip link set eth0 up
sudo ip link set eth0 down
~~~
# Informações do sistema

> **uname** - "Unix Name", usado para mostrar informações detalhadas sobre o sistema.
~~~bash
uname [opção]


~~~
- **-a**: mostra todos os dados do sistema
- **-r**: imprime a versão do Linux
- **-n**: mostra o hostname do node do sistema

> **top** - exibe todos os processos em execução e também mostra quanto da CPU cada um deles está usando.
~~~bash
top
~~~
- para resultados mais amigáveis, utilizar o **htop**, que permite usar o mouse e setas do teclado para navegar, além de apresentar o resultado em cores

> **ps** - exibe dados sobre os processos que estão em execução no sistema. Informações como o ID e a quantidade de recursos utilizados por cada um.
~~~bash
ps [opções]

# Exibe todos os processos de todos os usuários

ps aux

# Encontrar um processo específico

ps aux | grep firefox

# Ver a árvore de processos (mostra quem iniciou - hierarquia)

ps axjf
~~~
- **-A ou -e**: exibe todos os processos em execução
- **-u nome_de_usuário**: lista todos os processos associados a um determinado usuário
- **T**: mostra todos os processos relacionados à atual sessão do shell
- **-x**: inclui processos que não foram iniciados no terminal (serviços de fundo)

>**free** - verifica a quantidade de memória atual, em uso e disponível.
~~~bash
free [opção]


~~~
- **-b**: apresenta a quantidade de memória em bytes
- **-g**: apresenta a quantidade de memória em gigabytes
- **-k**: apresenta a quantidade de memória em quilobytes
- **-m**: apresenta a quantidade de memória em megabytes
- **-tera**: apresenta a quantidade de memória em terabytes
- **-h**: exibe todos os campos de saída dimensionados automaticamente para a unidade de três dígitos mais curta

> **whoami** - utilizado para mostrar o nome do usuário com o qual você está conectado com o sistema naquele momento.
~~~bash
whoami
~~~

> **df** - possibilita a visualização do espaço em disco usado e disponível.
~~~bash
df [opção]
~~~
- **-h**: exibe os dados em formato legível
- **-m**: apresenta as informações em megabytes
- **-k**: mostra os dados em quilobytes
- **-t**: apresenta o tipo de sistema de arquivos em uma nova coluna

> **du** - verifica quanto espaço do disco um arquivo ou diretório está ocupando.
~~~bash
du [opção][dirtório]
~~~
- **-s**: exibe o tamanho total de uma pasta especificada
- **-h**: oferece unidade mais inteligível
- **-m**: mostra as informações em megabytes
- **-k**: mostra as informações em quilobytes

> **exit** - encerra a execução de um processo e volta para o promp de comando anterior.
~~~bash
exit
~~~

> **man** - acesso ao manual completo para todos os comando que podem ser executados no terminal.
~~~bash
man [nome do comando]
~~~
- **-a**: mostra todas as páginas de acordo com o termo utilizado para pesquisar um comando
- **-k**: busca nos índices do manual uma palavra específica

> **history** - apresenta uma lista com até 500 comandos executado
~~~bash
history [opção]
~~~
- **-c**: limpa o histórico
- **-d**: offset: exclui apenas o histórico na posição OFFSET
- **-a**: adiciona linhas ao histórico
# Permissões e usuários

> **chmod** - "Change Mode" altera as permissões de um arquivo de maneira rápida e prática.
~~~bash
chmod [opção][permissão][nome_do_arquivo]

# Todo mundo faz tudo, soma os valores para cada categoria: (u) DONO, (g) GRUPO e (o) OUTROS - (a) TODOS

chmod 777 arquivo

# Dono faz tudo, grupo e outros apenas leem e executam

chmod 755 arquivo

# Dono lê e escreve, os outros apenas leem (padrão para arquivos comuns)

chmod 644 arquivo

# Só o dono lê e escreve, ninguém vê mais nada

chmod 600 arquivo

# Torna um arquivo executável

chmod +x script.sh

# Remover permissões de escrita do grupo e outros

chmod go-w arquivo.txt

# Dar permissão total apenas ao dono

chmod u=rwx arquivo.txt

# Muda as permissões de uma pasta e de todos os arquivos dentro dela

chmod -R 755 minha_pasta/
~~~
- permissões básicas:
	- *r / 4* (read)
	- *w / 2* (write)
	- *x / 1* (execute)
	- *0* nenhuma permissão
	- *+* adicionar
	- - remover
	- = definir exatamente
- **-c**: informa quando a última alteração foi realizada
- **-f**: suprime as mensagens de erro
- **-v** imprime detalhes do que está sendo feito pelo comando
- **-R**: aplica em pastas inteiras
![[Pasted image 20260216151322.png]]

> **chown** - "Change Owner" permite mudar o proprietário do arquivo.
~~~bash
chown [opção] [novo_dono]:[novo_grupo] arquivos

# Transforma usuário Pedro no dono do arquivo

sudo chown pedro documento.txt

# Muda dono e grupo ao mesmo tempo

sudo chown maria:editores texto.doc

# Muda apenas o grupo

sudo chown :webmasters index.html

# Aplica em uma pasta e tudo que estiver dentro dela

sudo chown -R usuario:grupo /var/www/meu_site
~~~

> **adduser** - pode ser utilizado para criar um usuário ou adicionar um usuário a um grupo específico.
~~~bash
sudo adduser nome_usuário

# Adicionar um usuário existente a um grupo (muito utilizado para dar permssões de administrador)

sudo adduser usuario sudo

# Cria um usuário de sistema (sem pasta /home)

sudo adduser --system nome_do_serviço

# Remover um usuário completamen
~~~
