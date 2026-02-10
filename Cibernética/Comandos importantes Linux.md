
Os seguintes elementos compõem um comando Linux:
- **CommandName** (nome do comando): a requisição que o usuário deseja executar;
- **Flag** (opção): serve para modificar a operação do comando. Ele pode ser incluído por meio de um ou dois hífens; e
- **Argument** (argumento): usado para adicionar informações à requisição. Não é obrigatório para todos os comandos.
---
# Gerenciamento de arquivos e diretórios

> **ls** - possibilita a visualização de todos os conteúdos contidos em um diretório. Para visualizar outros repositórios, é preciso escrever ls e incluir o caminho do diretório.
~~~~bash
ls /home/username/documents
~~~~
- **-R**: visualiza conteúdos dos subdiretórios
- **-l**: exibe uma lista detalhada
- **-a**: mostra os arquivos ocultos

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
~~~~

