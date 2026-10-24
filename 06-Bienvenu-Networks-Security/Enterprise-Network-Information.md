==========================================================================================================================

&#x20;                                             ENTERPRISE CORE HARDWARE REGISTRY

==========================================================================================================================

DEVICE TYPE  | DEVICE NAME     | IP ADDRESS      | PORT / INTERFACE

=========+=====================+=================+========================================================================

Router       | Router0         | 10.0.0.1        | GigabitEthernet 0/0 (Backbone Link to Router1)

Router       | Router1         | 10.0.0.2        | GigabitEthernet 0/0 (Backbone Link to Router0)

\------------+-----------------+-----------------+------------------------------------------------------------------------

L3 Switch    | L3-SW1          | 192.168.99.1    | Interface VLAN 99 (Active SVI Gateway)

L3 Switch    | L3-SW2          | 192.168.99.254  | Interface VLAN 99 (Active SVI Gateway)

L3 Switch    | L3-SW3          | 192.168.99.2    | Interface VLAN 99 (Active SVI Gateway)

L3 Switch    | L3-SW4          | 192.168.99.253  | Interface VLAN 99 (Active SVI Gateway)

\------------+-----------------+-----------------+------------------------------------------------------------------------

Switch       | ACCESS-SW1      | 192.168.99.10   | Interface VLAN 99 (Management Plane)

Switch       | ACCESS-SW2      | 192.168.99.11   | Interface VLAN 99 (Management Plane)

Switch       | ACCESS-SW3      | 192.168.99.12   | Interface VLAN 99 (Management Plane)

Switch       | ACCESS-SW4      | 192.168.99.13   | Interface VLAN 99 (Management Plane)

Switch       | ACCESS-SW5      | 192.168.99.14   | Interface VLAN 99 (Management Plane)

Switch       | ACCESS-SW6      | 192.168.99.15   | Interface VLAN 99 (Management Plane)

\------------+-----------------+-----------------+------------------------------------------------------------------------

Server       | Server0         | 192.168.100.2   | FastEthernet 0 (Central Infrastructure Management Node)

==========================================================================================================================



==========================================================================================================================

&#x20;                                                  MAIN OFFICE NETWORK

==========================================================================================================================

VLAN ID  | DEPARTMENT NAME     | NETWORK             | DEFAULT-GATEWAY

=========+=====================+=====================+====================================================================

VLAN 10  | INFORMATION-TECH    | 192.168.10.0/24     | 192.168.10.1

VLAN 20  | CUSTOMER-SERVICE    | 192.168.20.0/24     | 192.168.20.1

VLAN 30  | SALES               | 192.168.30.0/24     | 192.168.30.1

VLAN 40  | LEGAL               | 192.168.40.0/24     | 192.168.40.1

VLAN 50  | MARKETING           | 192.168.50.0/24     | 192.168.50.1

VLAN 60  | HUMAN-RESOURCES     | 192.168.60.0/24     | 192.168.60.1

VLAN 99  | MANAGEMENT          | 192.168.99.0/24     | 192.168.99.1

VLAN 100 | SERVERS             | 192.168.100.0/24    | 192.168.100.1

==========================================================================================================================



==========================================================================================================================

&#x20;                                                 MAIN OFFICE SITE PROFILE

==========================================================================================================================

BUILDING:  BUILDING A

LOCATION:  HELSINKI

COMPANY:   BIENVENU NETWORKING AND SECURITY

\---------+----------------------------------------------------------------------------------------------------------------

DEPARTMENTS \& STAFF ROSTER:

\---------+----------------------------------------------------------------------------------------------------------------

LEGAL:               GOKU, VEGETA, GOHAN, PICCOLO, BULMA, KRILIN

MARKETING:           TANJIRO, ZENITSU, INOSUKE, MUZAN, NEZUKO, AKAZA, GYUTARO

HR:                  ICHIGO, AIZEN, YAMAMOTO, RENJI, RUKIA, SHINJI

IT:                  SHIN, OUKI, TOU, KANKI, OUSEN, RIBOKU

CUSTOMER-SERVICE:    NAMI, ROBIN, FRANKY, LUFFY, ZORO, SANJI

SALES:               SINBAD, DAVID, SOLOMON, ALIBABA, JAFAR, ALADDIN

==========================================================================================================================



