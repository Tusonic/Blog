show system interface port1
    config system interface
        edit "port1"
            set vdom "root"
            set ip 192.168.1.99 255.255.255.0
            set allowaccess ping https ssh
            set type hard-switch
            set stp enable
            set role lan
            set snmp-index 6
        next
    end
show system interface port1
ta komenda wyświetla konfigurację dla interfejsu o nazwie "port1". Pozwala to na sprawdzenie aktualnych ustawień dla tego portu, takich jak adres IP, maska podsieci, typ interfejsu, dostępne metody dostępu itp.
config system interface
ta komenda przechodzi do trybu konfiguracji interfejsów systemowych. W tym trybie można dodawać, edytować lub usuwać interfejsy sieciowe w urządzeniu FortiGate.
edit "port1"
ta komenda wybiera interfejs o nazwie "port1" do edycji. Wszystkie poniższe komendy będą dotyczyć tego interfejsu.
set vdom "root"
przypisuje interfejs do domeny wirtualnej (VDOM) o nazwie "root". FortiGate pozwala na tworzenie wielu VDOM-ów, które działają jak oddzielne urządzenia wirtualne w obrębie tego samego urządzenia fizycznego.
set ip 192.168.1.99 255.255.255.0
ustawia adres IP dla interfejsu na 192.168.1.99 z maską sieci 255.255.255.0. Jest to konfiguracja adresacji IPv4.
set allowaccess ping https ssh
umożliwia dostęp do interfejsu za pomocą protokołów ping, HTTPS i SSH. Oznacza to, że do urządzenia można się połączyć zdalnie przy użyciu tych protokołów.
set type hard-switch
określa typ interfejsu jako fizycznie przełączany ("hard-switched"). To ustawienie dotyczy sposobu przetwarzania ruchu przez interfejs.
set stp enable
włącza protokół Spanning Tree Protocol (STP) na interfejsie. STP zapobiega pętlom sieciowym w sieciach Ethernet.
set role lan
określa rolę interfejsu jako LAN (Local Area Network). To ustawienie ma znaczenie dla polityk routingu i bezpieczeństwa.
set snmp-index 6
przypisuje indeks SNMP (Simple Network Management Protocol) dla interfejsu, co jest używane do monitorowania i zarządzania urządzeniami sieciowymi.