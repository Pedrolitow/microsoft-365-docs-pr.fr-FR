---
title: Mise en réseau de Contoso Corporation
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
ms.date: 10/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Comprendre l’infrastructure réseau contoso et la façon dont elle utilise la technologie SD-WAN pour optimiser les performances de mise en réseau à Microsoft 365 pour les services Cloud d’entreprise.
ms.openlocfilehash: ca673e6dcbf0f3db4bde33d388598e5f4ffac914
ms.sourcegitcommit: 628f195cbe3c00910f7350d8b09997a675dde989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "48637186"
---
# <a name="networking-for-the-contoso-corporation"></a>Mise en réseau de Contoso Corporation

Pour adopter une infrastructure de Cloud inclusive, Contoso a élaboré un changement fondamental dans la façon dont le trafic réseau vers les services Cloud transite. Au lieu d’un modèle interne Hub-and-spoke qui se concentre sur la connectivité réseau et le trafic pour le niveau suivant de la hiérarchie des bureaux, il a mappé des emplacements d’utilisateur à des connexions Internet locales et de sortie vers l’emplacement réseau Microsoft 365 le plus proche sur Internet.

## <a name="networking-infrastructure"></a>Infrastructure réseau

Voici les éléments réseau qui lient les bureaux Contoso dans le monde entier :

- Réseau étendu de commutation multiprotocole WAN (MPLS) 

  Un réseau MPLS WAN connecte le siège social de Paris aux bureaux régionaux et aux bureaux régionaux de satellites dans une configuration spoke-and-Hub. Le réseau permet aux utilisateurs d’accéder à des serveurs sur site qui composent des applications métiers dans le siège social de Paris. Il achemine également tout trafic Internet générique vers le Bureau de Paris, dans lequel les périphériques de sécurité du réseau dépassent les demandes. Dans chaque bureau, les routeurs acheminent le trafic vers des hôtes filaires ou des points d’accès sans fil sur des sous-réseaux, qui utilisent l’espace d’adressage IP privé.

- Accès Internet direct local pour le trafic Microsoft 365

  Chaque Office possède un périphérique WAN (SD-WAN) défini par le logiciel, qui dispose d’un ou de plusieurs circuits de réseau ISP locaux avec sa propre connectivité Internet via un serveur proxy. Elle est généralement implémentée en tant que liaison de réseau étendu à un fournisseur de services Internet local qui fournit également des adresses IP publiques et un serveur DNS local.

- Présence sur Internet

  Contoso possède le \. nom de domaine public contoso com. Le site Web public contoso pour commander des produits est un ensemble de serveurs dans un centre de contenu connecté à Internet dans le campus de Paris. Contoso utilise une/24 plage d’adresses IP publiques sur Internet.

La figure 1 illustre l’infrastructure de réseau contoso et ses connexions à Internet.

![Réseau contoso](../media/contoso-networking/contoso-networking-fig1.png)
 
**Figure 1 : réseau contoso**

## <a name="use-of-sd-wan-for-optimal-network-connectivity-to-microsoft"></a>Utilisation de la technologie SD-WAN pour la connectivité réseau optimale à Microsoft

Contoso a suivi les [principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md) pour :

- Identification et différenciation du trafic réseau Microsoft 365
- Sortir les connexions réseau localement
- Éviter les épingles de réseau
- Ignorer les périphériques de sécurité réseau en double

Il existe trois catégories de trafic réseau pour Microsoft 365 : *optimize*, *allow*et *default*. Optimiser et autoriser le trafic est le trafic réseau approuvé qui est chiffré et sécurisé aux points de terminaison et qui est destiné au réseau Microsoft 365.

Contoso a décidé d’effectuer les opérations suivantes :

- Utilisez la sortie Internet directe pour optimiser et autoriser le trafic de catégorie et transférer tout le trafic de catégorie par défaut vers la connexion Internet centrale de Paris.

- Déployer des périphériques SD-WAN au niveau de chaque bureau pour suivre facilement ces principes et obtenir des performances réseau optimales pour les services Cloud de Microsoft 365.

  Les appareils SD-WAN ont un port réseau local LAN pour le réseau local et plusieurs ports WAN. Un port WAN se connecte à son réseau MPLS. Un autre se connecte à un circuit du fournisseur de services Internet local. L’appareil SD-WAN achemine le trafic réseau de catégorie Optimiser et Autoriser sur le lien du fournisseur de services Internet.

