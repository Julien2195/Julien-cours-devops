# SwipeImmo

> Le Tinder de l'immobilier — Acheter, vendre ou louer entre particuliers, sans agent, grâce à la puissance des données.

---

## 1. Le concept

Aujourd'hui, pour vendre ou acheter un bien immobilier, on a deux options :
- **Passer par un agent** : cher (5 à 7% de commission), et on dépend de son expertise pour fixer le prix.
- **Se débrouiller seul** (LeBonCoin, PAP) : gratuit ou peu cher, mais on est livré à soi-même — comment fixer le bon prix ? Comment trouver le bon acheteur parmi des centaines d'annonces ?

**SwipeImmo propose une troisième voie** : une plateforme entre particuliers, où la technologie remplace l'agent immobilier grâce à deux innovations :

1. **Une estimation intelligente et transparente** — Le vendeur entre les informations de son bien, et la plateforme calcule un prix juste à partir des ventes réelles du quartier, des données publiques, et de l'environnement (transports, écoles, commerces...). Pas de boîte noire : le vendeur voit exactement pourquoi on lui propose ce prix.

2. **Des recommandations sur-mesure** — L'acheteur ne parcourt pas des centaines d'annonces. Il décrit ce qu'il cherche — y compris son mode de vie (enfants, lieu de travail, besoin de transports...) — et la plateforme lui propose uniquement les biens qui lui correspondent vraiment. Plus il utilise l'application, plus les suggestions s'affinent.

**Pour qui ?** Tous les particuliers en France qui veulent vendre, acheter ou louer.

**L'objectif** : Construire une première version fonctionnelle pour prouver que le concept marche, puis lever des fonds ou intégrer un incubateur pour accélérer.

**L'équipe** : 1 développeur, 2 commerciaux. Recrutement prévu après la première levée.

---

## 2. Comment ça marche pour le vendeur ?

### Créer son compte

Inscription rapide par email ou via Google/Apple. Le vendeur indique s'il souhaite vendre (disponible dès le lancement) ou louer (disponible dans un second temps).

### Publier son annonce — un parcours guidé pas à pas

La plateforme accompagne le vendeur à chaque étape, comme le ferait un bon agent :

1. **L'adresse** — Le vendeur saisit son adresse, la plateforme la localise automatiquement sur la carte.

2. **Les caractéristiques du bien** — Type (appartement, maison...), surface, nombre de pièces, étage, extérieur, parking, cave...

3. **L'état du bien** — État général, travaux récents, performance énergétique (DPE), diagnostics.

4. **Les photos** — La plateforme guide le vendeur pour prendre de bonnes photos : "Photographiez le salon depuis l'entrée", "Préférez la lumière naturelle", "Montrez chaque pièce". Des conseils concrets pour obtenir des photos de qualité sans photographe professionnel.

5. **L'estimation** — C'est le moment clé. La plateforme analyse les données et affiche :
   - Un **prix estimé** avec une fourchette (ex: entre 300 000€ et 340 000€, estimation centrale à 320 000€)
   - Les **raisons** qui expliquent ce prix : localisation, surface, état, performance énergétique...
   - Les **ventes récentes comparables** à proximité : adresse approximative, prix, date, surface
   - L'**environnement** du bien : transports, écoles, commerces, espaces verts
   - Un **indice de fiabilité** : plus il y a eu de ventes similaires récemment dans le quartier, plus l'estimation est précise

6. **Le choix du prix** — Le vendeur fixe librement son prix de vente. La plateforme affiche un indicateur visible par les acheteurs : "Prix cohérent avec le marché", "Au-dessus du marché" ou "Bonne affaire". Le vendeur n'est jamais obligé de suivre l'estimation.

7. **Vérification et publication** — Le vendeur prévisualise son annonce telle que les acheteurs la verront, puis la publie en un clic.

**Pour la location** (disponible en Phase 3) : des champs supplémentaires sont prévus — meublé ou non, type de bail, charges, dépôt de garantie. L'estimation intègre l'encadrement des loyers dans les villes concernées et prévient le bailleur si son prix dépasse le plafond légal.

### Suivre son annonce

Le vendeur dispose d'un tableau de bord avec le nombre de vues, les messages reçus, et la possibilité de modifier son annonce ou ajuster son prix à tout moment.

---

## 3. Comment ça marche pour l'acheteur ?

