# Site Holdistry

Site statique d'une seule page (aucun outil de build).

## Fichiers

- `index.html` : la page
- `robots.txt`, `sitemap.xml`, `llms.txt` : pour les moteurs de recherche et les IA
- `_headers` : en-têtes de sécurité pour Cloudflare Pages

## 1. Remplacer le domaine

Les fichiers contiennent `__DOMAINE__` (par exemple `holdistry.com`, sans `https://`).
Remplace-le avant de publier :

    sed -i 's/__DOMAINE__/holdistry.com/g' index.html robots.txt sitemap.xml llms.txt

Sans domaine pour l'instant : utilise l'adresse que Cloudflare te donnera
(`nom-du-projet.pages.dev`), puis refais la commande avec le vrai domaine plus tard.

## 2. Mettre sur GitHub

1. Crée un dépôt (privé ou public) nommé `holdistry-site`.
2. Ajoute les fichiers de ce dossier (glisser-déposer sur la page du dépôt, ou en ligne de commande) :

       git init
       git add .
       git commit -m "Site Holdistry"
       git branch -M main
       git remote add origin https://github.com/TON-COMPTE/holdistry-site.git
       git push -u origin main

## 3. Publier avec Cloudflare Pages

1. Cloudflare > Workers & Pages > Create > Pages > Connect to Git.
2. Choisis le dépôt `holdistry-site`.
3. Framework preset : None. Build command : vide. Build output directory : `/`.
4. Save and Deploy. Chaque modification poussée sur GitHub redéploie le site.
5. Domaine personnalisé : projet > Custom domains > Set up a domain.

## 4. Vérifier après mise en ligne

- `https://TON-DOMAINE/robots.txt`, `/sitemap.xml` et `/llms.txt` s'ouvrent.
- La page s'affiche en mode clair et en mode sombre sur téléphone.
- Soumets le sitemap dans Google Search Console et Bing Webmaster Tools.
- Aucune occurrence de `__DOMAINE__` ne reste : `grep -r __DOMAINE__ .`

## À compléter plus tard

- Une adresse de contact (page et données structurées).
- La dénomination juridique, la forme sociale et le siège, dès qu'ils sont arrêtés.
- Retirer la mention de non-sollicitation quand la structure le permet (avis d'un juriste).
