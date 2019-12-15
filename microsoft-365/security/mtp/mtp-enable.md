---
title: Activer la Protection Microsoft contre les menaces dans le Centre de sécurité Microsoft 365
description: Découvrez comment activer la Protection Microsoft contre les menaces et commencer à intégrer votre incident de sécurité et votre réponse.
keywords: prise en main, MTP, Protection Microsoft contre les menaces, M365, sécurité, emplacement des données
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
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
ms.openlocfilehash: a70754be6e1bd37d292a44e3ada82b3ae13ee6b7
ms.sourcegitcommit: 0c9c28a87201c7470716216d99175356fb3d1a47
ms.translationtype: MT + HT Review
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2019
ms.locfileid: "39911057"
---
# <a name="turn-on-microsoft-threat-protection"></a>Activer la Protection Microsoft contre les menaces

**S’applique à :**
- Protection Microsoft contre les menaces

[!include[Prerelease information](prerelease.md)]

La Protection Microsoft contre les menaces unifie votre processus de réponse aux incidents en intégrant les principales fonctionnalités de Microsoft Defender - Protection avancée contre les menaces (ATP), Office 365 - Protection avancée contre les menaces, Microsoft Cloud App Security et Azure ATP. Cette expérience unifiée ajoute des fonctionnalités puissantes auxquelles vous pouvez accéder dans le Centre de sécurité Microsoft 365.

## <a name="check-your-eligibility"></a>Vérifiez votre éligibilité
Les clients disposant d’une licence Microsoft 365 E5 ou équivalente peuvent utiliser la Protection Microsoft contre les menaces. Pour plus d'informations, [lire les conditions relatives aux licences](prerequisites.md#licensing-requirements).

## <a name="start-using-the-service"></a>Commencez à utiliser le service
L’activation du service de Protection Microsoft contre les menaces agrège les données des différents services intégrés. Les données sont traitées et stockées de façon centralisée pour identifier les nouvelles perspectives et rendre possible les flux de travail de réponse centralisée.

Avant de désactiver le service, le Centre de sécurité Microsoft 365 ([security.microsoft.com](https://security.microsoft.com)) n’affiche pas les options **incidents** et **Centre de notifications** dans le menu.

![Image du menu Centre de sécurité Microsoft 365 sans les fonctionnalités de Protection Microsoft contre les menaces](../images/mtp-off.png)
*Centre de sécurité Microsoft 365 avec la protection Microsoft contre les menaces désactivée*

Pour activer le service de Protection Microsoft contre les menaces, accédez à **Paramètres** > **Protection Microsoft contre les menaces** > **Accepter / Refuser** dans le Centre de sécurité Microsoft 365. Pour effectuer cette tâche, vous devez être un administrateur général ou un administrateur de sécurité dans [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles).

Si Microsoft Defender - Protection avancée contre les menaces a été configuré pour votre organisation, les données sont stockées et traitées dans le même emplacement de centre de données que celui que vous avez sélectionné pour [vos données Microsoft Defender – Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy). Si vous n’avez pas Microsoft Defender ATP, vous serez invité à choisir un nouvel emplacement de centre de données spécifiquement pour la Protection Microsoft contre les menaces. Vous devez fournir un consentement avant que les données soient partagées entre les services et agrégées.

### <a name="confirm-that-the-service-is-on"></a>Vérifiez que le service est activé
Une fois le service configuré, il ajoute :

- [Gestion des incidents](incidents-overview.md)
- Centre de notifications pour la gestion des [examen et réponse automatisés](mtp-autoir.md)
- La fonctionnalités de [repérage avancé](advanced-hunting-overview.md) à la page **Repérage**

![Image du menu Centre de sécurité Microsoft 365 avec les fonctionnalités de Protection Microsoft contre les menaces](../images/mtp-on.png)
*Centre de sécurité Microsoft 365 avec la gestion des incidents et d’autres fonctionnalités de Protection Microsoft contre les menaces*

### <a name="getting-azure-atp-data"></a>Obtention de données Azure ATP
Pour partager des données Azure ATP avec la Protection Microsoft contre les menaces, assurez-vous que Microsoft Cloud App Security et l’intégration Azure ATP sont activées. [Découvrez cette intégration](https://docs.microsoft.com/cloud-app-security/aatp-integration)


## <a name="turn-off-microsoft-threat-protection"></a>Désactiver la Protection Microsoft contre les menaces
Pour cesser d’utiliser la Protection Microsoft contre les menaces, accédez à **Paramètres** > **Protection Microsoft contre les menaces** > **Accepter / Refuser** dans le Centre de sécurité Microsoft 365. Désélectionnez **Activer la Protection Microsoft contre les menaces** et enregistrez les modifications.

Les données seront supprimées de façon définitive et les fonctionnalités correspondantes seront supprimées du Centre de sécurité Microsoft 365.

## <a name="get-assistance"></a>Obtenir de l'aide

Le personnel Microsoft peut vous aider à fournir ou à déprovisionner le service et les ressources associées sur votre locataire. Si vous souhaitez obtenir de l’aide, [veuillez contacter le support premier](https://go.microsoft.com/fwlink/?LinkID=733758).

## <a name="related-topics"></a>Sujets associés

- [Vue d’ensemble de la Protection Microsoft contre les menaces](microsoft-threat-protection.md)
- [Conditions requises et autres conditions préalables relatives aux licences](prerequisites.md)
- [Vue d’ensemble de Microsoft Defender - Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- [Vue d’ensemble d’Office 365 – Protection avancée contre les menaces](../office-365-security/office-365-atp.md)
- [Vue d’ensemble de Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)
- [Vue d’ensemble d’Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)
- [Stockage de données Microsoft Defender - Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy)
