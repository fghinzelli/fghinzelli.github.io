# WebUSB API 

[Documentação](https://wicg.github.io/webusb/)

Obs.: Funciona somente em localhost com http, em outros hosts, precisa ser https

### Exemplo
https://github.com/drffej/webusb.printer
https://web.dev/usb/

### Referências: 
- https://developers.google.com/web/updates/2016/03/access-usb-devices-on-the-web
- https://developers.google.com/web/fundamentals/native-hardware/build-for-webusb/
- https://medium.com/@gendor/connecting-to-usb-devices-with-your-browser-d433a6df6f2


### Observações para execução em ambiente Linux
- Testar comunicação com a impressora:
http://bematechpartners.com.br/wiki/index.php/2018/04/09/2039/
```
dmesg
echo “teste impressão MP4200TH” > /dev/ttyACM0
```

- Permissões especiais:  
 https://developers.google.com/web/fundamentals/native-hardware/build-for-webusb/#linux
    * Arquivo */etc/udev/rules.d/80-snap.core.rules* criado com o conteúdo:
    ```SUBSYSTEMS=="usb", ATTR{idVendor}=="03f4", ATTR{idProduct}=="2006", GROUP="plugdev"```

- Desativar o driver do SO:  
 https://stackoverflow.com/questions/47695160/failed-to-claim-interface-0-device-or-resource-busy/47724582
    * Listar os dispositivos   
    ```lsusb```
    * Pesquisar pelo número da porta do device   
    ```grep -l <bus>/<device> /sys/bus/usb/devices/*/uevent```
    * Ou visualizar informações do device conectado nos logs do kernel   
    ```tail -f /var/log/kern.log```
    * Unbind do dispositivo   
    ```echo -n "1-1.5:1.0" > /sys/bus/usb/drivers/usblp/unbind```
    ou
    ```echo -n "3-4:1.0" > /sys/bus/usb/drivers/cdc_acm/unbind```
    * Se a impressora em \dev\ttyS<n> estiver com permissões apenas para root, liberar as permissões   
    ```chmod 777 /dev/ttyS[0--9]```
    
    * Extra: Unbind on boot:  
    http://migueleonardortiz.com.ar/linux/learning-how-to-disable-specific-usb-devices-by-their-ports-in-linux/1645
    
- Instalação de drivers bematech    
    http://bematechpartners.com.br/wiki/index.php/2017/10/20/linux-utilizando-impressoras-e-sat-bematech-terminal-ou-arquivo-de-regras/
    http://bematechpartners.com.br/wiki/index.php/2017/06/22/utilizando-a-mp-4200-th-no-linux/
    http://bematechpartners.com.br/wiki/index.php/2020/01/24/erro-em-cups-linux-com-a-mp4200-th/

- Outros links   
 https://web.dev/usb/
 https://www.visuality.pl/posts/webusb-bridge-between-usb-devices-and-web-browsers
### Utilitários
- Verificar logs   
```chrome://device-log/```
- Autorizações USB   
```chrome://settings/content/usbDevices?search=usb```



