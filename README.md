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

Arrays en C
Escribir un programa que declare un array de tipo int que almacene los primeros diez números naturales. Imprimir el array un elemento por línea.

#include <stdio.h>

int main(void) {
int i = 0;
int numeros [10];
  for (i = 0; i < 10; i++) {
  numeros[i] = i + 1;
  printf("%d\n", numeros[i] );
}
  return 0;
}


Escribir un programa que haga lo mismo que el ejercicio anterior pero para los primeros n números naturales. El usuario ingresa n como argumento de línea de comandos.

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char const *argv[]) {
int n = atoi(argv[1]);
int numeros[n];
int i = 0;
for (i = 0; i < n; i++) {
  numeros[i] = i + 1;
  printf("%d\n", numeros[i] );
}
  return 0;
}

Escribir un programa que acepte dos argumentos n y m. El tamaño de un array es el argumento n. El programa llena el array con números aleatorios entre 0 y m y los imprime uno por línea.

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main(int argc, char const *argv[]) {
  srand(time(NULL));
  int n = atoi(argv[1]);
  int m = atoi(argv[2]);
  int numeros[n];
  for (i = 0; i < n; i++) {
    numero[i] = rand()%(m+1);
    printf("%d\n", numeros[i] );
  }

  return 0;
}

Escribir un programa que genere un array de 100 elementos con enteros aleatorios entre 0 y 100. Calcular el promedio de los valores en el array.

#include <stdio.h>
#include <time.h>

int main(void) {
  srand(time(NULL));
  int numeros[100];
  int sum= 0;

  for (i = 0; i < 100; i++) {
    numeros[i] = rand() %101;
    sum= numeros[i] + sum;
    printf("%d\n", sum/100 );
  }

  return 0;
}

Escribir un programa que genere un array de 100 lugares con enteros aleatorios entre 0 y 100. Encontrar el máximo y el mínimo del array.

#include <stdio.h>
#include <time.h>

int main(void) {
  srand(time(NULL))
  numeros[100];
  int max =101
  int min = -1

  for (i = 0; i < 100; i++) {
    numeros[i] = rand() %101;
  }
    if (numeros[i])>max {
      max = numeros[i]
    }
    if (numeros[i])<min {
      min = numeros[i]
    }

    printf("max: %d, min: %d",max,min);


  return 0;
}

Escribir un programa que calcule el producto punto entre dos vectores de dimensión N y valores reales. Siendo N una constante conocida en tiempo de compilación al igual que los componentes de los vectores.

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    int const n= 3;
    double v1[n];
    double v2[n];
    int prev= 0;
    for (size_t i = 0; i < n; i++)
    {
        if (prev != 0) {
            v1[i]= prev + 2;
            v2[i]= prev + 2;
        } else {
            v1[i]= 2;
            v2[i]= 2;
            prev= i + 2;
        }
    }
    double r= 0;
    for (size_t i = 0; i < 3; i++)
    {
        r+= v1[i] * v2[i];
    }
    printf("%lf\n", r);
    return 0;

Escribir un programa que genere un array de 100 elementos con valores aleatorios enteros del 0 al 9. Contar la cantidad de veces que aparece cada dígito en el array e imprimir una tabla con las frecuencias.

#define __USE_MINGW_ANSI_STDIO 1
#include <stdlib.h>
#include <stdio.h>
#include <time.h>
int main(void)
{
    srand(time(NULL));
    int randomNumbers[100];
    int counter[10]= {0};

    for (size_t i = 0; i< 100; i++) {
        randomNumbers[i]= rand()%10;
        counter[randomNumbers[i]]++;
    }
    for (size_t i = 0; i < 10; i++)
    {
        printf("%zu: %d%%\n", i, counter[i]);
    }
    return 0;
}

Escribir un programa que declare el array de enteros 1, 2, 3, 4, 5, 6 e invierta el orden del mismo. Luego imprimirlo.

#define __USE_MINGW_ANSI_STDIO 1
#include <stdlib.h>
#include <stdio.h>

int main(void)
{
    int numbers[]= {1,2,3,4,5,6};
    int invertedNumbers[(sizeof numbers)/sizeof numbers[0]];
    for (size_t i = 0; i < 6; i++)
    {
        invertedNumbers[i]= numbers[5-i];
        printf("%d\n", invertedNumbers[i]);
    }
    
    return 0;
}