### Créer son profil de recherche

Après inscription, l'acheteur répond à un questionnaire qui va bien au-delà des filtres classiques :

- Achat ou location ?
- Budget (minimum et maximum)
- Zone géographique souhaitée (une ville, un rayon, ou plusieurs zones)
- Type de bien (appartement, maison, studio...)
- Surface minimum, nombre de pièces
- Critères importants (balcon, parking, calme, proximité transports, bonne performance énergétique...)
- Situation (premier achat, investissement, déménagement...)
- **Mode de vie** — C'est ce qui fait la différence : nombre et âge des enfants, lieu de travail, moyen de transport habituel, centres d'intérêt liés au cadre de vie

Pour la location : critères supplémentaires comme meublé/non meublé, durée souhaitée, colocation, animaux acceptés.

### Découvrir des biens — le principe du swipe

L'acheteur découvre les biens **un par un, en plein écran**, comme sur Tinder :
- **Glisser à droite** pour aimer un bien (il est sauvegardé et l'application en prend note)
- **Glisser à gauche** pour passer au suivant
- **Bouton "Contacter"** pour écrire directement au vendeur

Chaque fiche affiche :
- Les photos (que l'on peut faire défiler), le prix, et l'indicateur de cohérence du prix
- Les caractéristiques principales
- La localisation sur une carte
- Les informations d'environnement **personnalisées** selon le profil (ex: "École primaire à 200m" pour une famille, "Station de métro à 5 min" pour quelqu'un sans voiture)
- Un **score de compatibilité** avec le profil de l'acheteur

Un **mode liste** est aussi disponible pour ceux qui préfèrent voir plusieurs biens d'un coup.

### Des recommandations qui s'améliorent avec le temps

Plus l'acheteur utilise la plateforme, plus les suggestions deviennent pertinentes :
- Les biens aimés orientent vers des biens similaires
- Les biens passés réduisent ce type de propositions
- Le temps passé sur une annonce et les critères consultés sont aussi pris en compte

L'acheteur voit quand ses recommandations sont mises à jour, et peut consulter les préférences détectées dans ses paramètres (ex: "Vous semblez préférer les biens avec extérieur") avec la possibilité de confirmer ou rejeter chaque préférence.

### Contacter le vendeur

Quand un bien plaît, l'acheteur ouvre une conversation par messagerie directement dans la plateforme. Les deux parties échangent librement — texte, partage de documents (diagnostics, plans...). La messagerie reste ouverte sans limite de durée. La plateforme n'intervient pas dans la suite (visites, négociation, notaire).

---

## 4. L'estimation : comment ça fonctionne ?

### Les données utilisées

L'estimation repose sur des **données publiques et gratuites**, complétées par les informations du vendeur :

| Source | Ce qu'elle apporte |
|--------|--------------------|
| Registre des ventes immobilières (DVF) | Toutes les transactions réelles en France — le socle de l'estimation |
| Cadastre | Surfaces parcellaires, informations foncières |
| INSEE | Revenus du quartier, démographie, équipements |
| Base Adresse Nationale | Localisation précise |
| Données transports (transport.data.gouv.fr) | Métro, bus, tram, gares à proximité |
| Annuaire Éducation Nationale | Crèches, écoles, collèges, lycées |
| Base des Équipements (INSEE) | Commerces, médecins, pharmacies |
| OpenStreetMap | Parcs, espaces verts |
| Carte du bruit | Niveaux sonores |
| Informations du vendeur | État du bien, travaux, DPE, photos |

### Comment le prix est calculé

1. On identifie les **ventes récentes similaires** autour du bien (même type, surface comparable)
2. On ajuste selon les **spécificités du bien** (état, performance énergétique, étage, extérieur...)
3. On prend en compte le **contexte du quartier** (revenus, dynamisme, équipements)
4. On produit un **prix central**, une **fourchette basse et haute**, et un **indice de fiabilité**

### Ce que le vendeur voit

- La liste des ventes comparables utilisées pour le calcul
- Les facteurs qui tirent le prix vers le haut ou vers le bas (ex: "Bonne performance énergétique : +5%", "Rez-de-chaussée sans extérieur : -8%")
- Une carte des ventes récentes dans le quartier

### Les limites, assumées en toute honnêteté

- En zone rurale avec peu de ventes récentes → la fourchette sera plus large et l'indice de fiabilité plus bas
- Pour les biens atypiques (loft, château, bien d'exception) → l'estimation sera moins précise, et c'est clairement indiqué

### L'environnement du bien

Chaque annonce est automatiquement enrichie avec les données de proximité :

- **Transports** — Stations à proximité, temps de trajet vers un point donné
- **Éducation** — Crèches, écoles, collèges, lycées avec la distance
- **Commerces et services** — Supermarchés, médecins, pharmacies
- **Cadre de vie** — Espaces verts, niveau de bruit

Ces informations sont visibles sur la fiche du bien ET utilisées pour affiner les recommandations aux acheteurs.

---

## 5. Le matching : pourquoi c'est différent

### Au-delà des filtres classiques

Sur LeBonCoin, on filtre par prix, surface et ville. On obtient des centaines de résultats à trier soi-même. SwipeImmo va plus loin :

- **Critères classiques** (budget, surface, type, localisation) → utilisés pour éliminer les biens hors sujet
- **Mode de vie** (enfants, lieu de travail, transport) → utilisés pour classer les biens restants par pertinence, grâce aux données d'environnement
- **Comportement** (biens aimés, ignorés, temps passé) → utilisés pour affiner progressivement les recommandations

### Trois exemples concrets

**Sophie et Marc — une famille qui achète**
Couple avec 2 enfants en primaire. Marc travaille à La Défense, pas de voiture. Cherchent un 4 pièces en banlieue ouest.
→ La plateforme priorise les biens proches du RER A, avec des écoles à distance à pied et des commerces de proximité. Un appartement à Saint-Germain-en-Laye avec une école à 200m et une gare à 10 min sera mieux classé qu'un bien identique à Massy, sans transport direct vers La Défense.

**Lucas — un jeune actif qui loue**
28 ans, travaille depuis chez lui, budget 800-1000€/mois. Cherche un studio ou T2 à Lyon.
→ La plateforme priorise le calme, les espaces verts, les cafés et espaces de coworking à proximité. Les transports en commun comptent moins puisqu'il travaille à distance.

**Catherine — une investisseuse**
Cadre qui achète un studio pour le louer. Budget 150-200k, objectif rentabilité.
→ La plateforme priorise le prix au m² par rapport au quartier, la forte demande locative dans la zone, et la rentabilité estimée.

---

## 6. Le modèle économique

### Ce qui est gratuit

- Créer un compte, publier une annonce, recevoir une estimation
- Envoyer et recevoir des messages
- Recevoir des recommandations personnalisées

### Les options payantes — Vendeurs

| Option | Ce que ça fait | Prix indicatif |
|--------|----------------|----------------|
| Mise en avant | L'annonce apparaît en priorité auprès des acheteurs compatibles pendant 7 jours | ~4,99€ |
| Annonce premium | Badge "vérifié", mise en avant visuelle, statistiques détaillées (nombre de vues, profil des visiteurs) | ~9,99€ |

### Les options payantes — Acheteurs

| Option | Ce que ça fait | Prix indicatif |
|--------|----------------|----------------|
| Alertes prioritaires | Être prévenu en premier (24h d'avance) quand un bien correspondant apparaît | ~2,99€/mois |
| Profil certifié | L'acheteur transmet une attestation bancaire ou une simulation de prêt. SwipeImmo vérifie le document et attribue un badge "solvabilité vérifiée" visible par les vendeurs, ce qui rassure et donne un avantage | ~4,99€ |

*Les prix seront ajustés après les premiers retours utilisateurs.*

### Projection de revenus (hypothèse prudente)

Avec 1 000 annonces actives et 5 000 acheteurs inscrits :
- 10% des vendeurs prennent la mise en avant → ~500€/mois
- 5% des vendeurs prennent premium → ~500€/mois
- 3% des acheteurs prennent les alertes prioritaires → ~450€/mois
- 5% des acheteurs certifient leur profil → ~1 250€ (paiement unique)

→ **~1 450€/mois de revenus récurrents + ~1 250€ ponctuels.** Modeste au démarrage, mais le mécanisme de monétisation est prouvé. La croissance vient du volume d'utilisateurs.

### Et après ? (post-levée de fonds)

- Partenariats avec des notaires, courtiers, déménageurs (apport de clients)
- Services d'accompagnement à la transaction
- Version professionnelle pour les agences indépendantes

---

## 7. La taille du marché

**Marché total** : ~1,1 million de transactions immobilières par an en France (dont ~700 000 dans l'ancien), pour une valeur totale de ~250 milliards d'euros par an.

**Marché accessible** : ~30% des transactions se font déjà entre particuliers, soit ~210 000 transactions par an. En ajoutant la location (~1,5 million de déménagements par an), le marché adressable est considérable.

**Objectif réaliste la première année** : Capter 0,05% du marché de la vente entre particuliers sur 2-3 villes → ~100-200 transactions facilitées. C'est suffisant comme preuve de traction pour une levée de fonds.

---

## 8. La levée de fonds

**Montant visé** : 200 000 à 400 000€ (pré-seed / seed)

**À quoi serviront les fonds :**
- Recruter 1 à 2 développeurs supplémentaires
- Budget marketing (référencement, réseaux sociaux, acquisition)
- Infrastructure et hébergement
- Trésorerie pour 12 à 18 mois de fonctionnement

**Quand ?** La levée sera déclenchée une fois la première version validée (objectifs de la Section 12 atteints).

---

## 9. Face à la concurrence

| Acteur | Estimation du prix | Recommandations intelligentes | Entre particuliers | Modèle |
|--------|-------------------|------------------------------|-------------------|--------|
| **LeBonCoin** | Non | Filtres basiques | Oui | Annonces payantes |
| **SeLoger** | Non | Filtres + alertes | Non (réservé aux pros) | Abonnement agences |
| **PAP** | Non | Filtres | Oui | Abonnement vendeur |
| **MeilleursAgents** | Oui (référence) | Non (pas de vente) | — | Vente de contacts aux agences |
| **Hosman / Proprioo** | Oui | Non | Hybride (agent à prix réduit) | Commission réduite (~3%) |
| **SwipeImmo** | **Oui, transparente** | **Oui, personnalisées** | **Oui** | **Gratuit + options payantes** |

**Ce qui nous distingue** : Aucun acteur ne combine les trois — estimation transparente + recommandations intelligentes + vente entre particuliers. MeilleursAgents estime mais ne vend pas. LeBonCoin vend mais n'estime pas et ne recommande pas. Hosman et Proprioo gardent un agent dans la boucle (et prennent une commission).

---

## 10. Le plan de construction — 3 phases

Le produit est construit en 3 étapes, réalistes pour un développeur seul :

### Phase 1 — Les fondations : estimation + annonces (~2-3 mois)

- Inscription et connexion
- Parcours guidé de création d'annonce (vente uniquement au départ)
- Intégration des données publiques (ventes, cadastre, statistiques)
- Estimation transparente (fourchette, explications, comparaisons)
- Choix du prix avec indicateur de cohérence
- Guide photo intégré
- Pages d'annonces consultables par tous

*La location arrive en Phase 3 pour ne pas complexifier le lancement.*

### Phase 2 — Les recommandations + la messagerie (~6-8 semaines)

- Questionnaire de profil acheteur (critères + mode de vie)
- Enrichissement des annonces avec les données d'environnement
- Interface de découverte par swipe (+ mode liste)
- Score de compatibilité sur chaque bien
- Aimer / passer / contacter
- Messagerie intégrée
- Notifications (nouveau bien compatible, nouveau message)
- Recommandations qui s'améliorent avec l'usage

### Phase 3 — La monétisation + la location (~4-6 semaines)

- Mise en avant et annonce premium (paiement intégré)
- Alertes prioritaires pour les acheteurs
- Profil certifié pour les acheteurs (après vérification des obligations légales liées à la manipulation de documents financiers)
- Tableau de bord vendeur avec statistiques détaillées
- Ouverture à la location : champs spécifiques (meublé, bail, charges), respect de l'encadrement des loyers, critères locataire

**Calendrier prévisionnel** : Phase 1 opérationnelle ~3 mois après le démarrage. Produit complet ~6 mois. Les commerciaux commencent à recruter des vendeurs dès la fin de la Phase 1.

### Ce qui n'est pas prévu pour cette version

- Réseau de photographes professionnels
- Accompagnement juridique ou notarial
- Application mobile dédiée (le site web fonctionne très bien sur mobile)
- Version pour les agences immobilières

---

## 11. La stratégie de lancement

### Les villes cibles

2 à 3 métropoles à forte demande immobilière (ex: Lyon, Bordeaux, Nantes). Le choix final dépend du réseau des deux commerciaux sur le terrain.

### Attirer les vendeurs d'abord — c'est la clé

C'est l'offre qui attire la demande. Sans annonces, pas d'acheteurs.

- **L'estimation gratuite est l'aimant principal** — un propriétaire peut estimer son bien gratuitement, sans engagement. Même s'il ne publie pas tout de suite, il découvre la plateforme.
- **Les commerciaux activent le terrain** — démarchage direct auprès de vendeurs qui publient déjà sur LeBonCoin ou PAP.
- **Réseaux sociaux locaux** — présence dans les groupes Facebook immobilier, forums locaux.

### Attirer les acheteurs ensuite

- Référencement naturel sur des recherches comme "estimation immobilière Lyon" ou "acheter sans agence Bordeaux"
- Les fiches bien enrichies (environnement, transports, écoles) sont du contenu facilement partageable
- Le bouche-à-oreille, porté par la qualité des recommandations

**Objectif par ville** : ~100 annonces actives pour que les recommandations aient du sens pour un acheteur.

---

## 12. Les indicateurs de succès

### L'indicateur principal

**Le nombre de mises en relation réussies** — un acheteur contacte un vendeur via la plateforme.

### Les objectifs à 6 mois après le lancement

| Ce qu'on mesure | Objectif | Ce que ça prouve |
|-----------------|----------|------------------|
| Annonces publiées | 200+ | L'estimation attire les vendeurs |
| Acheteurs inscrits | 1 000+ | Les recommandations attirent les acheteurs |
| Mises en relation | 100+ | La plateforme crée de la valeur |
| Vendeurs qui vont au bout du parcours | > 60% | Le parcours est clair et fluide |
| Acheteurs qui passent à une option payante | > 5% | Le modèle économique fonctionne |
| Satisfaction utilisateur (NPS) | > 30 | Le produit plaît |

**Si ces objectifs sont atteints → feu vert pour la levée de fonds.**

### Les autres métriques suivies

- **Acquisition** : inscriptions vendeurs vs acheteurs, taux de complétion des parcours
- **Engagement** : annonces publiées, biens aimés/contactés par acheteur, fréquence de retour, conversations ouvertes
- **Qualité des recommandations** : taux de contact après une recommandation, retours utilisateurs
- **Précision de l'estimation** : écart entre l'estimation et le prix de vente final (objectif : moins de 10% d'écart en médiane)
- **Monétisation** : taux de passage au payant, revenu moyen par utilisateur payant, options les plus populaires

---

## 13. Les risques et nos réponses

| Le risque | Notre réponse |
|-----------|---------------|
| "LeBonCoin et SeLoger existent déjà" | Ce sont des vitrines passives — l'utilisateur cherche, trie, se noie. SwipeImmo recommande activement les bons biens aux bonnes personnes, avec une estimation transparente en plus. |
| "L'estimation sera-t-elle fiable ?" | Elle repose sur les ventes réelles (données publiques), pas sur des estimations d'estimations. L'indice de fiabilité est affiché honnêtement. La transparence (montrer les raisons et les ventes comparables) crée la confiance, même quand la fourchette est large. |
| "Comment atteindre la masse critique ?" | Lancement ciblé sur 2-3 villes. L'estimation gratuite attire des vendeurs même sans acheteurs sur la plateforme. Objectif : 100 annonces par ville avant de pousser l'acquisition acheteurs. |
| "Et la réglementation ?" | Pas de commission sur les ventes = pas besoin de carte professionnelle d'agent immobilier. SwipeImmo est un outil de mise en relation (comme LeBonCoin). Points de vigilance : protection des données personnelles, encadrement des loyers, affichage du DPE obligatoire. |
| "Une équipe de 3 personnes, c'est suffisant ?" | Le produit est construit en 3 phases réalistes pour un développeur. La technologie utilisée est standard, ce qui facilite le recrutement après la levée. |
| "MeilleursAgents fait déjà l'estimation" | MeilleursAgents revend les contacts aux agences immobilières. SwipeImmo est entre particuliers et intègre l'estimation dans un parcours complet de recherche et de mise en relation. Ce n'est pas le même produit, ni le même client. |
