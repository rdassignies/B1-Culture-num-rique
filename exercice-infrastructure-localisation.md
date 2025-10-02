# Exercices Pratiques - Infrastructure et Localisation

## Module III - Section C : Infrastructure et localisation

---

## Exercice 1 : Tracer le chemin vers ChatGPT (15-20 min)

### Objectif pédagogique

Comprendre concrètement :
- Où se trouve physiquement ChatGPT
- Comment votre requête y arrive
- Les acteurs intermédiaires qui voient transiter vos données
- La notion de domaine, serveur, et géolocalisation

---

### Étape 1 : Analyser l'URL de ChatGPT (5 min)

#### Consignes

1. Ouvrez ChatGPT dans votre navigateur
2. Observez attentivement l'URL complète dans la barre d'adresse

**Exemple d'URL** : `https://chatgpt.com/c/abc123-def456`

#### Décryptage de l'URL

Décomposez chaque élément et notez vos observations :

| Élément | Signification | Rôle |
|---------|---------------|------|
| `https://` | HyperText Transfer Protocol Secure | Protocole de communication sécurisé, crypté |
| `chatgpt.com` | Nom de domaine | Adresse "lisible" du serveur |
| `/c/abc123...` | Chemin (path) | Identifiant unique de votre conversation |

#### Questions à explorer

**Q1 : Qui possède le domaine chatgpt.com ?**

