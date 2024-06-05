Realizado por:
  <li> Jose Antonio Guerrero Lazcano</li>
<h2 align = "center"> <font color = "darkorange" size = "+6"  font face = "bauhaus 93">  Indice </font> </h2>
<header> <font color = "red" size="+1" font face = "aharoni">
                <nav class="navegacion">
                    <ul class="Indice">
                       <li> <a href="#Descripción"> Descripción del Problemario </a> <br> </li>
                        <li> <a href="#Sobre la materia"> Sobre la materia </a> <br> </li>
                            <ul class="subindice"> 
                                <li> <a href="#Competencia de la Asignatura"> Competencia de la Asignatura </a> </li>
                                <li> <a href="#Competencia del tema"> Competencia del TEMA </a> </li>
                            </ul>
     <li> <a href="#Métodos numéricos para encontrar las raíces de ecuaciones que se encuentran en nuestro repositorio"> Sistemas de ecuaciones </a> <br> </li>
                            <ul class="subindice"> 
                                <li> <a href="#Eliminacion"> Eliminación-Gaussiana </a> </li>
                                <li> <a href="#Gauss"> Gauss-Jordan </a> </li>
                                <li> <a href="#Seidel"> Gauss-Seidel </a> </li> 
                                <li> <a href="#Jacobi"> Método de Jacobi </a> </li> 
                              <li> <a href = "#Descripción"> Descripción </a> <br> </li>
        <li> <a href = "#Temario"> Temario </a> <br> </li>
        <li> <a href = "#Métodos"> Métodos </a> <br> </li>
          <ul class = "subindice">
              <li> <a href="# Método del Trapecio "> Método del Trapecio </a> <br> </li>
              <li> <a href="# Método de Simpson 1/3 "> Método de Simpson 1/3 </a> <br> </li>
              <li> <a href="# Método de Simpson 3/8"> Método de Simpson 3/8 </a> <br> </li> 
              <li> <a href="# Método de la Cuadratura Gaussiana "> Método de la Cuadratura Gaussiana </a> <br> </li> 
                            </ul>
                    </ul>
                        <li> <a href="#Lineal"> Interpolación lineal (5 ejemplos). </a> </li>
                                <li> <a href="#cuadratica"> Interpolación cuadratica (1 ejemplo). </a> </li>
                                <li> <a href="#langrage"> Interpolación langrage (5 ejemplos). </a> </li> 
                                <li> <a href="#Newton"> Interpolación de newton (5 ejemplos). </a> </li> 
                       <li> <a href="#Lineal"> Euler (4 ejemplos). </a> </li>
                                <li> <a href="#Cuadratica"> Runge-Kutta (4 ejemplos). </a> </li>
                                <li> <a href="#Langrage"> Taylor (4 ejemplos). </a> </li> 
                </nav>
            </font> </header>

# Descripción
En este documento vamos a ver varios ejercicios sobre los distintos metodos como lo son:
  <li>1.- Eliminación-Gaussiana</li>
  <li>2.- Gauss-Jordan</li>
  <li>3.- Gauss-Seidel</li>
  <li>4.- Jacobi</li>
  
# Sobre la materia 
<h2 align = "center"> <font  size = "+6" > <a name="Competencia de la Asignatura">Competencia de la asignatura</font></a> </h2>
Aplica los métodos numéricos para resolver problemas científicos y de ingeniería utilizando la computadora.
<h2 align = "center"> <font size = "+6"  > <a name="Competencia del tema">Competencia del tema</font> </a></h2>
Aplica los métodos numéricos con el objeto de solucionar ecuaciones mediante los métodos de intervalo e interpolación apoyada de un lenguaje de programación.  

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<h1 align = "center"> <font  font face = "bauhaus 93"> <a name="Sistemas de ecuaciones"> Sistemas de ecuaciones </font></a> </h1>

<h2 align = "center"> <font font face = "forte"><a name="Eliminacion">  1. Eliminación Gaussiana </h2></a>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

La eliminación gaussiana es un método utilizado en álgebra lineal para resolver sistemas de ecuaciones lineales de una manera sistemática y paso a paso. Este método consiste en llevar un sistema de ecuaciones a una forma matricial, convertir una matriz cuadrada en una matriz triangular superior equivalente a la original y luego resolver el sistema sustituyendo las variables en cada ecuación resultante:

<h3> <font font face = "arial">Pasos de la eliminación Gaussiana:</h3>
<h5>Formar la matriz aumentada:</h5> Combinar la matriz de coeficientes y el vector de términos independientes en una sola matriz aumentada.
<h5>Pivoteo parcial: </h5> Si es necesario, intercambiar filas para asegurar que el elemento en la posición de pivote sea el mayor en valor absoluto en su columna.
<h5>Escalonar la matriz: </h5> Comenzar con la primera fila y hacer ceros debajo del elemento de pivote, utilizando operaciones elementales de fila.
<h5>Repetir el proceso: </h5> Aplicar el mismo procedimiento a las filas restantes, avanzando hacia abajo y creando ceros debajo de los pivotes.
<h5>Sustitución hacia atrás: </h5> Una vez que la matriz está en forma triangular superior, resolver el sistema de ecuaciones resultante mediante sustitución hacia atrás, empezando por la última ecuación y despejando las incógnitas hacia arriba.
<h5>Verificar la solución: </h5> Sustituir las soluciones encontradas en las ecuaciones originales para comprobar si satisfacen todas las ecuaciones del sistema.
   
