
Os seguintes elementos compõem um comando Linux:
- **CommandName** (nome do comando): a requisição que o usuário deseja executar;
- **Flag** (opção): serve para modificar a operação do comando. Ele pode ser incluído por meio de um ou dois hífens; e
- **Argument** (argumento): usado para adicionar informações à requisição. Não é obrigatório para todos os comandos.
---
# Gerenciamento de arquivos e diretórios

> **ls** - possibilita a visualização de todos os conteúdos contidos em um diretório. Para visualizar outros repositórios, é preciso escrever ls e incluir o caminho do diretório.
~~~~bash
ls/home/username/documents
~~~~
- **ls -R**: visualiza conteúdos dos subdiretórios
- **ls -l**: exibe uma lista detalhada
- **ls -a**: mostra os arquivos ocultos

> **cd** - usado para navegar entre diretórios e modificá-los.

~~~~bash
cd /home/usuario/documentos
~~~~

- **cd..** : para subir um diretório acima
- **cd ~**: para acessar a pasta do usuário logado
- **cd -**: para retornar para diretórios anteriores
