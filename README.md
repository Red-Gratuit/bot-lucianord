# Bot LuciaNord

Bot Telegram et API Flask prêts à être déployés sur Railway.

## Déploiement Railway

1. Connecter le dépôt GitHub à un nouveau service Railway.
2. Ajouter la variable `BOT_TOKEN` avec le token fourni par BotFather.
3. Générer un domaine public Railway. L'application configure alors le webhook Telegram avec ce domaine au démarrage.
4. Définir le healthcheck Railway sur `/health`.
5. Si la Mini App n'est pas celle par défaut, définir `MINI_APP_URL` avec son URL publique. Cette URL est indépendante du domaine du webhook.

Railway détecte `requirements.txt` et démarre l'application avec le `Procfile`. Le serveur écoute le port `$PORT` fourni par Railway.

## Persistance des produits

Sans volume Railway, les changements apportés à `products.json` peuvent être perdus lors d'un redéploiement ou d'un redémarrage. Pour les conserver, ajouter un volume monté sur `/data` et définir `PRODUCTS_FILE=/data/products.json`.

## État de la Mini App

Ce dépôt ne contient pas les fichiers de l'interface web (`index.html`, CSS ou JavaScript). Par défaut, le bouton du bot ouvre `https://designkeeper-admin-hub.lovable.app`; définir `MINI_APP_URL` pour utiliser une autre interface. Le service fournit aussi `/health` et les routes API.
