*__This book is dedicated to those who relentlessly pursue knowledge and selflessly
share it with others__*.


## Introduction


- O processo de aprendizagem da engenharia reversa é semelhante ao de aprendizado de uma língua estrangeira para um adulto. A
primeira fase do aprendizado de uma língua estrangeira começa com uma introdução às letras do alfabeto, que são usadas para
construir palavras com semântica bem definida. A próxima fase envolve a compreensão das regras gramaticais que definem como as
palavras são coladas para produzir uma frase adequada. Depois de se acostumar com essas regras, a pessoa aprende a costurar
várias frases para articular pensamentos complexos. Eventualmente chega ao ponto em que o aluno pode ler livros grandes 
escritos em estilos diferentes e ainda compreender os pensamentos neles contidos. Neste ponto, pode-se ler livros de
referência sobre os aspectos mais esotéricos da linguagem - sintaxe histórica, fonologia e assim por diante.


- No caso da engenharia reversa, a "língua" é a arquitetura/linguagem assembly. Uma palavra é uma instrução assembly. 
Os parágrafos são sequências de instruções assembly. Um livro é um programa. No entanto, para compreender totalmente um
livro, o leitor precisa saber mais do que apenas vocabulário e gramática. Esses elementos adicionais incluem estrutura e 
estilo de prosa, regras não escritas de escrita e outros. Compreender os programas de computador também requer o domínio de 
conceitos além das instruções assembly.


- Pode ser um tanto intimidante começar a aprender um assunto técnico inteiramente novo em um livro. No entanto, estaríamos 
enganando você se alegássemos que a engenharia reversa é um esforço de aprendizado simples e que pode ser completamente
dominado pela leitura deste livro. O processo de aprendizagem é bastante complexo porque requer conhecimento de vários 
domínios díspares do conhecimento. Por exemplo, um engenheiro reverso eficaz precisa ter conhecimento em arquitetura de 
computador, programação de sistemas, sistemas operacionais, compiladores e assim por diante. Para certas áreas, uma sólida 
formação matemática é necessária.


- Para fins de discussão, definimos vagamente a engenharia reversa como o processo de compreensão de um sistema. É um processo  de resolução de problemas. Esse "sistema" pode ser um dispositivo de hardware, um programa de software, um processo
físico ou químico e assim por diante. Para os objetivos do livro, o "sistema" é um programa de software. Para entender um
programa, você deve primeiro entender como o software é escrito. Portanto, o primeiro requisito é saber programar um
computador por meio de uma linguagem como C, C ++, Java e outras. Sugerimos primeiro aprender C devido à sua simplicidade,
eficácia e onipresença. Algumas referências excelentes a serem consideradas são :

1. The C Programming Language, de Brian Kernighan e Dennis Ritchie (Prentice Hall, 1988) 
2. C : A Reference Manual, de Samuel Harbison (Prentice Hall, 2002). 
3. C Programming: Deep C Secrets, de Peter Van Der Linden (Prentice Hall, 1994). 

- Neste ponto, você deve estar familiarizado com os conceitos de alto nível, como variáveis, escopos, funções, ponteiros,
condicionais, loops, call stacks e libraries. O conhecimento das estruturas de dados, como pilhas, queues , linked lists e threes pode ser útil, mas não são inteiramente necessário por agora. Para terminar, você pode folhear os seguintes livro:

1. Compilers: Principles, Techniques and Tools, de Alfred Aho, Ravi Sethi  e Jeffrey Ullman(Prentice Hall, 1994)
2. Linkers and Loaders, de John Levine (Morgan Kaufmann, 1999),

- Para entender melhor  como um programa é realmente montado. O objetivo principal da leitura desses livros é obter exposição aos conceitos básicos; você não precisa entender todas as páginas por enquanto (haverá tempo para isso mais tarde).

