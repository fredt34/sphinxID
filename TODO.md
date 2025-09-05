# Next

- [X] Créer le DPO par Instance
- [/] Gérer le DPO par Instance
- [ ] Gérer les Admins par Instance
- [ ] Gérer les Chercheurs par Labo - "Resp Projet"?
- [ ] Définir les autres users: utilisateurs
- [ ] Définir le mécanisme de Bris de glace (Instance)
- [ ] Chercheur: multi labos
- [ ] DPO: multi-instances (si même authentification: password, SSO)

- [X] Tables : [https://gridjs.io/]

Ajouter de la css sur les Grid

Chercheur: limiter l'affichage des labs à ceux (celui) autorisé pour le chercheur; le sélectionner directement

Sécurité : monter les clés depuis plusieurs serveurs, avec accès restreint au Vault par IP?

Initialisation: si pas de secretMetadata, le créer, mettre une 1ere valeur dans .instances

- [X] Check/enable logout for SuperAdmin

Instance
- [ ] Définir le mode SSO de connexion
  - [ ] Implémenter LDAP
  - [ ] Implémenter MS

- [ ] Définir l'IA à utiliser: url, model, key

Labo

Projet
- [ ] Définir le mode de numérotation des ID Recherche : libre, aléatoire, séquentiel (via IA)
    - [x] si IA: définir le template de compteur
    - [ ] Intégrer le CODE CGI
- [ ] Définir les règles d'affichage des n derniers compteurs
- [ ] Charger un tableau de clés en masse

Code
- [ ] Tester / empêcher / gérer une 2e insertion d'une clé (doublons)

Environnement : sphinxIDVx
- maj config.js

Initialisation de VaultID
nano ./sphinxid.config

root@vault:~# 
./connect.sh
./initialize.sh

## NEXT
[X] Mock ? devrait être vrai
[X] BIND : User ?? non - test avec user
[X] mécanisme de repli ne semble pas fonctionner

## Next 2

[ ] Analyze security of the mechanism of relying on information gathered from identity_policies, gotton on login, to dertermine user's rights: can a rogue user forge identity_policies and gain unauthorized access?

## Next 3

### Big changes:
[ ] Keep the html in 1 single index.html with extending current hide/show mechanisms
    OR move and split it in some-module-function.html.include files (or other file names /extensions if a standard exists for this stuff); 
    -- What's best ?
[ ] Change all the vanilla html to use only web-awesome (wa) web components
[ ] If trusting  identity_policies gotten on logon has no security issues (decided in step Next 2): check if the mechanism for Researchers can be expanded to dpo and admin, and then apply. This would unify the login process.

### Medium changes:
[ ] Add Status and Logo (image file) files for Instances
[ ] Add Presentation page (prez) for Instances (markdown)
[ ] When logged as SuperAdmin: Allow editing Name, Status and Logo of Instance
[ ] Display Instance's logo and prez text (as html) when instance is selected from the Selector
[ ] Get Labs (Instance childs) from rorData.relationships as saved in Instance - don't query ROR, we have the info.
[ ] Add a button to refresh the ROR childs

### Small changes:
[ ] Trim user names when created or input
When logged as Admin : 
[ ] Display the Lab Name and the code in () : "Institut des Sciences Sociales du Politique (03jdg7625)"
[ ] Allow Edit button for Labs to change Name, Desc, Dept, Status
