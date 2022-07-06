---
title: Gérer les stratégies d’obstacles à l’information
description: Découvrez comment modifier ou supprimer des stratégies pour les obstacles à l’information.
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
ms.openlocfilehash: a84b8e712de53b0abae81a05bbe1b2bef3237beb
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635302"
---
# <a name="manage-information-barriers-policies"></a>Gérer les stratégies d’obstacles à l’information

Une fois que vous avez [défini des stratégies d’obstacles à l’information,](information-barriers-policies.md) vous devrez peut-être apporter des modifications à ces stratégies ou à vos segments d’utilisateur, dans le cadre de la [résolution des problèmes](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) ou de la maintenance régulière.

## <a name="what-do-you-want-to-do"></a>Que souhaitez-vous faire ?

|**Action**|**Description**|
|:---------|:--------------|
| [Modifier les attributs d’un compte d’utilisateur](#edit-user-account-attributes) | Renseignez les attributs dans Azure Active Directory qui peuvent être utilisés pour définir des segments. <br> Modifiez les attributs de compte d’utilisateur lorsque les utilisateurs ne sont pas inclus dans les segments qu’ils doivent être, pour modifier les segments dans lesquels se trouvent les utilisateurs ou pour définir des segments à l’aide de différents attributs. |
| [Modifier un segment](#edit-a-segment) | Modifiez les segments lorsque vous voulez modifier la manière dont un segment est défini. <br> Par exemple, vous pouvez avoir défini des segments à l’origine à l’aide *de Department* et souhaiter maintenant utiliser un autre attribut, tel que *MemberOf*. |
| [Modifier une stratégie](#edit-a-policy) | Modifiez une stratégie d’obstacles à l’information lorsque vous souhaitez modifier le fonctionnement d’une stratégie.<br> Par exemple, au lieu de bloquer les communications entre deux segments, vous pouvez décider d’autoriser les communications à se produire uniquement entre certains segments. |
| [Définir une stratégie sur l’état inactif](#set-a-policy-to-inactive-status) |Définissez une stratégie sur l’état inactif lorsque vous souhaitez apporter des modifications à une stratégie ou si vous ne souhaitez pas qu’une stratégie soit en vigueur. |
| [Supprimer une stratégie](#remove-a-policy) | Supprimez une stratégie d’obstacles à l’information lorsque vous n’avez plus besoin d’une stratégie particulière en place. |
| [Supprimer un segment](#remove-a-segment) | Supprimez un segment d’obstacles à l’information lorsque vous n’avez plus besoin d’un segment particulier. |
| [Supprimer une stratégie et un segment](#remove-a-policy-and-segment) | Supprimez une stratégie d’obstacles à l’information et un segment en même temps. |
| [Arrêter une application de stratégie](#stop-a-policy-application) | Effectuez cette action lorsque vous souhaitez arrêter le processus d’application de stratégies d’obstacle à l’information. <br> L’arrêt d’une application de stratégie n’est pas instantané et n’annule pas les stratégies déjà appliquées aux utilisateurs. |
| [Définir des stratégies pour les obstacles à l’information](information-barriers-policies.md) | Définissez une stratégie d’obstacles à l’information lorsque vous n’avez pas encore de telles stratégies en place et que vous devez restreindre ou limiter les communications entre des groupes d’utilisateurs spécifiques. |
| [Résolution des problèmes de cloisonnement de l’information](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) | Reportez-vous à cet article lorsque vous rencontrez des problèmes inattendus liés aux obstacles à l’information. |

>[!IMPORTANT]
>Pour effectuer les tâches décrites dans cet article, vous devez disposer d’un rôle approprié, tel que l’un des éléments suivants :<br>- administrateur général Microsoft 365 Entreprise<br>- Administrateur général<br>- Administrateur de conformité<br>- Gestion de la conformité ib (il s’agit d’un nouveau rôle!)<br><br>Pour en savoir plus sur les prérequis pour les obstacles à l’information, consultez [Prérequis (pour les stratégies d’obstacle à l’information).](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met)<br><br> Veillez à [vous connecter à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="edit-user-account-attributes"></a>Modifier les attributs d’un compte d’utilisateur

Utilisez cette procédure pour modifier les attributs utilisés pour segmenter les utilisateurs. Par exemple, si vous utilisez un attribut Department et qu’un ou plusieurs comptes d’utilisateur n’ont actuellement aucune valeur répertoriée pour Department, vous devez modifier ces comptes d’utilisateur pour inclure les informations du service. Les attributs de compte d’utilisateur sont utilisés pour définir des segments afin que les stratégies d’obstacle aux informations puissent être affectées.

1. Pour afficher les détails d’un compte d’utilisateur spécifique, tels que les valeurs d’attribut et les segments affectés, utilisez l’applet de commande **Get-InformationBarrierRecipientStatus** avec des paramètres d’identité.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <br> Vous pouvez utiliser n’importe quelle valeur qui identifie de manière unique chaque utilisateur, telle que le nom, l’alias, le nom unique, le nom de domaine canonique, l’adresse e-mail ou le GUID. <br> (Vous pouvez également utiliser cette applet de commande pour un seul utilisateur : `Get-InformationBarrierRecipientStatus -Identity <value>`) |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <br> Dans cet exemple, nous faisons référence à deux comptes d’utilisateur dans Office 365 : *meganb* pour *Megan* et *alexw* pour *Alex*. |

2. Déterminez l’attribut que vous souhaitez modifier pour votre ou vos profils de compte d’utilisateur. Pour plus d’informations, consultez [Attributs pour les stratégies d’obstacles à l’information](information-barriers-attributes.md).

3. Modifiez un ou plusieurs comptes d’utilisateur pour inclure des valeurs pour l’attribut que vous avez sélectionné à l’étape précédente. Pour effectuer cette action, utilisez l’une des procédures suivantes :

    - Pour modifier un compte unique, consultez [Ajouter ou mettre à jour les informations de profil d’un utilisateur à l’aide d’Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

    - Pour modifier plusieurs comptes (ou utiliser PowerShell pour modifier un seul compte), consultez [Configurer les propriétés du compte d’utilisateur avec Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

## <a name="edit-a-segment"></a>Modifier un segment

Utilisez cette procédure pour modifier la définition d’un segment d’utilisateur. Par exemple, vous pouvez modifier le nom d’un segment ou le filtre utilisé pour déterminer qui est inclus dans le segment.

1. Pour afficher tous les segments existants, utilisez **l’applet de commande Get-OrganizationSegment** .

    Syntaxe: `Get-OrganizationSegment`

    Vous verrez une liste de segments et de détails pour chacun d’eux, tels que le type de segment, sa valeur UserGroupFilter, qui l’a créée ou modifiée pour la dernière fois, guid, etc.

    > [!TIP]
    > Imprimez ou enregistrez votre liste de segments pour référence ultérieurement. Par exemple, si vous souhaitez modifier un segment, vous devez connaître son nom ou identifier la valeur (utilisée avec le paramètre Identity).

2. Pour modifier un segment, utilisez l’applet de commande **Set-OrganizationSegment** avec le paramètre **Identity** et les détails pertinents.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` |`Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'HRDept'"` <br> Dans cet exemple, nous avons mis à jour le nom du service en *HRDept* pour le segment avec GUID *c96e0837-c232-4a8a-841e-ef45787d8fcd*. |

3. Une fois que vous avez terminé de modifier des segments pour votre organisation, vous pouvez [définir](information-barriers-policies.md#step-3-create-ib-policies) ou [modifier](#edit-a-policy) des stratégies d’obstacles à l’information.

## <a name="edit-a-policy"></a>Modifier une stratégie

1. Pour afficher la liste des stratégies actuelles relatives aux obstacles à l’information, utilisez l’applet de commande **Get-InformationBarrierPolicy** .

    Syntaxe: `Get-InformationBarrierPolicy`

    Dans la liste des résultats, identifiez la stratégie à modifier. Notez le GUID et le nom de la stratégie.

2. Utilisez l’applet **de commande Set-InformationBarrierPolicy** avec un paramètre **Identity** et spécifiez les modifications que vous souhaitez apporter.

    Exemple : Supposons qu’une stratégie a été définie pour empêcher le segment *Recherche* de communiquer avec les segments *Ventes* et *Marketing* . La stratégie a été définie à l’aide de cette applet de commande : `New-InformationBarrierPolicy -Name "Research-SalesMarketing" -AssignedSegment "Research" -SegmentsBlocked "Sales","Marketing"`

    Supposons que nous voulons le modifier afin que les membres du segment *Recherche* puissent uniquement communiquer avec les personnes du segment *RH* . Pour effectuer cette modification, nous utilisons cette applet de commande : `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -SegmentsAllowed "HR"`

    Dans cet exemple, nous avons remplacé *SegmentsBlocked par* *SegmentsAllowed* et spécifié le segment *RH* .

3. Une fois que vous avez terminé de modifier une stratégie, veillez à appliquer vos modifications. (Voir [Appliquer des stratégies d’obstacle à l’information](information-barriers-policies.md#step-4-apply-ib-policies).)

## <a name="set-a-policy-to-inactive-status"></a>Définir une stratégie sur l’état inactif

1. Pour afficher la liste des stratégies actuelles relatives aux obstacles à l’information, utilisez l’applet de commande **Get-InformationBarrierPolicy** .

    Syntaxe: `Get-InformationBarrierPolicy`

    Dans la liste des résultats, identifiez la stratégie que vous souhaitez modifier (ou supprimer). Notez le GUID et le nom de la stratégie.

2. Pour définir l’état de la stratégie sur Inactif, utilisez l’applet de commande **Set-InformationBarrierPolicy** avec un paramètre *Identity* et le paramètre *State* défini sur *Inactif*.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> Dans cet exemple, la stratégie d’obstacles à l’information qui a GUID *43c37853-ea10-4b90-a23d-ab8c9377247* est définie sur un état inactif. |

3. Pour appliquer vos modifications, utilisez l’applet de commande **Start-InformationBarrierPoliciesApplication** .

    Syntaxe: `Start-InformationBarrierPoliciesApplication`

    Les modifications sont appliquées utilisateur par utilisateur pour votre organisation. Si votre organisation est volumineuse, l’exécution de ce processus peut prendre 24 heures (ou plus). En règle générale, le traitement de 5 000 comptes d’utilisateurs prend environ une heure.

4. À ce stade, une ou plusieurs stratégies d’obstacles à l’information sont définies sur l’état inactif. À partir de là, vous pouvez effectuer l’une des actions suivantes :

    - Conservez-le tel quel (une stratégie définie sur l’état inactif n’a aucun effet sur les utilisateurs)
    - [Modifier une stratégie](#edit-a-policy) 
    - [Supprimer une stratégie](#remove-a-policy)

## <a name="remove-a-policy"></a>Supprimer une stratégie

1. Pour afficher la liste des stratégies actuelles relatives aux obstacles à l’information, utilisez l’applet de commande **Get-InformationBarrierPolicy** .

    Syntaxe: `Get-InformationBarrierPolicy`

    Dans la liste des résultats, identifiez la stratégie à supprimer. Notez le GUID et le nom de la stratégie. 

2. Vérifiez que la stratégie est définie sur l’état inactif. Pour définir l’état de la stratégie sur Inactif, utilisez l’applet de commande Set-InformationBarrierPolicy avec un paramètre Identity et le paramètre State défini sur Inactif.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive`  | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> Dans cet exemple, nous définissons une stratégie d’obstacles à l’information qui a le GUID *43c37853-ea10-4b90-a23d-ab8c9377247* sur un état inactif. |

3. Pour appliquer vos modifications à la stratégie, utilisez l’applet de commande **Start-InformationBarrierPoliciesApplication** .

    Syntaxe: `Start-InformationBarrierPoliciesApplication`

    Les modifications sont appliquées utilisateur par utilisateur pour votre organisation. Si votre organisation est volumineuse, l’exécution de ce processus peut prendre 24 heures (ou plus). En règle générale, le traitement de 5 000 comptes d’utilisateurs prend environ une heure.

4. Utilisez l’applet **de commande Remove-InformationBarrierPolicy** avec un paramètre Identity.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> Dans cet exemple, nous supprimons la stratégie qui a guid *43c37853-ea10-4b90-a23d-ab8c93772471*. |

    Lorsque vous y êtes invité, confirmez la modification.

## <a name="remove-a-segment"></a>Supprimer un segment

1. Pour afficher tous les segments existants, utilisez **l’applet de commande Get-OrganizationSegment** .

    Syntaxe: `Get-OrganizationSegment`

    Vous verrez une liste de segments et de détails pour chacun d’eux, tels que le type de segment, sa valeur UserGroupFilter, qui l’a créée ou modifiée pour la dernière fois, guid, etc.

    >[!TIP]
    >Imprimez ou enregistrez votre liste de segments pour référence ultérieurement. Par exemple, si vous souhaitez modifier un segment, vous devez connaître son nom ou identifier la valeur (utilisée avec le paramètre Identity).

2. Identifiez le segment à supprimer et assurez-vous que la stratégie IB associée au segment a été supprimée. Pour plus d’informations, consultez la procédure [Supprimer une](#remove-a-policy) stratégie.

3. Modifiez le segment qui sera supprimé pour supprimer la relation entre les utilisateurs et ce segment. Cette action met à jour la définition de segment et supprime tous les utilisateurs du segment. Vous allez utiliser le paramètre UserGroupFilter pour dissocier les utilisateurs du segment avant la suppression.

    Pour modifier un segment, utilisez l’applet de commande **Set-OrganizationSegment** avec le paramètre *Identity* et les détails pertinents.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> Dans cet exemple, pour le segment qui a le GUID c96e0837-c232-4a8a-841e-ef45787d8fcd, nous avons défini le nom de service *comme FakeDept* pour supprimer les utilisateurs du segment. Cet exemple utilise l’attribut *Department* , mais vous pouvez utiliser d’autres attributs comme il convient. L’exemple utilise *FakeDept* , car il n’existe pas et est certain de ne pas contenir d’utilisateurs. |

4. Pour appliquer vos modifications, utilisez l’applet de commande **Start-InformationBarrierPoliciesApplication** .

    Syntaxe: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >*L’attribut CleanupGroupSegmentLink* supprime les associations de groupe avec le segment sans associations d’utilisateurs.

    Les modifications sont appliquées utilisateur par utilisateur pour votre organisation. Si votre organisation est volumineuse, l’exécution de ce processus peut prendre 24 heures (ou plus). En règle générale, le traitement de 5 000 comptes d’utilisateurs prend environ une heure.

5. Pour supprimer un segment, utilisez l’applet de commande **Remove-OrganizationSegment** avec le paramètre *Identity* et les détails pertinents.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> Dans cet exemple, le segment qui a le GUID c96e0837-c232-4a8a-841e-ef45787d8fcd, a été supprimé. |

## <a name="remove-a-policy-and-segment"></a>Supprimer une stratégie et un segment

1. Pour afficher la liste des stratégies actuelles relatives aux obstacles à l’information, utilisez l’applet de commande **Get-InformationBarrierPolicy** .

    Syntaxe: `Get-InformationBarrierPolicy`

    Dans la liste des résultats, identifiez la stratégie à supprimer. Notez le GUID et le nom de la stratégie.

2. Pour afficher tous les segments existants, utilisez **l’applet de commande Get-OrganizationSegment** .

    Syntaxe: `Get-OrganizationSegment`

    Vous verrez une liste de segments et de détails pour chacun d’eux, tels que le type de segment, sa valeur de paramètre *UserGroupFilter* , qui l’a créée ou modifiée pour la dernière fois, guid, etc.

    >[!TIP]
    >Imprimez ou enregistrez votre liste de segments pour référence ultérieurement. Par exemple, si vous souhaitez modifier un segment, vous devez connaître son nom ou identifier la valeur (utilisée avec le paramètre Identity).

3. Pour définir l’état de la stratégie à supprimer sur inactif, utilisez l’applet de commande **Set-InformationBarrierPolicy** avec un paramètre *Identity* et le paramètre *State* défini sur *Inactif*.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Inactive` <br> Dans cet exemple, nous définissons une stratégie d’obstacles à l’information qui a guid 43c37853-ea10-4b90-a23d-ab8c93772471 sur un état inactif. |

4. Modifiez le segment qui sera supprimé pour supprimer la relation entre les utilisateurs et ce segment. Cette action met à jour la définition de segment et supprime tous les utilisateurs du segment. Vous allez utiliser le paramètre *UserGroupFilter* pour dissocier les utilisateurs du segment avant la suppression.

    Pour modifier un segment, utilisez l’applet de commande **Set-OrganizationSegment** avec le paramètre *Identity* et les détails pertinents.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> Dans cet exemple, pour le segment qui a le GUID c96e0837-c232-4a8a-841e-ef45787d8fcd, nous avons mis à jour le nom du service vers *FakeDept* pour supprimer les utilisateurs du segment. Cet exemple utilise l’attribut *Department* , mais vous pouvez utiliser d’autres attributs comme il convient. L’exemple utilise *FakeDept* , car il n’existe pas et est certain de ne contenir aucun utilisateur. |

5. Pour appliquer vos modifications, utilisez l’applet de commande **Start-InformationBarrierPoliciesApplication** .

    Syntaxe: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >*L’attribut CleanupGroupSegmentLink* supprime les associations de groupe avec le segment sans associations d’utilisateurs.

    Les modifications sont appliquées utilisateur par utilisateur pour votre organisation. Si votre organisation est volumineuse, l’exécution de ce processus peut prendre 24 heures (ou plus). En règle générale, le traitement de 5 000 comptes d’utilisateurs prend environ une heure.

6. Utilisez l’applet **de commande Remove-InformationBarrierPolicy** avec un paramètre *Identity* .

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> Dans cet exemple, la stratégie qui a GUID *43c37853-ea10-4b90-a23d-ab8c93772471* est supprimée. |

    Lorsque vous y êtes invité, confirmez la modification.

7. Pour supprimer un segment, utilisez l’applet de commande **Remove-OrganizationSegment** avec le paramètre *Identity* et les détails pertinents.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> Dans cet exemple, le segment avec GUID c96e0837-c232-4a8a-841e-ef45787d8fcd a été supprimé. |

## <a name="stop-a-policy-application"></a>Arrêter une application de stratégie

Une fois que vous avez commencé à appliquer des stratégies d’obstacles à l’information, si vous souhaitez empêcher l’application de ces stratégies, utilisez la procédure suivante. Le début du processus prendra environ 30 à 35 minutes.

1. Pour afficher l’état de l’application de stratégie d’obstacles à l’information la plus récente, utilisez l’applet de commande **Get-InformationBarrierPoliciesApplicationStatus** .

    Syntaxe: `Get-InformationBarrierPoliciesApplicationStatus`

    Notez le GUID de l’application.

2. Utilisez l’applet de commande **Stop-InformationBarrierPoliciesApplication** avec un paramètre Identity.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Stop-InformationBarrierPoliciesApplication -Identity GUID` | `Stop-InformationBarrierPoliciesApplication -Identity 46237888-12ca-42e3-a541-3fcb7b5231d1` <p> Dans cet exemple, nous arrêtons l’application des stratégies d’obstacles à l’information. |

## <a name="resources"></a>Ressources

- [Obtenir une vue d’ensemble des obstacles à l’information](information-barriers.md)
- [Définir des stratégies pour les obstacles à l’information](information-barriers-policies.md)
- [En savoir plus sur les obstacles à l’information dans Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [En savoir plus sur les obstacles à l’information dans SharePoint Online](/sharepoint/information-barriers)
- [En savoir plus sur les obstacles à l’information dans OneDrive](/onedrive/information-barriers)
- [Attributs pour les stratégies IB](information-barriers-attributes.md)
- [Résolution des problèmes de cloisonnement de l’information](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)
