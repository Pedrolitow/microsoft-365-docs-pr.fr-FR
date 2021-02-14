---
title: Évaluation de la connectivité réseau Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
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
description: Microsoft 365 est conçu pour permettre aux clients du monde entier de se connecter au service à l’aide d’une connexion Internet. Au fil de l’évolution du service, la sécurité, les performances et la fiabilité de Microsoft 365 sont améliorées en fonction des clients qui utilisent Internet pour établir une connexion au service.
ms.openlocfilehash: c0bca2f354d71aa2f4f0c2b6fd05cb4786368b43
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46690012"
---
# <a name="assessing-microsoft-365-network-connectivity"></a>Évaluation de la connectivité réseau Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft 365 est conçu pour permettre aux clients du monde entier de se connecter au service à l’aide d’une connexion Internet. Au fil de l’évolution du service, la sécurité, les performances et la fiabilité de Microsoft 365 sont améliorées en fonction des clients qui utilisent Internet pour établir une connexion au service.
  
Les clients qui prévoient d’utiliser Microsoft 365 doivent évaluer leurs besoins de connectivité Internet existants et prévus dans le cadre du projet de déploiement. Pour les déploiements de classe entreprise, une connectivité Internet fiable et de taille appropriée est un élément essentiel de l’utilisation de fonctionnalités et de scénarios Microsoft 365.
  
Les évaluations réseau peuvent être effectuées par de nombreuses personnes et organisations en fonction de votre taille et de vos préférences. L’étendue réseau de l’évaluation peut également varier en fonction de l’endroit où vous vous trouvez dans votre processus de déploiement. Pour vous aider à mieux comprendre ce qu’il faut faire pour effectuer une évaluation du réseau, nous avons produit un guide d’évaluation du réseau pour vous aider à comprendre les options disponibles. Cette évaluation déterminera les étapes et les ressources qui doivent être ajoutées au projet de déploiement pour vous permettre d’adopter Correctement Microsoft 365.
  
Une évaluation complète du réseau fournira des solutions possibles aux défis de conception réseau, ainsi que des détails d’implémentation. Certaines évaluations réseau montrent que la connectivité réseau optimale à Microsoft 365 peut être hébergée avec des modifications mineures de configuration ou de conception de l’infrastructure de sortie internet et réseau existante.

Certaines évaluations indiquent que la connectivité réseau à Microsoft 365 nécessite des investissements supplémentaires dans les composants réseau. Par exemple, les réseaux d’entreprise qui s’étendent sur plusieurs succursales et régions géographiques peuvent nécessiter des investissements dans des solutions SD-WAN ou une infrastructure de routage optimisée pour prendre en charge la connectivité Internet à Microsoft 365. Parfois, une évaluation indique que la connectivité réseau à Microsoft 365 est influencée par la réglementation ou les exigences de performances pour des scénarios tels que la qualité des médias [de Skype Entreprise Online.](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917) Ces exigences supplémentaires peuvent entraîner des investissements dans l’infrastructure de connectivité Internet, l’optimisation du routage et la connectivité directe spécialisée.

Quelques ressources pour vous aider à évaluer votre réseau :

