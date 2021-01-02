## Instrodução


O processo de aprendizagem da engenharia reversa é semelhante ao de aprendizado de uma língua estrangeira para um adulto. A
primeira fase do aprendizado de uma língua estrangeira começa com uma introdução às letras do alfabeto, que são usadas para
construir palavras com semântica bem definida. A próxima fase envolve a compreensão das regras gramaticais que definem como as
palavras são coladas para produzir uma frase adequada. Depois de se acostumar com essas regras, a pessoa aprende a montar
várias frases para articular pensamentos complexos. Eventualmente chega ao ponto em que o aluno pode ler livros grandes 
escritos em estilos diferentes e ainda compreender os pensamentos neles contidos. Neste ponto, pode-se ler livros de
referência sobre os aspectos mais esotéricos da linguagem - sintaxe histórica, fonologia e assim por diante.


No caso da engenharia reversa, a "língua" é a arquitetura do processador(assembly). Uma palavra é uma instrução assembly. 
Os parágrafos são sequências de instruções assembly. Um livro é um programa. No entanto, para compreender totalmente um
livro, o leitor precisa saber mais do que apenas vocabulário e gramática. Esses elementos adicionais incluem "estrutura e 
estilo de prosa, vocabulario informal" e outros. Compreender os programas de computador também requer o domínio de 
conceitos além das instruções assembly.


Pode ser um tanto intimidante começar a aprender um assunto técnico inteiramente novo em um livro. No entanto, estaríamos 
enganando você se alegássemos que a engenharia reversa é um esforço de aprendizado simples e que pode ser completamente
dominado pela leitura deste livro. O processo de aprendizagem é bastante complexo porque requer conhecimento de vários 
domínios diferentes do conhecimento. Por exemplo, um engenheiro reverso eficaz precisa ter conhecimento em arquitetura de 
computador, programação de sistemas, sistemas operacionais, compiladores e assim por diante. Para certas áreas, uma sólida 
formação matemática é necessária.


Para fins de discussão, definimos vagamente a engenharia reversa como o processo de entender como um sistema funciona.Esse
"sistema" pode ser um dispositivo de hardware, um programa de software, um processo físico ou químico e assim por diante.Para
os objetivos deste livro, o "sistema" é um *programa de software*.

Para entender um software, você deve primeiro aprender como escrevemos um software. Portanto, o primeiro requisito é saber programar com linguagens como C, C ++, Java e outras. Sugerimos primeiro aprender C devido à sua simplicidade, eficácia e onipresença. Algumas referências excelentes a serem consideradas são :

1. The C Programming Language, de Brian Kernighan e Dennis Ritchie (Prentice Hall, 1988) 
2. C : A Reference Manual, de Samuel Harbison (Prentice Hall, 2002). 
3. C Programming: Deep C Secrets, de Peter Van Der Linden (Prentice Hall, 1994). 


- Depois de ter compreendido os conceitos de alto nível, como variáveis, escopos, funções, ponteiros, condicionais, loops,
call stacks e libraries. O conhecimento das estruturas de dados, como pilhas, queues , linked lists e threes pode ser útil,
mas não são inteiramente necessário por agora. Para terminar, você pode folhear os seguintes livro:

1. Compilers: Principles, Techniques and Tools, de Alfred Aho, Ravi Sethi  e Jeffrey Ullman(Prentice Hall, 1994)
2. Linkers and Loaders, de John Levine (Morgan Kaufmann, 1999)


- Depois de ter um bom entendimento de como os programas normalmente são escritos, executados e depurados, você deve começar a 
explorar o ambiente de execução do programa, que inclui o processador e o sistema operacional. Sugerimos aprender primeiro 
sobre o processador Intel, folheando o Manual do desenvolvedor de software das arquiteturas Intel 64 e IA-32 Volume 1: 
Arquitetura básica da Intel, com atenção especial aos capítulos 2–7. Esses capítulos explicam os elementos básicos de um 
computador moderno. Os leitores interessados ​​em ARM devem considerar o Guia do Programador da Série Cortex-A e o Manual de 
Referência de Arquitetura ARMv7-A e ARMv7-R Edition da ARM. Embora nosso livro cubra x86 / x64 / ARM, não discutimos todos os
detalhes arquitetônicos. (Presumimos que o leitor irá consultar esses manuais, conforme necessário.) Ao folhear-los você deve
ter uma compreensão básica dos blocos de construção técnicos de um sistema de computação. Para uma compreensão mais
conceitual, considere Structured Computer Organization de Andrew Tanenbaum (Prentice Hall, 1998).


- Em seguida, você deve explorar o sistema operacional. Existem muitas diferenças entre sistemas operacionais, mas eles
compartilham  muitos conceitos comuns, incluindo Process, Threads, Virtual Memory, Separação de Privilégios, Multithreads e
assim por  diante. A melhor maneira de entender esses conceitos é ler Sistemas operacionais modernos(by Tenenbaum). Embora o
texto de Tanenbaum seja excelente para conceitos, não discute detalhes técnicos importantes para sistemas operacionais da vida
real. Para Windows, você deve considerar folhear o livro:

>Windows NT Device Driver Development por Peter Viscarola e Anthony Mason (Novo Riders Press, 1998).

Embora seja um livro sobre desenvolvimento de driver, o background de alguns capítulos fornecem uma introdução excelente e
concreta ao Windows. (Isso é também excelente material suplementar para o capítulo do Windows Kernel neste livro.) Para
inspiração adicional (e um excelente explanação de Windows Memory Menager), você também deve ler :

>>What Makes It? O Windows 7 (x64) Virtual Memory Manager, por Enrico Martignetti


- Neste ponto, você terá todo o conhecimento necessário para ler e entender o Capítulo 3 “O Kernel do Windows”. Você também
deve considerar aprender programação Win32. 

1. Programação do Sistema Windows, de Johnson Hart (Addison-Wesley Professional,2010)
2. Windows via C / C ++, de Jeffrey Richter e Christophe Nasarre (Microsoft Press, 2007)

São excelentes referências. Para o Capítulo 4, “Depuração e automação”, considere Por Dentro da Depuração do Windows:

1. Um Guia Prático para Estratégias de Depuração e Rastreamento no Windows, por Tarik Soulami (Microsoft Press, 2012)
2. Advanced Windows Debugging, de Mario Hewardt e Daniel Pravat (Addison-Wesley Professional, 2007). 