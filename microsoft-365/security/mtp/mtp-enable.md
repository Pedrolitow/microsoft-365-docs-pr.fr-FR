---
title: Activer Microsoft 365 Defender dans le Centre de sécurité Microsoft 365
description: Découvrez comment activer Microsoft 365 Defender et commencer à intégrer votre incident de sécurité et votre réponse.
keywords: commencer, activer MTP, Protection Microsoft contre les menaces, M365, sécurité, emplacement des données, autorisations requises, éligibilité aux licences, page paramètres
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
ms.openlocfilehash: 19f035a271626077911b05082a4aba6d67355cdb
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49930221"
---
# <a name="turn-on-microsoft-365-defender"></a>Activer Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[Microsoft 365 Defender](microsoft-threat-protection.md) unifie votre processus de réponse aux incidents en intégrant des fonctionnalités clés dans Microsoft Defender pour le point de terminaison, Microsoft Defender pour Office 365, Microsoft Cloud App Security et Microsoft Defender pour l’identité. Cette expérience unifiée ajoute des fonctionnalités puissantes auxquelles vous pouvez accéder dans le Centre de sécurité Microsoft 365.

Microsoft 365 Defender s’allume automatiquement lorsque les clients éligibles ayant les autorisations requises visitent le Centre de sécurité Microsoft 365. Lisez cet article pour comprendre les différents éléments prérequis et la façon dont Microsoft 365 Defender est mise en service.

## <a name="check-license-eligibility-and-required-permissions"></a>Vérifier l’éligibilité aux licences et les autorisations requises

Une licence pour un produit de sécurité Microsoft 365 vous permet généralement d’utiliser Microsoft 365 Defender dans le Centre de sécurité Microsoft 365 sans coût de licence supplémentaire. Nous vous recommandons d’obtenir une licence Microsoft 365 E5, E5 Security, A5 ou A5 Security ou une combinaison valide de licences qui donne accès à tous les services pris en charge.

