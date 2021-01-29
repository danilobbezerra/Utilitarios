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
<pre><code>
sudo systemctl enable **kestrel-helloapp.service**
sudo systemctl disable **kestrel-helloapp.service**

</code></pre>

### Start/Restart/Status
<pre><code>
sudo systemctl start **kestrel-helloapp.service**
sudo systemctl restart **kestrel-helloapp.service**
sudo systemctl status **kestrel-helloapp.service**

</code></pre>

---------------------------------------
# Alterando idioma sistema linux (Debian)

<pre>
<code>
sudoedit /etc/default/locale
</code>
</pre>
> Alterar arquivo para: LANG="pt_BR.UTF-8" onde **pt_BR** é o idioma desejado


---------------------------------------

# Comandos Docker
Gerando uma imagem docker
> estar no diretório onde está o arquivo DockerFile
<pre>
<code>
  docker build -t NomeImagem -f Dockerfile .
</code>
</pre>

Salvando fisicamente uma imagem em diretorio
<pre>
<code>
 docker image save NomeImagem -o c:\NomeImagem.img (com ou sem extensao)
</code>
</pre>




