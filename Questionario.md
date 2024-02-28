# Questionário Sistemas Embarcados I

## 1. Explique brevemente o que é compilação cruzada (***cross-compiling***) e para que ela serve.
R: A compilação cruzada (cross-compiling) é o processo de compilar código-fonte em uma plataforma de desenvolvimento diferente daquela em que o código será executado.
## 2. O que é um código de inicialização ou ***startup*** e qual sua finalidade?
R: É um conjunto de instruções executadas pelo processador assim que ele é ligado ou reiniciado. Sua finalidade principal é preparar o ambiente de execução para a execução do software do usuário.

## 3. Sobre o utilitário **make** e o arquivo **Makefile responda**:

#### (a) Explique com suas palavras o que é e para que serve o **Makefile**.
R: É um arquivo onde é definido as regras e instruções para compilar, vincular e instalar o software, Serve como uma forma te automatizar o processo de compilação de programas.
#### (b) Descreva brevemente o processo realizado pelo utilitário **make** para compilar um programa.
R: O utilitário Make automatiza a compilação de um programa, interpretando um Makefile com diretrizes de compilação. Ele analisa as dependências entre os arquivos, determina quais precisam ser compilados e executa os comandos para compilá-los. Após a compilação, o Make gera o executável final e exibe mensagens de erro em caso de problemas.

#### (c) Qual é a sintaxe utilizada para criar um novo **target**?
R: <br/>
target: prerequisites
<br/>recipe

#### (d) Como são definidas as dependências de um **target**, para que elas são utilizadas?
R: São definidas na mesma linha do target, após seu nome e antes dos comandos, como uma lista de arquivos ou targets que devem ser atualizados antes da construção do target. Por exemplo, no target "hello: main.o hello.o", "hello" depende dos arquivos "main.o" e "hello.o". Essas dependências são cruciais para gerenciar o processo de construção, garantindo que os targets sejam construídos na ordem correta e apenas quando necessário.

#### (e) O que são as regras do **Makefile**, qual a diferença entre regras implícitas e explícitas?
R: As regras implícitas são predefinidas no Make e não exigem declaração explícita, assumindo convenções de nomenclatura padrão, o que as torna úteis para arquivos seguindo essas convenções. Por outro lado, as regras explícitas são definidas pelo usuário no Makefile, permitindo uma personalização detalhada do processo de compilação, o que as torna úteis para arquivos com requisitos específicos de compilação. Enquanto as regras implícitas simplificam o processo para arquivos que seguem padrões comuns, as regras explícitas oferecem flexibilidade para lidar com situações mais complexas e requisitos individuais do projeto.

## 4. Sobre a arquitetura **ARM Cortex-M** responda:

### (a) Explique o conjunto de instruções ***Thumb*** e suas principais vantagens na arquitetura ARM. Como o conjunto de instruções ***Thumb*** opera em conjunto com o conjunto de instruções ARM?
R: O conjunto de instruções Thumb é uma extensão de 16 bits do conjunto de instruções ARM de 32 bits. Ele visa otimizar o desempenho e a eficiência dos processadores ARM. Suas principais vantagens incluem a redução pela metade do tamanho do código, o que é benéfico para dispositivos com memória limitada, e uma maior eficiência energética devido à execução mais rápida das instruções Thumb. Isso resulta em um menor consumo de energia e uma maior duração da bateria em dispositivos móveis. O conjunto de instruções Thumb trabalha em conjunto com o conjunto de instruções ARM, permitindo que as instruções Thumb e ARM sejam misturadas no mesmo programa. Isso otimiza o tamanho do código e o desempenho, de acordo com as necessidades, além de possibilitar a configuração do processador no modo Thumb para reduzir o consumo de energia em dispositivos com requisitos de desempenho menos exigentes.

