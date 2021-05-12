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
- https://wiki.archlinux.org/index.php/udev
- https://linuxconfig.org/tutorial-on-how-to-write-basic-udev-rules-in-linux
- https://unix.stackexchange.com/a/215725
- https://linux.die.net/man/7/udev

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
 https://medium.com/@gendor/connecting-to-usb-devices-with-your-browser-d433a6df6f2
 
- Sequencia funcional no Ubuntu Linux    
 
 ```
#!/bin/bash
echo 'SUBSYSTEM=="usb", ATTRS{idVendor}=="0b1b", ATTRS{idProduct}=="0003", GROUP="plugdev"' > /etc/udev/rules.d/69-bematech.rules
echo 'Rules file created'
echo ' ' > /dev/ttyACM0 && echo ' ' > /dev/ttyACM0
# chmod 777 /dev/ttyS*
PORTID=$(grep -l 'b1b/3' /sys/bus/usb/devices/*/uevent | tail -1 | tr "/" " " | awk '{print $5}')
echo -n $PORTID:1.0 >  /sys/bus/usb/drivers/cdc_acm/unbind
echo 'Driver unbounded'
echo 'Finish!'
 ```

### Impressora Bematech:  
  
1. Criar o arquivo */etc/udev/rules.d/00-bematech.rules* com o seguinte conteúdo:   
```
ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="0b1b", ATTRS{idProduct}=="0003", ATTR{bInterfaceNumber}=="00", GROUP="plugdev", RUN+="/usr/local/bin/unbind_bema.sh"
```   
2. Criar o script a seguir em /usr/local/bin/unbind_bematech.sh:   
``` 
#!/bin/bash
echo ' ' > /dev/ttyACM0 && echo ' ' > /dev/ttyACM0
PORTID=$(grep -l 'b1b/3' /sys/bus/usb/devices/*/uevent | tail -1 | tr "/" " " | awk '{print $5}')
echo -n ${PORTID:0:3}:1.0 >  /sys/bus/usb/drivers/cdc_acm/unbind
```
3. Incluir o usuário no grupo plugdev
```sudo usermod -a -G plugdev <username>```
 

### Impressora Diebold:
1. Criar o arquivo */etc/udev/rules.d/00-diebold.rules* com o seguinte conteúdo:
```SUBSYSTEM=="usb", ATTRS{idVendor}=="03f4", ATTRS{idProduct}=="2006", MODE="0664", GROUP="plugdev", RUN+="/bin/sh -c 'echo -n $id:1.0 > /sys/bus/usb/drivers/usblp/unbind'"```
2. Copiar shell script abaixo para */usr/local/bin/unbind_printer.sh*:
```
#!/bin/bash
echo ' ' > /dev/usb/lp0 && echo ' ' > /dev/usb/lp0
PORTID=$(grep -l '3f4/2006' /sys/bus/usb/devices/*/uevent | tail -1 | tr "/" " " | awk '{print $5}')
echo -n ${PORTID:0:3}:1.0 >  /sys/bus/usb/drivers/usblp/unbind
echo -n ${PORTID:0:3} >  /sys/bus/usb/drivers/usb/unbind
```
3. Incluir o usuário no grupo plugdev
```sudo usermod -a -G plugdev <username>```

 
### Utilitários
- Verificar logs   
```chrome://device-log/```
- Autorizações USB   
```chrome://settings/content/usbDevices?search=usb```
- udev monitor
``` udevadm monitor ```   
- Testar as configurações de um device sem carregar   
``` udevadm test --action="change" /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/ ```  
- Reload das configurações udev   
``` udevadm control --reload ```
- Restart udev   
```sudo service udev restart```

