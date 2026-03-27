## PortScan de rede

> **Objetivo**: Criar um script para descobrir quais hosts na rede possuem uma determinada porta aberta. O usuário deve informar a rede e o script deve retornar os host que possuem a porta 80 aberta.

~~~bash
#!/bin/bash
if [ "$1" == "" ]
then
	echo "Desec Security"
	echo "Modo de uso: $0 Rede"
	echo "Exemplo: $0 172.16.1"
else
for ip in {1..254};
do
hping -S -p 80 -c 1 $1.$ip 2> /dev/null | grep "flags=SA" | cut -d " " -f 2 | cut -d "=" -f 2;
done
~~~

## Parsing HTML

> **Objetivo**: Criar um script para identificar possíveis hosts em um domínio. O usuário deve informar o domínio e caso o site possua subdomínios na página ele deve retornar o 

~~~bash

~~~
