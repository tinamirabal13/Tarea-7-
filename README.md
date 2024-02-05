# Tarea-7-
Batalla de Pokémon con tuplas 
import random  

jugador = (100, 100)  # Tupla para almacenar los puntos de salud y defensa del jugador
oponente = (100, 100)  # Tupla para almacenar los puntos de salud y defensa del oponente
ataques_jugador = []  # Array para almacenar los ataques del jugador
ataques_oponente = []  # Array para almacenar los ataques del oponente

while jugador[0] > 0 and oponente[0] > 0:
    ataque_jugador = input("ataque: ")
    ataque_jugador = ataque_jugador.lower()
    ataques_jugador.append(ataque_jugador) 
    if ataque_jugador == "malicioso":
        oponente = (oponente[0] - 10, oponente[1])
    elif ataque_jugador == "placaje":
        placaje = 35 * (100 / oponente[1])
        oponente = (oponente[0] - placaje, oponente[1])
    elif ataque_jugador == "ascuas":
        pass
    else:
        print("¡Qué estás haciendo? ¡Tus ataques son malicioso, placaje y ascuas!")
        continue

    """turno del Oponente
       El turno del oponente se define con un Random
    """
    ataque_oponente = random.randrange(1, 3 + 1)
    ataques_oponente.append(ataque_oponente) 
    if ataque_oponente == 1:  # latigo
        jugador = (jugador[0] - 10, jugador[1] - 10)
    elif ataque_oponente == 2:  # placaje
        jugador = (jugador[0] - 35 * (100 / jugador[1]), jugador[1])
    elif ataque_oponente == 3:  # Pistola de agua
        jugador = (jugador[0] - 40, jugador[1])
        # randrange está garantizado a ser 1, 2 o 3

# Si termina el ciclo alguien ha ganado
if oponente[0] <= 0 and jugador[0] <= 0:
    print("empate")
elif oponente[0] <= 0:  # ya sabemos que el jugador es >0
    print("¡Felicidades, has ganado!")
else:  # ya sabemos que el oponente es >0
    print("Lo siento, has perdido")