- Voir [vue d’ensemble de la connectivité réseau Microsoft 365](microsoft-365-networking-overview.md) pour obtenir des informations conceptuelles sur la mise en réseau Microsoft 365.
- Consultez les principes de connectivité réseau [de Microsoft 365](https://aka.ms/o365networkingprinciples) pour comprendre les principes de connectivité pour gérer en toute sécurité le trafic Microsoft 365 et obtenir les meilleures performances possibles.
- Inscrivez-vous [à Microsoft FastTrack pour](https://www.microsoft.com/fasttrack) obtenir une assistance guidée avec la planification, la conception et le déploiement de Microsoft 365. 
- Consultez la section de test de connectivité [Microsoft 365](assessing-network-connectivity.md#the-microsoft-365-connectivity-test) ci-dessous pour exécuter des tests de connectivité de base qui fournissent des conseils spécifiques sur les améliorations de connectivité réseau qui peuvent être apportées entre un emplacement d’utilisateur donné et Microsoft 365.

> [!NOTE]
> L’autorisation Microsoft est requise pour utiliser ExpressRoute pour Office 365. Microsoft examine chaque demande du client et autorise expressRoute uniquement pour l’utilisation d’Office 365 lorsque les exigences réglementaires d’un client autorisent une connectivité directe. Si vous avez de telles exigences, fournissez l’extrait de texte et le lien web au règlement que vous interprétez pour signifier que la connectivité directe est requise dans le formulaire de demande ExpressRoute pour [Office 365](https://aka.ms/O365ERReview) pour commencer une révision Microsoft. Les abonnements non autorisés qui tentent de créer des filtres d’itinéraire pour Office 365 recevront un [message d’erreur.](https://support.microsoft.com/kb/3181709)
  
Points clés à prendre en compte lors de la planification de votre évaluation réseau pour Microsoft 365 :
  
- Microsoft 365 est un service sécurisé, fiable et hautes performances qui s’exécute sur Internet public. Nous continuons à investir pour améliorer ces aspects du service. Tous les services Microsoft 365 sont disponibles via la connectivité Internet.

- Nous optimisons continuellement les principaux aspects de Microsoft 365, tels que la disponibilité, la portée globale et les performances pour la connectivité internet. Par exemple, de nombreux services Microsoft 365 tirent parti d’un ensemble étendu de nodes Edge côté Internet. Ce réseau edge offre la meilleure proximité et les meilleures performances pour les connexions provenant d’Internet.

- Lorsque vous envisagez d’utiliser Microsoft 365 pour l’un des services inclus tels que Teams ou les fonctionnalités vocales, vidéo ou de réunion Skype Entreprise Online, les clients doivent effectuer une évaluation réseau de bout en bout et répondre aux exigences de connectivité à l’aide de [Microsoft FastTrack.](https://www.microsoft.com/fasttrack)

Si vous évaluez Microsoft 365 et que vous ne savez pas par où commencer l’évaluation de votre réseau ou si vous avez trouvé des défis de conception réseau que vous devez surmonter, contactez votre équipe de compte Microsoft.

## <a name="the-microsoft-365-connectivity-test"></a>Test de connectivité Microsoft 365

Le test de connectivité [Microsoft 365](https://aka.ms/netonboard) est un outil d’évaluation du réseau de preuve de concept qui exécute des tests de connectivité de base sur votre client Microsoft 365 et recommande des conceptions réseau spécifiques pour optimiser les performances de Microsoft 365. L’outil met en évidence les choix courants de conception de périmètre de réseau d’entreprise de grande taille qui sont utiles pour la navigation web Sur Internet, mais ont un impact sur les performances des applications SaaS de grande taille telles que Microsoft 365.

L’outil d’intégration réseau permet d’utiliser les outils suivants :

- Détecte votre emplacement ou vous pouvez spécifier un emplacement à tester
- Vérifie l’emplacement de sortie de votre réseau
- Teste le chemin d’accès réseau à la porte d’accès au service Microsoft 365 la plus proche
- Fournit des tests avancés à l’aide d’une application Windows 10 téléchargeable qui fournit des recommandations de conception de réseau de périmètre relatives aux serveurs proxy, aux pare-feu et au DNS. L’outil exécute également des tests de performances pour Skype Entreprise Online, Microsoft Teams, SharePoint Online et Exchange Online.

L’outil possède deux composants : une interface utilisateur basée sur un navigateur qui collecte des informations de connectivité de base et une application Windows 10 téléchargeable qui exécute des tests avancés et renvoie des données d’évaluation supplémentaires.

L’outil basé sur le navigateur affiche les informations suivantes :

- Onglet Résultats et impact
  - Emplacement sur une carte de la porte d’entrée du service en cours d’utilisation
  - Emplacement sur une carte d’autres portes frontales de service qui offriraient une connectivité optimale
  - Performances relatives comparées aux autres clients Microsoft 365 proches de chez vous
- Onglet Détails et solutions
  - Emplacement de l’utilisateur par ville et pays
  - Emplacement de sortie réseau par ville, état et pays
  - Distance de sortie de l’utilisateur vers le réseau
  - Emplacement de la porte d’entrée du service Exchange Online Microsoft 365
  - Porte d’entrée du service Exchange Online Microsoft 365 optimale pour l’emplacement de l’utilisateur
  - Clients dans votre domaine d’affaires avec de meilleures performances

L’application téléchargeable Tests avancés fournit les informations supplémentaires suivantes :

- Onglet Détails et solutions (appended)
  - Passerelle par défaut de l’utilisateur
  - Serveur DNS client
  - Résolution récursive DNS du client
  - Serveur DNS Exchange Online
  - Serveur DNS SharePoint Online
  - Identification du serveur proxy
  - Vérification de la connectivité des médias
  - Perte de paquets de qualité des médias
  - Latence de qualité des médias
  - Gigue de qualité des médias
  - Réordons des paquets de qualité des médias
- Tests de connectivité à plusieurs points de terminaison spécifiques aux fonctionnalités
- Diagnostics de chemin d’accès réseau qui incluent des données d’analyse et de latence pour les services Exchange Online, SharePoint Online et Teams

Vous pouvez en savoir plus sur le test de connectivité de Microsoft 365 et fournir des commentaires sur le point de vue du test de connectivité [Microsoft 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130) mis à jour avec un nouveau billet de blog sur les recommandations de conception réseau. Des informations sur les futures mises à jour de cet outil et d’autres mises à jour réseau Microsoft 365 seront publiées sur le blog mise en réseau [Office 365.](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
  
Voici un lien que vous pouvez utiliser pour revenir [ https://aka.ms/o365networkconnectivity :](https://aka.ms/o365networkconnectivity)
  
## <a name="related-topics"></a>Rubriques connexes

[Vue d’ensemble de la connectivité réseau Microsoft 365](microsoft-365-networking-overview.md)

[Principes de connectivité réseau Microsoft 365](https://aka.ms/o365networkingprinciples)

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)

[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)

[Service web URL et adresses IP Office 365](microsoft-365-ip-web-service.md)

[Optimisation du réseau et des performances de Microsoft 365](network-planning-and-performance.md)

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)
