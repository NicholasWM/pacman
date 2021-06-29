# PACMAN
![Alt ou título da imagem](./project.png)

## Assuntos:

  Alocação dinamica de memória
  Array de Ponteiros de Arrays
  Structs
  Typedef
  Ponteiros para Structs

## Comands

    gcc fogefoge.c mapa.c ui.c -o fogefoge.out -std=c99

## Alocação dinamica de memória com malloc() e free()

Artigo
<http://linguagemc.com.br/alocacao-dinamica-de-memoria-em-c/>

**Alocação Estática**

Na alocação estática de memória, os tipos de dados tem tamanho predefinido. Neste caso, o compilador vai alocar de forma automática o espaço de memória necessário. Sendo assim, dizemos que a alocação estática é feita em tempo de compilação. Este tipo de alocação tende a desperdiçar recursos, já que nem sempre é possível determinar previamente qual é o espaço necessário para armazenar as informações. Quando não se conhece o espaço total necessário, a tendência é o programador exagerar pois é melhor superdimensionar do que faltar espaço.

**Alocação Dinâmica**

Na alocação dinâmica podemos alocar espaços durante a execução de um programa, ou seja, a alocação dinâmica é feita em tempo de execução. Isto é bem interessante do ponto de vista do programador, pois permite que o espaço em memória seja alocado apenas quando necessário. Além disso, a alocação dinâmica permite aumentar ou até diminuir a quantidade de memória alocada.


**sizeof**

A função sizeof determina o número de bytes para um determinado tipo de dados.

É interessante notar que o número de bytes reservados pode variar de acordo com o compilador utilizado.
Exemplo:

x = sizeof(int); //retorna 4 no gcc

**malloc**

A função malloc aloca um espaço de memória e retorna um ponteiro do tipo void para o início do espaço de memória alocado.

**free**

A função free libera o espaço de memória alocado.

### **Exemplos**:
Quando um programador define tipo e o número de elementos um vetor ele está utilizando alocação estática.

Uma alternativa interessante é declarar um vetor como ponteiro, a fim de utilizar alocação dinâmica. Para tanto devemos usar a função malloc. Porém, esta função necessita saber a quantidade de bytes que devem ser reservados. Para fazer esse cálculo usamos o comando sizeof.

### **Alocando para Array de Arrays(Ponteiro para Array de Ponteiros)**
````cpp
  int** matriz;

  int linhas = 5;
  int colunas = 10;

  // alocando espaço para as linhas,
  // que guardam ponteiro de inteiro.
  matriz = malloc(sizeof(int*) * linhas);

  // agora, para cada linha, alocamos
  // espaço para um array com 10 ("colunas") posições.
  for(int i = 0; i < linhas; i++) {
      matriz[i] = malloc(sizeof(int) * colunas);
  }

  // agora podemos usar 'matriz' como uma matriz
  matriz[2][3] = 10;
````