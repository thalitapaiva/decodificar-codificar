#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main(void) {
    int C[60], *C2, i, j, l, tamanho_M;
    char M[60];
    char K[12] = "CHAVE2025/1";
    int menu;
    int tamanho_K = strlen(K);

    printf("\n| Bem-vindo ao Sistema de Codificação e Decodificação (SCDC)\n");

    do {
        printf("\n| Escolha uma opção:\n");
        printf("| 1 - Codificar\n");
        printf("| 2 - Decodificar\n");
        printf("| 3 - Sair\n");
        printf("Resposta: ");

        if (scanf("%d", &menu) != 1) {
            printf("\n| Entrada inválida. Tente novamente.\n");
            while (getchar() != '\n');
            continue;
        }

        switch(menu) {
            case 1:
                printf("\n| Codificação selecionada.\n");
                printf("| Digite uma mensagem (sem espaços, até 59 caracteres):\n");
                printf("| Obs: sem acentos, sem 'ç'.\n");
                printf("Resposta: ");
                scanf(" %59s", M);

                tamanho_M = strlen(M);
                printf("\n| Tamanho da mensagem: %d\n", tamanho_M);
                printf("| Mensagem codificada:\n| ----> ");

                l = 0;
                for (i = 0; i < tamanho_M; i++) {
                    C[i] = M[i] ^ K[l];
                    l = (l + 1) % tamanho_K;
                    printf("%d ", C[i]);
                }
                printf("<----\n");
                break;

            case 2:
                printf("\n| Decodificação selecionada.\n");
                printf("| Quantos caracteres possui sua mensagem codificada? (máx 60)\n");
                printf("Resposta: ");
                if (scanf("%d", &tamanho_M) != 1 || tamanho_M <= 0 || tamanho_M > 60) {
                    printf("| Quantidade inválida.\n");
                    while (getchar() != '\n');
                    continue;
                }

                C2 = (int*) malloc(tamanho_M * sizeof(int));
                if (C2 == NULL) {
                    printf("| Erro ao alocar memória.\n");
                    return 1;
                }

                printf("\n| Digite os %d números inteiros da mensagem codificada:\n", tamanho_M);
                for (j = 0; j < tamanho_M; j++) {
                    if (scanf("%d", &C2[j]) != 1) {
                        printf("| Entrada inválida. Cancelando decodificação.\n");
                        free(C2);
                        while (getchar() != '\n');
                        continue;
                    }
                }

                printf("\n| Mensagem decodificada:\n| ----> ");
                l = 0;
                for (i = 0; i < tamanho_M; i++) {
                    M[i] = C2[i] ^ K[l];
                    l = (l + 1) % tamanho_K;
                    printf("%c", M[i]);
                }
                M[tamanho_M] = '\0';
                printf(" <----\n");

                free(C2);
                break;

            case 3:
                printf("\n| Programa encerrado.\n| Até logo!\n");
                break;

            default:
                printf("| Opção inválida. Digite um número de 1 a 3.\n");
        }

    } while (menu != 3);

    return 0;
}