- Depois de ter um bom entendimento de como os programas são geralmente escritos, executados e depurados, você deve começar a 
explorar o ambiente de execução do programa, que inclui o processador e o sistema operacional. Sugerimos aprender primeiro 
sobre o processador Intel, folheando o Manual do desenvolvedor de software das arquiteturas Intel 64 e IA-32 Volume 1: 
Arquitetura básica da Intel, com atenção especial aos capítulos 2–7. Esses capítulos explicam os elementos básicos de um 
computador moderno. Os leitores interessados ​​em ARM devem considerar o Guia do Programador da Série Cortex-A e o Manual de 
Referência de Arquitetura ARMv7-A e ARMv7-R Edition da ARM. Embora nosso livro cubra x86 / x64 / ARM, não discutimos todos os
detalhes arquitetônicos. (Presumimos que o leitor irá consultar esses manuais, conforme necessário.) Ao folhear-los você deve
ter uma compreensão básica dos blocos de construção técnicos de um sistema de computação. Para uma compreensão mais
conceitual, considere Structured Computer Organization de Andrew Tanenbaum (Prentice Hall, 1998).


- Em seguida, você deve explorar o sistema operacional. Existem muitas diferenças entre sistemas operacionais, mas eles
compartilham  muitos conceitos comuns, incluindo Process, Threads, Virtual Memory, Separação de Privilégios, Multitarefa e
assim por  diante. o melhor maneira de entender esses conceitos é ler Sistemas operacionais modernos(by Tenenbaum). Embora o
texto de Tanenbaum seja excelente para conceitos, não discute detalhes técnicos importantes para sistemas operacionais da vida
real. Para Windows, você deve considerar folhear o **Windows NT Device Driver Development**, por Peter Viscarola e
Anthony Mason (Novo Riders Press, 1998); embora seja um livro sobre desenvolvimento de driver, o background de alguns
capítulos fornecem uma introdução excelente e concreta ao Windows. (Isso é também excelente material suplementar para o
capítulo do Windows Kernel neste livro.) Para inspiração adicional (e um excelente explanação de Windows Memory Menager), você
também deve ler a página What Makes It? O Windows 7 (x64) Virtual Memory Manager, por Enrico Martignetti (CreateSpace
Independent Publishing Platform, 2012).


- Neste ponto, você terá todo o conhecimento necessário para ler e entender o Capítulo 3 “O Kernel do Windows”. Você também
deve considerar aprender programação Win32. 

1. Programação do Sistema Windows, de Johnson Hart (Addison-Wesley Professional,2010)
2. Windows via C / C ++, de Jeffrey Richter e Christophe Nasarre (Microsoft Press, 2007)

São excelentes referências. Para o Capítulo 4, “Depuração e automação”, considere Por Dentro da Depuração do Windows:

1. Um Guia Prático para Estratégias de Depuração e Rastreamento no Windows, por Tarik Soulami (Microsoft Press, 2012)
2. Advanced Windows Debugging, de Mario Hewardt e Daniel Pravat (Addison-Wesley Professional, 2007). 



## Chapter 0x01 - x86 and x64


- O x86 é a arquitetura little-endian baseada no processador Intel 8086. Para o propósito de nosso capítulo, x86 é a
implementação de 32 bits da arquitetura Intel (IA-32), conforme definido no Intel Software Development Manual. De um modo
geral, pode operar em dois modos: real e protegido. O modo real é o estado do processador quando é ligado pela primeira vez e
suporta apenas um conjunto de instruções de 16 bits. O modo protegido é o estado do processador com suporte para memória
virtual, paginação e outros recursos; é o estado em que os sistemas operacionais modernos são executados. A extensão de 64
bits da arquitetura é chamada de x64 ou x86-64. Este capítulo discute o Arquitetura x86 operando em modo protegido.

