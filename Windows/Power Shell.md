
> O comando "Get-Command" lista os comandos do Power Shell

~~~powershell
# Filtrando os comandos

Get-Command | Select-String Test
~~~
# Criando um script em Power Shell
~~~powershell
notepad script.ps1

# Para executar

.\script.ps1
~~~

Script simples
~~~powershell
echo "Meu diretório atual: $(pwd)"
write-Host "Meu usuário atual: $(whoami)"

$ip = "192.168.0.1"
echo "Varrendo o Host: $ip"
~~~

## Variável
~~~powershell
$ip = Read-host "Digite o IP:"
echo "Varrendo o Host: $ip"
echo "Efetuando Ping no Host: $ip"
ping -n 1 $ip | Select-String "bytes=32"
~~~

## Parâmetros
~~~powershell
param($ip)
if (!$ip){
	echo "Desec Security"
	echo "Exemplo de uso: .\script.ps1 192.168.0.1"
} else {
echo "Efetuando ping no Host: $ip"
ping -n 1 $ip | Select-String "bytes=32"
}
~~~

## Condições e Repetições

~~~powershell
foreach ($var1 in 1..10) {echo "192.168.0.$var1}
~~~

~~~powershell
$idade = Read-Host "Qual a idade?"
if ($idade -ge "18"){
	echo "Pode dirigir"
} else {
	echo "Não pode dirigir"
}
~~~

### Ping Sweep

~~~powershell
# Filtrando os resultados, é necessário tornar o comando "ping" em uma variável
# Os comandos "try" e "catch" servem para tratar os erros e não exibir na tela

param($p1)
if (!$p1){
	echo "Desec Security"
	echo "Exemplo de uso: .\script.ps1 192.168.0"
} else {
foreach ($ip in 1..254){
try {$resp = ping -n 1 "$p1.$ip" | Select-String "bytes=32"
$resp.Line.split(' ')[2] - replace ":",""
} catch {}
}
}
~~~

### Port Scanner

~~~powershell
# Testa a conexão com um Host

Test-NetConnection www.businesscorp.com.br

# Faz o traceroute

Test-NetConnection www.businesscorp.com.br -TraceRoute

# Delimita a quantidade de saltos

Test-NetConnection www.businesscorp.com.br -TraceRoute -Hop 2

# Valida se uma porta está aberta

Test-NetConnection www.businesscorp.com.br -Port 80
~~~
