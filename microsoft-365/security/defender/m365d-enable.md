---
title: Activer Microsoft 365 Defender
description: Découvrez comment activer Microsoft 365 Defender et commencer à intégrer votre incident de sécurité et votre réponse.
keywords: commencer, activer Microsoft 365 Defender, Microsoft 365 Defender, M365, sécurité, emplacement des données, autorisations requises, éligibilité aux licences, page paramètres
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: cf3337aa169deb21209f3396742b1764b2b191a6
ms.sourcegitcommit: a0185d6b0dd091db6e1e1bfae2f68ab0e3cf05e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58247251"
---
# <a name="turn-on-microsoft-365-defender"></a>Activer Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[Microsoft 365 Defender](microsoft-365-defender.md) unifie votre processus de réponse aux incidents en intégrant des fonctionnalités clés dans Microsoft Defender pour le point de terminaison, Microsoft Defender pour Office 365, Microsoft Cloud App Security et Microsoft Defender pour l’identité. Cette expérience unifiée ajoute de puissantes fonctionnalités accessibles sur le portail Microsoft 365 Defender web.

Microsoft 365 Defender s’allume automatiquement lorsque les clients éligibles ayant les autorisations requises visitent Microsoft 365 Defender portail. Lisez cet article pour comprendre les différents éléments prérequis et la façon Microsoft 365 Defender est mise en service.

## <a name="check-license-eligibility-and-required-permissions"></a>Vérifier l’éligibilité aux licences et les autorisations requises

Une licence à un produit Microsoft 365 sécurité vous permet généralement d’utiliser Microsoft 365 Defender sans coût de licence supplémentaire. Nous vous recommandons d’obtenir une licence Microsoft 365 E5, E5 Security, A5 ou A5 Security ou une combinaison valide de licences qui donne accès à tous les services pris en charge.

Pour obtenir des informations détaillées sur les licences, [lisez les exigences de licence.](prerequisites.md#licensing-requirements)

### <a name="check-your-role"></a>Vérifier votre rôle

Vous devez être administrateur **général ou** **administrateur** de sécurité dans Azure Active Directory pour activer Microsoft 365 Defender. [Afficher vos rôles dans Azure AD](/azure/active-directory/users-groups-roles/directory-manage-roles-portal)

## <a name="supported-services"></a>Services pris en charge

Microsoft 365 Defender regroupe les données des différents services pris en charge que vous avez déjà déployés. Il traitera et stockera les données de manière centralisée pour identifier les nouvelles informations et rendre possibles des flux de travail de réponse centralisés. Il le fait sans affecter les déploiements, paramètres ou données existants associés aux services intégrés.

Pour obtenir la meilleure protection et optimiser les Microsoft 365 Defender, nous vous recommandons de déployer tous les services pris en charge applicables sur votre réseau. Pour plus d’informations, [voir sur le déploiement des services pris en charge.](deploy-supported-services.md)

## <a name="onboard-to-the-service"></a>Intégrer au service
L’intégration à Microsoft 365 Defender est simple. Dans le menu de navigation, sélectionnez n’importe quel élément, tel que  **incidents & alertes,** de **recherche,** de centre de action ou d’analyse des menaces pour lancer le processus d’intégration. 

### <a name="data-center-location"></a>Emplacement du centre de données

Microsoft 365 Defender stockera et traitera les données au même emplacement que celui utilisé [par Microsoft Defender pour endpoint.](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy) Si vous n’avez pas Microsoft Defender pour le point de terminaison, un nouvel emplacement de centre de données est automatiquement sélectionné en fonction de l’emplacement des services de sécurité Microsoft 365 actifs. L’emplacement du centre de données sélectionné est affiché à l’écran.

Sélectionnez **Besoin d’aide ?** dans le portail Microsoft 365 Defender pour contacter le support Microsoft sur la mise en service Microsoft 365 Defender dans un autre emplacement de centre de données.

> [!NOTE]
> Dans le passé, Microsoft Defender pour point de terminaison était automatiquement mis en service dans les centres de données de l’Union européenne (UE) lorsqu’il était allumé via Azure Defender. Microsoft 365 Defender sera automatiquement mis en service dans le même centre de données de l’UE pour les clients qui ont mis en service Defender pour endpoint de cette manière dans le passé.

### <a name="confirm-that-the-service-is-on"></a>Vérifiez que le service est activé

Une fois le service configuré, il ajoute :

- [Gestion des incidents](incidents-overview.md)
- [File d’attente des alertes](investigate-alerts.md)
- Centre de notifications pour la gestion des [examen et réponse automatisés](m365d-autoir.md)
- [Fonctionnalités de recherche](advanced-hunting-overview.md) avancées
- Analyses de menaces

![Image du volet Microsoft 365 Defender navigation du portail avec des fonctionnalités Microsoft 365 Defender de Microsoft 365 Defender avec la gestion des incidents et ](../../media/overview-incident.png)
 *d’autres fonctionnalités*

### <a name="getting-microsoft-defender-for-identity-data"></a>Obtention de données Microsoft Defender pour l’identité 
Pour activer l’intégration avec Microsoft Cloud App Security, vous devez vous connecter au Microsoft Cloud App Security au moins une fois.

## <a name="get-assistance"></a>Obtenir de l'aide

Pour obtenir des réponses aux questions les plus fréquemment posées sur l’Microsoft 365 Defender, [lisez le FAQ.](m365d-enable-faq.md)

Le personnel du support microsoft peut vous aider à fournir ou à désapprovisioner le service et les ressources associées sur votre client. Pour obtenir de l’aide, **sélectionnez Besoin d’aide ?** dans Microsoft 365 Defender portail. Lorsque vous contactez le support technique, Microsoft 365 Defender.

## <a name="related-topics"></a>Rubriques connexes

- [Forum aux questions](m365d-enable-faq.md)
- [Conditions requises et autres conditions préalables relatives aux licences](prerequisites.md)
- [Déployer les services pris en charge](deploy-supported-services.md)
- [Microsoft 365 Defender vue d’ensemble](microsoft-365-defender.md)
- [Vue d’ensemble de Microsoft Defender for Endpoint](../defender-endpoint/microsoft-defender-endpoint.md)
- [Vue d’ensemble Office 365 Defender for Office 365](../office-365-security/defender-for-office-365.md)
- [Aperçu de Microsoft Cloud App Security ](/cloud-app-security/what-is-cloud-app-security)
- [Vue d’ensemble de Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp)
- [Microsoft Defender pour le stockage des données de point de terminaison](../defender-endpoint/data-storage-privacy.md)
