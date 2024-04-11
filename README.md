# calculadora

#include <stdio.h>

int main() {
    int x, y, op, resultado = 1, contX = 0, contY = 0;
    int tempX, tempY;

    printf("Digite dois numeros inteiros: ");
    scanf("%d %d", &x, &y);
    printf("Escolha entre:\n 1- soma entre os numeros\n 2- subtracao entre os numeros\n 3- divisao entre os numeros\n 4- multiplicacao entre os numeros\n 5- exponenciacao entre os numeros\n 6- remover o y-esimo digito do x\n 7- construção do número cujos dígitos são a soma daqueles em x e y\n 8- digitos alternando entre si\n 9- digitos alternando entre si e com ordem reversa\n");
    scanf("%d", &op);

    switch (op) {
        case 1: 
            printf("Soma entre os numeros: %d", x + y); 
            break;
        case 2: 
            printf("Subtracao entre os numeros: %d", x - y);
            break;
        case 3:
            printf("A divisao entre os numeros e: %d", x / y);
            break;
        case 4:
            printf("A multiplicacao entre os numeros e: %d", x * y);
            break;
        case 5:
            resultado = 1;
            for (int i = 0; i < y; i++)
                resultado *= x;
            printf("A exponenciacao entre os numeros e: %d", resultado);
            break;
        case 6: // deu meio errado
          if (x < 0) x *= -1; // se o x for negativo, vira positivo
          if (y < 0) y *= -1; // se o y for negativo, vira positivo
            if (y <= 0) 
                resultado = x;
            else {
                int divisor = 1;
                for (int i = 1; i < y; i++) {
                    divisor *= 10;
                }
                int parte1 = x / (divisor * 10);
                int parte2 = x % divisor;
                resultado = parte1 * divisor + parte2;
            }
            printf("O resultado e: %d", resultado);
            break;
        case 7:
          if (x < 0) x *= -1; // se o x for negativo, vira positivo
          if (y < 0) y *= -1; // se o y for negativo, vira positivo
            tempX = x; 
            tempY = y;
            while (tempX > 0) {
                tempX /= 10;
                contX++;
            }
            while (tempY > 0) {
                tempY /= 10;
                contY++;
            }
            if (contX != contY) {
                printf("erro: os numeros nao possuem o mesmo numero de digitos.\n");
            } else {
                resultado = 0;
                int multiplicador = 1;
                while (x > 0 || y > 0) {
                    resultado += ((x % 10) + (y % 10)) * multiplicador;
                    x /= 10;
                    y /= 10;
                    multiplicador *= 10;
                }
                printf("novo numero: %d", resultado);
            }
            break;
          case 8: // deu meio errado
            if (x < 0) x *= -1; // se o x for negativo, vira positivo
            if (y < 0) y *= -1; // se o y for negativo, vira positivo
              tempX = x; 
              tempY = y;
              while (tempX > 0) {
                  tempX /= 10;
                   contX++;
              }
              while (tempY > 0) {
                  tempY /= 10;
                  contY++;
              }
              if (contX != contY) {
                printf("erro: os numeros nao possuem o mesmo numero de digitos.\n");
             } else {
                 resultado = 0;
              int multiplicador = 1;
                 while (x > 0 || y > 0) {
                   resultado += (x % 10) * multiplicador;
                    x /= 10;
                    multiplicador *= 10;
                    resultado += (y % 10) * multiplicador;
                     y /= 10;
                    multiplicador *= 10;
                        }
                     printf("novo numero: %d", resultado);
                    }
                    break;
            case 9: // deu meio errado
            if (x < 0) x *= -1; // se o x for negativo, vira positivo
            if (y < 0) y *= -1; // se o y for negativo, vira positivo
             tempX = x; // Inicializando tempX e tempY
             tempY = y;
               while (tempX > 0) {
             tempX /= 10;
             contX++;
             }
             while (tempY > 0) {
             tempY /= 10;
             contY++;
             }
            if (contX != contY) {
            printf("erro: os numeros nao possuem o mesmo numero de digitos.\n");
            } else {
           resultado = 0;
          int multiplicador = 1;
          while (y > 0) {
          resultado *= 10;
          resultado += y % 10;
          y /= 10;
         }
          while (x > 0) {
            resultado *= 10;
            resultado += x % 10;
            x /= 10;
           }
        printf("novo numero: %d", resultado);
         }
         break;
         default:
         printf("invalido\n");
        break;
       }

 return 0;
 }
