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

Création de compte simple (email ou connexion sociale). Le vendeur indique s'il vend (Phase 1) ou loue (Phase 3).

### Étape 2 — Wizard de création d'annonce

Un parcours guidé étape par étape qui remplace le travail de l'agent :

1. **Adresse** — Saisie de l'adresse, géolocalisation automatique.
2. **Caractéristiques** — Type de bien, surface, nombre de pièces, étage, extérieur, parking...
3. **État & travaux** — État général, travaux récents, diagnostics (DPE notamment).
4. **Photos** — Upload guidé avec conseils intégrés ("photographiez chaque pièce", "lumière naturelle recommandée", bonnes pratiques).
5. **Estimation** — L'algorithme génère :
   - Prix estimé + fourchette (ex: 300k - 340k, central 320k)
   - Facteurs explicatifs (localisation, surface, état, DPE...)
   - Biens similaires vendus récemment à proximité (adresse approximative, prix, date, surface)
   - Données d'environnement (transports, écoles, commerces, cadre de vie)
   - Indice de confiance (plus il y a de transactions comparables, plus l'estimation est fiable)
6. **Fixation du prix** — Le vendeur choisit son prix. Un indicateur de cohérence s'affiche ("prix cohérent", "au-dessus du marché", "bonne affaire"). Le vendeur n'est pas obligé de suivre l'estimation.
7. **Prévisualisation & publication** — Le vendeur voit l'annonce telle que les acheteurs la verront, puis publie.

**Spécificités location** : Le wizard inclut des champs supplémentaires pour la location — meublé/non meublé, type de bail, charges comprises ou non, dépôt de garantie. L'estimation intègre l'encadrement des loyers dans les zones concernées et alerte le bailleur si son prix dépasse le plafond légal.

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

**Spécificités location** : critères supplémentaires — meublé/non meublé, durée souhaitée, colocation, animaux acceptés.

### Étape 2 — Feed de recommandations

L'interface reprend le principe du swipe : les biens sont présentés **un par un en plein écran** (type carte Tinder), avec swipe droite pour liker, swipe gauche pour passer, et un bouton pour contacter directement. Ce format force l'attention sur chaque bien et génère des signaux clairs pour l'algorithme.

Pour chaque bien affiché :

- Photos (carousel swipeable), prix, indicateur de cohérence du prix
- Caractéristiques principales
- Localisation sur carte
- Données d'environnement pertinentes pour son profil (ex: "école primaire à 200m" pour une famille)
- Score de compatibilité avec son profil

Un **mode liste** est aussi disponible pour les utilisateurs qui préfèrent parcourir plusieurs biens rapidement.

### Étape 3 — Apprentissage comportemental

Au fil de l'utilisation, l'algorithme affine les recommandations :

- Biens likés → plus de biens similaires
- Biens ignorés/passés → moins de biens de ce type
- Temps passé sur une annonce, critères consultés...

L'utilisateur voit l'impact : un bandeau discret "Recommandations mises à jour" quand l'algo ajuste significativement le feed. Il peut aussi consulter et modifier ses préférences détectées dans les paramètres (ex: "Vous semblez préférer les biens avec extérieur" — avec possibilité de confirmer ou rejeter).

### Étape 4 — Mise en relation

Quand l'acheteur contacte un vendeur, une conversation s'ouvre dans la messagerie intégrée. Les deux parties échangent librement — texte, partage de documents (diagnostics, plans). La messagerie reste ouverte sans limitation de durée. L'app n'intervient pas dans la suite de la transaction (visites, négociation, notaire).

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

### Personas

**Persona 1 — Famille qui achète** : Couple avec 2 enfants en primaire, travaillant à La Défense, sans voiture. Cherche un 4 pièces en banlieue ouest. → Le matching priorise la proximité RER A, les écoles à distance piétonne, et les commerces de proximité. Un bien à Saint-Germain-en-Laye avec école à 200m et gare à 10 min sera mieux classé qu'un bien identique à Massy sans transports directs.

**Persona 2 — Jeune actif qui loue** : Développeur de 28 ans, travaille en remote, budget 800-1000€/mois. Cherche un studio/T2 à Lyon. → Le matching priorise le calme, la fibre, les espaces verts, les cafés/coworking à proximité. Moins de poids sur les transports (remote).

**Persona 3 — Investisseur** : Cadre qui achète un studio pour du locatif. Budget 150-200k, rendement visé. → Le matching priorise le prix au m² par rapport au quartier, la tension locative (demande vs offre dans la zone), et la rentabilité estimée.

## 6. Business model — Freemium

### Gratuit

- Création de compte, profil, recherche
- Publication d'une annonce (avec estimation + données d'environnement)
- Messagerie intégrée
- Recommandations personnalisées

### Options payantes — Vendeurs

