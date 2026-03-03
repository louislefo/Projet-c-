# [cite_start]Projet : Programmation Orientée Objet en C++ - ALTERDUNE [cite: 1, 2, 9]

[cite_start]**Auteur :** Daniel Wladdimiro [cite: 3]  
[cite_start]**Institution :** ESILV [cite: 3]  
[cite_start]**Contact :** daniel.wladdimiro@devinci.fr [cite: 4]  
[cite_start]**Période :** Second semestre 2025-2026 [cite: 5]

---

## [cite_start]1. Introduction [cite: 6]
[cite_start]La programmation orientée objet (POO) est un paradigme fondamental pour le développement de logiciels structurés et modulaires. [cite: 7] [cite_start]Ce projet doit être réalisé en binôme. [cite: 8] [cite_start]Il propose la création d'un mini-jeu de type RPG nommé ALTERDUNE, où les entités (joueur, monstres, objets) sont modélisées sous forme de classes. [cite: 9, 10]

## [cite_start]2. Description du Projet [cite: 11]
[cite_start]Le projet consiste à développer un jeu par console structuré autour des éléments suivants : [cite: 12]
* [cite_start]Un menu principal hors combat. [cite: 13]
* [cite_start]Des combats au tour par tour. [cite: 14]
* [cite_start]Un système de fins multiples basé sur les choix du joueur. [cite: 15]
* [cite_start]Le chargement de données depuis deux fichiers obligatoires. [cite: 16]

### [cite_start]2.1 Objectif du projet [cite: 17]
L'objectif est de mettre en pratique les concepts suivants :
* [cite_start]**L'encapsulation** (attributs privés, accesseurs/modificateurs). [cite: 19]
* [cite_start]**L'héritage** (joueur/monstres). [cite: 20]
* [cite_start]**Le polymorphisme** (comportements spécifiques selon la catégorie de monstre). [cite: 21]
* [cite_start]**La composition** (inventaire, actions ACT, bestiaire). [cite: 22]
* [cite_start]**La lecture de fichiers** pour initialiser les objets. [cite: 23]

---

## [cite_start]3. Démarrage d'une partie [cite: 24]
[cite_start]Au lancement du programme : [cite: 25]
1. [cite_start]Le joueur saisit le nom de son personnage. [cite: 27]
2. [cite_start]Le jeu charge `items.csv` (inventaire initial) et `monsters.csv` (ennemis possibles). [cite: 28, 29, 30]
3. [cite_start]Le jeu affiche un résumé incluant le nom, les HP (actuel et maximum) et la liste des items avec leurs quantités. [cite: 31, 32, 33, 34]

---

## [cite_start]4. Condition de fin de partie et fins multiples [cite: 35]
[cite_start]Une partie se termine lorsque le joueur obtient 10 victoires. [cite: 36] [cite_start]Le jeu affiche alors une fin selon l'historique : [cite: 37]
* [cite_start]**Fin Génocidaire :** Le joueur a tué tous les monstres vaincus (0 épargné). [cite: 38]
* [cite_start]**Fin Pacifiste :** Le joueur a épargné tous les monstres vaincus (0 tué). [cite: 39]
* [cite_start]**Fin Neutre :** Le joueur a à la fois tué et épargné des monstres. [cite: 40]

---

## [cite_start]5. Monstres, catégories et actions ACT [cite: 41]

### [cite_start]5.1 Catégories de monstres [cite: 42]
[cite_start]La catégorie détermine le nombre d'actions ACT disponibles : [cite: 43]
* [cite_start]**NORMAL :** 2 actions. [cite: 44]
* [cite_start]**MINIBOSS :** 3 actions. [cite: 45]
* [cite_start]**BOSS :** 4 actions. [cite: 45]

### [cite_start]5.2 Système Mercy [cite: 46]
[cite_start]Chaque monstre possède une jauge Mercy (de 0 à 100). [cite: 47] [cite_start]Si la jauge est $\ge 100$, le joueur peut épargner le monstre pour gagner le combat sans le tuer. [cite: 48]

### [cite_start]5.3 Catalogue d'actions ACT [cite: 49]
[cite_start]Les actions sont pré-définies dans le code (map ou vector) et possèdent un identifiant, un texte affiché et un impact sur la jauge Mercy (positif, négatif ou nul). [cite: 50, 51, 52, 53]
**Contraintes :**
* [cite_start]Minimum 8 actions différentes dans le catalogue. [cite: 55]
* [cite_start]Au moins 2 actions avec un impact négatif. [cite: 56]
* [cite_start]La jauge Mercy est bornée entre 0 et l'objectif (ex. 100). [cite: 58]

