# O que é o OpenStack e como pode ajudar você?

O OpenStack é um software Open Source que você pode instalar em vários servidores
e serve para agregar uma camada de orquestração (uma camada de gerenciamento 
através de interface web, API ou CLI).

Cada um desses servidores será responsável por um ou mais serviços do OpenStack, 
já que o mesmo é totalmente modular. Por exemplo:

Você pode fazer uma arquitetura com um controller, um network node e 1 ou mais 
compute nodes, nesse caso cada um desses servidores ficaria responsável por um ou
mais serviços.

## CONTROLLER

Serviço de mensageria: (ex: RabbitMq) que é responsável por administrar as filas 
de mensagens trocadas entre todos os serviços do OpenStack.

Banco de dados: (ex: MariaDB) onde estarão todas as bases de dados dos serviços do
OpenStack (serviço de rede, imagens, computação, armazenamento de objetos, 
armazenamento de blocos, etc). Para cada um dos serviços que serão utilizados na sua
nuvem precisará existir uma base de dados no serviço de DB do controller.

Você também pode instalar no controller alguns serviços que não requerem um node 
dedicado, como glance (serviço de imagens), Cinder (block storage), Ceilometer 
(telemetria), Heat (orquestração), etc. Mas você também pode instalar esses serviços
em nodes dedicados, pois o OpenStack é como se fosse um quebra-cabeças, você instala
os serviços e conecta um com o outro.

## NETWORK NODE

Serviço de Rede: Neutron – Esse serviço pode ser instalado em um servidor separado
(ou mais de um servidor configurados em HA), ele é responsável por fornecer os 
recursos de rede para a nuvem (interfaces, firewall, load balance, vpn, portas L2, 
etc).

## COMPUTE NODES

Esses nodes são responsáveis por toda a parte de computação, ou seja, por hospedar
as instâncias (máquinas virtuais). O serviço que gerencia as instâncias e interage
com o hypervisor (que podem ser vários: KVM, XEN, VMWARE, HYPER-V, QEMU, etc…) é 
o Nova Compute.

Esses nodes podem ser adicionados à nuvem conforme a necessidade de recursos, assim 
sua nuvem se torna verticalmente escalável.
