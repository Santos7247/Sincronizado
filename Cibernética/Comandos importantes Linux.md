
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
- Obs.: o comando "colordiff" apresenta 