# ShotPro — firmwares de la caméra

Ce dépôt sert uniquement à distribuer les firmwares de la caméra à
l'application ShotPro. L'application lit les **Releases** de ce dépôt : publier
une release suffit pour proposer la mise à jour à tous les utilisateurs, sans
nouvelle version de l'app ni serveur à maintenir.

> ⚠️ Ce dépôt est **public** : n'y mettez que les fichiers firmware fournis par
> le constructeur, jamais de document interne ni de mot de passe.

## Déployer une nouvelle version du firmware

### 1. Préparer les fichiers

Récupérez le ou les fichiers `.bin` envoyés par le constructeur et **ne les
renommez pas** :

| Modèle      | Fichier      |
|-------------|--------------|
| Q8L         | `FWQ8L.bin`  |
| Q8L PRO     | `FWQ8_8.bin` |

L'application choisit le fichier dont le nom correspond exactement à celui que
la caméra annonce elle-même. Une caméra ne peut donc jamais recevoir le
firmware d'un autre modèle. Une release peut contenir un seul modèle ou les
deux.

### 2. Créer la release (en test d'abord)

1. Sur la page d'accueil du dépôt, colonne de droite (tout en bas sur mobile),
   section **Releases** → **Create a new release**. Ou directement :
   <https://github.com/Rob1Lu/shotpro-firmware/releases/new>
2. **Choose a tag** → saisir un nouveau tag → **Create new tag**. Le tag doit
   être **la version exacte que la caméra affichera après la mise à jour**,
   par exemple `V.120261019.0`. C'est ainsi que l'app sait qu'une caméra est
   déjà à jour.
   - Si vous ne la connaissez pas encore, mettez la version annoncée par le
     constructeur et corrigez-la après le test (étape 4).
3. **Release title** : libre, par exemple `Firmware 2026-10-19`.
4. **Description** : les notes de version, **en langage simple**. Elles sont
   affichées telles quelles aux utilisateurs dans l'application.
5. **Attach binaries** : glissez le ou les fichiers `.bin`.
6. Cochez **Set as a pre-release**. Une pre-release n'est visible que par les
   versions de test de l'application, les utilisateurs ne la voient pas.
7. **Publish release**.

### 3. Tester sur une caméra

Avec une version de test de l'application :

1. Téléphone connecté à Internet : ouvrir l'app. L'écran de connexion propose
   de télécharger le firmware (environ 34 Mo).
2. Se connecter à la caméra : une fenêtre « Nouveau firmware disponible »
   apparaît. Choisir **Mettre à jour**, puis **Installer**. Batterie
   suffisamment chargée obligatoire.
3. Attendre la fin : envoi (environ 20 s), vérification, installation,
   redémarrage de la caméra, puis calibrage du gyroscope guidé par l'app.
4. Noter la version affichée dans **Réglages → Firmware de la caméra**.

### 4. Diffuser à tous les utilisateurs

Sur la release : **Edit** (icône crayon), puis :

- si la version affichée par la caméra diffère du tag, corriger le tag pour
  qu'il soit **identique** ;
- décocher **Set as a pre-release** ;
- cocher **Set as the latest release** ;
- **Update release**.

C'est immédiat : les utilisateurs la verront dès que leur téléphone aura eu
accès à Internet avec l'app ouverte.

## Ce que voit l'utilisateur

- **Écran de connexion**, téléphone encore sur Internet : une carte propose de
  télécharger la mise à jour sur le téléphone.
- **Juste après la connexion à la caméra** : une fenêtre annonce la nouvelle
  version. L'utilisateur peut l'**ignorer** : elle ne reviendra plus pour cette
  version, mais la mise à jour reste accessible dans **Réglages → Firmware de
  la caméra**.
- **Après une mise à jour** : le calibrage du gyroscope est **obligatoire**.
  Tant qu'il n'a pas été confirmé, une fenêtre impossible à fermer l'impose à
  chaque connexion avant toute utilisation de la caméra.

## Retirer une version

Supprimer la release, ou la repasser en pre-release. L'application se rabat sur
la release publiée la plus récente qui contient le fichier du modèle. Une
caméra déjà mise à jour n'est **pas** rétrogradée.

## Règles à respecter

- Ne jamais renommer un `.bin`.
- Un tag = la version exacte affichée par la caméra après la mise à jour.
- Toujours tester en pre-release sur une caméra avant de diffuser.
- Ne jamais publier un firmware non fourni par le constructeur.
