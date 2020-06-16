# HTTP2
[https://http2.github.io/](https://http2.github.io/)

* **HPACK** - Headers são enviados em código binário e comprimidos usando o algoritmo  HPACK
* **GZIP** - GZIP HTTP1.1 era opcional e precisave ser ativado. Na versão 2 é padrão e obrigatório.
* **TLS** - TLS padrão.
* **Headers Steteful** - Os cabeçalhos que se repetem não são reenviados
* **Server Push** - O servidor pode enviar várias respostas em paralelo, devolvendo a página principal juntamente com os arquivos estáticos, por exemplo.
* **Multiplexing** - Várias requisições e respostas podem ser feitas, sem que seja necessário aguardar o retorno na anterio.
