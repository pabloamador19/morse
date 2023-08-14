from machine import Pin
import time
import esp32

# Sección de definiciones  --------> VARIABLES/CONSTANTES

tiempoEntreLetras   = 250
tiempoEntrePalabras = 750
tiempoEntreMensajes = 2000

tiempoPunto         = 250
tiempoRaya          = 750
pinMorse            = 21

mensaje ='EA7RI'
MORSE_CODE_DICT = { 'A':'.-', 
                    'B':'-...',
                    'C':'-.-.', 
                    'D':'-..', 
                    'E':'.',
                    'F':'..-.', 
                    'G':'--.', 
                    'H':'....',
                    'I':'..', 
                    'J':'.---', 
                    'K':'-.-',
                    'L':'.-..', 
                    'M':'--', 
                    'N':'-.',
                    'O':'---', 
                    'P':'.--.', 
                    'Q':'--.-',
                    'R':'.-.', 
                    'S':'...', 
                    'T':'-',
                    'U':'..-', 
                    'V':'...-', 
                    'W':'.--',
                    'X':'-..-', 
                    'Y':'-.--', 
                    'Z':'--..',
                    '1':'.----', 
                    '2':'..---', 
                    '3':'...--',
                    '4':'....-', 
                    '5':'.....', 
                    '6':'-....',
                    '7':'--...', 
                    '8':'---..', 
                    '9':'----.',
                    '0':'-----', 
                    ', ':'--..--', 
                    '.':'.-.-.-',
                    '?':'..--..', 
                    '/':'-..-.', 
                    '-':'-....-',
                    '(':'-.--.', 
                    ')':'-.--.-'}


# Sección de definiciones  --------> FUNCIONES

def parpadeo(veces):
    Pin(2, Pin.OUT).value(0)
    for num in range(veces):
        Pin(2, Pin.OUT).value(1)
        time.sleep_ms(110)
        Pin(2, Pin.OUT).value(0)
        time.sleep_ms(110)

def decrypt(message):
 
    # extra space added at the end to access the
    # last morse code
    message += ' '
 
    decipher = ''
    citext = ''
    for letter in message:
 
        # checks for space
        if (letter != ' '):
 
            # counter to keep track of space
            i = 0
 
            # storing morse code of a single character
            citext += letter
 
        # in case of space
        else:
            # if i = 1 that indicates a new character
            i += 1
 
            # if i = 2 that indicates a new word
            if i == 2 :
 
                 # adding space to separate words
                decipher += ' '
            else:
 
                # accessing the keys using their values (reverse of encryption)
                decipher += list(MORSE_CODE_DICT.keys())[list(MORSE_CODE_DICT.values()).index(citext)]
                citext = ''
 
    return decipher


def add(number1, number2):
    return number1 + number2

def encrypt(message):
    cipher = ''
    for letter in message:
        if letter != ' ':
 
            # Looks up the dictionary and adds the
            # corresponding morse code
            # along with a space to separate
            # morse codes for different characters
            cipher += MORSE_CODE_DICT[letter] + ' '
        else:
            # 1 space indicates different characters
            # and 2 indicates different words
            cipher += ' '
 
    return cipher





# AQUÍ EMPIEZA EL MAIN
# DEFINIR FUNCIONES PARA

# PUNTO
# RAYA
# ESPACIO ENTRE LETRAS
# ESPACIO ENTRE PALABRAS
# Tiempo entre envios




# time.sleep(1)           # sleep for 1 second
# time.sleep_ms(500)      # sleep for 500 milliseconds
# time.sleep_us(10)       # sleep for 10 microseconds
# start = time.ticks_ms() # get millisecond counter
# delta = time.ticks_diff(time.ticks_ms(), start) # compute time difference



print("Hola Mundo! . Enciendo LED pin2 durante 1 segundo")
Pin(pinMorse, Pin.OUT).value(1)
time.sleep(1) 
Pin(pinMorse, Pin.OUT).value(0)


print(add(1,1))
print(esp32.hall_sensor())     # read the internal hall sensor
print(esp32.raw_temperature()) # read the internal temperature of the MCU, in Fahrenheit
print((esp32.raw_temperature()-32)*(5/9)) # TEMPERATURA UINTERNA DE LA mcu EN GRADOS
esp32.ULP()             # access to the Ultra-Low-Power Co-processor



parpadeo(10)


print(mensaje.upper())
print(encrypt(mensaje.upper()))
Pin(pinMorse, Pin.OUT).value(0)

while True:
    for letter in encrypt(mensaje.upper()):
        print(letter)
        if (letter == ' '):
            Pin(pinMorse, Pin.OUT).value(0)
            time.sleep_ms(tiempoEntrePalabras)
        else:
            Pin(pinMorse, Pin.OUT).value(0)
            time.sleep_ms(tiempoEntreLetras)
            
        if (letter == '.'):
            Pin(pinMorse, Pin.OUT).value(1)
            time.sleep_ms(tiempoPunto)
        else:
            if (letter == '-'):
                Pin(pinMorse, Pin.OUT).value(1)
                time.sleep_ms(tiempoRaya) 






    time.sleep_ms(tiempoEntreMensajes)







