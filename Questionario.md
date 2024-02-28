# Questionário Sistemas Embarcados I

## 1. Explique brevemente o que é compilação cruzada (***cross-compiling***) e para que ela serve.
<b>R:<b/> <br/>
Cross-compiling é um processo no qual o código fonte de um programa é compilado em um sistema de desenvolvimento que é diferente do sistema no qual o programa será executado. Essa abordagem é necessária quando o ambiente de desenvolvimento e o ambiente de execução têm arquiteturas de processador diferentes, sistemas operacionais diferentes, ou quando o sistema embarcado não possui recursos para realizar a compilação diretamente.

## 2. O que é um código de inicialização ou ***startup*** e qual sua finalidade?
<b>R:<b/> <br/>
É uma parte essencial que é responsável por configurar o ambiente de execução antes de transferir o controle para o programa principal. Ele é responsável pela configuração de Hardware, inicialização de memória, definição do vetor de interrupção, configuração do ambiente de execução, chamada do programa principal.

## 3. Sobre o utilitário **make** e o arquivo **Makefile responda**:

#### (a) Explique com suas palavras o que é e para que serve o **Makefile**.
<b>R:<b/> <br/>
O Makefile é um arquivo de configuração usado em conjunto com o utilitário make para automatizar o processo de compilação e construção de projetos de software.

#### (b) Descreva brevemente o processo realizado pelo utilitário **make** para compilar um programa.
<b>R:<b/> <br/>
O Make automatiza o processo de compilação dos programas lendo as regras e as dependências de um arquivo Makefile. Analizando as dependências entre arquivos fonte e objetos, o Make verifica se houve alterações e executa os comandos de compilação necessários. Ele gera objetos compilados, realiza a vinculação e cria o executável final.

#### (c) Qual é a sintaxe utilizada para criar um novo **target**?
<b>R:<b/> <br/>
A sintaxe é: <br/>
target:prerequisites <br/>
recipe <br/>
Onde os prerequisites são as dependências do target e o recipe são os comandos.

#### (d) Como são definidas as dependências de um **target**, para que elas são utilizadas?
<b>R:<b/> <br/>
As dependências de um target em um Makefile são definidas logo após o nome do target, separadas por espaços.
As dependências representam os arquivos ou outros targets que o target em questão precisa antes de ser construído. Quando o make é executado, ele verifica as datas de modificação dessas dependências em relação ao próprio target. Se alguma dependência tiver uma data de modificação mais recente do que a do target, o make entende que o target precisa ser reconstruído.

#### (e) O que são as regras do **Makefile**, qual a diferença entre regras implícitas e explícitas?
<b>R:<b/> <br/>
Em um Makefile, as regras são declarações que especificam como gerar um target. Elas indicam as dependências necessárias e os comandos que devem ser executados para criar ou atualizar o target. As regras explícitas são aquelas em que você fornece explicitamente os comandos para construir um target específico. As regras implícitas são regras padrão incorporadas no **`make`** para compilar e vincular arquivos de determinados tipos.

## 4. Sobre a arquitetura **ARM Cortex-M** responda:

### (a) Explique o conjunto de instruções ***Thumb*** e suas principais vantagens na arquitetura ARM. Como o conjunto de instruções ***Thumb*** opera em conjunto com o conjunto de instruções ARM?
<b>R:<b/> <br/>
O conjunto de instruções Thumb é uma extensão da arquitetura ARM, otimizado para sistemas embarcados, oferecendo instruções mais compactas. Essa compacidade resulta em economia de espaço de memória e menor consumo de energia.

### (b) Explique as diferenças entre as arquiteturas ***ARM Load/Store*** e ***Register/Memory***.
<b>R:<b/> <br/>
Arquitetura ARM Load/Store: Nessa arquitetura, apenas as instruções de carga LDR e armazenamento STR podem acessar a memória. As operações de processamento são realizadas apenas entre registradores, e não diretamente entre registradores e memória.
Arquitetura Register/Memory: Nessa abordagem, instruções de processamento podem operar diretamente entre registradores, sem a necessidade de acessar a memória.
<br/>Diferenças: Enquanto as instruções Load/Store movem dados entre a memória e os registradores, as instruções Register/Memory operam diretamente em dados armazenados nos registradores e na memória, eliminando a necessidade de movimentação explícita de dados entre esses dois locais.

