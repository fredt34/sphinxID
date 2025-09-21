# Documentation de SphinxID

Certains projets de recherche imposent l'utilisation d'identifiants anonymes pour les personnes sujet de recherche - en particulier dans les domaines de la santé ou des sciences humaines et sociales.

En l'absence de solution technique, les chercheurs sont généralement les détenteurs des fichiers d'association 
: de simples fichiers Excel. Ces fichiers sont partagés (ou pas) et backupés (ou pas). Cette "solution" n'est pas satisfaisante du point de vue du RGPD.

SphinxID répond à ce besoin en:
  - permettant aux chercheurs de déclarer les associations entre les personnes et les codes de recherche, tout en leur interdisant la consultation de ces associations;
  - réservant la consultation des fichiers d'association au Délégué à la protection des données (DPD/DPO);
  - limitant le rôle du DPO à la levée unitaire d'anonymat;
  - sécurisant les secrets et en traçant toutes les opérations de manière inviolable, grâce à Hashicorp Vault:
    - Vault gère strictement et nativement les contrôles et les journaux d'accès;
    - SphinxID n'est qu'une interface de paramétrage et de consultation de Vault.

Pour chaque projet, les chercheurs habilités peuvent saisir des informations [clé, secret], où le 'secret' est une donnée identifiante du participant (nom, prénom, etc.) associée à la 'clé' (ID anonyme de recherche).

### Exemple

- ➡️ Un chercheur travaillant sur un projet de recherche en santé saisit des informations d'association [nom du participant, ID anonyme de recherche] dans SphinxID.
- ➡️ Cette association est chiffrée et stockée dans Vault
- ➡️ Seul le DPO, garant de la protection des données, peut y accéder si nécessaire - aucun chercheur ne peut jamais accéder aux associations [ID de recherche - identité du participant].

## Organisation

### Instances

Chaque Ecole, Université... est définie en tant qu'Instance.

Le SuperAdministrateur crée l'instance à partir du ROR, annuaire international d'identifiants pour les organimes de recherche.

Chaque instance comporte:
  - 1 administrateur (ou plus)
  - 1 DPO
(La solution complète permettra de définir des DPO Adjoints.)

Chaque instance s'appuie sur 1 système d'authentification: LDAP, SAML ou OIDC (les deux derniers sont en attente).

On peut définir une IA à utiliser pour chaque instance afin de définir simplement des compteurs.

Par exemple: ENS Paris-Saclay. 

### Laboratoires

Pour chaque instance, son administrateur définit 
  - 1+ Laboratoire
    - Et pour chaque Laboratoire:
      - 1+ chercheur(s)

Par exemple: labos de tests L1 et L2.

### Projets

Pour chaque laboratoire, les chercheurs peuvent définir 1+ Projet(s).

Un projet peut définir:
  - des exemples de séquence de compteur (via l'IA de l'instance)
  - le mode de définition des secrets
  - l'affichage des _n_ derniers secrets

### Secrets

Pour chaque Projet, les chercheurs habilités (= chercheur créateur + éventuels autres chercheurs invités) peuvent saisir des informations [clé, secret]
  - règles possibles pour le secret - le créateur du projet sélectionne l'une de ces règles:
    - Le chercheur saisit directement le secret;
    - L'application définit le secret par une séquence, par exemple ID100, ID200, ID300... (avec des règles et exemples pour génération via une IA);
    - L'application propose un secret aléatoire (avec des règles spécifiques au projet)

## Utilisateurs et rôles


Les utilisateurs de tests définis sont:

  - ens-admin
  - ens-dpo
  - ens-l1-r1
  - ens-l1-r2
  - ens-l1-r3
  - ens-l2-r1
  - ens-l2-r2
  - ens-l2-r3

ens-l1-r1, ens-l1-r2 et ens-l1-r3 sont les chercheurs de test pour Labo1. Idem pour L2.

## Status

SphinxID est en cours de développement et est au stade Maquettage.

## Informations techniques

Sphinx est une application web uniquement (PWA en Vanilla javascript, utilisant les Web Components Web Awesome [ex Shoelace]), appelant l'API de Hashicorp Vault.

Sphinx est développé à 99% par IA (Claude, Grok free).

Des scripts Shell permettent de configurer l'instance Vault.

## Autres informations

SphinxID sera un logiciel Libre, licence en cours de sélection.

Le code de SphinxID sera hébergé sur Github.

Chaque organisme de recherche pourra télécharger et exploiter une ou plusieurs instances, seul ou conjointement avec d'autres organismes.

L'application sera disponible en FR en EN (langues officielles), et est conçue pour supporter toute autre langue.

## Contraintes

## Licence

SphinxID is released under the GNU AGPL-3.0 License (see [LICENSE](LICENSE)).

Additional licensing restrictions (NO commercial use, French version) are available in [LICENCE-ADDITIONAL.md](LICENCE-ADDITIONAL.md).