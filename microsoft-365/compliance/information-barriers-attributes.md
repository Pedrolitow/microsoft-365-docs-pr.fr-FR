---
title: Attributs du cloisonnement de l’information
description: Cet article est une référence pour les attributs de compte d’utilisateur Azure Active Directory que vous pouvez utiliser pour définir des segments d’obstacles à l’information.
keywords: Microsoft 365, Microsoft Purview, conformité, obstacles à l’information
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e09331fb819d2b00764cd6dacd1687ade8ee116c
ms.sourcegitcommit: 99494a5530ad64802f341573ad42796134190296
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2022
ms.locfileid: "65396264"
---
# <a name="information-barriers-attributes"></a>Attributs du cloisonnement de l’information

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Certains attributs dans Azure Active Directory peuvent être utilisés pour segmenter les utilisateurs dans les barrières à l’information (IB). Une fois les segments définis, ces segments peuvent être utilisés comme filtres pour les stratégies IB. Par exemple, vous pouvez utiliser **Department** pour définir des segments d’utilisateurs par service au sein de votre organisation (en supposant qu’aucun employé ne travaille simultanément pour deux services).

Cet article explique comment utiliser des attributs avec des barrières à l’information et fournit une liste d’attributs qui peuvent être utilisés. Pour en savoir plus sur les obstacles à l’information, consultez les ressources suivantes :

- [Obstacles aux informations](information-barriers.md)
- [Définir des stratégies pour les obstacles à l’information dans Microsoft Teams](information-barriers-policies.md)
- [Modifier (ou supprimer) des stratégies IB](information-barriers-edit-segments-policies.md)

## <a name="how-to-use-attributes-in-ib-policies"></a>Comment utiliser des attributs dans les stratégies IB

Les attributs répertoriés dans cet article peuvent être utilisés pour définir ou modifier des segments d’utilisateurs. Vos segments définis servent de paramètres (appelés valeurs *UserGroupFilter* ) dans les [stratégies IB](information-barriers-policies.md).

1. Déterminez l’attribut que vous souhaitez utiliser pour définir des segments. (Consultez la section [Référence](#reference) de cet article.)

2. Assurez-vous que les comptes d’utilisateurs ont des valeurs remplies pour les attributs que vous avez sélectionnés à l’étape 1. Affichez les détails du compte d’utilisateur et, si nécessaire, modifiez les comptes d’utilisateur pour inclure des valeurs d’attribut. 

    - Pour modifier plusieurs comptes (ou utiliser PowerShell pour modifier un seul compte), consultez [Configurer les propriétés du compte d’utilisateur avec Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

    - Pour modifier un compte unique, consultez [Ajouter ou mettre à jour les informations de profil d’un utilisateur à l’aide de Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

3. [Définissez des segments à l’aide de PowerShell](information-barriers-policies.md#define-segments-using-powershell), comme dans les exemples suivants :

    |**Exemple**|**Cmdlet**|
    |:----------|:---------|
    | Définir un segment appelé Segment1 à l’aide de l’attribut Department | `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "Department -eq 'Department1'"` |
    | Définir un segment appelé SegmentA à l’aide de l’attribut MemberOf (supposons que cet attribut contient des noms de groupe, tels que « BlueGroup ») | `New-OrganizationSegment -Name "SegmentA" -UserGroupFilter "MemberOf -eq 'BlueGroup'"` |
    | Définir un segment appelé DayTraders à l’aide d’ExtensionAttribute1 (supposons que cet attribut contient des titres de travaux, tels que « DayTrader ») | `New-OrganizationSegment -Name "DayTraders" -UserGroupFilter "ExtensionAttribute1 -eq 'DayTrader'"` |

    > [!TIP]
    > Lorsque vous définissez des segments, utilisez le même attribut pour tous vos segments. Par exemple, si vous définissez certains segments à l’aide *de Department*, définissez tous les segments à l’aide de *Department*. Ne définissez pas certains segments à l’aide *de Department* et d’autres à l’aide *de MemberOf*. Assurez-vous que vos segments ne se chevauchent pas ; chaque utilisateur doit être affecté à exactement un segment.

## <a name="reference"></a>Référence

Le tableau suivant répertorie les attributs que vous pouvez utiliser avec les barrières à l’information.

|**Azure Active Directory nom<br/> de propriété (nom d’affichage LDAP)**|**nom de la propriété Exchange**|
|:---------------------------------------------------------------|:-------------------------|
| Co | Co |
| Company | Company |
| Service | Service |
| ExtensionAttribute1 | CustomAttribute1 |
| ExtensionAttribute2 | CustomAttribute2 |
| ExtensionAttribute3 | CustomAttribute3 |
| ExtensionAttribute4 | CustomAttribute4 |
| ExtensionAttribute5 | CustomAttribute5 |
| ExtensionAttribute6 | CustomAttribute6 |
| ExtensionAttribute7 | CustomAttribute7 |
| ExtensionAttribute8 | CustomAttribute8 |
| ExtensionAttribute9 | CustomAttribute9 |
| ExtensionAttribute10 | CustomAttribute10 |
| ExtensionAttribute11 | CustomAttribute11 |
| ExtensionAttribute12 | CustomAttribute12 |
| ExtensionAttribute13 | CustomAttribute13 |
| ExtensionAttribute14 | CustomAttribute14 |
| ExtensionAttribute15 | CustomAttribute15 |
| MSExchExtensionCustomAttribute1 | ExtensionCustomAttribute1 |
| MSExchExtensionCustomAttribute2 | ExtensionCustomAttribute2 |
| MSExchExtensionCustomAttribute3 | ExtensionCustomAttribute3 |
| MSExchExtensionCustomAttribute4 | ExtensionCustomAttribute4 |
| MSExchExtensionCustomAttribute5 | ExtensionCustomAttribute5 |
| MailNickname | Alias |
| PhysicalDeliveryOfficeName | Bureau |
| PostalCode | PostalCode |
| ProxyAddresses | EmailAddresses |
| StreetAddress | StreetAddress |
| TargetAddress | ExternalEmailAddress |
| UsageLocation | UsageLocation |
| UserPrincipalName | UserPrincipalName |
| Courrier | WindowsEmailAddress |
| Description | Description |
| MemberOf | MemberOfGroup |

## <a name="resources"></a>Ressources

- [Définir des stratégies pour les obstacles à l’information dans Microsoft Teams](information-barriers-policies.md)
- [Résolution des problèmes de cloisonnement de l’information](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)
- [Obstacles aux informations](information-barriers.md)
