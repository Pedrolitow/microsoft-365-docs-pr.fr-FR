---
title: Résolution des problèmes d’obstacles aux informations
description: Utilisez cet article comme guide pour résoudre les problèmes d’obstacles aux informations.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
localization_priority: None
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3810dd977ef0d25642ba86a2b62a036c9a4ace06
ms.sourcegitcommit: eac5d9f759f290d3c51cafaf335a1a1c43ded927
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2021
ms.locfileid: "50126561"
---
# <a name="troubleshooting-information-barriers"></a>Résolution des problèmes d’obstacles aux informations

[Les obstacles à l’information](information-barriers.md) peuvent aider votre organisation à rester conforme aux exigences légales et aux réglementations du secteur. Par exemple, avec les obstacles à l’information, vous pouvez restreindre la communication entre des groupes spécifiques d’utilisateurs afin d’éviter un conflit d’intérêts ou d’autres problèmes. (Pour en savoir plus sur la façon de configurer les obstacles à l’information, voir Définir des [stratégies pour les obstacles à l’information.)](information-barriers-policies.md)

Si des personnes rencontrent des problèmes inattendus après que des obstacles à l’information sont en place, vous pouvez prendre certaines mesures pour résoudre ces problèmes. Utilisez cet article comme guide.

> [!IMPORTANT]
> Pour effectuer les tâches décrites dans cet article, vous devez avoir un rôle approprié, tel que l’un des suivants :<br/>- Administrateur général Microsoft 365 Entreprise<br/>- Administrateur général<br/>- Administrateur de conformité<br/>- Gestion de la conformité DUES (il s’agit d’un nouveau rôle !)<p>Pour en savoir plus sur les conditions préalables pour les obstacles à l’information, voir [Conditions préalables (pour les stratégies d’obstacle à l’information).](information-barriers-policies.md#prerequisites)<p>Veillez à [vous connecter au Centre de sécurité & conformité PowerShell.](/powershell/exchange/connect-to-scc-powershell)

## <a name="issue-users-are-unexpectedly-blocked-from-communicating-with-others-in-microsoft-teams"></a>Problème : les utilisateurs ne peuvent pas communiquer avec d’autres personnes dans Microsoft Teams. 

Dans ce cas, les personnes rapportent des problèmes inattendus lors de la communication avec d’autres personnes dans Microsoft Teams. En voici quelques exemples :

- Un utilisateur recherche, mais n’est pas en mesure de le trouver, un autre utilisateur dans Microsoft Teams.
- Un utilisateur peut trouver, mais ne peut pas sélectionner, un autre utilisateur dans Microsoft Teams.
- Un utilisateur peut voir un autre utilisateur, mais ne peut pas lui envoyer de messages dans Microsoft Teams.

### <a name="what-to-do"></a>Procédure

Déterminez si les utilisateurs sont affectés par une stratégie d’obstacle à l’information. Selon la façon dont les stratégies sont configurées, les obstacles à l’information peuvent fonctionner comme prévu. Vous pouvez également être dans l’devoir d’affiner les stratégies de votre organisation.

1. Utilisez la cmdlet **Get-InformationBarrierRecipientStatus** avec le paramètre Identity. 

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity` <p> Vous pouvez utiliser n’importe quelle valeur d’identité qui identifie de manière unique chaque destinataire, telle que le nom, l’alias, le nom unique (DN), le nom unique canonique, l’adresse e-mail ou le GUID. |`Get-InformationBarrierRecipientStatus -Identity meganb` <p> Dans cet exemple, nous utilisons un alias (*meganb*) pour le paramètre Identity. Cette cmdlet retourne des informations qui indiquent si l’utilisateur est affecté par une stratégie d’obstacle à l’information. (Recherchez *ExoPolicyId : \<GUID> .) |

    **Si les utilisateurs ne sont pas inclus dans les stratégies d’obstacle à l’information, contactez le support technique.** Sinon, passez à l’étape suivante.

2. Découvrez les segments inclus dans une stratégie d’obstacle à l’information. Pour ce faire, utilisez la `Get-InformationBarrierPolicy` cmdlet avec le paramètre Identity. 

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Get-InformationBarrierPolicy` <p> Utilisez des détails, tels que le GUID de stratégie (ExoPolicyId) que vous avez reçu à l’étape précédente, en tant que valeur d’identité. | `Get-InformationBarrierPolicy -Identity b42c3d0f-49e9-4506-a0a5-bf2853b5df6f` <p> Dans cet exemple, nous allons obtenir des informations détaillées sur la stratégie d’obstacle aux informations qui possède ExoPolicyId *b42c3d0f-49e9-4506-a0a5-bf2853b5df6f*. |

    Après avoir exécuté l’cmdlet, dans les résultats, recherchez les valeurs **AssignedSegment,** **SegmentsAllowed** et **SegmentsBlocked.**

    Par exemple, après l’exécution de la cmdlet, nous avons vu ce qui suit `Get-InformationBarrierPolicy` dans notre liste de résultats :

    ```powershell
    AssignedSegment : Sales
    SegmentsAllowed : {}
    SegmentsBlocked : {Research}
    ```

    Dans ce cas, nous pouvons voir qu’une stratégie d’obstacle à l’information affecte les personnes qui font partie des segments Ventes et Recherche. Dans ce cas, les employés de Sales ne peuvent pas communiquer avec des personnes de recherche.

    Si cela semble correct, les obstacles aux informations fonctionnent comme prévu. Si ce n’est pas le cas, passez à l’étape suivante.

3. Assurez-vous que vos segments sont définis correctement. Pour ce faire, utilisez la `Get-OrganizationSegment` cmdlet et examinez la liste des résultats.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Get-OrganizationSegment`<p> Utilisez cette cmdlet avec un paramètre Identity. | `Get-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <p> Dans cet exemple, nous allons obtenir des informations sur le segment dont le GUID *est c96e0837-c232-4a8a-841e-ef45787d8fcd*. |

    Examinez les détails du segment. Si nécessaire, [modifiez un segment,](information-barriers-edit-segments-policies.md#edit-a-segment)puis ré-utilisez l’cmdlet. `Start-InformationBarrierPoliciesApplication`

    Si vous avez encore des problèmes avec votre stratégie d’obstacle **à l’information, contactez le support technique.**

## <a name="issue-communications-are-allowed-between-users-who-should-be-blocked-in-microsoft-teams"></a>Problème : les communications sont autorisées entre les utilisateurs qui doivent être bloqués dans Microsoft Teams

Dans ce cas, bien que les obstacles à l’information soient définis, actifs et appliqués, les personnes qui doivent être empêchées de communiquer entre elles sont en quelque sorte en mesure de discuter et de s’appeler mutuellement dans Microsoft Teams.

### <a name="what-to-do"></a>Procédure

Vérifiez que les utilisateurs en question sont inclus dans une stratégie d’obstacle aux informations. 

1. Utilisez la cmdlet **Get-InformationBarrierRecipientStatus** avec les paramètres Identity.

    |**Syntaxe** _|_ *Exemple**|
    |:----------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Vous pouvez utiliser n’importe quelle valeur qui identifie chaque utilisateur de manière unique, telle que le nom, l’alias, le nom unique, le nom de domaine canonique, l’adresse e-mail ou le GUID. |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> Dans cet exemple, nous faisons référence à deux comptes d’utilisateurs dans Office 365 : *meganb* pour *Megan* et *alexw* pour *Alex*. |

    > [!TIP]
    > Vous pouvez également utiliser cette cmdlet pour un seul utilisateur : `Get-InformationBarrierRecipientStatus -Identity <value>`

2. Examinez les résultats. La cmdlet **Get-InformationBarrierRecipientStatus** renvoie des informations sur les utilisateurs, telles que les valeurs d’attribut et les stratégies de obstacle aux informations appliquées.

    Examinez les résultats, puis prenez les étapes suivantes, comme décrit dans le tableau suivant :

    |**Results**|**Que faire ensuite ?**|
    |:----------|:------------------|
    | Aucun segment n’est répertorié pour les utilisateurs sélectionnés | Effectuez l’une des opérations suivantes :<br/>- Affecter des utilisateurs à un segment existant en éditant leurs profils utilisateur dans Azure Active Directory. (Voir [Configurer les propriétés de compte d’utilisateur avec Office 365 PowerShell.)](/microsoft-365/enterprise/configure-user-account-properties-with-microsoft-365-powershell)<br/>- Définissez un segment à l’aide [d’un attribut pris en charge pour les obstacles à l’information.](information-barriers-attributes.md) Ensuite, [définissez une nouvelle stratégie ou](information-barriers-policies.md#part-2-define-information-barrier-policies) [modifiez une stratégie existante](information-barriers-edit-segments-policies.md#edit-a-policy) pour inclure ce segment. |
    | Les segments sont répertoriés, mais aucune stratégie d’obstacle aux informations n’est affectée à ces segments | Effectuez l’une des opérations suivantes :<br/>- [Définir une nouvelle stratégie de obstacle aux informations](information-barriers-policies.md#part-2-define-information-barrier-policies) pour chaque segment en question <br/>- [Modifier une stratégie d’obstacle aux informations existante pour](information-barriers-edit-segments-policies.md#edit-a-policy) l’affecter au segment correct |
    | Les segments sont répertoriés et chacun d’eux est inclus dans une stratégie d’obstacle aux informations | - Exécutez `Get-InformationBarrierPolicy` l’cmdlet pour vérifier que les stratégies de obstacle aux informations sont actives<br/>- Exécutez la `Get-InformationBarrierPoliciesApplicationStatus` cmdlet pour confirmer que les stratégies sont appliquées<br/>- Exécutez la `Start-InformationBarrierPoliciesApplication` cmdlet pour appliquer toutes les stratégies actives d’obstacle aux informations |

## <a name="issue-i-need-to-remove-a-single-user-from-an-information-barrier-policy"></a>Problème : je dois supprimer un seul utilisateur d’une stratégie d’obstacle aux informations

Dans ce cas, les stratégies de blocage de l’information sont en vigueur et un ou plusieurs utilisateurs ne peuvent pas communiquer avec d’autres personnes dans Microsoft Teams. Au lieu de supprimer complètement les stratégies d’obstacle à l’information, vous pouvez supprimer un ou plusieurs utilisateurs individuels des stratégies d’obstacle à l’information.

### <a name="what-to-do"></a>Procédure

Les stratégies d’obstacle à l’information sont affectées à des segments d’utilisateurs. Les segments sont définis à l’aide de certains [attributs dans les profils de compte d’utilisateur.](information-barriers-attributes.md) Si vous devez supprimer une stratégie d’un seul utilisateur, envisagez de modifier le profil de cet utilisateur dans Azure Active Directory afin que l’utilisateur ne soit plus inclus dans un segment affecté par les obstacles à l’information.

1. Utilisez la cmdlet **Get-InformationBarrierRecipientStatus** avec les paramètres Identity. Cette cmdlet renvoie des informations sur les utilisateurs, telles que les valeurs d’attribut et les stratégies de obstacle aux informations appliquées.

    |**Syntaxe**|**Exemple**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Vous pouvez utiliser n’importe quelle valeur qui identifie chaque utilisateur de manière unique, telle que le nom, l’alias, le nom unique, le nom de domaine canonique, l’adresse e-mail ou le GUID. | `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> Dans cet exemple, nous faisons référence à deux comptes d’utilisateurs dans Office 365 : *meganb* pour *Megan* et *alexw* pour *Alex*.          |
    | `Get-InformationBarrierRecipientStatus -Identity <value>` <p> Vous pouvez utiliser n’importe quelle valeur qui identifie l’utilisateur de manière unique, telle que le nom, l’alias, le nom unique, le nom de domaine canonique, l’adresse e-mail ou le GUID.|`Get-InformationBarrierRecipientStatus -Identity jeanp`<p> Dans cet exemple, nous faisons référence à un seul compte dans Office 365 : *jeanp*. |

2. Examinez les résultats pour voir si des stratégies d’obstacle aux informations sont affectées et à quels segments le ou les utilisateurs appartiennent.

3. Pour supprimer un utilisateur d’un segment affecté par les obstacles à l’information, mettez à jour les informations de profil de [l’utilisateur dans Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

4. Attendez environ 30 minutes que FwdSync se produise. Vous pouvez également exécuter la `Start-InformationBarrierPoliciesApplication` cmdlet pour appliquer toutes les stratégies actives d’obstacle aux informations.

## <a name="issue-the-information-barrier-application-process-is-taking-too-long"></a>Problème : le processus d’application de obstacle à l’information prend trop de temps

Après l’exécution de la cmdlet **Start-InformationBarrierPoliciesApplication,** la fin du processus prend beaucoup de temps.

### <a name="what-to-do"></a>Procédure

N’oubliez pas que lorsque vous exécutez la cmdlet d’application de stratégie, des stratégies d’obstacle aux informations sont appliquées (ou supprimées), utilisateur par utilisateur, pour tous les comptes de votre organisation. Si vous avez un grand nombre d’utilisateurs, le processus prendra un certain temps. (En règle générale, le traitement de 5 000 comptes d’utilisateur prend environ une heure.)

1. La cmdlet **Get-InformationBarrierPoliciesApplicationStatus** permet de vérifier l’état de l’application de stratégie la plus récente.

    |**Pour afficher l’application de stratégie la plus récente**|**Pour afficher l’état de toutes les applications de stratégie**|
    |:---------------------------------------------|:---------------------------------------------|
    | `Get-InformationBarrierPoliciesApplicationStatus` | `Get-InformationBarrierPoliciesApplicationStatus -All $true` |

    Cela permet d’afficher des informations sur la fin, l’échec ou l’avancement de l’application de stratégie.

2. En fonction des résultats de l’étape précédente, prenez l’une des étapes suivantes :
  
    |**État**|**Étape suivante**|
    |:---------|:------------|
    | **Non commencée** | Si cela fait plus de 45 minutes que la cmdlet **Start-InformationBarrierPoliciesApplication** a été exécuté, consultez votre journal d’audit pour voir s’il existe des erreurs dans les définitions de stratégie ou une autre raison pour laquelle l’application n’a pas démarré. |
    | **Échec** | Si l’application a échoué, examinez votre journal d’audit. Examinez également vos segments et stratégies. Des utilisateurs sont-ils affectés à plusieurs segments ? Des segments sont-ils affectés à plusieurs segments ? Si nécessaire, [modifiez des segments](information-barriers-edit-segments-policies.md#edit-a-segment) et/ou [](information-barriers-edit-segments-policies.md#edit-a-policy)modifiez des stratégies, puis ré-exécutez l’cmdlet **Start-InformationBarrierPoliciesApplication.** |
    | **En cours** | Si l’application est toujours en cours, laissez plus de temps pour se terminer. Si cela fait plusieurs jours, collectez vos journaux d’audit, puis contactez le support technique. |

## <a name="issue-information-barrier-policies-are-not-being-applied-at-all"></a>Problème : les stratégies d’obstacle à l’information ne sont pas appliquées du tout

Dans ce cas, vous avez défini des segments, défini des stratégies d’obstacle aux informations et tenté d’appliquer ces stratégies. Toutefois, lorsque vous exécutez la cmdlet, vous pouvez voir que `Get-InformationBarrierPoliciesApplicationStatus` l’application de stratégie a échoué.

### <a name="what-to-do"></a>Procédure

Assurez-vous que votre organisation n’a pas de stratégies de [carnet d’adresses Exchange](/exchange/address-books/address-book-policies/address-book-policies) en place. De telles stratégies empêcheront l’application de stratégies de obstacle à l’information.

1. Connectez-vous à [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez la cmdlet [Get-AddressBookPolicy](/powershell/module/exchange/get-addressbookpolicy) et examinez les résultats.

    |**Results**|**Étape suivante**|
    |:----------|:------------|
    | Les stratégies de carnet d’adresses Exchange sont répertoriées | [Supprimer des stratégies de carnet d’adresses](/exchange/address-books/address-book-policies/remove-an-address-book-policy) |
    | Aucune stratégie de carnet d’adresses n’existe |Consulter vos journaux d’audit pour savoir pourquoi l’application de stratégie échoue |

3. [Afficher l’état des comptes d’utilisateur, des segments, des stratégies ou de l’application de stratégie.](information-barriers-policies.md#view-status-of-user-accounts-segments-policies-or-policy-application)

## <a name="issue-information-barrier-policy-not-applied-to-all-designated-users"></a>Problème : stratégie de obstacle à l’information non appliquée à tous les utilisateurs désignés

Après avoir défini des segments, défini des stratégies d’obstacle aux informations et tenté d’appliquer ces stratégies, il se peut que vous trouviez que la stratégie s’applique à certains destinataires, mais pas à d’autres.
Lorsque vous exécutez la `Get-InformationBarrierPoliciesApplicationStatus` cmdlet, recherchez du texte comme celui-ci dans la sortie.

> Identité : `<application guid>`
>
> Nombre total de destinataires : 81527
>
> Destinataires en échec : 2
>
> Catégorie d’échec : Aucune
>
> Status: Complete

### <a name="what-to-do"></a>Procédure

1. Recherchez . `<application guid>` Vous pouvez copier ce code PowerShell et modifier vos variables.

```powershell
$DetailedLogs = Search-UnifiedAuditLog -EndDate <yyyy-mm-ddThh:mm:ss>  -StartDate <yyyy-mm-ddThh:mm:ss> -RecordType InformationBarrierPolicyApplication -ResultSize 1000 |?{$_.AuditData.Contains(<application guid>)} 
```

2. Vérifiez la sortie détaillée du journal d’audit pour les valeurs des champs `"UserId"` et des `"ErrorDetails"` champs. Cela vous donnera la raison de l’échec. Vous pouvez copier ce code PowerShell et modifier vos variables.

```powershell
   $DetailedLogs[1] |fl
```

Par exemple :

> « UserId » : User1
>
>« ErrorDetails »:"Status:TROPPolicyConflict. Erreur : le segment DE LATS « id1 » et le segment « id2 de segment 2 » sont en conflit et ne peuvent pas être affectés au destinataire.

3. En règle générale, vous constatez qu’un utilisateur a été inclus dans plusieurs segments. Vous pouvez résoudre ce problème en mettant à jour `-UserGroupFilter` la valeur dans `OrganizationSegments` .

4. Ré-appliquez les stratégies d’obstacle à l’information à l’aide de ces [procédures stratégies de obstacles à l’information.](information-barriers-policies.md#part-3-apply-information-barrier-policies)

## <a name="resources"></a>Ressources

- [Définir des stratégies pour les obstacles aux informations dans Microsoft Teams](information-barriers-policies.md)
- [Obstacles aux informations](information-barriers.md)
