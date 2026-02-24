# Infrastruktura Sieciowa dla Małej Firmy IT

Projekt zaliczeniowy z przedmiotu Projektowanie i Obsługa Sieci Komputerowych (Uniwersytet Bielsko-Bialski, semestr 5, 2025/26). Celem projektu jest stworzenie planu budynku oraz infrastruktury sieciowej dla małej firmy informatycznej.

## Architektura Sieci i Podział na VLAN-y
Sieć została zaprojektowana z myślą o szybkim transferze danych, bezpieczeństwie oraz niezawodnym dostępie do internetu dla zespołu programistów, testerów i administracji. Zastosowano następujący podział logiczny:
* **VLAN 10 (Programiści):** Adresacja 192.168.10.0/24. Zapewnia pełny dostęp do serwera kodu źródłowego i repozytoriów Git.
* **VLAN 20 (Testerzy):** Adresacja 192.168.20.0/24. Umożliwia dostęp do środowisk testowych i narzędzi QA.
* **VLAN 30 (Administracja):** Adresacja 192.168.30.0/24. Służy do zarządzania infrastrukturą sieciową, serwerami i monitoringu.
* **VLAN 40 (Serwery):** Adresacja 192.168.40.0/24. Przeznaczony do przechowywania danych firmowych i kopii zapasowych.
* **VLAN 50 (Biuro zarządu):** Adresacja 192.168.50.0/24. Dostęp do zasobów administracyjnych i dokumentacji.
* **VLAN 60 (Domyślny) i VLAN 1 (Management):** Odpowiednio adresacje 192.168.60.0/24 oraz 192.168.1.0/24.

## Sprzęt Sieciowy i Serwerowy
Centralnym punktem sieci jest szafa rack 24U (Lanberg 19" 600x800) zlokalizowana w serwerowni. W jej skład wchodzą:
* **Router:** Cisco C921-4P. Odpowiada za routing między VLAN-ami oraz połączenie z siecią WAN.
* **Firewall:** Cisco Firepower 1010. Dedykowane urządzenie typu Next-Generation Firewall (NGFW) oddzielający sieć wewnętrzną od publicznej sieci WAN.
* **Przełączniki (Switche):** 2x Cisco CBS220-24P-4G-EU z obsługą zasilania PoE.
    * **Switch 1:** Obsługuje biura programistów i testerów (VLAN 10 i 20).
    * **Switch 2:** Obsługuje administrację, serwerownię, kamery i punkty dostępowe (VLAN 30 i 40).
* **Punkty dostępowe (AP):** 2x Cisco Business CBW150AX-E. Zapewniają bezprzewodowy dostęp do sieci w biurach.
* **Serwery:** Serwer Dell PowerEdge R450 (wirtualizacja serwera Git i testowego) oraz serwer NAS Synology DS423 z dyskami WD Red Plus 4TB (kopie zapasowe).
* **Monitoring:** System oparty o zasilanie PoE składający się z 4 kamer zewnętrznych, 4 wewnętrznych (Reolink) oraz rejestratora NVR.
* **Zasilanie awaryjne:** UPS PowerWalker VI 1500 R1U. Zabezpiecza kluczowe urządzenia przed utratą zasilania.

## Okablowanie
* **Okablowanie poziome:** Skrętka UTP/FTP Kategorii 6 (Cat6) obsługująca standard 1Gb/s. Wykorzystano łącznie około 750 metrów kabla.
* **Gniazda:** Zastosowano 9 podwójnych gniazdek RJ-45 w standardzie T568B.
* **Patchcordy:** Kable Cat6 zapewniające połączenia w szafie Rack oraz przy stanowiskach pracy.

## Symulacja i Konfiguracja
Całość topologii oraz konfiguracja urządzeń sieciowych (w tym konfiguracja VLAN, adresacja IP, protokoły oraz zabezpieczenia port-security) została przygotowana, zamodelowana i przetestowana z wykorzystaniem oprogramowania Cisco Packet Tracer.
