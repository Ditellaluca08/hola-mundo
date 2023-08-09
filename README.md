def mostrar_menu():
    print("Hola, ¿qué quieres jugar?:")
    print("1. Piedra, papel o tijera")
    print("2. Buscaminas")
    print("3. Ahorcado")
    print("4. Tres en línea")
    print("5. Tres en línea contra bot")
    print("6. Adiviná el número")
    print("7. Adiviná el número 2")

while True:
    mostrar_menu()
    opcion = input("Ingresa el número del juego (o '0' para salir): ")

    while opcion not in ['0', '1', '2', "3", "4", "5", "6", "7"]:
        print("Opción no válida. Por favor, elige una opción válida.")
        opcion = input("Ingresa el número del juego (o '0' para salir): ")

    if opcion == "0":
        break

    if opcion == "1":
        import piedra_papel_tijera
        piedra_papel_tijera.jugar_piedra_papel_tijera()
    elif opcion == "2":
        import buscaminas
        buscaminas.jugar_buscaminas()
    elif opcion == "3":
        import ahorcado
        ahorcado.jugar_ahorcado()
    elif opcion == "4":
        import tres_en_linea
        tres_en_linea.jugar_tres_en_linea()
    elif opcion == "5":
        import tres_en_linea_bot
        tres_en_linea_bot.jugar_tres_en_linea_bot()
    elif opcion == "6":
        import adiviná_el_número
        adiviná_el_número.adiviná_el_número()
    elif opcion == "7":
        import adivina_el_numero_2
        adivina_el_numero_2.jugar_adivina_el_numero_2()

    jugar_otro = input("¿Deseas jugar otro juego? Ingresa 's' para sí, o cualquier otra tecla para salir: ")
    if jugar_otro.lower() != "s":
        break

        import random

def jugar_adivina_el_numero_2():
    while True:
        numero_secreto = random.randint(1, 1000)
        intentos = 0

        print("¡Bienvenido al juego de adivinanzas!")
        print("Estoy pensando en un número del 1 al 1000. Adivina, tenes 10 intentos")

        while intentos < 10:
            try:
                intento = int(input("Tira fruta: "))
            except ValueError:
                print("Escribi bien bobi.")
                continue

            intentos += 1

            if intento < numero_secreto:
                print("El número secreto es mayor.")
            elif intento > numero_secreto:
                print("El número secreto es menor.")
            else:
                print(f"Mu bien. Adivinaste el numero {numero_secreto} en {intentos} intentos")
                break
        else:
            print(f"Agotaste tus 10 intentos. El número secreto era {numero_secreto}. ¡ALTO BOT!")

        jugar_nuevamente = input("¿Quieres jugar de nuevo? (s/n): ")
        if jugar_nuevamente.lower() != 's':
            print("nos vemos bro")
            break

if _name_ == "_main_":
    jugar_adivina_el_numero_2()

    import random

def adiviná_el_número():
    print("¡Bienvenido a Adiviná el Número!")
    print("Estoy pensando en un número entre 1 y 100. ¿Puedes adivinar cuál es?")

    número_secreto = random.randint(1, 100)
    intentos = 0

    while True:
        try:
            guess = int(input("Ingresa tu adivinanza: "))
            intentos += 1

            if guess == número_secreto:
                print(f"¡Felicitaciones! Adivinaste el número en {intentos} intentos.")
                break
            elif guess < número_secreto:
                print("Demasiado bajo. Intenta nuevamente.")
            else:
                print("Demasiado alto. Intenta nuevamente.")
        except ValueError:
            print("Ingresa un número válido.")


if _name_ == "_main_":
    adiviná_el_número()

    import random

AHORCADO = ['''
      +---+
      |   |
          |
          |
          |
    =========''', '''
      +---+
      |   |
      O   |
          |
          |
    =========''', '''
      +---+
      |   |
      O   |
      |   |
          |
    =========''', '''
      +---+
      |   |
      O   |
     /|   |
          |
    =========''', '''
      +---+
      |   |
      O   |
     /|\  |
          |
    =========''', '''
      +---+
      |   |
      O   |
     /|\  |
     /    |
    =========''', '''
      +---+
      |   |
      O   |
     /|\  |
     / \  |
    =========''']
palabras = 'valoracion aprender python comida juego web imposible variable curso volador cabeza reproductor mirada escritor billete lapicero celular revista gratuito disco voleibol anillo estrella'.split()

