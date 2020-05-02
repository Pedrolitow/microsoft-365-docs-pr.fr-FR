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
ms.openlocfilehash: f1c616a3d752324b8db5fdd5069904989a25eade
ms.sourcegitcommit: b57d597edbff5ab6cff8c2b04d27c15b0024776f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "43997513"
---
# <a name="turn-on-microsoft-threat-protection"></a>Activer la Protection Microsoft contre les menaces

**S’applique à :**
- Protection Microsoft contre les menaces

La Protection Microsoft contre les menaces unifie votre processus de réponse aux incidents en intégrant les principales fonctionnalités de Microsoft Defender - Protection avancée contre les menaces (ATP), Office 365 - Protection avancée contre les menaces, Microsoft Cloud App Security et Azure ATP. Cette expérience unifiée ajoute des fonctionnalités puissantes auxquelles vous pouvez accéder dans le Centre de sécurité Microsoft 365.

Pour bénéficier de la meilleure protection et optimiser la protection Microsoft contre les menaces, nous vous recommandons de déployer tous les services pris en charge applicables sur votre réseau. Pour plus d’informations, consultez la rubrique [Deploying Supported services](deploy-supported-services.md).

## <a name="check-license-eligibility-and-required-permissions"></a>Vérifier l’éligibilité de la licence et les autorisations requises
Une licence Microsoft 365 E5, E5 Security, a5 ou a5 ou une combinaison valide de licences donne accès aux services pris en charge et vous permet d’utiliser la protection Microsoft contre les menaces dans le centre de sécurité Microsoft 365.

Pour obtenir des informations détaillées sur les licences, [Lisez les conditions relatives aux licences](prerequisites.md#licensing-requirements).

### <a name="check-your-role"></a>Vérifier votre rôle
Vous devez être **administrateur général** ou administrateur de **sécurité** dans Azure Active Directory pour activer Microsoft Threat Protection. [Afficher vos rôles dans Azure AD](https://docs.microsoft.com//azure/active-directory/users-groups-roles/directory-manage-roles-portal)

## <a name="start-using-the-service"></a>Commencez à utiliser le service
Microsoft Threat Protection agrège les données des différents services intégrés. Il traitera et stockera les données de manière centralisée afin d’identifier les nouvelles idées et de créer des flux de travail de réponse centralisée.

Avant d’activer le service, le centre de sécurité Microsoft 365 ([Security.Microsoft.com](https://security.microsoft.com)) affiche la **page d’accueil** de la protection de Microsoft contre les menaces lorsque vous sélectionnez **incidents**, **Centre de maintenance**ou sélection dans le volet de navigation. Ces options de navigation ne s’affichent pas si vous n’êtes pas éligible à l’utilisation de la protection contre les menaces Microsoft.

![Image de la page d’accueil de la protection de Microsoft contre les menaces affichée si Microsoft Threat](../../media/mtp-welcome.png)
protection n’a pas été activé sur la*page d’accueil de Microsoft Threat Protection dans le centre de sécurité Microsoft 365*

Pour activer Microsoft Threat Protection, terminez simplement le processus à partir de la page d’accueil. Vous pouvez également activer Microsoft Threat Protection en accédant aux **paramètres** ([Security.Microsoft.com/Settings](https://security.microsoft.com/settings)) dans le volet de navigation et en sélectionnant **Microsoft Threat Protection**. Cliquez sur **Enregistrer**.

>[!NOTE]
>Si vous ne voyez pas les **paramètres** dans le volet de navigation ou que vous n’avez pas accès à la page, vérifiez vos autorisations et licences.

### <a name="select-data-center-location"></a>Sélectionner l’emplacement du centre de données
Si Microsoft Defender - Protection avancée contre les menaces a été configuré pour votre organisation, les données sont stockées et traitées dans le même emplacement de centre de données que celui que vous avez sélectionné pour [vos données Microsoft Defender – Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy). Si vous n’avez pas Microsoft Defender ATP, vous serez invité à choisir un nouvel emplacement de centre de données spécifiquement pour la Protection Microsoft contre les menaces. 

Vous devez fournir le consentement avant le partage des données entre les services et l’agrégation.

### <a name="confirm-that-the-service-is-on"></a>Vérifiez que le service est activé
Une fois le service configuré, il ajoute :

- [Gestion des incidents](incidents-overview.md)
- Centre de notifications pour la gestion des [examen et réponse automatisés](mtp-autoir.md)
- Fonctionnalités de [chasse avancées](advanced-hunting-overview.md)

![Image du volet de navigation du centre de sécurité Microsoft 365 avec les](../../media/mtp-on.png)
fonctionnalités de protection de Microsoft Threat*Centre de sécurité Microsoft 365 avec gestion des incidents et autres fonctionnalités de protection contre les menaces Microsoft*

### <a name="getting-azure-atp-data"></a>Obtention de données Azure ATP
Pour partager des données Azure ATP avec la Protection Microsoft contre les menaces, assurez-vous que Microsoft Cloud App Security et l’intégration Azure ATP sont activées. [Découvrez cette intégration](https://docs.microsoft.com/cloud-app-security/aatp-integration)


## <a name="turn-off-microsoft-threat-protection"></a>Désactiver la Protection Microsoft contre les menaces
Pour cesser d’utiliser la Protection Microsoft contre les menaces, accédez à **Paramètres** > **Protection Microsoft contre les menaces** > **Accepter / Refuser** dans le Centre de sécurité Microsoft 365. Désélectionnez **Activer la Protection Microsoft contre les menaces** et enregistrez les modifications.

Les fonctionnalités correspondantes seront supprimées du centre de sécurité Microsoft 365.

## <a name="get-assistance"></a>Obtenir de l'aide

Le personnel du support Microsoft peut vous aider à mettre en service ou à mettre hors service le service et les ressources associées sur votre client. Pour obtenir de l’aide, sélectionnez **besoin d’aide ?** dans le centre de sécurité Microsoft 365. Lorsque vous contactez le support technique, mentionnez Microsoft Threat Protection.

## <a name="related-topics"></a>Sujets associés

- [Vue d’ensemble de la Protection Microsoft contre les menaces](microsoft-threat-protection.md)
- [Conditions requises et autres conditions préalables relatives aux licences](prerequisites.md)
- [Déployer les services pris en charge](deploy-supported-services.md)
- [Vue d’ensemble de Microsoft Defender - Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- [Vue d’ensemble d’Office 365 – Protection avancée contre les menaces](../office-365-security/office-365-atp.md)
- [Vue d’ensemble de Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)
- [Vue d’ensemble d’Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)
- [Stockage de données Microsoft Defender - Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy)
