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
ms.openlocfilehash: 8f966060ebc9a30166647b397b93f2b45356df74
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42083721"
---
# <a name="turn-on-microsoft-threat-protection"></a>Activer la Protection Microsoft contre les menaces

**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

La Protection Microsoft contre les menaces unifie votre processus de réponse aux incidents en intégrant les principales fonctionnalités de Microsoft Defender - Protection avancée contre les menaces (ATP), Office 365 - Protection avancée contre les menaces, Microsoft Cloud App Security et Azure ATP. Cette expérience unifiée ajoute des fonctionnalités puissantes auxquelles vous pouvez accéder dans le Centre de sécurité Microsoft 365.

## <a name="check-license-eligibility-and-required-permissions"></a>Vérifier l’éligibilité de la licence et les autorisations requises
Les clients disposant de Microsoft 365 E5, de Microsoft 365 E5 sécurité ou d’une combinaison équivalente de licences peuvent utiliser Microsoft Threat Protection. Pour plus d'informations, [lire les conditions relatives aux licences](prerequisites.md#licensing-requirements).

Vous devez être **administrateur général** ou administrateur de **sécurité** dans [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles) pour activer Microsoft Threat Protection.

## <a name="start-using-the-service"></a>Commencez à utiliser le service
Microsoft Threat Protection agrège les données des différents services intégrés. Il traitera et stockera les données de manière centralisée afin d’identifier les nouvelles idées et de créer des flux de travail de réponse centralisée.

Avant d’activer le service, le centre de sécurité Microsoft 365 ([Security.Microsoft.com](https://security.microsoft.com)) n’affiche pas les **incidents** ni les options du **Centre de notifications** dans le volet de navigation.

![Image du volet de navigation du centre de sécurité Microsoft 365 sans les](../../media/mtp-off.png)
fonctionnalités Microsoft Threat Protection*Centre de sécurité Microsoft 365 avec la protection Microsoft contre les menaces désactivée*

Pour activer Microsoft Threat Protection, sélectionnez **paramètres** dans le volet de navigation. Dans la **[page Paramètres](https://security.microsoft.com/settings)**, consultez la section**opt-in/opt-out**de la **protection de Microsoft contre** > les menaces.

>[!NOTE]
>Si vous ne voyez pas les **paramètres** dans le volet de navigation ou que vous n’avez pas accès à la page, vérifiez vos autorisations et licences.

### <a name="select-data-center-location"></a>Sélectionner l’emplacement du centre de données
Si Microsoft Defender - Protection avancée contre les menaces a été configuré pour votre organisation, les données sont stockées et traitées dans le même emplacement de centre de données que celui que vous avez sélectionné pour [vos données Microsoft Defender – Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy). Si vous n’avez pas Microsoft Defender ATP, vous serez invité à choisir un nouvel emplacement de centre de données spécifiquement pour la Protection Microsoft contre les menaces. 

Vous devez fournir le consentement avant le partage des données entre les services et l’agrégation.

### <a name="confirm-that-the-service-is-on"></a>Vérifiez que le service est activé
Une fois le service configuré, il ajoute :

- [Gestion des incidents](incidents-overview.md)
- Centre de notifications pour la gestion des [examen et réponse automatisés](mtp-autoir.md)
- La fonctionnalités de [repérage avancé](advanced-hunting-overview.md) à la page **Repérage**

![Image du volet de navigation du centre de sécurité Microsoft 365 avec les](../../media/mtp-on.png)
fonctionnalités de protection de Microsoft Threat*Centre de sécurité Microsoft 365 avec gestion des incidents et autres fonctionnalités de protection contre les menaces Microsoft*

### <a name="getting-azure-atp-data"></a>Obtention de données Azure ATP
Pour partager des données Azure ATP avec la Protection Microsoft contre les menaces, assurez-vous que Microsoft Cloud App Security et l’intégration Azure ATP sont activées. [Découvrez cette intégration](https://docs.microsoft.com/cloud-app-security/aatp-integration)


## <a name="turn-off-microsoft-threat-protection"></a>Désactiver la Protection Microsoft contre les menaces
Pour cesser d’utiliser la Protection Microsoft contre les menaces, accédez à **Paramètres** > **Protection Microsoft contre les menaces** > **Accepter / Refuser** dans le Centre de sécurité Microsoft 365. Désélectionnez **Activer la Protection Microsoft contre les menaces** et enregistrez les modifications.

Les données seront définitivement supprimées et les fonctionnalités correspondantes seront supprimées du centre de sécurité Microsoft 365.

## <a name="get-assistance"></a>Obtenir de l'aide

Le personnel du support Microsoft peut vous aider à mettre en service ou à mettre hors service le service et les ressources associées sur votre client. Pour obtenir de l’aide, sélectionnez **besoin d’aide ?** dans le centre de sécurité Microsoft 365. Lorsque vous contactez le support technique, mentionnez Microsoft Threat Protection.

## <a name="related-topics"></a>Sujets associés

- [Vue d’ensemble de la Protection Microsoft contre les menaces](microsoft-threat-protection.md)
- [Conditions requises et autres conditions préalables relatives aux licences](prerequisites.md)
- [Vue d’ensemble de Microsoft Defender - Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- [Vue d’ensemble d’Office 365 – Protection avancée contre les menaces](../office-365-security/office-365-atp.md)
- [Vue d’ensemble de Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)
- [Vue d’ensemble d’Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)
- [Stockage de données Microsoft Defender - Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy)
