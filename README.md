## Sistemas informáticos - Actividad 6.1

## 1. Recibir un número entero por teclado y decir si es positivo
```bash
#!/bin/bash

echo "Introduce un número entero:"
read num

if [ $num -gt 0 ]
then
 	echo "El número es positivo"
fi

```
## 2. Recibir un número entero por teclado y decir si es negativo
```bash
#!/bin/bash

echo "Introduce un número entero:"
read num

if [ $num -lt 0 ]
then 
	echo "El número es negativo"
fi
```
## 3. Recibir un número entero por teclado y decir si es igual a 0
```bash
#!/bin/bash

echo "Introduce un número entero:"
read num

if [ $num -eq 0 ]
then
  echo "El número es igual a 0"
fi
```
## 4. Recibir un número entero por teclado y decir si es positivo, negativo o cero.
```bash
#!/bin/bash

echo "Introduce un número entero:"
read num

if [ $num -gt 0 ]
then
  echo "El número es positivo"
elif [ $num -lt 0 ]
then
  echo "El número es negativo"
else
  echo "El número es igual a 0"
fi
```
## 5. Comprobar si el número de parámetros introducido es igual a 3, en el caso de que sea incorrecto mostrará un mensaje de error
```bash
#!/bin/bash

if [ $# -ne 3 ]
then
  echo "Error: El número de parámetros introducido es incorrecto. Debe introducir 3 parámetros."
else
  echo "¡El número de parámetros es correcto!"
fi
```
## 6. Recibir dos números por parámetros y lo suma. En caso de que el número de parámetros sea incorrecto mostrará un mensaje de error
```bash
#!/bin/bash

if [ $# -ne 2 ]
then
  echo "Error: El número de parámetros introducido es incorrecto. Debe introducir 2 parámetros."
else
  sum=$(($1 + $2))
  echo "La suma de $1 y $2 es: $sum"
fi
```
## 7. Recibir 3 parámetros. En el caso de que reciba un número diferente mostrará un mensaje de error. Los dos primeros serán números y el tercero será uno de los siguientes símbolos "+" "-" "X" "/", dependiendo del tercer parámetro introducido realizará la correspondiente operación. En el caso de que se introduzca un símbolo diferente, presentará un mensaje indicando cuales son las opciones correctas.
```bash
#!/bin/bash

# Comprobamos si se han recibido tres parámetros
if [ $# -ne 3 ]; then
    echo "Error: Debe introducir tres parámetros."
    exit 1
fi

# Comprobamos si los dos primeros parámetros son números
re='^[0-9]+$'
if ! [[ $1 =~ $re ]] || ! [[ $2 =~ $re ]]; then
    echo "Error: Los dos primeros parámetros deben ser números enteros."
    exit 1
fi

# Comprobamos si el tercer parámetro es válido
if [[ $3 != "+" && $3 != "-" && $3 != "x" && $3 != "/" ]]; then
    echo "Error: El tercer parámetro debe ser +, -, x o /."
    exit 1
fi

# Realizamos la operación correspondiente
if [[ $3 == "+" ]]; then
    resultado=$(($1 + $2))
elif [[ $3 == "-" ]]; then
    resultado=$(($1 - $2))
elif [[ $3 == "x" ]]; then
    resultado=$(($1 * $2))
else
    resultado=$(($1 / $2))
fi

echo "El resultado de la operación es: $resultado"
```
##  8. Recibir la ruta de un fichero e indicar si existe
```bash
#!/bin/bash

# Verificar si se recibió un parámetro
if [ $# -ne 1 ]; then
  echo "Debe ingresar la ruta del fichero como parámetro"
  exit 1
fi

# Verificar si el fichero existe
if [ -f $1 ]; then
  echo "El fichero $1 existe"
else
  echo "El fichero $1 no existe"
fi
```
## 9. Recibir la ruta de un fichero e indiciar si es un directorio o un fichero.
```bash
#!/bin/bash

if [ "$#" -ne 1 ]; then
  echo "Error: debe ingresar una única ruta como argumento"
  exit 1
fi

if [ -d "$1" ]; then
  echo "$1 es un directorio"
elif [ -f "$1" ]; then
  echo "$1 es un archivo"
else
  echo "La ruta $1 no existe"
fi
```
## 10. Recibir la ruta de un fichero e indicar los permisos que tiene (escritura, lectura, ejecución)
```bash
#!/bin/bash

# Pedir ruta del archivo o directorio
read -p "Introduce la ruta del archivo o directorio: " ruta

# Comprobar si existe el archivo/directorio
if [ -e "$ruta" ]; then
  # Mostrar permisos
  permisos=$(ls -l "$ruta" | cut -d ' ' -f 1)
  echo "Los permisos de $ruta son: $permisos"
else
  echo "El archivo o directorio no existe"
fi
```
## 11. Imprimir por pantalla 50 veces la palabra "hola"
```bash
#!/bin/bash

for (( i=1; i<=50; i++ ))
do
    echo "hola"
done
```
## 12. Leer una palabra por teclado y mostrarla por consola. Debe realizar esta operación 10 veces.
```bash
#!/bin/bash

read -p "Introduce una palabra: " palabra

for ((int i=1; i<=10; i++))
do
	echo $palabra
done
```
## 13. Recibir un número por parámetro. El programa imprimirá los números del 0 al n por pantalla.
```bash
#!/bin/bash

if [ $# -ne 1 ]; then
  echo "Error: Debe introducir un número como parámetro."
  exit 1
fi

n=$1

if ! [[ $n =~ ^[0-9]+$ ]]; then
  echo "Error: El parámetro introducido no es un número."
  exit 1
fi

for (( i=0; i<=$n; i++ ))
do
  echo $i
done
```
## 14. Se debe pasar un número n por parámetro. El programa imprimirá los números del 0 al n por pantalla.
```bash
#!/bin/bash

if [ $# -ne 1 ]; then
  echo "Error: Debe pasar un solo número como parámetro"
  exit 1
fi

n=$1

for ((i=0;i<=n;i++)); do
  echo $i
done
```
## 15. Recibir un número n por parámetro. El programa tendrá que sumar todos los números entre 1 y n. Posteriormente mostrará el resultado de la suma por pantalla.
```bash
#!/bin/bash

# Verificar que se haya ingresado un número como parámetro
if [ $# -ne 1 ]; then
  echo "Error: se debe ingresar un número como parámetro"
  exit 1
fi

# Asignar el primer parámetro a una variable
n=$1

# Inicializar la variable de suma
suma=0

# Iterar desde 1 hasta n, acumulando la suma
for (( i=1; i<=n; i++ )); do
  suma=$((suma+i))
done

# Imprimir el resultado de la suma
echo "La suma de los números del 1 al $n es: $suma"
```
## 16. Recibir dos números por parámetro. El programa deberá hacer que el primer parámetro tome el valor del segundo parámetro y el segundo parámetro tome el valor del primero. Por ejemplo, si se introduce el 2 y el 0, en un principio$1 es 1 y $2 es 9. Tras la ejecución del programa $1 valdrá 9 y $2 1.
```bash
#!/bin/bash

# Comprobar si el número de parámetros es correcto
if [ $# -ne 2 ]; then
  echo "Error: Se deben pasar dos números por parámetro."
  exit 1
fi

# Intercambiar los valores de las variables
aux=$1
1=$2
2=$aux

echo "El primer parámetro es ahora $1 y el segundo parámetro es ahora $2."
```
## 17. Programa que lea palabras hasta que escriba ":q"
```bash
#!/bin/bash

echo "Escribe palabras (para salir escribe ':q')"

while true; do
    read word
    if [ "$word" = ":q" ]; then
        break
    fi
    echo "Palabra: $word"
done
```
## 18. Programa que lea palrabras y las guarde en un fichero de forma ordenada hasta que se escriba ":q"
```bash
#!/bin/bash

# Declarar el array
declare -a palabras

# Inicializar el índice
i=0

# Leer palabras hasta que se escriba ":q"
while true
do
    read palabra
    if [ "$palabra" == ":q" ]
    then
        break
    fi
    palabras[i]=$palabra
    ((i++))
done

# Ordenar el array
sorted=($(for word in "${palabras[@]}"; do echo "$word"; done | sort))

# Guardar el array en un archivo
printf "%s\n" "${sorted[@]}" > palabras.txt

echo "Las palabras han sido guardadas en palabras.txt"
```
## 19. Programa que lea palabras y las guarde en un fichero de forma ordenada, hasta que se escriba ":q"
```bash
#!/bin/bash

filename="palabras.txt"

echo "Escribe tus palabras (para salir escribe :q)"
read palabra

while [ "$palabra" != ":q" ]
do
  echo $palabra >> $filename
  read palabra
done

echo "¡Hasta pronto!"
```
## 20. Realiza un programa que solicite un número y compruebe si se encuentra en un archivo llamado número.txt.
```bash
#!/bin/bash

# Pedimos al usuario que introduzca un número
numero = input("Introduce un número: ")

# Abrimos el archivo en modo lectura
with open('numero.txt', 'r') as archivo:
    # Leemos todas las líneas del archivo y las almacenamos en una lista
    numeros = archivo.readlines()
    # Comprobamos si el número introducido se encuentra en la lista
    if numero+'\n' in numeros:
        print("El número {} se encuentra en el archivo".format(numero))
    else:
        print("El número {} no se encuentra en el archivo".format(numero))

```
