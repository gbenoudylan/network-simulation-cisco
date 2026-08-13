# network-simulation-cisco
 Network Simulation — Cisco Packet Tracer

Cartographie et simulation d'une architecture réseau d'entreprise à 3 niveaux (bordure / cœur / accès), réalisée sous Cisco Packet Tracer, inspirée d'un site d'entreprise réel.

Projet réalisé dans le cadre d'un stage en ingénierie systèmes & réseaux — les éléments identifiants (noms d'hôtes réels, adressage de production, credentials) ont été génériques ou anonymisés.

 Architecture

Modèle en 3 couches (architecture hiérarchique Cisco) :

Couche	Équipements	Rôle
Bordure (Border)	2× routeurs C8200L	Connexion WAN / Internet, redondance
Cœur (Core)	Stack C9300X	Routage haute performance, backbone
Distribution / Accès	Stack C3850 + 9× C9200 (dual-homed)	Connexion des postes utilisateurs, redondance par double-attachement
        Internet
           │
   ┌───────┴───────┐
   │  2× C8200L     │   ← Bordure (redondance)
   └───────┬───────┘
           │
     ┌─────┴─────┐
     │  C9300X    │       ← Cœur
     └─────┬─────┘
           │
     ┌─────┴─────┐
     │  C3850     │       ← Distribution
     └─────┬─────┘
           │
   ┌───────┴────────┐
   │ 9× C9200        │    ← Accès (dual-homed)
   └────────────────┘
⚙️ Éléments configurés
VLANs : segmentation logique par service/usage
Adressage IP : plan d'adressage cohérent par VLAN/site
OSPF : routage dynamique entre les couches cœur et distribution, convergence testée
Dual-homing : switches d'accès rattachés à deux switches de distribution pour la résilience
ACLs : contrôle de flux entre segments (selon version du fichier)
 Contenu du repo
network-simulation.pkt — fichier Cisco Packet Tracer (topologie complète, configs incluses)
docs/plan-adressage.md — plan VLAN/IP
docs/schema-architecture.png — export visuel de la topologie
 Pour ouvrir le projet
Installer Cisco Packet Tracer (gratuit avec un compte Cisco Networking Academy)
Ouvrir le fichier network-simulation.pkt
Explorer la topologie, les configurations des équipements et les tests de connectivité (ping, traceroute, show ip route)
 Compétences mobilisées

Cisco Packet Tracer · Architecture réseau 3 niveaux · OSPF · VLAN · Adressage IP · Redondance / Dual-homing · ACL

 Note

Ce projet modélise une architecture inspirée d'un environnement d'entreprise réel dans un but pédagogique et de démonstration ; il ne reproduit pas l'adressage ni la configuration exacte de production.
