# VMFS 5 – Principais Características


Suporte a volumes de 2TB para cada VMFS, isso aumenta a flexibilidade para seu adm de storage, quando cria ou usa a LUN, você pode usar 64 TB de volumes estendidos. Padrão 1MB file system block size com suporte de 2TB virtual disks. Em versões anteriores um block size de tamanho maior era requerido, e o adm tinha que decidir se queria uma maior capacidade ou uma performance melhor.


Clustered file system - cluster file system permite acesso ao discos por varios hosts
<!-- more -->

Encapsulation - VMS que residem no VMFS tem seus dados organizados e encapsulados em diretorios


Dynamic growth - VMFS podem ser expandidos e extendidos permitindo flexibilidade e escalabilidade, esse processo pode acontecer com a vm em execução no datastore, VMDK podemo ser expandidos sobre VMFS volumes, em tempo de execução da vm


Backup e recoverability - VMFS permite o uso de proxys para realizar bkp, enquanto a vm esta em uso.


Large single extend volumes - storage device maiores que 2TB agora são suportados para uso como VMFS datasore, o limite novo VMFS-5 é 64TB..


Large Physical RDMs- RDM em physical compatibility mode agora tem o tamanho maximo de 64TB


Smaller sub-blocks - sub-blocos com o tamanho de 8KB os principais arquivos tem tamanho entre 1kb e 8kb vai consumir somente 8kb


Smaller file support - usado para arquivos menores ou igual a 1kb , para esses arquivos a localização da descrição do arquivo sera armazenada no metadado do VMFS se esses aquivos ficarem maiores que 1kb então esse arquivo vai iniciar usando 8kb de blocos em disco, a ideia com pequenos sub-blocos e suporte a arquivos pequenos é diminuir a quantidade de espaço em disco que é consumido por um VMFS datastore.


Large file number - aproximadamente 130 mil arquivos por datastore


ATS anhancement - hardware assited locking- tambem conhecido como Atomic test e set (ATS) agora é usado para file locking em storage devices que suportam hardware accelaration.



Suporte a 2TB disk size para RDMs em physical compatibility


Mode. Você pode usar a physical compatibility RDMs para até 64TB


Capaciadade de Online, in-place upgrade. Voce pode fazer upgrade do VMFS-3 datastores para VMFS-5 sem parada.