| Option | Description | Prix indicatif |
|--------|-------------|----------------|
| Boost de visibilité | Annonce en priorité dans les feeds compatibles pendant 7 jours | ~4,99€ |
| Annonce premium | Badge vérifié, mise en avant visuelle, statistiques détaillées (vues, profil des visiteurs) | ~9,99€ |

### Options payantes — Acheteurs

| Option | Description | Prix indicatif |
|--------|-------------|----------------|
| Alertes prioritaires | Notifié en premier (24h d'avance) sur les nouveaux biens matching | ~2,99€/mois |
| Profil certifié | L'acheteur uploade une attestation bancaire ou simulation de prêt ; SwipeImmo vérifie le document et attribue un badge "solvabilité vérifiée" visible par les vendeurs | ~4,99€ |

*Les prix sont indicatifs et seront ajustés en fonction des tests A/B sur le MVP.*

### Scénario de revenus (hypothèse prudente)

Avec 1 000 annonces actives et 5 000 acheteurs inscrits :
- 10% de vendeurs prennent un boost → 100 × 4,99€ = ~500€/mois
- 5% de vendeurs prennent premium → 50 × 9,99€ = ~500€/mois
- 3% d'acheteurs prennent alertes → 150 × 2,99€ = ~450€/mois
- 5% d'acheteurs certifient leur profil → 250 × 4,99€ = ~1 250€/mois (one-shot)

→ ~1 450€/mois récurrent (boosts + premium + alertes) + ~1 250€ en one-shots (profils certifiés). Modeste, mais démontre le mécanisme. La croissance vient du volume.

### Monétisation future (post-levée)

- Partenariats notaires, courtiers, déménageurs (apport d'affaires)
- Services d'accompagnement à la transaction
- Version pro pour agences indépendantes

## 7. Taille du marché

**TAM (Total Addressable Market)** : ~1,1 million de transactions immobilières/an en France (dont ~700k dans l'ancien). Valeur totale des transactions : ~250 Mds€/an.

**SAM (Serviceable Addressable Market)** : ~30% des transactions se font déjà entre particuliers (PAP), soit ~210k transactions/an. Avec l'ajout de la location (~1,5M de déménagements/an), le marché adressable est considérable.

**SOM (Serviceable Obtainable Market)** : Objectif Year 1 post-MVP : capter 0,05% du marché C2C vente sur 2-3 villes → ~100-200 transactions facilitées, soit une preuve de traction suffisante pour une Série Seed.

## 8. Levée de fonds

**Montant visé** : Pré-seed / Seed de 200-400k€

**Utilisation des fonds** :
- Recrutement de 1-2 développeurs supplémentaires
- Budget marketing digital (SEO, social, acquisition)
- Infrastructure données (hébergement, pipelines)
- Trésorerie 12-18 mois de runway

**Jalons de la levée** : Le MVP validé (objectifs Section 11 atteints) constitue le signal pour déclencher la levée.

## 9. Analyse concurrentielle

| Acteur | Estimation | Matching | C2C pur | Modèle |
|--------|-----------|----------|---------|--------|
| **LeBonCoin** | Non | Filtres basiques | Oui | Annonces payantes |
| **SeLoger** | Non | Filtres + alertes | Non (pros) | Abonnement agences |
| **PAP** | Non | Filtres | Oui | Abonnement vendeur |
| **MeilleursAgents** | Oui (référence) | Non (pas de marketplace) | N/A | Leads pour agences |
| **Hosman / Proprioo** | Oui | Non | Hybride (agent low-cost) | Commission réduite (~3%) |
| **SwipeImmo** | **Oui, transparente** | **Oui, intelligent + comportemental** | **Oui** | **Freemium** |

**Différenciation clé** : Aucun acteur ne combine estimation transparente + matching intelligent + C2C pur. MeilleursAgents fait l'estimation mais ne vend pas. LeBonCoin vend mais n'estime pas et ne matche pas. Hosman/Proprioo gardent un agent dans la boucle.

## 10. Périmètre du MVP — Phasage

Le MVP est découpé en 3 phases pour rester réaliste avec 1 développeur :

### Phase 1 — Fondations : estimation + annonces (~8-10 semaines)

- Inscription / connexion (vendeur + acheteur)
- Wizard de création d'annonce guidé (vente uniquement en Phase 1)
- Pipeline de données : DVF + cadastre + INSEE + Base Adresse Nationale
- Estimation algorithmique transparente (fourchette, facteurs, comparables)
- Fixation du prix avec indicateur de cohérence
- Guidage photo intégré
- Pages d'annonces publiques consultables

*La location est introduite en Phase 3 pour ne pas complexifier le lancement.*

### Phase 2 — Matching + interaction (~6-8 semaines)

- Onboarding profil acheteur (critères + mode de vie)
- Enrichissement environnement (transports, écoles, commerces, cadre de vie)
- Feed de recommandations avec swipe (+ mode liste)
- Score de compatibilité
- Like / passer / contacter
- Messagerie intégrée
- Notifications (nouveau match, nouveau message)
- Apprentissage comportemental basique (likes/passes)

### Phase 3 — Monétisation + location (~4-6 semaines)

- Boost de visibilité (paiement intégré)
- Annonce premium
- Alertes prioritaires acheteur
- Profil certifié acheteur (upload attestation + vérification — après consultation juridique sur les obligations réglementaires liées à la manipulation de documents financiers)
- Tableau de bord vendeur (statistiques détaillées)
- Ouverture à la location : champs spécifiques (meublé/bail/charges), encadrement des loyers, critères locataire

**Planning prévisionnel** : Phase 1 opérationnelle ~3 mois après le démarrage, MVP complet (Phase 3) ~6 mois. Les commerciaux activent l'acquisition vendeurs dès la fin de Phase 1.

### Hors MVP

- Réseau de photographes partenaires
- Accompagnement à la transaction (notaire, juridique)
- App mobile native (PWA suffit)
- Version pro pour agences

## 11. Go-to-market

### Stratégie de lancement

**Villes cibles** : 2-3 métropoles à forte tension immobilière (ex: Lyon, Bordeaux, Nantes). Le choix final dépend du réseau des 2 commerciaux sur le terrain.

**Acquisition vendeurs (priorité)** — C'est l'offre qui attire la demande :
- L'estimation gratuite est l'aimant principal — un propriétaire peut estimer son bien sans engagement
- Les commerciaux démarchent en direct : agences en mandat simple, vendeurs PAP sur LeBonCoin/PAP
- Présence sur les réseaux sociaux locaux (groupes Facebook immobilier, forums ville)

**Acquisition acheteurs** — Suit naturellement l'offre :
- SEO sur "estimation immobilière [ville]", "acheter sans agence [ville]"
- Partage social des fiches bien (données d'environnement = contenu partageable)
- Bouche-à-oreille stimulé par la qualité du matching

**Objectif masse critique par ville** : ~100 annonces actives pour que le matching ait du sens pour un acheteur.

## 12. KPIs & Objectifs de validation

### North Star Metric

**Nombre de mises en relation qualifiées** (un acheteur contacte un vendeur via la plateforme).

### Objectifs de validation du MVP (6 mois post-lancement)

| Métrique | Objectif | Validation |
|----------|----------|------------|
| Annonces publiées | 200+ | L'outil d'estimation attire les vendeurs |
| Acheteurs inscrits | 1 000+ | Le matching attire les acheteurs |
| Mises en relation | 100+ | Le produit crée de la valeur |
| Taux complétion wizard | > 60% | Le parcours vendeur est fluide |
| Taux conversion payant | > 5% | Le modèle économique fonctionne |
| Retour utilisateur (NPS) | > 30 | Le produit plaît |

Si ces objectifs sont atteints → signal fort pour lever des fonds / entrer en incubateur.

### Métriques de suivi

**Acquisition** : inscriptions (vendeurs vs acheteurs), taux de complétion wizard/onboarding

**Engagement** : annonces publiées, biens likés/contactés par acheteur, fréquence de retour, taux d'ouverture conversations

**Qualité matching** : taux de contact après recommandation, pertinence perçue (feedback)

**Estimation** : écart estimation vs prix final (objectif : estimation médiane à moins de 10% du prix de vente final), taux de vendeurs suivant l'estimation

**Monétisation** : conversion gratuit → payant, ARPU, options les plus achetées

## 13. Risques & réponses

| Risque | Réponse |
|--------|---------|
| LeBonCoin / SeLoger existent déjà | Ils sont des marketplaces passives. SwipeImmo est un moteur de matching actif avec estimation transparente. Voir analyse concurrentielle. |
| Fiabilité de l'estimation | Basée sur DVF (transactions réelles). Indice de confiance affiché honnêtement. Transparence des facteurs crée la confiance. |
| Masse critique (poule et œuf) | Lancement ciblé 2-3 villes. L'estimation gratuite est un aimant à vendeurs même sans acheteurs. Objectif : 100 annonces/ville avant push acheteurs. |
| Réglementation | Pas de commission = pas de carte pro. Outil de mise en relation. Vigilance RGPD, encadrement loyers, DPE obligatoire. |
| Équipe réduite (1 dev) | MVP phasé en 3 étapes réalistes. PWA + stack standard = recrutement facile post-levée. |
| MeilleursAgents fait déjà l'estimation | MeilleursAgents vend des leads aux agences. SwipeImmo est C2C et intègre l'estimation dans un parcours complet de mise en relation. Pas le même produit. |
