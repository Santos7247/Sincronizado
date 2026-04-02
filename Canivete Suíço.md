# Bash Scripting
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

> **Objetivo**: Criar um script para identificar possíveis hosts em um domínio. O usuário deve informar o domínio e caso o site possua subdomínios na página ele deve retornar o IP dos hosts.

~~~bash
# 1º Passo: extrair o código HTML da páigna e salvar o conteúdo como index.html

wget businesscorp.com.br

# 2º Passo: analisar o código fonte atrás de endereços e salvar no arquivo "lista"

grep href index.html | cut -d "/" -f 3 | grep "\." | cut -d '"' -f 1 | grep -v "<l" > lista

# 3º Passo: descobrir o endereço IP de um domínio

for url in $(cat lista);do host $url | grep "has address";done 
~~~
