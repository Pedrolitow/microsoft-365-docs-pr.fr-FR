---
title: Activer la Protection Microsoft contre les menaces dans le Centre de sécurité Microsoft 365
description: Découvrez comment activer la Protection Microsoft contre les menaces et commencer à intégrer votre incident de sécurité et votre réponse.
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
ms.openlocfilehash: b6ac30f7e32bbec80952ad4f2104032886b11503
ms.sourcegitcommit: 0650da0e54a2b484a3156b3aabe44397fbb38e00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "45016342"
---
# <a name="turn-on-microsoft-threat-protection"></a>Activer la Protection Microsoft contre les menaces

**S’applique à :**
- Protection Microsoft contre les menaces

La [protection de Microsoft contre les menaces](microsoft-threat-protection.md) unifie votre processus de réponse aux incidents en intégrant des fonctionnalités clés dans la protection avancée contre les menaces Microsoft Defender, Office 365 ATP, la sécurité des applications Cloud Microsoft et Azure ATP. Cette expérience unifiée ajoute des fonctionnalités puissantes auxquelles vous pouvez accéder dans le Centre de sécurité Microsoft 365.

La protection contre les menaces Microsoft s’active automatiquement lorsque les clients éligibles disposant des autorisations requises se reporter au centre de sécurité Microsoft 365. Lisez cet article pour comprendre les différentes conditions préalables et la configuration de la protection contre les menaces Microsoft.

## <a name="check-license-eligibility-and-required-permissions"></a>Vérifier l’éligibilité de la licence et les autorisations requises
Une licence pour un produit de sécurité Microsoft 365 vous permet généralement d’utiliser la protection Microsoft contre les menaces dans le centre de sécurité Microsoft 365 sans coût de licence supplémentaire. Nous vous recommandons d’obtenir une licence de sécurité Microsoft 365 E5, E5 sécurité, a5 ou a5 ou une combinaison valide de licences qui donne accès à tous les services pris en charge.

