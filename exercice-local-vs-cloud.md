# Exercice Pratique - Local vs Cloud

## Module I / III - Section C : Infrastructure et localisation

---

## Exercice 4 : Local vs Cloud - Expérience pratique (30 min)

### Objectif pédagogique

Comprendre concrètement la différence fondamentale entre :
- **Traitement Cloud** : Les calculs se font sur un serveur distant
- **Traitement Local** : Les calculs se font sur votre propre machine

---

### Partie A : Traitement Cloud - ChatGPT (10 min)

#### Expérience 1 : ChatGPT nécessite Internet

**Préparation** :
1. Ouvrez ChatGPT dans votre navigateur
2. Commencez une conversation, posez 2-3 questions
3. Vérifiez que tout fonctionne normalement

**Expérience** :
1. **Coupez complètement votre connexion Internet** :
   - Sur Mac : Désactivez le Wi-Fi dans la barre de menu
   - Sur Windows : Désactivez le Wi-Fi ou débranchez le câble Ethernet
   - Ou mettez votre ordinateur en mode Avion

2. Essayez de poser une nouvelle question à ChatGPT

**Que se passe-t-il ?** :
- ☐ Un message d'erreur apparaît
- ☐ La page ne charge plus
- ☐ "Impossible de se connecter"
- ☐ Le cercle de chargement tourne indéfiniment

**Notez vos observations** :

_______________________________________________

_______________________________________________

**Réactivez votre connexion Internet** et vérifiez que ChatGPT fonctionne à nouveau.

#### Analyse - Où se passe le traitement ?

**Schéma du fonctionnement** :

```
┌─────────────────────┐
│  Votre Ordinateur   │
│                     │
│  [Navigateur Web]   │  ← Interface uniquement
│  - Affiche le chat  │  ← Pas de calcul IA ici
│  - Envoie le texte  │
└──────────┬──────────┘
           │
           │ Internet (HTTPS)
           │
           ▼
┌─────────────────────┐
│  Serveur OpenAI     │
│   (USA / Cloud)     │
│                     │
│  [Modèle GPT-4]     │  ← Le calcul IA se fait ICI
│  - Traite la req.   │
│  - Génère réponse   │
└─────────────────────┘
```

**Conclusion Partie A** :

Remplissez les blancs :

- Votre ordinateur joue le rôle de _________________ (terminal/interface)
- Le traitement IA se fait sur _________________ (serveur distant/OpenAI)
- Sans Internet, ChatGPT _________________ (fonctionne / ne fonctionne pas)
- Vos données doivent _________________ (quitter votre ordinateur / rester locales)

---

### Partie B : Traitement Local - Applications hors ligne (10 min)

#### Expérience 2 : Correcteur orthographique (traitement local)

**Préparation** :
1. Ouvrez un logiciel de traitement de texte :
   - Microsoft Word (si installé localement, pas Word Online)
   - LibreOffice Writer
   - Pages (Mac)
   - Notepad++ avec plugin de vérification

2. Vérifiez que le correcteur orthographique est activé

**Test avec Internet** :
1. Tapez une phrase avec des fautes : "Jé fé dé fotes dortografe"
2. Le correcteur souligne-t-il les erreurs ? ☐ Oui ☐ Non

**Expérience hors ligne** :
1. **Coupez votre connexion Internet** (mode avion)
2. Ouvrez un nouveau document
3. Tapez à nouveau : "Jé fé dé fotes dortografe"

**Que se passe-t-il ?** :
- ☐ Le correcteur fonctionne toujours
- ☐ Les fautes sont soulignées
- ☐ Les suggestions de correction apparaissent
- ☐ Aucun message d'erreur

**Notez vos observations** :

_______________________________________________

_______________________________________________

#### Analyse - Où se passe le traitement ?

**Schéma du fonctionnement local** :

```
┌─────────────────────────────────┐
│     Votre Ordinateur            │
│                                 │
│  [Application Word/LibreOffice] │
│   ├─ Affichage du texte        │
│   ├─ Dictionnaire (fichier)    │  ← Stocké sur votre disque
│   └─ Algorithme correction     │  ← S'exécute localement
│                                 │
│  Le traitement se fait ICI      │
│  Aucune donnée envoyée dehors   │
└─────────────────────────────────┘

          ❌ Pas d'Internet nécessaire
```

**Conclusion Partie B** :

- Le dictionnaire est stocké _________________ (sur votre ordinateur / sur un serveur)
- Le traitement se fait _________________ (localement / à distance)
- Sans Internet, le correcteur _________________ (fonctionne / ne fonctionne pas)
- Vos documents _________________ (quittent votre ordinateur / restent privés)

---

### Partie C : Cas hybride - Microsoft 365 Copilot (10 min)

#### Expérience 3 : Modèle hybride

Si vous avez accès à **Microsoft Word avec Copilot** ou **Google Docs** :

**Test 1 : Fonctionnalités de base (avec Internet)**
1. Ouvrez Word/Google Docs en ligne
2. Tapez du texte
3. Utilisez le correcteur orthographique de base
4. Utilisez Copilot/Assistant IA (demandez de rédiger un paragraphe)

**Test 2 : Hors ligne**
1. Coupez Internet
2. Fonctionnalités qui marchent encore : _________________
3. Fonctionnalités qui ne marchent plus : _________________

**Analyse** :

