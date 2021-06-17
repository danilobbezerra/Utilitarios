# Utilitarios
Repositório publico para armazenamento de comandos, dicas, técnicas etc...


# LINUX
## Criando um serviço que inicializa a aplicação ASP.NET CORE

sudo nano /etc/systemd/system/kestrel-helloapp.service

> Este comando abre um editor de texto onde é possivel criar e já salvar o arquivo com o nome desejado no caso está sendo salvo como: **kestrel-helloapp.service**

<pre><code>
[Unit]
Description=Aqui vai a descrição do servico

[Service]
#Diretório de trabalho
WorkingDirectory=/home/admin/app
#Caminho do objeto a ser iniciado
ExecStart=/usr/bin/dotnet /home/admin/app/ArquivoDLLdoProjeto.dll
#Reiniciar sempre caso ocorra falhas
Restart=always
#Tempo de restar após ocorrer uma falha:
RestartSec=10
KillSignal=SIGINT
#Nome Identificador de log
SyslogIdentifier=dotnet-example
User=admin
#Variaveis de ambiente a serem configuradas
Environment=ASPNETCORE_ENVIRONMENT=Production
Environment=DOTNET_PRINT_TELEMETRY_MESSAGE=false

[Install]
WantedBy=multi-user.target

</code></pre>

### Habilitar/Desabilitar o serviço
<pre><code>sudo systemctl enable **kestrel-helloapp.service**</code></pre>
<pre><code>sudo systemctl disable **kestrel-helloapp.service**</code></pre>


### Start/Restart/Status
<pre><code>sudo systemctl start **kestrel-helloapp.service**</code></pre>
<pre><code>sudo systemctl restart **kestrel-helloapp.service**</code></pre>
<pre><code>sudo systemctl status **kestrel-helloapp.service**</code></pre>

### REMOVE UM DIRETORIO E ARQUIVOS SEM CONFIRMAÇÃO
<pre><code>rm -rf dirname</code></pre>

### COPIAR ARQUIVOS DE UM SERVIDOR PARA OUTRO
<pre><code>scp -r root@XXX.XXX.XXX.XXX:/diretorio/origem/arquivos/ou/pasta /diretorio/destino</code></pre>
ou
<pre><code>scp -r /diretorio/origem/arquivos/ou/pasta root@XXX.XXX.XXX.XXX:/diretorio/destino</code></pre>

### RODAR SPEED TEST NO LINUX (Testado no Ubuntu)
<pre><code>curl -s https://install.speedtest.net/app/cli/install.deb.sh | sudo bash</code></pre>
<pre><code>sudo apt-get install speedtest</code></pre>

FORMA DE TESTAR
<pre><code>speedtest -s SERVERID -f csv|tsv|jsonl|json|json-pretty</code></pre>

SERVERID Pode ser obtido na lista de servidores abaixo
<pre><code>https://c.speedtest.net/speedtest-servers-static.php</code></pre>


---------------------------------------
# Alterando idioma sistema linux (Debian)

<pre><code>sudoedit /etc/default/locale</code></pre>
> Alterar arquivo para: LANG="pt_BR.UTF-8" onde **pt_BR** é o idioma desejado


---------------------------------------

# Comandos Docker
Gerando uma imagem docker
> estar no diretório onde está o arquivo DockerFile
<pre><code>docker build -t NomeImagem -f Dockerfile .</code></pre>

Salvando fisicamente uma imagem em diretorio
<pre><code>docker image save NomeImagem -o c:\NomeImagem.img (com ou sem extensao)</code></pre>


Sobe as imagens especificadas em um docker compose
<pre><code>docker-compose up -d --build</code></pre>



---------------------------------------

# MYSQL
Alterando mysql para aceitar nomes de tabelas minusculo/maiusculo, editando o arquivo: **my.cnf**
> estar no diretório onde está o arquivo DockerFile
<pre>
<code>
 [mysqld]
 lower_case_table_names=1
</code>
</pre>



