# Maths_Quizz

import random

NOMBRE_MIN = 1
NOMBRE_MAX = 10
NOMBRE_QUESTIONS = 10

def poser_question():
    a = random.randint(NOMBRE_MIN, NOMBRE_MAX)
    b = random.randint(NOMBRE_MIN, NOMBRE_MAX)
    o = random.randint(0, 1)  # 0 --> +, 1 --> *
    operateur_str = "+" if o == 0 else "*"
    calcul = a + b if o == 0 else a * b

    try:
        reponse_str = input(f"Calculez {a} {operateur_str} {b} : ")
        reponse_int = int(reponse_str)
    except ValueError:
        print("Veuillez entrer un nombre valide.")
        return False  # Considère la réponse incorrecte si la saisie est invalide

    if reponse_int == calcul:
        return True
    else:
        print(f"Réponse incorrecte. La bonne réponse était {calcul}.")
        return False

nb_points = 0
for i in range(NOMBRE_QUESTIONS):
    print(f"Question n° {i + 1} sur {NOMBRE_QUESTIONS}")
    if poser_question():
        print("Réponse correcte")
        nb_points += 1
    else:
        print("Réponse incorrecte")
    print()

print(f"Votre score final est : {nb_points} / {NOMBRE_QUESTIONS}")

# Evaluation
pourcentage_score = (nb_points / NOMBRE_QUESTIONS) * 100
if nb_points == 0:
    print("Révisez vos maths !")
elif nb_points == NOMBRE_QUESTIONS:
    print("Excellent !")
elif pourcentage_score >= 50:
    print("Pas mal ! Continuez ainsi.")
else:
    print("Peut mieux faire.")
