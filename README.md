# EJERCICIO

Implementar utilizando el diseño top-down un calendario juliano sabiendo que: el día juliano correspondiente a una fecha es un número entero que indica los días que han transcurrido desde el 1 de enero del año indicado. Debemos crear un programa principal que al introducir una fecha nos diga el día juliano que corresponde. Para ello podemos hacer las siguientes subrutinas (procedimientos o funciones):

* LeerFecha: Nos permite leer por teclado una fecha (día, mes y año).
* DiasDelMes: Recibe un mes y un año y nos dice los días de ese mes en ese año.
* EsBisiesto: Recibe un año y nos dice si es bisiesto.
* Calcular_Dia_Juliano: recibe una fecha y nos devuelve el día juliano.

1. Debemos descomponer el problema en tareas más pequeñas. 
2. Debemos crear un programa principal que al introducir una fecha nos diga el día juliano que corresponde.

Este podría ser:

    Algoritmo DiaJuliano
      Definir d,m,a como Entero
      LeerFecha(d,m,a)
      Escribir "Día Juliano: ",Calcular_Dia_Juliano(d,m,a)
    FinAlgoritmo
    
3. Ahora deberíamos abordar el LeerFecha: este debería ser un Procedimiento que lee por teclado el día, mes y el año y lo devuelve como parámetro de entrada y salida: día, mes y año. Aquí mucho ojo con el paso por valor y paso por referencia.

        Funcion LeerFecha(day Por Referencia,month Por Referencia, year Por Referencia)
          Escribir Sin Saltar "Día:"
          Leer day;
          Escribir Sin Saltar "Mes:"
          Leer month;
          Escribir Sin Saltar "Año:"
          Leer year
        FinFuncion
 
4. Seguidamente implementamos la función Calcular_Dia_Juliano: Recibe un día, mes y año y devuelve el día juliano correspondiente a esa fecha. El día juliano correspondiente a una fecha es un  número entero que indica los días que han transcurrido desde el 1 de enero del año indicado. Depende de la función DiasDelMes (con parámetros de entrada: día, mes y año). La función Calcular_Dia_Juliano debe devolver el día juliano.


        Funcion diaj <- Calcular_Dia_Juliano(day,month,year)
          Definir mes como Entero
          definir diaj como Entero
          diaj<-0
          Para mes<-1 hasta month-1 Hacer
            diaj<-diaj + DiasDelMes(mes,year)
          FinPara
          diaj <- diaj + day
        FinFuncion
        
5. Seguidamente debemos abordar la función DiasDelMes que ecibe un mes y un año y devuelve el número de días que tiene ese mes en ese año. Necesita la función EsBisiesto. Parámetros de entrada: mes y año y devuelve los días del mes en ese año.

        Funcion dias <- DiasDelMes(month,year)
            Definir dias Como Entero;
            Segun month Hacer
                1,3,5,7,8,10,12:
                    dias<-31
                4,6,9,11:
                    dias<-30
                2: //El mes de febrero depende de si el año es bisiesto
                    Si EsBisiesto(year) Entonces
                        dias<-29
                    SiNo
                        dias<-28
                    FinSi
            FinSegun
        FinFuncion
        
6. Finalmente atacamos a la función EsBisiesto que recibe un año y devuelve si es o no bisiesto. Parámetros de entrada: año y debe devolver alor lógico (booleano) indicando si es bisiesto (Verdadero) o no (Falso).

        Funcion bisiesto <- EsBisiesto(year)
            Definir bisiesto como Logico
            Si (year % 4 = 0 Y NO (year % 100 = 0)) O year % 400 = 0 Entonces
                bisiesto <- Verdadero
            SiNo
                bisiesto <- Falso
            FinSi
        FinFuncion
