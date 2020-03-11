# WebUSB API 

[Documentação](https://wicg.github.io/webusb/)

### Exemplo
https://github.com/drffej/webusb.printer

### Referências: 
- https://developers.google.com/web/updates/2016/03/access-usb-devices-on-the-web
- https://developers.google.com/web/fundamentals/native-hardware/build-for-webusb/
- https://medium.com/@gendor/connecting-to-usb-devices-with-your-browser-d433a6df6f2

### Observações para execução em ambiente Linux
- Permissões especiais:  
 https://developers.google.com/web/fundamentals/native-hardware/build-for-webusb/#linux

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

### Utilitários
- Verificar logs   
```chrome://device-log/```
- Autorizações USB   
```chrome://settings/content/usbDevices?search=usb```

