---
title: Définir des stratégies d’obstacle aux informations
description: Découvrez comment définir des stratégies pour les obstacles aux informations dans Microsoft Teams.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
localization_priority: None
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ce387799a2f9e6d6cdffe063d3adf7310d7e7757
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52842721"
---
# <a name="define-information-barrier-policies"></a>Définir des stratégies d’obstacle aux informations

Avec les obstacles à l’information, vous pouvez définir des stratégies conçues pour empêcher certains segments d’utilisateurs de communiquer entre eux, ou autoriser des segments spécifiques à communiquer uniquement avec certains autres segments. Les stratégies d’obstacle à l’information peuvent aider votre organisation à maintenir la conformité avec les normes et réglementations du secteur pertinentes et à éviter les conflits d’intérêts potentiels. Pour plus d’informations, voir [Obstacles à l’information.](information-barriers.md)

Cet article explique comment planifier, définir, implémenter et gérer des stratégies de obstacle à l’information. Plusieurs étapes sont impliquées et le flux de travail est divisé en plusieurs parties. Veillez à lire les conditions [préalables](#prerequisites) et l’ensemble du processus avant de commencer à définir (ou modifier) des stratégies d’obstacle à l’information.

> [!TIP]
> Cet article inclut un exemple [de scénario](#example-contosos-departments-segments-and-policies) et un Excel [téléchargeable](https://github.com/MicrosoftDocs/OfficeDocs-O365SecComp/raw/public/SecurityCompliance/media/InfoBarriers-PowerShellGenerator.xlsx) pour vous aider à planifier et définir vos stratégies d’obstacle à l’information.

## <a name="concepts-of-information-barrier-policies"></a>Concepts des stratégies de cloisonnement de l’information

Lorsque vous définissez des stratégies pour les obstacles à l’information, vous travaillez avec les attributs de compte d’utilisateur, les segments, les stratégies « bloquer » et/ou « autoriser » et l’application de stratégie.

- Les attributs du compte utilisateur sont définis dans Azure Active Directory (ou Exchange Online). Ces attributs peuvent inclure le service, la fonction, l’emplacement, le nom d’équipe et d’autres détails du profil du poste. 
- Les segments sont des ensembles d’utilisateurs définis dans le Centre de sécurité & conformité à l’aide d’un attribut de compte **d’utilisateur sélectionné.** (consultez la [liste des attributs pris en charge](information-barriers-attributes.md)).
- Les stratégies de cloisonnement de l’information déterminent les limites ou les restrictions de communication. Lorsque vous définissez des stratégies de cloisonnement de l’information, vous avez le choix entre deux types de stratégie :
    - Les stratégies « Bloquer » empêchent un segment de communiquer avec un autre segment.
    - Les stratégies « Autoriser » permettent à un segment de communiquer uniquement avec certains autres segments.
- L’application de la stratégie est effectuée une fois toutes les stratégies de cloisonnement de l’information sont définies et que vous êtes prêt à les appliquer au sein de votre organisation.

## <a name="the-work-flow-at-a-glance"></a>Flux de travail en un clin d’œil

| Phase | Ce qui est impliqué |
|:--------|:------------------|
| [S’assurer que les conditions préalables sont remplies](#prerequisites) | - Vérifier que vous avez les [licences et autorisations requises](information-barriers.md#required-licenses-and-permissions)<br/>- Vérifier que votre annuaire inclut des données pour segmenter les utilisateurs<br/>- Activer la recherche dans l’annuaire dans l’étendue Microsoft Teams<br/>- Assurez-vous que la journalisation d’audit est allumée<br/>- Assurez-vous qu’aucune stratégie Exchange de carnet d’adresses n’est en place<br/>- Utiliser PowerShell (des exemples sont fournis)<br/>- Fournir le consentement de l’administrateur Microsoft Teams (les étapes sont incluses) |
| [Partie 1 : segmenter les utilisateurs de votre organisation](#part-1-segment-users) | - Déterminer les stratégies nécessaires<br/>- Établir une liste de segments à définir<br/>- Identifier les attributs à utiliser<br/>- Définir des segments en termes de filtres de stratégie |
| [Partie 2 : définir des stratégies de obstacle aux informations](#part-2-define-information-barrier-policies) | - Définir vos stratégies (ne s’appliquent pas encore)<br/>- Choisir parmi deux types (bloquer ou autoriser) |
| [Partie 3 : appliquer des stratégies de obstacle aux informations](#part-3-apply-information-barrier-policies) | - Définir des stratégies sur l’état actif<br/>- Exécuter l’application de stratégie<br/>- Afficher l’état de la stratégie |
| (Selon les besoins) [Modifier un segment ou une stratégie](information-barriers-edit-segments-policies.md) | - Modifier un segment<br/>- Modifier ou supprimer une stratégie<br/>- Réexécuter l’application de stratégie<br/>- Afficher l’état de la stratégie |
| (Selon les besoins) [Résolution des problèmes](information-barriers-troubleshooting.md)| - Prendre des mesures lorsque les choses ne fonctionnent pas comme prévu|

## <a name="prerequisites"></a>Configuration requise

En plus des [licences et autorisations requises,](information-barriers.md#required-licenses-and-permissions)assurez-vous que les conditions suivantes sont remplies :

- Données d’annuaire : assurez-vous que la structure de votre organisation est reflétée dans les données d’annuaire. Pour effectuer cette action, assurez-vous que les attributs de compte d’utilisateur, tels que l’appartenance à un groupe, le nom du service, etc. sont correctement remplis dans Azure Active Directory (ou Exchange Online). Pour en savoir plus, consultez les ressources suivantes :
  - [Attributs pour les stratégies d’obstacle aux informations](information-barriers-attributes.md)
  - [Ajouter ou mettre à jour les informations de profil d’un utilisateur à l’aide Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [Configurer les propriétés des comptes d'utilisateur avec Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)

- Recherche dans l’annuaire dans l’étendue : avant de définir la première stratégie d’obstacle aux informations de votre [organisation,](/MicrosoftTeams/teams-scoped-directory-search)vous devez activer la recherche dans l’annuaire Microsoft Teams . Patientez au moins 24 heures après l’activation de la recherche dans l’annuaire dans l’étendue avant de configurer ou de définir des stratégies d’obstacle à l’information.

- Licence EXO : les stratégies DE LAS fonctionnent uniquement si une licence EXO a été attribuée aux utilisateurs cibles.

- Journalisation d’audit : pour rechercher l’état d’une application de stratégie, l’enregistrement d’audit doit être allumé. Nous vous recommandons d’activer l’audit avant de commencer à définir des segments ou des stratégies. Pour plus d’informations, voir Activer ou désactiver la [recherche dans le journal d’audit.](turn-audit-log-search-on-or-off.md)

- Aucune stratégie de carnet d’adresses - Avant de définir et d’appliquer des stratégies de barrières aux informations, assurez-vous qu’Exchange stratégies de carnet d’adresses ne sont pas en place. Les obstacles aux informations sont basés sur les stratégies de carnet d’adresses, mais les deux types de stratégies ne sont pas compatibles. Si vous avez de telles stratégies, veillez d’abord à supprimer [vos stratégies de carnet d’adresses.](/exchange/address-books/address-book-policies/remove-an-address-book-policy) Une fois que les stratégies d’obstacle à l’information sont activées et que le [](/exchange/address-books/hierarchical-address-books/hierarchical-address-books) carnet d’adresses hiérarchique est activé, tous les utilisateurs qui ne sont pas inclus dans un segment d’obstacles à l’information voient le carnet d’adresses hiérarchique dans Exchange en ligne. 

- PowerShell : actuellement, les stratégies d’obstacle aux informations sont définies et gérées dans le Centre de sécurité Office 365 conformité & à l’aide des cmdlets PowerShell. Bien que plusieurs exemples soient fournis dans cet article, vous devez être familiarisé avec les cmdlets et paramètres PowerShell. Vous aurez également besoin du module Azure PowerShell’équipe.
    - [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell)
    - [Installer le module Azure PowerShell’installation](/powershell/azure/install-az-ps?view=azps-2.3.2)

- Consentement de l’administrateur pour les obstacles à l’information dans Microsoft Teams : lorsque vos stratégies DE DISTRIBUTION sont en place, ils peuvent supprimer les utilisateurs de conformité non-TOA des groupes (c’est-à-dire les canaux Teams, qui sont basés sur des groupes). Cette configuration permet de s’assurer que votre organisation reste conforme aux stratégies et réglementations. Utilisez la procédure suivante pour permettre aux stratégies d’obstacle aux informations de fonctionner comme prévu dans Microsoft Teams.

   1. Conditions préalables : installer les Azure PowerShell à partir [d’Install Azure PowerShell](/powershell/azure/install-az-ps).

   1. Exécutez les cmdlets PowerShell suivantes :

      ```powershell
      Connect-AzAccount -Tenant "<yourtenantdomain.com>"  //for example: Connect-AzAccount -Tenant "Contoso.onmicrosoft.com"
      $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
      $sp=Get-AzADServicePrincipal -ServicePrincipalName $appId
      if ($sp -eq $null) { New-AzADServicePrincipal -ApplicationId $appId }
      Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
      ```

   1. Lorsque vous y invitez, connectez-vous à l’aide de votre compte scolaire ou Office 365.

   1. Dans la **boîte de dialogue Autorisations demandées,** examinez les informations, puis choisissez **Accepter**. Les autorisations demandées par l’application sont accordées ci-dessous.
      
      > [!div class="mx-imgBorder"]
      > ![image](https://user-images.githubusercontent.com/8932063/107690955-b1772300-6c5f-11eb-9527-4235de860b27.png)


Lorsque toutes les conditions préalables sont remplies, passer à la section suivante.

> [!TIP]
> Pour vous aider à préparer votre plan, un exemple de scénario est inclus dans cet article. [Consultez les services, segments et stratégies de Contoso.](#example-contosos-departments-segments-and-policies)<p>En outre, un Excel téléchargeable est disponible pour vous aider à planifier et définir vos segments et stratégies (et à créer vos cmdlets PowerShell). [Obtenir le workbook](https://github.com/MicrosoftDocs/OfficeDocs-O365SecComp/raw/public/SecurityCompliance/media/InfoBarriers-PowerShellGenerator.xlsx).

## <a name="part-1-segment-users"></a>Partie 1 : segmenter les utilisateurs

Au cours de cette phase, vous déterminez les stratégies d’obstacle aux informations qui sont nécessaires, vous devez établir une liste de segments à définir, puis définir vos segments.

### <a name="determine-what-policies-are-needed"></a>Déterminer les stratégies nécessaires

Compte tenu des réglementations légales et industrielles, qui sont les groupes au sein de votre organisation qui auront besoin de stratégies de obstacle à l’information ? Faites une liste. Existe-t-il des groupes qui doivent être empêchés de communiquer avec un autre groupe ? Existe-t-il des groupes qui doivent être autorisés à communiquer uniquement avec un ou deux autres groupes ? Pensez aux stratégies dont vous avez besoin comme appartenant à l’un des deux groupes :

- Les stratégies de blocage empêchent un groupe de communiquer avec un autre groupe.
- Les stratégies d'« autoriser » permettent à un groupe de communiquer uniquement avec certains autres groupes spécifiques.

Lorsque vous avez votre liste initiale de groupes et de stratégies, continuez à identifier les segments dont vous aurez besoin.

### <a name="identify-segments"></a>Identifier les segments

En plus de votre liste initiale de stratégies, faites une liste de segments pour votre organisation. Les utilisateurs qui seront inclus dans les stratégies d’obstacle à l’information doivent appartenir à un segment. Planifiez soigneusement vos segments en tant qu’utilisateur ne peut se trouver que dans un seul segment. Chaque segment ne peut avoir qu’une seule stratégie d’obstacle aux informations appliquée.

> [!IMPORTANT]
> Un utilisateur ne peut se trouver que dans un seul segment.

Déterminez les attributs dans les données d’annuaire de votre organisation que vous utiliserez pour définir des segments. Vous pouvez utiliser *Service,* *MemberOf* ou l’un des attributs pris en charge. Assurez-vous que vous avez des valeurs dans l’attribut que vous sélectionnez pour les utilisateurs. [Consultez la liste des attributs pris en charge pour les obstacles aux informations.](information-barriers-attributes.md)

> [!IMPORTANT]
> **Avant de passer à la section suivante,** assurez-vous que vos données d’annuaire ont des valeurs pour les attributs que vous pouvez utiliser pour définir des segments. Si vos données d’annuaire ne comportent pas de valeurs pour les attributs que vous souhaitez utiliser, les comptes d’utilisateurs doivent être mis à jour pour inclure ces informations avant de passer aux obstacles à l’information. Pour obtenir de l’aide, consultez les ressources suivantes :<br/>- [Configurer les propriétés du compte d’utilisateur Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)<br/>- [Ajouter ou mettre à jour les informations de profil d’un utilisateur à l’aide Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

### <a name="define-segments-using-powershell"></a>Définir des segments à l’aide de PowerShell

La définition de segments n’affecte pas les utilisateurs ; Il définit simplement la phase de définition et d’application des stratégies d’obstacle à l’information.

1. Utilisez la cmdlet **New-OrganizationSegment** avec le **paramètre UserGroupFilter** qui correspond à l’attribut [que](information-barriers-attributes.md) vous souhaitez utiliser.

    | Syntaxe | Exemple |
    |:---------|:----------|
    | `New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"` |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>Dans cet exemple, un segment appelé *HR* est défini à l’aide de *HR*, une valeur dans l’attribut *Department.* La **partie -eq** de la cmdlet fait référence à « égal à ». (Vous pouvez également utiliser **-ne** pour dire « n’est pas égal à ». Voir Utilisation des valeurs « égal à » et « [non égal à » dans les définitions de segment.)](#using-equals-and-not-equals-in-segment-definitions) |

    Après avoir exécuté chaque cmdlet, vous devez voir une liste de détails sur le nouveau segment. Les détails incluent le type du segment, qui l’a créé ou modifié pour la dernière fois, etc. 

2. Répétez ce processus pour chaque segment que vous souhaitez définir.

    > [!IMPORTANT]
    > **Assurez-vous que vos segments ne se chevauchent pas.** Chaque utilisateur qui sera affecté par les obstacles à l’information doit appartenir à un (et un seul) segment. Aucun utilisateur ne doit appartenir à au moins deux segments. (Voir [l’exemple : segments définis par Contoso](#contosos-defined-segments) dans cet article.)

Une fois que vous avez défini vos segments, continuez à définir des stratégies de [obstacle à l’information.](#part-2-define-information-barrier-policies)

### <a name="using-equals-and-not-equals-in-segment-definitions"></a>Utilisation de « equals » et « not equals » dans les définitions de segment

Dans l’exemple suivant, nous définissons un segment de telle façon que « Service est égal à HR ». 

| Exemple | Remarque |
|:----------|:-------|
|`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` | Notez que dans cet exemple, la définition de segment inclut un paramètre « equals » (égal à) qui est le **paramètre -eq**. |

Vous pouvez également définir des segments à l’aide d’un paramètre « not equals », indiqué **par -ne,** comme indiqué dans le tableau suivant :

| Syntaxe | Exemple |
|:---------|:----------|
| `New-OrganizationSegment -Name "NotSales" -UserGroupFilter "Department -ne 'Sales'"` | Dans cet exemple, nous avons défini un segment appelé *NotSales* qui inclut tout le monde qui n’est pas dans *sales*. La **partie -ne** de la cmdlet fait référence à « n’est pas égal à ». |

En plus de définir des segments à l’aide de « equals » ou « not equals », vous pouvez définir un segment à l’aide des paramètres « equals » et « not equals ». Vous pouvez également définir des filtres de groupe complexes à l’aide d’opérateurs *logiques AND* *et OR.*

| Syntaxe | Exemple |
|:---------|:----------|
| `New-OrganizationSegment -Name "LocalFTE" -UserGroupFilter "Location -eq 'Local'" -and "Position -ne 'Temporary'"` | Dans cet exemple, nous avons défini un segment appelé *LocalFTE* qui inclut les personnes qui se trouvent localement et dont les postes ne sont pas répertoriés comme *temporaires*. |
| `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "MemberOf -eq 'group1@contoso.com'' -and MemberOf -ne 'group3@contoso.com'"`| Dans cet exemple, nous avons défini un segment appelé *Segment1* qui inclut les personnes qui sont membres de group1@contoso.com et non de membres de group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment2" -UserGroupFilter "MemberOf -eq 'group2@contoso.com' -or MemberOf -ne 'group3@contoso.com'"` | Dans cet exemple, nous avons défini un segment appelé *Segment2* qui inclut les personnes qui sont membres de group2@contoso.com et non de membres de group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment1and2" -UserGroupFilter "(MemberOf -eq 'group1@contoso.com' -or MemberOf -eq 'group2@contoso.com') -and MemberOf -ne 'group3@contoso.com'"`| Dans cet exemple, nous avons défini un segment appelé *Segment1and2* qui inclut les membres de group1@contoso.com et group2@contoso.com et non les membres de group3@contoso.com. |

> [!TIP]
> Si possible, utilisez des définitions de segment qui incluent « -eq » ou « -ne ». Essayez de ne pas définir de définitions de segment complexes.

## <a name="part-2-define-information-barrier-policies"></a>Partie 2 : définir des stratégies de obstacle aux informations

Déterminez si vous devez empêcher les communications entre certains segments ou limiter les communications à certains segments. Dans l’idéal, vous utiliserez le nombre minimal de stratégies pour vous assurer que votre organisation est conforme aux exigences légales et industrielles.

Avec votre liste de segments d’utilisateurs et les stratégies d’obstacle à l’information que vous souhaitez définir, sélectionnez un scénario, puis suivez les étapes.

- [Scénario 1 : bloquer les communications entre les segments](#scenario-1-block-communications-between-segments)
- [Scénario 2 : Autoriser un segment à communiquer avec un seul autre segment](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> **Assurez-vous que lorsque vous définissez des stratégies, vous n’affectez** pas plus d’une stratégie à un segment. Par exemple, si vous définissez une stratégie pour un segment appelé *Ventes,* ne définissez pas de stratégie supplémentaire pour *sales*.<p> En outre, lorsque vous définissez des stratégies d’obstacle à l’information, veillez à définir ces stratégies sur l’état inactif jusqu’à ce que vous soyez prêt à les appliquer. La définition (ou la modification) des stratégies n’affecte pas les utilisateurs tant que ces stratégies ne sont pas définies sur l’état actif, puis appliquées.

(Voir [l’exemple : les stratégies de obstacle à l’information de Contoso](#contosos-information-barrier-policies) dans cet article.)

### <a name="scenario-1-block-communications-between-segments"></a>Scénario 1 : bloquer les communications entre les segments

Lorsque vous souhaitez empêcher les segments de communiquer les uns avec les autres, vous définissez deux stratégies : une pour chaque direction. Chaque stratégie bloque la communication à sens unique.

Par exemple, supposons que vous vouliez bloquer les communications entre le segment A et le segment B. Dans ce cas, vous définissez une stratégie qui empêche le segment A de communiquer avec le segment B, puis vous définissez une deuxième stratégie pour empêcher le segment B de communiquer avec le segment A.

1. Pour définir votre première stratégie de blocage, utilisez la cmdlet **New-InformationBarrierPolicy** avec le **paramètre SegmentsBlocked.**

    | Syntaxe | Exemple |
    |:--------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"` | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> Dans cet exemple, nous avons défini une stratégie appelée *Sales-Research* pour un segment appelé *Ventes*. Lorsqu’elle est active et appliquée, cette stratégie empêche les utilisateurs des ventes de communiquer avec des personnes dans un segment appelé *Recherche.*  |

2. Pour définir votre deuxième segment de blocage, utilisez de nouveau la cmdlet **New-InformationBarrierPolicy** avec le paramètre **SegmentsBlocked,** cette fois avec les segments inversés.

    | Exemple | Remarque |
    |:----------|:-------|
    |`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` | Dans cet exemple, nous avons défini une stratégie appelée *Research-Sales* pour empêcher *la recherche* de communiquer avec *sales*. |

3. Procédez à l’une des actions suivantes :

   - (Si nécessaire) [Définir une stratégie pour autoriser un segment à communiquer uniquement avec un autre segment](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment) 
   - (Une fois toutes vos stratégies définies) [Appliquer des stratégies de obstacle à l’information](#part-3-apply-information-barrier-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>Scénario 2 : Autoriser un segment à communiquer avec un seul autre segment

1. Pour permettre à un segment de communiquer avec un seul autre segment, utilisez la cmdlet **New-InformationBarrierPolicy** avec le paramètre **SegmentsAllowed.**

    | Syntaxe | Exemple |
    |:----------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"` | `New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive` <p> Dans cet exemple, nous avons défini une stratégie appelée *Manufacturing-HR* pour un segment appelé *Manufacturing*. Lorsqu’elle est active et appliquée, cette stratégie permet aux personnes de fabrication de communiquer uniquement avec des personnes dans un segment appelé *RH*.  (Dans ce cas, *la fabrication ne* peut pas communiquer avec des utilisateurs qui ne font pas partie des ressources *humaines.)* |

    **Si nécessaire, vous pouvez spécifier plusieurs segments avec cette cmdlet, comme illustré dans l’exemple suivant.**

    | Syntaxe | Exemple |
    |:---------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name", "segment3name","segment1name"` | `New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive` <p> Dans cet exemple, nous avons défini une stratégie qui  permet au segment *Recherche* de communiquer uniquement avec les ressources humaines *et la fabrication.* |

    Répétez cette étape pour chaque stratégie que vous souhaitez définir pour permettre à des segments spécifiques de communiquer uniquement avec certains autres segments spécifiques.

2. Procédez à l’une des actions suivantes :

   - (Si nécessaire) [Définir une stratégie pour bloquer les communications entre segments](#scenario-1-block-communications-between-segments) 
   - (Une fois toutes vos stratégies définies) [Appliquer des stratégies de obstacle à l’information](#part-3-apply-information-barrier-policies)

## <a name="part-3-apply-information-barrier-policies"></a>Partie 3 : appliquer des stratégies de obstacle aux informations

Les stratégies d’obstacle à l’information ne sont pas en vigueur tant que vous ne les avez pas définies sur l’état actif, puis que vous n’avez pas appliqué les stratégies.

1. Utilisez la cmdlet **Get-InformationBarrierPolicy** pour voir la liste des stratégies qui ont été définies. Notez l’état et l’identité (GUID) de chaque stratégie.

    Syntaxe : `Get-InformationBarrierPolicy`

2. Pour définir une stratégie sur l’état actif, utilisez la cmdlet **Set-InformationBarrierPolicy** avec un paramètre **Identity** et le paramètre **State** sur **Active**. 

    | Syntaxe | Exemple |
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Active` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p> Dans cet exemple, nous avons mis en place une stratégie d’obstacle aux informations dont le GUID *43c37853-ea10-4b90-a23d-ab8c93772471* est actif. |

    Répétez cette étape selon le cas pour chaque stratégie.

3. Lorsque vous avez terminé de définir vos stratégies d’obstacle aux informations sur l’état actif, utilisez la cmdlet **Start-InformationBarrierPoliciesApplication** dans le Centre de sécurité & conformité.

    Syntaxe : `Start-InformationBarrierPoliciesApplication`

    Après l’avoir exécuté, laissez 30 minutes au système pour commencer `Start-InformationBarrierPoliciesApplication` à appliquer les stratégies. Le système applique les stratégies utilisateur par utilisateur. Le système traite environ 5 000 comptes d’utilisateurs par heure.

## <a name="view-status-of-user-accounts-segments-policies-or-policy-application"></a>Afficher l’état des comptes d’utilisateur, segments, stratégies ou application de stratégie

Avec PowerShell, vous pouvez afficher l’état des comptes d’utilisateurs, des segments, des stratégies et de l’application de stratégie, comme répertorié dans le tableau suivant.

| Pour afficher ces informations | Prendre cette action |
|:---------------|:----------|
| Comptes d’utilisateur | Utilisez la cmdlet **Get-InformationBarrierRecipientStatus** avec les paramètres Identity. <p> Syntaxe : `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Vous pouvez utiliser n’importe quelle valeur qui identifie chaque utilisateur de manière unique, telle que le nom, l’alias, le nom unique, le nom de domaine canonique, l’adresse e-mail ou le GUID. <p> Exemple : `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> Dans cet exemple, nous faisons référence à deux comptes d’utilisateur dans Office 365 : *meganb* pour *Megan* et *alexw* pour *Alex*. <p> (Vous pouvez également utiliser cette cmdlet pour un seul utilisateur : `Get-InformationBarrierRecipientStatus -Identity <value>` ) <p> Cette cmdlet renvoie des informations sur les utilisateurs, telles que les valeurs d’attribut et les stratégies de obstacle aux informations appliquées.|
| Segments | Utilisez la cmdlet **Get-OrganizationSegment.**<p> Syntaxe : `Get-OrganizationSegment` <p> Cette cmdlet affiche la liste de tous les segments définis pour votre organisation. |
| Stratégies de obstacle à l’information | Utilisez la cmdlet **Get-InformationBarrierPolicy.** <p> Syntaxe : `Get-InformationBarrierPolicy` <p> Cette cmdlet affiche la liste des stratégies d’obstacle aux informations qui ont été définies et leur état. |
| Application de stratégie de obstacle à l’information la plus récente | Utilisez la cmdlet **Get-InformationBarrierPoliciesApplicationStatus.** <p> Syntaxe : `Get-InformationBarrierPoliciesApplicationStatus`<p> Cette cmdlet affiche des informations sur la fin, l’échec ou l’avancement de l’application de stratégie. |
| Toutes les applications de stratégie de obstacle à l’information|Utiliser `Get-InformationBarrierPoliciesApplicationStatus -All`<p> Cette cmdlet affiche des informations sur la fin, l’échec ou l’avancement de l’application de stratégie.|

<!-- IN the " The most recent information barrier policy application, add link to troubleshooting topic -->

## <a name="what-if-i-need-to-remove-or-change-policies"></a>Que se passe-t-il si j’ai besoin de supprimer ou de modifier des stratégies ?

Des ressources sont disponibles pour vous aider à gérer vos stratégies de obstacle aux informations.

- En cas de problème avec les obstacles à l’information, voir [Résolution des problèmes d’obstacles aux informations.](information-barriers-troubleshooting.md)
- Pour arrêter l’application des stratégies, voir [Arrêter une application de stratégie.](information-barriers-edit-segments-policies.md#stop-a-policy-application)
- Pour supprimer une stratégie de obstacle à l’information, voir [Supprimer une stratégie.](information-barriers-edit-segments-policies.md#remove-a-policy)
- Pour apporter des modifications à des segments ou des stratégies, voir [Modifier (ou supprimer) les stratégies d’obstacle à l’information.](information-barriers-edit-segments-policies.md)

## <a name="example-contosos-departments-segments-and-policies"></a>Exemple : services, segments et stratégies de Contoso

Voici un exemple qui montre comment une organisation peut aborder la définition des segments et des stratégies.

### <a name="contosos-departments-and-plan"></a>Départements et plan de Contoso

Contoso compte cinq départements : Ressources Humaines, Ventes, Marketing, Recherche et Production. Afin de rester conformes aux réglementations du secteur, les membres de certains services ne sont pas censés communiquer avec d’autres services, comme le prévoit le tableau suivant :

| Segment | Peut communiquer avec | Ne peut pas communiquer avec |
|:----------|:--------------|:-----------------|
| RH | Tout le monde | (aucune restriction) |
| Ventes | RH, Marketing, Fabrication | Recherche |
| Marketing | Tout le monde | (aucune restriction) |
| Recherche | RH, Marketing, Fabrication | Ventes |
| Fabrication | RH, Marketing | Toute personne autre que rh ou marketing |

Pour cette structure, le plan de Contoso inclut trois stratégies d’obstacle à l’information :

1. Une stratégie conçue pour empêcher les ventes de communiquer avec la recherche (et une autre stratégie pour empêcher la recherche de communiquer avec les ventes).

2. Stratégie conçue pour permettre à la fabrication de communiquer uniquement avec les ressources humaines et le marketing.

Pour ce scénario, il n’est pas nécessaire de définir des stratégies pour les ressources humaines ou le marketing.

### <a name="contosos-defined-segments"></a>Segments définis par Contoso

Contoso utilisera l’attribut Department dans Azure Active Directory pour définir des segments, comme suit :

| Service | Définition de segment |
|:-------------|:---------------------|
| RH | `New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` |
| Ventes | `New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"` |
| Marketing | `New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"` |
| Recherche | `New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"` |
| Production | `New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"` |

Une fois les segments définis, Contoso procède à la définition des stratégies.

### <a name="contosos-information-barrier-policies"></a>Stratégies de cloisonnement de l’information de Contoso

Contoso définit trois stratégies, comme décrit dans le tableau suivant :

| Stratégie | Définition de la stratégie |
|:---------|:--------------------|
| **Stratégie 1 : empêcher le département des Ventes de communiquer avec la Recherche** | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> Dans cet exemple, la stratégie de cloisonnement de l’information est nommée *Sales-Research*. Lorsque cette stratégie est active et appliquée, elle empêche les utilisateurs du segment Ventes de communiquer avec les utilisateurs du segment Recherche. Cette stratégie est une stratégie à sens seul . Cela n’empêche pas la recherche de communiquer avec les ventes. Pour cela, la stratégie 2 est nécessaire. |
| **Stratégie 2 : empêcher la Recherche de communiquer avec le département des Ventes** | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> Dans cet exemple, la stratégie de cloisonnement de l’information est nommée *Research-Sales*. Lorsque cette stratégie est active et appliquée, elle empêche les utilisateurs du segment Recherche de communiquer avec les utilisateurs du segment Ventes. |
| **Stratégie 3 : autoriser la fabrication à communiquer uniquement avec les ressources humaines et le marketing** | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p> Dans ce cas, la stratégie de cloisonnement de l’information est nommée *Manufacturing-HRMarketing*. Lorsque cette stratégie est active et appliquée, la Production ne peut communiquer qu’avec les Ressources Humaines et le Marketing. Les ressources humaines et le marketing ne sont pas limités à communiquer avec d’autres segments. |

Lorsque des segments et des stratégies sont définis, Contoso applique les stratégies en exécutant l’cmdlet **Start-InformationBarrierPoliciesApplication.**

Lorsque l’cmdlet se termine, Contoso est conforme aux exigences légales et industrielles.

## <a name="resources"></a>Ressources

- [Obtenir une vue d’ensemble des obstacles aux informations](information-barriers.md)
- [En savoir plus sur les obstacles aux informations dans Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [En savoir plus sur les obstacles aux informations dans SharePoint Online](/sharepoint/information-barriers)
- [En savoir plus sur les obstacles aux informations dans OneDrive](/onedrive/information-barriers)