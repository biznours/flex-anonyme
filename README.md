# Flex Anonyme

Page web qui retire les données personnelles d'un relevé IBKR / MEXEM avant de l'envoyer à quelqu'un :
nom, adresse, e-mail, date de naissance, numéro de compte (remplacé par `U0000000`, y compris dans le nom
du fichier), numéros d'autres comptes et identifiant de connexion à moitié masqué.

Formats : XML FlexQuery et CSV de relevé d'activité (section « Informations du compte » / « Account Information »).

Tout se fait dans le navigateur : le fichier n'est envoyé nulle part. Les opérations, positions et montants
restent identiques à l'octet près, et la page vérifie qu'aucune donnée retirée ne figure plus dans le fichier
avant de proposer le téléchargement.

Site : https://biznours.github.io/flex-anonyme/
