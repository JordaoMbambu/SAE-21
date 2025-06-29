# Infrastructure Réseau d'un Campus Universitaire (SAE 2.01)

Ce projet présente la conception, la simulation et la configuration complète de l'infrastructure réseau pour un campus universitaire multi-sites. Réalisé dans le cadre de la S.A.E 2.01, il répond à un cahier des charges exigeant, intégrant des technologies avancées de routage, de segmentation VLAN, de sécurité et de services réseau.



---

## ➤ Contexte du Projet

Le scénario simule un réseau d'école composé de **4 sites géographiques distincts (LANs)**. Chaque site héberge plusieurs départements (formations, administration, enseignants) et des serveurs critiques (WEB, TFTP). L'architecture physique de chaque site repose sur **3 bâtiments interconnectés en boucle** par des liens Gigabit pour assurer la redondance.

Le défi principal était de créer un plan d'adressage optimisé et une configuration sécurisée permettant à des milliers d'utilisateurs de communiquer efficacement tout en protégeant les ressources sensibles du réseau.

---

## ➤ Objectifs et Technologies Clés

Ce projet démontre la maîtrise des compétences suivantes :

* **🌐 Plan d'adressage et Sous-réseaux**
    * Découpage de la plage `172.16.0.0/16` en utilisant la méthode **VLSM (Variable Length Subnet Masking)** pour optimiser l'allocation d'adresses IP sur 4 LANs de tailles variables (jusqu'à 8500 machines).
    * Création de liaisons point à point inter-sites à partir du réseau `192.168.1.0`.

* **‍💻 Segmentation et Commutation**
    * Mise en place de **5 VLANs** par site pour isoler les flux de trafic : administration, services, deux formations distinctes et enseignants.
    * Configuration des ports de switchs en mode **Access** et **Trunk** (802.1Q) pour la circulation des VLANs.
    * Utilisation du **Spanning Tree Protocol (STP)** pour gérer la topologie en boucle et prévenir les tempêtes de broadcast.

* **↔️ Routage**
    * Configuration du **routage Inter-VLAN** sur les routeurs de chaque site pour permettre la communication contrôlée entre les différents VLANs.
    * Déploiement du protocole de **routage dynamique RIP** pour assurer la connectivité entre les 4 sites distants.

* **🛡️ Sécurité**
    * Implémentation de **Listes de Contrôle d'Accès (ACLs)** pour filtrer le trafic, sécuriser l'accès aux serveurs (FTP, TFTP) et restreindre la communication entre les VLANs étudiants et administratifs.
    * Sécurisation des équipements réseau (routeurs, switchs) avec différents niveaux de mots de passe (enable, console, VTY).

* **🌍 Services et Accès WAN**
    * Mise en place de **NAT statique** pour rendre les serveurs WEB internes accessibles depuis Internet.
    * Configuration de **NAT dynamique (PAT)** pour permettre aux utilisateurs des différents VLANs d'accéder à Internet via une plage d'adresses IP publiques limitée.
    * Déploiement de serveurs **WEB** et **TFTP** virtualisés sur chaque LAN pour les services et la sauvegarde des configurations.

---

## ➤ Structure du Dépôt

* **`📁 SAE21_JORDAO_MBAMBU_PLAN_D'ADRESSAGE.xlsx`**: Le plan d'adressage VLSM détaillé pour chaque LAN et VLAN.
* **`📁 SAE21_JORDAO_MBAMBU_Tableau_atributtion_adressage_réseau.xlsx`**: Tableau d'attribution des adresses IP pour tous les équipements du réseau (PCs, serveurs, interfaces de routeurs, etc.).
* **`📁 SAE21_JORDAO_MBAMBU_Tableau_Port_Switch_.xlsx`**: Documentation complète du mappage des ports des switchs, indiquant quel port est assigné à quel VLAN en mode access ou trunk.
* **`📁 cahier_charges_SAE21.pdf`**: Le document original détaillant toutes les contraintes et objectifs du projet.
* **`📁 topologie_campus.pkt`**: Le fichier de simulation Cisco Packet Tracer contenant l'intégralité de la topologie et des configurations matérielles.
* **`📁 img/`**: Contient les images et captures d'écran pour ce README.

---

## ➤ Comment Utiliser ce Projet

1.  **Prérequis** : Assurez-vous d'avoir installé **Cisco Packet Tracer** (version 8.0 ou supérieure recommandée) et un tableur comme Microsoft Excel ou LibreOffice Calc.
2.  **Explorer la simulation** : Ouvrez le fichier `topologie_campus.pkt` pour visualiser la topologie et inspecter la configuration de chaque équipement.
3.  **Comprendre les objectifs** : Consultez le `cahier_charges_SAE21.pdf` pour comprendre les raisons derrière chaque choix de configuration.
4.  **Vérifier les configurations** : Les **trois fichiers Excel** servent de référence rapide pour trouver toutes les informations sur l'adressage IP, l'attribution des adresses et la configuration des ports des switchs.

---

## ➤ Auteur

* **Jordão Mbambu**
    * Portfolio (à venir)
    * [LinkedIn](https://www.linkedin.com/in/JordaoMbambu)

---

## ➤ Licence

Ce projet est distribué sous la licence MIT. Voir le fichier `LICENSE` pour plus d'informations.
