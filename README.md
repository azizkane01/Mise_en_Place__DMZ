
# Mise en place d’une DMZ sécurisée avec `nftables`

Dans ce projet, nous avons conçu une architecture réseau simulée dans **GNS3** afin de mettre en place une **DMZ (zone démilitarisée)**. L’objectif est de renforcer la sécurité du réseau en le segmentant en plusieurs zones : **LAN**, **DMZ**, et **réseau client (Internet)**.

Nous avons configuré un pare-feu Linux jouant un rôle central entre ces différentes zones. Grâce à `nftables`, nous avons défini des règles de filtrage pour contrôler finement le trafic :

* Le **réseau LAN** peut accéder à Internet, mais **Internet ne peut pas accéder au LAN**, grâce à des règles de filtrage strictes.
* Les **clients externes** peuvent uniquement accéder aux **services hébergés dans la DMZ** (par exemple, un serveur web), sans pouvoir interagir avec le LAN.
* Cette architecture permet d’**isoler la partie sensible du réseau** interne d’Internet, conformément aux bonnes pratiques en matière de sécurité réseau.

Le pare-feu applique également du **NAT** pour permettre aux hôtes internes de sortir vers Internet, et journalise les connexions bloquées pour faciliter l’audit de sécurité.

Nous avons également déployé un serveur web dans la DMZ et testé les flux de communication pour vérifier que l’isolation entre les zones fonctionne comme prévu.