## <a name="the-contoso-line-of-business-app-infrastructure"></a>Infrastructure d’application métier contoso

Contoso a conçu son infrastructure d’application métier et d’intranet de serveur pour les éléments suivants :

- Les succursales utilisent des serveurs de mise en cache locale pour stocker les documents et les sites web internes les plus sollicités.
- Les centres régionaux utilisent les serveurs d’applications régionaux pour les bureaux régionaux et les succursales. Ces serveurs se synchronisent avec les serveurs du siège social à Paris.
- Les centres de l’Université de Paris contiennent des serveurs d’applications centralisées qui servent l’ensemble de l’organisation.

La figure 2 montre le pourcentage de capacité de trafic réseau utilisé lors de l’accès aux serveurs sur l’intranet contoso.

![L’infrastructure contoso pour les applications internes](../media/contoso-networking/contoso-networking-fig2.png)
 
**Figure 2 : infrastructure contoso pour les applications internes**

Pour les bureaux satellites ou régionaux satellites, 60% des ressources nécessaires aux employés peuvent être pris en charge par les serveurs Office Hub et régionaux satellites. Les demandes de ressources supplémentaires 40% doivent passer par la liaison WAN vers le campus de Paris.

## <a name="network-analysis-and-preparation-for-microsoft-365-for-enterprise"></a>Analyse et préparation réseau pour Microsoft 365 pour les entreprises

L’adoption réussie de Microsoft 365 pour Enterprise Services par les utilisateurs de contoso dépend de la connectivité hautement disponible et performante à Internet ou directement aux services Cloud de Microsoft. Contoso a effectué les étapes suivantes pour planifier et implémenter une connectivité optimisée à Microsoft 365 pour les services Cloud d’entreprise :

1. Création d’un diagramme réseau WAN d’entreprise pour faciliter la planification

   Pour démarrer sa planification réseau, Contoso a créé un diagramme indiquant son emplacement de bureau, la connectivité réseau existante, les périphériques de périmètre réseau existants et les classes de service qui sont gérées sur le réseau. Ils ont utilisé ce diagramme pour chaque étape suivante de la planification et de l’implémentation de la connectivité réseau.

2. Création d’un plan pour Microsoft 365 pour la connectivité réseau d’entreprise

   Contoso a utilisé les [principes de connectivité réseau de microsoft 365](microsoft-365-network-connectivity-principles.md) et des exemples d’architectures réseau de référence pour identifier SD-WAN comme la topologie préférée de la connectivité Microsoft 365.

3. Analyse de l’utilisation de la connexion Internet et de la bande passante MPLS-WAN au niveau de chaque bureau, et augmentation de la bande passante selon les besoins

   L’utilisation actuelle de chaque Office a été analysée, et les circuits ont été augmentés de manière à ce que le trafic Cloud Microsoft 365 prévu fonctionne avec une moyenne de 20% de capacité inutilisée.

4. Optimiser les performances vers les services réseau Microsoft

   Contoso a déterminé l’ensemble des points de terminaison Office 365, Intune et Azure et configuré des pare-feu, des périphériques de sécurité et d’autres systèmes sur Internet pour des performances optimales. Les points de terminaison pour Office 365 optimiser et autoriser le trafic de catégorie ont été configurés sur les périphériques SD-WAN pour le routage via le circuit du fournisseur de services Internet.

5. Configurer le DNS interne

   Le DNS doit être fonctionnel et le trafic Microsoft 365 doit y être vérifié.

6. Valider le point de terminaison réseau et la connectivité de ports

   Contoso a exécuté les outils de test de connectivité réseau Microsoft pour valider la connectivité pour Microsoft 365 pour les services Cloud d’entreprise.

7. Optimiser les ordinateurs des employés pour la connectivité réseau

   Des ordinateurs individuels ont été vérifiés pour s’assurer que les dernières mises à jour du système d’exploitation ont été installées et que la surveillance de la sécurité du point de terminaison était active sur tous les clients.

## <a name="next-step"></a>Étape suivante

[En savoir plus](contoso-identity.md) sur la façon dont Contoso exploite ses services de domaine Active Directory (AD DS) locaux dans le cloud pour les employés, et fédère l’authentification pour les clients et les partenaires professionnels.

## <a name="see-also"></a>Voir aussi

[Feuille de route de mise en réseau pour Microsoft 365](networking-roadmap-microsoft-365.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)
