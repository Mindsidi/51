# 51
#include <stdio.h>

int main(){

int z[20][20]={ {81,49,31,73,55,79,14,29,93,71,40,67,53,88,30,3,49,13,36,65}, {52,70,95,23,4,60,11,42,69,24,68,56,1,32,56,71,37,2,36,91}, {22,31,16,71,51,67,63,89,41,92,36,54,22,40,40,28,66,33,13,80}, {24,47,32,60,99,3,45,2,44,75,33,53,78,36,84,20,35,17,12,50}, {32,98,81,28,64,23,67,10,26,38,40,67,59,54,70,66,18,38,64,70}, {67,26,20,68,2,62,12,20,95,63,94,39,63,8,40,91,66,49,94,21}, {24,55,58,5,66,73,99,26,97,17,78,78,96,83,14,88,34,89,63,72}, {21,36,23,9,75,0,76,44,20,45,35,14,0,61,33,97,34,31,33,95}, {78,17,53,28,22,75,31,67,15,94,3,80,4,62,16,14,9,53,56,92}, {16,39,5,42,96,35,31,47,55,58,88,24,0,17,54,24,36,29,85,57}, {86,56,0,48,35,71,89,7,5,44,44,37,44,60,21,58,51,54,17,58}, {19,80,81,68,5,94,47,69,28,73,92,13,86,52,17,77,4,89,55,40}, {04,52,8,83,97,35,99,16,7,97,57,32,16,26,26,79,33,27,98,66}, {88,36,68,87,57,62,20,72,3,46,33,67,46,55,12,32,63,93,53,69}, {04,42,16,73,38,25,39,11,24,94,72,18,8,46,29,32,40,62,76,36}, {20,69,36,41,72,30,23,88,34,62,99,69,82,67,59,85,74,4,36,16}, {20,73,35,29,78,31,90,1,74,31,49,71,48,86,81,16,23,57,5,54}, {1,70,54,71,83,51,54,69,16,92,33,48,61,43,52,1,89,19,67,48}};

int produto=0, produtoMax=0; int i, j; // linha e coluna for (i=0; i<17; i++) { for (j=0; j<20; j++) { produto = z[i][j]* z[i][j+1]* z[i][j+2]* z[i][j+3]; if(produto > produtoMax){ // foi achada uma sequencia // com produto maior que // o ja achado produtoMax = produto; } } } printf("maximox: %d\n", produtoMax);

for (i=0; i<17; i++) { for (j=0; j<20; j++) { produto = z[i][j]* z[i+1][j]* z[i+2][j]* z[i+3][j]; if(produto > produtoMax){ // foi achada uma sequencia // com produto maior que // o ja achado produtoMax = produto; } } } printf("maximoy: %d\n", produtoMax); for (i=0; i<17; i++) { for (j=0; j<17; j++) { produto = z[i][j]* z[i+1][j+1]* z[i+2][j+2]* z[i+3][j+3]; if(produto > produtoMax){ // foi achada uma sequencia // com produto maior que // o ja achado produtoMax = produto; } } } printf("maximok: %d\n", produtoMax); for (i=3; i<20; i++) { for (j=0; j<17; j++) { produto = z[i][j]* z[i-1][j+1]* z[i-2][j+2]* z[i-3][j+3]; if(produto > produtoMax){ // foi achada uma sequencia // com produto maior que // o ja achado produtoMax = produto; } } } printf("maximo-k: %d\n", produtoMax); return 0; }

int main(){ // char: [-128,127] char aposta[6], napostas; int i, j, k, repetiu, tmp;

printf("Digite quantas apostas gerar: "); scanf("%d", &napostas);

srand(time(0)); // cria uma semente para o rng

// INICIO DA REPETICAO DA GERACAO DE APOSTAS for (k=0; k<napostas; k++) { // gera um no. aleatorio na faixa [1,60] aposta[0]=1+rand()%60; for (i=1; i<6; i++) { // gera o numero e so desiste... do{ aposta[i]=1+rand()%60; // verifica se para uma das apostas // anteriores houve alguma coincidencia repetiu = 0; for (j=0; j<i; j++) { if(aposta[i] == aposta[j]){ repetiu = 1; } } // ... quando o numero nao se repete }while (repetiu == 1); } // ordena a aposta for (i=0; i<5; i++) { for (j=i+1; j<6; j++) { if(aposta[i] > aposta[j]){ tmp = aposta[i]; aposta[i] = aposta[j]; aposta[j] = tmp; } } }

for (i=0; i<6; i++) {
  printf("%d, ", aposta[i]);
}
printf("\n");
} // FIM DA REPETICAO DA GERACAO DE APOSTAS return 0; }

Questão da prova

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main()
{
    char str[1000];
    int c, i=0;

    printf("Digite um numero.\n");
    gets(str);
    int  tamanho= strlen(str);
    int certo=0, sinal=0;
    printf("Vc digitou %d caracteres e eles ", tamanho);
    while(i<=tamanho){

        if ((str[i]>=48)&&(str[i]<=57))
            certo++;
        if(str[i]==46)
            certo++;
        if(((str[0]<48)&&(str[0]<57))&&((str[0]!=43)&&(str[0]!=45))){
            printf("nao formam um numero\n");
           return 0;}
        if(((str[i]==46)||(str[i]==44))&&((str[i+1]==46)||(str[i+1]==44))){
            printf("nao formam um numero\n");
            return 0;
      }
        i++;
    }
    if((str[0]==45)||(str[0]==43)){
        certo++;
    }
    if(tamanho==certo){
        printf("formam um numero\n");}
    else {
        printf("nao formam um numero\n");
    }
}