Escribir un programa similar al anterior pero que invierta un array con los primeros 20 números pares.

#define __USE_MINGW_ANSI_STDIO 1
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main(void)
{
    srand(time(NULL));
    int numbers[100]= {0};
    int numbersLength= sizeof numbers/sizeof numbers[0];
    for (size_t i = 1; i < 20; i++)
    {
        numbers[i]= numbers[i-1]+2;
    }
    for (size_t i = 20; i < numbersLength; i++)
    {
        numbers[i]= rand()%100;
    }
    int invertedNumbers[numbersLength];
    for (size_t i = 0; i < numbersLength; i++)
    {
        invertedNumbers[i]= numbers[(numbersLength-1)-i];
        printf("%d\n", invertedNumbers[i]);
    }
    return 0;
}

Escribir un programa que imprima tres strings representando una mano de truco aleatoria, por ejemplo: "Cuatro de copas", "Ancho de espada", "Tres de basto".

#define __USE_MINGW_ANSI_STDIO 1
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <time.h>

int main(void)
{
    srand(time(NULL));
    char *type[4]= {"copas", "basto", "espada", "oro"};
    char *number[10]= {"Uno", "Dos", "Tres", "Cuatro", "Cinco", "Seis", "Siete", "Diez", "Once", "Doce"};
    char card[100]= "\0";
    for (size_t i = 0; i < 3; i++)
    {
        strcat(card, number[rand()%10]);
        strcat(card, " de ");
        strcat(card, type[rand()%4]);
        strcat(card, "\n");
    }
    printf("%s", card);
    return 0;
}


Escribir un programa que reciba un string como argumento y cuente la cantidad de carácteres en la palabra.

#define __USE_MINGW_ANSI_STDIO 1
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char const *argv[])
{
    printf("%zu", strlen(argv[1]));
    return 0;
}

Escribir un programa que reciba un string como argumento y decida si la palabra es un palíndromo o no.

#define __USE_MINGW_ANSI_STDIO 1
#include <stdlib.h>
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

int main(int argc, char const *argv[])
{
    bool isPalindrome= true;
    size_t arg1Length= strlen(argv[1]);
    for (size_t i = 0; i < arg1Length; i++)
    {
        if (argv[1][i] != argv[1][(arg1Length-1)-i]) {
            isPalindrome= false;
            break;
        }
    }
    printf("%s", isPalindrome ? "True" : "False");
    return 0;
}

Escribir un programa que reciba un argumento entero e imprima el mes del año correspondiente o un error si el argumento es menor a 1 o mayor a 12.

 #include <stdlib.h>
 #include <stdio.h>
 int main(int argc, char  *argv[]) {
int n=atoi(argv[1]);
char *meses[12]={"enero","febrero","marzo","abril","mayo","junio","julio","agosto","septiembre","octubre","noviembre","diciembre"};
if (n<1||n>12) {
  printf("error");
return 0;
}
printf("%s\n",meses[n-1] );

   return 0;
 }

Escribir un programa que declare un array de 40 posiciones representando un mazo de cartas para jugar al truco. El array debe estar ordenado por palo y número. Imprimir el mazo por consola.

#define __USE_MINGW_ANSI_STDIO 1
#include <stdlib.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
    char *type[4]= {"copas", "basto", "espada", "oro"};
    char *number[10]= {"Uno", "Dos", "Tres", "Cuatro", "Cinco", "Seis", "Siete", "Diez", "Once", "Doce"};
    char deck[40][100];
    int deckIndex= 0;
    for (int i = 0; i < 4; i++)
    {
        for (int j = 0; j < 10; j++) {
          sprintf(deck[deckIndex], "%s de %s\n", number[j], type[i]);
          deckIndex++;
        }
    }
    for (int i = 0; i < 40; i++)
    {
        printf(deck[i]);
    }
    return 0;
}

Escribir un programa que use el mazo de cartas del ejercicio anterior para repartir tres cartas. Mezclar el mazo antes de repartir. Imprimir una cantidad n de manos donde n es un argumento del programa.

##define __USE_MINGW_ANSI_STDIO 1
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <time.h>
#include <stdbool.h>

