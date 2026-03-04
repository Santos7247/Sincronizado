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
porta=80
echo "Varrendo o host: $ip na porta: $porta"
~~~

- executando comandos
~~~bash
#!/bin/bash

echo "Digite o IP:"
read ip

echo "Efetuando PING no host:" %ip
ping -c1 $ip
~~~

~~~bash
#!/bin/bash

echo "Digite o serviço a ser iniciado:"
read var1

service $var1 restart

echo "Serviçoes ativos:"
ps aux | grep $var1

echo "Portas abertas:"
netstat -nlpt
~~~
## Trabalhando com condições

- **lt** - less than **<**
- **gt** - greater than **>**
- **le** - less or equal **<=**
- **ge** - greater or equal >=
- **eq** - equal =
- **ne** - not equal !=

~~~bash
#!/bin/bash

echo "Qual a cor do semáforo?"
read cor
if [ "$cor" == "verde" ]
then
	echo "Siga em frente."
elif [ "$cor" == "amarelo" ]
then
	echo "Aguarde!"
else
	echo "PARE!"
fi
~~~

~~~bash
#!/bin/bash

echo "Qual a sua idade?"
read idade

if [ "$idade" -ge "18" ]
then
	echo "Pode dirigir."
else
	echo "Não pode dirigir."
fi
~~~

- Menu
~~~bash
#!/bin/bash

echo "O cliente autorizou o Pentest?"
echo "1 - Sim"
echo "2 - Não"
read resp

case $resp in
"1")
	echo "Pode iniciar o Pentest."
;;
"2")
	echo "Pentes pendente, aguarde o cliente autorizar."
;;
esac
~~~
## Argumentos

~~~bash
#!/bin/bash

# Validando se o usuário colocou o argumento

if [ "$1" == ""]
then
	echo "Modo de uso: $0 192.168.0.1 80"
else
	echo "Varrendo host: $1 e porta $2"
fi
~~~

- Executando o script com argumentos:
~~~bash
./script.sh 192.168.0.1 8000
~~~

## Repetições
~~~bash
# Cria uma sequência de 1 a 10

echo {1..10}
echo {a..z}

seq 1 10
~~~

> **for**

~~~bash
for ip in {1..10};do echo 192.168.0.$ip;done
~~~

~~~bash
#!/bin/bash

for ip in $(seq 100 120);
do
echo 172.16.1.$ip
done
~~~

>**while**

~~~bash
while true; do echo "Hacked";done
~~~
