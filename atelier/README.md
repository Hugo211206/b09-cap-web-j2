# Cap Web

Ce README est à écrire par votre binôme au round 2, en 3 parties : à quoi sert Cap Web, comment l'installer et le lancer, et les 3 modules de `public/js` avec le rôle de chacun. La fiche est [documenter le projet](../defis/R2-ce-que-voit-l-agent.md).

En attendant, dans ce dossier : `npm start` lance Cap Web sur http://127.0.0.1:3000 (Ctrl+C l'arrête), et `npm test` lance les tests. On ne modifie jamais `tests/contrat/`, `browser/contrat.spec.js` ni `cahier-personnel.json`.

## À quoi sert Cap Web

Cap Web est un petit chatbot à règles, dans une page web : on écrit un message, il répond.
Il ne s'agit pas d'une IA : il reconnaît quelques mots (« salut », « aide », « test » et deux mots propres au binôme) et donne une réponse de repli pour le reste.
Le projet sert à apprendre le HTML, le CSS, le JavaScript, le DOM, les tests automatisés et Git.

## Installer et lancer

Il faut Node 24.20 ou plus. Dans un terminal PowerShell, depuis ce dossier `atelier` (si PowerShell refuse `npm`, tapez `npm.cmd`) :

1. Vérifier la version de Node :
   ```powershell
   node --version
   ```
2. Installer les outils (une vulnérabilité est annoncée : ne lancez pas `npm audit fix`) :
   ```powershell
   npm ci
   ```
3. Créer le cahier personnel, puis l'ouvrir dans l'éditeur pour y mettre votre limite (160 à 400, par pas de 10) et vos deux mots :
   ```powershell
   Copy-Item cahier-personnel.exemple.json cahier-personnel.json
   ```
4. Lancer Cap Web, puis ouvrir http://127.0.0.1:3000 dans le navigateur (Ctrl+C l'arrête) :
   ```powershell
   npm start
   ```
5. Lancer les tests (la dernière ligne doit afficher `fail 0`) :
   ```powershell
   npm test
   ```

## Les 3 modules de `public/js`

- `brain.js` : le cerveau. Il contient la limite, les mots reconnus et les réponses, et exporte deux fonctions pures, sans accès à la page : `validateMessage` vérifie un message (texte, non vide, pas trop long) et `replyTo` choisit la réponse.
- `view.js` : l'affichage. `renderMessages` dessine l'historique de la conversation dans la page, en texte seulement (jamais de HTML injecté). Il ne décide d'aucune réponse.
- `app.js` : le câblage. Il écoute le formulaire, appelle `validateMessage` puis `replyTo`, ajoute les messages à l'historique, le sauvegarde dans le navigateur (`localStorage`) et demande l'affichage à `view.js`.
