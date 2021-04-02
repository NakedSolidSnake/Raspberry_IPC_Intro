# Comunicação entre processos

Nessa série iremos tratar de comunicação entre processos, recurso muito utilizado nos sistemas operacionais, veremos os tipos existentes e exemplos usando o famoso botão e LED, nos primeiros artigos iremos abordar a configuração do ambiente, instalação de programas e com uma introdução para explicar o que é IPC(Inter process communication).

## Introdução
Nos sistemas operacionais tais como Windows e Linux muitos dos seus recursos operam
sobre a forma de processos, e processos são instâncias de programas em execução, ou seja, um programa gera um processo, e também 
existem processos que rodam em segundo plano disponibilizando algum tipo
de serviço, a seguir alguns exemplos:


* alsa   - usado para inicializar o Alsa (_Advanced Linux Sound Architecture_).
* crond  - usado para executar programas de usuários em tempo periódicos pré-determinados.
* dhcpd  - usado para inicializar o servidor de Host Dinâmico dchp.
* httpd  - usado para inicializar o servidor Web Apache.
* mysql  - usado para inicializar o servidor de Banco de Dados MySQL.
* sshd   - é um daemon que serve conexões ssh.
* syslog - usado para fornecer um arquivo unificado de log do sistema.

Quando o sistema operacional lança um processo, esse processo tem uma memória reservada para poder realizar a sua execução, ou seja, sua memória fica protegida somente para o seu uso, e para se comunicar com outros processos é necessário algum mecanismo que permita essa comunicação ou alguma outra forma que os dados sejam compartilhados entre os processos, é nesse momento que entra em cena o _IPC_.

## O que é _IPC_?
O _IPC_ é um mecanismo que permite que dois ou mais processos realizem a troca de dados entre si. Isso é extremamente útil devido ao fato que um processo possui sua própria região de memória onde outros processos não tem a permissão de acessar aquele espaço de memória.

## Tipos de _IPC_
Existem dois tipos de _IPC_ o _pull-based_ e o _push-based_:

* _pull-based_ -  requer um meio, como um armazenamento para compartilhar os dados, isso porque os processos que querem ler esses dados precisam dar um _pull_ desses dados. Neste caso os dados serão lidos através de um elemento intermediário, como um repositório de dados, onde um processo pode escrever dados nesse repositório enquanto outro processo realiza a leitura desses dados. Para esse grupo de _IPC_ é fortemente recomendado realizar a sincronia para que não haja concorrência, os _IPC_ referente a esse grupo são:
    
