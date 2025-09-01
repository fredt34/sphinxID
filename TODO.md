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

NEXT
- Mock ? devrait être vrai
- BIND : User ?? non - test avec user
- mécanisme de repli ne semble pas fonctionner