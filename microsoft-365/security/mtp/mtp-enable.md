---
title: Activer Microsoft 365 Defender dans le centre de sécurité Microsoft 365
description: Découvrez comment activer Microsoft 365 Defender et commencer à intégrer votre incident de sécurité et votre réponse.
keywords: prise en main, activer le MTP, protection Microsoft contre les menaces, M365, sécurité, emplacement des données, autorisations requises, éligibilité des licences, page Paramètres
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
ms.openlocfilehash: fbe98b814b253551432ea35102f2bd6eeba921f8
ms.sourcegitcommit: 1beaf89d2faa32f11fe1613be2fa2b31c4bc4a91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "49602085"
---
# <a name="turn-on-microsoft-365-defender"></a>Activer Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[Microsoft 365 Defender](microsoft-threat-protection.md) unifie votre processus de réponse aux incidents en intégrant les fonctionnalités clés de Microsoft Defender pour le point de terminaison, Microsoft Defender pour Office 365, Microsoft Cloud App Security et Microsoft Defender for Identity. Cette expérience unifiée ajoute des fonctionnalités puissantes auxquelles vous pouvez accéder dans le Centre de sécurité Microsoft 365.

Microsoft 365 Defender s’active automatiquement lorsque les clients éligibles disposant des autorisations requises sont le centre de sécurité Microsoft 365. Lisez cet article pour comprendre les différentes conditions préalables et la configuration de Microsoft 365 Defender.

## <a name="check-license-eligibility-and-required-permissions"></a>Vérifier l’éligibilité de la licence et les autorisations requises
Une licence pour un produit de sécurité Microsoft 365 vous permet généralement d’utiliser Microsoft 365 Defender dans le centre de sécurité Microsoft 365 sans coût de licence supplémentaire. Nous vous recommandons d’obtenir une licence de sécurité Microsoft 365 E5, E5 sécurité, a5 ou a5 ou une combinaison valide de licences qui donne accès à tous les services pris en charge.

