# Proyecto Módulo 1 - Visor de Memoria
**Materia:** Lenguajes de Interfaz (SCC-1014)  
**Fecha de entrega:** Jueves 10 de septiembre de 2026 (Semana 3)

## 1. Descripción del Proyecto
Este programa está desarrollado en ensamblador **x86-64** utilizando el compilador **UASM** y el enlazador de Microsoft (`link.exe`). Su propósito es recorrer un arreglo de 10 elementos de 64 bits (`DQ`) alojados en la sección `.data`, obteniendo de forma dinámica sus direcciones de memoria física y sus valores almacenados. 

Toda la información se despliega en la consola en formato hexadecimal de 16 dígitos (rellenado con ceros a la izquierda y en letras mayúsculas), cumpliendo con un diseño sin macros y respetando la terminación limpia mediante `ret` sin dependencias externas complejas.

## 2. Requisitos Técnicos Cumplidos
* **R1 (Arreglo):** Arreglo de 10 elementos `DQ` inicializado en la sección `.data`.
* **R2 & R3 (Recorrido y Direccionamiento):** Uso del registro puntero `RBX` incrementando de 8 en 8 bytes y un contador de iteraciones en `R12`.
* **R4 & RT3 (Salida en Consola y Formato):** Despliegue con 16 dígitos fijos en mayúsculas mediante la cadena de formato `%016llX`.
* **RT1 & R5 (Terminación):** Finalización del proceso mediante `ret` devolviendo el control al sistema operativo.
* **RT4 (Convención de Llamada):** Respeto al *Shadow Space* (32 bytes) en la pila para la arquitectura de Windows x64.

## 3. Instrucciones de Compilación y Enlace

Para compilar y enlazar el proyecto desde el **Developer Command Prompt de Visual Studio**, ejecute los siguientes comandos:

```bash
# 1. Ensamblar el código fuente con UASM generando el archivo objeto (.obj)
uasm64 -win64 visor.asm

# 2. Enlazar el objeto con la librería nativa msvcrt para la salida en consola
link /SUBSYSTEM:CONSOLE /ENTRY:main visor.obj msvcrt.lib
```

## 4. Capturas de Pantalla (Evidencia de Ejecución)

### Consola de Comandos (Compilación y Resultado)
![Compilación y Ejecución](ruta_a_tu_captura_de_consola.png)

### Depuración en x64dbg (Opcional / Recomendado)
![Depuración en x64dbg](ruta_a_tu_captura_de_x64dbg.png)

