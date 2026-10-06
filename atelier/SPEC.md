# Spécification de Cap Web

Chaque critère dit ce que fait Cap Web, puis ce qui le vérifie : un test du contrat (`tests/contrat/brain.contrat.test.js`, lancé par `npm test`) ou un essai dans la page (`npm start`, puis http://127.0.0.1:3000).

1. Quand on envoie un message de 201 caractères, Cap Web le refuse et l'erreur cite 200 ; à 200 caractères, il l'accepte.
   Vérifié par : test « accepte 200 caractères et refuse 201 ».

2. Quand on envoie un message vide ou fait uniquement d'espaces, Cap Web le refuse et affiche une erreur.
   Vérifié par : test « refuse le vide et les espaces seuls ».

3. Quand on écrit « bonjour », Cap Web donne la même réponse qu'à « salut », quelles que soient la casse et les espaces autour (`'  SALUT '` compris).
   Vérifié par : tests « donne la même réponse à « bonjour » et à « salut » » et « ignore la casse et les espaces autour ».

4. Quand on écrit une phrase qu'il ne connaît pas, Cap Web répond par un repli distinct des réponses à « salut », « aide » et « test ».
   Vérifié par : test « répond à une phrase inconnue par un repli distinct ».

5. Quand on envoie `<b>gras</b>`, Cap Web l'affiche tel quel, chevrons compris, sans mettre le texte en gras.
   Vérifié par : test « view.js affiche du texte et ne décide pas des réponses », et essai dans la page : envoyer `<b>gras</b>` et voir les chevrons.
