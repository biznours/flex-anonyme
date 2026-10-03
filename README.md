# Flex Anonyme

Page web qui retire les données personnelles d'un relevé IBKR / MEXEM avant de l'envoyer à quelqu'un :
nom, adresse, e-mail, date de naissance, numéro de compte (remplacé par un faux numéro stable, y compris dans le nom
du fichier), numéros d'autres comptes et identifiant de connexion à moitié masqué.

Formats : XML FlexQuery, CSV de relevé d'activité (section « Informations du compte » / « Account Information ») et requête Flex exportée en CSV (colonne « ClientAccountID »).

Tout se fait dans le navigateur : le fichier n'est envoyé nulle part. Les opérations, positions et montants
restent identiques à l'octet près, et la page vérifie qu'aucune donnée retirée ne figure plus dans le fichier
avant de proposer le téléchargement.

Site : https://biznours.github.io/flex-anonyme/

## Faux numéro de compte

Le vrai numéro est remplacé par `U` + 8 chiffres calculés par scrypt (N = 65536, r = 8, p = 1, sel fixe
`flex-anonyme-v1`) : toujours le même pour un même compte, sur tout ordinateur, sans rien stocker.
Le calcul (64 Mo, quelques secondes) est volontairement coûteux : le code étant public, retrouver le vrai
numéro obligerait à essayer un par un les ~100 millions de numéros IBKR possibles.

scrypt-js 3.0.1 (MIT, Richard Moore) est inclus localement : `scrypt.js`, licence dans `scrypt-LICENSE.txt`.
