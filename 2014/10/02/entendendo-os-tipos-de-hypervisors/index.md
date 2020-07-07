# Entendendo os tipos de Hypervisors


****Esxi ****– É o core do Vsphere suíte, ele é responsável pela camada de virtualização dos servidores é parte fundamental para os demais produtos da suíte. Existe uma diferença entre a versão anterior da suíte, onde o Hypervisor estava disponível em duas diferentes versões ESX e ESXi. Ambos produtos compartilham a mesma engine, suportam as mesmas features e usam o mesmo modelo de licenciamento, e  ambos são considerados bare-metal installation. No ESX a vmware usava uma derivação do Linux como service console, no caso o Redhat. A service console provia uma interface de gerenciamento para os hosts, que permitia a interação direta com o Host. A service console também incluía serviços tradicionais como firewall, agentes de simple network management protocol (SNMP) além de web server.

<!-- more -->

Tipos de Hypersivor:

Geralmente os hypervisor são agrupados em duas classes, Hypervisors do tipo 1 e do tipo 2.

****Tipo 1**** – o Hypervisor é executado diretamente no hardware físico e muitas vezes é referido como bare-metal hypervisor. Ex. Esxi e Xenserver.

****Tipo 2**** -  O hypervisor requer um sistema operacional host para prover suporte a I/O e gerenciamento de memória. Ex. Vmware Workstation e VirtualBox