def buscarPalabraAleat(listaPalabras):
    palabraAleatoria = random.randint(0, len(listaPalabras) - 1)
    return listaPalabras[palabraAleatoria]

def displayBoard(AHORCADO, letraIncorrecta, letraCorrecta, palabraSecreta):
    print(AHORCADO[len(letraIncorrecta)])
    print("")
    fin = " "
    print('Letras incorrectas:', fin)
    for letra in letraIncorrecta:
        print(letra, fin)
    print("")
    espacio = '_' * len(palabraSecreta)
    for i in range(len(palabraSecreta)):
        if palabraSecreta[i] in letraCorrecta:
            espacio = espacio[:i] + palabraSecreta[i] + espacio[i + 1:]
    for letra in espacio:
        print(letra, fin)
    print("")


def elijeLetra(algunaLetra):
    while True:
        print('Adivina una letra:')
        letra = input()
        letra = letra.lower()
        if len(letra) != 1:
            print('Introduce una sola letra.')
        elif letra in algunaLetra:
            print('Ya elegiste esta, usá otra')
        elif letra not in 'abcdefghijklmnopqrstuvwxyz':
            print('Sólo se permiten letras.')
        else:
            return letra


def jugar_ahorcado():
    print('Quieres jugar de nuevo? (Si o No)')
    return input().lower().startswith('s')


print('A H O R C A D O')
letraIncorrecta = ""
letraCorrecta = ""
palabraSecreta = buscarPalabraAleat(palabras)
finJuego = False
while True:
    displayBoard(AHORCADO, letraIncorrecta, letraCorrecta, palabraSecreta)
    letra = elijeLetra(letraIncorrecta + letraCorrecta)
    if letra in palabraSecreta:
        letraCorrecta = letraCorrecta + letra
        letrasEncontradas = True
        for i in range(len(palabraSecreta)):
            if palabraSecreta[i] not in letraCorrecta:
                letrasEncontradas = False
                break
        if letrasEncontradas:
            print('bien, la palabra correcta era esa "' + palabraSecreta + '" ganaste')
            finJuego = True
    else:
        letraIncorrecta = letraIncorrecta + letra
        if len(letraIncorrecta) == len(AHORCADO) - 1:
            displayBoard(AHORCADO, letraIncorrecta, letraCorrecta, palabraSecreta)
            print('!\nDespues de ' + str(len(letraIncorrecta)) + ' letras erroneas y ' + str(
                len(letraCorrecta)) + ' letras correctas, la palabra era "' + palabraSecreta + '"')
            finJuego = True
    if finJuego:
        if jugar_ahorcado():
            letraIncorrecta = ""
            letraCorrecta = ""
            finJuego = False
            palabraSecreta = buscarPalabraAleat(palabras)
        else:
            break

            import random

def jugar_piedra_papel_tijera():
    while True:
        a = int(input("Elija 1 de estos 3 elementos: 1 = Piedra, 2 = Papel, 3 = Tijera: "))

        if a < 1 or a > 3:
            print("Valor no existente, elija uno que si exista.")
            continue

        b = random.randint(1, 3)
        print(b)

        if a == 1 and b == 3:
            print("¡Ganaste! Piedra le gana a tijera")
        elif a == 1 and b == 2:
            print("¡Perdiste! Piedra no le gana a papel")
        elif a == 1 and b == 1:
            print("¡Empate!")
        elif a == 2 and b == 1:
            print("¡Ganaste! Papel le gana a piedra")
        elif a == 2 and b == 2:
            print("¡Empate!")
        elif a == 2 and b == 3:
            print("¡Perdiste! Papel no le gana a tijera")
        elif a == 3 and b == 1:
            print("¡Perdiste! Tijera no le gana a piedra")
        elif a == 3 and b == 2:
            print("¡Ganaste! Tijera le gana a papel")
        elif a == 3 and b == 3:
            print("¡Empate!")

        while True:
            opcion = input("¿quiere jugar de nuevo? Ingresa 1 para volver a jugar, o 2 para salir: ")
            if opcion not in ['1', '2']:
                print("valor no existente. Elija uno que si exista.")
            else:
                break

        if opcion == '2':
            break

jugar_piedra_papel_tijera()

def mostrar_tablero(tablero):
    for fila in tablero:
        print(" | ".join(fila))
        print("---------")


def hay_empate(tablero):
    for fila in tablero:
        for casilla in fila:
            if casilla == " ":
                return False
    return True


