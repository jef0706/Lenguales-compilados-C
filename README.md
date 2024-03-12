#include <stdio.h>

void convertirMonedas(float cantidad, char origen, char destino);
float tasaDeCambio(char origen, char destino);

int main() {
    float cantidad;
    char origen, destino;

    printf("Bienvenido al conversor de monedas\n");
    printf("Ingresa la cantidad a convertir: ");
    scanf("%f", &cantidad);

    printf("Ingresa la moneda de origen (Q para Quetzales, D para Dólares, E para Euros): ");
    scanf(" %c", &origen); // El espacio antes de %c ayuda a ignorar cualquier newline pendiente en el buffer

    printf("Ingresa la moneda de destino (Q para Quetzales, D para Dólares, E para Euros): ");
    scanf(" %c", &destino);

    convertirMonedas(cantidad, origen, destino);

    return 0;
}

void convertirMonedas(float cantidad, char origen, char destino) {
    float tasa = tasaDeCambio(origen, destino);
    if (tasa == 0.0f) {
        printf("Una de las monedas seleccionadas no es válida.\n");
    } else {
        float convertido = cantidad * tasa;
        printf("%.2f convertidos son: %.2f\n", cantidad, convertido);
    }
}

float tasaDeCambio(char origen, char destino) {
    // Tasas de cambio hipotéticas
    // Q -> D: 0.13, Q -> E: 0.11
    // D -> Q: 7.7, D -> E: 0.85
    // E -> Q: 9, E -> D: 1.18

    if (origen == 'Q' && destino == 'D') return 0.13;
    else if (origen == 'Q' && destino == 'E') return 0.11;
    else if (origen == 'D' && destino == 'Q') return 7.7;
    else if (origen == 'D' && destino == 'E') return 0.85;
    else if (origen == 'E' && destino == 'Q') return 9;
    else if (origen == 'E' && destino == 'D') return 1.18;
    else return 0.0; // Monedas no válidas o intento de convertir la misma moneda
}
