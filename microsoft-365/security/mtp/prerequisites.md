---
title: Conditions préalables pour la Protection Microsoft contre les menaces
description: En savoir plus sur les exigences en matière de licences, de matériel et de logiciels, ainsi que sur les autres paramètres de configuration de la Protection Microsoft contre les menaces.
keywords: conditions requises, configuration matérielle, logicielle, navigateur, MTP, M365, licence, E5, a5, EMS, acheter
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 50ca606a6bef9cec528b6b0ef78142f050e37c51
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48195490"
---
# <a name="microsoft-threat-protection-prerequisites"></a>Conditions préalables pour la Protection Microsoft contre les menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

Découvrez les licences et autres conditions requises pour la mise en service et l’utilisation de la [protection contre les menaces Microsoft](microsoft-threat-protection.md).

## <a name="licensing-requirements"></a>Critères de licence
L’une de ces licences vous donne accès aux fonctionnalités de protection contre les menaces Microsoft dans le centre de sécurité Microsoft 365 sans frais supplémentaires :

- Microsoft 365 E5 ou a5
- Microsoft 365 E5 sécurité ou a5 sécurité
- Windows 10 entreprise E5 ou a5
- Enterprise Mobility + Security (EMS) E5 ou a5 
- Office 365 E5 ou a5
- Microsoft Defender – Protection avancée contre les menaces
- Azure Advanced Threat Protection 
- Microsoft Cloud App Security
- Office 365 – Protection avancée contre les menaces (plan 2)

> [!NOTE]
> Les licences d’évaluation pour Office 365 ne fournissent actuellement pas d’accès à Microsoft Threat Protection.

Pour plus d’informations, [consultez les plans de services d’entreprise Microsoft 365](https://www.microsoft.com/licensing/product-licensing/microsoft-365-enterprise).

> Vous n’avez pas encore de licence ? [Essayez ou achetez un abonnement Microsoft 365](https://docs.microsoft.com/microsoft-365/commerce/try-or-buy-microsoft-365?view=o365-worldwide)

### <a name="check-your-existing--licenses"></a>Vérifiez vos licences existantes
Accédez au centre d’administration Microsoft 365 ([admin.Microsoft.com](https://admin.microsoft.com/)) pour afficher vos licences existantes. Dans le Centre d'administration, accédez à **Facturation** > **Licences**.

>[!NOTE]
> Vous devez disposer du rôle d' **administrateur de facturation** ou de **lecteur global** [dans Azure ad](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles) pour être en mesure d’afficher les informations de licence. Si vous rencontrez des problèmes d’accès, veuillez contacter un administrateur général.

## <a name="required-permissions"></a>Autorisations requises
Vous devez être **administrateur général** ou administrateur de **sécurité** dans Azure Active Directory pour activer Microsoft Threat Protection. Pour obtenir la liste des rôles requis pour utiliser Microsoft Threat Protection et des informations sur la façon dont l’accès aux données est réglementé, consultez la rubrique [Managing Access to Microsoft Threat Protection](mtp-permissions.md).

## <a name="browser-requirements"></a>Configuration requise pour le navigateur
Accédez à la protection contre les menaces Microsoft dans le centre de sécurité Microsoft 365 à l’aide de Microsoft Edge, d’Internet Explorer 11 ou de n’importe quel navigateur Web compatible HTML 5.

## <a name="availability-to-us-gcc-gcc-high-and-other-us-government-institutions"></a>Disponibilité aux États-Unis GCC, GCC High et d’autres établissements gouvernementaux américains
Actuellement, la protection de Microsoft contre les menaces n’est *pas* disponible pour :
- Cloud communautaire pour le gouvernement américain (GCC)
- Niveau supérieur du Cloud communautaire pour le gouvernement américain (GCC High)
- Ministère américain de la défense
- Tous les établissements gouvernementaux américains avec des licences commerciales

## <a name="related-topics"></a>Sujets associés
- [Vue d’ensemble de la Protection Microsoft contre les menaces](microsoft-threat-protection.md)
- [Activer la Protection Microsoft contre les menaces](mtp-enable.md)
- [Gérer l’accès et les autorisations](mtp-permissions.md)
