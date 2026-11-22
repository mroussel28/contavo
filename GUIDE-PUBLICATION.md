# Contavo : guide de publication (Android d'abord)

Ce dossier est une copie publique, sans aucune de tes données. Elle est indépendante de tes outils personnels.

## 0. Avant de commencer
- **Adresse de contact publique** : crée une adresse dédiée (par ex. contavo.contact@outlook.fr) plutôt que ton adresse perso. Google l'affiche sur la fiche de l'app.
- Remplace `[ADRESSE_CONTACT]` dans `confidentialite.html`, `mentions-legales.html` et `conditions.html` (Bloc-notes → Rechercher/Remplacer).
- **Nom** : vérifie que « Contavo » est libre (recherche sur le Play Store et sur data.inpi.fr). Sinon, dis-moi le nom choisi et je mets tout à jour.

## 1. Mettre l'app en ligne (GitHub Pages, gratuit)
1. Connecte-toi sur github.com, puis clique sur **New repository**. Nom : `contavo`, réglé sur **Public**, et clique sur **Create**.
2. Clique sur **uploading an existing file** et glisse **tout le contenu** du dossier, y compris les dossiers `icons` et `.well-known` et le fichier `.nojekyll`. Puis clique sur **Commit changes**.
   - Les noms qui commencent par un point (`.well-known`, `.nojekyll`) sont masqués par Windows. Dans l'Explorateur, active Affichage → Afficher → Éléments masqués.
3. Va dans **Settings → Pages → Source : Deploy from a branch → main / (root) → Save**.
4. Quelques minutes plus tard, l'app est en ligne à l'adresse `https://mroussel28.github.io/contavo/`.
5. Test : ouvre cette adresse sur ton iPhone dans Safari, puis Partager → **Sur l'écran d'accueil**. Sur Android : Chrome → **Installer l'application**. Tout fonctionne déjà, sans passer par les stores.

## 2. Créer le paquet Android (sans rien installer)
1. Va sur **pwabuilder.com**, colle l'adresse de l'étape 1 et clique sur **Start**. Le score doit indiquer que le manifest et le service worker sont OK.
2. Choisis **Package for stores → Android → Google Play**.
   - Package ID : `io.github.mroussel28.contavo`
   - App name : Contavo
   - Laisse la génération d'une nouvelle clé de signature.
3. Télécharge le zip. **Conserve précieusement** le fichier `signing.keystore` et ses mots de passe (`signing-key-info.txt`), sur ton NAS et sur une clé USB. Sans eux, plus aucune mise à jour possible.
4. Le zip contient un fichier `assetlinks.json`. Remplace avec lui celui de `.well-known/` sur GitHub. C'est ce qui supprime la barre d'adresse dans l'app Android.

## 3. Google Play Console
1. Va sur play.google.com/console et crée un compte **Personnel**. Il faut **25 $ une seule fois** et une vérification d'identité (pièce d'identité + téléphone Android).
2. **Créer une application** : Contavo, Français, Application, **Gratuite**.
3. Dans **Contenu de l'application** :
   - Règles de confidentialité : `https://mroussel28.github.io/contavo/confidentialite.html`
   - Annonces : **Non**
   - Accès : toutes les fonctionnalités sont disponibles sans restriction.
   - Classification du contenu : questionnaire → catégorie « Utilitaire / Productivité », aucun contenu sensible.
   - Public cible : **18 ans et plus** (outil de finances personnelles).
   - **Sécurité des données** : « Votre application collecte-t-elle ou partage-t-elle des données utilisateur ? » → **Non**. C'est exact : tout reste sur l'appareil, rien n'est transmis.
   - Applications financières : déclare « aucune de ces fonctionnalités » (pas de prêt accordé, pas de paiement, pas de trading).
   - DSA / statut de commerçant : **Non-commerçant** (app gratuite, sans pub, à titre personnel).
4. **Fiche du Play Store** : utilise les textes ci-dessous, l'icône `icons/icon-512.png` et au moins 2 captures d'écran (prends-les sur ton téléphone).
5. **Test fermé** : importe le fichier `.aab` du zip PWABuilder et invite **au moins 12 testeurs** par e-mail (adresses Gmail). Ils doivent rester inscrits **14 jours d'affilée**. Pense à la famille, aux amis et aux collègues volontaires.
6. Après les 14 jours, clique sur **Demander l'accès à la production** et réponds précisément (qui a testé, ce qui a été corrigé).

## 4. Textes de la fiche Play Store
**Description courte (80 caractères max)** :
Livraisons, véhicules, salaire, prêts : vos comptes, 100 % sur votre téléphone.

**Description complète** :
Contavo réunit dans une seule application gratuite le suivi de votre quotidien :
• Livraisons entre particuliers : rémunération, pourboires, coût réel du trajet, net par heure, objectif du mois.
• Véhicules : dépenses par catégorie (recharge, carburant, entretien, assurance, péages), coût réel au kilomètre.
• Bulletins de salaire : brut, net, impôt prélevé, cumuls annuels, évolution d'un mois à l'autre, taux horaire.
• Prêts et assurances : mensualité, capital restant dû, échéancier complet, total de vos charges mensuelles.

Vos données restent sur votre appareil : aucun compte, aucune publicité, aucun traceur, aucune donnée envoyée sur Internet. Sauvegarde et restauration par fichier, export CSV pour Excel. Fonctionne hors connexion, en mode clair ou sombre.

Les calculs sont indicatifs et ne remplacent pas vos documents officiels.

## 5. Mises à jour
Pour changer l'app, il suffit de remplacer les fichiers sur GitHub. La version Android affiche le site, donc elle est à jour aussitôt, sans nouvelle validation. À chaque version, augmente le numéro `CACHE` dans `sw.js` et `VERSION` dans `index.html`, sinon les téléphones garderont l'ancienne version en cache.

## 6. iPhone (plus tard)
Apple refuse le plus souvent les apps qui reprennent un site web (règle 4.2). Il faudra des fonctions propres au téléphone (notifications de rappel d'échéance, widget…), un compte Apple Developer (99 $/an) et un Mac ou un service de compilation en ligne. En attendant, l'installation depuis Safari (étape 1.5) donne déjà une icône et un fonctionnement hors connexion sur iPhone.