int main(int argc, char const *argv[])
{
    srand(time(NULL));
    char *type[4]= {"copas", "basto", "espada", "oro"};
    char *number[10]= {"Uno", "Dos", "Tres", "Cuatro", "Cinco", "Seis", "Siete", "Diez", "Once", "Doce"};
    char deck[40][100]= {{'\0'}};
    char *randDeck[40];
    int deckIndex= 0;
    int randIndexes[40]= {0};
    int n= atoi(argv[1]);
    for (int i = 0; i < 4; i++)
    {
        for (int j = 0; j < 10; j++) {
          char card[100] = "";
          strcat(card, number[j]);
          strcat(card, " de ");
          strcat(card, type[i]);
          strcat(deck[deckIndex], card);
          deckIndex++;
        }
    }
    int i= 1;
    while (i < 40) {
      int randNum= rand()%40;
      bool isUnique= true;
      if (randIndexes[i-1] == randNum) {
        isUnique= false;
      }
      if (isUnique) {
        randIndexes[i]= rand()%40;
        i++;
      }
    }
    for (size_t i = 0; i < 40; i++) {
      randDeck[i]= deck[randIndexes[i]];
    }
    for (size_t i = 0; i < n*3; i++) {
      printf("%s\n", randDeck[i]);
    }
    return 0;
  }


Escribir un programa que reciba un argumento de tipo string y busque en un array conocido en tiempo de compilación si el string está en el array. Si está el programa devuelve el índice del elemento y de lo contrario devuelve -1.

#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <stdbool.h>

int main(int argc, char const *argv[]) {
  char *text[]= {"ur mom", "69420", "69", "420"};
  bool match= false;
  for (size_t i = 0; i < 4; i++) {
    if (strcmp(argv[1], text[i])==0) {
      match= true;
      printf("%d\n", i);
    }
  }
  if (!match) {
    printf("-1\n");
  }
  return 0;
}


Escribir un programa que genere una lista con los primeros n números de Fibonacci usando un array de dimensión n.

#define __USE_MINGW_ANSI_STDIO 1
#include <stdlib.h>
#include <stdio.h>

int main(int argc, char const *argv[])
{
    int i= 2;
    int length= atoi(argv[1]);
    long long unsigned int fibonacci[length];
    fibonacci[0]= 0;
    fibonacci[1]= 1;
    while (i < length) {
        fibonacci[i]= fibonacci[i-1]+fibonacci[i-2];
        i++;
    }
    for (size_t j = 0; j < length; j++)
    {
        printf("%zu\n", fibonacci[j]);
    }
    
    return 0;
}


Escribir un programa que traduzca una palabra ingresada como argumento a código Morse, separando cada letra con un espacio. El programa recibe su argumento en letras minísculas únicamente.

#include <stdio.h>
#include <stdbool.h>
#include <string.h>
char morseAlphabet[26][100]= {"\0"};
void morseConstructor(void) {
    char d[]= "---";
    char p[]= ".";
    sprintf(morseAlphabet[0], "%s %s   ", p,d);
    sprintf(morseAlphabet[1], "%s %s %s %s   ", d,p,p,p);
    sprintf(morseAlphabet[2], "%s %s %s %s   ", d,p,d,p);
    sprintf(morseAlphabet[3], "%s %s %s   ", d,p,p);
    sprintf(morseAlphabet[4], "%s   ", p);
    sprintf(morseAlphabet[5], "%s %s %s %s   ", p,p,d,p);
    sprintf(morseAlphabet[6], "%s %s %s   ", d,d,p);
    sprintf(morseAlphabet[7], "%s %s %s %s   ", p,p,p,p);
    sprintf(morseAlphabet[8], "%s %s   ", p,p);
    sprintf(morseAlphabet[9], "%s %s %s %s   ", p,d,d,d);
    sprintf(morseAlphabet[10], "%s %s %s   ", d,p,d);
    sprintf(morseAlphabet[11], "%s %s %s %s   ", p,d,p,p);
    sprintf(morseAlphabet[12], "%s %s   ", d,d);
    sprintf(morseAlphabet[13], "%s %s   ", d,p);
    sprintf(morseAlphabet[14], "%s %s %s   ", d,d,d);
    sprintf(morseAlphabet[15], "%s %s %s %s   ", p,d,d,p);
    sprintf(morseAlphabet[16], "%s %s %s %s   ", d,d,p,d);
    sprintf(morseAlphabet[17], "%s %s %s   ", p,d,p);
    sprintf(morseAlphabet[18], "%s %s %s   ", p,p,p);
    sprintf(morseAlphabet[19], "%s   ", d);
    sprintf(morseAlphabet[20], "%s %s %s   ", p,p,d);
    sprintf(morseAlphabet[21], "%s %s %s %s   ", p,p,p,d);
    sprintf(morseAlphabet[22], "%s %s %s   ", p,d,d);
    sprintf(morseAlphabet[23], "%s %s %s %s   ", d,p,p,d);
    sprintf(morseAlphabet[24], "%s %s %s %s   ", d,p,d,d);
    sprintf(morseAlphabet[25], "%s %s %s %s   ", d,d,p,p);
    return;
}

