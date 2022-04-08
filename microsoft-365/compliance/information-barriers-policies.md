---
title: Démarrer avec le cloisonnement de l’information
description: Découvrez comment prendre en main les obstacles à l’information.
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
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: fb6de09c0c020631f42d8f2f09cb236affb94417
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2022
ms.locfileid: "64713534"
---
# <a name="get-started-with-information-barriers"></a>Démarrer avec le cloisonnement de l’information

Avec les barrières à l’information, vous pouvez définir des stratégies conçues pour empêcher certains segments d’utilisateurs de communiquer entre eux ou autoriser des segments spécifiques à communiquer uniquement avec certains autres segments. Les stratégies d’obstacle à l’information peuvent aider votre organisation à maintenir la conformité aux normes et réglementations pertinentes du secteur et à éviter les conflits d’intérêts potentiels. Pour plus d’informations, consultez [En savoir plus sur les obstacles à l’information](information-barriers.md).

Cet article explique comment configurer des stratégies d’obstacle à l’information. Plusieurs étapes sont impliquées. Veillez donc à passer en revue l’ensemble du processus avant de commencer à configurer des stratégies d’obstacle à l’information.

> [!TIP]
> Cet article inclut un [exemple de scénario](#example-scenario-contosos-departments-segments-and-policies) pour vous aider à planifier et à définir vos stratégies d’obstacle à l’information.

## <a name="concepts"></a>Concepts

Lorsque vous définissez des stratégies pour les obstacles à l’information, vous travaillez avec les attributs de compte d’utilisateur, les segments, les stratégies « block » et/ou « allow » et l’application de stratégie.

- Les attributs du compte utilisateur sont définis dans Azure Active Directory (ou Exchange Online). Ces attributs peuvent inclure le service, la fonction, l’emplacement, le nom d’équipe et d’autres détails du profil du poste.
- Les segments sont des ensembles d’utilisateurs définis dans le Centre de conformité Microsoft 365 à l’aide d’un **attribut de compte d’utilisateur** sélectionné. (consultez la [liste des attributs pris en charge](information-barriers-attributes.md)).
- Les stratégies de cloisonnement de l’information déterminent les limites ou les restrictions de communication. Lorsque vous définissez des stratégies de cloisonnement de l’information, vous avez le choix entre deux types de stratégie :
  - *Bloquer* les stratégies pour empêcher un segment de communiquer avec un autre.
  - *Autoriser* les stratégies de n’autoriser qu’un segment à communiquer avec certains autres segments uniquement.
- L’application de la stratégie est effectuée une fois toutes les stratégies de cloisonnement de l’information sont définies et que vous êtes prêt à les appliquer au sein de votre organisation.

## <a name="configuration-at-a-glance"></a>Configuration en un clin d’œil

| **Étapes** | **Ce qui est impliqué** |
|:------|:----------------|
| **Étape 1** : [Vérifier que les conditions préalables sont remplies](#step-1-make-sure-prerequisites-are-met) | - Vérifiez que vous disposez des [licences et autorisations requises](information-barriers.md#required-licenses-and-permissions)<br/>vérifier que votre annuaire inclut des données pour la segmentation des utilisateurs.<br/>- Activer [la recherche par nom pour Microsoft Teams](/microsoftteams/teams-scoped-directory-search)<br/>vous assurer que l’enregistrement d’audit est activé.<br/>vous assurer qu’aucune stratégie de carnet d’adresses Exchange n’est mise en place.<br/>- Utiliser PowerShell (des exemples sont fournis)<br/>- Fournir le consentement de l’administrateur pour Microsoft Teams (les étapes sont incluses) |
| **Étape 2** : [Segmenter les utilisateurs de votre organisation](#step-2-segment-users-in-your-organization) | - Déterminer les stratégies nécessaires<br/>- Créer une liste de segments à définir<br/>- Identifier les attributs à utiliser<br/>- Définir des segments en termes de filtres de stratégie |
| **Étape 3** : [Définir des stratégies d’obstacle à l’information](#step-3-define-information-barrier-policies) | - Définir vos stratégies (ne pas encore appliquer)<br/>- Choisir parmi deux types (bloquer ou autoriser) |
| **Étape 4** : [Appliquer des stratégies d’obstacle à l’information](#step-4-apply-information-barrier-policies) | - Définir des stratégies sur l’état actif<br/>- Exécuter l’application de stratégie<br/>- Afficher l’état de la stratégie |
| **Étape 5** : [Configuration des obstacles à l’information sur SharePoint et OneDrive (facultatif)](#step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive) | - Configurer des obstacles à l’information pour les SharePoint et les OneDrive |
| **Étape 6** : [Modes de barrières d’information (facultatif)](#step-6-information-barriers-modes) | - Mettre à jour les modes de barrière des informations le cas échéant |

## <a name="step-1-make-sure-prerequisites-are-met"></a>Étape 1 : Vérifier que les conditions préalables sont remplies

En plus [des licences et autorisations requises](information-barriers.md#required-licenses-and-permissions), assurez-vous que les exigences suivantes sont remplies avant de configurer les obstacles à l’information :

- **Données d’annuaire** : assurez-vous que la structure de votre organisation est reflétée dans les données d’annuaire. Pour effectuer cette action, assurez-vous que les attributs de compte d’utilisateur, tels que l’appartenance au groupe, le nom du service, etc., sont correctement renseignés dans Azure Active Directory (ou Exchange Online). Pour en savoir plus, consultez les ressources suivantes :
  - [Attributs pour les stratégies d’obstacle aux informations](information-barriers-attributes.md)
  - [Ajouter ou mettre à jour les informations de profil d’un utilisateur à l’aide de Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [Configurer les propriétés des comptes d'utilisateur avec Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)

- **Recherche d’annuaires délimités** : avant de définir la première stratégie d’obstacle à l’information de votre organisation, vous devez [activer la recherche d’annuaire délimitée dans Microsoft Teams](/MicrosoftTeams/teams-scoped-directory-search). Attendez au moins 24 heures après l’activation de la recherche d’annuaire délimité avant de configurer ou de définir des stratégies d’obstacle aux informations.

- **Exchange Online licences : les** stratégies d’obstacles à l’information fonctionnent uniquement si une licence Exchange Online a été attribuée aux utilisateurs cibles.

- **Vérifiez que la journalisation d’audit est activée** : pour rechercher l’état d’une application de stratégie, la journalisation d’audit doit être activée. L'audit est activé par défaut pour les organisations Microsoft 365. Certaines organisations peuvent avoir désactivé l'audit pour des raisons spécifiques. Si l'audit est désactivé pour votre organisation, c'est peut-être parce qu'un autre administrateur l'a désactivé. Nous vous recommandons de confirmer que vous pouvez réactiver l'audit lorsque vous terminez cette étape. Pour plus d’informations, voir [Activer ou désactiver la recherche dans le journal d’audit](turn-audit-log-search-on-or-off.md).

- **Aucune stratégie de carnet d’adresses** : avant de définir et d’appliquer des stratégies de barrière à l’information, assurez-vous qu’aucune stratégie de carnet d’adresses Exchange n’est en place. Les obstacles aux informations sont basés sur les stratégies de carnet d’adresses, mais les deux types de stratégies ne sont pas compatibles. Si vous avez de telles stratégies, veillez d’abord à [supprimer vos stratégies de carnet d’adresses](/exchange/address-books/address-book-policies/remove-an-address-book-policy) . Une fois que les stratégies de barrière de l’information sont activées et que vous avez activé le carnet d’adresses hiérarchique, tous les utilisateurs **_qui ne sont pas inclus_** dans un segment de barrière de l’information voient le [carnet d’adresses hiérarchique](/exchange/address-books/hierarchical-address-books/hierarchical-address-books) dans Exchange en ligne.

- **Gérer à l’aide de PowerShell** : Actuellement, les stratégies de barrière d’information sont définies et gérées dans le Centre de sécurité & conformité PowerShell. Bien que plusieurs exemples soient fournis dans cet article, vous devez être familiarisé avec les applets de commande et les paramètres PowerShell. Vous aurez également besoin du module PowerShell Azure Active Directory.
  - [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell)
  - [Installer Azure Active Directory PowerShell pour Graph](/powershell/azure/active-directory/install-adv2)

- **Consentement de l’administrateur pour les obstacles à l’information dans Microsoft Teams** : lorsque vos stratégies IB sont en place, elles peuvent supprimer les utilisateurs non conformes à l’IB des groupes (c’est-à-dire les canaux Teams, qui sont basés sur des groupes). Cette configuration permet de garantir que votre organisation reste conforme aux stratégies et réglementations. Utilisez la procédure suivante pour permettre aux stratégies de barrière d’information de fonctionner comme prévu dans Microsoft Teams.

   1. Prérequis : [installez Azure Active Directory PowerShell pour Graph](/powershell/azure/active-directory/install-adv2).

   1. Exécutez les applets de commande Windows PowerShell suivantes dans cet ordre:

      ```powershell
      Connect-AzureAD -Tenant "<yourtenantdomain.com>"  //for example: Connect-AzureAD -Tenant "Contoso.onmicrosoft.com"
      $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
      $sp=Get-AzureADServicePrincipal -Filter "appid eq '$($appid)'"
      if ($sp -eq $null) { New-AzureADServicePrincipal -AppId $appId }
      Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
      ```

   1. Lorsque vous y invitez, connectez-vous à l’aide de votre compte scolaire ou Office 365.

   1. Dans la boîte de dialogue **Autorisations demandées** , passez en revue les informations, puis choisissez **Accepter**. Les autorisations demandées par l’application sont fournies ci-dessous.

      > [!div class="mx-imgBorder"]
      > ![Image.](https://user-images.githubusercontent.com/8932063/107690955-b1772300-6c5f-11eb-9527-4235de860b27.png)

Lorsque toutes les conditions préalables sont remplies, passez à l’étape suivante.

> [!TIP]
> Pour vous aider à préparer votre plan, un exemple de scénario est inclus dans cet article. [Consultez les services, segments et stratégies de Contoso](#example-scenario-contosos-departments-segments-and-policies).

## <a name="step-2-segment-users-in-your-organization"></a>Étape 2 : Segmenter les utilisateurs de votre organisation

Au cours de cette étape, vous déterminez les stratégies d’obstacle à l’information nécessaires, créez une liste de segments à définir, puis définissez vos segments.

### <a name="determine-what-policies-are-needed"></a>Déterminer les stratégies nécessaires

Compte tenu des réglementations légales et sectorielles, qui sont les groupes au sein de votre organisation qui auront besoin de stratégies d’obstacle à l’information ? Dressez une liste. Y a-t-il des groupes qui devraient être empêchés de communiquer avec un autre groupe ? Y a-t-il des groupes qui doivent être autorisés à communiquer uniquement avec un ou deux autres groupes ? Considérez les stratégies dont vous avez besoin comme appartenant à l’un des deux groupes :

- Les stratégies « Bloquer » empêchent un groupe de communiquer avec un autre groupe.
- Les stratégies « Autoriser » permettent à un groupe de communiquer uniquement avec certains autres groupes spécifiques.

Lorsque vous avez votre liste initiale de groupes et de stratégies, procédez à l’identification des segments dont vous aurez besoin.

### <a name="identify-segments"></a>Identifier les segments

En plus de votre liste initiale de stratégies, dressez une liste de segments pour votre organisation. Les utilisateurs qui seront inclus dans les stratégies d’obstacle à l’information doivent appartenir à un segment. Planifier soigneusement vos segments en tant qu’utilisateur ne peut se trouver qu’en un seul segment. Chaque segment ne peut avoir qu’une seule stratégie d’obstacle à l’information appliquée.

> [!IMPORTANT]
> Un utilisateur ne peut se trouver que dans un seul segment.

Déterminez les attributs dans les données d’annuaire de votre organisation que vous utiliserez pour définir des segments. Vous pouvez utiliser *Department*, *MemberOf* ou l’un des attributs pris en charge. Assurez-vous que vous avez des valeurs dans l’attribut que vous sélectionnez pour les utilisateurs. [Consultez la liste des attributs pris en charge pour les obstacles à l’information](information-barriers-attributes.md).

> [!IMPORTANT]
> **Avant de passer à la section suivante, assurez-vous que vos données d’annuaire ont des valeurs pour les attributs que vous pouvez utiliser pour définir des segments**. Si vos données d’annuaire n’ont pas de valeurs pour les attributs que vous souhaitez utiliser, les comptes d’utilisateur doivent être mis à jour pour inclure ces informations avant de passer aux obstacles à l’information. Pour obtenir de l’aide à ce sujet, consultez les ressources suivantes :<br/>- [Configurer les propriétés du compte d’utilisateur avec Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)<br/>- [Ajouter ou mettre à jour les informations de profil d’un utilisateur à l’aide de Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

### <a name="define-segments-using-powershell"></a>Définir des segments à l’aide de PowerShell

La définition de segments n’affecte pas les utilisateurs ; il définit simplement la phase de définition et d’application des stratégies d’obstacle à l’information.

1. Utilisez [l’applet](information-barriers-attributes.md) **de commande New-OrganizationSegment** avec le paramètre **UserGroupFilter** qui correspond à l’attribut que vous souhaitez utiliser.

    | Syntaxe | Exemple |
    |:---------|:----------|
    | `New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"` |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>Dans cet exemple, un segment appelé *RH* est défini à l’aide des *ressources humaines*, une valeur dans l’attribut *Department* . La partie **-eq** de l’applet de commande fait référence à « equals ». (Vous pouvez également utiliser **-ne** pour signifier « non égal à ». Voir [Utilisation de « equals » et de « not equals » dans les définitions de segment](#using-equals-and-not-equals-in-segment-definitions).) |

    Une fois que vous avez exécuté chaque applet de commande, vous devez voir une liste de détails sur le nouveau segment. Les détails incluent le type du segment, qui l’a créé ou modifié pour la dernière fois, et ainsi de suite. 

2. Répétez ce processus pour chaque segment que vous souhaitez définir.

    > [!IMPORTANT]
    > **Assurez-vous que vos segments ne se chevauchent pas**. Chaque utilisateur qui sera affecté par les barrières à l’information doit appartenir à un seul segment (et un seul). Aucun utilisateur ne doit appartenir à deux segments ou plus. (Voir [l’exemple : segments définis par Contoso](#contosos-defined-segments) dans cet article.)

Une fois que vous avez défini vos segments, passez à définir des stratégies [d’obstacle à l’information](#step-3-define-information-barrier-policies).

### <a name="using-equals-and-not-equals-in-segment-definitions"></a>Utilisation de « equals » et de « not equals » dans les définitions de segment

Dans l’exemple suivant, nous définissons un segment de sorte que « Department equals HR ». 

| Exemple | Remarque |
|:----------|:-------|
|`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` | Notez que dans cet exemple, la définition de segment inclut un paramètre « equals » nommé **-eq**. |

Vous pouvez également définir des segments à l’aide d’un paramètre « non égal à », désigné comme **-ne**, comme indiqué dans le tableau suivant :

| Syntaxe | Exemple |
|:---------|:----------|
| `New-OrganizationSegment -Name "NotSales" -UserGroupFilter "Department -ne 'Sales'"` | Dans cet exemple, nous avons défini un segment appelé *NotSales* qui inclut toutes les personnes qui ne sont pas dans *Sales*. La partie **-ne** de l’applet de commande fait référence à « non égal ». |

En plus de définir des segments en utilisant « equals » ou « not equals », vous pouvez définir un segment à l’aide de paramètres « equals » et « not equals ». Vous pouvez également définir des filtres de groupe complexes à l’aide d’opérateurs *AND* et *OR* logiques.

| Syntaxe | Exemple |
|:---------|:----------|
| `New-OrganizationSegment -Name "LocalFTE" -UserGroupFilter "Location -eq 'Local'" -and "Position -ne 'Temporary'"` | Dans cet exemple, nous avons défini un segment appelé *LocalFTE* qui inclut les personnes qui se trouvent localement et dont les postes ne sont pas répertoriés comme *temporaires*. |
| `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "MemberOf -eq 'group1@contoso.com'' -and MemberOf -ne 'group3@contoso.com'"`| Dans cet exemple, nous avons défini un segment appelé *Segment1* qui inclut des personnes qui sont membres de group1@contoso.com et non membres de group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment2" -UserGroupFilter "MemberOf -eq 'group2@contoso.com' -or MemberOf -ne 'group3@contoso.com'"` | Dans cet exemple, nous avons défini un segment appelé *Segment2* qui inclut des personnes qui sont membres de group2@contoso.com et non membres de group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment1and2" -UserGroupFilter "(MemberOf -eq 'group1@contoso.com' -or MemberOf -eq 'group2@contoso.com') -and MemberOf -ne 'group3@contoso.com'"`| Dans cet exemple, nous avons défini un segment appelé *Segment1and2* qui inclut des membres de group1@contoso.com et de group2@contoso.com et non des membres de group3@contoso.com. |

> [!TIP]
> Si possible, utilisez des définitions de segment qui incluent « -eq » ou « -ne ». Essayez de ne pas définir de définitions de segment complexes.

## <a name="step-3-define-information-barrier-policies"></a>Étape 3 : Définir des stratégies d’obstacle à l’information

Déterminez si vous devez empêcher les communications entre certains segments ou limiter les communications à certains segments. Dans l’idéal, vous utiliserez le nombre minimal de stratégies pour vous assurer que votre organisation est conforme aux exigences légales et sectorielles.

Avec votre liste de segments d’utilisateurs et les stratégies de barrière à l’information que vous souhaitez définir, sélectionnez un scénario, puis suivez les étapes.

- [Scénario 1 : Bloquer les communications entre les segments](#scenario-1-block-communications-between-segments)
- [Scénario 2 : Autoriser un segment à communiquer avec un seul autre segment](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> **Assurez-vous qu’au fur et à mesure que vous définissez des stratégies, vous n’affectez pas plusieurs stratégies à un segment**. Par exemple, si vous définissez une stratégie pour un segment appelé *Sales*, ne définissez pas de stratégie supplémentaire pour *Sales*.<p> En outre, lorsque vous définissez des stratégies d’obstacle à l’information, veillez à définir ces stratégies sur l’état inactif jusqu’à ce que vous soyez prêt à les appliquer. La définition (ou la modification) de stratégies n’affecte pas les utilisateurs tant que ces stratégies ne sont pas définies sur l’état actif, puis appliquées.

(Voir [l’exemple : Stratégies de cloisonnement des informations de Contoso](#contosos-information-barrier-policies) dans cet article.)

### <a name="scenario-1-block-communications-between-segments"></a>Scénario 1 : bloquer les communications entre les segments

Lorsque vous souhaitez empêcher les segments de communiquer entre eux, vous définissez deux stratégies : une pour chaque direction. Chaque stratégie bloque la communication à sens unique.

Par exemple, supposons que vous souhaitez bloquer les communications entre le segment A et le segment B. Dans ce cas, vous définissez une stratégie empêchant le segment A de communiquer avec le segment B, puis définissez une deuxième stratégie pour empêcher le segment B de communiquer avec le segment A.

1. Pour définir votre première stratégie de blocage, utilisez l’applet de commande **New-InformationBarrierPolicy** avec le paramètre **SegmentsBlocked** .

    | Syntaxe | Exemple |
    |:--------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"` | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> Dans cet exemple, nous avons défini une stratégie appelée *Sales-Research* pour un segment appelé *Sales*. Lorsqu’elle est active et appliquée, cette stratégie empêche les personnes de *Sales* de communiquer avec des personnes dans un segment appelé *Recherche*. |

2. Pour définir votre deuxième segment de blocage, utilisez à nouveau l’applet de commande **New-InformationBarrierPolicy** avec le paramètre **SegmentsBlocked** , cette fois avec les segments inversés.

    | Exemple | Remarque |
    |:----------|:-------|
    |`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` | Dans cet exemple, nous avons défini une stratégie appelée *Research-Sales* pour empêcher *Research* de communiquer avec *Sales*. |

3. Passez à l’une des actions suivantes :

   - (Si nécessaire) [Définir une stratégie pour permettre à un segment de communiquer uniquement avec un autre segment](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment) 
   - (Une fois toutes vos stratégies définies) [Appliquer des stratégies d’obstacle à l’information](#step-4-apply-information-barrier-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>Scénario 2 : Autoriser un segment à communiquer avec un seul autre segment

1. Pour permettre à un segment de communiquer avec un seul autre segment, utilisez l’applet de commande **New-InformationBarrierPolicy** avec le paramètre **SegmentsAllowed** .

    | Syntaxe | Exemple |
    |:----------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"` | `New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive` <p> Dans cet exemple, nous avons défini une stratégie appelée *Manufacturing-HR* pour un segment appelé *Manufacturing*. Lorsqu’elle est active et appliquée, cette stratégie permet aux personnes du secteur *de la fabrication* de communiquer uniquement avec les personnes d’un segment appelé *RH*. (Dans ce cas, *la fabrication* ne peut pas communiquer avec les utilisateurs qui ne font pas partie des *RH*.) |

    **Si nécessaire, vous pouvez spécifier plusieurs segments avec cette applet de commande, comme illustré dans l’exemple suivant.**

    | Syntaxe | Exemple |
    |:---------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name", "segment3name","segment1name"` | `New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive` <p> Dans cet exemple, nous avons défini une stratégie qui permet au segment *Recherche* de communiquer uniquement avec *les ressources humaines* et *la fabrication*. |

    Répétez cette étape pour chaque stratégie que vous souhaitez définir pour permettre à des segments spécifiques de communiquer uniquement avec certains autres segments spécifiques.

2. Passez à l’une des actions suivantes :

   - (Si nécessaire) [Définir une stratégie pour bloquer les communications entre les segments](#scenario-1-block-communications-between-segments) 
   - (Une fois toutes vos stratégies définies) [Appliquer des stratégies d’obstacle à l’information](#step-4-apply-information-barrier-policies)

## <a name="step-4-apply-information-barrier-policies"></a>Étape 4 : Appliquer des stratégies d’obstacle à l’information

Les politiques de barrière d'information ne sont pas en vigueur tant que vous ne les faites pas passer au statut actif, puis que vous les appliquez.

1. Utilisez l’applet de commande **Get-InformationBarrierPolicy** pour afficher la liste des stratégies qui ont été définies. Notez l’état et l’identité (GUID) de chaque stratégie.

    Syntaxe: `Get-InformationBarrierPolicy`

2. Pour définir une stratégie sur l’état actif, utilisez l’applet de commande **Set-InformationBarrierPolicy** avec un paramètre **Identity** et le paramètre **State** défini sur **Active**. 

    | Syntaxe | Exemple |
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Active` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p> Dans cet exemple, nous définissons une stratégie de barrière d’information qui a le GUID *43c37853-ea10-4b90-a23d-ab8c93772471* sur l’état actif. |

    Répétez cette étape en fonction de chaque stratégie.

3. Une fois que vous avez terminé de définir vos stratégies de barrière des informations sur l’état actif, utilisez l’applet de commande **Start-InformationBarrierPoliciesApplication** dans le Centre de sécurité & conformité.

    Syntaxe: `Start-InformationBarrierPoliciesApplication`

    Après avoir exécuté `Start-InformationBarrierPoliciesApplication`, attendez 30 minutes pour que le système commence à appliquer les politiques. Le système applique les stratégies utilisateur par utilisateur. Le système traite environ 5 000 comptes d’utilisateurs par heure.

### <a name="view-status-of-user-accounts-segments-policies-or-policy-application"></a>Afficher l’état des comptes d’utilisateur, des segments, des stratégies ou de l’application de stratégie

Avec PowerShell, vous pouvez afficher l’état des comptes d’utilisateur, des segments, des stratégies et de l’application de stratégie, comme indiqué dans le tableau suivant.

| Pour afficher ces informations | Effectuer cette action |
|:---------------|:----------|
| Comptes d’utilisateur | Utilisez l’applet de commande **Get-InformationBarrierRecipientStatus** avec les paramètres d’identité. <p> Syntaxe: `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Vous pouvez utiliser n’importe quelle valeur qui identifie de manière unique chaque utilisateur, telle que le nom, l’alias, le nom unique, le nom de domaine canonique, l’adresse e-mail ou le GUID. <p> Exemple : `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> Dans cet exemple, nous faisons référence à deux comptes d’utilisateur dans Office 365 : *meganb* pour *Megan* et *alexw* pour *Alex*. <p> (Vous pouvez également utiliser cette applet de commande pour un seul utilisateur : `Get-InformationBarrierRecipientStatus -Identity <value>`) <p> Cette applet de commande retourne des informations sur les utilisateurs, telles que les valeurs d’attribut et les stratégies de barrière d’information appliquées.|
| Segments | Utilisez **l’applet de commande Get-OrganizationSegment** .<p> Syntaxe: `Get-OrganizationSegment` <p> Cette applet de commande affiche la liste de tous les segments définis pour votre organisation. |
| Stratégies d’obstacle aux informations | Utilisez l’applet **de commande Get-InformationBarrierPolicy** . <p> Syntaxe: `Get-InformationBarrierPolicy` <p> Cette applet de commande affiche une liste des stratégies d’obstacle à l’information qui ont été définies, ainsi que leur état. |
| L’application de stratégie d’obstacle à l’information la plus récente | Utilisez l’applet de commande **Get-InformationBarrierPoliciesApplicationStatus** . <p> Syntaxe: `Get-InformationBarrierPoliciesApplicationStatus`<p> Cette applet de commande affiche des informations indiquant si l’application de stratégie est terminée, a échoué ou est en cours. |
| Toutes les applications de stratégie d’obstacle à l’information|Utiliser `Get-InformationBarrierPoliciesApplicationStatus -All`<p> Cette applet de commande affiche des informations indiquant si l’application de stratégie est terminée, a échoué ou est en cours.|

<!-- IN the " The most recent information barrier policy application, add link to troubleshooting topic -->

### <a name="what-if-i-need-to-remove-or-change-policies"></a>Que se passe-t-il si je dois supprimer ou modifier des stratégies ?

Des ressources sont disponibles pour vous aider à gérer vos stratégies d’obstacle à l’information.

- Si un problème se produit avec les obstacles à l’information, consultez [Dépannage des obstacles à l’information](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting).
- Pour empêcher l’application de stratégies, consultez [Arrêter une application de stratégie](information-barriers-edit-segments-policies.md#stop-a-policy-application).
- Pour supprimer une stratégie d’obstacle à l’information, consultez [Supprimer une stratégie](information-barriers-edit-segments-policies.md#remove-a-policy).
- Pour apporter des modifications aux segments ou aux stratégies, consultez [Modifier (ou supprimer) les stratégies de cloisonnement des informations](information-barriers-edit-segments-policies.md).

## <a name="step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive"></a>Étape 5 : Configuration des obstacles à l’information sur les SharePoint et les OneDrive

Si vous configurez des obstacles à l’information pour SharePoint et OneDrive, vous devez activer les obstacles à l’information sur ces services. Vous devez également activer les obstacles à l’information sur ces services si vous configurez des obstacles à l’information pour Microsoft Teams. Lorsqu’une équipe Microsoft Teams est créée, un site SharePoint est automatiquement créé et associé à Microsoft Teams pour l’expérience de fichiers. Les stratégies d’obstacle à l’information ne sont pas honorées sur SharePoint site et les fichiers par défaut.

Pour activer les obstacles à l’information dans SharePoint et OneDrive, suivez les instructions et les étapes décrites dans l’article [Utiliser les obstacles à l’information avec SharePoint](/sharepoint/information-barriers) article.

## <a name="step-6-information-barriers-modes"></a>Étape 6 : Modes de barrières d’information

Les modes peuvent aider à renforcer l’accès, le partage et l’appartenance à une ressource Microsoft 365 en fonction du mode IB de la ressource. Les modes sont pris en charge sur les sites Groupes Microsoft 365, Microsoft Teams, OneDrive et SharePoint et sont automatiquement activés dans votre configuration IB nouvelle ou existante.

Les modes IB suivants sont pris en charge sur Microsoft 365 ressources :

| **Mode** | **Description** | **Exemple** |
|:-----|:------------|:--------|
| **Ouvert** | Aucune stratégie ou segment IB n’est associé à la ressource Microsoft 365. N’importe qui peut être invité à être membre de la ressource. | Un site d’équipe créé pour l’événement de pique-nique pour votre organisation. |
| **Owner Moderated (préversion)** | La stratégie IB de la ressource Microsoft 365 est déterminée à partir de la stratégie IB du propriétaire de la ressource. Les propriétaires de ressources peuvent inviter n’importe quel utilisateur à la ressource en fonction de leurs stratégies IB. Ce mode est utile lorsque votre entreprise souhaite autoriser la collaboration entre les utilisateurs de segment incompatibles qui sont modérés par le propriétaire. Seul le propriétaire de la ressource peut ajouter de nouveaux membres en fonction de sa stratégie IB. | Le vice-président des ressources humaines souhaite collaborer avec les VPs of Sales and Research. Nouveau site SharePoint défini avec le mode IB *Owner Moderated* pour ajouter les utilisateurs des segments Ventes et Recherche au même site. Il incombe au propriétaire de s’assurer que les membres appropriés sont ajoutés à la ressource. |
| **Implicite** | La stratégie ib ou les segments de la ressource Microsoft 365 sont hérités de la stratégie IB des membres de la ressource. Le propriétaire peut ajouter des membres tant qu’ils sont compatibles avec les membres existants de la ressource. Il s’agit du mode IB par défaut pour Microsoft Teams. | L’utilisateur du segment Ventes crée une équipe Microsoft Teams pour collaborer avec d’autres segments compatibles de l’organisation. |
| **Explicit** | La stratégie IB de la ressource Microsoft 365 correspond aux segments associés à la ressource. Le propriétaire de la ressource ou l’administrateur SharePoint peut gérer les segments de la ressource.  | Un site créé uniquement pour permettre aux membres du segment Ventes de collaborer en associant le segment Ventes au site.   |

Pour plus d’informations sur les modes de barrière d’information et la façon dont ils sont configurés entre les services, consultez les articles suivants :

- [Modes d’obstacle à l’information et Microsoft Teams](/microsoftteams/information-barriers-in-teams)
- [Modes d’obstacle à l’information et OneDrive](/onedrive/information-barriers)
- [Modes d’obstacle à l’information et Microsoft Office SharePoint Online](/sharepoint/information-barriers)

## <a name="example-scenario-contosos-departments-segments-and-policies"></a>Exemple de scénario : services, segments et stratégies de Contoso

Pour voir comment une organisation peut aborder la définition de segments et de stratégies, prenez en compte l’exemple de scénario suivant.

### <a name="contosos-departments-and-plan"></a>Départements et plan de Contoso

Contoso compte cinq départements : Ressources Humaines, Ventes, Marketing, Recherche et Production. Pour rester conformes aux réglementations de l’industrie, les membres de certains ministères ne sont pas censés communiquer avec d’autres ministères, comme indiqué dans le tableau suivant :

| Segment | Peut communiquer avec | Ne peut pas communiquer avec |
|:----------|:--------------|:-----------------|
| RH | Tout le monde | (aucune restriction) |
| Ventes | RH, Marketing, Fabrication | Recherche |
| Marketing | Tout le monde | (aucune restriction) |
| Recherche | RH, Marketing, Fabrication | Ventes |
| Production | RH, Marketing | Toute autre personne que les RH ou le marketing |

Pour cette structure, le plan de Contoso inclut trois stratégies d’obstacle à l’information :

1. Une stratégie conçue pour empêcher sales de communiquer avec Research (et une autre stratégie pour empêcher Research de communiquer avec Sales).

2. Une stratégie conçue pour permettre à Manufacturing de communiquer uniquement avec les rh et le marketing.

Pour ce scénario, il n’est pas nécessaire de définir des stratégies pour les RH ou le marketing.

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
| **Stratégie 1 : empêcher le département des Ventes de communiquer avec la Recherche** | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> Dans cet exemple, la stratégie de cloisonnement de l’information est nommée *Sales-Research*. Lorsque cette stratégie est active et appliquée, elle empêche les utilisateurs du segment Ventes de communiquer avec les utilisateurs du segment Recherche. Cette stratégie est unidirectionnelle; cela n’empêchera pas Research de communiquer avec Sales. Pour cela, la stratégie 2 est nécessaire. |
| **Stratégie 2 : empêcher la Recherche de communiquer avec le département des Ventes** | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> Dans cet exemple, la stratégie de cloisonnement de l’information est nommée *Research-Sales*. Lorsque cette stratégie est active et appliquée, elle empêche les utilisateurs du segment Recherche de communiquer avec les utilisateurs du segment Ventes. |
| **Stratégie 3 : Autoriser la fabrication à communiquer uniquement avec les rh et le marketing** | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p> Dans ce cas, la stratégie de cloisonnement de l’information est nommée *Manufacturing-HRMarketing*. Lorsque cette stratégie est active et appliquée, la Production ne peut communiquer qu’avec les Ressources Humaines et le Marketing. Les ressources humaines et le marketing ne sont pas limités à la communication avec d’autres segments. |

Une fois les segments et les stratégies définis, Contoso applique les stratégies en exécutant l’applet de commande **Start-InformationBarrierPoliciesApplication** .

Une fois l’applet de commande terminée, Contoso est conforme aux exigences légales et industrielles.

## <a name="resources"></a>Ressources

- [Obtenir une vue d’ensemble des obstacles à l’information](information-barriers.md)
- [En savoir plus sur les obstacles à l’information dans Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [En savoir plus sur les obstacles à l’information dans SharePoint Online](/sharepoint/information-barriers)
- [En savoir plus sur les obstacles à l’information dans OneDrive](/onedrive/information-barriers)
