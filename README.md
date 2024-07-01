import random

def elegir_palabra():
    # Lista de palabras para elegir
    palabras = ['python', 'programacion', 'computadora', 'java', 'codigo']
    return random.choice(palabras)

def mostrar_palabra(palabra, letras_adivinadas):
    # Mostrar las letras adivinadas y reemplazar las no adivinadas con '_'
    resultado = ''
    for letra in palabra:
        if letra in letras_adivinadas:
            resultado += letra
        else:
            resultado += '_'
    return resultado

def es_palabra_adivinada(palabra, letras_adivinadas):
    # Verificar si todas las letras de la palabra han sido adivinadas
    for letra in palabra:
        if letra not in letras_adivinadas:
            return False
    return True

def ahorcado():
    # Inicializar variables
    palabra = elegir_palabra()
    palabra = elegir_palabra()
    letras_adivinadas = []
    intentos = 6

    print("¡Bienvenido al juego del ahorcado!")
    
    while intentos > 0:
        print("\nPalabra a adivinar: ", mostrar_palabra(palabra, letras_adivinadas))
        print("Intentos restantes:", intentos)
        
        intento = input("Adivina una letra: ").lower()

        # Verificar si la letra ya ha sido adivinada
        if intento in letras_adivinadas:
            print("Ya has intentado esa letra. ¡Intenta con otra!")
            continue

        # Verificar si la letra está en la palabra
        if intento in palabra:
            print("¡Adivinaste una letra!")
            letras_adivinadas.append(intento)
            
            # Verificar si se ha adivinado toda la palabra
            if es_palabra_adivinada(palabra, letras_adivinadas):
                print("\n¡Felicidades! ¡Has adivinado la palabra correctamente!")
                print("La palabra era:", palabra)
                break
        else:
            print("¡Incorrecto! Esa letra no está en la palabra.")
            letras_adivinadas.append(intento)
            intentos -= 1
        
    if intentos == 0:
        print("\n¡Oh no! Te has quedado sin intentos.")
        print("La palabra era:", palabra)

# Llamar a la función principal para iniciar el juego
ahorcado()
