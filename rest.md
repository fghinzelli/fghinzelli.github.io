# REST - Representational State Transfer

Em sistemas REST, **as URIs devem conter apenas substantivos**, que são nossos recursos: 
*/restaurante/adiciona* não é uma boa URI, pois contém um verbo e não está identificando um recurso, mas sim uma operação.

## Operações

As semânticas principais são:

**GET** - recupera informações sobre o recurso identificado pela URI. Ex: listar restaurante, visualizar o restaurante 1. Uma requisição GET não deve modificar nenhum recurso do seu sistema, ou seja, não deve ter nenhum efeito colateral, você apenas recupera informações do sistema.

**POST** - adiciona informações usando o recurso da URI passada. Ex: adicionar um restaurante. Pode adicionar informações a um recurso ou criar um novo recurso.

**PUT** - adiciona (ou modifica) um recurso na URI passada. Ex: atualizar um restaurante.

**DELETE** - remove o recurso representado pela URI passada. Ex: remover um restaurante.

## Representações

Cabeçalhos(Accept/Content-Type) são usados para especificar as representações(JSON,XML,...)
