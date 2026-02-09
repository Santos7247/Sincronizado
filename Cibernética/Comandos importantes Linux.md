
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
