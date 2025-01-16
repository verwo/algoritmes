# Oefeningen en Oplossingen: Hoofdstuk 3 - Big O-notatie

### Oefeningen

1. **Analyseer de tijdcomplexiteit van de volgende code:**
   ```python
   def example(array):
       for i in range(len(array)):
           for j in range(10):
               print(array[i], j)
   ```

2. **Geef de Big O-notatie van:**
   - Het itereren over een lijst.
   - Het uitvoeren van een binaire zoekopdracht.

3. **Maak een grafiek die de complexiteiten O(1), O(n), en O(n²) toont voor n van 1 tot 100.**

4. **Beantwoord de volgende vragen in termen van Big O:**
   - Je hebt een naam en wilt het telefoonnummer van de persoon vinden in een telefoonboek.
   - Je hebt een telefoonnummer en wilt de naam van de persoon vinden. (Hint: Dit vereist een lineaire zoekopdracht.)
   - Je wilt de nummers van alle mensen in het telefoonboek lezen.
   - Je wilt de nummers lezen van alleen de namen die beginnen met de letter "A".

---

### Oplossingen

#### 1. Analyseer de tijdcomplexiteit van de code:

**Code:**
```python
   def example(array):
       for i in range(len(array)):
           for j in range(10):
               print(array[i], j)
```

**Oplossing:**
- De buitenste `for`-loop loopt door elk element in `array` → **O(n)**.
- De binnenste `for`-loop loopt altijd 10 keer → **O(1)** (constant).
- Totale tijdcomplexiteit: **O(n)**.

#### 2. Geef de Big O-notatie van:
- **Het itereren over een lijst:**
   - **O(n)** (lineaire tijdcomplexiteit).

- **Het uitvoeren van een binaire zoekopdracht:**
   - **O(log n)** (logaritmische tijd).

#### 3. Maak een grafiek:
- **O(1):** Constant, de waarde blijft gelijk ongeacht de invoergrootte.
- **O(n):** Lineair, de tijd neemt proportioneel toe met de invoergrootte.
- **O(n²):** Kwadratisch, de tijd groeit exponentieel bij grotere invoer.
<img src="./media/output.png">

**🚀 Voor gevorderden :**
```python
import matplotlib.pyplot as plt
import numpy as np

n = np.arange(1, 101)
constant = np.ones_like(n)
linear = n
quadratic = n**2

plt.figure(figsize=(10, 6))
plt.plot(n, constant, label='O(1)', linestyle='--')
plt.plot(n, linear, label='O(n)')
plt.plot(n, quadratic, label='O(n²)')
plt.yscale('log')
plt.xlabel('Invoergrootte (n)')
plt.ylabel('Aantal operaties')
plt.title('Complexiteiten O(1), O(n), en O(n²)')
plt.legend()
plt.grid()
plt.show()
```

#### 4. Beantwoord de volgende vragen in termen van Big O:

1. **Je hebt een naam en wilt het telefoonnummer van de persoon vinden in een telefoonboek:**
   - **O(log n)** (binaire zoekopdracht).

2. **Je hebt een telefoonnummer en wilt de naam van de persoon vinden:**
   - **O(n)** (lineaire zoekopdracht).

3. **Je wilt de nummers van alle mensen in het telefoonboek lezen:**
   - **O(n)** (alle items doorlopen).

4. **Je wilt de nummers lezen van alleen de namen die beginnen met de letter "A":**
   - **Als gesorteerd:** **O(k)** (waarbij k het aantal namen met "A" is).
   - **Als niet gesorteerd:** **O(n)** (lineair zoeken).
