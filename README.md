# convertiseur_en_python
```python
import time
import sys

def afficher_animation(texte, duree=2):
    """Affiche une animation simple avec un texte."""
    print(texte, end="")
    for _ in range(duree):
        for point in "...":
            print(point, end="", flush=True)
            time.sleep(0.5)
    print()  # Nouvelle ligne

def convertir_longueur(valeur, unite_de, unite_vers):
    """Convertir une valeur entre différentes unités de longueur."""
    conversions = {
        "mètre": 1,
        "kilomètre": 0.001,
        "centimètre": 100,
        "millimètre": 1000,
        "pouce": 39.3701,
        "pied": 3.28084,
        "mile": 0.000621371,
    }
    if unite_de not in conversions or unite_vers not in conversions:
        raise ValueError("Unité inconnue. Vérifiez les unités saisies.")
    return valeur * conversions[unite_vers] / conversions[unite_de]

def convertir_poids(valeur, unite_de, unite_vers):
    """Convertir une valeur entre différentes unités de poids."""
    conversions = {
        "kilogramme": 1,
        "gramme": 1000,
        "livre": 2.20462,
        "once": 35.274,
    }
    if unite_de not in conversions or unite_vers not in conversions:
        raise ValueError("Unité inconnue. Vérifiez les unités saisies.")
    return valeur * conversions[unite_vers] / conversions[unite_de]

def convertir_temperature(valeur, unite_de, unite_vers):
    """Convertir une valeur entre différentes unités de température."""
    if unite_de == "Celsius":
        if unite_vers == "Fahrenheit":
            return valeur * 9/5 + 32
        elif unite_vers == "Kelvin":
            return valeur + 273.15
    elif unite_de == "Fahrenheit":
        if unite_vers == "Celsius":
            return (valeur - 32) * 5/9
        elif unite_vers == "Kelvin":
            return (valeur - 32) * 5/9 + 273.15
    elif unite_de == "Kelvin":
        if unite_vers == "Celsius":
            return valeur - 273.15
        elif unite_vers == "Fahrenheit":
            return (valeur - 273.15) * 9/5 + 32
    elif unite_de not in ["Celsius", "Fahrenheit", "Kelvin"] or unite_vers not in ["Celsius", "Fahrenheit", "Kelvin"]:
        raise ValueError("Unité inconnue. Vérifiez les unités saisies.")
    return valeur  # Si les unités sont identiques

def main():
    print("Bienvenue dans le convertisseur d'unités !")
    afficher_animation("Chargement", duree=3)

    while True:
        try:
            print("\nChoisissez le type de conversion :")
            print("1 - Longueur")
            print("2 - Poids")
            print("3 - Température")
            print("4 - Quitter")
            choix = input("Entrez votre choix (1, 2, 3 ou 4) : ")

            if choix == "4":
                print("Merci d'avoir utilisé le convertisseur. À bientôt !")
                sys.exit()

            if choix not in ["1", "2", "3"]:
                raise ValueError("Choix invalide. Veuillez entrer 1, 2, 3 ou 4.")

            if choix == "1":
                unite_de = input("Entrez l'unité de départ (mètre, kilomètre, centimètre, etc.) : ").lower()
                unite_vers = input("Entrez l'unité d'arrivée : ").lower()
                valeur = float(input("Entrez la valeur à convertir : "))
                resultat = convertir_longueur(valeur, unite_de, unite_vers)
            elif choix == "2":
                unite_de = input("Entrez l'unité de départ (kilogramme, gramme, livre, etc.) : ").lower()
                unite_vers = input("Entrez l'unité d'arrivée : ").lower()
                valeur = float(input("Entrez la valeur à convertir : "))
                resultat = convertir_poids(valeur, unite_de, unite_vers)
            elif choix == "3":
                unite_de = input("Entrez l'unité de départ (Celsius, Fahrenheit, Kelvin) : ").capitalize()
                unite_vers = input("Entrez l'unité d'arrivée : ").capitalize()
                valeur = float(input("Entrez la valeur à convertir : "))
                resultat = convertir_temperature(valeur, unite_de, unite_vers)

            afficher_animation("Conversion en cours", duree=3)
            print(f"Résultat : {valeur} {unite_de} = {resultat:.2f} {unite_vers}")
        except ValueError as e:
            print(f"Erreur : {e}. Veuillez réessayer.")
        except Exception as e:
            print(f"Une erreur inattendue s'est produite : {e}. Veuillez réessayer.")

if __name__ == "__main__":
    main()

```
