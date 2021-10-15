# Yii2
 The Fast, Secure and Professional PHP Framework  
 [https://www.yiiframework.com/](https://www.yiiframework.com/)  
 [https://github.com/yiisoft/yii2](https://github.com/yiisoft/yii2)  
 
## Desenvolvimento com Docker
 Estrutura com três containers: Aplicação + Database + Pgadmin
 
- Dockerfile para geração da imagem para desenvolvimento:
 ```console
FROM schmunk42/yii2-app-basic:latest

# LDAP modules
RUN apt update \
    && apt remove -y php5-fpm \
    && apt install -y php5-ldap \
    && php5enmod ldap \
    && apt install -y php5-fpm --option=Dpkg::Options::=--force-confdef

# Ajuste de fuso horário
RUN apt --only-upgrade install tzdata
    
# Xdebug    
RUN apt-get -y --no-install-recommends install php5-xdebug \
    && apt-get clean \
    && echo "zend_extension=/usr/lib/php5/20131226/xdebug.so" > /etc/php5/mods-available/xdebug.ini \
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
- Build da nova imagem:
```console
docker build -t fghinzelli/yii2 .
```
- Arquivo docker-compose.yml para os Três containers 
```console
version: '3'

services:
  yii2-dev:
    image: fghinzelli/yii2
    container_name: yii2-dev
    ports:
      - "8000:80"
    volumes:
      - <path_repositorio_de_codigo>:/app
    networks:
      - yii2-network
    depends_on:
      - database

  postgres:
    image: postgres:9.6
    container_name: database
    ports:
      - "5440:5432"
    environment:
      POSTGRES_PASSWORD: "password"
    volumes:
      - <path_postgres>:/var/lib/postgresql/data
    networks:
      - yii2-network

  pgadmin4:
    image: dpage/pgadmin4
    container_name: pgadmin
    environment:
      PGADMIN_DEFAULT_EMAIL: "user@domain.com"
      PGADMIN_DEFAULT_PASSWORD: "password"
    ports:
      - "15432:80"
    depends_on:
      - postgres
    networks:
      - yii2-network

networks:
  yii2-network:
    driver: bridge
```
 
## Debugger

1. Instalação e configuração do xdebug
```console
# Instala o xdebug
apt-get update \
&& apt-get install -y --no-install-recommends install php5-xdebug \
&& apt-get clean \
# Procurar o local do arquivo xdebug.so
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
  * Netbeans (com PDT)
     - *Tools > Options > PHP*. 
        * Debugger Port: 9000 (Ou outra, caso esta não esteja disponível)
        * Session ID: netbeans-xdebug (ou outro, mas deve ser igual ao definido no parâmetro xdebug.idekey) 
     - *No Projeto > Properties > Run Configuration* 
        * Run As: Local Web Site
        * Project URL: http://localhost:8000/ (A porta é a usada pelo servidor web)
        * Index File (IMPORTANTE): web/index.php

## Integração de app transpilada em React
- Copiar os arquivos css e js para os diretórios /web/css e /web/js
- Incluir arquivos Estáticos no arquivo AppAsset.php
- Na página inicial da aplicação (/views/site/index.php) adicionar a div principal: ``` <div id="root"></div> ```

## Gii
Para geração/atualização dos arquivos de Internacionalização (/app/messages/pt-BR/):

``` php yii message-enum "@app/config/i18n.php" ``` 

## Iframe problems
Verificar se o controller possui, no método behaviors o parâmetro 'iframeble' setado
```
public function behaviors()
    {
        return [
            'verbs' => [
                'class' => VerbFilter::className(),
                'actions' => [
                    'delete' => ['POST'],
                ],
            ],
            'iframeable' => [
                'class' => IframeableBehavior::className(),
            ]
        ];
    }
```