| Fonctionnalité | Local ou Cloud ? | Fonctionne hors ligne ? |
|----------------|------------------|-------------------------|
| Saisie de texte | | |
| Correction orthographique basique | | |
| Mise en forme (gras, italique) | | |
| Copilot / Assistant IA | | |
| Traduction automatique | | |
| Génération de texte par IA | | |

---

### Synthèse comparative (5 min)

#### Tableau récapitulatif

| Critère | Traitement LOCAL | Traitement CLOUD |
|---------|------------------|------------------|
| **Exemple** | Correcteur Word, Calculatrice | ChatGPT, Claude, Gemini |
| **Internet nécessaire ?** | ❌ Non | ✅ Oui (obligatoire) |
| **Vitesse** | ⚡ Instantanée | 🌐 Dépend de la connexion |
| **Confidentialité** | 🔒 Données restent sur votre PC | ⚠️ Données envoyées au serveur |
| **Puissance de calcul** | 💻 Limitée par votre machine | ☁️ Serveurs très puissants |
| **Mises à jour** | 📦 Installations manuelles | 🔄 Automatiques et continues |
| **Coût** | 💰 Achat logiciel (une fois) | 💳 Souvent abonnement mensuel |
| **Accessibilité** | 📍 Un seul appareil | 🌍 Tous vos appareils |
| **En panne réseau** | ✅ Fonctionne | ❌ Inaccessible |

#### Avantages et inconvénients

**TRAITEMENT LOCAL** ✅ ❌

Avantages :
- ✅ Fonctionne sans Internet
- ✅ Confidentialité maximale (données ne sortent pas)
- ✅ Pas de latence réseau
- ✅ Pas de coût récurrent (après achat)

Inconvénients :
- ❌ Limité par la puissance de votre ordinateur
- ❌ Nécessite de l'espace disque
- ❌ Mises à jour manuelles
- ❌ Ne bénéficie pas des dernières avancées IA (trop gourmandes)

**TRAITEMENT CLOUD** ✅ ❌

Avantages :
- ✅ Accès aux modèles IA les plus puissants
- ✅ Accessible de partout (téléphone, tablette, PC)
- ✅ Mises à jour automatiques
- ✅ Pas de limite de puissance de calcul

Inconvénients :
- ❌ Nécessite Internet (inutilisable hors ligne)
- ❌ Dépendance à un fournisseur tiers
- ❌ Questions de confidentialité et souveraineté
- ❌ Coûts récurrents (abonnements)

---

### Cas d'usage : Quand utiliser quoi ?

#### Scénarios pratiques

Pour chaque situation, indiquez si vous privilégiez **Local** ou **Cloud** :

| Situation | Local ou Cloud ? | Justification |
|-----------|------------------|---------------|
| Rédiger un contrat confidentiel avec des données sensibles | | |
| Générer des idées de brainstorming pour un projet | | |
| Corriger l'orthographe d'un document | | |
| Analyser 500 décisions de justice | | |
| Travailler dans le train sans connexion | | |
| Collaborer avec 5 collègues sur un document | | |
| Traiter des données médicales | | |
| Créer une présentation PowerPoint | | |

---

### Questions de réflexion finale

**Q1 : Avenir de l'IA - Local ou Cloud ?**

Actuellement, la tendance est au Cloud pour l'IA. Mais de nouvelles solutions émergent :
- **LLaMA, Mistral 7B** : Modèles qui peuvent tourner sur un PC puissant
- **Apple Intelligence** : IA locale sur iPhone/Mac
- **Microsoft Copilot+** : Traitement hybride (local + cloud)

Selon vous, quel sera le modèle dominant dans 5 ans ? Pourquoi ?

_______________________________________________

_______________________________________________

**Q2 : Implications juridiques**

En tant que juriste, quelles questions vous posez-vous sur :
- Le stockage de données clients sur des serveurs cloud ?
- La conformité RGPD ?
- Le secret professionnel de l'avocat ?

_______________________________________________

_______________________________________________

**Q3 : Compromis personnel**

Pour votre usage personnel des IA, quel équilibre trouvez-vous entre :
- Puissance (Cloud)
- Confidentialité (Local)

_______________________________________________

_______________________________________________

---

### Pour aller plus loin (facultatif)

#### Tester une IA locale

Si vous avez un ordinateur puissant (16 Go RAM minimum) :

1. **Installez LM Studio** (gratuit) : [https://lmstudio.ai/](https://lmstudio.ai/)
2. Téléchargez un petit modèle (ex: Mistral 7B)
3. Testez-le complètement hors ligne
4. Comparez avec ChatGPT :
   - Qualité des réponses
   - Vitesse
   - Facilité d'usage

**Observations** :

_______________________________________________

_______________________________________________

---

## Conclusion de l'exercice

### Ce que vous avez appris

- ✅ Cloud = traitement sur serveur distant (nécessite Internet)
- ✅ Local = traitement sur votre machine (fonctionne hors ligne)
- ✅ Chaque approche a ses avantages et inconvénients
- ✅ Le choix dépend de vos besoins (puissance vs confidentialité)

### Liens avec le cours

Cet exercice illustre concrètement :
- **Section C.1** : Local vs Cloud
- **Section C.2** : Données en transit vs données au repos
- **Section C.3** : Souveraineté et enjeux juridiques

**Vous êtes maintenant capables de** :
- Comprendre où vont vos données
- Évaluer les risques de confidentialité
- Choisir l'outil adapté selon le contexte
- Expliquer ces concepts à un client ou collègue