<h5> <font font face = "arial"> <b> <i> Ejemplo 1: </i> </b> </h5>

    package Eliminacion_Gaussiana;

    public class ejercicio1 {

    public static void main(String[] args) {
        int n = 3;
        double[][] matrix = {
                {3.0, -0.1, -0.2, 7.85},
                {0.1, 7.0, -0.3, -19.3},
                {0.3, -0.2, 10.0, 71.4}
        };
        double[] result = Eliminacion(matrix, n);
        for (int i = 0; i < n; i++) {
            System.out.println("x[" + i + "] = " + result[i]);
        }
    }

    public static double[] Eliminacion(double[][] matrix, int n) {
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                double factor = matrix[j][i] / matrix[i][i];
                for (int k = i; k < n + 1; k++) {
                    matrix[j][k] -= factor * matrix[i][k];
                }
            }
        }

        double[] result = new double[n];
        for (int i = n - 1; i >= 0; i--) {
            result[i] = matrix[i][n];
            for (int j = i + 1; j < n; j++) {
                result[i] -= matrix[i][j] * result[j];
            }
            result[i] /= matrix[i][i];
        }

        return result;
    }
    }



![Captura de pantalla 2024-05-30 230412](https://github.com/AntonioGuerrer0/Problemario_TEMA_3/assets/161759650/9e71a232-e654-43b5-b365-b490ccc00c04)


      


<h2 align = "center"> <font font face = "forte"> <a name="Gauss">  2.- Gauss-Jordan </h2></a>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

El método de Gauss-Jordan es una variante del método de eliminación gaussiana que se utiliza para resolver sistemas de ecuaciones lineales. En este método, al igual que en la eliminación gaussiana, se busca llevar la matriz de coeficientes a una forma escalonada, pero con la diferencia de que se busca obtener una matriz escalonada reducida a su forma más simple, conocida como forma escalonada reducida por filas o forma canónica.

<h3> <font font face = "arial">Pasos del Método de Gauss Jordan: </h3>
<h5>Formar la Matriz Aumentada: </h5> Se comienza escribiendo el sistema de ecuaciones en forma matricial, creando una matriz aumentada que incluya tanto los coeficientes de las variables como los términos independientes.
<h5>Escalonar la Matriz: </h5>Se aplican operaciones elementales de fila para obtener ceros debajo de la diagonal principal y unos en la diagonal principal. Esto implica realizar operaciones como intercambiar filas, multiplicar filas por constantes y sumar múltiplos de unas filas a otras.
<h5>Reducir la Matriz a su Forma Escalonada Reducida: </h5>Se continúa escalonando la matriz hasta obtener una forma escalonada reducida, donde la parte de los coeficientes de las variables se convierte en una matriz identidad.
<h5>Obtener las Soluciones: </h5>Una vez se ha alcanzado la forma escalonada reducida, se leen las soluciones directamente de la matriz identidad. Cada fila de la matriz identidad corresponde a una variable del sistema de ecuaciones.
<h5>Verificar las Soluciones: </h5> Es importante comprobar las soluciones obtenidas sustituyéndolas en las ecuaciones originales para asegurarse de que satisfacen todas las ecuaciones del sistema.
   
<h5> <font font face = "arial"> <b> <i> Ejemplo 1: </i> </b> </h5>


    package Gauss_Jordan;
    
    /**
     *
     * @author tono_
     */
    public class ejercicio1 {
    
       
        public static void main(String[] args) {
           System.out.println("GAUSS-JORDAN");
            double[][] matriz = 
            {   {3, -1, 2, 5},
                {2, 1, 1, 7},
                {1, 3, -2, 4} };
            double[][] resultados = operaciones(matriz);
            Resultados(resultados);
        }
    
        public static double[][] operaciones(double[][] matriz) {
            int fila = matriz.length;
            int columna = matriz[0].length;
            for (int i = 0; i < fila; i++) {
                double pivote = matriz[i][i];
                for (int j = i + 1; j < columna; j++) {
                    matriz[i][j] /= pivote;
                }
                matriz[i][i] = 1;
                for (int j = 0; j < fila; j++) {
                    if (i != j) {
                        double epala = matriz[j][i];
                        for (int k = i; k < columna; k++) {
                            matriz[j][k] -= epala * matriz[i][k];
                        }
                    }
                }
            }
            return matriz;
        }
    
        public static void Resultados(double[][] matriz) {
            System.out.println("Los resultados son: ");
            System.out.println("X = " + matriz[0][3]);
            System.out.println("Y = " + matriz[1][3]);
            System.out.println("Z = " + matriz[2][3]);
        }
    }


![Captura de pantalla 2024-05-30 230610](https://github.com/AntonioGuerrer0/Problemario_TEMA_3/assets/161759650/2e6dadab-2acd-4e4d-85d3-2e7e66ea4e44)


    
<h2 align = "center"> <font font face = "forte"> <a name="Seidel">  3.- Gauss-Seidel </h2></a>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

El método de Gauss-Seidel es una técnica iterativa utilizada para resolver sistemas de ecuaciones lineales. En este método, se mejora el método de Jacobi al utilizar las soluciones más recientes a medida que se calculan, en lugar de esperar a completar una iteración completa. Esto significa que las soluciones se actualizan en cada paso, lo que puede acelerar la convergencia del método.

<h3> <font font face = "arial">Pasos de Gauss-Seidel:</h3>
<h5>Inicialización de las Variables: </h5> Se comienza con una estimación inicial de las soluciones del sistema de ecuaciones lineales.
<h5>Iteración:</h5>Para cada ecuación en el sistema:
<li>Utilizar los valores más recientes de las variables ya calculadas.</li>
<li>Resolver la ecuación para encontrar una nueva estimación de la variable.</li>
<li>Actualizar el valor de la variable con la nueva estimación.</li>
<li>Repetir este proceso para todas las ecuaciones del sistema en cada iteración.</li>
<h5>Criterio de parada:</h5><li>Establecer un criterio de convergencia, como una tolerancia o un número máximo de iteraciones.</li>
<li>Verificar si se ha alcanzado la precisión deseada o el número máximo de iteraciones.</li>
<h5>Convergencia:</h5><li> Comprobar si el método converge hacia la solución del sistema de ecuaciones lineales.</li>
<li>Ajustar los parámetros, como la elección inicial y la precisión, si es necesario para mejorar la convergencia.</li>
<h5>Obtencion de soluciones:</h5> <li>Una vez que se alcanza la convergencia, las soluciones obtenidas en la última iteración se consideran como las soluciones aproximadas del sistema de ecuaciones lineales.</li>
   
<h5> <font font face = "arial"> <b> <i> Ejemplo 1: </i> </b> </h5>

   
    package Seidel;
    
    /**
     *
     * @author tono_
     */
    public class ejercicio1 {
    
        /**
         * @param args the command line arguments
         */
        public static void main(String[] args) {
        double[][] A = {
                    {3.0, -0.1, -0.2},
                    {0.1, 7.0, -0.3},
                    {0.3, -0.2, 10.0}
            };
            double[] b = {7.85, -19.3, 71.4};
            double[] x = gaussSeidel(A, b);
            for (int i = 0; i < x.length; i++) {
                System.out.println("x[" + i + "] = " + x[i]);
            }
            
            System.out.println("Me da ese redondeo por la tolerancia de los puntos decimales. ");
    
        }
    
        public static double[] gaussSeidel(double[][] A, double[] b) {
            int n = A.length;
            double[] x = new double[n];
            double[] newX = new double[n];
            int max = 100;
            double epsilon = 1e-10;
    
            for (int iter = 0; iter < max; iter++) {
                for (int i = 0; i < n; i++) {
                    newX[i] = b[i];
                    for (int j = 0; j < n; j++) {
                        if (j != i) {
                            newX[i] -= A[i][j] * x[j];
                        }
                    }
                    newX[i] /= A[i][i];
                }
    
                boolean stop = true;
                for (int i = 0; i < n; i++) {
                    if (Math.abs(newX[i] - x[i]) > epsilon) {
                        stop = false;
                        break;
                    }
                }
    
                if (stop) {
                    break;
                }
    
                System.arraycopy(newX, 0, x, 0, n);
            }
            return x;
        }
    }
![Captura de pantalla 2024-05-30 230740](https://github.com/AntonioGuerrer0/Problemario_TEMA_3/assets/161759650/df17d8f7-4d84-4434-920e-ad37743069b2)



    

    
<h2 align = "center"> <font font face = "forte"> <a name="Jacobi">  4. Jacobi </h2></a>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

El método de Jacobi es un algoritmo iterativo utilizado para resolver sistemas de ecuaciones lineales. En este método, se descompone la matriz de coeficientes del sistema en una suma de una matriz diagonal y dos matrices complementarias. Luego, se utiliza esta descomposición para iterar y encontrar soluciones aproximadas para el sistema de ecuaciones.

<h3> <font font face = "arial">Pasos del método de Jacobi:</h3>
<h5>Descomposición de la matriz: </h5><li> Descomponer la matriz de coeficientes del sistema en una matriz diagonal 
D y dos matrices complementarias L y U, de forma que = ++A=D+L+U, donde:</li>
<li>D es la matriz diagonal que contiene los elementos diagonales de A.
<li>L es la matriz triangular inferior con ceros en la diagonal.</li>
<li>U es la matriz triangular superior con ceros en la diagonal.</li>
<h5>Inicialización: </h5><li>Inicializar un vector de soluciones inicial x(0).</li>
<li>Establecer un criterio de convergencia, como una tolerancia ϵ o un número máximo de iteraciones.</li>
<h5>Iteración: </h5><li>Establecer un criterio de convergencia, como una tolerancia o un número máximo de iteraciones.</li>
<li>Verificar si se ha alcanzado la precisión deseada o el número máximo de iteraciones.</li>
<h5>Criterio de Parada: </h5><li>Verificar si se ha alcanzado la convergencia comparando la diferencia entre las soluciones actuales y las anteriores con la tolerancia establecida.</li>
<li>Detener las iteraciones si se cumple el criterio de convergencia o se alcanza el número máximo de iteraciones.</li>
<h5>Obtencion de soluciones:</h5> <li>Las soluciones aproximadas obtenidas en la última iteración se consideran como las soluciones del sistema de ecuaciones lineales.</li>
   
<h5> <font font face = "arial"> <b> <i> Ejemplo 1: </i> </b> </h5>

    package Jacobi;
    
    /**
     *
     * @author tono_
     */
    public class ejercicio1 {
    
         public static final double EPSILON = 0.0001;
        public static final int MAX_ITERATIONS = 100;
    
        public static void main(String[] args) {
            double[][] coefficients = {{3, -1, 1}, {2, 4, -1}, {-1, 2, 5}};
            double[] constants = {4, 1, 1}; 
            double[] solution = solveJacobi(coefficients, constants);
            
            System.out.println("Solución encontrada:");
            for (int i = 0; i < solution.length; i++) {
                System.out.println("x" + (i + 1) + " = " + solution[i]);
            }
        }
    
        public static double[] solveJacobi(double[][] coefficients, double[] constants) {
            int n = constants.length;
            double[] solution = new double[n];
            double[] nextSolution = new double[n];
            int iterations = 0;
            boolean converged = false;
    
            while (!converged && iterations < MAX_ITERATIONS) {
                for (int i = 0; i < n; i++) {
                    double sum = constants[i];
                    for (int j = 0; j < n; j++) {
                        if (j != i) {
                            sum -= coefficients[i][j] * solution[j];
                        }
                    }
                    nextSolution[i] = sum / coefficients[i][i];
                }
    
                double maxDifference = 0.0;
                for (int i = 0; i < n; i++) {
                    double difference = Math.abs(nextSolution[i] - solution[i]);
                    if (difference > maxDifference) {
                        maxDifference = difference;
                    }
                }
    
                if (maxDifference < EPSILON) {
                    converged = true;
                }
    
                for (int i = 0; i < n; i++) {
                    solution[i] = nextSolution[i];
                }
    
                iterations++;
            }
    
            if (iterations == MAX_ITERATIONS) {
                System.out.println("El método no converge después de " + MAX_ITERATIONS + " iteraciones.");
            }
    
            return solution;
        }
    }


![Captura de pantalla 2024-05-30 230853](https://github.com/AntonioGuerrer0/Problemario_TEMA_3/assets/161759650/c0a992a2-95d0-4b6d-a90f-b1c3038aec55)

<h1> <font color = "darkred" size="+5" font face = "cooper black"> <b> <i> Tema 4: Métodos de solución de problemas aplicando diferenciación y integración<i> </b> </font> </h1>
<h3 align = "center"> <font  font face = "bauhaus 93">  <a name="Descripción"> Descripción</a> </font> </h3>

En este documento podremos obser el funcionamiento de diversos métodos aplicandolos en funciones de diferenciación e integración númerica, los cuales son:

  1. Método del Trapecio 
  2. Método de Simpson 1/3
  3. Método de Simpson 3/8
  4. Método de la Cuadratura Gaussiana

En cada una de las carpetas podremos encontrar lo que son los códigos de cada método, tanto de su diferenciación como la de integración, y en cada carpeta podremos encontrar cinco programas los cuales estan desarrollados en el lenguaje de programación Java, en los cuales estarán documentados para un mayor entendimiento del programa.

-----------------------------------------------------------------------------------------

<h3 align = "center"> <font  font face = "bauhaus 93">  <a name="Temario"> Temario</a> </font> </h3>

   4.1 Diferenciación Numérica 
   
   4.2 Integración Numérica
   
   4.3 Integración Múltiple
   
   4.4 Aplicación

-----------------------------------------------------------------------------------------

<h2 align = "center"> <font  font face = "bauhaus 93"> <a name="Métodos"> Métodos</a> </font> </h2>

<h3 align = "center"> <font  font face = "bauhaus 93"> <a name=" Método del Trapecio ">  Método del Trapecio </a> </font> </h3>

<h4> <font font face = "arial"> Descripción </h4>
  
el Método del Trapecio es una técnica numérica utilizada para aproximar el valor de una integral definida. Consiste en dividir el intervalo de integración en segmentos pequeños y aproximar el área bajo la curva utilizando trapecios en lugar de rectángulos, lo que generalmente mejora la precisión de la aproximación. Este método se basa en la idea de que un trapecio puede aproximar mejor el área bajo una curva que un rectángulo.
<h4> <font font face = "arial">Pseudocódigo </h4>
  
1. Pseudocódigo para realizar la integración

        Función Trapecio_Integración(f, a, b, n):
            h = (b - a) / n
            suma = 0.5 * (f(a) + f(b))
            Para i desde 1 hasta n-1:
                xi = a + i * h
                suma = suma + f(xi)
            resultado = h * suma
            Devolver resultado


2. Pseudocódigo para realizar la diferenciación

        Función Trapecio_Diferenciación(f, a, b, n):
            h = (b - a) / n
            suma = f(a) + f(b)
            Para i desde 1 hasta n-1:
                xi = a + i * h
                suma = suma + 2 * f(xi)
            resultado = h * suma / 2
            Devolver resultado

<h4> <font font face = "arial"> <b> <i> Ejemplo en código </i> </b> </h4>

    package Método_Trapecio;

    import java.util.function.Function;

    public class ejercicio1 {

    public static double integrate(double a, double b, int n, Function<Double, Double> func) {
        double h = (b - a) / n;
        double sum = 0.5 * (func.apply(a) + func.apply(b));

        for (int i = 1; i < n; i++) {
            double x = a + i * h;
            sum += func.apply(x);
        }

        return h * sum;
    }

    public static double differentiate(double x, double h, Function<Double, Double> func) {
        double result = (func.apply(x + h) - func.apply(x - h)) / (2 * h);
        return result;
    }

    public static void main(String[] args) {
        Function<Double, Double> func = (x) -> Math.cos(x); // Función: cos(x)
        double a = 0; // Límite inferior
        double b = Math.PI / 2; // Límite superior
        int n = 100; // Número de segmentos
        double x0 = Math.PI / 4; // Punto en el que se desea calcular la derivada
        double h = 0.01; // Tamaño del paso

        double integral = integrate(a, b, n, func);
        System.out.println("Integral de cos(x) de 0 a π/2: " + integral);

        double derivative = differentiate(x0, h, func);
        System.out.println("Derivada de cos(x) en x = " + x0 + ": " + derivative);
    }
    }


<h4> <font font face = "arial"> Programa ejecutado </h4>

![Captura de pantalla 2024-05-30 225009](https://github.com/AntonioGuerrer0/PROBLEMARIO_TEMA-4/assets/161759650/5e1d96cd-c1f1-49dd-b003-6ea76beb8026)


<h3 align = "center"> <font  font face = "bauhaus 93"> <a name=" Método de Simpson 1/3 ">  Método de Simpson 1/3 </a> </font> </h3>

<h4> <font font face = "arial"> Descripción </h4>

el Método de Simpson 1/3 es otro método numérico utilizado para aproximar el valor de una integral definida. Este método es más preciso que el Método del Trapecio y se basa en la interpolación de la función integranda por medio de polinomios de segundo grado (parábolas).
<h4> <font font face = "arial">Pseudocódigo </h4>
  
1. Pseudocódigo para realizar la integración

        Función Simpson_Integración(f, a, b, n):
            h = (b - a) / n
            suma = f(a) + f(b)
            Para i desde 1 hasta n-1:
                xi = a + i * h
                Si i es impar:
                    suma = suma + 4 * f(xi)
                Sino:
                    suma = suma + 2 * f(xi)
            resultado = h * suma / 3
            Devolver resultado

2. Pseudocódigo para realizar la diferenciación
    
       Función Simpson_Diferenciación(f, a, b, n):
        h = (b - a) / n
        suma = f(a) + f(b)
        Para i desde 1 hasta n-1:
            xi = a + i * h
            Si i es impar:
                suma = suma + 4 * f(xi)
            Sino:
                suma = suma + 2 * f(xi)
        resultado = h * suma / 3
        resultado = resultado / h # Para la diferenciación
        Devolver resultado

<h4> <font font face = "arial"> <b> <i> Ejemplo en código </i> </b> </h4>

    package Método_Simpson1_3;
    
    import java.util.function.Function;
   
    public class Ejercicio1 {
        // Método para calcular la integral numérica utilizando el Método de Simpson 1/3
        public static double integrate(double a, double b, int n, Function<Double, Double> func) {
            double h = (b - a) / n;
            double sum = func.apply(a) + func.apply(b);
    
            for (int i = 1; i < n; i += 2) {
                double x = a + i * h;
                sum += 4 * func.apply(x);
            }
    
            for (int i = 2; i < n - 1; i += 2) {
                double x = a + i * h;
                sum += 2 * func.apply(x);
            }
    
            return (h / 3) * sum;
        }
        
        // Método para calcular la derivada numérica utilizando el Método de Simpson 1/3
        public static double differentiate(double x, double h, Function<Double, Double> func) {
            double result = (func.apply(x - 2 * h) - 8 * func.apply(x - h) + 8 * func.apply(x + h) - func.apply(x + 2 * h)) / (12 * h);
            return result;
        }
        
        public static void main(String[] args) {
            // Definir la función que se desea integrar y diferenciar
            Function<Double, Double> func = (x) -> Math.sin(x); // Ejemplo: función seno
            
            // Definir los límites de integración y el número de segmentos
            double a = 0; // Límite inferior
            double b = Math.PI / 2; // Límite superior
            int n = 4; // Número de segmentos (debe ser par para el Método de Simpson 1/3)
            
            // Calcular la integral numérica utilizando el Método de Simpson 1/3
            double integral = integrate(a, b, n, func);
            System.out.println("Resultado de la integración: " + integral);
            
            // Calcular la derivada numérica utilizando el Método de Simpson 1/3
            double x0 = Math.PI / 4; // Punto en el que se desea calcular la derivada
            double h = 0.1; // Tamaño del paso
            double derivative = differentiate(x0, h, func);
            System.out.println("Resultado de la diferenciación en x = " + x0 + ": " + derivative);
        }
    }

<h4> <font font face = "arial"> Programa ejecutado </h4>

![Captura de pantalla 2024-05-30 225428](https://github.com/AntonioGuerrer0/PROBLEMARIO_TEMA-4/assets/161759650/935cc0fe-e3c6-48de-b7f4-4a9934aa63ba)

<h3 align = "center"> <font  font face = "bauhaus 93"> <a name=" Método de Simpson 3/8 ">  Método de Simpson 3/8 </a> </font> </h3>

<h4> <font font face = "arial"> Descripción </h4>

El Método de Simpson 3/8 es una extensión del Método de Simpson 1/3 y también se utiliza para aproximar el valor de una integral definida. Este método es aún más preciso que el Método de Simpson 1/3 y el Método del Trapecio, ya que utiliza polinomios de tercer grado (cúbicos) para aproximar la función integranda en cada subintervalo.
<h4> <font font face = "arial">Pseudocódigo </h4>
  
1. Pseudocódigo para realizar la integración

        Función Simpson_3_8_Integración(f, a, b, n):
            h = (b - a) / n
            suma = f(a) + f(b)
            Para i desde 1 hasta n-1:
                xi = a + i * h
                Si i es divisible por 3:
                    suma = suma + 2 * f(xi)
                Sino Si i no es divisible por 3 pero es impar:
                    suma = suma + 3 * f(xi)
                Sino:
                    suma = suma + 3 * f(xi)
            resultado = 3 * h * suma / 8
            Devolver resultado

2. Pseudocódigo para realizar la diferenciación

       Función Simpson_3_8_Diferenciación(f, a, b, n):
        h = (b - a) / n
        suma = f(a) + f(b)
        Para i desde 1 hasta n-1:
            xi = a + i * h
            Si i es divisible por 3:
                suma = suma + 2 * f(xi)
            Sino Si i no es divisible por 3 pero es impar:
                suma = suma + 3 * f(xi)
            Sino:
                suma = suma + 3 * f(xi)
        resultado = 3 * h * suma / 8
        resultado = resultado / h # Para la diferenciación
        Devolver resultado

<h4> <font font face = "arial"> <b> <i> Ejemplo en código </i> </b> </h4>

     package Método_Simpson3_8;

    import java.util.function.Function;


    public class ejercicio3 {

    public static double integrate(double a, double b, int n, Function<Double, Double> func) {
        double h = (b - a) / n;
        double sum = func.apply(a) + func.apply(b);

        for (int i = 1; i < n; i++) {
            double x = a + i * h;
            sum += i % 3 == 0 ? 2 * func.apply(x) : 3 * func.apply(x);
        }

        return (3 * h / 8) * sum;
    }

    public static double differentiate(double x, double h, Function<Double, Double> func) {
        double result = (-func.apply(x + 2 * h) + 9 * func.apply(x + h) - 9 * func.apply(x - h) + func.apply(x - 2 * h)) / (24 * h);
        return result;
    }

    public static void main(String[] args) {
        Function<Double, Double> func = (x) -> x * x - 3 * x + 2; // Función: x^2 - 3x + 2
        double a = -2; // Límite inferior
        double b = 3; // Límite superior
        int n = 12; // Número de segmentos
        double x0 = 2; // Punto en el que se desea calcular la derivada
        double h = 0.1; // Tamaño del paso

        double arcLength = integrate(a, b, n, func);
        System.out.println("Longitud del arco de la función: " + arcLength);

        double derivative = differentiate(x0, h, func);
        System.out.println("Derivada de la función en x = " + x0 + ": " + derivative);
    }
    }


<h4> <font font face = "arial"> Programa ejecutado </h4>

![Captura de pantalla 2024-05-30 225550](https://github.com/AntonioGuerrer0/PROBLEMARIO_TEMA-4/assets/161759650/1101bb8c-165d-4bef-9ecc-839ed6d4bf4b)

<h3 align = "center"> <font  font face = "bauhaus 93"> <a name=" Método de la Cuadratura Gaussiana ">  Método de la Cuadratura Gaussiana </a> </font> </h3>

<h4> <font font face = "arial"> Descripción </h4>
  
El Método de la Cuadratura Gaussiana es una técnica de integración numérica que utiliza una selección cuidadosa de puntos de evaluación y pesos para proporcionar una alta precisión en la aproximación de integrales definidas. A diferencia de los métodos de interpolación como el Método del Trapecio o el Método de Simpson, la Cuadratura Gaussiana no intenta ajustar polinomios a la función a integrar. En cambio, aprovecha las propiedades de ciertas funciones de peso para elegir de manera óptima los puntos de evaluación.

<h4> <font font face = "arial">Pseudocódigo </h4>
  
1. Pseudocódigo para realizar la integración

        Función Cuadratura_Gaussiana_Integración(f, a, b, n):
            coeficientes, nodos = obtener_coeficientes_y_nodos(n)
            suma = 0
            Para i desde 0 hasta n-1:
                xi = (b - a) / 2 * nodos[i] + (b + a) / 2
                suma = suma + coeficientes[i] * f(xi)
            resultado = (b - a) / 2 * suma
            Devolver resultado

2. Pseudocódigo para realizar la diferenciación

        Función Cuadratura_Gaussiana_Diferenciación(f, a, b, n):
            coeficientes, nodos = obtener_coeficientes_y_nodos(n)
            suma = 0
            Para i desde 0 hasta n-1:
                xi = (b - a) / 2 * nodos[i] + (b + a) / 2
                suma = suma + coeficientes[i] * f(xi)
            resultado = suma
            Devolver resultado

<h4> <font font face = "arial"> <b> <i> Ejemplo en código </i> </b> </h4>

     package Método_Cuadratura_Gaussiana;

    import java.util.function.Function;


    public class ejercicio1 {

    // Coeficientes y nodos de Cuadratura Gaussiana para dos puntos
    private static final double[] nodes = {-0.5773502692, 0.5773502692};
    private static final double[] weights = {1.0, 1.0};

    // Método para calcular la integral numérica utilizando Cuadratura Gaussiana
    public static double integrate(double a, double b, Function<Double, Double> func) {
        double integral = 0.0;
        double transform = (b - a) / 2.0;

        for (int i = 0; i < nodes.length; i++) {
            double x = transform * nodes[i] + (a + b) / 2.0;
            integral += weights[i] * func.apply(x);
        }

        return transform * integral;
    }

    // Método para calcular la derivada numérica utilizando Cuadratura Gaussiana
    public static double differentiate(double x, double h, Function<Double, Double> func) {
        double derivative = 0.0;

        for (int i = 0; i < nodes.length; i++) {
            double xi = x + h * nodes[i];
            derivative += weights[i] * func.apply(xi);
        }

        return derivative / h;
    }

    public static void main(String[] args) {
        Function<Double, Double> func = (x) -> Math.cos(x); // Función: cos(x)
        double a = 0; // Límite inferior
        double b = Math.PI / 2; // Límite superior
        double x0 = Math.PI / 4; // Punto en el que se desea calcular la derivada
        double h = 0.1; // Tamaño del paso

        // Calcular la integral numérica utilizando Cuadratura Gaussiana
        double integralResult = integrate(a, b, func);
        System.out.println("Integral de cos(x) desde 0 a π/2: " + integralResult);

        // Calcular la derivada numérica utilizando Cuadratura Gaussiana
        double derivative = differentiate(x0, h, func);
        System.out.println("Derivada de cos(x) en x = " + x0 + ": " + derivative);
    }
    }


<h4> <font font face = "arial"> Programa ejecutado </h4>


![Captura de pantalla 2024-05-30 225644](https://github.com/AntonioGuerrer0/PROBLEMARIO_TEMA-4/assets/161759650/62981968-cc4d-4ef0-a468-d427d4ac9d6e)

<h2 align = "center"> <font font face = "forte">  <a name="Descripcion"> Descripción </a></h2>
La interpolación en métodos numéricos es una técnica utilizada para estimar valores desconocidos de una función a partir de un conjunto de valores conocidos. Es una herramienta fundamental en el análisis numérico y se emplea en diversas áreas como la ingeniería, la física y la economía, donde es necesario trabajar con datos discretos o aproximar funciones.  

  Existen varios métodos de interpolación, cada uno con sus propias características y aplicaciones. Algunos de los más comunes son:
  <li>1.-Interpolación lineal</li>
  <li>2.-Interpolación cuadratica</li>
  <li>3.-Interpolación langrage</li>
  <li>4.-Interpolación de newton</li>

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<h2 align = "center"> <font font face = "forte">  <a name="Lineal"> 1. Interpolación lineal </a></h2>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

La interpolación lineal es útil cuando buscamos un valor entre puntos dados. Se puede considerar como "llenar los espacios" de una tabla de datos. La estrategia para la interpolación lineal es usar una línea recta para conectar los datos conocidos a ambos lados del punto desconocido.   

<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>

    public static double interpolate(double[] x, double[] y, double xTarget) {
        int n = x.length;
        double yTarget = 0;

        int i = 0;
        while (i < n - 1 && x[i] < xTarget) {
            i++;
        }

        if (i == 0) {
            yTarget = y[0];
        } else if (i == n - 1) {
            yTarget = y[n - 1];
        } else {
            double x0 = x[i - 1];
            double x1 = x[i];
            double y0 = y[i - 1];
            double y1 = y[i];

            double m = (y1 - y0) / (x1 - x0);
            double b = y0 - m * x0;
            yTarget = m * xTarget + b;
        }

        return yTarget;
    }

    public static void main(String[] args) {
        double[] x = {1.0, 2.0, 3.0, 4.0, 5.0};

        double[] y = {2.0, 4.0, 6.0, 8.0, 10.0};

        double xTarget = 2.5;
        double yTarget = interpolate(x, y, xTarget);

        System.out.println("El valor de y para x = " + xTarget + " es " + yTarget);
    }
}

<h2 align = "center"> <font font face = "forte">  <a name="Cuadratica"> 2.- Interpolación cuadratica </a></h2>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

La interpolación cuadrática es un método utilizado en matemáticas y ciencias computacionales para encontrar una función cuadrática que pase a través de un conjunto de puntos dados. En lugar de ajustarse a una línea recta como en la interpolación lineal, la interpolación cuadrática utiliza una función de segundo grado (una parábola) para aproximar los valores entre los puntos conocidos. Este método es útil cuando se necesita una aproximación suave y curva entre los puntos de datos, lo que puede proporcionar una representación más precisa de la relación subyacente entre los puntos interpolados.   

<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>

    public static void main(String[] args) {
        System.out.println("Solucion de ecuaciones cuadráticas");
        double a = 1, b = -3, c = 2, x1, x2, producto, cuadrado, diferencia, raiz;

        cuadrado = Math.pow(b, 2);
        producto = 4 * a * c;
        diferencia = cuadrado - producto;
        raiz = Math.sqrt(diferencia);

        x1 = (-b + raiz) / (2 * a);
        x2 = (-b - raiz) / (2 * a);

        System.out.println("La ecuacion es: " + a + "x^2 + " + b + "x + " + c + " = 0");
        System.out.println("Las raices son:");
        System.out.println("El valor de x1 es: " + x1);
        System.out.println("El valor de x2 es: " + x2);
    }
}


<h2 align = "center"> <font font face = "forte"> <a name="Langrage">  3.- Interpolación langrage </a></h2>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

La interpolación de Lagrange es un método matemático para encontrar un polinomio que pasa a través de un conjunto de puntos dados. A diferencia de la interpolación cuadrática, que utiliza un polinomio de grado 2, la interpolación de Lagrange puede generar polinomios de cualquier grado para ajustarse a los puntos.   

<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>


    public static double interpolate(double[] x, double[] y, double xTarget) {
        double result = 0;

        for (int i = 0; i < x.length; i++) {
            double term = y[i];
            for (int j = 0; j < x.length; j++) {
                if (j != i) {
                    term = term * (xTarget - x[j]) / (x[i] - x[j]);
                }
            }
            result += term;
        }

        return result;
    }

    public static void main(String[] args) {
        double[] x = {0.5, 1.5, 2.5, 3.5, 4.5};
        double[] y = {2.5, 4.5, 6.5, 8.5, 10.5};
        double xTarget = 3.0;

        double yTarget = interpolate(x, y, xTarget);

        System.out.println("El valor interpolado de y para x = " + xTarget + " es " + yTarget);
    }
}



<h2 align = "center"> <font font face = "forte"> <a name="Newton">  4.Interpolación de newton </a></h2>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

La interpolación de Newton es un método utilizado en matemáticas y análisis numérico para encontrar un polinomio que pase a través de un conjunto de puntos dados. Este método fue desarrollado por Isaac Newton y es una alternativa a la interpolación de Lagrange.   

<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>
  <h2 align = "center"> <font font face = "forte">  <a name="Descricpcion"> Descripción </a></h2>
Los métodos de Euler, Taylor y Runge-Kutta son herramientas numéricas para resolver ecuaciones diferenciales. El método de Euler es simple pero puede ser inestable, el método de Taylor es preciso pero no se utiliza comúnmente, y el método de Runge-Kutta es preciso y estable, siendo especialmente popular el método de Runge-Kutta de orden 4.
  
Existen varios métodos para resolver ecuaciones diferenciales, cada uno con sus propias características y aplicaciones. Algunos de los más comunes son:
  <li>1.-Euler</li>
  <li>2.-Runge-Kutta</li>
  <li>3.-Taylor</li>

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<h2 align = "center"> <font font face = "forte">  <a name="Lineal"> 1. Euler </a></h2>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

El método de Euler es un procedimiento numérico utilizado para aproximar soluciones de ecuaciones diferenciales ordinarias mediante la creación de una secuencia de puntos, calculados con un paso fijo, que siguen la pendiente de la función en cada punto.<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>



    
    public static void main(String[] args) {
        // Ecuación diferencial: dy/dx = (x + y + xy)
        // Condiciones iniciales: y(0) = 0.5
        double x0 = 0, y0 = 0.5, x, y, h = 0.1, xEnd = 0.3;
        int n = (int)((xEnd - x0) / h);
        
        x = x0;
        y = y0;
        
        System.out.println("x\ty");
        System.out.println(x + "\t" + y);
        
        for (int i = 0; i < n; i++) {
            y = y + h * dydx(x, y);
            x = x + h;
            System.out.println(x + "\t" + y);
        }
    }
    
    public static double dydx(double x, double y) {
        return x + y + x * y;
    }

![Captura de pantalla 2024-05-29 122105](https://github.com/AntonioGuerrer0/T6----E2----Problemario/assets/161759650/3f70e622-1d9b-45c2-bf8b-35bb29f10d23)


<h2 align = "center"> <font font face = "forte">  <a name="Cuadratica"> 2.- Runge-Kutta </a></h2>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

El método de Runge-Kutta es una familia de métodos numéricos para resolver ecuaciones diferenciales ordinarias (EDOs). Los métodos de Runge-Kutta son más precisos que el método de Euler. El más común es el método de Runge-Kutta de cuarto orden (RK4), que proporciona una buena combinación de precisión y eficiencia.   
<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>

   
    
    public static void main(String[] args) {
        // Ecuación diferencial: dy/dx = x^2 - y
        // Condiciones iniciales: y(0) = 2
        double x0 = 0, y0 = 2, x, y, h = 0.05, xEnd = 0.2;
        int n = (int)((xEnd - x0) / h);
        
        x = x0;
        y = y0;
        
        System.out.println("x\ty");
        System.out.println(x + "\t" + y);
        
        for (int i = 0; i < n; i++) {
            double k1 = h * dydx(x, y);
            double k2 = h * dydx(x + 0.5 * h, y + 0.5 * k1);
            double k3 = h * dydx(x + 0.5 * h, y + 0.5 * k2);
            double k4 = h * dydx(x + h, y + k3);
            
            y = y + (k1 + 2*k2 + 2*k3 + k4) / 6;
            x = x + h;
            System.out.println(x + "\t" + y);
        }
    }
    
    public static double dydx(double x, double y) {
        return x * x - y;
    }

![Captura de pantalla 2024-05-29 122118](https://github.com/AntonioGuerrer0/T6----E2----Problemario/assets/161759650/5e6a0f6a-5182-4169-9e91-ba4727b27203)

 

<h2 align = "center"> <font font face = "forte"> <a name="Langrage">  3.- Taylor </a></h2>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

El método de Taylor es un procedimiento numérico para resolver ecuaciones diferenciales ordinarias (EDOs) que utiliza la expansión en serie de Taylor para aproximar la solución. Este método se basa en la idea de que una función puede ser aproximada por una suma de sus derivadas evaluadas en un punto.   
<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>

     package Taylor;

      public class Ejercicio_4 {
   
    public static void main(String[] args) {
        // Ecuación diferencial: dy/dx = y - x^2
        // Condiciones iniciales: y(0) = 3
        double x0 = 0, y0 = 3, x, y, h = 0.02, xEnd = 0.08;
        int n = (int)((xEnd - x0) / h);
        
        x = x0;
        y = y0;
        
        System.out.println("x\ty");
        System.out.println(x + "\t" + y);
        
        for (int i = 0; i < n; i++) {
            double k1 = h * dydx(x, y);
            double k2 = h * (dydx(x + h, y + k1));
            
            y = y + (k1 + k2) / 2;
            x = x + h;
            System.out.println(x + "\t" + y);
        }
    }
    
    public static double dydx(double x, double y) {
        return y - x * x;
    }

![Captura de pantalla 2024-05-29 122131](https://github.com/AntonioGuerrer0/T6----E2----Problemario/assets/161759650/ec6adfeb-834d-4b38-95d3-2826585b6fc5)

    public static double interpolate(double[] x, double[] y, double xTarget) {
        double yTarget = y[0];
        for (int i = 0; i < x.length - 1; i++) {
            if (x[i] <= xTarget && x[i + 1] > xTarget) {
                double h = x[i + 1] - x[i];
                double k = (xTarget - x[i]) / h;
                double y0 = y[i];
                double y1 = y[i + 1];
                yTarget = y0 + k * (y1 - y0);
                break;
            }
        }
        return yTarget;
    }

    public static void main(String[] args) {
        double[] x = {10.0, 20.0, 30.0, 40.0, 50.0};
        double[] y = {15.0, 25.0, 35.0, 45.0, 55.0};

        double xTarget = 25.0;

        double yTarget = interpolate(x, y, xTarget);

        System.out.println("El valor interpolado de y para x = " + xTarget + " es " + yTarget);
    }
}
