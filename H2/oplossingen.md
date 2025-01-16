# Oplossingen: H2

### Oefeningen

1. **Stel je hebt een gesorteerde lijst met 128 namen. Hoeveel stappen zijn nodig om een naam te vinden met binaire zoekopdrachten?**

2. **Wat gebeurt er als je de lijst verdubbelt naar 256 namen? Hoeveel stappen zijn dan nodig?**

3. **Pas de binaire zoekopdracht toe op de lijst `[2, 4, 6, 8, 10, 12, 14]` om 10 te vinden. Teken de stappen in een flowchart.**

4. **Verander de Python-code zodat deze ook de stappen toont die worden doorlopen.**

5. **Wat gebeurt er als de lijst niet is gesorteerd? Leg uit waarom binaire zoekopdrachten in dat geval niet werken.**

6. **Schrijf een functie die controleert of een lijst gesorteerd is voordat een binaire zoekopdracht wordt uitgevoerd.**

---

### Oplossingen

1. **Aantal stappen voor 128 namen:**
   - Bij een lijst van 128 elementen kost een binaire zoekopdracht maximaal **log₂(128) = 7 stappen**.

2. **Aantal stappen voor 256 namen:**
   - Bij een lijst van 256 elementen kost een binaire zoekopdracht maximaal **log₂(256) = 8 stappen**.

3. **Flowchart voor het zoeken naar 10 in `[2, 4, 6, 8, 10, 12, 14]`:**

   ```mermaid
   graph TD;
       Start((Start)) --> CheckMidden{Is lijst[midden] == 10?};
       CheckMidden -->|Ja| Gevonden((Gevonden));
       CheckMidden -->|Nee| Compare{Is lijst[midden] > 10?};
       Compare -->|Ja| UpdateHoog[hoog = midden - 1];
       Compare -->|Nee| UpdateLaag[laag = midden + 1];
       UpdateHoog --> CheckMidden;
       UpdateLaag --> CheckMidden;
   ```

4. **Python-code die stappen toont:**
   ```python
   def binaire_zoekopdracht(lijst, doel):
       laag = 0
       hoog = len(lijst) - 1

       while laag <= hoog:
           midden = (laag + hoog) // 2
           print(f"Controle: laag={laag}, hoog={hoog}, midden={midden}, waarde={lijst[midden]}")

           if lijst[midden] == doel:
               return midden
           elif lijst[midden] > doel:
               hoog = midden - 1
           else:
               laag = midden + 1

       return -1  # Niet gevonden

   lijst = [2, 4, 6, 8, 10, 12, 14]
   doel = 10
   resultaat = binaire_zoekopdracht(lijst, doel)
   print("Resultaat:", resultaat)
   ```

5. **Wat gebeurt er als de lijst niet is gesorteerd?**
   - **Antwoord:** Binaire zoekopdrachten werken alleen met gesorteerde lijsten. Als de lijst niet gesorteerd is, kunnen verkeerde resultaten ontstaan omdat het algoritme uitgaat van een gesorteerde structuur. Bijvoorbeeld, het algoritme kan overslaan waar het doelgetal daadwerkelijk is.

6. **Functie om te controleren of een lijst gesorteerd is:**
   ```python
   def is_gesorteerd(lijst):
       for i in range(len(lijst) - 1):
           if lijst[i] > lijst[i + 1]:
               return False
       return True

   lijst = [2, 4, 6, 8, 10, 12, 14]
   print("Is de lijst gesorteerd?", is_gesorteerd(lijst))
   ```