### (c) Os processadores **ARM Cortex-M** oferecem diversos recursos que podem ser explorados por sistemas baseados em **RTOS** (***Real Time Operating Systems***). Por exemplo, a separação da execução do código em níveis de acesso e diferentes modos de operação. Explique detalhadamente como funciona os níveis de acesso de execução de código e os modos de operação nos processadores **ARM Cortex-M**.

### (d) Explique como os processadores ARM tratam as exceções e as interrupções. Quais são os diferentes tipos de exceção e como elas são priorizadas? Descreva a estratégia de **group priority** e **sub-priority** presente nesse processo.

### (e) Qual a diferença entre os registradores **CPSR** (***Current Program Status Register***) e **SPSR** (***Saved Program Status Register***)?

### (f) Qual a finalidade do **LR** (***Link Register***)?

### (g) Qual o propósito do Program Status Register (PSR) nos processadores ARM?

### (h) O que é a tabela de vetores de interrupção?

### (i) Qual a finalidade do NVIC (**Nested Vectored Interrupt Controller**) nos microcontroladores ARM e como ele pode ser utilizado em aplicações de tempo real?

### (j) Em modo de execução normal, o Cortex-M pode fazer uma chamada de função usando a instrução **BL**, que muda o **PC** para o endereço de destino e salva o ponto de execução atual no registador **LR**. Ao final da função, é possível recuperar esse contexto usando uma instrução **BX LR**, por exemplo, que atualiza o **PC** para o ponto anterior. No entanto, quando acontece uma interrupção, o **LR** é preenchido com um valor completamente  diferente,  chamado  de  **EXC_RETURN**.  Explique  o  funcionamento  desse  mecanismo  e especifique como o **Cortex-M** consegue fazer o retorno da interrupção. 

### (k) Qual  a  diferença  no  salvamento  de  contexto,  durante  a  chegada  de  uma  interrupção,  entre  os processadores Cortex-M3 e Cortex M4F (com ponto flutuante)? Descreva em termos de tempo e também de uso da pilha. Explique também o que é ***lazy stack*** e como ele é configurado. 


## Referências

### Básicas

[1] [STM32F411xC Datasheet](https://www.st.com/resource/en/datasheet/stm32f411ce.pdf)

[2] [RM0383 Reference Manual](https://www.st.com/resource/en/reference_manual/rm0383-stm32f411xce-advanced-armbased-32bit-mcus-stmicroelectronics.pdf)

[3] [Using the GNU Compiler Collection (GCC)](https://gcc.gnu.org/onlinedocs/gcc/index.html)

[4] [GNU Make](https://www.gnu.org/software/make/manual/html_node/index.html)

### Vídeos Microsoft Teams

[5] [05 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[6] [06 - Arquitetura Cortex-M Parte 1/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[7] [07 - Arquitetura Cortex-M Parte 2/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[8] [08 - Microcontroladores STM32](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[9] [10 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

### Material Suplementar

[5] [A General Overview of What Happens Before main()](https://embeddedartistry.com/blog/2019/04/08/a-general-overview-of-what-happens-before-main/)
 
[6] [Bare metal embedded lecture-1: Build process](https://youtu.be/qWqlkCLmZoE?si=mn5yDnJYudQ1PpZH)
 
[7] [Bare metal embedded lecture-2: Makefile and analyzing relocatable obj file](https://youtu.be/Bsq6P1B8JqI?si=yuNLPj3JQ-2IT1yo)
 
[8] [Bare metal embedded lecture-3: Writing MCU startup file from scratch](https://youtu.be/2Hm8eEHsgls?si=c27MpZ47ApiMSwHR)
 
[9] [Lecture 15: Booting Process](https://youtu.be/3brOzLJmeek?si=MsHRUEJP8zofjwJQ)
