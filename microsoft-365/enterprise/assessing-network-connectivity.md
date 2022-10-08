---
title: Évaluation de la connectivité réseau Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 6/23/2020
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Microsoft 365 est conçu pour permettre aux clients du monde entier de se connecter au service à l’aide d’une connexion Internet. À mesure que le service évolue, la sécurité, les performances et la fiabilité de Microsoft 365 sont améliorées en fonction des clients qui utilisent Internet pour établir une connexion au service.
ms.openlocfilehash: 576f7c1e35a13e7fe6473b73e648a80c261876a8
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68198468"
---
# <a name="assessing-microsoft-365-network-connectivity"></a>Évaluation de la connectivité réseau Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft 365 est conçu pour permettre aux clients du monde entier de se connecter au service à l’aide d’une connexion Internet. À mesure que le service évolue, la sécurité, les performances et la fiabilité de Microsoft 365 sont améliorées en fonction des clients qui utilisent Internet pour établir une connexion au service.
  
Les clients qui envisagent d’utiliser Microsoft 365 doivent évaluer leurs besoins de connectivité Internet existants et prévus dans le cadre du projet de déploiement. Pour les déploiements de classes d’entreprise, la connectivité Internet fiable et de taille appropriée est un élément essentiel de l’utilisation des fonctionnalités et des scénarios Microsoft 365.
  
Les évaluations réseau peuvent être effectuées par de nombreuses personnes et organisations différentes en fonction de votre taille et de vos préférences. L’étendue réseau de l’évaluation peut également varier en fonction de l’endroit où vous vous trouvez dans votre processus de déploiement. Pour vous aider à mieux comprendre ce qu’il faut pour effectuer une évaluation réseau, nous avons produit un guide d’évaluation réseau pour vous aider à comprendre les options disponibles. Cette évaluation détermine les étapes et ressources à ajouter au projet de déploiement pour vous permettre d’adopter correctement Microsoft 365.
  
Une évaluation réseau complète fournira des solutions possibles aux problèmes de conception réseau, ainsi que des détails d’implémentation. Certaines évaluations réseau montrent que la connectivité réseau optimale à Microsoft 365 peut être prise en charge avec des modifications mineures de configuration ou de conception de l’infrastructure réseau et de sortie Internet existante.