int main(int argc, char const *argv[])
{
    morseConstructor();
    char morse[200]= {'\0'};
    for (size_t i = 0; i < strlen(argv[1]); i++)
    {
        int charToInt= (int)argv[1][i];
        bool isLetter= (charToInt > 96 && charToInt < 123);
        if (isLetter) {
            strcat(morse, morseAlphabet[charToInt-97]);
        } else {
            printf("Invalid inputs\n");
            return 0;
        }
    }
    printf("%s", morse);
    return 0;
    
}

Ampliar el programa anterior para traducir un mensaje de varias palabras. En la traducción a Morse cada letra está separada por un espacio y cada palabra con un |.

#include <stdlib.h>
#include <stdio.h>
#include <stdbool.h>
#include <string.h>
char morseAlphabet[26][100]= {"\0"};
void morseConstructor(void) {
    char d[]= "---";
    char p[]= ".";
    sprintf(morseAlphabet[0], "%s %s   ", p,d);
    sprintf(morseAlphabet[1], "%s %s %s %s   ", d,p,p,p);
    sprintf(morseAlphabet[2], "%s %s %s %s   ", d,p,d,p);
    sprintf(morseAlphabet[3], "%s %s %s   ", d,p,p);
    sprintf(morseAlphabet[4], "%s   ", p);
    sprintf(morseAlphabet[5], "%s %s %s %s   ", p,p,d,p);
    sprintf(morseAlphabet[6], "%s %s %s   ", d,d,p);
    sprintf(morseAlphabet[7], "%s %s %s %s   ", p,p,p,p);
    sprintf(morseAlphabet[8], "%s %s   ", p,p);
    sprintf(morseAlphabet[9], "%s %s %s %s   ", p,d,d,d);
    sprintf(morseAlphabet[10], "%s %s %s   ", d,p,d);
    sprintf(morseAlphabet[11], "%s %s %s %s   ", p,d,p,p);
    sprintf(morseAlphabet[12], "%s %s   ", d,d);
    sprintf(morseAlphabet[13], "%s %s   ", d,p);
    sprintf(morseAlphabet[14], "%s %s %s   ", d,d,d);
    sprintf(morseAlphabet[15], "%s %s %s %s   ", p,d,d,p);
    sprintf(morseAlphabet[16], "%s %s %s %s   ", d,d,p,d);
    sprintf(morseAlphabet[17], "%s %s %s   ", p,d,p);
    sprintf(morseAlphabet[18], "%s %s %s   ", p,p,p);
    sprintf(morseAlphabet[19], "%s   ", d);
    sprintf(morseAlphabet[20], "%s %s %s   ", p,p,d);
    sprintf(morseAlphabet[21], "%s %s %s %s   ", p,p,p,d);
    sprintf(morseAlphabet[22], "%s %s %s   ", p,d,d);
    sprintf(morseAlphabet[23], "%s %s %s %s   ", d,p,p,d);
    sprintf(morseAlphabet[24], "%s %s %s %s   ", d,p,d,d);
    sprintf(morseAlphabet[25], "%s %s %s %s   ", d,d,p,p);
    return;
}

