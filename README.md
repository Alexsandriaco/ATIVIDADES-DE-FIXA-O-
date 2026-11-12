#include <stdio.h>
#define MAX 10
typedef struct {
    int dados[MAX];
    int tamanho;
} 
void inicializar(Lista *lista) {
    lista->tamanho = 0;
}
int inserirFim(Lista *lista, int valor) {
    if (lista->tamanho >= MAX) return 0;
    lista->dados[lista->tamanho++] = valor;
    return 1;
}
void imprimir(Lista *lista) {
    printf("[ ");
    for (int i = 0; i < lista->tamanho; i++) {
        printf("%d ", lista->dados[i]);
    }
    printf("] (tamanho: %d)\n", lista->tamanho);
}
int removerPosicao(Lista *lista, int posicao) {
        if (lista == NULL || posicao < 0 || posicao >= lista->tamanho) {
        return 0;
    }
    for (int i = posicao; i < lista->tamanho - 1; i++) {
        lista->dados[i] = lista->dados[i + 1];
    }
    return 1;
}
int main() {
    Lista lista;
    inicializar(&lista);
    for (int i = 1; i <= 5; i++) {
        inserirFim(&lista, i * 10);
    }
    printf("Inicial:");
    imprimir(&lista);
    removerPosicao(&lista, 0);
    printf("Sem o primeiro:");
    imprimir(&lista);
    removerPosicao(&lista,1);
    printf("Sem intermediario:");
    imprimir(&lista);
    removerPosicao(&lista,lista.tamanho-1);
    printf("Sem o ultimo:");
    imprimir(&lista);
    return 0;
}
