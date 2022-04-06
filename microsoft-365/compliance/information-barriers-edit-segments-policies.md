---
title: Gérer les stratégies de obstacles à l’information
description: Découvrez comment modifier ou supprimer des stratégies et des segments pour les obstacles à l’information.
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
ms.openlocfilehash: fc8cc7e4fcbfb9fe9c2ee0f1c531511d9c2fa0b6
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634358"
---
# <a name="manage-information-barriers-policies"></a>Gérer les stratégies de obstacles à l’information

Une fois que vous avez défini des [stratégies d’obstacles](information-barriers-policies.md) à l’information, vous devrez peut-être [](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) apporter des modifications aux stratégies ou segments d’utilisateurs dans le cadre du dépannage ou pour une maintenance régulière.

## <a name="what-do-you-want-to-do"></a>Que souhaitez-vous faire ?

|**Action**|**Description**|
|:---------|:--------------|
| [Modifier les attributs d’un compte d’utilisateur](#edit-user-account-attributes) | Remplissez les attributs Azure Active Directory qui peuvent être utilisés pour définir des segments. <br> Modifiez les attributs de compte d’utilisateur lorsque les utilisateurs ne sont pas inclus dans les segments qu’ils doivent être, pour modifier les segments dans lesquels se trouver ou pour définir des segments à l’aide d’attributs différents. |
| [Modifier un segment](#edit-a-segment) | Modifiez les segments lorsque vous voulez modifier la manière dont un segment est défini. <br> Par exemple, vous avez peut-être défini à l’origine des segments à l’aide de *Department* et vous souhaitez maintenant utiliser un autre attribut, tel *que MemberOf*. |
| [Modifier une stratégie](#edit-a-policy) | Modifiez une stratégie de obstacles à l’information lorsque vous souhaitez modifier le fonctionnement d’une stratégie.<br> Par exemple, au lieu de bloquer les communications entre deux segments, vous pouvez décider de n’autoriser les communications qu’entre certains segments. |
| [Définir une stratégie sur l’état inactif](#set-a-policy-to-inactive-status) |Définissez une stratégie sur l’état inactif lorsque vous souhaitez apporter des modifications à une stratégie ou lorsque vous ne souhaitez pas qu’une stratégie soit en vigueur. |
| [Supprimer une stratégie](#remove-a-policy) | Supprimez une stratégie de obstacles à l’information lorsque vous n’avez plus besoin d’une stratégie particulière. |
| [Supprimer un segment](#remove-a-segment) | Supprimez un segment d’obstacles aux informations lorsque vous n’avez plus besoin d’un segment particulier. |
| [Supprimer une stratégie et un segment](#remove-a-policy-and-segment) | Supprimez une stratégie de obstacles à l’information et un segment en même temps. |
| [Arrêter une application de stratégie](#stop-a-policy-application) | Faites cette action lorsque vous souhaitez arrêter le processus d’application des stratégies d’obstacles à l’information. <br> L’arrêt d’une application de stratégie n’est pas instantané et n’annulera pas les stratégies déjà appliquées aux utilisateurs. |
| [Définir des stratégies pour les obstacles à l’information](information-barriers-policies.md) | Définissez une stratégie de obstacles à l’information lorsque vous n’avez pas encore mis en place de telles stratégies et que vous devez restreindre ou limiter les communications entre des groupes d’utilisateurs spécifiques. |
| [Résolution des problèmes de cloisonnement de l’information](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) | Reportez-vous à cet article lorsque vous êtes face à des problèmes inattendus avec les obstacles à l’information. |

>[!IMPORTANT]
>Pour effectuer les tâches décrites dans cet article, vous devez avoir un rôle approprié, tel que l’un des suivants :<br>- administrateur Microsoft 365 Entreprise général<br>- Administrateur général<br>- Administrateur de conformité<br>- Gestion de la conformité DE LAS (il s’agit d’un nouveau rôle !)<br><br>Pour en savoir plus sur les conditions préalables pour les obstacles à l’information, voir [Conditions préalables (pour les stratégies de obstacles à l’information).](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met)<br><br> Veillez à [vous connecter au Centre de sécurité & conformité PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="edit-user-account-attributes"></a>Modifier les attributs d’un compte d’utilisateur

Utilisez cette procédure pour modifier les attributs utilisés pour segmenter les utilisateurs. Par exemple, si vous utilisez un attribut Department et qu’aucun ou plusieurs comptes d’utilisateurs n’ont actuellement de valeurs répertoriées pour Service, vous devez modifier ces comptes d’utilisateur pour inclure des informations de service. Les attributs de compte d’utilisateur sont utilisés pour définir des segments afin que des stratégies d’obstacles à l’information soient affectées.

1. Pour afficher les détails d’un compte d’utilisateur spécifique, tels que les valeurs d’attribut et les segments affectés, utilisez la cmdlet **Get-InformationBarrierRecipientStatus** avec les paramètres Identity.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <br> Vous pouvez utiliser n’importe quelle valeur qui identifie chaque utilisateur de manière unique, telle que le nom, l’alias, le nom unique, le nom de domaine canonique, l’adresse e-mail ou le GUID. <br> (Vous pouvez également utiliser cette cmdlet pour un seul utilisateur : `Get-InformationBarrierRecipientStatus -Identity <value>`) |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <br> Dans cet exemple, nous faisons référence à deux comptes d’utilisateur dans Office 365 : *meganb* pour *Megan* et *alexw* pour *Alex*. |

2. Déterminez l’attribut à modifier pour vos profils de compte d’utilisateur. Pour plus d’informations, voir [Attributes for information barriers policies](information-barriers-attributes.md).

3. Modifiez un ou plusieurs comptes d’utilisateur pour inclure des valeurs pour l’attribut que vous avez sélectionné à l’étape précédente. Pour ce faire, utilisez l’une des procédures suivantes :

    - Pour modifier un compte unique, voir Ajouter ou mettre à jour les informations de profil [d’un utilisateur à l’aide Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

    - Pour modifier plusieurs comptes (ou utiliser PowerShell pour modifier un seul compte), voir Configurer les propriétés du compte d’utilisateur [Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

## <a name="edit-a-segment"></a>Modifier un segment

Utilisez cette procédure pour modifier la définition d’un segment d’utilisateur. Par exemple, vous pouvez modifier le nom d’un segment ou le filtre utilisé pour déterminer qui est inclus dans le segment.

1. Pour afficher tous les segments existants, utilisez la cmdlet **Get-OrganizationSegment** .

    Syntaxe : `Get-OrganizationSegment`

    Vous verrez une liste de segments et de détails pour chacun d’eux, tels que le type de segment, sa valeur UserGroupFilter, qui l’a créé ou modifié pour la dernière fois, le GUID, etc.

    > [!TIP]
    > Imprimez ou enregistrez votre liste de segments pour référence ultérieurement. Par exemple, si vous souhaitez modifier un segment, vous devez connaître son nom ou sa valeur d’identification (utilisé avec le paramètre Identity).

2. Pour modifier un segment, utilisez la cmdlet **Set-OrganizationSegment** avec le paramètre **Identity** et les détails pertinents.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` |`Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'HRDept'"` <br> Dans cet exemple, nous avons mis à jour le nom du service en *HRDept* pour le segment avec guid *c96e0837-c232-4a8a-841e-ef45787d8fcd*. |

3. Lorsque vous avez terminé la modification des segments pour votre organisation, vous pouvez [](information-barriers-policies.md#step-3-define-information-barrier-policies) définir ou [](#edit-a-policy) modifier des stratégies de obstacles aux informations.

## <a name="edit-a-policy"></a>Modifier une stratégie

1. Pour afficher la liste des stratégies de obstacles à l’information actuelles, utilisez la cmdlet **Get-InformationBarrierPolicy** .

    Syntaxe : `Get-InformationBarrierPolicy`

    Dans la liste des résultats, identifiez la stratégie à modifier. Notez le GUID et le nom de la stratégie.

2. Utilisez la cmdlet **Set-InformationBarrierPolicy** avec un paramètre **Identity** et spécifiez les modifications que vous souhaitez apporter.

    Exemple : supposons qu’une stratégie a été définie pour empêcher le segment *Recherche* de  communiquer avec *les segments* Ventes et Marketing. La stratégie a été définie à l’aide de cette cmdlet : `New-InformationBarrierPolicy -Name "Research-SalesMarketing" -AssignedSegment "Research" -SegmentsBlocked "Sales","Marketing"`

    Supposons que nous voulions le modifier afin que les personnes *du segment Recherche* ne peuvent communiquer qu’avec des personnes du segment *RESSOURCES* HUMAINES. Pour effectuer cette modification, nous utilisons cette cmdlet : `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -SegmentsAllowed "HR"`

    Dans cet exemple, nous avons modifié *SegmentsBlocked* en *SegmentsAllowed* et spécifié le segment *RH* .

3. Lorsque vous avez terminé de modifier une stratégie, veillez à appliquer vos modifications. (Voir Appliquer [les stratégies de obstacles aux informations](information-barriers-policies.md#step-4-apply-information-barrier-policies).)

## <a name="set-a-policy-to-inactive-status"></a>Définir une stratégie sur l’état inactif

1. Pour afficher la liste des stratégies de obstacles à l’information actuelles, utilisez la cmdlet **Get-InformationBarrierPolicy** .

    Syntaxe : `Get-InformationBarrierPolicy`

    Dans la liste des résultats, identifiez la stratégie que vous souhaitez modifier (ou supprimer). Notez le GUID et le nom de la stratégie.

2. Pour définir l’état de la stratégie comme inactif, utilisez la cmdlet **Set-InformationBarrierPolicy** avec un paramètre *Identity* et le paramètre *State* sur *Inactif*.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> Dans cet exemple, la stratégie d’obstacles à l’information dont le GUID *est 43c37853-ea10-4b90-a23d-ab8c9377247* est définie sur un état inactif. |

3. Pour appliquer vos modifications, utilisez l’cmdlet **Start-InformationBarrierPoliciesApplication** .

    Syntaxe : `Start-InformationBarrierPoliciesApplication`

    Les modifications sont appliquées utilisateur par utilisateur pour votre organisation. Si votre organisation est de grande taille, le processus peut prendre 24 heures (ou plus). En règle générale, le traitement de 5 000 comptes d’utilisateur prend environ une heure.

4. À ce stade, une ou plusieurs stratégies de obstacles à l’information sont définies sur l’état inactif. À partir de là, vous pouvez faire l’une des actions suivantes :

    - Conservez-la telle qu’elle est (une stratégie définie sur l’état inactif n’a aucun effet sur les utilisateurs)
    - [Modifier une stratégie](#edit-a-policy) 
    - [Supprimer une stratégie](#remove-a-policy)

## <a name="remove-a-policy"></a>Supprimer une stratégie

1. Pour afficher la liste des stratégies de obstacles à l’information actuelles, utilisez la cmdlet **Get-InformationBarrierPolicy** .

    Syntaxe : `Get-InformationBarrierPolicy`

    Dans la liste des résultats, identifiez la stratégie à supprimer. Notez le GUID et le nom de la stratégie. 

2. Assurez-vous que la stratégie est définie sur l’état inactif. Pour définir l’état de la stratégie comme inactif, utilisez la cmdlet Set-InformationBarrierPolicy avec un paramètre Identity et le paramètre State sur Inactif.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive`  | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> Dans cet exemple, nous avons fixé une stratégie de obstacles à l’information dont le GUID *43c37853-ea10-4b90-a23d-ab8c9377247* est inactif. |

3. Pour appliquer vos modifications à la stratégie, utilisez la cmdlet **Start-InformationBarrierPoliciesApplication** .

    Syntaxe : `Start-InformationBarrierPoliciesApplication`

    Les modifications sont appliquées utilisateur par utilisateur pour votre organisation. Si votre organisation est de grande taille, le processus peut prendre 24 heures (ou plus). En règle générale, le traitement de 5 000 comptes d’utilisateur prend environ une heure.

4. Utilisez la cmdlet **Remove-InformationBarrierPolicy** avec un paramètre Identity.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> Dans cet exemple, nous allons supprimer la stratégie dont le GUID *est 43c37853-ea10-4b90-a23d-ab8c93772471*. |

    Lorsque vous y invitez, confirmez la modification.

## <a name="remove-a-segment"></a>Supprimer un segment

1. Pour afficher tous les segments existants, utilisez la cmdlet **Get-OrganizationSegment** .

    Syntaxe : `Get-OrganizationSegment`

    Vous verrez une liste de segments et de détails pour chacun d’eux, tels que le type de segment, sa valeur UserGroupFilter, qui l’a créé ou modifié pour la dernière fois, le GUID, etc.

    >[!TIP]
    >Imprimez ou enregistrez votre liste de segments pour référence ultérieurement. Par exemple, si vous souhaitez modifier un segment, vous devez connaître son nom ou sa valeur d’identification (utilisé avec le paramètre Identity).

2. Identifiez le segment à supprimer et assurez-vous que la stratégie DNS associée au segment a été supprimée. Pour plus [d’informations, voir](#remove-a-policy) supprimer une procédure de stratégie.

3. Modifiez le segment qui sera supprimé pour supprimer la relation entre les utilisateurs et ce segment. Cette action met à jour la définition de segment et supprime tous les utilisateurs du segment. Vous utiliserez le paramètre UserGroupFilter pour dissocier les utilisateurs du segment avant la suppression.

    Pour modifier un segment, utilisez la cmdlet **Set-OrganizationSegment** avec le paramètre *Identity* et les détails pertinents.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> Dans cet exemple, pour le segment dont le GUID est c96e0837-c232-4a8a-841e-ef45787d8fcd, nous avons défini le nom du service en tant que *FakeDept* pour supprimer les utilisateurs du segment. Cet exemple utilise *l’attribut Department* , mais vous pouvez utiliser d’autres attributs selon le cas. L’exemple utilise *FakeDept* , car il n’existe pas et il est certain de ne pas contenir d’utilisateurs. |

4. Pour appliquer vos modifications, utilisez l’cmdlet **Start-InformationBarrierPoliciesApplication** .

    Syntaxe : `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >*L’attribut CleanupGroupSegmentLink* supprime les associations de groupe avec le segment sans associations d’utilisateurs.

    Les modifications sont appliquées utilisateur par utilisateur pour votre organisation. Si votre organisation est de grande taille, le processus peut prendre 24 heures (ou plus). En règle générale, le traitement de 5 000 comptes d’utilisateur prend environ une heure.

5. Pour supprimer un segment, utilisez la cmdlet **Remove-OrganizationSegment** avec le paramètre *Identity* et les détails pertinents.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> Dans cet exemple, le segment dont le GUID est c96e0837-c232-4a8a-841e-ef45787d8fcd8 a été supprimé. |

## <a name="remove-a-policy-and-segment"></a>Supprimer une stratégie et un segment

1. Pour afficher la liste des stratégies de obstacles à l’information actuelles, utilisez la cmdlet **Get-InformationBarrierPolicy** .

    Syntaxe : `Get-InformationBarrierPolicy`

    Dans la liste des résultats, identifiez la stratégie à supprimer. Notez le GUID et le nom de la stratégie.

2. Pour afficher tous les segments existants, utilisez la cmdlet **Get-OrganizationSegment** .

    Syntaxe : `Get-OrganizationSegment`

    Vous verrez une liste de segments et de détails pour chacun d’eux, tels que le type de segment, sa valeur de paramètre *UserGroupFilter* , qui l’a créé ou modifié pour la dernière fois, le GUID, etc.

    >[!TIP]
    >Imprimez ou enregistrez votre liste de segments pour référence ultérieurement. Par exemple, si vous souhaitez modifier un segment, vous devez connaître son nom ou sa valeur d’identification (utilisé avec le paramètre Identity).

3. Pour définir l’état de la stratégie à supprimer sur inactif, utilisez la cmdlet **Set-InformationBarrierPolicy** avec un paramètre *Identity* et le paramètre *State* sur *Inactif*.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Inactive` <br> Dans cet exemple, nous avons fixé une stratégie de obstacles à l’information dont le GUID 43c37853-ea10-4b90-a23d-ab8c93772471 est inactif. |

4. Modifiez le segment qui sera supprimé pour supprimer la relation entre les utilisateurs et ce segment. Cette action met à jour la définition de segment et supprime tous les utilisateurs du segment. Vous utiliserez le paramètre *UserGroupFilter* pour dissocier les utilisateurs du segment avant la suppression.

    Pour modifier un segment, utilisez la cmdlet **Set-OrganizationSegment** avec le paramètre *Identity* et les détails pertinents.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> Dans cet exemple, pour le segment dont le GUID est c96e0837-c232-4a8a-841e-ef45787d8fcd, nous avons mis à jour le nom du service en *FakeDept* pour supprimer les utilisateurs du segment. Cet exemple utilise *l’attribut Department* , mais vous pouvez utiliser d’autres attributs selon le cas. L’exemple utilise *FakeDept* , car il n’existe pas et ne contient aucun utilisateur. |

5. Pour appliquer vos modifications, utilisez l’cmdlet **Start-InformationBarrierPoliciesApplication** .

    Syntaxe : `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >*L’attribut CleanupGroupSegmentLink* supprime les associations de groupe avec le segment sans associations d’utilisateurs.

    Les modifications sont appliquées utilisateur par utilisateur pour votre organisation. Si votre organisation est de grande taille, le processus peut prendre 24 heures (ou plus). En règle générale, le traitement de 5 000 comptes d’utilisateur prend environ une heure.

6. Utilisez la cmdlet **Remove-InformationBarrierPolicy** avec un *paramètre Identity* .

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> Dans cet exemple, la stratégie dont le GUID *est 43c37853-ea10-4b90-a23d-ab8c93772471* est supprimée. |

    Lorsque vous y invitez, confirmez la modification.

7. Pour supprimer un segment, utilisez la cmdlet **Remove-OrganizationSegment** avec le paramètre *Identity* et les détails pertinents.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> Dans cet exemple, le segment avec GUID c96e0837-c232-4a8a-841e-ef45787d8fcd8 a été supprimé. |

## <a name="stop-a-policy-application"></a>Arrêter une application de stratégie

Une fois que vous avez commencé à appliquer des stratégies d’obstacles à l’information, si vous souhaitez empêcher l’application de ces stratégies, appliquez la procédure suivante. Le processus prendra environ 30 à 35 minutes.

1. Pour afficher l’état de l’application de stratégie d’obstacles à l’information la plus récente, utilisez la cmdlet **Get-InformationBarrierPoliciesApplicationStatus** .

    Syntaxe : `Get-InformationBarrierPoliciesApplicationStatus`

    Notez le GUID de l’application.

2. Utilisez la cmdlet **Stop-InformationBarrierPoliciesApplication** avec un paramètre Identity.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Stop-InformationBarrierPoliciesApplication -Identity GUID` | `Stop-InformationBarrierPoliciesApplication -Identity 46237888-12ca-42e3-a541-3fcb7b5231d1` <p> Dans cet exemple, nous arrêtons l’application des stratégies de obstacles à l’information. |

## <a name="resources"></a>Ressources

- [Obtenir une vue d’ensemble des obstacles aux informations](information-barriers.md)
- [Définir des stratégies pour les obstacles à l’information](information-barriers-policies.md)
- [En savoir plus sur les obstacles aux informations dans Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [En savoir plus sur les obstacles aux informations dans SharePoint Online](/sharepoint/information-barriers)
- [En savoir plus sur les obstacles aux informations dans OneDrive](/onedrive/information-barriers)
- [Attributs des stratégies de obstacles à l’information](information-barriers-attributes.md)
- [Résolution des problèmes de cloisonnement de l’information](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)