int main(int argc, char const *argv[])
{
    morseConstructor();
    char morse[200]= {'\0'};
    int j= 1;
    while (j < argc)
    {
        for (size_t i = 0; i < strlen(argv[j]); i++)
        {
            int charToInt= (int)argv[j][i];
            bool isLetter= (charToInt > 96 && charToInt < 123);
            if (isLetter) {
                strcat(morse, morseAlphabet[charToInt-97]);
            } else {
                printf("Invalid inputs\n");
                return 0;
            }
        }
        strcat(morse, "| ");
        j++;
    }
    printf(
        morse);
    return 0;

Escribir un programa que convierta una palabra a todas letras minísculas. Ingresar la palabra como argumento.

#include <stdlib.h>
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

int main(int argc, char const *argv[])
{
    char stringInLowercase[200]= {0};
    for (size_t i = 0; i < strlen(argv[1]); i++)
    {
        int intChar= (int)argv[1][i];
        stringInLowercase[i]= (char)(intChar+32);
    }
    printf(stringInLowercase);
    return 0;
}

Escribir un programa que declare una matriz (array bidimensional) de 3 x 3 de números enteros. Los elementos de la matriz se conocen en tiempo de compilación. Imprimir la matriz, una fila por línea separando con espacios los elementos.

#include <stdlib.h>
#include <stdio.h>

int main(void)
{
    int array[][3]= {{55,6,1}, {5,3,4}, {6,8,1}};
    for (size_t i = 0; i < 3; i++)
    {
        for (size_t j = 0; j < 3; j++)
        {
            printf("%d ", array[i][j]);
        }
        printf("\n");
    }
    
    return 0;

Escribir un programa que acepte un argumento n y genere la matriz identidad de dimensión n x n. Usar arrays bidimensionales.

#include <stdlib.h>
#include <stdio.h>

int main(int argc, char const *argv[])
{
    int n= atoi(argv[1]);
    int array[n][n];
    for (size_t i = 0; i < n; i++)
    {
        for (size_t j = 0; j < n; j++)
        {
            array[i][j]= 0;
        }
        
    }
    
    for (size_t i = 0; i < n; i++)
    {
        array[n][n]= 1;
    }
    return 0;
}

Escribir un programa que declare un array de enteros de 3 x 3 y guarde en cada elemento los primeros 9 argumentos recibidos por línea de comandos.

#include <stdlib.h>
#include <stdio.h>

int main(int argc, char const *argv[])
{
    int matrix[3][3];
    int count =1;
    for (size_t i = 0; i < 3; i++)
    {
        for (size_t j = 0; j < 3; j++)
        {
            matrix[i][j]= atoi(argv[count]);
            count++;
        }
        
    }
    for (size_t i = 0; i < 3; i++)
    {
        for (size_t j = 0; j < 3; j++)
        {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }
    return 0;
}

Escribir un programa que declare dos matrices de 3 x 3 A y B y calcule una tercera matriz C = A + B. Imprimir C.

#include <stdlib.h>
#include <stdio.h>

int main(void)
{
    int matrixA[][3]= {{55,6,1}, {5,3,4}, {6,8,1}};
    int matrixB[][3]= {{55,6,1}, {5,3,4}, {6,8,1}};
    int matrixC[3][3];
    for (size_t i = 0; i < 3; i++)
    {
        for (size_t j = 0; j < 3; j++)
        {
            matrixC[i][j]= matrixA[i][j]+matrixB[i][j];
        }
        
    }
    for (size_t i = 0; i < 3; i++)
    {
        for (size_t j = 0; j < 3; j++)
        {
            printf("%d ", matrixC[i][j]);
        }
        printf("\n");
    }
    return 0;
}

Escribir un programa que calcule la traza de una matriz cuadrada. La traza es la suma de los elementos de la diagonal principal.

#include <stdlib.h>
#include <stdio.h>

int main(void)
{
    int matrix[][2]= {
        {2,6},
        {4,78}
    };
    int trace= 0;
    for (size_t i = 0; i < 2; i++)
    {
        trace+= matrix[i][i];
    }
    printf("%d", trace);
    return 0;
}


Escribir un programa que acepte un argumento p (probabilidad) y un argumento n. Crear una matriz que represente un tablero del juego buscaminas de n x n marcando con un -1 las casillas con minas o cero de lo contrario. Usar la probabilidad p para determinar si un casillero tiene o no una mina.

#include <time.h>

int main(int argc, char const *argv[])
{
    srand(time(NULL));
    int n= atoi(argv[1]);
    int chance= atoi(argv[2]);
    int matrix[n][n];
    for (size_t i = 0; i < n; i++)
    {
        for (size_t j = 0; j < n; j++)
        {
            if (chance <= ((rand()%100)+1))
            {
                matrix[i][j]= 1;
            } else {
                matrix[i][j]= 0;
            }
        }
        
    }
    for (size_t i = 0; i < n; i++)
    {
        for (size_t j = 0; j < n; j++)
        {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }
    return 0;
}

Siguiendo el programa anterior, volver a recorrer el array para llenar los casilleros sin minas con el número de minas vecinas. Consideren usar un array de n+2 x n+2 para representar el tablero.

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main(int argc, char const *argv[])
{
    srand(time(NULL));
    int n= atoi(argv[1]);
    int chance= atoi(argv[2]);
    int matrix[n+2][n+2];
    for (size_t i = 0; i < n+2; i++)
    {
        for (size_t j = 0; j < n+2; j++)
        {
            if (chance <= ((rand()%100)+1))
            {
                matrix[i][j]= -1;
            } else {
                matrix[i][j]= 0;
            }
        }
        
    }

    for (size_t i = 1; i < n+1; i++)
    {
        for (size_t j = 1; j < n+2; j++)
        {
            if (matrix[i][j]==0) {
                for (size_t y = 0; y < 3; y++)
                {
                    for (size_t x = 0; x < 3; x++)
                    {
                        if (matrix[(i-1)+y][(j-1)+x] == -1) {
                            matrix[i][j]++;
                        }
                    }
                    
                }
                
            }
        }
        
    }
        

    for (size_t i = 0; i < n; i++)
    {
        for (size_t j = 0; j < n; j++)
        {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }
    return 0;
}

Escribir un programa que implemente la multiplicación de matrices cuadradas de n x n. Dar valores a las matrices A y B en tiempo de compilación. Usar tres ciclos anidados.
Escribir un programa que declare y asigne valores a una matriz de 4 x 4. Imprimir el promedio de cada fila y cada columna.

#include <stdlib.h>
#include <stdio.h>

int main(void)
{
    int matrixA[3][3]= {
        {5,6,8},
        {83,4,8},
        {7,3,1}
    };
    int matrixB[3][3]= {
        {6,23,4},
        {47,6,2},
        {7,5,1}
    };
    int matrixResult[3][3]= {0};
    int count= 0;
    size_t mBj = 0, mBi=0, mAi=0,count1=0;

        int temp[3][3];
        while (mBi < 3)
        {
            while (mAi < 3)
            {
                temp[mBi][mAi]= matrixB[mBj][mBi]*matrixA[mBi][mAi];
                mAi++;
            }
            mBi++;
        }
        while (mBj < 3)
        {
            matrixResult[mBj][count]+= temp[count1][count];
            count1++;
            if (count1 ==3)
            {   
                count1= 0;
                count++;
                if (count== 3)
                {
                    count=0;
                    mBj++;
                }
            }
            
        }
    for (size_t i = 0; i < 3; i++)
    {
        for (size_t j = 0; j < 3; j++)
        {
            printf("%d ", matrixResult[i][j]);
        }
        printf("\n");
    }
    return 0;
}

Escribir un programa que simule lo que se conoce como "caminos aleatorios". Usar una matriz de números enteros de 15 x 15 inicialmente llena de ceros. Poner un 1 en el centro de la matriz e ir llenando con unos representando los pasos del "caminante". La caminata termina cuando se sale de la matriz original. El caminante puede dar un paso a la vez a la izquierda, derecha, arriba o abajo. Pero no puede volver sobre sus pasos. Imprimir la matriz que representa la caminata al terminar.

#include <stdlib.h>
#include <stdio.h>

int main(void)
{
    int matrix[4][4]= {
    {5,6,8,6},
    {83,4,8,7},
    {7,3,1,9},
    {5,8,4,3}
    };
    for (size_t i = 0; i < 4; i++)
    {
        double sum= 0;
        for (size_t j = 0; j < 4; j++)
        {
            sum+= matrix[i][j];
        }
        printf("%f ", sum/4);
    }
    printf("\n");
    for (size_t i = 0; i < 4; i++)
    {
        double sum= 0;
        for (size_t j = 0; j < 4; j++)
        {
            sum+= matrix[j][i];
        }
        printf("%f ", sum/4);
    }
    
    return 0;
}

Funciones
Escribir una función saludar() que imprima un saludo en pantalla.

#include <stdio.h>
#include <stdlib.h>
void saludar(){
printf("Hola\n");
}
int main(void){
saludar();

  return 0;
}

Escribir una función saludar() que reciba un argumento de tipo string e imprima "Hola, ". Por ejemplo saludar("Juan") imprime "Hola, Juan".

#include <stdio.h>
#include <stdlib.h>
void saludar(char *e){
printf("Hola,%s\n",e);
}

int main(void){
saludar("Juan");
  return 0;
}

Escribir una función que devuelva 1 o 0 según sus tres argumentos enteros sean iguales entre sí o no.

#include <stdio.h>
#include <stdlib.h>

int iguales(int x, int y, int z){
  if (x==y && x==z && y==z) {
   return 1;
  } else {
    return 0;
  }
}


int main(int argc, char  *argv[]) {
int x=atoi(argv[1]);
int y=atoi(argv[2]);
int z=atoi(argv[3]);
printf("%d\n",iguales(x,y,z));
  return 0;
}


Escribir una función is_triangle() que reciba tres argumentos enteros y devuelva 1 si los tres argumentos pueden ser la longitud de los tres lados de un triángulo. Devolver cero en caso contrario.

#include <stdio.h>
#include <stdlib.h>

int is_triangle(int a,int b,int c){
  if (a<b+c && b<a+c && c<a+b) {
    return 1;
  } else {
    return 0;
  }
}

int main(int argc, char *argv[]) {
  int a=atof(argv[1]);
  int b=atof(argv[2]);
  int c=atof(argv[3]);
printf("%d\n",is_triangle(a,b,c) );

  return 0;
}


Escribir una función que calcule las raíces de una función cuadrática. Usar tres argumentos double a, b y c. Devolver NAN si no hay raíces reales.

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
double resolvente(double a, double b, double c){
  if (a==0) {
  return NAN;
  }
  double discriminant = b * b - 4.0 * a * c;
  if (discriminant < 0) {
  return NAN;
  }

  double root = sqrt(discriminant);
  printf("x1: %.2f\n", (-b + root) / (2.0 * a));
  printf("x2: %.2f\n", (-b - root) / (2.0 * a));
}

int main(int argc, char  *argv[]) {
  double a=atof(argv[1]);
  double b=atof(argv[2]);
  double c=atof(argv[3]);
  printf("%.2f\n", resolvente(a,b,c));
  return 0;
}

Escribir una función random() que reciba dos enteros a y b y devuelva un entero aleatorio entre a y b.

#include <time.h>
#include <stdio.h>
#include <stdlib.h>

int N_random(int a, int b){
  return (random() % (b - a + 1)+ a);
}


int main(int argc, char  *argv[]) {
  srand(time(NULL));
  int a=atoi(argv[1]);
  int b=atoi(argv[2]);

  printf("%d\n",N_random(a,b));
  return 0;
}

Escribir una función que reciba un array y su longitud e imprima el array por consola, separando cada número con un espacio y un \n al terminar.

#include <stdio.h>
#include <stdlib.h>
void print_array(int n,int array[]){
for (int i = 0; i < n; i++) {
  printf("%d ", array[i] );
}

printf("\n");
}


int main(int argc, char  *argv[]) {
  int lista[] = {1,2,3};
  print_array(3, lista);
  return 0;
}

Escribir una función que cuente la cantidad de carácteres en un string.

#include <stdio.h>
#include <stdlib.h>
void Char_Cant(char *a) {
  int i=0;
  while (a[i]) {
    printf("%c",a[i] );
    i++;
  }
printf(" tiene %d caracteres\n",i );
}


int main(int argc, char  *argv[]) {
// char a=atoi(argv[1]);
  Char_Cant(argv[1]);
  return 0;
}

Escribir una función que intercambie dos valores en un array de enteros.

#include <stdio.h>
#include <stdlib.h>

void print_array(int n,int array[]){
for (int i = 0; i < n; i++) {
  printf("%d ", array[i] );
}

printf("\n");
}

void changer(int i,int j,int lista[]){
int temp=lista[i];
  lista[i]=lista[j];
  lista[j]=temp;


}


int main(int argc, char  *argv[]) {
  int i=atoi(argv[1]);
int j=atoi(argv[2]);
  int lista[9] = {1,2,3,4,5,6,7,8,9};
  print_array(9, lista);
   changer(i,j,lista);
   print_array(9, lista);
  return 0;
}

Escribir una función que intercambie los valores de dos variables enteras.

#include <stdio.h>
#include <stdlib.h>

void swap(int a,int b) {
  int temp=a;
  a=b;
  b=temp;
  printf("%d,%d\n",a,b );
}

int main(int argc, char  *argv[]) {
  int a=atoi(argv[1]);
  int b=atoi(argv[2]);
printf("%d,%d\n",a,b );
swap(a,b);
  return 0;
}

Escribir una función que devuelva el máximo en un array de enteros.

#include <stdio.h>
#include <stdlib.h>
void array_max(int array[]) {
  int max=-99999;
  for (int i = 0; i < 5; i++) {
    if(array[i]>max)max=array[i];
  }
  printf("%d\n",max );
}


int main(void) {
  int lista[]={1,3,5,4,2};
  array_max(lista);
  return 0;
}


Escribir una función que devuelva el mínimo en un array de enteros.

#include <stdio.h>
#include <stdlib.h>
void array_max(int array[]) {
  int min=99999;
  for (int i = 0; i < 5; i++) {
    if(array[i]<min)min=array[i];
  }
  printf("%d\n",min );
}


int main(void) {
  int lista[]={1,3,5,4,2};
  array_max(lista);
  return 0;
}

Escribir una función que calcule el factorial de un entero n.

#include <stdio.h>
#include <stdlib.h>
int factorial(int a){
  int j=1;
  for (int i = 1; i < a+1; i++) {
    j*=i;

  }
  return j;
}


int main(int argc, char  *argv[]) {
  int a=atoi(argv[1]);
  printf("%d\n",factorial(a) );
    return 0;
}


Escribir una función que calcule el MCD de dos enteros usando el algoritmo de Euclides.

#include <stdio.h>
#include <stdlib.h>
int mcd(int a, int b) {
    if(b == 0) return a;
    return mcd(b, a%b);
}


int main(int argc, char  *argv[]) {
  int a=atoi(argv[1]);
  int b=atoi(argv[2]);
  printf("%d\n",mcd(a,b) );
  return 0;
}

Escribir una función que devuelva la enésima potencia de dos.
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
int potencia(int n){return pow(2,n);}

int main(int argc, char  *argv[]) {
int n=atoi(argv[1]);
printf("%d\n",potencia(n));
  return 0;
}


Escribir una función que determine si un string es palíndromo o no.

#include <stdlib.h>
#include <stdio.h>
#include <stdbool.h>


bool palindromo(char a[]) {


bool EsPalindromo=true;

    int length=0;
    while (a[length] != 0) length++;

for (int i = 0; i < length/2 ; i++) {
  if (!(a[i] == a[length-i-1])) {
    EsPalindromo=false;
  }
}

if (EsPalindromo) {
  return true;
}else {
return false;
}
}

int main(int argc, char *argv[]){
  printf("%d\n", palindromo(argv[1]));
  return 0;
}
Escribir una función que calcule el producto punto de dos vectores de dimensión N.

#include <stdio.h>
#include <stdlib.h>
int producto_escalar(int n){
int a[n];
int b[n];
for (int i = 1; i < n+1; i++) {
  a[i]=i;
  b[i]=i;
}
int producto_escalar=0;
  for (int i = 0; i < n+1; i++) {
    producto_escalar=producto_escalar+(a[i]*b[i]);
  }

return producto_escalar;

}


int main(int argc, char  *argv[]) {
  int n=atoi(argv[1]);
  printf("%d\n", producto_escalar(n));
  return 0;
}
Escribir una función que calcule el factorial de un número de manera recursiva.
#include <stdio.h>
#include <stdlib.h>

int factorial(int a) {
  if (a == 0) return 1;
  return factorial(a - 1) * a;
}

int main(int argc, char  *argv[]) {
  int a=atoi(argv[1]);
  printf("%d\n",factorial(a));
  return 0;
}


Escribir una función recursiva que calcule el enésimo número de Fibonacci.

#include <stdlib.h>
#include <stdio.h>

void fibo(int n){

int fibonacci[n];
fibonacci[0]=0;
fibonacci[1]=1;
for (int i = 2; i < n; i++) {
fibonacci[i]= fibonacci[i-1]+fibonacci[i-2];
}
for (int i = 0; i < n; i++) {
  printf("%d ", fibonacci[i]);
}
printf("\n" );
}

int main(int argc, char  *argv[]) {
int n=atoi(argv[1]);
  fibo(n);
  return 0;
}

Escribir una función que busque un número en un array de enteros y devuelva el índice en el array si lo encuentra o -1 en caso contrario.
#include <stdio.h>
#include <stdlib.h>

int buscar(int a[],int size,int search){
  for (int i = 0; i < size; i++) {
    if (a[i]==search)return i;
  }
  return -1;
}

int main(int argc, char  *argv[]) {
  int a[]={1,2,3,4,5,6,7,8};
  printf("%d\n", buscar(a,8,8));
  return 0;
}