---

## [cite_start]6. Menu de Simulation (Menu principal) [cite: 62]
[cite_start]Options disponibles : [cite: 63]
* [cite_start]**Bestiaire :** Affiche les monstres vaincus avec leurs caractéristiques (nom, catégorie, statistiques) et le résultat (tué ou épargné). [cite: 64, 69, 70, 71, 72, 73, 74]
* [cite_start]**Statistiques :** Affiche le nom, les HP, le nombre de tués/épargnés et le nombre de victoires. [cite: 66, 75, 76, 77, 78, 79, 80, 81]
* [cite_start]**Items :** Affiche l'inventaire et permet d'utiliser un objet (soin) même hors combat. [cite: 67, 82, 83, 84, 85, 86, 87]
* [cite_start]**Démarrer un combat :** Lance un combat aléatoire contre un ennemi du fichier CSV. [cite: 65, 88, 89]
* [cite_start]**Quitter.** [cite: 68]

---

## [cite_start]7. Combat [cite: 91]
[cite_start]Le combat oppose le joueur à un monstre jusqu'à ce que l'un des deux soit vaincu. [cite: 92]

### [cite_start]7.1 Menu de combat [cite: 93]
[cite_start]À chaque tour, le joueur choisit entre : **FIGHT, ACT, ITEM, MERCY**. [cite: 94, 95, 97, 98, 99]

### [cite_start]7.2 Règles de dégâts [cite: 96]
[cite_start]Les dégâts sont calculés aléatoirement à chaque attaque : [cite: 100, 101]
[cite_start]$$deg\hat{a}ts = rand(0, HP_{defenseur}^{max})$$ [cite: 102]
* [cite_start]Si dégâts $= 0$, l'attaque est ratée. [cite: 104]
* [cite_start]Les HP ne peuvent pas descendre sous 0. [cite: 106]

### [cite_start]7.3 Actions du joueur [cite: 110]
* **FIGHT :** Attaque directe. [cite_start]Si HP du monstre $= 0$, il est tué. [cite: 111, 112]
* [cite_start]**ACT :** Choix d'une action selon la catégorie du monstre pour modifier la jauge Mercy. [cite: 113, 114, 116]
* [cite_start]**ITEM :** Utilise un objet et consomme le tour. [cite: 118, 119, 120]
* [cite_start]**MERCY :** Épargne le monstre si Mercy $\ge 100$. [cite: 122, 123]

### [cite_start]7.4 Tour du monstre [cite: 125]
[cite_start]Le monstre attaque le joueur selon la même formule. [cite: 126] [cite_start]Si le joueur tombe à 0 HP, la partie est perdue immédiatement. [cite: 127]

---

## [cite_start]8. Chargement des Données [cite: 128]

### [cite_start]8.1 items.csv [cite: 136]
[cite_start]Format : `nom; type; valeur; quantite` [cite: 139]
* [cite_start]`type` : Limité à `HEAL`. [cite: 140]
* [cite_start]`valeur` : Points de vie rendus. [cite: 140]

### [cite_start]8.2 monsters.csv [cite: 147]
[cite_start]Format : `categorie; nom; hp; atk; def; mercyGoal; act1; act2; act3; act4` [cite: 155]
* [cite_start]Les catégories `NORMAL`, `MINIBOSS` et `BOSS` utilisent respectivement 2, 3 ou 4 actions. [cite: 156, 157, 158]

---

## [cite_start]9. Évaluation [cite: 163]

| Étape | Poids | Critères principaux |
| :--- | :--- | :--- |
| **Mini-suivi (TD11-12)** | [cite_start]20% [cite: 165] | [cite_start]UML initial, structure du code, premières classes. [cite: 169, 170] |
| **Soutenance P1 (TD15-16)** | [cite_start]80% [cite: 172] | [cite_start]UML final, POO (héritage, encapsulation, polymorphisme), lecture fichiers, gameplay. [cite: 176, 177, 180, 181, 182, 183] |
| **Soutenance P2 (TD17-18)** | [cite_start]- [cite: 188] | [cite_start]Session Q&R sur la maîtrise individuelle du code. [cite: 189] |

[cite_start]**Bonus :** Jusqu'à +4 points pour un projet "sur-salient". [cite: 191, 192]  
[cite_start]**Formule :** $Note = 0.2 \times Note_{mini} + 0.8 \times Note_{soutenance} + bonus - penalite$ [cite: 196]