---
title: Forum aux questions lors de l’activation de Microsoft 365 Defender
description: Obtenez des réponses aux questions les plus fréquemment posées sur la gestion des licences, des autorisations, des paramètres initiaux et d’autres produits et services liés à l’activation de Microsoft 365 Defender
keywords: Forum aux questions, FAQ, GCC, mise en route, activer le MTP, protection Microsoft contre les menaces, M365, sécurité, emplacement des données, autorisations requises, éligibilité de la licence, page Paramètres
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 3dae9f208f5bb08d694322eb9f7cff35986930da
ms.sourcegitcommit: d7975c391e03eeb96e29c1d02e77d2a1433ea67c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "48920489"
---
# <a name="frequently-asked-questions-when-turning-on-microsoft-365-defender"></a>Forum aux questions lors de l’activation de Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Lisez les réponses aux questions les plus fréquemment posées sur l’activation de [Microsoft 365 Defender](microsoft-threat-protection.md), notamment les licences et autorisations requises, le déploiement des services de prise en charge et les paramètres initiaux.

Pour obtenir des instructions sur la façon d’activer le service, [Lisez activer Microsoft 365 Defender](mtp-enable.md).

## <a name="i-dont-have-a-microsoft-365-e5-license-can-i-still-use-microsoft-365-defender"></a>Je n’ai pas de licence Microsoft 365 E5. Puis-je toujours utiliser Microsoft 365 Defender ?

Les clients disposant des licences non E5 suivantes peuvent utiliser Microsoft 365 Defender :

- Microsoft Defender pour point de terminaison
- Microsoft Defender pour identité
- Microsoft Cloud App Security
- Defender pour Office 365 (plan 2)
 
Pour obtenir la liste complète des licences prises en charge, [Lisez les conditions requises en matière de licences](prerequisites.md#licensing-requirements).

## <a name="do-i-need-to-install-or-deploy-anything-to-start-using-microsoft-365-defender"></a>Dois-je installer ou déployer quoi que ce soit pour commencer à utiliser Microsoft 365 Defender ?

Non, Microsoft 365 Defender consolide les données des services de sécurité Microsoft 365 que vous avez déjà déployés. Une fois que vous l’activez, l’incident, l’automatisation et l’expérience de la chasse commenceront à fonctionner dans l’étendue des produits déployés. Si aucun de ces produits n’est déployé correctement, Microsoft 365 Defender n’affiche pas de données et ne peut effectuer aucune action.

Pour optimiser vos expériences Microsoft 365 Defender, nous vous recommandons de déployer *tous les* [produits et services de sécurité Microsoft 365](deploy-supported-services.md)pris en charge.

## <a name="where-does-microsoft-365-defender-process-and-store-my-data"></a>Où Microsoft 365 Defender traite-t-il et stocke-t-il mes données ?
Microsoft 365 Defender sélectionne automatiquement un emplacement optimal pour le centre de données où les données consolidées sont traitées et stockées. Si vous disposez de Microsoft Defender for Endpoint, il sélectionne le même emplacement que celui utilisé par Defender for Endpoint.

>[!NOTE]
>Microsoft Defender for Endpoint provisions automatiques dans les centres de données de l’Union européenne (UE) lors de l’activation via Azure Defender. Microsoft 365 Defender est automatiquement mis en service dans le même centre de données UE pour les clients qui ont configuré Microsoft Defender pour un point de terminaison de cette manière. 

L’emplacement du centre de données est affiché avant et après la mise en service du service dans la page Paramètres de Microsoft 365 Defender ( **paramètres > microsoft 365 Defender** ). Si vous préférez utiliser un autre emplacement pour les centres de données, sélectionnez **besoin d’aide ?** dans le centre de sécurité Microsoft 365 pour contacter le support Microsoft.

## <a name="where-can-i-access-microsoft-365-defender"></a>Où puis-je accéder à Microsoft 365 Defender ?

Microsoft 365 Defender est disponible dans le centre de sécurité Microsoft 365. Pour accéder au centre de sécurité, accédez à l’URL [https://security.microsoft.com](https://security.microsoft.com) .

##  <a name="what-permissions-do-i-need-to-access-microsoft-365-defender-in-microsoft-365-security-center"></a>Quelles sont les autorisations nécessaires pour accéder à Microsoft 365 Defender dans le centre de sécurité Microsoft 365 ?

Comptes affectés les rôles Azure Active Directory (AD) suivants peuvent accéder aux fonctionnalités et aux données de Microsoft 365 Defender :

- Administrateur général
- Administrateur de sécurité
- Opérateur de sécurité
- Lecteur général
- Lecteur de sécurité

>[!NOTE]
>Les paramètres de contrôle d’accès basé sur un rôle dans Microsoft Defender pour le point de terminaison influent sur l’accès aux données. Pour plus d’informations, consultez la rubrique [Managing Access to Microsoft 365 Defender](mtp-permissions.md).

## <a name="what-time-zone-does-microsoft-365-defender-default-to"></a>Sur quels fuseaux horaires la valeur par défaut de Microsoft 365 Defender est-elle définie ?
Par défaut, Microsoft 365 Defender affiche les informations d’heure dans le fuseau horaire UTC. Vous pouvez modifier ce paramètre pour utiliser votre fuseau horaire local. [En savoir plus sur la définition du fuseau horaire](mtp-time-zone.md)

## <a name="how-can-i-learn-about-new-microsoft-365-defender-feature-and-ui-updates"></a>Comment puis-je en savoir plus sur la nouvelle fonctionnalité de Microsoft 365 Defender et les mises à jour de l’interface utilisateur ?

Microsoft fournit régulièrement des informations par le biais des différents canaux, notamment :

- [Centre de messages](../../admin/manage/message-center.md) dans le centre d’administration Microsoft 365
- Blogposts dans la [communauté technique de conformité des & de sécurité Microsoft 365](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/bg-p/securityprivacycompliance)

Obtenez les dernières expériences disponibles sur le public en activant l' [aperçu des fonctionnalités](preview.md).

## <a name="is-microsoft-365-defender-available-for-us-government-community-cloud-gcc-or-gcc-high"></a>Microsoft 365 Defender est-il disponible pour le Cloud Community Government (GCC) ou GCC High ?
Il n’est pas disponible pour le moment.

## <a name="related-topics"></a>Rubriques connexes

- [Vue d’ensemble de Microsoft 365 Defender](microsoft-threat-protection.md)
- [Activez Microsoft 365 Defender](mtp-enable.md).
- [Conditions requises et autres conditions préalables relatives aux licences](prerequisites.md)
- [Déployer les services pris en charge](deploy-supported-services.md)
- [Activer les fonctionnalités d’aperçu](preview.md)