Pour obtenir des informations détaillées sur les licences, [lisez les exigences de licence.](prerequisites.md#licensing-requirements)

### <a name="check-your-role"></a>Vérifier votre rôle

Vous devez être administrateur **général ou** **administrateur** de sécurité dans Azure Active Directory pour activer Microsoft 365 Defender. [Afficher vos rôles dans Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-manage-roles-portal)

## <a name="supported-services"></a>Services pris en charge

Microsoft 365 Defender regroupe les données des différents services pris en charge que vous avez déjà déployés. Il traitera et stockera les données de manière centralisée pour identifier les nouvelles informations et rendre les flux de travail de réponse centralisés possibles. Il le fait sans affecter les déploiements, paramètres ou données existants associés aux services intégrés.

Pour obtenir la meilleure protection et optimiser Microsoft 365 Defender, nous vous recommandons de déployer tous les services pris en charge applicables sur votre réseau. Pour plus d’informations, [voir sur le déploiement des services pris en charge.](deploy-supported-services.md)

## <a name="before-starting-the-service"></a>Avant de démarrer le service

Avant d’activer le service, le Centre de sécurité Microsoft 365 ([security.microsoft.com](https://security.microsoft.com)) affiche la page des paramètres  de Microsoft 365 Defender lorsque vous sélectionnez **Incidents,** Centre de sécurité ou Recherche dans le volet de navigation. Ces éléments de navigation ne sont pas affichés si vous n’êtes pas éligible pour utiliser Microsoft 365 Defender.

![Image de la page des paramètres de Microsoft 365 Defender affichée si Microsoft 365 Defender n’a pas été désactivé dans les paramètres de Microsoft 365 Defender dans le Centre de sécurité ](../../media/mtp-enable/mtp-settings.png)
 *Microsoft 365*

## <a name="starting-the-service"></a>Démarrage du service

Pour activer Microsoft 365 Defender, sélectionnez simplement Activer **Microsoft 365 Defender** et appliquez la modification. Vous pouvez également accéder à cette option en sélectionnant **Paramètres** ([security.microsoft.com/settings](https://security.microsoft.com/settings)) dans le volet de navigation, puis en sélectionnant **Microsoft 365 Defender**.

> [!NOTE]
> Si vous ne voyez pas **Paramètres** dans le volet de navigation ou si vous n’avez pas pu accéder à la page, vérifiez vos autorisations et licences.

### <a name="data-center-location"></a>Emplacement du centre de données

Microsoft 365 Defender stockera et traitera les données au même emplacement que celui utilisé par [Microsoft Defender pour le point de terminaison.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy) Si vous n’avez pas Microsoft Defender pour point de terminaison, un nouvel emplacement de centre de données est automatiquement sélectionné en fonction de l’emplacement des services de sécurité Microsoft 365 actifs. L’emplacement du centre de données sélectionné est affiché à l’écran.

Sélectionnez **Besoin d’aide ?** dans le Centre de sécurité Microsoft 365 pour contacter le support Microsoft concernant la mise en service de Microsoft 365 Defender dans un autre emplacement de centre de données.

> [!NOTE]
> Microsoft Defender pour le point de terminaison met automatiquement en services les centres de données de l’Union européenne (UE) lorsqu’il est allumé par le biais d’Azure Defender. Microsoft 365 Defender sera automatiquement mis en service dans le même centre de données de l’UE pour les clients qui ont mis en service Defender pour endpoint de cette manière.

### <a name="confirm-that-the-service-is-on"></a>Vérifiez que le service est activé

Une fois le service configuré, il ajoute :

- [Gestion des incidents](incidents-overview.md)
- Centre de notifications pour la gestion des [examen et réponse automatisés](mtp-autoir.md)
- [Fonctionnalités de recherche](advanced-hunting-overview.md) avancées

![Image du volet de navigation du Centre de sécurité Microsoft 365 avec Microsoft 365 Defender qui propose le Centre de sécurité Microsoft 365 avec la gestion des incidents et d’autres fonctionnalités de ](../../media/mtp-enable/mtp-on.png)
 *Microsoft 365 Defender*

### <a name="getting-microsoft-defender-for-identity-data"></a>Obtention de données Microsoft Defender pour l’identité

Pour partager des données Microsoft Defender pour l’identité avec Microsoft 365 Defender, assurez-vous que Microsoft Cloud App Security et l’intégration de Microsoft Defender pour l’identité sont allumés. [En savoir plus sur cette intégration.](https://docs.microsoft.com/cloud-app-security/mdi-integration)

## <a name="get-assistance"></a>Obtenir de l'aide

Pour obtenir des réponses aux questions les plus fréquemment posées sur l’accès à Microsoft 365 Defender, [lisez le FAQ.](mtp-enable-faq.md)

Le personnel du support microsoft peut vous aider à fournir ou à désapprovisioner le service et les ressources associées sur votre client. Pour obtenir de l’aide, **sélectionnez Besoin d’aide ?** dans le Centre de sécurité Microsoft 365. Lorsque vous contactez le support technique, mentionnez Microsoft 365 Defender.

## <a name="related-topics"></a>Rubriques associées

- [Forum aux questions](mtp-enable-faq.md)
- [Conditions requises et autres conditions préalables relatives aux licences](prerequisites.md)
- [Déployer les services pris en charge](deploy-supported-services.md)
- [Vue d’ensemble de Microsoft 365 Defender](microsoft-threat-protection.md)
- [Vue d’ensemble de Microsoft Defender for Endpoint](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- [Vue d’ensemble de Defender pour Office 365](../office-365-security/office-365-atp.md)
- [Vue d’ensemble de Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)
- [Vue d’ensemble de Microsoft Defender for Identity](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)
- [Microsoft Defender pour le stockage des données de point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy)
