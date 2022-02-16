1) Escribir un programa que acepte tres argumentos enteros e imprima "iguales" si los tres números son iguales o "no iguales" de lo contrario.
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char const *argv[])
{
    int x = atoi(argv[1]);
    int y = atoi(argv[2]);
    int z = atoi(argv[3]);
    if (x == y && y == z)
    {
        printf("Equals");
        return 0;
    }
    printf("Not equals");
    return 0;
}

Escribir una versión mejorada del programa para calcular las raíces de una función cuadrática, del apunte anterior. El programa debe imprimir un mensaje de error en los casos que el discriminante sea menor a cero (raíz negativa) o el argumento a sea igual a cero (división por cero).

#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int main(int argc, char const *argv[])
{
    double a = atof(argv[1]);
    double b = atof(argv[2]);
    double c = atof(argv[3]);
    if (a == 0)
    {
        printf("Cant divide by zero");
        return 0;
    }
    
    double discriminante = (b*b)+(-4*a*c);
    if (discriminante < 0)
    {
        printf("The equation has no real solution");
        return 0;
    }
    
    printf("Root 1 = %f\n", ((b*-1) / (2*a)) + (sqrt(discriminante) / (2*a)));
    printf("Root 2 = %f\n", ((b*-1) / (2*a)) - (sqrt(discriminante) / (2*a)));
    return 0;
}

