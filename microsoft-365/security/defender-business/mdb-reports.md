---
title: Rapports dans Microsoft Defender pour Entreprises (prévisualisation)
description: Obtenir une vue d’ensemble des rapports disponibles dans Microsoft Defender pour Entreprises (prévisualisation)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 01/06/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 819a2cb286459cb6741ecd6f1da12bb2b3fa9634
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61942787"
---
# <a name="reports-in-microsoft-defender-for-business-preview"></a>Rapports dans Microsoft Defender pour Entreprises (prévisualisation)

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et [](https://aka.ms/mdb-preview) sera progressivement mis en place pour les clients et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un ensemble initial de [scénarios](mdb-tutorials.md#try-these-preview-scenarios)et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. Microsoft Defender pour Entreprise (prévisualisation) inclut plusieurs rapports, comme décrit dans le tableau suivant :<br/><br/>

Plusieurs rapports sont disponibles dans le portail Microsoft 365 Defender ( [https://security.microsoft.com](https://security.microsoft.com) ). Cet article décrit ces rapports, leur utilisation et leur recherche.

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise.</a> Vos commentaires sont les bienvenus.
>

<br/><br/>

## <a name="reports-in-defender-for-business"></a>Rapports dans Defender for Business

|Rapport  |Description  |
|---------|---------|
| **Rapport de sécurité**  | Le rapport de sécurité fournit des informations sur les identités, les appareils et les applications de votre entreprise. Pour accéder à ce rapport, dans le volet de navigation, sélectionnez **Rapport**  >  **de sécurité** générale des  >  **rapports.** <br/><br/>**CONSEIL** Vous pouvez afficher des informations similaires sur la page d’accueil de votre portail Microsoft 365 Defender ( [https://security.microsoft.com](https://security.microsoft.com) ). |
| **Protection contre les menaces**  | Le rapport sur la protection contre les menaces fournit des informations sur les alertes et les tendances des alertes. Utilisez la **colonne Tendances des alertes** pour afficher des informations sur les alertes déclenchées au cours des 30 derniers jours. Utilisez la **colonne État de l’alerte** pour afficher les informations de capture instantanée actuelles sur les alertes, telles que les catégories d’alertes non résolues et leur classification. Pour accéder à ce rapport, dans le volet de navigation, sélectionnez **Rapports**  >  **Points de terminaison protection** contre  >  **les menaces**. <br/><br/>**CONSEIL**: vous pouvez également utiliser la liste **Incidents** pour afficher des informations sur les alertes. Dans le volet de navigation, choisissez **Incidents** pour afficher et gérer les incidents actuels. Pour plus d’informations, voir [Afficher et gérer les incidents dans Microsoft Defender entreprise (prévisualisation).](mdb-view-manage-incidents.md) |
| **Intégrité et conformité des appareils** | Le rapport sur l’état et la conformité de l’appareil fournit des informations sur l’état et les tendances de l’appareil. Vous pouvez utiliser ce rapport pour déterminer si les capteurs Defender entreprise (prévisualisation) fonctionnent correctement sur les appareils et l’état actuel Antivirus Microsoft Defender. Pour accéder à ce rapport, dans le volet de navigation, sélectionnez **Points** de terminaison rapports État  >  **d’état** et  >  **conformité de l’appareil.** <br/><br/>**CONSEIL**: vous pouvez utiliser la liste **d’inventaire** des appareils pour afficher des informations sur les appareils de votre entreprise. Dans le volet de navigation, choisissez **Inventaire des appareils.** Pour plus d’informations, voir [Gérer les appareils dans Microsoft Defender entreprise (prévisualisation).](mdb-manage-devices.md) |
| **Appareils vulnérables** | Le rapport sur les appareils vulnérables fournit des informations sur les appareils et les tendances. Utilisez la colonne **Tendances** pour afficher des informations sur les appareils qui ont eu des alertes au cours des 30 derniers jours. Utilisez la colonne **État** pour afficher les informations de capture instantanée actuelles sur les appareils qui ont des alertes. Pour accéder à ce rapport, dans le volet de navigation, sélectionnez **Points** de terminaison de rapports - Appareils  >  **vulnérables.**  >  <br/><br/>**CONSEIL**: vous pouvez utiliser la liste **d’inventaire** des appareils pour afficher des informations sur les appareils de votre entreprise. Dans le volet de navigation, choisissez **Inventaire des appareils.** Pour plus d’informations, voir [Gérer les appareils dans Microsoft Defender entreprise (prévisualisation).](mdb-manage-devices.md) |
| **Protection web** | Le rapport de protection web indique les tentatives d’accès aux sites de hameçonnage, aux vecteurs de programmes malveillants, aux sites d’exploitation, aux sites de réputation basse ou non confiance et aux sites explicitement bloqués. Les catégories de sites bloqués comprennent le contenu pour adultes, les sites de loisirs, les sites de responsabilité légale, etc. Pour accéder à ce rapport, dans le volet de navigation, sélectionnez **Rapports**  >  **Points de terminaison**  >  **Web Protection**.<br/><br/>**CONSEIL**: si vous n’avez pas encore configuré la protection web pour votre entreprise, sélectionnez le **bouton Paramètres** dans un affichage de rapport. Ensuite, sous **Règles,** choisissez **filtrage de contenu Web**. Pour en savoir plus sur le filtrage de contenu web, voir [Filtrage de contenu Web.](../defender-endpoint/web-content-filtering.md) |

## <a name="see-also"></a>Voir aussi

- [Commencer à utiliser Microsoft Defender pour les entreprises (prévisualisation)](mdb-get-started.md)

- [Afficher et gérer les incidents dans Microsoft Defender entreprise (prévisualisation)](mdb-view-manage-incidents.md)

- [Gérer les appareils dans Microsoft Defender pour Entreprises (prévisualisation)](mdb-manage-devices.md)
