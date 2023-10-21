# Depto de Sistemas y Computación
# Ing. En Sistemas Computacionales
# SISTEMAS PROGRAMABLES 23a


# OBJETIVO:
Realizar un menu con 3 push Buttons mostrandose en una Oled Display

# CÓDIGO
```python
## Depto de Sistemas y Computación
## Ing. En Sistemas Computacionales
## SISTEMAS PROGRAMABLES 23a
## Autor (es): Jesus Antonio Sanchez Santos
## Repositorio: https://github.com/antsz25/2.3MenuPushButtons
## Fecha de revisión:   20/10/2023
## Objetivo: Realizar un menu con 3 push Buttons mostrandose en una Oled Display

#Importar librerias
from machine import Pin,I2C
import utime
from ssd1306 import SSD1306_I2C
#Definicion de Pines
button1 = Pin(15,Pin.IN,Pin.PULL_DOWN) #Este pin tiene una configuracion distinta en el resistor, debido a que es un boton normalmente cerrado
button2 = Pin(14,Pin.IN,Pin.PULL_UP) #Definicion de pin para boton normalmente abierto
button3 = Pin(13,Pin.IN,Pin.PULL_UP) #Definicion de pin para boton normalmente abierto
#Configuracion de pines para el display OLED
i2c = I2C(0,scl=Pin(17),sda=Pin(16))
display = SSD1306_I2C(128,64,i2c)
#Ciclo infinito del circuito
while True:
    #Obtencion de valores de estado de los botones
    state1 = button1.value()
    state2 = button2.value()
    state3 = button3.value()
    #El boton al presionarse, su valor cambia de 0 a 1 (Falso para 0, Verdadero para 1)
    if state1 == True:
        display.fill(0)
        display.text("Opcion A", 0, 32)
        display.show()
    elif state2 == True:
        display.fill(0)
        display.text("Opcion B", 0, 32)
        display.show()
    elif state3 == True:
        display.fill(0)
        display.text("Opcion C", 0, 32)
        display.show()
    else: #Valor por defecto, menu principal cuando no se presiona ningun boton
        display.fill(0)
        display.text("Menu de opciones",0,5)
        display.text("Azul: A",0,15)
        display.text("Blanco: B",0,25)
        display.text("Rojo: C",0,35)
        display.show()
    utime.sleep(0.3)
```

# PRUEBAS
<a href="https://youtube.com/shorts/Rp1m2zCZxtc?feature=share" target="_blank"><img src="https://github.com/antsz25/2.3MenuPushButtons/blob/main/Portada.jpg" alt="Ejemplo de Imagen" width="300" height="200"></a>


# CONCLUSIONES
Los pushbottons manejan dos tipos: NC y NO. En primera instancia, hay que saber cual es el que esta siendo utilizado, para poder realizar el código posteriormente. De otro modo, puede generar muchos problemas al momento de comprender su funcionamiento.