Escribir un programa que simule tirar un dado "cargado". Imprimiendo el resultado de tirar el dado, teniendo en cuenta que la probabilidad de tirar un 1, 2, 3, 4 o 5 es de 1/8 y de tirar un 6 es de 3/8.

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main(void)
{   
    srand(time(NULL));
    int rng= (rand()%80)+ 1;
    if (rng <= 10)
    {
        printf("1");
    }
    if (rng <= 20 && rng > 10)
    {
        printf("2");
    }
    if (rng <= 30 && rng > 20)
    {
        printf("3");
    }
    if (rng <= 40 && rng > 30)
    {
        printf("4");
    }
    if (rng <= 50 && rng > 40)
    {
        printf("5");
    }
    if (rng > 50 && rng <= 80)
    {
        printf("6");
    }
    re

Escribir un programa que imprima los números entre el 1000 y el 1999, mostrando 5 números por línea.

#include <stdio.h>

int main(void)
{
    int line1 = 996;
    int line2 = 997;
    int line3 = 998;
    int line4 = 999;
    int line5 = 1000;
    while (line5 < 1995)
    {
        line1 = line1 + 5;
        line2 = line2 + 5;
        line3 = line3 + 5;
        line4 = line4 + 5;
        line5 = line5 + 5;
        printf("%d\t%d\t%d\t%d\t%d\n", line1, line2, line3, line4, line5);
    }
    printf("1996\t1997\t1998\n");
    return 0;
}

Escribir un programa que acepte un argumento entero n e imprima n números aleatorios entre 0 y 100. Al finalizar el programa debe imprimir el valor promedio de los números que aparecieron.

#include <stdlib.h>
#include <stdio.h>
#include <time.h>

int main(int argc, char const *argv[])
{
    int reqnums = atoi(argv[1]);
    int i = 0;
    double sum = 0;
    int rng = 0;
    srand(time(NULL));
    while (i < reqnums)
    {
        rng = rand()%101;
        printf("%d\n", rng);
        sum = sum + rng;
        i++;
    }
    double avg = sum/reqnums;
    printf("Average= %f", avg);
    return 0;
}

Escribir un programa que imprima una tabla con los valores de las funciones: ln n, n, n ln n, n2, n3, 2n para los valores de n: 1, 2, 4, 8, 16, 32, 64. Usar caracteres \t para alinear las columnas y las funciones pow() y log() de math.h.

#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int main(void)
{
    double n = 1;
    while (n <= 64)
    {
        printf("%lf\t%.0lf\t%lf\t%.0lf\t%.0lf\t%.0lf\n", log(n), n, n*log(n), n*n, n*n*n, pow(2.0, n));
        n = n*2;
    }
    return 0;
}

Escribir un programa que acepte un argumento entero n y use dos loops anidados para imprimir un patrón como el de un tablero de ajedrez usando asteriscos y espacios con n filas y columnas.

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char const *argv[])
{
    int n = atoi(argv[1]);
    int count = 1;
    int rows = 0;
    for (int column = 0; column < n; column++)
    {
        while (rows < n)
        {
            printf("*");
            rows++;
            if (rows < n)
            {
                printf(" ");
                rows++;
            }
            
        }
        printf("\n");
        rows = 0;
        count++;
        if (count % 2 == 0)
        {
            printf(" ");
            rows++;
        }
    }
    
    return 0;

Escribir un programa que acepte un número arbitrario de argumentos enteros por línea de comandos e imprima el máximo de los números ingresados.

#include <stdlib.h>
#include <stdio.h>
#include <limits.h>

int main(int argc, char const *argv[])
{
    int max = INT_MIN;
    int current = 0;
    for (int i = 1; i < argc; i++)
    {
        current = atoi(argv[i]);
        if (max < current)
        {
            max = current;
        }
    }
    printf("%d\n", max);
    return 0;
}

Escribir un programa como el anterior pero que nos dé el máximo, el mínimo y el promedio de los números ingresados.

#include <stdlib.h>
#include <stdio.h>
#include <limits.h>

int main(int argc, char const *argv[])
{
    int max = INT_MIN;
    int min = INT_MAX;
    int sum = 0;
    int current = 0;
    for (int i = 1; i < argc; i++)
    {
        current = atoi(argv[i]);
        sum= sum + current;
        if (max < current)
        {
            max = current;
        }
        if (current < min)
        {
            min = current;
        }
    }
    printf("Average = %f\n", sum / (double)(argc -1));
    printf("Max = %d\n", max);
    printf("Min = %d\n", min);
    return 0;

Escribir un programa que use la función atan2() de math.h para calcular el ángulo que forma un vector de coordenadas (x, y) con el eje x. Por ejemplo el vector (1, 1) forma un ángulo de 45º y el vector (0, -1) un ángulo de 270º. La función atan2(y, x) calcula la arcotangente de y dividido x.

#include <stdio.h>
#include <math.h>

int main(void)
{
    int x, y;
    printf("Enter x and y\n");
    scanf("%i %i", &x, &y);
    printf("Angle is %f", atan2(x, y));
    return 0;
}

Escribir un programa que acepte como argumento un número entero e imprima el número con los digitos al revés. Por ejemplo para la entrada 12345 debe imprimir 54321.

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char const *argv[])
{
    char strnum[65535];
    printf("enter number\n");
    scanf("%s", strnum);
    size_t length = strlen(strnum);
    for (size_t i = length - 1; i >= 0; i--)
    {
        printf("%c", strnum[i]);
    }
    
    return 0;

Escribir un programa que use un ciclo for para imprimir los primeros n números de Fibonacci. Usar un argumento de línea de comandos para el valor de n. La sucesión de Fibonacci comienza así: 0, 1, 1, 2, 3, 5, 8, 13, 21 ... etc. El próximo número en la sucesión es la suma de los dos anteriores.

#include <stdio.h>

int main (void) {
    printf("Enter the length of the sequence\n");
    int length, a= 1, b= 0, i= 0;
    scanf("%d", &length);
    while (i < length) {
        b= b + a;
        printf("%d ", b);
        i++;
        if (i < length)
        {
            a= a + b;
            printf("%d ", a);
            i++;
        }
    }
    return 0;
}

Escribir un programa que calcule el factorial de un número n ingresado como argumento.

#define __USE_MINGW_ANSI_STDIO 1
#include <stdio.h>

int main(void) {
    size_t n, a= 1;
    printf("Enter a number\n");
    scanf("%zu", &n);
    printf("1 ");
    for (size_t i = 1; i <= n; i++)
    {
        a = a*i;
        printf("%zu ", a);
    }
    return 0;
}

Usando el Algoritmo de Euclides para encontrar el MCD (máximo común divisor) escribir un programa que acepte como argumento dos números enteros e imprima su MCD.

#include <stdio.h>

int gcd(int a, int b) {
    if (a<0) a= -a;
    if (b<0) b= -b;
    if (a < b) {
        int temp;
        temp= a;
        a= b;
        b= temp;
    }
    if (b == 0) return a;
    int r= a%b;
    if (r == 0) {return b;}else{return gcd(b, r);}
}

int main (void) {
    int a, b;
    printf("Enter two numbers\n");
    scanf("%d %d", &a, &b);
    printf("%d", gcd(a, b));
    return 0;
}

Escribir un programa que acepte un argumento n entero e imprima los números de 1 hasta n y su cuadrado.

#define __USE_MINGW_ANSI_STDIO 1
#include <stdio.h>

int main (void) {
    int a;
    printf("Enter a number\n");
    scanf("%i", &a);
    for (size_t i = 1; i <= a; i++)
    {
        printf("%zu ", i);
    }
    printf("\n%i", a*a);
    return 0;
}

Escribir un programa que imprima los números en el rango del 1 al 100 que al ser divididos por un argumento entero n, su resto sea igual a 3.

#include <stdio.h>
#include <stdlib.h>

int main (int argc, char const *argv[]) {
  int num = atoi(argv[1]);
  for (int i = 1; i <= 100; i++) {
    if ((i%num)==3) {
      printf("%d\t", i);
    }
  }
  printf("\n");
  return 0;
}

Escribir un programa que acepte dos argumentos enteros representando coordenadas en el plano cartesiano. El programa debe imprimir a que cuadrante pertenece el punto. Los cuadrantes del plano cartesiano se representan con los números romanos I, II, III y IV.

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char const *argv[]) {
  int x= atoi(argv[1]);
  int y= atoi(argv[2]);
  if (x>0 && y>0) {
    printf("The vector is in the 1st quadrant\n");
  } else if (x<0 && y>0) {
    printf("The vector is in the 2nd quadrant\n");
  } else if (x<0 && y<0) {
    printf("The vector is in the 3rd quadrant\n");
  } else if (x>0 && y<0) {
    printf("Vector is in the 4th quadrant\n");
  }
  return 0;
}

Escribir un programa que acepte dos números enteros y calcule su cociente. Si la división de los números no tiene resto igual a cero entonces imprimir "No se pueden dividir" y salir del programa. Por ejemplo, a = 20, b = 5 debe imprimir 4. Con a = 20 y b = 3 debe imprimir "No se pueden dividir".

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char const *argv[]) {
  int a= atoi(argv[1]);
  int b= atoi(argv[2]);
  if (a%b != 0) {
    printf("Cannot divide these numbers\n");
  }
  return 0;
}

Escribir un programa que acepte dos argumentos enteros a y b e imprima todos los números divisibles por 3 entre a y b. El segundo argumento tiene que ser mayor o igual que el primero. Si a es mayor a b el programa debe imprimir un mensaje indicando al usuario el uso correcto del programa y salir.
#define __USE_MINGW_ANSI_STDIO 1
#include <stdio.h>
#include <stdlib.h>

int main(void) {
  int i, b;
  printf("Enter first number\n");
  scanf("%d", &i);
  printf("Enter second number\n");
  scanf("%d", &b);
  while (i <= b) {
    if (i%3 == 0) printf("%d ", i);
    i++;
  }
  printf("\n");
  return 0;
}


