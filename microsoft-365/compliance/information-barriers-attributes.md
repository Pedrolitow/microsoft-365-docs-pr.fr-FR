---
title: Attributs du cloisonnement de l’information
description: Cet article est une référence pour les Azure Active Directory de compte d’utilisateur que vous pouvez utiliser pour définir des segments d’obstacles à l’information.
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
ms.openlocfilehash: 33143e85bf17a707ade6dd0d6d0c66886fd85373
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60179150"
---
# <a name="information-barriers-attributes"></a>Attributs du cloisonnement de l’information

Certains attributs dans Azure Active Directory peuvent être utilisés pour segmenter les utilisateurs. Une fois les segments définis, ces segments peuvent être utilisés comme filtres pour les stratégies d’obstacle à l’information. Par exemple, vous pouvez utiliser **Service** pour définir des segments d’utilisateurs par service au sein de votre organisation (en supposant qu’aucun employé ne travaille pour deux services en même temps).

Cet article explique comment utiliser des attributs avec des obstacles à l’information et fournit une liste d’attributs qui peuvent être utilisés. Pour en savoir plus sur les obstacles aux informations, consultez les ressources suivantes :

- [Obstacles aux informations](information-barriers.md)
- [Définir des stratégies pour les obstacles à l’information Microsoft Teams](information-barriers-policies.md)
- [Modifier (ou supprimer) des stratégies de cloisonnement de l’information](information-barriers-edit-segments-policies.md)

## <a name="how-to-use-attributes-in-information-barrier-policies"></a>Comment utiliser des attributs dans les stratégies de obstacle à l’information

Les attributs répertoriés dans cet article peuvent être utilisés pour définir ou modifier des segments d’utilisateurs. Vos segments définis servent de paramètres (appelés valeurs *UserGroupFilter)* dans les stratégies [d’obstacle aux informations.](information-barriers-policies.md)

1. Déterminez l’attribut que vous souhaitez utiliser pour définir des segments. (Voir la section [Référence](#reference) de cet article.)

2. Assurez-vous que les comptes d’utilisateurs ont des valeurs remplies pour les attributs que vous avez sélectionnés à l’étape 1. Affichez les détails du compte d’utilisateur et, si nécessaire, modifiez les comptes d’utilisateur pour inclure des valeurs d’attribut. 

    - Pour modifier plusieurs comptes (ou utiliser PowerShell pour modifier un seul compte), voir Configurer les propriétés du compte d’utilisateur [Office 365 PowerShell.](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)

    - Pour modifier un compte unique, voir Ajouter ou mettre à jour les informations de profil d’un utilisateur à [l’aide Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

3. [Définissez des segments à l’aide de PowerShell,](information-barriers-policies.md#define-segments-using-powershell)comme dans les exemples suivants :

    |**Exemple**|**Cmdlet**|
    |:----------|:---------|
    | Définir un segment appelé Segment1 à l’aide de l’attribut Department | `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "Department -eq 'Department1'"` |
    | Définissez un segment appelé SegmentA à l’aide de l’attribut MemberOf (supposons que cet attribut contient des noms de groupe, tels que « BlueGroup »). | `New-OrganizationSegment -Name "SegmentA" -UserGroupFilter "MemberOf -eq 'BlueGroup'"` |
    | Définissez un segment appelé DayTraders à l’aide d’ExtensionAttribute1 (supposons que cet attribut contient des titres de poste, tels que « DayTrader ») | `New-OrganizationSegment -Name "DayTraders" -UserGroupFilter "ExtensionAttribute1 -eq 'DayTrader'"` |

    > [!TIP]
    > Lorsque vous définissez des segments, utilisez le même attribut pour tous vos segments. Par exemple, si vous définissez certains segments à l’aide de *Department*, définissez tous les segments à l’aide de *Department*. Ne définissez pas certains segments à l’aide de *Department* et d’autres à l’aide *de MemberOf*. Assurez-vous que vos segments ne se chevauchent pas ; chaque utilisateur doit être affecté à exactement un segment.

## <a name="reference"></a>Référence

Le tableau suivant répertorie les attributs que vous pouvez utiliser avec les obstacles aux informations.

|**Azure Active Directory de la propriété <br/> (nom complet LDAP)**|**Exchange de la propriété**|
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

- [Définir des stratégies pour les obstacles à l’information Microsoft Teams](information-barriers-policies.md)
- [Résolution des problèmes de cloisonnement de l’information](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)
- [Obstacles aux informations](information-barriers.md)