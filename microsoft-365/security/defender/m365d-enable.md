---
title: Activer Microsoft 365 Defender
description: Découvrez comment activer Microsoft 365 Defender et commencer à intégrer votre incident de sécurité et votre réponse.
keywords: prise en main, activer Microsoft 365 Defender, Microsoft 365 Defender, M365, sécurité, emplacement des données, autorisations requises, éligibilité de la licence, page paramètres
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
- M365-security-compliance
- m365solution-getstarted
- highpri
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: cac5660ca9ee61aa11fffe61cc67e1d2a6594231
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67475975"
---
# <a name="turn-on-microsoft-365-defender"></a>Activer Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[Microsoft 365 Defender](microsoft-365-defender.md) unifie votre processus de réponse aux incidents en intégrant des fonctionnalités clés dans Microsoft Defender pour point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender for Cloud Apps et Microsoft Defender pour Identity. Cette expérience unifiée ajoute des fonctionnalités puissantes accessibles dans le portail Microsoft 365 Defender.

Microsoft 365 Defender s’active automatiquement lorsque les clients éligibles disposant des autorisations requises visitent Microsoft 365 Defender portail. Lisez cet article pour comprendre les différents prérequis et la façon dont Microsoft 365 Defender est provisionné.

## <a name="check-license-eligibility-and-required-permissions"></a>Vérifier l’éligibilité de la licence et les autorisations requises

Une licence pour un produit de sécurité Microsoft 365 vous permet généralement d’utiliser Microsoft 365 Defender sans frais de licence supplémentaires. Nous vous recommandons d’obtenir une licence de sécurité Microsoft 365 E5, E5 Security, A5 ou A5 ou une combinaison valide de licences qui fournit l’accès à tous les services pris en charge.

Pour obtenir des informations détaillées sur les licences, [lisez les conditions d’octroi de la licence](prerequisites.md#licensing-requirements).

### <a name="check-your-role"></a>Vérifier votre rôle

Vous devez être l’un des rôles suivants pour activer Microsoft 365 Defender :

- Administrateur général
- Administrateur de sécurité
- Opérateur de sécurité
- Lecteur général
- Lecteur de sécurité
- Administrateur de conformité
- Administrateur de conformité des données
- Administrateur de l'application
- Administrateur de l'application cloud

[Afficher vos rôles dans Azure AD](/azure/active-directory/users-groups-roles/directory-manage-roles-portal)

## <a name="supported-services"></a>Services pris en charge

Microsoft 365 Defender regroupe les données des différents services pris en charge que vous avez déjà déployés. Les données sont traitées et stockées de façon centralisée pour identifier les nouvelles informations et rendre possible les flux de travail de réponse centralisés. Elles les font sans affecter les déploiements, paramètres ou données existants associés aux services intégrés.

Pour obtenir la meilleure protection et optimiser Microsoft 365 Defender, nous vous recommandons de déployer tous les services pris en charge applicables sur votre réseau. Pour plus d’informations, [consultez le déploiement des services pris en charge](deploy-supported-services.md).

## <a name="onboard-to-the-service"></a>Intégrer au service
L’intégration à Microsoft 365 Defender est simple. Dans le menu de navigation, sélectionnez n’importe quel élément, tel que **incidents & alertes**, **repérage**, **centre d’actions** ou **analyse des menaces** pour lancer le processus d’intégration. 

### <a name="data-center-location"></a>Emplacement du centre de données

Microsoft 365 Defender stocke et traite les données au [même emplacement que celui utilisé par Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy). Si vous n’avez pas de Microsoft Defender pour point de terminaison, un nouvel emplacement de centre de données est automatiquement sélectionné en fonction de l’emplacement des services de sécurité Microsoft 365 actifs. L’emplacement du centre de données sélectionné s’affiche à l’écran.

**Sélectionnez Besoin d’aide dans** le portail Microsoft 365 Defender pour contacter le support Microsoft concernant l’approvisionnement Microsoft 365 Defender dans un autre emplacement de centre de données.

> [!NOTE]
> Par le passé, Microsoft Defender pour point de terminaison automatiquement approvisionné dans les centres de données de l’Union européenne (UE) lorsqu’ils sont activés via Microsoft Defender pour le cloud. Microsoft 365 Defender provisionne automatiquement dans le même centre de données de l’UE pour les clients qui ont provisionné Defender pour point de terminaison de cette manière par le passé.

### <a name="confirm-that-the-service-is-on"></a>Vérifiez que le service est activé

Une fois le service configuré, il ajoute :

- [Gestion des incidents](incidents-overview.md)
- [File d’attente des alertes](investigate-alerts.md)
- Centre de notifications pour la gestion des [examen et réponse automatisés](m365d-autoir.md)
- [Fonctionnalités avancées de chasse](advanced-hunting-overview.md)
- Analyses de menaces

:::image type="content" source="../../media/overview-incident.png" alt-text="Volet de navigation dans le portail Microsoft 365 Defender avec des fonctionnalités de Microsoft 365 Defender" lightbox="../../media/overview-incident.png":::
*portail Microsoft 365 Defender avec la gestion des incidents et d’autres fonctionnalités*

### <a name="getting-microsoft-defender-for-identity-data"></a>Obtention de données Microsoft Defender pour Identity 
Pour activer l’intégration à Microsoft Defender for Cloud Apps, vous devez vous connecter au Microsoft Defender for Cloud Apps au moins une fois.

## <a name="get-assistance"></a>Obtenir de l'aide

Pour obtenir des réponses aux questions les plus fréquemment posées sur l’activation de Microsoft 365 Defender, [lisez le FAQ](m365d-enable-faq.md).

Le personnel du support technique Microsoft peut vous aider à approvisionner ou déprovisionner le service et les ressources associées sur votre locataire. Pour obtenir de **l’aide, sélectionnez Besoin d’aide dans** le portail Microsoft 365 Defender. Lorsque vous contactez le support technique, mentionnez Microsoft 365 Defender.

## <a name="related-topics"></a>Voir aussi

- [Foire aux questions](m365d-enable-faq.md)
- [Conditions requises et autres conditions préalables relatives aux licences](prerequisites.md)
- [Déployer les services pris en charge](deploy-supported-services.md)
- [vue d’ensemble de Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender pour point de terminaison vue d’ensemble](../defender-endpoint/microsoft-defender-endpoint.md)
- [Defender pour Office 365 vue d’ensemble](../office-365-security/defender-for-office-365.md)
- [Vue d’ensemble de Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)
- [Microsoft Defender pour Identity vue d’ensemble](/azure-advanced-threat-protection/what-is-atp)
- [stockage de données Microsoft Defender pour point de terminaison](../defender-endpoint/data-storage-privacy.md)