Pour obtenir des informations détaillées sur les licences, [Lisez les conditions relatives aux licences](prerequisites.md#licensing-requirements).

### <a name="check-your-role"></a>Vérifier votre rôle
Vous devez être **administrateur général** ou administrateur de **sécurité** dans Azure Active Directory pour activer Microsoft 365 Defender. [Afficher vos rôles dans Azure AD](https://docs.microsoft.com//azure/active-directory/users-groups-roles/directory-manage-roles-portal)

## <a name="supported-services"></a>Services pris en charge
Microsoft 365 Defender agrège les données à partir des différents services pris en charge que vous avez déjà déployés. Il traitera et stockera les données de manière centralisée afin d’identifier les nouvelles idées et de créer des flux de travail de réponse centralisée. Il effectue cette opération sans affecter les déploiements, paramètres ou données existants associés aux services intégrés.

Pour bénéficier de la meilleure protection et optimiser Microsoft 365 Defender, nous vous recommandons de déployer tous les services pris en charge applicables sur votre réseau. Pour plus d’informations, consultez la rubrique [Deploying Supported services](deploy-supported-services.md).

## <a name="before-starting-the-service"></a>Avant de démarrer le service
Avant d’activer le service, le centre de sécurité Microsoft 365 ([Security.Microsoft.com](https://security.microsoft.com)) affiche la page Paramètres de Microsoft 365 Defender lorsque vous sélectionnez **incidents**, **Centre de maintenance** ou **sélection** dans le volet de navigation. Ces éléments de navigation ne s’affichent pas si vous n’êtes pas éligible à l’utilisation de Microsoft 365 Defender.

![Image de la page Paramètres de Microsoft 365 Defender affichée si Microsoft 365 Defender n’a pas été activé pour les ](../../media/mtp-enable/mtp-settings.png)
 *paramètres de Microsoft 365 Defender dans le centre de sécurité Microsoft 365*

## <a name="starting-the-service"></a>Démarrage du service
Pour activer Microsoft 365 Defender, il vous suffit de sélectionner **activer microsoft 365 Defender** et d’appliquer la modification. Vous pouvez également accéder à cette option en sélectionnant **paramètres** ([Security.Microsoft.com/Settings](https://security.microsoft.com/settings)) dans le volet de navigation, puis en sélectionnant **Microsoft 365 Defender**.

>[!NOTE]
>Si vous ne voyez pas les **paramètres** dans le volet de navigation ou que vous n’avez pas accès à la page, vérifiez vos autorisations et licences.

### <a name="data-center-location"></a>Emplacement du centre de données
Microsoft 365 Defender stockera et traite les données dans le [même emplacement que celui utilisé par Microsoft Defender pour le point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy). Si vous ne disposez pas de Microsoft Defender for Endpoint, un nouvel emplacement de centre de données est automatiquement sélectionné en fonction de l’emplacement des services de sécurité Microsoft 365 actifs. L’emplacement du centre de données sélectionné est affiché à l’écran. 

Sélectionnez **besoin d’aide ?** dans le centre de sécurité Microsoft 365 pour contacter le support Microsoft concernant la mise en service de Microsoft 365 Defender dans un autre emplacement de centre de données. 

>[!NOTE]
>Microsoft Defender for Endpoint provisions automatiques dans les centres de données de l’Union européenne (UE) lors de l’activation via Azure Defender. Microsoft 365 Defender est automatiquement mis en service dans le même centre de données UE pour les clients qui ont configuré Defender pour le système d’extrémité de cette manière. 

### <a name="confirm-that-the-service-is-on"></a>Vérifiez que le service est activé
Une fois le service configuré, il ajoute :

- [Gestion des incidents](incidents-overview.md)
- Centre de notifications pour la gestion des [examen et réponse automatisés](mtp-autoir.md)
- Fonctionnalités de [chasse avancées](advanced-hunting-overview.md)

![Image du volet de navigation du centre de sécurité Microsoft 365 avec les fonctionnalités Microsoft 365 Defender ](../../media/mtp-enable/mtp-on.png)
 *Microsoft 365 Centre de sécurité avec gestion des incidents et autres fonctionnalités Microsoft 365 Defender*

### <a name="getting-microsoft-defender-for-identity-data"></a>Obtention de Microsoft Defender pour les données d’identité
Pour partager Microsoft Defender pour les données d’identité avec Microsoft 365 Defender, assurez-vous que Microsoft Cloud App Security et Microsoft Defender for Identity Integration sont activés. [Découvrez cette intégration](https://docs.microsoft.com/cloud-app-security/aatp-integration)


## <a name="get-assistance"></a>Obtenir de l'aide

Pour obtenir des réponses aux questions les plus fréquemment posées sur l’activation de Microsoft 365 Defender, [Lisez le Forum aux](mtp-enable-faq.md)questions.

Le personnel du support Microsoft peut vous aider à mettre en service ou à mettre hors service le service et les ressources associées sur votre client. Pour obtenir de l’aide, sélectionnez **besoin d’aide ?** dans le centre de sécurité Microsoft 365. Lorsque vous contactez le support technique, mentionnez Microsoft 365 Defender.

## <a name="related-topics"></a>Rubriques connexes

- [Forum aux questions](mtp-enable-faq.md)
- [Conditions requises et autres conditions préalables relatives aux licences](prerequisites.md)
- [Déployer les services pris en charge](deploy-supported-services.md)
- [Vue d’ensemble de Microsoft 365 Defender](microsoft-threat-protection.md)
- [Vue d’ensemble de Microsoft Defender pour les points de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- [Vue d’ensemble de Defender for Office 365](../office-365-security/office-365-atp.md)
- [Vue d’ensemble de Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)
- [Vue d’ensemble de Microsoft Defender for Identity](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)
- [Microsoft Defender pour le stockage des données de point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy)
