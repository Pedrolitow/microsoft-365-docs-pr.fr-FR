---
title: Mise en réseau de Contoso Corporation
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Comprendre l’infrastructure réseau de Contoso et la façon dont l’entreprise utilise sa technologie SD-WAN pour optimiser les performances réseau afin de Microsoft 365 pour les services cloud d’entreprise.
ms.openlocfilehash: f8450b63bed68de414c0ea585b6f5e199c87ad90
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093940"
---
# <a name="networking-for-the-contoso-corporation"></a>Mise en réseau de Contoso Corporation

Pour adopter une infrastructure cloud inclusive, Contoso a conçu un changement fondamental dans le trafic réseau vers les services cloud. Au lieu d’un modèle hub-and-spoke interne qui concentre la connectivité réseau et le trafic pour le niveau suivant de la hiérarchie des bureaux, ils mappaient les emplacements utilisateur à la sortie Internet locale et aux connexions locales à l’emplacement réseau Microsoft 365 le plus proche sur Internet.

## <a name="networking-infrastructure"></a>Infrastructure réseau

Voici les éléments réseau qui relient les bureaux De Contoso à travers le monde :

- Réseau étendu de commutation multiprotocole WAN (MPLS) 

  Un réseau WAN MPLS connecte le siège de Paris aux bureaux régionaux et aux bureaux régionaux aux bureaux satellites dans une configuration spoke-and-hub. Le réseau permet aux utilisateurs d’accéder aux serveurs locaux qui composent des applications métier au siège social de Paris. Il achemine également tout trafic Internet générique vers le bureau de Paris, où les appareils de sécurité réseau récurent les demandes. Dans chaque bureau, les routeurs fournissent le trafic vers des hôtes câblés ou des points d’accès sans fil sur des sous-réseaux, qui utilisent l’espace d’adressage IP privé.

- Accès Internet direct local pour le trafic Microsoft 365

  Chaque bureau dispose d’un appareil SD-WAN (Software-Defined WAN) doté d’un ou de plusieurs circuits réseau internet locaux avec sa propre connectivité Internet via un serveur proxy. Il est généralement implémenté sous la forme d’un lien WAN vers un fournisseur de services Internet local qui fournit également des adresses IP publiques et un serveur DNS local.

- Présence sur Internet

  Contoso possède le nom de domaine public contosocom\.. Le site web public Contoso pour commander des produits est un ensemble de serveurs dans un centre de données connecté à Internet sur le campus de Paris. Contoso utilise une plage d’adresses IP publiques /24 sur Internet.

La figure 1 illustre l’infrastructure réseau de Contoso et ses connexions à Internet.

![Réseau Contoso.](../media/contoso-networking/contoso-networking-fig1.png)
 
**Figure 1 : Réseau Contoso**

## <a name="use-of-sd-wan-for-optimal-network-connectivity-to-microsoft"></a>Utilisation de la technologie SD-WAN pour la connectivité réseau optimale à Microsoft

Contoso a suivi les [principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md) pour :

- Identification et différenciation du trafic réseau Microsoft 365
- Sortir les connexions réseau localement
- Éviter les épingles de réseau
- Ignorer les périphériques de sécurité réseau en double

Il existe trois catégories de trafic réseau pour Microsoft 365 : *Optimiser*, *Autoriser* et *Par défaut*. Optimiser et autoriser le trafic est un trafic réseau approuvé chiffré et sécurisé aux points de terminaison et destiné au réseau Microsoft 365.

Contoso a décidé d’effectuer les opérations suivantes :

- Utilisez la sortie Internet directe pour optimiser et autoriser le trafic de catégorie et transférer tout le trafic de catégorie par défaut vers la connexion Internet centrale basée à Paris.

- Déployez des appareils SD-WAN à chaque bureau comme un moyen simple de suivre ces principes et d’obtenir des performances réseau optimales pour Microsoft 365 services cloud.

  Les appareils SD-WAN ont un port réseau local LAN pour le réseau local et plusieurs ports WAN. Un port WAN se connecte à son réseau MPLS. Un autre se connecte à un circuit isp local. L’appareil SD-WAN achemine le trafic réseau de catégorie Optimiser et Autoriser sur le lien du fournisseur de services Internet.

