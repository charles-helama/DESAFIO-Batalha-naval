# DESAFIO-Batalha-naval
Criando o código com níveis de dificuldades!
#include <stdio.h>

#define TAM_TABULEIRO 10
#define TAM_NAVIO 3

int main() {
    int tabuleiro[TAM_TABULEIRO][TAM_TABULEIRO] = {0};

    // Coordenadas dos navios
    int linha_navio_horizontal = 2;
    int coluna_navio_horizontal = 4;

    int linha_navio_vertical = 5;
    int coluna_navio_vertical = 7;

    int pode_posicionar = 1;
    int i, j, c; // ?? Declarações fora dos loops

    // Posicionar navio horizontal
    if (coluna_navio_horizontal + TAM_NAVIO <= TAM_TABULEIRO) {
        pode_posicionar = 1;
        for (i = 0; i < TAM_NAVIO; i++) {
            if (tabuleiro[linha_navio_horizontal][coluna_navio_horizontal + i] != 0) {
                pode_posicionar = 0;
                break;
            }
        }
        if (pode_posicionar) {
            for (i = 0; i < TAM_NAVIO; i++) {
                tabuleiro[linha_navio_horizontal][coluna_navio_horizontal + i] = 3;
            }
        } else {
            printf("Erro: sobreposição ao posicionar navio horizontal.\n");
        }
    } else {
        printf("Erro: navio horizontal fora dos limites do tabuleiro.\n");
    }

    // Posicionar navio vertical
    if (linha_navio_vertical + TAM_NAVIO <= TAM_TABULEIRO) {
        pode_posicionar = 1;
        for (i = 0; i < TAM_NAVIO; i++) {
            if (tabuleiro[linha_navio_vertical + i][coluna_navio_vertical] != 0) {
                pode_posicionar = 0;
                break;
            }
        }
        if (pode_posicionar) {
            for (i = 0; i < TAM_NAVIO; i++) {
                tabuleiro[linha_navio_vertical + i][coluna_navio_vertical] = 3;
            }
        } else {
            printf("Erro: sobreposição ao posicionar navio vertical.\n");
        }
    } else {
        printf("Erro: navio vertical fora dos limites do tabuleiro.\n");
    }

    // Exibir o tabuleiro
    printf("\nTABULEIRO BATALHA NAVAL (0 = água, 3 = navio)\n\n");

    // Cabeçalho A-J
    printf("   ");
    for (c = 0; c < TAM_TABULEIRO; c++) {
        printf(" %c", 'A' + c);
    }
    printf("\n");

    // Conteúdo das linhas
    for (i = 0; i < TAM_TABULEIRO; i++) {
        printf("%2d ", i + 1);
        for (j = 0; j < TAM_TABULEIRO; j++) {
            printf(" %d", tabuleiro[i][j]);
        }
        printf("\n");
    }

    return 0;
}