- O x86 oferece suporte ao conceito de separação de privilégios por meio de uma abstração chamada Ring Level. O processador
suporta quatro Ring Levels, numerados de 0 a 3. (Os rings 1 e 2 não são comumente usados, portanto não são discutidos
aqui.) O Ring 0 é o nível de privilégio mais alto e pode modificar todas as configurações do sistema. O Ring 3 é o nível de
privilégios mais baixo e só pode ler/modificar um subconjunto das configurações do sistema. Portanto, os sistemas
operacionais modernos geralmente implementam a separação de privilégios de Userland/Kerneland por ter aplicativos em
user-mode executados no Ring 3 e os de kernel-mode no Ring 0. O Ring Level é codificado no registrador CS e às vezes referido
como o nível de privilégio atual (CPL) na documentação oficial.


Este capítulo discute a arquitetura x86 / IA-32 conforme definida no Intel 64 e IA-32 Architectures Software Developer’s Manual, Volumes 1–3 (www.intel.com/content/www/us/en/processors/architectures-software-developermanuals.html)




### Registers Set and Data Types


**GPRs - General Porpouse Registers**


- Ao operar em Protect-mode, a arquitetura x86 fornece 8 registradores de uso geral de 32 bits. São os seguintes GPRs:

		EAX, EBX, ECX, EDX, EDI, ESI, EBP, and ESP.

- Alguns destes podem ser subdividios em registradores de 16 ou 8 bits.
- O Instruction Pointer(ponteiro da proxima instrução), é armazenado no registrador :

		EIP


_Alguns registradores e seus propósitos_:

ECX = usado como contador nas implementações de loop
ESI = usado como origem em operações com strings/memory
EDI = usado como destino em operações com strings/memory

EBP = Base frame pointer
ESP = Stack pointer


- Tipos de dados mais cumuns :


**BYTE** - 8 bits . 	Ex : AL,BL,AH,BH
**WORD** - 16 bits . 	Ex : AX,BX,SI
**DWORD**- 32 bits .  	Ex : EAX,EBX,EDI
**QWORD**- 64 bits . 	Embora o x86 não tenha GPRs de 64 bits, ele pode combinar dois registradores, tipo( EDX:EAX ), e
tratá-los como valores de 64 bits em alguns cenários. Exemplo: , a instrução **RDTSC** grava um valor de 64 bits em EDX:EAX


**EFLAGS** = O registrador EFLAGS de 32 bits é usado para armazenar o status de operações aritméticas e outros estados de
execução (por exemplo, Trap Flag). Quando a instrução "ADD" anterior resultou em zero, **ZF**(Zero Flag) será definido como 1.
As flags de EFLAGS são usados principalmente para implementar ramificação condicionais.


- Além dos GPRs, EIP e EFLAGS, também existem registradores que controlam mecanismos importantes do sistema de low-level,como
virtual memory, interrupts e degugging. Por exemplo :

CR0 = controla se a paginação está ativada ou desativada
CR2 = contém o endereço linear que causou uma falha de página
CR3 = é o endereço base de uma estrutura de dados de paginação
CR4 = controla as configurações de virtualização de hardware. 
DR0 – DR7 =  são usados por Memory Breakpoints.Voltaremos a esses registradores mais tarde na seção “Mecanismo do sistema”.

_NOTE: Embora haja sete registradores de debugging, o sistema permite apenas quatro Memory BreakPoints (DR0-DR3).
Os registradores restantes são usados para status._


- Existem também registradores específicos do modelo (MSRs). Como o nome indica, esses registradores podem variar entre os
diferentes processadores da Intel e AMD. Cada MSR é identificado por nome e um número de 32 bits, e é lido/escrito por meio
das instruções RDMSR/WRMSR. Eles são acessíveis apenas ao código rodando em ring 0 e normalmente são usados para armazenar
contadores especiais e implementar funcionalidade de low-level. Por exemplo, a instrução **SYSENTER** transfere a execução
para o endereço armazenado no IA32_SYSENTER_EIP (MSR (0x176), que geralmente é o sistema operacional que gerencia as
systemsCalls ( chamadas de sistema ). MSRs são discutidos ao longo do livro à medida que aparecem.



### Instrutions Set

- 

