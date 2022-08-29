---
title: Rapports dans Microsoft Defender pour entreprises
description: Obtenez une vue d’ensemble des rapports de sécurité dans Defender entreprise. Les rapports affichent les menaces, les alertes, les vulnérabilités et l’état de l’appareil détectés.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.date: 08/11/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: fe74557403791c759838dbf6d632bc50b59698cf
ms.sourcegitcommit: 9b10e56b9e83f3a80757fa6108bebd1d80cf4178
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67320369"
---
# <a name="reports-in-microsoft-defender-for-business"></a>Rapports dans Microsoft Defender pour entreprises

Plusieurs rapports sont disponibles dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Cet article décrit ces rapports, comment vous pouvez les utiliser et comment les trouver.

## <a name="reports-in-defender-for-business"></a>Rapports dans Defender entreprise

|Rapport  |Description  |
|---------|---------|
| **Rapport de sécurité**  | Le rapport de sécurité fournit des informations sur les identités, les appareils et les applications de votre entreprise. Pour accéder à ce rapport, dans le volet de navigation, choisissez **Rapports** >  de **sécurité** **générale** > . <br/><br/>Vous pouvez afficher des informations similaires sur la page d’accueil de votre portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). |
| **Protection contre les menaces**  | Le rapport de protection contre les menaces fournit des informations sur les alertes et les tendances des alertes. Utilisez la colonne **Tendances d’alerte** pour afficher des informations sur les alertes qui ont été déclenchées au cours des 30 derniers jours. Utilisez la colonne **État de l’alerte** pour afficher les informations d’instantané actuelles sur les alertes, telles que les catégories d’alertes non résolues et leur classification. Pour accéder à ce rapport, dans le volet de navigation, choisissez **Rapports** > **Endpoints** > **Threat Protection**. <br/><br/>Vous pouvez également utiliser la liste **des incidents** pour afficher des informations sur les alertes. Dans le volet de navigation, choisissez **Incidents** pour afficher et gérer les incidents actuels. Pour plus d’informations, consultez [Afficher et gérer les incidents dans Defender entreprise](mdb-view-manage-incidents.md). |
| **Intégrité et conformité des appareils** | Le rapport sur l’intégrité et la conformité des appareils fournit des informations sur l’intégrité et les tendances des appareils. Vous pouvez utiliser ce rapport pour déterminer si les capteurs Defender entreprise fonctionnent correctement sur les appareils et l’état actuel de l’antivirus Microsoft Defender. Pour accéder à ce rapport, dans le volet de navigation, choisissez **Rapports** > **Points de terminaison** > **Intégrité et conformité de l’appareil**. <br/><br/>Vous pouvez utiliser la liste **d’inventaire des** appareils pour afficher des informations sur les appareils de votre entreprise. Dans le volet de navigation, choisissez **Inventaire des appareils**. Pour plus d’informations, consultez [Gérer les appareils dans Defender entreprise](mdb-manage-devices.md). |
| **Appareils vulnérables** | Le rapport sur les appareils vulnérables fournit des informations sur les appareils et les tendances. Utilisez la colonne **Tendances** pour afficher des informations sur les appareils qui ont reçu des alertes au cours des 30 derniers jours. Utilisez la colonne **État** pour afficher les informations d’instantané actuelles sur les appareils qui ont des alertes. Pour accéder à ce rapport, dans le volet de navigation, choisissez **Rapports** > **Points de terminaison Les** > **appareils vulnérables**.<br/><br/>**CONSEIL** : Vous pouvez utiliser la liste **d’inventaire des** appareils pour afficher des informations sur les appareils de votre entreprise. Dans le volet de navigation, choisissez **Inventaire des appareils**. Pour plus d’informations, consultez [Gérer les appareils dans Defender entreprise](mdb-manage-devices.md). |
| **Protection web** | Le rapport de protection web montre les tentatives d’accès aux sites de hameçonnage, aux vecteurs de programmes malveillants, aux sites d’exploitation, aux sites non approuvés ou à faible réputation et aux sites qui sont explicitement bloqués. Les catégories de sites bloqués incluent le contenu pour adultes, les sites de loisirs, les sites de responsabilité légale, etc. Pour accéder à ce rapport, dans le volet de navigation, choisissez **Reports** > **Endpoints** > **Web Protection**.<br/><br/>Si vous n’avez pas encore configuré la protection web pour votre entreprise, choisissez le bouton **Paramètres** dans un affichage rapport. Ensuite, sous **Règles**, choisissez **le filtrage de contenu Web**. Pour en savoir plus sur le filtrage de contenu web, consultez filtrage [de contenu web](../defender-endpoint/web-content-filtering.md). |
| **Pare-feu** | Le rapport de pare-feu affiche les connexions entrantes, sortantes et d’application bloquées. Ce rapport montre également les adresses IP distantes connectées par plusieurs appareils et les adresses IP distantes avec le plus de tentatives de connexion. <br/><br/>Si vous n’avez pas encore configuré votre protection pare-feu, dans le volet de navigation, choisissez Configuration de **l’appareil** de gestion de **la** >  configuration **des** >  points de terminaison. Pour plus d’informations, consultez [Pare-feu dans Defender pour Entreprises](mdb-firewall.md). |
| **Contrôle des appareils** | Le rapport de contrôle d’appareil affiche des informations sur l’utilisation des médias, telles que l’utilisation d’appareils de stockage amovibles dans votre organisation. |


## <a name="see-also"></a>Voir aussi

- [Prise en main de Defender entreprise](mdb-get-started.md)
- [Afficher et gérer les incidents dans Defender entreprise](mdb-view-manage-incidents.md)
- [Gérer les appareils dans Defender entreprise](mdb-manage-devices.md)
