---
title: Forum aux questions lors de l’activation de Microsoft 365 Defender
description: Obtenez des réponses aux questions les plus fréquemment posées sur les licences, les autorisations, les paramètres initiaux et d’autres produits et services liés à l’activation de Microsoft 365 Defender
keywords: forum aux questions, FAQ, GCC, prise en main, activer Microsoft 365 Defender, Microsoft 365 Defender, M365, sécurité, emplacement des données, autorisations requises, éligibilité de la licence, page paramètres
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 782751ad3a554250095bdfe020a2ccf01b4ccba0
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68051385"
---
# <a name="frequently-asked-questions-when-turning-on-microsoft-365-defender"></a>Forum aux questions lors de l’activation de Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Lisez les réponses aux questions les plus fréquemment posées sur l’activation [des Microsoft 365 Defender](microsoft-365-defender.md), notamment les licences et autorisations requises, le déploiement des services de support et les paramètres initiaux.

Pour obtenir des instructions sur la façon d’activer le service, [lisez Activer Microsoft 365 Defender](m365d-enable.md).

## <a name="i-dont-have-a-microsoft-365-e5-license-can-i-still-use-microsoft-365-defender"></a>Je n’ai pas de licence Microsoft 365 E5. Puis-je toujours utiliser Microsoft 365 Defender ?

Les clients disposant des licences non E5 suivantes peuvent utiliser Microsoft 365 Defender :

- Microsoft Defender pour point de terminaison
- Microsoft Defender pour l’identité
- Microsoft Defender for Cloud Apps
- Defender pour Office 365 (Plan 2)

Pour obtenir la liste complète des licences prises en charge, [lisez les exigences en matière de licences](prerequisites.md#licensing-requirements).

## <a name="do-i-need-to-install-or-deploy-anything-to-start-using-microsoft-365-defender"></a>Dois-je installer ou déployer quoi que ce soit pour commencer à utiliser Microsoft 365 Defender ?

Non, Microsoft 365 Defender consolide les données des services de sécurité Microsoft 365 que vous avez déjà déployés. Une fois que vous l’activez, les expériences d’incident, d’automatisation et de chasse commencent à fonctionner dans l’étendue des produits déployés. Si aucun de ces produits n’est correctement déployé, Microsoft 365 Defender n’affiche aucune donnée et ne peut prendre aucune action.

Pour optimiser vos expériences Microsoft 365 Defender, nous vous recommandons de déployer *tous les* [produits et services de sécurité Microsoft 365](deploy-supported-services.md) pris en charge.

## <a name="where-does-microsoft-365-defender-process-and-store-my-data"></a>Où Microsoft 365 Defender traite-t-il et stocke-t-il mes données ?

Microsoft 365 Defender sélectionne automatiquement un emplacement optimal pour le centre de données où les données consolidées sont traitées et stockées. Si vous avez Microsoft Defender pour point de terminaison, il sélectionne le même emplacement que celui utilisé par Defender pour point de terminaison.

>[!NOTE]
>Microsoft Defender pour point de terminaison provisionne automatiquement dans les centres de données de l’Union européenne (UE) lorsqu’ils sont activés via Microsoft Defender pour le cloud. Microsoft 365 Defender provisionne automatiquement dans le même centre de données de l’UE pour les clients qui ont approvisionné Microsoft Defender pour point de terminaison de cette manière.

L’emplacement du centre de données s’affiche avant et après le provisionnement du service dans la page paramètres de Microsoft 365 Defender (**Paramètres > Microsoft 365 Defender**). Si vous préférez utiliser un autre emplacement de centre de données, sélectionnez **Besoin d’aide dans** le portail Microsoft 365 Defender pour contacter le support Microsoft.

## <a name="where-can-i-access-microsoft-365-defender"></a>Où puis-je accéder à Microsoft 365 Defender ?

Microsoft 365 Defender est disponible à l’adresse suivante : <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a>.

## <a name="what-permissions-do-i-need-to-access-microsoft-365-defender"></a>Quelles sont les autorisations dont j’ai besoin pour accéder à Microsoft 365 Defender ?

Les comptes auxquels les rôles Azure Active Directory (Azure AD) suivants sont affectés peuvent accéder à Microsoft 365 Defender fonctionnalités et données :

- Administrateur général
- Administrateur de sécurité
- Opérateur de sécurité
- Lecteur général
- Lecteur de sécurité
- Administrateur de conformité
- Administrateur de conformité des données
- Administrateur de l'application
- Administrateur de l'application cloud


> [!NOTE]
> Les paramètres de contrôle d’accès en fonction du rôle dans Microsoft Defender pour point de terminaison influencent l’accès aux données. Pour plus d’informations, voir la [gestion de l’accès Microsoft 365 Defender](m365d-permissions.md).

## <a name="what-time-zone-does-microsoft-365-defender-default-to"></a>À quel fuseau horaire Microsoft 365 Defender par défaut ?

Par défaut, Microsoft 365 Defender affiche les informations d’heure dans le fuseau horaire UTC. Vous pouvez modifier ce paramètre pour utiliser votre fuseau horaire local. [En savoir plus sur la définition du fuseau horaire](m365d-time-zone.md)

## <a name="how-can-i-learn-about-new-microsoft-365-defender-feature-and-ui-updates"></a>Comment puis-je en savoir plus sur les nouvelles fonctionnalités Microsoft 365 Defender et les mises à jour de l’interface utilisateur ?

Microsoft fournit régulièrement des informations via les différents canaux, notamment :

- Centre [de messages](../../admin/manage/message-center.md) dans Centre d'administration Microsoft 365
- Blogposts in the [Microsoft 365 security & compliance tech community](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/bg-p/securityprivacycompliance)

Obtenez les dernières expériences disponibles publiquement en activant les [fonctionnalités en préversion](preview.md).

## <a name="related-topics"></a>Voir aussi

- [vue d’ensemble de Microsoft 365 Defender](microsoft-365-defender.md)
- [Activez Microsoft 365 Defender](m365d-enable.md).
- [Conditions requises et autres conditions préalables relatives aux licences](prerequisites.md)
- [Déployer les services pris en charge](deploy-supported-services.md)
- [Activer les fonctionnalités d’aperçu](preview.md)
