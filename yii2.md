# Yii2
 Framework PHP
 
## Debugger

1. Instalação e configuração do xdebug
```
# Instala o xdebug
apt-get update \
&& apt-get install -y --no-install-recommends install php5-xdebug \
&& apt-get clean \
# Arocurar o local do arquivo xdebug.so
find / -name xdebug.so
# Adicionar as configurações do xdebug ao arquivo do módulo carregado pelo php
echo "zend_extension=<path_do_arquivo_xdebug>/xdebug.so" > /etc/php5/mods-available/xdebug.ini \
&& echo "xdebug.remote_enable=on" >> /etc/php5/mods-available/xdebug.ini \
&& echo "xdebug.remote_handler=dbgp" >> /etc/php5/mods-available/xdebug.ini \
&& echo "xdebug.remote_port=9005" >> /etc/php5/mods-available/xdebug.ini \
&& echo "xdebug.remote_autostart=on" >> /etc/php5/mods-available/xdebug.ini \
&& echo "xdebug.remote_connect_back=0" >> /etc/php5/mods-available/xdebug.ini \
&& echo "xdebug.idekey=netbeans-xdebug" >> /etc/php5/mods-available/xdebug.ini \
&& echo "xdebug.profiler_enable=on" >> /etc/php5/mods-available/xdebug.ini \
&& echo "xdebug.profiler_enable_trigger=on" >> /etc/php5/mods-available/xdebug.ini \
&& echo "xdebug.remote_host=172.17.0.1" >> /etc/php5/mods-available/xdebug.ini
```

2. Configuração da IDE
  * Netbeans
  
