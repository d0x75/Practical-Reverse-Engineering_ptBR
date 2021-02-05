# Capítulo 0x03 - The Windows Kernel


Este capítulo discute os princípios e técnicas necessárias para analisar o código do driver do modo kernel, como rootkits, na plataforma Windows. Como os drivers interagem com o sistema operacional por meio de interfaces bem definidas, a tarefa analítica pode ser decomposta nos seguintes objetivos gerais:

■ Compreender como os principais componentes do sistema operacional são implementados
■ Compreender a estrutura de um driver
■ Compreender as interfaces do driver do usuário e do sistema operacional do driver e como o Windows as implementa
■ Compreender como certas construções de software de driver se manifestam em forma binária
■ Aplicar sistematicamente o conhecimento das etapas anteriores no processo geral de engenharia reversa 


Se o processo de engenharia reversa dos drivers do Windows pudesse ser modelado como uma tarefa discreta, 90% estariam entendendo como o Windows funciona e 10% estariam entendendo o código assembly. Portanto, o capítulo foi escrito como uma introdução ao kernel do Windows para engenheiros reversos.Ele começa com uma discussão sobre as interfaces do kernel do usuário e sua implementação. A seguir, ele discute listas vinculadas e como elas são usadas no Windows. Em seguida, ele explica conceitos como threads, processos, memória, interrupções e como eles são usados no kernel e drivers. Depois disso, ele vai para a arquitetura de um driver do modo kernel e a interface de programação do driverkernel. Ele conclui aplicando esses conceitos à engenharia reversa de um rootkit.

A menos que especificado de outra forma, todos os exemplos neste capítulo foram retirados do Windows 8 RTM.




## Windows Fundamentals


Começamos com uma discussão dos principais conceitos do kernel do Windows, incluindo estruturas de dados fundamentais e objetos do kernel relevantes para a programação do driver e engenharia reversa.



### Memory Layout

Como muitos sistemas operacionais, o Windows divide o espaço de endereço virtual em duas partes: kernel e espaço do usuário. No x86 e ARM, os 2 GB superiores são reservados para o kernel e os 2 GB inferiores são para os processos do usuário. Portanto, endereços virtuais de 0 a 0x7fffffff estão no espaço do usuário, 0x80000000 e acima estão no espaço do kernel. No x64, o mesmo conceito se aplica, exceto que o espaço do usuário é de 0 a 0x000007ff`ffffffff e o espaço do kernel é 0xffff0800`00000000 e acima. A Figura 3-1 ilustra o layout geral em x86 e x64. O espaço de memória do kernel é basicamente o mesmo em todos os processos. No entanto, os processos em execução só têm acesso ao espaço de endereço do usuário; o código do modo kernel pode acessar ambos. (Alguns intervalos de
endereços do kernel, como aqueles em sessão e hiperespaço, variam de processo para.) Este é um fato importante a se ter em mente, 
porque voltaremos a ele mais tarde, ao discutir o contexto de execução. As páginas dos modos kernel e usuário são diferenciadas por um bit especial em sua entrada na tabela de páginas.



Quando um thread em um processo é agendado para execução, o sistema operacional altera um registro específico do processador para apontar para o diretório da página desse processo em particular. Isso ocorre para que todas as traduções de endereços virtuais para físicos sejam específicas para o processo e não para outros. É assim que o sistema operacional pode ter vários processos e cada um tem a ilusão de que possui todo o espaço de endereço do modo de usuário. Nas arquiteturas x86 e x64, o registro base do diretório da página é CR3; no ARM é o registro base da tabela de tradução (TTBR).



**NOTA** : É possível alterar esse comportamento padrão especificando a opção / 3GB nas opções de inicialização. Com / 3GB, o espaço de endereço do usuário aumenta para 3GB e o 1GB restante é para o kernel. Os intervalos de endereço do usuário / kernel são armazenados em dois símbolos no kernel:
MmSystemRangeStart (kernel) e MmHighestUserAddress (usuário). Esses símbolos podem ser visualizados com um depurador de kernel. Você pode notar que há um intervalo de 64 KB entre o espaço do usuário / kernel no x86 / ARM. Esta região, normalmente conhecida como região sem acesso, existe para que o kernel não cruze acidentalmente o limite do endereço e corrompa a memória do modo de usuário. No x64, o leitor astuto pode perceber que 0xffff0800`00000000 é um endereço não canônico e, portanto, inutilizável pelo sistema operacional. Este endereço é realmente usado apenas como um separador entre o espaço do usuário / kernel. O primeiro endereço utilizável no espaço do kernel começa em 0xffff8000`00000000.






