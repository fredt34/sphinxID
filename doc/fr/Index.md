# SphinxID - Documentation de base

## Présentation

SphinxID est conçu pour gérer de façon sécurisée les identifiants anonymes des participants à la recherche, notamment dans les domaines sensibles comme la santé et les sciences humaines et sociales. Il remplace les fichiers Excel d’association, peu sécurisés, par un système robuste et traçable basé sur Hashicorp Vault.

### Fonctionnalités principales

- Les chercheurs peuvent déclarer les associations entre participants et codes de recherche, mais ne peuvent pas consulter ces associations.
- Seul le Délégué à la Protection des Données (DPD/DPO) peut accéder aux associations, et uniquement pour une levée d’anonymat unitaire.
- Tous les secrets et opérations sont stockés et journalisés de façon sécurisée dans Vault.
- SphinxID sert d’interface de paramétrage et de consultation pour Vault.
- **Les droits d’accès sont strictement définis par les policies Vault et sont inviolables.**
- **Toutes les actions sont tracées et inviolables, garantissant une auditabilité totale.**

## Concepts clés

### Instances

- Chaque organisation (école, université, etc.) est une Instance.
- Les instances sont créées à partir du registre ROR.
- Chaque instance possède au moins un administrateur et un DPO.
- L’authentification se fait via LDAP, SAML ou OIDC.

### Authentification LDAP

- Prise en charge des modes bind authentifié et anonyme.
- Retour en temps réel sur la configuration et la compatibilité LDAP.

### Laboratoires

- Les administrateurs définissent un ou plusieurs laboratoires par instance.
- Chaque laboratoire peut avoir plusieurs chercheurs.

### Projets

- Les chercheurs définissent des projets au sein des laboratoires.
- Les projets peuvent spécifier des règles de génération de secrets (manuel, séquence, aléatoire).

### Secrets

- Les chercheurs saisissent des paires [clé, secret] pour chaque projet.
- Les règles de secret sont spécifiques à chaque projet et peuvent être manuelles, séquentielles ou aléatoires.

## Architecture des données

- Toutes les données sont stockées sous un chemin racine (ex : `sphinxIDVXX`) dans Vault.
- Liste globale des instances : `/globaldata/.instances`
- Données d’instance : `/[codeInstance]/.instance-info`
- Laboratoires : `/[codeInstance]/labs/[codeLab]/lab-info`
- Projets : `/[codeInstance]/labs/[codeLab]/projects/[codeProjet]/project-info`
- Secrets : `/[codeInstance]/labs/[codeLab]/projects/[codeProjet]/secrets/[clé]`

## Exemple de workflow

1. Le chercheur saisit les informations du participant et l’ID anonyme dans SphinxID.
2. Les données sont chiffrées et stockées dans Vault.
3. Seul le DPO peut accéder à l’association si nécessaire.
