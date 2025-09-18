#include <stdio.h>
#include <stdlib.h>

// Tamanho fixo da matriz de habilidade
#define TAM_HABILIDADE 5
#define CENTRO (TAM_HABILIDADE / 2)

// Gera uma matriz em formato de cone (3 linhas superiores)
void gerar_cone(int matriz[TAM_HABILIDADE][TAM_HABILIDADE]) {
    int i, j;

    // Zera toda a matriz
    for (i = 0; i < TAM_HABILIDADE; i++) {
        for (j = 0; j < TAM_HABILIDADE; j++) {
            matriz[i][j] = 0;
        }
    }

    // Preenche 3 linhas superiores com formato de cone
    for (i = 0; i < 3; i++) {
        for (j = 0; j < TAM_HABILIDADE; j++) {
            if (abs(j - CENTRO) <= i) {
                matriz[i][j] = 3;
            }
        }
    }
}

// Gera uma matriz em formato de cruz
void gerar_cruz(int matriz[TAM_HABILIDADE][TAM_HABILIDADE]) {
    int i, j;

    for (i = 0; i < TAM_HABILIDADE; i++) {
        for (j = 0; j < TAM_HABILIDADE; j++) {
            if (i == CENTRO || j == CENTRO) {
                matriz[i][j] = 3;
            } else {
                matriz[i][j] = 0;
            }
        }
    }
}

// Gera uma matriz com formato de octaedro (losango)
void gerar_octaedro(int matriz[TAM_HABILIDADE][TAM_HABILIDADE]) {
    int i, j;

    for (i = 0; i < TAM_HABILIDADE; i++) {
        for (j = 0; j < TAM_HABILIDADE; j++) {
            if (abs(i - CENTRO) + abs(j - CENTRO) <= CENTRO) {
                matriz[i][j] = 3;
            } else {
                matriz[i][j] = 0;
            }
        }
    }
}

// Imprime a matriz no console
void imprimir_matriz(int matriz[TAM_HABILIDADE][TAM_HABILIDADE]) {
    int i, j;

    for (i = 0; i < TAM_HABILIDADE; i++) {
        for (j = 0; j < TAM_HABILIDADE; j++) {
            printf("%d ", matriz[i][j]);
        }
        printf("\n");
    }
    printf("\n");
}

int main() {
    // Matrizes para armazenar as habilidades
    int cone[TAM_HABILIDADE][TAM_HABILIDADE];
    int cruz[TAM_HABILIDADE][TAM_HABILIDADE];
    int octaedro[TAM_HABILIDADE][TAM_HABILIDADE];

    // Geração das formas
    gerar_cone(cone);
    gerar_cruz(cruz);
    gerar_octaedro(octaedro);

    // Impressão
    printf("Cone:\n");
    imprimir_matriz(cone);

    printf("Cruz:\n");
    imprimir_matriz(cruz);

    printf("Octaedro:\n");
    imprimir_matriz(octaedro);

    return 0;
}