## <a name="the-contoso-line-of-business-app-infrastructure"></a>Infrastructure d’application métier Contoso

Contoso a conçu son infrastructure intranet d’application métier et de serveur pour les éléments suivants :

- Les succursales utilisent des serveurs de mise en cache locale pour stocker les documents et les sites web internes les plus sollicités.
- Les centres régionaux utilisent les serveurs d’applications régionaux pour les bureaux régionaux et les succursales. Ces serveurs se synchronisent avec les serveurs du siège social à Paris.
- Les centres de données du campus de Paris contiennent des serveurs d’applications centralisés qui servent l’ensemble de l’organisation.

La figure 2 montre le pourcentage de capacité de trafic réseau utilisée lors de l’accès aux serveurs sur l’intranet Contoso.

![Infrastructure Contoso pour les applications internes.](../media/contoso-networking/contoso-networking-fig2.png)
 
**Figure 2 : Infrastructure Contoso pour les applications internes**

Pour les bureaux de hubs satellites ou régionaux, 60 % des ressources nécessaires aux employés peuvent être desservies par des serveurs de bureaux hubs satellites et régionaux. Les 40% de demandes de ressources supplémentaires doivent passer par le lien WAN vers le campus de Paris.

## <a name="network-analysis-and-preparation-for-microsoft-365-for-enterprise"></a>Analyse du réseau et préparation des Microsoft 365 pour l’entreprise

La réussite de l’adoption de Microsoft 365 pour les services d’entreprise par les utilisateurs de Contoso dépend d’une connectivité hautement disponible et performante à Internet ou directement aux services cloud Microsoft. Contoso a pris les mesures suivantes pour planifier et implémenter une connectivité optimisée à Microsoft 365 pour les services cloud d’entreprise :

1. Créer un diagramme de réseau WAN d’entreprise pour faciliter la planification

   Pour démarrer sa planification réseau, Contoso a créé un diagramme montrant les emplacements de ses bureaux, la connectivité réseau existante, les périphériques de périmètre réseau existants et les classes de service gérées sur le réseau. Ils ont utilisé ce diagramme pour chaque étape ultérieure de la planification et de l’implémentation de la connectivité réseau.

2. Créer un plan de Microsoft 365 pour la connectivité réseau d’entreprise

   Contoso a utilisé les [principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md) et les exemples d’architectures réseau de référence pour identifier SD-WAN comme topologie préférée pour Microsoft 365 connectivité.

3. Analyser l’utilisation de la connexion Internet et la bande passante MPLS-WAN à chaque bureau, et augmenter la bande passante en fonction des besoins

   L’utilisation actuelle de chaque bureau a été analysée et les circuits ont été augmentés afin que les prévisions Microsoft 365 trafic basé sur le cloud fonctionnent avec une capacité inutilisée en moyenne de 20 %.

4. Optimiser les performances pour les services réseau Microsoft

   Contoso a déterminé l’ensemble des points de terminaison Office 365, Intune et Azure, et configuré des pare-feu, des appareils de sécurité et d’autres systèmes dans le chemin d’accès Internet pour des performances optimales. Les points de terminaison pour Office 365 optimiser et autoriser le trafic de catégorie ont été configurés dans les appareils SD-WAN pour le routage sur le circuit isp.

5. Configurer le DNS interne

   Le DNS doit être fonctionnel et le trafic Microsoft 365 doit y être vérifié.

6. Valider la connectivité du point de terminaison réseau et du port

   Contoso a exécuté les outils de test de connectivité réseau Microsoft pour valider la connectivité des Microsoft 365 pour les services cloud d’entreprise.

7. Optimiser les ordinateurs des employés pour la connectivité réseau

   Des ordinateurs individuels ont été vérifiés pour s’assurer que les dernières mises à jour du système d’exploitation ont été installées et que la surveillance de la sécurité des points de terminaison était active sur tous les clients.

## <a name="next-step"></a>Étape suivante

Découvrez comment Contoso [tire parti de ses services de domaine Active Directory local dans le cloud pour les](contoso-identity.md) employés et fédère l’authentification pour les clients et les partenaires commerciaux.

## <a name="see-also"></a>Voir aussi

[Feuille de route de mise en réseau pour Microsoft 365](networking-roadmap-microsoft-365.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)
