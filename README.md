# Actividad6.1
## Daniel Vargas


## Ejercicio 1
Recibir un número entero por teclado y decir si es positivo.
```sh
#!/bin/bash

read  -p "Introduce un número: " num

if (( num > 0 )); then
    echo "$num es positivo"
else
    echo "$num no es positivo"
fi
```

## Ejercicio 2
Recibir un número entero por teclado y decir si es negativo.
```sh

#!/bin/bash

read -p "Introduce un número: " num

if (( num > 0 )); then
    echo "$num es positivo"
elif (( num == 0 )); then
    echo "$num es cero"
else
    echo "$num es negativo"
fi
```

## Ejercicio 3
Recibir un número entero por teclado y decir si es igual a cero.
```sh
#!/bin/bash

read -p "Introduce un número: " num

if (( num == 0 )); then
    echo "$num es igual a cero"
else
    echo "$num no es igual a cero"
fi
```

## Ejercicio 4
Recibir un numero entero por teclado y decir si es positivo, negativo o cero.
```sh
#!/bin/bash

read -p "Introduce un número: " num

if (( num > 0 )); then
    echo "$num es positivo"
elif (( num < 0 )); then
    echo "$num es negativo"
else
    echo "$num es cero"
fi
```

## Ejercicio 5
Comprobar si el número de parámetros introducido es igual a 3, en el caso de que sea otro número mostrará un mensaje de error por pantalla.
```sh
#!/bin/bash

if (( $# == 3 )); then
    echo "El número de parámetros introducidos es 3"
else
    echo "Error, número de parámetros distinto de 3"
fi
```

## Ejercicio 6
Recibir dos números por parámetros y lo suma. En caso de que el número de parámetros sea incorrecto mostrará un mensaje de error.
```sh

#!/bin/bash

if (( $# == 2 )); then
    result=$(( $1 + $2 ))
    echo "El resultado de $1 + $2 es $result"
else
    echo "Error: el número de parámetros introducidos es distinto de 2"
fi
```

## Ejercicio 7
Recibir 3 parámetros. En el caso de que reciba un número diferente mostrará un mensaje de error. Los dos primeros serán dos números y el tercero será uno de los siguientes símbolos “+” “-“ “x” “/”, dependiendo del tercer parámetro introducido realizara la correspondiente operación. El en caso de que se introduzca un símbolo diferente, presentará un mensaje indicando cuales son las opciones correctas
```sh

#!/bin/bash

if (( $# == 3 )); then
    case "$3" in
        "+")
            echo "$1 + $2 = $(( $1 + $2 ))"
            ;;
        "-")
            echo "$1 - $2 = $(( $1 - $2 ))"
            ;;
        "*")
            echo "$1 x $2 = $(( $1 * $2 ))"
            ;;
        "/")
            echo "$1 / $2 = $(( $1 / $2 ))"
            ;;
        *)
            echo "Error: La operación introducida es incorrecta"
            ;;
    esac
else
    echo "Error: El número de parámetros es distinto de 3"
fi
```

## Ejercicio 8
Recibir la ruta de un fichero e indicar si existe.
```sh
#!/bin/bash

if [ -f "$1" ]; then
    echo "El fichero existe"
else
    echo "El fichero no existe"
fi
```

## Ejercicio 9
Recibir la ruta de un fichero e indicar si es un directorio o un fichero.
```sh
#!/bin/bash

if [ -f "$1" ]; then
    echo "Es un fichero"
elif [ -d "$1" ]; then
    echo "Es un directorio"
fi
```

## Ejercicio 10
Recibir la ruta de un fichero e indicar los permisos que tiene (escritura, lectura, ejecución)
```sh
#!/bin/bash

ls -l $1 | cut -d " " -f 1,10
```

## Ejercicio 11
Imprimir por pantalla 50 veces la palabra hola.
```sh
#!/bin/bash

for i in {1..50}
do
    echo Hola
done
```

## Ejercicio 12
Leer una palabra por teclado y mostrarla por consola. Debe realizar esta operación 10 veces.
```sh
#!/bin/bash

read -p "Introduce una palabra: " palabra

for (( i=1; i<=10; i++ ))
do
    echo "$palabra"
done
```

## Ejercicio 13
Recibir un número por parámetro. El programa imprimirá la palabra “hola” el número de veces indicado por parámetro.
```sh
#!/bin/bash

for ((i=0; i<$1; i++))
do
    echo "hola"
done
```

## Ejercicio 14
Se debe pasar un número n por parámetro. El programa imprimirá los números del 0 al n por pantalla.
```sh
#!/bin/bash

for (( i=1; i<=$1; i++ ))
do 
    echo $i
done
```

## Ejercicio 15
Recibir un número n por parámetro. El programa tendrá que sumar todos los números entre 1 y n. Posteriormente mostrará el resultado de la suma por pantalla
```sh
for (( i=0; i<=$1; i++ ))
do 
    result=$(($result+$i))
done

echo "La suma de los números enteros desde 0 hasta $1 es: $result"
```

## Ejercicio 16
Recibir dos números por parámetro. El programa deberá hacer que el primer parámetro tome el valor del segundo parámetro y el segundo parámetro tome el valor del primero. Por ejemplo si se introduce el 2 y el 9, en un principio $1 es 1 y $2 es 9. Tras la ejecución del programa $1 valdrá 9 y $2 1.
```sh
#!/bin/bash

num1=$1
num2=$2

echo "El valor de num1 es $num1, el valor de num2 es $num2"

num1=$((num1+num2))
num2=$((num1-num2))
num1=$((num1-num2))

echo "El valor de num1 es $num1, el valor de num2 es $num2"
```

## Ejercicio 17
Programa que lea palabras hasta que se escriba “:q”
```sh
#!/bin/bash

palabra=""

while [[ "$palabra" != ":q" ]]
do
read -p "Introduzca una palabra: " palabra
done
```
## Ejercicio 18
Programa que lea palabras y las guarde en un fichero, hasta que se escriba “:q”

## Ejercicio 19
Programa que lea palabras y las guarde en un fichero de forma ordenada, hasta que se escriba “:q”

## Ejercicio 20
Realiza un programa que solicite un número y compruebe si se encuentre en un archivo llamado números.txt
```sh
#!/bin/bash

archivo="numeros.txt"

read -p "Introduce un número: " num

if  grep -qw "$num" "$archivo"; then
    echo "El número $num se encuentra en el $archivo"
else
    echo "El número $num no se encuentra en el $archivo"
fi
```
