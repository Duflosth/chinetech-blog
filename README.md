# CHINETECH

Blog statique Astro pour publier des analyses sur la tech chinoise avec des articles Markdown éditables via Decap CMS.

## Utilisation locale

1. Installer les dépendances :

   ```sh
   npm install
   ```

2. Lancer le site :

   ```sh
   npm run dev
   ```

3. Ouvrir l'adresse affichée par Astro, généralement `http://localhost:4321`.

Les pages principales sont :

- `/` pour la homepage.
- `/articles/` pour tous les articles publiés.
- `/articles/nom-de-l-article/` pour une page article.
- `/admin/` pour Decap CMS après déploiement Netlify.

## Publier un article

Les articles vivent dans `src/content/articles/`. Chaque fichier Markdown contient un en-tête avec :

- `title`
- `description`
- `date`
- `author`
- `tags`
- `cover`
- `draft`
- `featured`
- `featuredRank`

`draft: true` masque l'article du site public. Pour publier, passer `draft` à `false`.

## Choisir les articles à la une

Sur la homepage, la section "À la une" utilise les articles avec `featured: true`. Le champ `featuredRank` contrôle l'ordre : `1` passe avant `2`.

Si aucun article n'est marqué à la une, la homepage reprend automatiquement les articles publiés les plus récents.

## Newsletter

Le formulaire de newsletter utilise Netlify Forms avec le nom `newsletter`. Les inscriptions seront visibles dans l'interface Netlify une fois le site déployé.

Pour envoyer automatiquement les emails, connecter ensuite l'export Netlify Forms à un outil comme Resend, Brevo, Zapier ou Make. Aucun token n'est placé dans le frontend.

## Déploiement Netlify

1. Créer un site Netlify depuis le dépôt GitHub.
2. Choisir la branche de production `master`.
3. Utiliser la commande de build `npm run build`.
4. Utiliser le dossier de publication `dist`.
5. Vérifier que la détection des Forms est active pour la newsletter.

Le fichier `netlify.toml` contient déjà ces réglages de build.

## Admin Decap CMS

Decap est configuré dans `public/admin/config.yml` avec :

- `backend: git-gateway`
- `branch: master`
- `media_folder: public/uploads`
- `public_folder: /uploads`

Étapes Netlify :

1. Activer Identity.
2. Régler les inscriptions sur "Invite only".
3. Inviter les éditeurs.
4. Activer Git Gateway dans les services Identity et le connecter au dépôt GitHub.

`/admin/` peut rester public : seuls les utilisateurs invités via Netlify Identity peuvent publier. Ne jamais ajouter de token GitHub dans le frontend.

## Vérification avant publication

Exécuter :

```sh
npm run build
npm run preview
```

Vérifier ensuite :

- La homepage `/`.
- Les archives `/articles/`.
- Une page article.
- Le filtrage des brouillons.
- Le formulaire newsletter et la page `/merci/`.
- L'admin `/admin/` une fois Netlify Identity et Git Gateway activés.
