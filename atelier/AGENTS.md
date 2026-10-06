# Conventions du projet Cap Web

Ces règles s'appliquent à tout le monde : aux développeurs comme à l'agent.

## Nommage

- Une fonction porte un verbe qui dit ce qu'elle fait, en camelCase : `validateMessage`, `renderMessages`, `replyTo`.
- Une constante de réglage, fixée une fois pour tout le projet, s'écrit en MAJUSCULES : `LIMITE`, `MOTS`, `REPONSES`.
- Une variable porte un nom qui dit ce qu'elle contient, pas son type : `historique` plutôt que `tableau`, `auteur` plutôt que `el`.
- Un fichier JavaScript porte un nom court en minuscules, qui dit son rôle : `brain.js` (les règles), `view.js` (l'affichage), `app.js` (le câblage). Un test porte le nom de ce qu'il teste, suivi de `.test.js`.
- Un message de commit commence par son type, suivi de deux-points, puis dit en une phrase ce qui change : `fix:` (correction), `feat:` (nouvelle fonction), `test:` (tests), `docs:` (documentation), `refactor:` (renommage ou réorganisation sans changement de comportement). Exemple : `fix: replyTo ignore les espaces autour du message`.

## Interdits

1. Ne modifie jamais `tests/contrat/`, `browser/contrat.spec.js` ni `cahier-personnel.json`. Si un test te semble faux, arrête-toi et explique pourquoi.
2. N'utilise jamais `innerHTML`, `outerHTML` ni `insertAdjacentHTML` : le texte de l'utilisateur s'affiche avec `textContent`, jamais comme du HTML.
3. `brain.js` reste pur : aucun accès à `document`, `window` ni `localStorage`. Seuls `view.js` et `app.js` touchent à la page.
4. N'ajoute, ne retire et ne met à jour aucune dépendance (`package.json`, `package-lock.json`), et ne lance jamais `npm audit fix`.
5. N'écris jamais de clé, de mot de passe ni de donnée personnelle dans un fichier, un commit ou un message.
6. Ne fais aucun commit et aucun push à la place du binôme : propose le changement, le binôme relit le diff et fait le commit.