Pour obtenir des informations détaillées sur les licences, [Lisez les conditions relatives aux licences](prerequisites.md#licensing-requirements).

### <a name="check-your-role"></a>Vérifier votre rôle
Vous devez être **administrateur général** ou administrateur de **sécurité** dans Azure Active Directory pour activer Microsoft Threat Protection. [Afficher vos rôles dans Azure AD](https://docs.microsoft.com//azure/active-directory/users-groups-roles/directory-manage-roles-portal)

## <a name="supported-services"></a>Services pris en charge
Microsoft Threat Protection agrège les données à partir des différents services pris en charge que vous avez déjà déployés. Il traitera et stockera les données de manière centralisée afin d’identifier les nouvelles idées et de créer des flux de travail de réponse centralisée. Il effectue cette opération sans affecter les déploiements, paramètres ou données existants associés aux services intégrés.

Pour bénéficier de la meilleure protection et optimiser la protection Microsoft contre les menaces, nous vous recommandons de déployer tous les services pris en charge applicables sur votre réseau. Pour plus d’informations, consultez la rubrique [Deploying Supported services](deploy-supported-services.md).

## <a name="before-starting-the-service"></a>Avant de démarrer le service
Avant d’activer le service, le centre de sécurité Microsoft 365 ([Security.Microsoft.com](https://security.microsoft.com)) affiche la page Paramètres de protection de Microsoft contre les menaces lorsque vous sélectionnez **incidents**, **Centre de maintenance** **ou sélection** dans le volet de navigation. Ces éléments de navigation ne s’affichent pas si vous n’êtes pas éligible à l’utilisation de la protection contre les menaces Microsoft.

![Image de la page des paramètres de protection contre les menaces Microsoft affichée si Microsoft Threat Protection n’a pas été activé sur les ](../../media/mtp-enable/mtp-settings.png)
 *paramètres de protection contre les menaces Microsoft dans le centre de sécurité Microsoft 365*

## <a name="starting-the-service"></a>Démarrage du service
Pour activer Microsoft Threat Protection, sélectionnez simplement **activer la protection contre Microsoft Threat** et appliquer la modification. Vous pouvez également accéder à cette option en sélectionnant **paramètres** ([Security.Microsoft.com/Settings](https://security.microsoft.com/settings)) dans le volet de navigation, puis en sélectionnant **protection Microsoft contre les menaces**.

>[!NOTE]
>Si vous ne voyez pas les **paramètres** dans le volet de navigation ou que vous n’avez pas accès à la page, vérifiez vos autorisations et licences.

### <a name="data-center-location"></a>Emplacement du centre de données
Microsoft Threat Protection stocke et traite les données au [même emplacement que celui utilisé par Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy). Si vous ne disposez pas de Microsoft Defender ATP, un nouvel emplacement de centre de données est automatiquement sélectionné en fonction de l’emplacement des services de sécurité Microsoft 365 actifs. L’emplacement du centre de données sélectionné est affiché à l’écran. 

Sélectionnez **besoin d’aide ?** dans le centre de sécurité Microsoft 365 pour contacter le support Microsoft sur la mise en service de la protection contre les menaces Microsoft dans un autre emplacement de centre de données. 

>[!NOTE]
>Microsoft Defender s’approvisionne automatiquement dans les centres de données de l’Union européenne (UE) lors de l’activation via le centre de sécurité Azure. La protection Microsoft contre les menaces est automatiquement mise en service dans le centre de données de l’UE pour les clients qui ont configuré Microsoft Defender ATP de cette manière. 

### <a name="confirm-that-the-service-is-on"></a>Vérifiez que le service est activé
Une fois le service configuré, il ajoute :

- [Gestion des incidents](incidents-overview.md)
- Centre de notifications pour la gestion des [examen et réponse automatisés](mtp-autoir.md)
- Fonctionnalités de [chasse avancées](advanced-hunting-overview.md)

![Image du volet de navigation du centre de sécurité Microsoft 365 avec les fonctionnalités de protection de Microsoft Threat ](../../media/mtp-enable/mtp-on.png)
 *Centre de sécurité Microsoft 365 avec gestion des incidents et autres fonctionnalités de protection contre les menaces Microsoft*

### <a name="getting-azure-atp-data"></a>Obtention de données Azure ATP
Pour partager des données Azure ATP avec la Protection Microsoft contre les menaces, assurez-vous que Microsoft Cloud App Security et l’intégration Azure ATP sont activées. [Découvrez cette intégration](https://docs.microsoft.com/cloud-app-security/aatp-integration)


## <a name="turn-off-microsoft-threat-protection"></a>Désactiver la Protection Microsoft contre les menaces
Pour cesser d’utiliser la Protection Microsoft contre les menaces, accédez à **Paramètres** > **Protection Microsoft contre les menaces** > **Accepter / Refuser** dans le Centre de sécurité Microsoft 365. Désélectionnez **activer la protection de Microsoft contre les menaces** et appliquer les modifications.

Les fonctionnalités correspondantes seront supprimées du centre de sécurité Microsoft 365.

## <a name="get-assistance"></a>Obtenir de l'aide

Pour obtenir des réponses aux questions les plus fréquemment posées sur l’activation de Microsoft Threat Protection, [Lisez le Forum aux](mtp-enable-faq.md)questions.

Le personnel du support Microsoft peut vous aider à mettre en service ou à mettre hors service le service et les ressources associées sur votre client. Pour obtenir de l’aide, sélectionnez **besoin d’aide ?** dans le centre de sécurité Microsoft 365. Lorsque vous contactez le support technique, mentionnez Microsoft Threat Protection.

## <a name="related-topics"></a>Voir aussi

- [Forum aux questions](mtp-enable-faq.md)
- [Conditions requises et autres conditions préalables relatives aux licences](prerequisites.md)
- [Déployer les services pris en charge](deploy-supported-services.md)
- [Vue d’ensemble de la Protection Microsoft contre les menaces](microsoft-threat-protection.md)
- [Vue d’ensemble de Microsoft Defender - Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- [Vue d’ensemble d’Office 365 – Protection avancée contre les menaces](../office-365-security/office-365-atp.md)
- [Vue d’ensemble de Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)
- [Vue d’ensemble d’Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)
- [Stockage de données Microsoft Defender - Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy)