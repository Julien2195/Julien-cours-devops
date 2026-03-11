# SwipeImmo — Design Spec

> "Tinder de l'immobilier" — Plateforme de mise en relation immobilière entre particuliers, augmentée par la data.

## 1. Vision & Proposition de valeur

SwipeImmo est une plateforme web (PWA) de mise en relation immobilière entre particuliers en France, qui remplace l'agent immobilier par deux mécanismes intelligents :

1. **Estimation transparente** — Un algorithme basé sur les données publiques (DVF, cadastre, INSEE) et les informations du vendeur produit une estimation fiable avec fourchette de prix, explication des facteurs, comparaison avec les ventes récentes, et données d'environnement (transports, écoles, commerces, cadre de vie).

2. **Matching intelligent** — L'acheteur/locataire remplit un profil structuré intégrant ses critères classiques ET son mode de vie. L'algorithme recommande des biens pertinents et affine ses suggestions en fonction du comportement de l'utilisateur.

**Cible** : Particuliers en France — vendeurs, acheteurs et locataires.

**Positionnement** : PAP augmenté par la data. Plus fiable que LeBonCoin (estimation + matching), moins cher qu'un agent (pas de commission 5-7%).

**Objectif** : MVP pour valider l'idée et lever des fonds / entrer en incubateur.

**Équipe** : 1 développeur, 2 commerciaux. Recrutement prévu après validation.

## 2. Parcours utilisateur — Vendeur / Bailleur

### Étape 1 — Inscription & profil

Création de compte simple (email ou connexion sociale). Le vendeur indique s'il vend ou loue.

### Étape 2 — Wizard de création d'annonce

Un parcours guidé étape par étape qui remplace le travail de l'agent :

1. **Adresse** — Saisie de l'adresse, géolocalisation automatique.
2. **Caractéristiques** — Type de bien, surface, nombre de pièces, étage, extérieur, parking...
3. **État & travaux** — État général, travaux récents, diagnostics (DPE notamment).
4. **Photos** — Upload guidé avec conseils intégrés ("photographiez chaque pièce", "lumière naturelle recommandée", bonnes pratiques). Score de qualité photo pour encourager de meilleures prises.
5. **Estimation** — L'algorithme génère :
   - Prix estimé + fourchette (ex: 300k - 340k, central 320k)
   - Facteurs explicatifs (localisation, surface, état, DPE...)
   - Biens similaires vendus récemment à proximité (adresse approximative, prix, date, surface)
   - Données d'environnement (transports, écoles, commerces, cadre de vie)
   - Indice de confiance (plus il y a de transactions comparables, plus l'estimation est fiable)
6. **Fixation du prix** — Le vendeur choisit son prix. Un indicateur de cohérence s'affiche ("prix cohérent", "au-dessus du marché", "bonne affaire"). Le vendeur n'est pas obligé de suivre l'estimation.
7. **Prévisualisation & publication** — Le vendeur voit l'annonce telle que les acheteurs la verront, puis publie.

### Étape 3 — Gestion

Tableau de bord avec : statistiques de vues, messages reçus, possibilité de modifier l'annonce ou ajuster le prix.

## 3. Parcours utilisateur — Acheteur / Locataire

### Étape 1 — Inscription & onboarding structuré

Après création de compte, un questionnaire définit le profil de recherche :

- Achat ou location ?
- Budget (min/max)
- Zone géographique souhaitée (ville, rayon, ou plusieurs zones)
- Type de bien (appartement, maison, studio...)
- Surface minimum, nombre de pièces
- Critères importants (balcon, parking, calme, proximité transports, DPE...)
- Situation (premier achat, investissement, déménagement...)
- **Mode de vie** : enfants (âge, école), lieu de travail, moyen de transport, centres d'intérêt liés au cadre de vie

### Étape 2 — Feed de recommandations

L'acheteur arrive sur un feed personnalisé de biens correspondant à son profil. Pour chaque bien :

- Photos, prix, indicateur de cohérence du prix
- Caractéristiques principales
- Localisation sur carte
- Données d'environnement pertinentes pour son profil (ex: "école primaire à 200m" pour une famille)
- Score de compatibilité avec son profil

Actions possibles : **liker** (sauvegardé + signal pour l'algo), **passer**, **contacter** (ouvre la messagerie).

### Étape 3 — Apprentissage comportemental

Au fil de l'utilisation, l'algorithme affine les recommandations :

- Biens likés → plus de biens similaires
- Biens ignorés/passés → moins de biens de ce type
- Temps passé sur une annonce, critères consultés...

### Étape 4 — Mise en relation

Quand l'acheteur contacte un vendeur, une conversation s'ouvre dans la messagerie intégrée. Les deux parties échangent librement. L'app accompagne jusqu'à la mise en relation, pas au-delà.

## 4. Estimation algorithmique

### Sources de données

| Source | Données | Usage |
|--------|---------|-------|
| DVF (Demandes de Valeurs Foncières) | Historique transactions immobilières France | Socle de l'estimation |
| Cadastre | Surface parcellaire, infos foncières | Complément estimation |
| INSEE | Revenus médians, démographie, équipements | Contextualisation quartier |
| Base Adresse Nationale | Géolocalisation précise | Localisation |
| transport.data.gouv.fr (GTFS) | Stations métro, bus, tram, gare | Environnement transport |
| Base Éducation Nationale | Crèches, écoles, collèges, lycées | Environnement éducation |
| Base Permanente des Équipements (INSEE) | Commerces, services, santé | Environnement services |
| OpenStreetMap | Espaces verts, parcs | Cadre de vie |
| Carte du bruit | Niveaux sonores | Cadre de vie |
| Données vendeur | État, travaux, DPE, photos | Ajustement estimation |

### Logique d'estimation

1. Identifier les transactions DVF récentes dans un rayon autour du bien (même type, surface comparable)
2. Ajuster en fonction des caractéristiques spécifiques (état, DPE, étage, extérieur...)
3. Pondérer par les données socio-économiques du quartier (INSEE)
4. Produire : prix central, fourchette basse/haute, indice de confiance

### Transparence

- Liste des transactions comparables utilisées
- Facteurs qui influencent le prix (ex: "DPE A : +5%", "RDC sans extérieur : -8%")
- Carte des ventes récentes dans le quartier

### Limites assumées

- Zones rurales avec peu de transactions → fourchette large + indice de confiance bas
- Biens atypiques (loft, château...) → estimation moins fiable, clairement indiqué

### Données d'environnement

Chaque bien est enrichi automatiquement :

- **Transports** — Stations à proximité, temps de trajet vers un point donné
- **Éducation** — Crèches, écoles, collèges, lycées avec distance
- **Commerces & services** — Proximité supermarchés, médecins, pharmacies
- **Cadre de vie** — Espaces verts, niveau de bruit, sécurité

Ces données alimentent à la fois la fiche du bien ET le scoring de matching.

## 5. Matching intelligent

### Critères de scoring

Le matching ne se limite pas à "3 pièces, 300k, Paris 11e". Il intègre :

- **Critères classiques** : budget, surface, type, localisation → filtre binaire
- **Mode de vie** : enfants, lieu de travail, transport → scoring pondéré via données d'environnement
- **Comportement** : biens likés, ignorés, temps passé → ajustement progressif des poids

### Exemple

Un acheteur avec 2 enfants en primaire, travaillant à La Défense, sans voiture :
→ Un appartement à 5 min du RER A, avec une école à 200m, sera mieux scoré qu'un bien identique sans ces critères, même à prix équivalent.

## 6. Business model — Freemium

### Gratuit

- Création de compte, profil, recherche
- Publication d'une annonce (avec estimation + données d'environnement)
- Messagerie intégrée
- Recommandations personnalisées

### Options payantes — Vendeurs

| Option | Description | Modèle |
|--------|-------------|--------|
| Boost de visibilité | Annonce en priorité dans les feeds compatibles | Ponctuel (ex: 4,99€ / 7 jours) |
| Annonce premium | Badge vérifié, mise en avant visuelle, statistiques détaillées | Ponctuel |

### Options payantes — Acheteurs

| Option | Description | Modèle |
|--------|-------------|--------|
| Alertes prioritaires | Notifié en premier sur les nouveaux biens matching | Ponctuel |
| Profil certifié | Vérification solvabilité, badge confiance | Ponctuel |

### Monétisation future (post-levée)

- Partenariats notaires, courtiers, déménageurs (apport d'affaires)
- Services d'accompagnement à la transaction
- Version pro pour agences indépendantes

## 7. Périmètre du MVP

### Inclus

**Vendeur / Bailleur**
- Inscription / connexion
- Wizard de création d'annonce guidé
- Estimation algorithmique transparente
- Fixation du prix avec indicateur de cohérence
- Guidage photo intégré
- Tableau de bord (vues, messages)

**Acheteur / Locataire**
- Inscription / connexion
- Onboarding profil de recherche (critères + mode de vie)
- Feed de biens recommandés avec score de compatibilité
- Données d'environnement par bien
- Like / passer / contacter
- Apprentissage comportemental

**Commun**
- Messagerie intégrée
- Notifications (nouveau match, nouveau message)
- Options payantes (boost, premium, alertes, profil certifié)

### Hors MVP

- Réseau de photographes partenaires
- Accompagnement à la transaction (notaire, juridique)
- App mobile native (PWA suffit)
- Version pro pour agences

## 8. KPIs

### North Star Metric

**Nombre de mises en relation qualifiées** (un acheteur contacte un vendeur via la plateforme).

### Acquisition

- Nombre d'inscriptions (vendeurs vs acheteurs)
- Taux de complétion du wizard vendeur
- Taux de complétion de l'onboarding acheteur

### Engagement

- Nombre d'annonces publiées
- Nombre de biens likés / contactés par acheteur
- Fréquence de retour sur l'app
- Taux d'ouverture des conversations en messagerie

### Qualité du matching

- Taux de contact après recommandation
- Pertinence perçue (feedback utilisateur)

### Estimation

- Écart entre estimation et prix final de vente
- Taux de vendeurs qui suivent l'estimation vs écart important

### Monétisation

- Taux de conversion gratuit → payant
- Revenu moyen par utilisateur payant
- Options les plus achetées

## 9. Risques & réponses

| Risque | Réponse |
|--------|---------|
| LeBonCoin / SeLoger existent déjà | Ils sont des marketplaces passives. SwipeImmo est un moteur de matching actif avec estimation transparente. |
| Fiabilité de l'estimation | Basée sur DVF (transactions réelles). Indice de confiance affiché honnêtement. Transparence des facteurs crée la confiance. |
| Masse critique (poule et œuf) | Lancement ciblé 2-3 villes. L'estimation gratuite est un aimant à vendeurs même sans acheteurs. |
| Réglementation | Pas de commission = pas de carte pro. Outil de mise en relation. Vigilance RGPD, encadrement loyers, DPE obligatoire. |
| Équipe réduite (1 dev) | PWA + stack standard = recrutement facile post-levée. MVP scopé pour un dev. |
