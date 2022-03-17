---
title: Rapports dans Microsoft Defender pour les entreprises
description: Obtenir une vue d’ensemble des rapports disponibles dans Microsoft Defender entreprise
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 68b5c15b69c1f485bb9ed90bab06c2ceaa2978d9
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63527083"
---
# <a name="reports-in-microsoft-defender-for-business"></a>Rapports dans Microsoft Defender pour les entreprises

> [!IMPORTANT]
> Microsoft Defender for Business est en déploiement [Microsoft 365 Business Premium clients,](../../business-premium/index.md) à partir du 1er mars 2022. Defender for Business as a standalone subscription is in preview, and will roll out gradually to customers and IT Partners who [sign-up here](https://aka.ms/mdb-preview) to request it. La [prévisualisation inclut un ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Plusieurs rapports sont disponibles dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Cet article décrit ces rapports, leur utilisation et leur recherche.

<br/><br/>

## <a name="reports-in-defender-for-business"></a>Rapports dans Defender for Business

|Rapport  |Description  |
|---------|---------|
| **Rapport de sécurité**  | Le rapport de sécurité fournit des informations sur les identités, les appareils et les applications de votre entreprise. Pour accéder à ce rapport, dans le volet de navigation, choisissez **Rapport** **ReportsGeneralSecurity** >  > . <br/><br/>**CONSEIL** Vous pouvez afficher des informations similaires sur la page d’accueil de votre portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). |
| **Protection contre les menaces**  | Le rapport sur la protection contre les menaces fournit des informations sur les alertes et les tendances des alertes. Utilisez la **colonne Tendances des alertes** pour afficher des informations sur les alertes déclenchées au cours des 30 derniers jours. Utilisez la **colonne État de l’alerte** pour afficher les informations de capture instantanée actuelles sur les alertes, telles que les catégories d’alertes non résolues et leur classification. Pour accéder à ce rapport, dans le volet de navigation, sélectionnez **Protection** **ReportsEndpointsThreat** >  > . <br/><br/>**CONSEIL** : vous pouvez également utiliser la liste **Incidents** pour afficher des informations sur les alertes. Dans le volet de navigation, choisissez **Incidents** pour afficher et gérer les incidents actuels. Pour plus d’informations, voir [Afficher et gérer les incidents dans Microsoft Defender entreprise](mdb-view-manage-incidents.md). |
| **Intégrité et conformité des appareils** | Le rapport sur l’état et la conformité de l’appareil fournit des informations sur l’état et les tendances de l’appareil. Vous pouvez utiliser ce rapport pour déterminer si les capteurs Defender entreprise fonctionnent correctement sur les appareils et l’état actuel de Antivirus Microsoft Defender. Pour accéder à ce rapport, dans le volet de navigation, sélectionnez **État** d’état et conformité **ReportsEndpointsDevice** >  > . <br/><br/>**CONSEIL** : vous pouvez utiliser la liste **d’inventaire** des appareils pour afficher des informations sur les appareils de votre entreprise. Dans le volet de navigation, choisissez Inventaire **des appareils**. Pour plus d’informations, voir [Gérer les appareils dans Microsoft Defender entreprise](mdb-manage-devices.md). |
| **Appareils vulnérables** | Le rapport sur les appareils vulnérables fournit des informations sur les appareils et les tendances. Utilisez la colonne **Tendances** pour afficher des informations sur les appareils qui ont eu des alertes au cours des 30 derniers jours. Utilisez la colonne **État** pour afficher les informations de capture instantanée actuelles sur les appareils qui ont des alertes. Pour accéder à ce rapport, dans le volet de navigation, sélectionnez **Appareils** **ReportsEndpointsVulnerable** >  > .<br/><br/>**CONSEIL** : vous pouvez utiliser la liste **d’inventaire** des appareils pour afficher des informations sur les appareils de votre entreprise. Dans le volet de navigation, choisissez Inventaire **des appareils**. Pour plus d’informations, voir [Gérer les appareils dans Microsoft Defender entreprise](mdb-manage-devices.md). |
| **Protection web** | Le rapport de protection web indique les tentatives d’accès aux sites de hameçonnage, aux vecteurs de programmes malveillants, aux sites d’exploitation, aux sites de réputation basse ou non confiance et aux sites explicitement bloqués. Les catégories de sites bloqués comprennent le contenu pour adultes, les sites de loisirs, les sites de responsabilité légale, etc. Pour accéder à ce rapport, dans le volet de navigation, choisissez **ReportsEndpointsWeb** >  >  **Protection**.<br/><br/>**CONSEIL** : si vous n’avez pas encore configuré la protection web pour votre entreprise, sélectionnez le **bouton Paramètres** dans un affichage de rapport. Ensuite, sous **Règles**, choisissez **Filtrage de contenu Web**. Pour en savoir plus sur le filtrage de contenu web, voir [Filtrage de contenu Web](../defender-endpoint/web-content-filtering.md). |

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise</a>. Vos commentaires sont les bienvenus.
>

## <a name="see-also"></a>Voir aussi

- [Commencer à utiliser Microsoft Defender pour les entreprises](mdb-get-started.md)

- [Afficher et gérer les incidents dans Microsoft Defender entreprise](mdb-view-manage-incidents.md)

- [Gérer les appareils dans Microsoft Defender pour les entreprises](mdb-manage-devices.md)