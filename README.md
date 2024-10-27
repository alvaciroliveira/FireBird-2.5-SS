# Instrução Utilização Firebird SS 2.5

1- Primeiro instalação de complementos:

> sudo apt install libncurses5

2- Download Pacote Firebird SS

> wget https://github.com/FirebirdSQL/firebird/releases/download/R2_5_9/FirebirdSS-2.5.9.27139-0.amd64.tar.gz

3- Descompactar e Instalação:

> sudo tar -xvf FirebirdSS-2.5.9.27139-0.amd64.tar.gz

> cd FirebirdSS-2.5.9.27139-0.amd64

> sudo ./install.sh

Senha Padrão depende do seu sistema sugiro usar:
>masterkey

4- Informar ao Sistema qual a pasta terá permissão de uso ao Firebird:

> sudo chown firebird:firebird /Pasta Sistema

> sudo nano /opt/firebird/firebird.conf

# Inserir a Linha:
> DatabaseAccess = Restrict /Pasta Sistema

5- Habilitar Firewall ao Firebird, considerando que já tenha UFW já instalado:

> sudo ufw allow 3050/tcp

6- Liberando o banco.FDB para utilização, dentro da Pasta do Sistema:

> chmod 666 DADOS5.FDB

7- Reiniciar Firebird para aplicar mudanças e conectar bando ao ISQL:

> sudo /opt/firebird/bin/fbmgr.bin -restart

> sudo /opt/firebird/bin/isql # "Sugestão usar o comando já na Pasta do Sistema"

> CONNECT "banco.FDB" user 'SYSDBA' password 'masterkey';

> exit;

# ------------------------------
# List of known database aliases
# ------------------------------
# Windows

> banco.FDB on localhost = C:\Pasta Sistema\banco.FDB

# Linux

> banco.FDB on localhost = /Pasta Sistema/banco.FDB

Créditos: https://blog.unagui.info/como-instalar-firebird-2-5-no-debian-buster/
