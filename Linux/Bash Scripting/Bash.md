~~~bash
nano script.sh

# Dá permissão de execução ao script

chmod +x script.sh
~~~


~~~bash
#!/bin/bash

# 'echo' exibe texto na tela

echo "Desec Security"

# Exibe o resultado do comando após o texto

echo 'Sistema ligado por:' $(uptime -p)
echo 'Diretório atual:' $(pwd)
echo 'User atual:' $(whoami)
~~~

## Variáveis

~~~bash
#!/bin/bash

ip=192.168.0.1
echo "Varrendo o host:" $ip
~~~
- utiliza um valor determinado pelo usuário
~~~bash
#!/bin/bash

echo "Digite o IP:"
read ip

echo "Varrendo o host:" $ip
~~~