Méthode :
1. Allez sur un service WHOIS : [https://www.whois.com/whois/](https://www.whois.com/whois/)
2. Tapez : `chatgpt.com`
3. Notez les informations :
   - Propriétaire (Registrant) : _________________
   - Pays d'enregistrement : _________________
   - Date de création : _________________
   - Date d'expiration : _________________

**Q2 : Le protocole HTTPS - pourquoi est-il important ?**

Cliquez sur le cadenas 🔒 dans la barre d'adresse :
- Le certificat est-il valide ? ☐ Oui ☐ Non
- Délivré par : _________________
- Valide jusqu'au : _________________

**Que signifie HTTPS ?**
- Les données entre votre navigateur et le serveur sont **chiffrées**
- Personne ne peut lire vos conversations en transit (ni votre FAI, ni les routeurs intermédiaires)
- Garantit que vous communiquez bien avec le vrai chatgpt.com (pas un imposteur)

---

### Étape 2 : Trouver l'adresse IP du serveur (5 min)

#### Qu'est-ce qu'une adresse IP ?

Le nom de domaine `chatgpt.com` est comme un nom de contact dans votre téléphone. L'adresse IP est comme le numéro de téléphone réel. Les ordinateurs utilisent les adresses IP pour communiquer.

#### Méthode A : Utiliser la commande `ping`

**Sur Windows** :
1. Ouvrez l'Invite de commandes (tapez `cmd` dans la recherche Windows)
2. Tapez : `ping chatgpt.com`
3. Appuyez sur Entrée

**Sur Mac/Linux** :
1. Ouvrez le Terminal (Cmd+Espace, tapez "Terminal")
2. Tapez : `ping chatgpt.com`
3. Appuyez sur Entrée

#### Ce que vous devriez voir :

```
Envoi d'une requête 'ping' sur chatgpt.com [104.18.x.x] avec 32 octets de données :
Réponse de 104.18.x.x : octets=32 temps=15 ms TTL=58
Réponse de 104.18.x.x : octets=32 temps=14 ms TTL=58
```

**Notez l'adresse IP** : _________________ (exemple : 104.18.x.x)

**Notez le temps de réponse (latence)** : _________________ ms

#### Que signifie cette latence ?

- **< 20 ms** : Excellent - serveur très proche ou connexion très rapide
- **20-50 ms** : Bon - serveur probablement dans le même pays/continent
- **50-150 ms** : Moyen - serveur sur un autre continent
- **> 150 ms** : Lent - serveur très éloigné ou connexion saturée

---

### Étape 3 : Tracer la route complète (5 min)

#### Objectif

Visualiser tous les routeurs intermédiaires entre vous et ChatGPT.

#### Commande à utiliser

**Sur Mac/Linux** :
```bash
traceroute chatgpt.com
```

**Sur Windows** :
```cmd
tracert chatgpt.com
```

#### Exemple de résultat :

```
Détermination de l'itinéraire vers chatgpt.com [104.18.x.x]
avec un maximum de 30 sauts :

  1    <1 ms    <1 ms    <1 ms  192.168.1.1        [Votre box Internet]
  2     5 ms     4 ms     5 ms  10.255.255.254     [Réseau Orange/SFR/Free...]
  3    10 ms    11 ms    10 ms  ae42-0.ncply102.rbci.orange.net [91.121.x.x]
  4    15 ms    14 ms    15 ms  ae41-0.ncidf101.rbci.orange.net [193.251.x.x]
  5    20 ms    19 ms    20 ms  81.52.x.x
  6    25 ms    24 ms    25 ms  104.18.x.x         [Serveur ChatGPT]

Itinéraire déterminé.
```

#### Analyse du traceroute

Remplissez ce tableau avec vos résultats réels :

| Saut n° | Adresse IP | Nom du routeur | Temps (ms) | Qui gère ce routeur ? |
|---------|------------|----------------|------------|-----------------------|
| 1 | | | | Votre box/routeur |
| 2 | | | | Votre FAI (Orange/Free/SFR...) |
| 3 | | | | |
| 4 | | | | |
| ... | | | | |
| Final | | | | OpenAI / Cloudflare |

**Comptez le nombre total de sauts** : _________________

**Chaque saut représente** :
- Un routeur qui voit transiter vos données
- Un point potentiel de surveillance ou de défaillance
- Une étape dans le voyage de votre requête

---

### Étape 4 : Géolocaliser le serveur (5 min)

#### Méthode

1. Copiez l'adresse IP finale obtenue à l'étape 2
2. Allez sur un service de géolocalisation IP :
   - [https://www.ip2location.com/](https://www.ip2location.com/)
3. Collez l'adresse IP et recherchez

#### Notez les informations géographiques

**Informations obtenues** :

- Pays : _________________
- Ville : _________________
- Région : _________________
- Code postal : _________________
- Latitude/Longitude : _________________
- Fournisseur (ISP) : _________________ (probablement Cloudflare ou AWS)

#### Observations importantes

**Note 1 : Cloudflare et les CDN**

Vous avez probablement trouvé une adresse IP Cloudflare, pas directement OpenAI. Pourquoi ?

- **Cloudflare** est un réseau de diffusion de contenu (CDN - Content Delivery Network)
- OpenAI utilise Cloudflare pour :
  - Distribuer la charge entre plusieurs serveurs
  - Vous connecter au serveur le plus proche géographiquement
  - Protéger contre les attaques DDoS
  - Accélérer les temps de réponse

**Schéma simplifié** :

```
Vous → Internet → Cloudflare (serveur proche) → OpenAI (serveur principal)
                   ↑
                   Vous êtes ICI dans le traceroute
```

**Note 2 : Localisation approximative**

La géolocalisation IP n'est pas toujours précise au mètre près :
- ✅ Le pays est généralement correct
- ⚠️ La ville peut être approximative
- ❌ Le code postal est souvent une estimation

---

### Étape 5 : Synthèse et réflexion (5 min)

#### Questions de réflexion

**Q1 : Distance parcourue**

En vous basant sur la géolocalisation, estimez la distance entre vous et le serveur :

Distance approximative : _________________ km

**Q2 : Vitesse de transmission**

Si votre message met 20 ms pour arriver au serveur à 6000 km de distance :

Vitesse approximative : 6000 km ÷ 0,020 s = 300 000 km/s

C'est proche de la vitesse de la lumière ! (299 792 km/s)

Les données voyagent dans des câbles en fibre optique où la lumière circule presque à sa vitesse maximale.

**Q3 : Qui peut voir vos données en transit ?**

Listez tous les acteurs qui voient vos données passer :

1. ☐ Votre système d'exploitation (Windows/Mac)
2. ☐ Votre routeur/box Internet
3. ☐ Votre Fournisseur d'Accès Internet (FAI)
4. ☐ Les routeurs intermédiaires (backbone Internet)
5. ☐ Cloudflare (CDN)
6. ☐ OpenAI (serveur final)

**Mais** : Grâce au HTTPS (🔒), ils voient que vous communiquez avec chatgpt.com, mais **ne peuvent pas lire le contenu** de vos conversations.

**Q4 : Enjeux de souveraineté**

Si le serveur est aux États-Unis :
- Vos données sont soumises au droit américain (CLOUD Act)
- Les autorités américaines peuvent demander l'accès aux données
- Le RGPD européen s'applique-t-il ? Comment ?

---

### Pour aller plus loin (facultatif)

#### Comparez avec d'autres services IA

Refaites l'exercice complet avec :

| Service | Nom de domaine | IP | Pays | Latence |
|---------|----------------|----|----|---------|
| ChatGPT | chatgpt.com | | | |
| Claude | claude.ai | | | |
| Gemini | gemini.google.com | | | |
| Copilot | copilot.microsoft.com | | | |
| Mistral | chat.mistral.ai | | | |

**Observation** : Lequel est le plus proche de vous ? Le plus rapide ?

---

## Conclusion de l'exercice

### Ce que vous avez appris

**Exercice 1 - Tracer le chemin vers ChatGPT** :
- ✅ Un nom de domaine cache une adresse IP
- ✅ Vos données traversent de nombreux routeurs
- ✅ La géolocalisation révèle où sont les serveurs
- ✅ HTTPS protège vos données en transit
- ✅ Cloudflare sert d'intermédiaire

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

---

## Pour aller plus loin

Consultez également **[exercice-local-vs-cloud.md](exercice-local-vs-cloud.md)** pour approfondir la différence entre traitement local et cloud.
