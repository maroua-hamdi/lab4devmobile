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

![MainActivity.java](image2.png)

---

### Étape 4 — Premier fragment : `FragmentOne`

**Layout `fragment_one.xml` :** un `TextView` "Fragment One" et un bouton "Dire bonjour".

![fragment_one.xml](image5.png)

**Code `FragmentOne.java` :** au clic sur le bouton, le texte change pour "Bonjour depuis Fragment 1 !".

![FragmentOne.java](image3.png)

---

### Étape 5 — Deuxième fragment : `FragmentTwo`

**Layout `fragment_two.xml` :** un `TextView` "Valeur : 0" et une `SeekBar` avec `max="100"`.

![fragment_two.xml](image6.png)

**Code `FragmentTwo.java` :** la SeekBar met à jour le TextView en temps réel, et la progression est sauvegardée avec `onSaveInstanceState`.

![FragmentTwo.java](image4.png)

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

![Écran Fragment 1 initial](image7.png)

**Fragment 1 — après clic sur "Dire bonjour" :**

![Écran Fragment 1 après clic](image8.png)

---

## Notions clés apprises

- **Fragment** : composant UI modulaire attaché à une `Activity`
- **FragmentManager** : gestionnaire des fragments dans une activité
- **FragmentTransaction** : permet d'ajouter, remplacer ou supprimer des fragments dynamiquement
- **onSaveInstanceState** : mécanisme de sauvegarde de l'état d'un fragment
- **Cycle de vie d'un fragment** : `onCreate` → `onCreateView` → `onViewCreated` → `onResume` → `onPause` → `onDestroyView` → `onDestroy`
