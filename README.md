# LAB 4 — Manipulation Dynamique des Fragments avec FragmentManager et FragmentTransaction

**Cours :** Programmation Mobile — Android avec Java  



---

## Objectif général

Ce lab a pour but d'apprendre à :

- Créer et utiliser des **fragments dynamiques** dans une activité Android
- Naviguer entre plusieurs fragments avec **FragmentManager**
- Gérer les **événements et états** dans les fragments (clics, SeekBar, etc.)
- Comprendre le **cycle de vie** d'un fragment

---

## Structure du projet

```
FragmentsLab/
├── app/src/main/
│   ├── java/com/example/fragmentslab/
│   │   ├── MainActivity.java
│   │   ├── FragmentOne.java
│   │   └── FragmentTwo.java
│   └── res/layout/
│       ├── activity_main.xml
│       ├── fragment_one.xml
│       └── fragment_two.xml
└── AndroidManifest.xml
```

---

## Étapes réalisées

### Étape 2 — Interface principale (`activity_main.xml`)

Le layout principal contient un `LinearLayout` horizontal avec deux boutons et un `FrameLayout` conteneur pour les fragments.

<img width="1920" height="1016" alt="image" src="https://github.com/user-attachments/assets/8c310950-4b88-4b74-9c1e-a936bc362dcc" />


---

### Étape 3 — Contrôleur : `MainActivity.java`

La `MainActivity` gère la navigation entre les fragments via `getSupportFragmentManager()`. Au démarrage, **FragmentOne** est chargé par défaut.

<img width="1920" height="1018" alt="image" src="https://github.com/user-attachments/assets/58e08ff9-066f-4d53-bb5f-8cff842055be" />


---

### Étape 4 — Premier fragment : `FragmentOne`

**Layout `fragment_one.xml` :** un `TextView` "Fragment One" et un bouton "Dire bonjour".

<img width="1920" height="1022" alt="image" src="https://github.com/user-attachments/assets/8d7a5771-3fdf-4eb1-8686-a08558eb8aed" />



**Code `FragmentOne.java` :** au clic sur le bouton, le texte change pour "Bonjour depuis Fragment 1 !".

<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/fa166ac7-f484-444b-9340-fcc7aee98772" />


---

### Étape 5 — Deuxième fragment : `FragmentTwo`

**Layout `fragment_two.xml` :** un `TextView` "Valeur : 0" et une `SeekBar` avec `max="100"`.

<img width="1917" height="1020" alt="image" src="https://github.com/user-attachments/assets/ee8efd9e-77a5-44c9-acd1-c04b7b86297d" />


**Code `FragmentTwo.java` :** la SeekBar met à jour le TextView en temps réel, et la progression est sauvegardée avec `onSaveInstanceState`.

<img width="1910" height="1021" alt="image" src="https://github.com/user-attachments/assets/a0a1441d-09bd-4ac8-9db6-1d737d5d7869" />


---

### Étape 6 — Navigation entre fragments

La navigation est gérée dans `MainActivity` avec `FragmentTransaction.replace()`.

---

### Étape 8 — Vérification visuelle

| Fragment | Contenu affiché | Interaction |
|----------|----------------|-------------|
| Fragment 1 | "Fragment One" + bouton "Dire bonjour" | Clic → affiche "Bonjour depuis Fragment 1 !" |
| Fragment 2 | "Valeur : 0" + SeekBar | Déplacement → met à jour la valeur affichée |

**Fragment 1 — état initial :**

<img width="266" height="515" alt="image" src="https://github.com/user-attachments/assets/57fad18d-8d46-42b8-bd5a-b779c5aa59ec" />


**Fragment 1 — après clic sur "Dire bonjour" :**

<img width="237" height="493" alt="image" src="https://github.com/user-attachments/assets/c5a4eb4b-161d-4f20-9e6d-8d7ff9fef037" />


**Fragment 2 — état initial (Valeur : 0) :**

<img width="274" height="507" alt="image" src="https://github.com/user-attachments/assets/a2de9a95-a758-44cf-a1a6-6637a602c981" />

**Fragment 2 — après déplacement de la SeekBar (Valeur : 27) :**

<img width="257" height="506" alt="image" src="https://github.com/user-attachments/assets/95ac8368-de3b-48e0-861a-bda255fb4755" />


---

## Notions clés apprises

- **Fragment** : composant UI modulaire attaché à une `Activity`
- **FragmentManager** : gestionnaire des fragments dans une activité
- **FragmentTransaction** : permet d'ajouter, remplacer ou supprimer des fragments dynamiquement
- **onSaveInstanceState** : mécanisme de sauvegarde de l'état d'un fragment
- **Cycle de vie d'un fragment** : `onCreate` → `onCreateView` → `onViewCreated` → `onResume` → `onPause` → `onDestroyView` → `onDestroy`
