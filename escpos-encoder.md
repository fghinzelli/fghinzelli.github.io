# ESC POS

Sintaxe criada pela EPSON e reutilizada por outros fabricantes

Testes realizados com impressora *Diebold TSP143MD*. Para utilizar os comandos da sintaxe ESCPOS, é necessário acessar 
o menu de configuração e alterar, dado que o padrão é utilizar outra codificação.

Para a utilização em uma App ReactJS foi utilizada a biblioteca esc-pos-encoder:
https://www.npmjs.com/package/esc-pos-encoder

### Links de conteúdo
https://reliance-escpos-commands.readthedocs.io/en/latest/imaging.html
https://reference.epson-biz.com/modules/ref_escpos/index.php?content_id=88
https://reliance-escpos-commands.readthedocs.io/en/latest/font_cmds.html

```js
function print() {
    let EscPosEncoder = require('esc-pos-encoder');
    let encoder = new EscPosEncoder();

    // Tabulacoes
    let encodingText = encoder
      .initialize()
      //altura x largura expandidas
      //.raw([ 0x1d, 0x21, 0x11 ])
      .raw([ 0x1b, 0x44, 10, 15, 20, 25, 0x00 ])
      .raw([ 0x09 ])
      .text('A')
      .raw([ 0x09 ])
      .text('B')
      .raw([ 0x09 ])
      .text('C')
      .raw([ 0x09 ])
      .text('D')
      .raw([ 0x1b, 0x4a, 200])
      .encode();
    device.transferOut(2, encodingText)
      .catch(error => { console.log(error); })

    let img = new Image();
    img.src = brasao;
    img.onload = function() {
      let encodingImage = encoder
        .initialize()
        .codepage('cp860')
        .image(img, 128, 128, 'atkinson')
        .align('center')
        .raw([ 0x1b, 0x44, 14, 0x00 ])
        .bold()
        .raw([ 0x09 ])
        .text('MUNICÍPIO DE CAXIAS DO SUL')
        .raw([ 0x0a ])
        .raw([ 0x09 ])
        .text('SECRETARIA DA RECEITA MUNICIPAL')
        .raw([ 0x1b, 0x4a, 200])
        .raw([ 0x1b, 0x69 ])
        .encode();
      device.transferOut(2, encodingImage)
        .catch(error => { console.log(error); })
    }

    let result = encoder
        .initialize()
        //.raw([ 0x1b, 0x43, 200 ])
        .bold(true)
        // Aumentar tamanho dos caracteres (quarto e quinto parametros = altura (0~10) x largura (0~14) )
        //.raw([ 0x1b, 0x2b, 0x30, 3, 4, 0x30 ])
        .align('center')
        .line('ABC')
        .bold(false)
        .text('CDE')
        // Código de barras
        //.raw([ 0x1b, 0x7c, 0x30, 0x78, 0x02, 0x00, 0x30, 0x31, 0x32, 0x33, 0x34, 0x35, 0x36, 0x37, 0x38, 0x39, 0x30, 0x31 ])
        // Impressão e deslocamento (terceiro parametro 0~255)
        .raw([ 0x1b, 0x4a, 100])
        //.text('| The quick brown fox jumps over the |')
        // Corte
        .raw([ 0x1b, 0x69 ])
        .encode();    
    console.log(result)
  
  }
```