### (b) Explique as diferenças entre as arquiteturas ***ARM Load/Store*** e ***Register/Memory***.
R: Arquitetura Load/Store:
Nesta arquitetura, todas as operações de acesso à memória são realizadas por meio de instruções específicas de carga (load) e armazenamento (store). Isso significa que, para realizar operações aritméticas ou lógicas com dados da memória, é necessário primeiro carregá-los em registradores da CPU, realizar as operações e, em seguida, armazenar os resultados de volta na memória.
Essa abordagem simplifica o conjunto de instruções da CPU, pois as instruções aritméticas e lógicas operam apenas nos registradores da CPU.

Arquitetura Register/Memory:
Nessa arquitetura, as operações aritméticas e lógicas podem ser realizadas diretamente entre os registradores da CPU e os dados armazenados na memória. Não é necessário carregar e armazenar dados em registradores intermediários antes e depois de operações de cálculo.
Isso pode simplificar o código em alguns casos, mas também pode resultar em um conjunto de instruções mais complexo, pois as instruções devem lidar com operandos tanto em registradores quanto na memória.

### (c) Os processadores **ARM Cortex-M** oferecem diversos recursos que podem ser explorados por sistemas baseados em **RTOS** (***Real Time Operating Systems***). Por exemplo, a separação da execução do código em níveis de acesso e diferentes modos de operação. Explique detalhadamente como funciona os níveis de acesso de execução de código e os modos de operação nos processadores **ARM Cortex-M**.
R: Os processadores ARM Cortex-M possuem níveis de acesso de execução de código e modos de operação. No nível de acesso, há o Thread Mode, para execução de aplicativos, e o Handler Mode, para tratamento de exceções. Já nos modos de operação, destaca-se o Thread Mode para execução de aplicativos normais, e o Privileged Mode, reservado para o kernel do RTOS e com acesso privilegiado aos recursos do sistema. Essa separação permite o controle preciso da execução do código, garantindo segurança e eficiência em sistemas baseados em RTOS.

### (d) Explique como os processadores ARM tratam as exceções e as interrupções. Quais são os diferentes tipos de exceção e como elas são priorizadas? Descreva a estratégia de **group priority** e **sub-priority** presente nesse processo.
R: Tratamento de exceções e interrupções nos processadores ARM:
Os processadores ARM gerenciam exceções e interrupções de forma organizada para assegurar a estabilidade e confiabilidade dos sistemas. Exceções podem ser de hardware, desencadeadas por eventos como interrupções de periféricos, ou de software, resultantes da execução de instruções específicas. Essas exceções são priorizadas conforme sua urgência e importância para garantir um tratamento adequado.

Estratégia de group e sub priority no processador ARM Cortex-M:
O processador ARM Cortex-M utiliza uma estratégia de priorização de exceções baseada em dois níveis: group priority e sub-priority. Na prioridade de grupo, as exceções são agrupadas em diferentes níveis de prioridade, enquanto a subprioridade é usada para desempatar entre exceções com a mesma prioridade de grupo. Essa abordagem assegura que as exceções mais críticas sejam tratadas primeiro, mantendo a responsividade do sistema em tempo real.

### (e) Qual a diferença entre os registradores **CPSR** (***Current Program Status Register***) e **SPSR** (***Saved Program Status Register***)?
R:SPSR é usado temporariamente para armazenar o estado do programa durante a troca de contexto, garantindo que o programa possa retomar sua execução normal após o tratamento de exceções ou interrupções. <br/>
CPSR mantém o estado atual do programa durante sua execução normal.

### (f) Qual a finalidade do **LR** (***Link Register***)?
R: O Link Register armazena o endereço de retorno de uma sub-rotina ou função, permitindo que o programa retorne à instrução após a chamada da sub-rotina e continue sua execução normal.

### (g) Qual o propósito do Program Status Register (PSR) nos processadores ARM?
R: O Program Status Register nos processadores ARM tem como propósito principal manter informações sobre o estado atual do processador durante a execução do programa. Isso envolve registros sobre o modo de operação atual (como modo de usuário, modo privilegiado e modo de interrupção), status de condição (flags) provenientes de operações aritméticas e lógicas, além do controle de interrupções e exceções. O PSR é essencial para o controle e o funcionamento adequado do processador, garantindo a correta execução do código e a gestão de eventos críticos durante a execução do programa.

