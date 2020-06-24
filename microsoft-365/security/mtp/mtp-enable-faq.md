---
title: Forum aux questions lors de l’activation de la protection contre les menaces Microsoft
description: Obtenez des réponses aux questions les plus fréquemment posées sur la gestion des licences, des autorisations, des paramètres initiaux et d’autres produits et services liés à l’activation de la protection contre les menaces Microsoft.
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
ms.openlocfilehash: 9dcfeb5616afc8953e862d6d1a542d694582b157
ms.sourcegitcommit: bd5a08785b5ec320b04b02f8776e28bce5fb448f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "44845069"
---
# <a name="frequently-asked-questions-when-turning-on-microsoft-threat-protection"></a>Forum aux questions lors de l’activation de la protection contre les menaces Microsoft

**S’applique à :**
- Protection Microsoft contre les menaces

Lisez les réponses aux questions les plus fréquemment posées sur l’activation de la [protection contre les menaces Microsoft](microsoft-threat-protection.md), y compris les licences et autorisations requises, le déploiement des services de support et les paramètres initiaux.

Pour obtenir des instructions sur la façon d’activer le service, [Lisez activer la protection contre les menaces Microsoft](mtp-enable.md).

## <a name="i-dont-have-a-microsoft-365-e5-license-can-i-still-use-microsoft-threat-protection"></a>Je n’ai pas de licence Microsoft 365 E5. Puis-je toujours utiliser Microsoft Threat Protection ?

Les clients disposant des licences non E5 suivantes peuvent utiliser Microsoft Threat Protection :

- Microsoft Defender – Protection avancée contre les menaces
- Azure Advanced Threat Protection
- Microsoft Cloud App Security
- Office 365 – Protection avancée contre les menaces (plan 2)
 
Pour obtenir la liste complète des licences prises en charge, [Lisez les conditions requises en matière de licences](prerequisites.md#licensing-requirements).

## <a name="do-i-need-to-install-or-deploy-anything-to-start-using-microsoft-threat-protection"></a>Dois-je installer ou déployer quoi que ce soit pour commencer à utiliser Microsoft Threat Protection ?

Non, Microsoft Threat Protection consolide les données des services de sécurité Microsoft 365 que vous avez déjà déployés. Une fois que vous l’activez, l’incident, l’automatisation et l’expérience de la chasse commenceront à fonctionner dans l’étendue des produits déployés. Si aucun de ces produits n’est déployé correctement, la protection de Microsoft contre les menaces n’affichera pas de données et ne pourra effectuer aucune action.

Pour optimiser vos expériences de protection contre les menaces Microsoft, nous vous recommandons de déployer *tous les* [produits et services de sécurité Microsoft 365](deploy-supported-services.md)pris en charge.

## <a name="where-does-microsoft-threat-protection-process-and-store-my-data"></a>Où le processus de protection contre les menaces Microsoft et stocke-t-il mes données ?
La protection contre les menaces Microsoft sélectionne automatiquement un emplacement optimal pour le centre de données où les données consolidées sont traitées et stockées. Si vous disposez de Microsoft Defender ATP, il sélectionne le même emplacement que celui utilisé par Microsoft Defender ATP.

>[!NOTE]
>Microsoft Defender s’approvisionne automatiquement dans les centres de données de l’Union européenne (UE) lors de l’activation via le centre de sécurité Azure. La protection Microsoft contre les menaces est automatiquement mise en service dans le centre de données de l’UE pour les clients qui ont configuré Microsoft Defender ATP de cette manière. 

L’emplacement du centre de données est affiché avant et après la mise en service du service dans la page Paramètres de protection contre les menaces Microsoft (**paramètres > protection contre les menaces Microsoft**). Si vous préférez utiliser un autre emplacement pour les centres de données, sélectionnez **besoin d’aide ?** dans le centre de sécurité Microsoft 365 pour contacter le support Microsoft.

## <a name="where-can-i-access-microsoft-threat-protection"></a>Où puis-je accéder à la protection contre les menaces Microsoft ?

Microsoft Threat Protection est disponible dans le centre de sécurité Microsoft 365. Pour accéder au centre de sécurité, accédez à l’URL [https://security.microsoft.com](https://security.microsoft.com) .

##  <a name="what-permissions-do-i-need-to-access-microsoft-threat-protection-in-microsoft-365-security-center"></a>Quelles sont les autorisations nécessaires pour accéder à Microsoft Threat Protection dans le centre de sécurité Microsoft 365 ?

Les comptes affectés aux rôles Azure Active Directory (AD) suivants peuvent accéder aux fonctionnalités et données de la Protection Microsoft contre les menaces :

- Administrateur général
- Administrateur de sécurité
- Opérateur de sécurité
- Lecteur général
- Lecteur de sécurité

>[!NOTE]
>Les paramètres de contrôle d’accès basé sur un rôle dans Microsoft Defender ATP influent sur l’accès aux données. Pour plus d’informations, consultez la rubrique [gestion de l’accès à Microsoft Threat Protection](mtp-permissions.md).

## <a name="what-time-zone-does-microsoft-threat-protection-default-to"></a>Sur quels fuseaux horaires la protection contre les menaces Microsoft est-elle par défaut ?
Par défaut, Microsoft Threat Protection affiche des informations d’heure dans le fuseau horaire UTC. Vous pouvez modifier ce paramètre pour utiliser votre fuseau horaire local. [En savoir plus sur la définition du fuseau horaire](mtp-time-zone.md)

## <a name="how-can-i-learn-about-new-microsoft-threat-protection-feature-and-ui-updates"></a>Comment puis-je obtenir des informations sur la nouvelle fonctionnalité de protection contre les menaces Microsoft et les mises à jour de l’interface utilisateur ?

Microsoft fournit régulièrement des informations par le biais des différents canaux, notamment :

- [Centre de messages](../../admin/manage/message-center.md) dans le centre d’administration Microsoft 365
- Blogposts dans la [communauté technique de conformité des & de sécurité Microsoft 365](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/bg-p/securityprivacycompliance)

Obtenez les dernières expériences disponibles sur le public en activant l' [aperçu des fonctionnalités](preview.md).

## <a name="is-microsoft-threat-protection-available-for-us-government-community-cloud-gcc-or-gcc-high"></a>La Protection Microsoft contre les menaces est-elle disponible pour cloud de la communauté pour le service public des États-Unis (GCC) ou GCC High ?
Il n’est pas disponible pour le moment.

## <a name="related-topics"></a>Sujets associés

- [Vue d’ensemble de la Protection Microsoft contre les menaces](microsoft-threat-protection.md)
- [Activez la protection contre les menaces Microsoft](mtp-enable.md).
- [Conditions requises et autres conditions préalables relatives aux licences](prerequisites.md)
- [Déployer les services pris en charge](deploy-supported-services.md)
- [Activer les fonctionnalités d’aperçu](preview.md)