def jugar_tres_en_linea():
    while True:
        tablero = [[" " for _ in range(3)] for _ in range(3)]
        jugador_actual = "X"
        juego_terminado = False

        while not juego_terminado:
            mostrar_tablero(tablero)
            try:
                fila = int(input("Ingrese el número de fila (0-2): "))
                columna = int(input("Ingrese el número de columna (0-2): "))

                if fila not in [0, 1, 2] or columna not in [0, 1, 2]:
                    print("Valor inválido. Ingrese un número entre 0 y 2.")
                    continue

                if tablero[fila][columna] == " ":
                    tablero[fila][columna] = jugador_actual
                    if (tablero[0][0] == tablero[1][1] == tablero[2][2] == jugador_actual or
                            tablero[0][2] == tablero[1][1] == tablero[2][0] == jugador_actual or
                            tablero[fila][0] == tablero[fila][1] == tablero[fila][2] == jugador_actual or
                            tablero[0][columna] == tablero[1][columna] == tablero[2][columna] == jugador_actual):
                        mostrar_tablero(tablero)
                        print("El jugador", jugador_actual, "ganó")
                        juego_terminado = True
                    elif hay_empate(tablero):
                        mostrar_tablero(tablero)
                        print("¡Empate!")
                        juego_terminado = True
                    else:
                        jugador_actual = "O" if jugador_actual == "X" else "X"
                else:
                    print("Esa casilla ya está siendo usada, introduzca otra")
            except ValueError:
                print("Valor inválido. Ingrese un número entre 0 y 2.")

        opcion = input(
            "¿Quiere jugar de vuelta? Ingrese 1 para volver a jugar, si no lo desea, ingrese otro parámetro: ")
        if opcion != "1":
            print("Gracias por jugar. ¡Chau!")
            break

            import random

def mostrar_tablero(tablero):
    for fila in tablero:
        print(" | ".join(fila))
        print("---------")

def verificar_ganador(tablero, jugador):
    for fila in tablero:
        if fila.count(jugador) == 3:
            return True

    for columna in range(3):
        if tablero[0][columna] == tablero[1][columna] == tablero[2][columna] == jugador:
            return True

    if tablero[0][0] == tablero[1][1] == tablero[2][2] == jugador:
        return True
    if tablero[0][2] == tablero[1][1] == tablero[2][0] == jugador:
        return True

    return False

def entrada_valida(fila, columna):
    return fila in [0, 1, 2] and columna in [0, 1, 2]

def obtener_entrada_usuario():
    while True:
        try:
            fila = int(input("Ingrese el número de fila (0-2): "))
            columna = int(input("Ingrese el número de columna (0-2): "))

            if not entrada_valida(fila, columna):
                print("Valor inválido. Ingrese un número entre 0 y 2.")
                continue

            return fila, columna
        except ValueError:
            print("Valor inválido. Ingrese un número entre 0 y 2.")

def jugar_tres_en_linea_bot():
    while True:
        tablero = [[" " for _ in range(3)] for _ in range(3)]
        jugador_actual = "X"
        juego_terminado = False

        while not juego_terminado:
            mostrar_tablero(tablero)

            if jugador_actual == "X":
                fila, columna = obtener_entrada_usuario()
            else:
                print("Turno del bot:")
                fila = random.randint(0, 2)
                columna = random.randint(0, 2)
                print("El bot eligió la fila", fila, "y la columna", columna)

            if tablero[fila][columna] == " ":
                tablero[fila][columna] = jugador_actual
                if verificar_ganador(tablero, jugador_actual):
                    mostrar_tablero(tablero)
                    if jugador_actual == "X":
                        print("Ganaste")
                    else:
                        print("Cómo te va a ganar un bot? ¡Jaja!")
                    juego_terminado = True
                elif all(all(casilla != " " for casilla in fila) for fila in tablero):
                    mostrar_tablero(tablero)
                    print("Empataste con un bot, ¡jaja!")
                    juego_terminado = True
                else:
                    jugador_actual = "O" if jugador_actual == "X" else "X"
            else:
                print("Esa casilla ya está ocupada. Intenta de nuevo.")

        opcion = input("¿Deseas jugar de nuevo? Ingresa 1 para volver a jugar o 2 para salir: ")
        if opcion == "2":
            print("Gracias por jugar. ¡Hasta luego!")
            break
        elif opcion != "1":
            print("Opción inválida. Saliendo del juego.")
            break

jugar_tres_en_linea_bot()
