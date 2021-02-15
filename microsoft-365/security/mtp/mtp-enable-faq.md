---
title: Questions fréquemment posées lors de l' turning on Microsoft 365 Defender
description: Obtenez des réponses aux questions les plus fréquemment posées sur la gestion des licences, les autorisations, les paramètres initiaux et d’autres produits et services liés à l’activation de Microsoft 365 Defender
keywords: forum aux questions, FAQ, GCC, commencer, activer MTP, Protection Microsoft contre les menaces, M365, sécurité, emplacement des données, autorisations requises, éligibilité aux licences, page paramètres
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
ms.technology: m365d
ms.openlocfilehash: 2cb9aed070959644e3660188835386118d5f4d9b
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49930185"
---
# <a name="frequently-asked-questions-when-turning-on-microsoft-365-defender"></a>Questions fréquemment posées lors de l' turning on Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Lisez les réponses aux questions les plus fréquemment posées sur l’utilisation de [Microsoft 365 Defender,](microsoft-threat-protection.md)y compris les licences et autorisations requises, le déploiement des services de support et les paramètres initiaux.

Pour obtenir des instructions sur la façon d’activer le service, lisez [Activer Microsoft 365 Defender.](mtp-enable.md)

## <a name="i-dont-have-a-microsoft-365-e5-license-can-i-still-use-microsoft-365-defender"></a>Je n’ai pas de licence Microsoft 365 E5. Puis-je toujours utiliser Microsoft 365 Defender ?

Les clients titulaires des licences non E5 suivantes peuvent utiliser Microsoft 365 Defender :

- Microsoft Defender pour point de terminaison
- Microsoft Defender pour l’identité
- Microsoft Cloud App Security
- Defender pour Office 365 (Plan 2)
 
Pour obtenir la liste complète des licences pris en charge, [lisez les conditions requises pour les licences.](prerequisites.md#licensing-requirements)

## <a name="do-i-need-to-install-or-deploy-anything-to-start-using-microsoft-365-defender"></a>Dois-je installer ou déployer quoi que ce soit pour commencer à utiliser Microsoft 365 Defender ?

Non, Microsoft 365 Defender consolide les données des services de sécurité Microsoft 365 que vous avez déjà déployés. Une fois que vous l’avez mis en place, les expériences d’incident, d’automatisation et de recherche commenceront à fonctionner dans l’étendue des produits déployés. Si aucun de ces produits n’est correctement déployé, Microsoft 365 Defender n’affiche aucune donnée et ne peut pas prendre d’action.

Pour optimiser vos expériences Microsoft 365  Defender, nous vous recommandons de déployer tous les produits et services de sécurité [Microsoft 365 pris en charge.](deploy-supported-services.md)

## <a name="where-does-microsoft-365-defender-process-and-store-my-data"></a>Où Microsoft 365 Defender peut-il traiter et stocker mes données ?
Microsoft 365 Defender sélectionne automatiquement un emplacement optimal pour le centre de données où les données consolidées sont traitées et stockées. Si vous avez Microsoft Defender pour point de terminaison, il sélectionne le même emplacement que celui utilisé par Defender pour le point de terminaison.

>[!NOTE]
>Microsoft Defender pour le point de terminaison met automatiquement en services les centres de données de l’Union européenne (UE) lorsqu’il est allumé par le biais d’Azure Defender. Microsoft 365 Defender sera automatiquement mis en service dans le même centre de données de l’UE pour les clients qui ont mis en service Microsoft Defender pour endpoint de cette manière. 

L’emplacement du centre de données s’affiche avant et après la mise en service du service dans la page des paramètres de Microsoft 365 Defender ( Paramètres >**Microsoft 365 Defender**). Si vous préférez utiliser un autre emplacement de centre de données, sélectionnez Besoin d’aide **?** dans le Centre de sécurité Microsoft 365 pour contacter le support Microsoft.

## <a name="where-can-i-access-microsoft-365-defender"></a>Où puis-je accéder à Microsoft 365 Defender ?

Microsoft 365 Defender est disponible dans le Centre de sécurité Microsoft 365. Pour accéder au centre de sécurité, accédez à [https://security.microsoft.com](https://security.microsoft.com) l’URL.

##  <a name="what-permissions-do-i-need-to-access-microsoft-365-defender-in-microsoft-365-security-center"></a>De quelles autorisations ai-je besoin pour accéder à Microsoft 365 Defender dans le Centre de sécurité Microsoft 365 ?

Les comptes affectés aux rôles Azure Active Directory (AD) suivants peuvent accéder aux fonctionnalités et données de Microsoft 365 Defender :

- Administrateur général
- Administrateur de sécurité
- Opérateur de sécurité
- Lecteur général
- Lecteur de sécurité

>[!NOTE]
>Les paramètres de contrôle d’accès en fonction du rôle dans Microsoft Defender pour point de terminaison influencent l’accès aux données. Pour plus d’informations, voir [la gestion de l’accès à Microsoft 365 Defender.](mtp-permissions.md)

## <a name="what-time-zone-does-microsoft-365-defender-default-to"></a>Quel fuseau horaire Microsoft 365 Defender utilise-t-il par défaut ?
Par défaut, Microsoft 365 Defender affiche les informations d’heure dans le fuseau horaire UTC. Vous pouvez modifier ce paramètre pour utiliser votre fuseau horaire local. [En savoir plus sur la définition du fuseau horaire](mtp-time-zone.md)

## <a name="how-can-i-learn-about-new-microsoft-365-defender-feature-and-ui-updates"></a>Comment puis-je en savoir plus sur les nouvelles fonctionnalités de Microsoft 365 Defender et les mises à jour de l’interface utilisateur ?

Microsoft fournit régulièrement des informations via les différents canaux, notamment :

- Centre [de messages](../../admin/manage/message-center.md) dans le Centre d’administration Microsoft 365
- Billets de blog dans la communauté technique de sécurité et [conformité & Microsoft 365](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/bg-p/securityprivacycompliance)

Obtenez les dernières expériences disponibles publiquement en allumer les [fonctionnalités d’aperçu.](preview.md)

## <a name="is-microsoft-365-defender-available-for-us-government-community-cloud-gcc-or-gcc-high"></a>Microsoft 365 Defender est-il disponible pour le cloud communautaire du gouvernement américain (GCC) ou GCC High ?
Il n’est pas disponible pour le moment.

## <a name="related-topics"></a>Rubriques connexes

- [Présentation de Microsoft 365 Defender](microsoft-threat-protection.md)
- [Activer Microsoft 365 Defender.](mtp-enable.md)
- [Conditions requises et autres conditions préalables relatives aux licences](prerequisites.md)
- [Déployer les services pris en charge](deploy-supported-services.md)
- [Activer les fonctionnalités d’aperçu](preview.md)