### (h) O que é a tabela de vetores de interrupção?
R: É uma estrutura de dados utilizada em sistemas microcontroladores e processadores para direcionar o controle da execução do programa para rotinas específicas de tratamento de interrupções ou exceções.

### (i) Qual a finalidade do NVIC (**Nested Vectored Interrupt Controller**) nos microcontroladores ARM e como ele pode ser utilizado em aplicações de tempo real?
R: O Nested Vectored Interrupt Controller (NVIC) nos microcontroladores ARM tem como finalidade gerenciar interrupções de forma eficiente, priorizando, encaminhando e controlando o tratamento de interrupções em sistemas embarcados. Ele desempenha um papel essencial na organização e no direcionamento adequado das interrupções, garantindo uma resposta rápida e ordenada a eventos externos ou situações excepcionais.

Em aplicações de tempo real, o NVIC é utilizado para garantir uma resposta precisa e previsível a eventos críticos. Ele permite a priorização de interrupções, o aninhamento de interrupções para tratamento imediato de eventos prioritários, o controle fino sobre as prioridades das interrupções e a temporização precisa de eventos, assegurando o funcionamento correto do sistema dentro de prazos específicos. Essas características tornam o NVIC uma ferramenta essencial para sistemas em tempo real, onde a resposta rápida a eventos é fundamental para o desempenho adequado da aplicação.

### (j) Em modo de execução normal, o Cortex-M pode fazer uma chamada de função usando a instrução **BL**, que muda o **PC** para o endereço de destino e salva o ponto de execução atual no registador **LR**. Ao final da função, é possível recuperar esse contexto usando uma instrução **BX LR**, por exemplo, que atualiza o **PC** para o ponto anterior. No entanto, quando acontece uma interrupção, o **LR** é preenchido com um valor completamente  diferente,  chamado  de  **EXC_RETURN**.  Explique  o  funcionamento  desse  mecanismo  e especifique como o **Cortex-M** consegue fazer o retorno da interrupção. 
R: Quando uma interrupção ocorre no Cortex-M, o valor atual do registrador LR é salvo em um registro especial chamado LR de modo de exceção, enquanto o LR é preenchido com um valor chamado EXC_RETURN. Esse valor contém informações sobre o estado anterior do processador. Para retornar da interrupção, o processador executa uma instrução BX LR, que carrega o valor EXC_RETURN de volta ao PC. O processador então usa essas informações para restaurar o contexto anterior à interrupção, garantindo uma transição suave e eficiente de volta à execução do código principa

### (k) Qual  a  diferença  no  salvamento  de  contexto,  durante  a  chegada  de  uma  interrupção,  entre  os processadores Cortex-M3 e Cortex M4F (com ponto flutuante)? Descreva em termos de tempo e também de uso da pilha. Explique também o que é ***lazy stack*** e como ele é configurado. 
R: No Cortex-M3, durante a chegada de uma interrupção, o contexto do processador é automaticamente salvo na pilha do modo de exceção, incluindo registros principais, como o LR, mas excluindo os registradores de ponto flutuante. Já no Cortex-M4F, que possui suporte a ponto flutuante, além dos registros principais, os registradores de ponto flutuante também são salvos, o que pode aumentar o tempo necessário para o salvamento do contexto devido à complexidade adicional.

O "lazy stack" é uma técnica utilizada para otimizar o salvamento de contexto em processadores Cortex-M. Com essa abordagem, o processador salva apenas os registros necessários para o contexto atual, em vez de salvar todos os registros do modo de exceção. Isso é configurável por meio de flags no processador e permite escolher entre o salvamento completo do contexto ou o "lazy stack" dependendo das necessidades da aplicação, reduzindo assim o tempo necessário para salvar e restaurar o contexto e melhorando a eficiência do tratamento de interrupções.


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
