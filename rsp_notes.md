
### Tools

   * bridge-utils 
     Dienstprogramme für die Konfiguration der Linux-Ethernet-Brücke
   *sshfs
     Dateisystemclient, der auf dem SSH-Dateiübertragungsprotokoll basiert


### Setting up Card

   * Erase Card and format to __FAT( MS DOS )__
   * unmount newly created partition
   * sudo dd if=... of=... __of disk not the partition

### Setting up SSH

   * Connect rspy to Monitor
   * Get IP via __ifconfig__ 
   * log in to rsp via ssh
   * adding fixed ip-address to rspy 
   * log to rspy using __ssh pi@192.168.0.X__

### Setting up SSH without password

   Helping save a lot of time. 

   * Run command __ssh-keygen__ on host
   * upload id_rsa.pub__ to Raspberry with Command 
     __scp id_rsa.pub pi@192.168.0.X:ssh/authorized_key__
   * Mount pair folder in Host with command
     __sshfs pi@192.168.0.X:home/pi /name/of/remotepath_host__


### Conclusion. 
    this is a short description( memo ) of what I do to work in a convenient
    manner on my raspberry-pi. 
    __Feel free to do what ever you want with this document__
    __I m in no way responsable on how this setup may affect you infracsture__