Certaines évaluations indiquent que la connectivité réseau à Microsoft 365 nécessitera des investissements supplémentaires dans les composants réseau. Par exemple, les réseaux d’entreprise qui s’étendent sur plusieurs filiales et plusieurs régions géographiques peuvent nécessiter des investissements dans des solutions SD-WAN ou une infrastructure de routage optimisée pour prendre en charge la connectivité Internet à Microsoft 365. Parfois, une évaluation indique que la connectivité réseau à Microsoft 365 est influencée par la réglementation ou les exigences de performances pour des scénarios tels que [Skype Entreprise qualité des médias en ligne](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Ces exigences supplémentaires peuvent entraîner des investissements dans l’infrastructure de connectivité Internet, l’optimisation du routage et une connectivité directe spécialisée.

Quelques ressources pour vous aider à évaluer votre réseau :

- Consultez [la vue d’ensemble de la connectivité réseau Microsoft 365](microsoft-365-networking-overview.md) pour obtenir des informations conceptuelles sur la mise en réseau Microsoft 365.
- Consultez les [principes de connectivité réseau de Microsoft 365](./microsoft-365-network-connectivity-principles.md) pour comprendre les principes de connectivité pour gérer en toute sécurité le trafic Microsoft 365 et obtenir les meilleures performances possibles.
- Inscrivez-vous à [Microsoft FastTrack](https://www.microsoft.com/fasttrack) pour obtenir de l’aide guidée sur la planification, la conception et le déploiement de Microsoft 365. 
- Consultez la section de [test de connectivité Microsoft 365](assessing-network-connectivity.md#the-microsoft-365-connectivity-test) ci-dessous pour exécuter des tests de connectivité de base qui fournissent des conseils spécifiques sur les améliorations de connectivité réseau qui peuvent être apportées entre un emplacement utilisateur donné et Microsoft 365.

> [!NOTE]
> L’autorisation Microsoft est nécessaire pour utiliser ExpressRoute pour Office 365. Microsoft examine chaque demande du client et autorise uniquement ExpressRoute pour Office 365 utilisation lorsque les exigences réglementaires d’un client imposent une connectivité directe. Si vous avez de telles exigences, fournissez l’extrait de texte et le lien web vers le règlement que vous interprétez comme indiquant que la connectivité directe est requise dans [ExpressRoute pour Office 365 formulaire de demande](https://aka.ms/O365ERReview) pour commencer une révision Microsoft. Les abonnements non autorisés qui tentent de créer des filtres de routage pour Office 365 recevront un [message d’erreur](https://support.microsoft.com/kb/3181709).
  
Points clés à prendre en compte lors de la planification de votre évaluation réseau pour Microsoft 365 :
  
- Microsoft 365 est un service sécurisé, fiable et hautes performances qui s’exécute sur l’Internet public. Nous continuons d’investir pour améliorer ces aspects du service. Tous les services Microsoft 365 sont disponibles via la connectivité Internet.

- Nous optimisons continuellement les principaux aspects de Microsoft 365, tels que la disponibilité, la portée mondiale et les performances pour la connectivité Basée sur Internet. Par exemple, de nombreux services Microsoft 365 tirent parti d’un ensemble étendu de nœuds de périphérie accessibles sur Internet. Ce réseau de périphérie offre la meilleure proximité et les meilleures performances pour les connexions entrantes sur Internet.

- Lorsque vous envisagez d’utiliser Microsoft 365 pour l’un des services inclus tels que Teams ou Skype Entreprise fonctionnalités de voix, de vidéo ou de réunion en ligne, les clients doivent effectuer une évaluation réseau de bout en bout et répondre aux exigences de connectivité à l’aide [de Microsoft FastTrack](https://www.microsoft.com/fasttrack).

Si vous évaluez Microsoft 365 et que vous ne savez pas par où commencer votre évaluation réseau ou si vous avez trouvé des défis de conception réseau que vous avez besoin d’aide pour surmonter, collaborez avec votre équipe de compte Microsoft.

## <a name="the-microsoft-365-connectivity-test"></a>Test de connectivité Microsoft 365

Le [test de connectivité Microsoft 365](https://aka.ms/netonboard) est un outil d’évaluation réseau de preuve de concept (POC) qui exécute des tests de connectivité de base sur votre locataire Microsoft 365 et formule des recommandations de conception réseau spécifiques pour optimiser les performances de Microsoft 365. L’outil met en évidence les choix courants de conception de périmètre réseau des grandes entreprises qui sont utiles pour la navigation web Sur Internet, mais qui ont un impact sur les performances des applications SaaS volumineuses telles que Microsoft 365.

L’outil d’intégration réseau effectue les opérations suivantes :

- Détecte votre emplacement ou vous pouvez spécifier un emplacement à tester
- Vérifie l’emplacement de la sortie de votre réseau
- Teste le chemin d’accès réseau à la porte d’entrée du service Microsoft 365 le plus proche
- Fournit des tests avancés à l’aide d’une application Windows 10 téléchargeable qui fournit des recommandations de conception de réseau de périmètre liées aux serveurs proxy, aux pare-feu et au DNS. L’outil exécute également des tests de performances pour Skype Entreprise Online, Microsoft Teams, SharePoint Online et Exchange Online.

L’outil comporte deux composants : une interface utilisateur basée sur un navigateur qui collecte des informations de connectivité de base et une application Windows 10 téléchargeable qui exécute des tests avancés et retourne des données d’évaluation supplémentaires.

L’outil basé sur le navigateur affiche les informations suivantes :

- Onglet Résultats et impact
  - Emplacement sur une carte de la porte d’entrée du service en service en service
  - Emplacement sur une carte d’autres portes d’entrée de service qui fourniraient une connectivité optimale
  - Performances relatives par rapport aux autres clients Microsoft 365 proches de chez vous
- Onglet Détails et solutions
  - Emplacement de l’utilisateur par ville et pays
  - Emplacement de sortie réseau par ville, état et pays
  - Distance de sortie de l’utilisateur vers le réseau
  - Emplacement de la porte d’entrée du service Microsoft 365 Exchange Online
  - Porte d’entrée optimale du service Microsoft 365 Exchange Online pour l’emplacement de l’utilisateur
  - Clients de votre région métropolitaine avec de meilleures performances

L’application téléchargeable Tests avancés fournit les informations supplémentaires suivantes :

- Onglet Détails et solutions (ajouté)
  - Passerelle par défaut de l’utilisateur
  - Serveur DNS client
  - Résolveur récursif DNS client
  - serveur DNS Exchange Online
  - Serveur DNS SharePoint Online
  - Identification du serveur proxy
  - Vérification de la connectivité multimédia
  - Perte de paquets de qualité multimédia
  - Latence de qualité multimédia
  - Gigue de qualité des médias
  - Réorganisation des paquets de qualité multimédia
- Tests de connectivité à plusieurs points de terminaison spécifiques aux fonctionnalités
- Diagnostics de chemin d’accès réseau qui incluent des données de suivi et de latence pour les services Exchange Online, SharePoint Online et Teams

Vous pouvez en savoir plus sur le test de connectivité Microsoft 365 et fournir des commentaires dans le billet [de blog mis à jour sur le POC de test de connectivité Microsoft 365 avec de nouvelles recommandations de conception réseau](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130) . Des informations sur les futures mises à jour de cet outil et d’autres mises à jour réseau microsoft 365 seront publiées sur le blog [de mise en réseau Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking).
  
Voici un court lien que vous pouvez utiliser pour revenir : [https://aka.ms/o365networkconnectivity.](./microsoft-365-network-connectivity-principles.md)
  
## <a name="related-topics"></a>Rubriques connexes

[Vue d’ensemble de la connectivité réseau Microsoft 365](microsoft-365-networking-overview.md)

[Principes de connectivité réseau Microsoft 365](./microsoft-365-network-connectivity-principles.md)

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)

[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)

[Service web URL et adresses IP Office 365](microsoft-365-ip-web-service.md)

[Optimisation des performances et du réseau Microsoft 365](network-planning-and-performance.md)

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)