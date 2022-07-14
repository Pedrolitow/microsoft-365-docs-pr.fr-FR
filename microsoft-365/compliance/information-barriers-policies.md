---
title: Démarrer avec le cloisonnement de l’information
description: Découvrez comment prendre en main les obstacles à l’information dans Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, conformité, obstacles à l’information
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
ms.openlocfilehash: d2f2eb77dd143f82ced98f8fce424cc729e26df7
ms.sourcegitcommit: 221212fff9737e0ea386755deb8fed62ae9c254b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2022
ms.locfileid: "66787801"
---
# <a name="get-started-with-information-barriers"></a>Démarrer avec le cloisonnement de l’information

Cet article explique comment configurer des stratégies d’obstacles à l’information (IB) dans votre organisation. Plusieurs étapes sont impliquées. Veillez donc à passer en revue l’ensemble du processus avant de commencer à configurer les stratégies IB.

Vous allez configurer IB dans votre organisation à l’aide de la [portail de conformité Microsoft Purview](https://compliance.microsoft.com) ou à l’aide [de Office 365 PowerShell sécurité et conformité](/powershell/exchange/scc-powershell). Pour les organisations qui configurent IB pour la première fois, nous vous recommandons d’utiliser la solution **d’obstacles à l’information** dans le portail de conformité. Si vous gérez une configuration IB existante et que vous êtes à l’aise avec PowerShell, vous disposez toujours de cette option.

Pour plus d’informations sur les scénarios et fonctionnalités de l’IB, consultez [En savoir plus sur les obstacles à l’information](information-barriers.md).

> [!TIP]
> Pour vous aider à préparer votre plan, un [exemple de scénario](#example-scenario-contosos-departments-segments-and-policies) est inclus dans cet article.

## <a name="required-subscriptions-and-permissions"></a>Abonnements et autorisations requis

Avant de commencer à utiliser IB, vous devez confirmer votre abonnement Microsoft 365 et tous les modules complémentaires. Pour accéder à IB et l’utiliser, votre organisation doit disposer de l’un des abonnements ou modules complémentaires suivants :

- abonnement Microsoft 365 E5/A5 (version payante ou d’évaluation)
- abonnement Office 365 E5/A5/A3/A1 (version payante ou d’évaluation)
- Conformité avancée Office 365 module complémentaire (plus disponible pour les nouveaux abonnements)
- Microsoft 365 E3/A3/A1 + le module complémentaire conformité Microsoft 365 E5/A5
- Microsoft 365 E3/A3/A1 + le module complémentaire de gestion des risques internes Microsoft 365 E5/A5

Pour plus d’informations, consultez [l’aide relative aux licences Microsoft 365 pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

Pour [gérer les stratégies IB](information-barriers-policies.md), vous devez disposer de l’un des rôles suivants :

- Administrateur général Microsoft 365
- Administrateur général Office 365
- Administrateur de conformité
- Gestion de la conformité IB

Si vous souhaitez en savoir plus sur les rôles et les autorisations, consultez la page [Autorisations dans le Centre de sécurité et conformité Office 365](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

## <a name="configuration-concepts"></a>Concepts de configuration

Lorsque vous configurez IB, vous travaillez avec plusieurs objets et concepts.

- Les **attributs du compte utilisateur** sont définis dans Azure Active Directory (ou Exchange Online). Ces attributs peuvent inclure le service, la fonction, l’emplacement, le nom d’équipe et d’autres détails du profil du poste. Vous allez affecter des utilisateurs ou des groupes à des segments avec ces attributs.
- **Les segments sont des ensembles** de groupes ou d’utilisateurs définis dans le portail de conformité ou à l’aide de PowerShell qui utilisent des attributs de groupe ou de compte d’utilisateur sélectionnés. Pour plus d’informations, consultez la liste [des attributs pris en charge par IB](information-barriers-attributes.md) .
- **Les stratégies IB** déterminent les limites ou restrictions de communication. Lorsque vous définissez des stratégies IB, vous choisissez parmi deux types de stratégies :
  - *Bloquer* les stratégies pour empêcher un segment de communiquer avec un autre.
  - *Autoriser* les stratégies de n’autoriser qu’un segment à communiquer avec certains autres segments uniquement.

    > [!NOTE]
    > Pour *les stratégies d’autorisation* , les groupes et les utilisateurs non IB ne sont pas visibles par les utilisateurs inclus dans les segments et stratégies IB. Si vous avez besoin que les groupes et les utilisateurs non IB soient visibles par les utilisateurs inclus dans les segments et stratégies ib, vous devez utiliser des stratégies *de bloc* .

- **L’application** de stratégie est effectuée une fois que toutes les stratégies IB sont définies et que vous êtes prêt à les appliquer dans votre organisation.
- **Visibilité des utilisateurs et groupes non IB**. Les utilisateurs et les groupes non IB sont des utilisateurs et des groupes exclus des segments et des stratégies ib. Selon le type de stratégies IB (bloquer ou autoriser), le comportement de ces utilisateurs et de ces groupes diffère dans Microsoft Teams, SharePoint, OneDrive et dans votre liste d’adresses globale. Pour les utilisateurs définis dans *les stratégies d’autorisation* , les groupes et utilisateurs non IB ne sont pas visibles par les utilisateurs inclus dans les segments et les stratégies IB. Pour les utilisateurs définis dans les stratégies de *bloc* , les groupes et les utilisateurs non IB sont visibles par les utilisateurs inclus dans les segments et stratégies IB.
- **Prise en charge des groupes**. Seuls les groupes modernes sont actuellement pris en charge dans ib et les listes de distribution/groupes de sécurité sont traités comme des groupes non IB.
- **Comptes d’utilisateur masqués/désactivés**. Pour les comptes masqués/désactivés dans votre organisation, le paramètre *HiddenFromAddressListEnabled* est automatiquement défini sur *True* lorsque les comptes d’utilisateurs sont masqués ou désactivés. Dans les organisations compatibles ib, ces comptes ne peuvent pas communiquer avec tous les autres comptes d’utilisateur. Dans Microsoft Teams, toutes les conversations, y compris ces comptes, sont verrouillées ou les utilisateurs sont automatiquement supprimés des conversations.

## <a name="configuration-overview"></a>Vue d’ensemble de la configuration

| **Étapes** | **Ce qui est impliqué** |
|:------|:----------------|
| **Étape 1** : [Vérifier que les conditions préalables sont remplies](#step-1-make-sure-prerequisites-are-met) | - Vérifiez que vous disposez des abonnements et autorisations requis <br/>vérifier que votre annuaire inclut des données pour la segmentation des utilisateurs.<br/>- Activer [la recherche par nom pour Microsoft Teams](/microsoftteams/teams-scoped-directory-search)<br/>vous assurer que l’enregistrement d’audit est activé.<br/>vous assurer qu’aucune stratégie de carnet d’adresses Exchange n’est mise en place. <br/>- Fournir le consentement de l’administrateur pour Microsoft Teams (étapes incluses) |
| **Étape 2** : [Segmenter les utilisateurs de votre organisation](#step-2-segment-users-in-your-organization) | - Déterminer les stratégies nécessaires<br/>- Créer une liste de segments à définir<br/>- Identifier les attributs à utiliser<br/>- Définir des segments en termes de filtres de stratégie |
| **Étape 3** : [Créer des stratégies d’obstacles à l’information](#step-3-create-ib-policies) | - Créer vos stratégies (ne s’appliquent pas encore)<br/>- Choisir parmi deux types (bloquer ou autoriser) |
| **Étape 4** : [Appliquer des stratégies d’obstacle à l’information](#step-4-apply-ib-policies) | - Définir des stratégies sur l’état actif<br/>- Exécuter l’application de stratégie<br/>- Afficher l’état de la stratégie |
| **Étape 5** : [Configuration des obstacles à l’information sur SharePoint et OneDrive (facultatif)](#step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive) | - Configurer IB pour SharePoint et OneDrive |
| **Étape 6** : [Modes de barrières d’information (facultatif)](#step-6-information-barriers-modes) | - Mettre à jour les modes IB le cas échéant |

## <a name="step-1-make-sure-prerequisites-are-met"></a>Étape 1 : Vérifier que les conditions préalables sont remplies

En plus des abonnements et autorisations requis, assurez-vous que les exigences suivantes sont remplies avant de configurer IB :

- **Données d’annuaire** : assurez-vous que la structure de votre organisation est reflétée dans les données d’annuaire. Pour effectuer cette action, assurez-vous que les attributs de compte d’utilisateur (tels que l’appartenance au groupe, le nom du service, etc.) sont correctement renseignés dans Azure Active Directory (ou Exchange Online). Pour en savoir plus, consultez les ressources suivantes :
  - [Attributs pour les stratégies d’obstacle aux informations](information-barriers-attributes.md)
  - [Ajouter ou mettre à jour les informations de profil d’un utilisateur à l’aide d’Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [Configurer les propriétés des comptes d'utilisateur avec Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)

- **Recherche d’annuaires délimités** : avant de définir la première stratégie IB de votre organisation, vous devez [activer la recherche d’annuaires délimités dans Microsoft Teams](/MicrosoftTeams/teams-scoped-directory-search). Attendez au moins 24 heures après l’activation de la recherche d’annuaire délimitée avant de configurer ou de définir des stratégies IB.

- **Vérifiez que la journalisation d’audit est activée** : pour rechercher l’état d’une application de stratégie IB, la journalisation d’audit doit être activée. L'audit est activé par défaut pour les organisations Microsoft 365. Certaines organisations peuvent avoir désactivé l'audit pour des raisons spécifiques. Si l'audit est désactivé pour votre organisation, c'est peut-être parce qu'un autre administrateur l'a désactivé. Nous vous recommandons de confirmer que vous pouvez réactiver l'audit lorsque vous terminez cette étape. Pour plus d’informations, voir [Activer ou désactiver la recherche dans le journal d’audit](turn-audit-log-search-on-or-off.md).

- **Supprimer les stratégies de carnet d’adresses Exchange Online existantes** : avant de définir et d’appliquer des stratégies IB, vous devez supprimer toutes les stratégies de carnet d’adresses Exchange Online existantes dans votre organisation. Les stratégies IB sont basées sur des stratégies de carnet d’adresses et les stratégies ABP existantes ne sont pas compatibles avec les ABA créées par IB. Pour supprimer vos stratégies de carnet d’adresses existantes, consultez [Supprimer une stratégie de carnet d’adresses dans Exchange Online](/exchange/address-books/address-book-policies/remove-an-address-book-policy). Pour plus d’informations sur les politiques et les Exchange Online de l’IB, consultez [Obstacles à l’information et Exchange Online](information-barriers.md#information-barriers-and-exchange-online).

- **Gérer à l’aide de PowerShell (facultatif)** : les segments et stratégies IB peuvent être définis et gérés dans Office 365 PowerShell sécurité & conformité. Bien que plusieurs exemples soient fournis dans cet article, vous devez être familiarisé avec les applets de commande et les paramètres PowerShell si vous choisissez d’utiliser PowerShell pour configurer et gérer des segments et des stratégies IB. Vous aurez également besoin du module Azure Active Directory PowerShell si vous choisissez cette option de configuration.
  - [Se connecter à la sécurité et conformité PowerShell](/powershell/exchange/connect-to-scc-powershell)
  - [Installer Azure Active Directory PowerShell pour Graph](/powershell/azure/active-directory/install-adv2)

- **Administration consentement pour IB dans Microsoft Teams** : lorsque vos stratégies IB sont en place, elles peuvent supprimer les utilisateurs non conformes à l’IB des groupes (par exemple, les canaux Teams, qui sont basés sur des groupes). Cette configuration permet de garantir que votre organisation reste conforme aux stratégies et réglementations. Utilisez la procédure suivante pour permettre aux stratégies IB de fonctionner comme prévu dans Microsoft Teams.

   1. Prérequis : [Installer Azure Active Directory PowerShell pour Graph](/powershell/azure/active-directory/install-adv2).

   2. Exécutez les applets de commande Windows PowerShell suivantes dans cet ordre:

      ```powershell
      Connect-AzureAD -Tenant "<yourtenantdomain.com>"  //for example: Connect-AzureAD -Tenant "Contoso.onmicrosoft.com"
      $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
      $sp=Get-AzureADServicePrincipal -Filter "appid eq '$($appid)'"
      if ($sp -eq $null) { New-AzureADServicePrincipal -AppId $appId }
      Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
      ```

   3. Lorsque vous y invitez, connectez-vous à l’aide de votre compte scolaire ou Office 365.

   4. Dans la boîte de dialogue **Autorisations demandées** , passez en revue les informations, puis choisissez **Accepter**.

Lorsque toutes les conditions préalables sont remplies, passez à l’étape suivante.

## <a name="step-2-segment-users-in-your-organization"></a>Étape 2 : Segmenter les utilisateurs de votre organisation

Dans cette étape, vous allez déterminer les stratégies IB nécessaires, créer une liste de segments à définir et définir vos segments. La définition de segments n’affecte pas les utilisateurs. Elle définit simplement la phase de définition et d’application des stratégies IB.

### <a name="determine-what-policies-are-needed"></a>Déterminer les stratégies nécessaires

En tenant compte des besoins de votre organisation, déterminez les groupes au sein de votre organisation qui auront besoin de stratégies IB. Posez-vous les questions suivantes :

- Existe-t-il des réglementations internes, légales ou sectorielles qui imposent la restriction de la communication et de la collaboration entre les groupes et les utilisateurs de votre organisation ?
- Y a-t-il des groupes ou des utilisateurs qui doivent être empêchés de communiquer avec un autre groupe d’utilisateurs ?
- Y a-t-il des groupes ou des utilisateurs qui doivent être autorisés à communiquer uniquement avec un ou deux autres groupes d’utilisateurs ?

Considérez les stratégies dont vous avez besoin comme appartenant à l’un des deux types suivants :

- Les politiques de *blocage* empêchent un groupe de communiquer avec un autre groupe.
- *Autoriser les* stratégies permet à un groupe de communiquer uniquement avec des groupes spécifiques.

Lorsque vous disposez de votre liste initiale de groupes et de stratégies nécessaires, procédez à l’identification des segments dont vous aurez besoin pour les stratégies IB.

### <a name="identify-segments"></a>Identifier les segments

En plus de votre liste initiale de stratégies, dressez une liste de segments pour votre organisation. Les utilisateurs qui seront inclus dans les stratégies IB doivent appartenir à un segment. Planifier soigneusement vos segments en tant qu’utilisateur ne peut se trouver qu’en un seul segment. Chaque segment ne peut avoir qu’une seule stratégie IB appliquée.

> [!IMPORTANT]
> Un utilisateur ne peut se trouver que dans un seul segment.

Déterminez les attributs dans les données d’annuaire de votre organisation que vous utiliserez pour définir des segments. Vous pouvez utiliser *Department*, *MemberOf* ou l’un des attributs IB pris en charge. Assurez-vous que vous avez des valeurs dans l’attribut que vous sélectionnez pour les utilisateurs. Pour plus d’informations, consultez les [attributs pris en charge pour IB](information-barriers-attributes.md).

> [!IMPORTANT]
> **Avant de passer à la section suivante, assurez-vous que vos données d’annuaire ont des valeurs pour les attributs que vous pouvez utiliser pour définir des segments**. Si vos données d’annuaire n’ont pas de valeurs pour les attributs que vous souhaitez utiliser, les comptes d’utilisateur doivent être mis à jour pour inclure ces informations avant de continuer à configurer IB. Pour obtenir de l’aide à ce sujet, consultez les ressources suivantes :<br/>- [Configurer les propriétés du compte d’utilisateur avec Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)<br/>- [Ajouter ou mettre à jour les informations de profil d’un utilisateur à l’aide d’Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

### <a name="define-segments-using-the-compliance-portal"></a>Définir des segments à l’aide du portail de conformité

Pour définir des segments dans le portail de conformité, procédez comme suit :

1. Connectez-vous au [portail de conformité](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation.
2. Dans le portail de conformité, sélectionnez **Segments des obstacles à l’information** > .
3. Dans la page **Segments** , sélectionnez **Nouveau segment** pour créer et configurer un nouveau segment.
4. Dans la page **Nom** , entrez un nom pour le segment. Vous ne pouvez pas renommer un segment une fois qu’il a été créé.
5. Sélectionnez **Suivant**.
6. Dans la page **Filtre de groupe d’utilisateurs** , **sélectionnez Ajouter** pour configurer le groupe et les attributs utilisateur pour le segment. Choisissez un attribut pour le segment dans la liste des attributs disponibles.
7. Pour l’attribut sélectionné, sélectionnez *Égal* ou *Non égal* , puis entrez la valeur de l’attribut. Par exemple, si vous avez sélectionné *Department* comme attribut et *Equals*, vous pouvez entrer *Marketing* en tant que *service* défini pour cette condition de segment. Vous pouvez ajouter des conditions supplémentaires pour un attribut en sélectionnant **Ajouter une condition**. Si vous devez supprimer une condition d’attribut ou d’attribut, sélectionnez l’icône supprimer pour l’attribut ou la condition.
8. Ajoutez des attributs supplémentaires en fonction des besoins dans la page de **filtre du groupe d’utilisateurs** , puis sélectionnez **Suivant**.
9. Dans la page **Vérifier vos paramètres** , passez en revue les paramètres que vous avez choisis pour le segment, ainsi que les suggestions ou avertissements pour vos sélections. Sélectionnez **Modifier** pour modifier l’un des attributs et conditions du segment ou **sélectionnez Envoyer** pour créer le segment.

    > [!IMPORTANT]
    > **Assurez-vous que vos segments ne se chevauchent pas**. Chaque utilisateur qui sera affecté par les stratégies IB doit appartenir à un seul segment (et un seul). Aucun utilisateur ne doit appartenir à deux segments ou plus. Consultez [l’exemple : les segments définis de Contoso](#contosos-defined-segments) dans cet article pour obtenir un exemple de scénario.

### <a name="define-segments-using-powershell"></a>Définir des segments à l’aide de PowerShell

Pour définir des segments avec PowerShell, procédez comme suit :

1. Utilisez [l’applet](information-barriers-attributes.md) **de commande New-OrganizationSegment** avec le paramètre **UserGroupFilter** qui correspond à l’attribut que vous souhaitez utiliser.

    | Syntaxe | Exemple |
    |:---------|:----------|
    | `New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"` |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>Dans cet exemple, un segment appelé *RH* est défini à l’aide des *ressources humaines*, une valeur dans l’attribut *Department* . La partie **-eq** de l’applet de commande fait référence à « equals ». (Vous pouvez également utiliser **-ne** pour signifier « non égal à ». Voir [Utilisation de « equals » et de « not equals » dans les définitions de segment](#using-equals-and-not-equals-in-powershell-segment-definitions).) |

    Une fois que vous avez exécuté chaque applet de commande, vous devez voir une liste de détails sur le nouveau segment. Les détails incluent le type du segment, qui l’a créé ou modifié pour la dernière fois, et ainsi de suite. 

2. Répétez ce processus pour chaque segment que vous souhaitez définir.

    > [!IMPORTANT]
    > **Assurez-vous que vos segments ne se chevauchent pas**. Chaque utilisateur qui sera affecté par les stratégies IB doit appartenir à un seul segment (et un seul). Aucun utilisateur ne doit appartenir à deux segments ou plus. Consultez [l’exemple : les segments définis de Contoso](#contosos-defined-segments) dans cet article pour obtenir un exemple de scénario.

Une fois que vous avez défini vos segments, passez à [l’étape 3 : Créer des stratégies IB](#step-3-create-ib-policies).

### <a name="using-equals-and-not-equals-in-powershell-segment-definitions"></a>Utilisation de « equals » et de « not equals » dans les définitions de segment PowerShell

Dans l’exemple suivant, nous configurons des segments IB à l’aide de PowerShell et définissons un segment tel que « Department equals HR ».

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
| `New-OrganizationSegment -Name "LocalFTE" -UserGroupFilter "Location -eq 'Local'" -and "Position -ne 'Temporary'"` | Dans cet exemple, nous avons défini un segment appelé *LocalFTE* qui inclut les utilisateurs qui se trouvent localement et dont les positions ne sont pas répertoriées comme *temporaires*. |
| `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "MemberOf -eq 'group1@contoso.com'' -and MemberOf -ne 'group3@contoso.com'"`| Dans cet exemple, nous avons défini un segment appelé *Segment1* qui inclut les utilisateurs qui sont membres de group1@contoso.com et non membres de group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment2" -UserGroupFilter "MemberOf -eq 'group2@contoso.com' -or MemberOf -ne 'group3@contoso.com'"` | Dans cet exemple, nous avons défini un segment appelé *Segment2* qui inclut les utilisateurs qui sont membres de group2@contoso.com et non membres de group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment1and2" -UserGroupFilter "(MemberOf -eq 'group1@contoso.com' -or MemberOf -eq 'group2@contoso.com') -and MemberOf -ne 'group3@contoso.com'"`| Dans cet exemple, nous avons défini un segment appelé *Segment1and2* qui inclut des utilisateurs dans group1@contoso.com et group2@contoso.com et non des membres de group3@contoso.com. |

> [!TIP]
> Si possible, utilisez des définitions de segment qui incluent « -eq » ou « -ne ». Essayez de ne pas définir de définitions de segment complexes.

## <a name="step-3-create-ib-policies"></a>Étape 3 : Créer des stratégies IB

Lorsque vous créez vos stratégies IB, vous déterminez si vous devez empêcher les communications entre certains segments ou limiter les communications à certains segments. Dans l’idéal, vous utiliserez le nombre minimal de stratégies IB pour vous assurer que votre organisation est conforme aux exigences internes, légales et sectorielles. Vous pouvez utiliser le portail de conformité ou PowerShell pour créer et appliquer des stratégies IB.

> [!TIP]
> Pour la cohérence de l’expérience utilisateur, nous vous recommandons d’utiliser des stratégies de blocage pour la plupart des scénarios si possible.

Avec votre liste de segments d’utilisateurs et les stratégies IB que vous souhaitez définir, sélectionnez un scénario, puis suivez les étapes.

- [Scénario 1 : Bloquer les communications entre les segments](#scenario-1-block-communications-between-segments)
- [Scénario 2 : Autoriser un segment à communiquer avec un seul autre segment](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> **Assurez-vous qu’au fur et à mesure que vous définissez des stratégies, vous n’affectez pas plusieurs stratégies à un segment**. Par exemple, si vous définissez une stratégie pour un segment appelé *Ventes*, ne définissez pas de stratégie supplémentaire pour le segment *Ventes* .<br> En outre, lorsque vous définissez des stratégies IB, veillez à définir ces stratégies sur l’état inactif jusqu’à ce que vous soyez prêt à les appliquer. La définition (ou la modification) de stratégies n’affecte pas les utilisateurs tant que ces stratégies ne sont pas définies sur l’état actif, puis appliquées.

### <a name="scenario-1-block-communications-between-segments"></a>Scénario 1 : bloquer les communications entre les segments

Lorsque vous souhaitez empêcher les segments de communiquer entre eux, vous définissez deux stratégies : une pour chaque direction. Chaque stratégie bloque la communication dans une seule direction.

Par exemple, supposons que vous souhaitez bloquer les communications entre le segment A et le segment B. Dans ce cas, vous devez définir deux stratégies :

- Une stratégie empêchant le segment A de communiquer avec le segment B
- Une deuxième stratégie pour empêcher le segment B de communiquer avec le segment A

#### <a name="create-policies-using-the-compliance-portal-for-scenario-1"></a>Créer des stratégies à l’aide du portail de conformité pour le scénario 1

Pour définir des stratégies dans le portail de conformité, procédez comme suit :

1. Connectez-vous au [portail de conformité](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation.
2. Dans le portail de conformité, sélectionnez **Stratégies d’obstacles à l’information** > .
3. Dans la page **Stratégies** , sélectionnez **Créer une stratégie** pour créer et configurer une stratégie IB.
4. Dans la page **Nom** , entrez un nom pour la stratégie, puis sélectionnez **Suivant**.
5. Dans la page **Segment affecté** , **sélectionnez Choisir un segment**. Utilisez la zone de recherche pour rechercher un segment par nom ou faites défiler pour sélectionner le segment dans la liste affichée. Sélectionnez **Ajouter** pour ajouter le segment sélectionné à la stratégie. Vous ne pouvez sélectionner qu’un seul segment.
6. Sélectionnez **Suivant**.
7. Dans la page **Communication et collaboration** , sélectionnez le type de stratégie dans le champ **Communication et collaboration** . Les options de stratégie sont *autorisées* ou *bloquées*. Dans cet exemple de scénario, *Blocked* est sélectionné pour la première stratégie.

    >[!IMPORTANT]
    >L’état Autorisé et Bloqué pour les segments ne peut pas être modifié après la création d’une stratégie. Pour modifier l’état après avoir créé une stratégie, vous devez la supprimer et en créer une nouvelle.

8. **Sélectionnez Choisir un segment** pour définir les actions du segment cible. Vous pouvez affecter plusieurs segments dans cette étape. Par exemple, si vous vouliez empêcher les utilisateurs d’un segment appelé *Sales* de communiquer avec les utilisateurs dans un segment appelé *Recherche*, vous auriez défini le segment *Ventes* à l’étape 5 et vous affecteriez *Research* dans l’option **Choisir un segment** dans cette étape.
9. Sélectionnez **Suivant**.
10. Dans la page **État de** la stratégie, basculez l’état de la stratégie active **sur Activé**. Sélectionnez **Suivant** pour continuer.
11. Dans la page **Vérifier vos paramètres** , passez en revue les paramètres que vous avez choisis pour la stratégie, ainsi que les suggestions ou avertissements pour vos sélections. Sélectionnez **Modifier** pour modifier l’un des segments et l’état de la stratégie ou **sélectionnez Envoyer** pour créer la stratégie.

Dans cet exemple, vous allez répéter les étapes précédentes pour créer une deuxième stratégie *de blocage* afin de restreindre l’accès des utilisateurs d’un segment appelé *Research* à la communication avec les utilisateurs d’un segment appelé *Ventes*. Vous auriez défini le segment *Recherche* à l’étape 5 et vous attribueriez *Sales* (ou plusieurs segments) dans l’option **Choisir un segment** .

#### <a name="create-policies-using-powershell-for-scenario-1"></a>Créer des stratégies à l’aide de PowerShell pour le scénario 1

Pour définir des stratégies avec PowerShell, procédez comme suit :

1. Pour définir votre première stratégie de blocage, utilisez l’applet de commande **New-InformationBarrierPolicy** avec le paramètre **SegmentsBlocked** .

    | Syntaxe | Exemple |
    |:--------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"` | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> Dans cet exemple, nous avons défini une stratégie appelée *Sales-Research* pour un segment appelé *Sales*. Lorsqu’elle est active et appliquée, cette stratégie empêche les utilisateurs dans *Sales* de communiquer avec les utilisateurs dans un segment appelé *Recherche*. |

2. Pour définir votre deuxième segment de blocage, utilisez à nouveau l’applet de commande **New-InformationBarrierPolicy** avec le paramètre **SegmentsBlocked** , cette fois avec les segments inversés.

    | Exemple | Remarque |
    |:----------|:-------|
    |`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` | Dans cet exemple, nous avons défini une stratégie appelée *Research-Sales* pour empêcher *Research* de communiquer avec *Sales*. |

3. Passez à l’une des actions suivantes :

   - (Si nécessaire) [Définir une stratégie pour permettre à un segment de communiquer uniquement avec un autre segment](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment) 
   - (Une fois toutes vos stratégies définies) [Appliquer des stratégies IB](#step-4-apply-ib-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>Scénario 2 : Autoriser un segment à communiquer avec un seul autre segment

Lorsque vous souhaitez autoriser un segment à communiquer avec un seul autre segment, vous ne définissez qu’une seule stratégie pour ce segment. Le segment avec lequel il est communiqué ne nécessite pas de stratégie directionnelle similaire (car il peut communiquer et collaborer avec tout le monde par défaut).

#### <a name="create-a-policy-using-the-compliance-portal-for-scenario-2"></a>Créer une stratégie à l’aide du portail de conformité pour le scénario 2

Pour définir des stratégies dans le portail de conformité, procédez comme suit :

1. Connectez-vous au [portail de conformité](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation.
2. Dans le portail de conformité, sélectionnez **Stratégies d’obstacles à l’information** > .
3. Dans la page **Stratégies** , sélectionnez **Créer une stratégie** pour créer et configurer une stratégie IB.
4. Dans la page **Nom** , entrez un nom pour la stratégie, puis sélectionnez **Suivant**.
5. Dans la page **Segment affecté** , **sélectionnez Choisir un segment**. Utilisez la zone de recherche pour rechercher un segment par nom ou faites défiler pour sélectionner le segment dans la liste affichée. Sélectionnez **Ajouter** pour ajouter le segment sélectionné à la stratégie. Vous ne pouvez sélectionner qu’un seul segment.
6. Sélectionnez **Suivant**.
7. Dans la page **Communication et collaboration** , sélectionnez le type de stratégie dans le champ **Communication et collaboration** . Les options de stratégie sont *autorisées* ou *bloquées*. Dans cet exemple de scénario, *Allowed* est sélectionné pour la stratégie.

    >[!IMPORTANT]
    >L’état Autorisé et Bloqué pour les segments ne peut pas être modifié après la création d’une stratégie. Pour modifier l’état après avoir créé une stratégie, vous devez la supprimer et en créer une nouvelle.

8. **Sélectionnez Choisir un segment** pour définir les actions du segment cible. Vous pouvez affecter plusieurs segments dans cette étape. Par exemple, si vous vouliez autoriser les utilisateurs d’un segment appelé *Fabrication* à communiquer avec les utilisateurs dans un segment appelé *RH*, vous auriez défini le segment *Fabrication* à l’étape 5 et vous attribueriez *des ressources humaines* dans l’option **Choisir un segment** à cette étape.
9. Sélectionnez **Suivant**.
10. Dans la page **État de** la stratégie, basculez l’état de la stratégie active **sur Activé**. Sélectionnez **Suivant** pour continuer.
11. Dans la page **Vérifier vos paramètres** , passez en revue les paramètres que vous avez choisis pour la stratégie, ainsi que les suggestions ou avertissements pour vos sélections. Sélectionnez **Modifier** pour modifier l’un des segments et l’état de la stratégie ou **sélectionnez Envoyer** pour créer la stratégie.

#### <a name="create-a-policy-using-powershell-for-scenario-2"></a>Créer une stratégie à l’aide de PowerShell pour le scénario 2

Pour définir des stratégies avec PowerShell, procédez comme suit :

1. Pour permettre à un segment de communiquer avec un seul autre segment, utilisez l’applet de commande **New-InformationBarrierPolicy** avec le paramètre **SegmentsAllowed** .

    | Syntaxe | Exemple |
    |:----------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"` | `New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive` <p> Dans cet exemple, nous avons défini une stratégie appelée *Manufacturing-HR* pour un segment appelé *Manufacturing*. Lorsqu’elle est active et appliquée, cette stratégie permet aux utilisateurs de *Manufacturing de* communiquer uniquement avec les utilisateurs d’un segment appelé *RH*. Dans ce cas, *manufacturing* ne peut pas communiquer avec les utilisateurs qui ne font pas partie des *RH*. |

    **Si nécessaire, vous pouvez spécifier plusieurs segments avec cette applet de commande, comme illustré dans l’exemple suivant.**

    | Syntaxe | Exemple |
    |:---------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name", "segment3name","segment1name"` | `New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive` <p> Dans cet exemple, nous avons défini une stratégie qui permet au segment *Recherche* de communiquer uniquement avec *les ressources humaines* et *la fabrication*. |

    Répétez cette étape pour chaque stratégie que vous souhaitez définir pour permettre à des segments spécifiques de communiquer uniquement avec certains autres segments spécifiques.

2. Passez à l’une des actions suivantes :

   - (Si nécessaire) [Définir une stratégie pour bloquer les communications entre les segments](#scenario-1-block-communications-between-segments) 
   - (Une fois toutes vos stratégies définies) [Appliquer des stratégies IB](#step-4-apply-ib-policies)

## <a name="step-4-apply-ib-policies"></a>Étape 4 : Appliquer des stratégies IB

Les stratégies IB ne sont pas en vigueur tant que vous ne les avez pas définies sur l’état actif et appliqué les stratégies.

### <a name="apply-policies-using-the-compliance-portal"></a>Appliquer des stratégies à l’aide du portail de conformité

Pour appliquer des stratégies dans le portail de conformité, procédez comme suit :

1. Connectez-vous au [portail de conformité](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation.
2. Dans le portail de conformité, sélectionnez Application **de stratégie d’obstacles** > **à l’information**.
3. Dans la page **Application des stratégies** , **sélectionnez Appliquer toutes les stratégies** pour appliquer toutes les stratégies IB de votre organisation.

    >[!NOTE]
    >Autorisez 30 minutes pour que le système commence à appliquer les stratégies. Le système applique les stratégies utilisateur par utilisateur. Le système traite environ 5 000 comptes d’utilisateurs par heure.

### <a name="apply-policies-using-powershell"></a>Appliquer des stratégies à l’aide de PowerShell

Pour appliquer des stratégies à l’aide de PowerShell, procédez comme suit :

1. Utilisez l’applet de commande **Get-InformationBarrierPolicy** pour afficher la liste des stratégies qui ont été définies. Notez l’état et l’identité (GUID) de chaque stratégie.

    Syntaxe: `Get-InformationBarrierPolicy`

2. Pour définir une stratégie sur l’état actif, utilisez l’applet de commande **Set-InformationBarrierPolicy** avec un paramètre **Identity** et le paramètre **State** défini sur **Active**. 

    | Syntaxe | Exemple |
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Active` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p> Dans cet exemple, nous définissons une stratégie IB qui a le GUID *43c37853-ea10-4b90-a23d-ab8c93772471* sur l’état actif. |

    Répétez cette étape en fonction de chaque stratégie.

3. Lorsque vous avez terminé de définir vos stratégies IB sur l’état actif, utilisez l’applet de commande **Start-InformationBarrierPoliciesApplication** dans Security & Compliance PowerShell.

    Syntaxe: `Start-InformationBarrierPoliciesApplication`

    Après avoir exécuté `Start-InformationBarrierPoliciesApplication`, attendez 30 minutes pour que le système commence à appliquer les politiques. Le système applique les stratégies utilisateur par utilisateur. Le système traite environ 5 000 comptes d’utilisateurs par heure.

### <a name="view-status-of-user-accounts-segments-policies-or-policy-application"></a>Afficher l’état des comptes d’utilisateur, des segments, des stratégies ou de l’application de stratégie

Avec PowerShell, vous pouvez afficher l’état des comptes d’utilisateur, des segments, des stratégies et de l’application de stratégie, comme indiqué dans le tableau suivant.

| Pour afficher ces informations | Effectuer cette action |
|:---------------|:----------|
| Comptes d’utilisateur | Utilisez l’applet de commande **Get-InformationBarrierRecipientStatus** avec les paramètres d’identité. <p> Syntaxe: `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Vous pouvez utiliser n’importe quelle valeur qui identifie de manière unique chaque utilisateur, telle que le nom, l’alias, le nom unique, le nom de domaine canonique, l’adresse e-mail ou le GUID. <p> Exemple : `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> Dans cet exemple, nous faisons référence à deux comptes d’utilisateur dans Office 365 : *meganb* pour *Megan* et *alexw* pour *Alex*. <p> (Vous pouvez également utiliser cette applet de commande pour un seul utilisateur : `Get-InformationBarrierRecipientStatus -Identity <value>`) <p> Cette applet de commande retourne des informations sur les utilisateurs, telles que les valeurs d’attribut et les stratégies IB appliquées.|
| Segments | Utilisez **l’applet de commande Get-OrganizationSegment** .<p> Syntaxe: `Get-OrganizationSegment` <p> Cette applet de commande affiche la liste de tous les segments définis pour votre organisation. |
| Stratégies IB | Utilisez l’applet **de commande Get-InformationBarrierPolicy** . <p> Syntaxe: `Get-InformationBarrierPolicy` <p> Cette applet de commande affiche la liste des stratégies IB qui ont été définies et leur état. |
| L’application de stratégie IB la plus récente | Utilisez l’applet de commande **Get-InformationBarrierPoliciesApplicationStatus** . <p> Syntaxe: `Get-InformationBarrierPoliciesApplicationStatus`<p> Cette applet de commande affiche des informations indiquant si l’application de stratégie est terminée, a échoué ou est en cours. |
| Toutes les applications de stratégie IB|Utiliser `Get-InformationBarrierPoliciesApplicationStatus -All`<p> Cette applet de commande affiche des informations indiquant si l’application de stratégie est terminée, a échoué ou est en cours.|

### <a name="what-if-i-need-to-remove-or-change-policies"></a>Que se passe-t-il si je dois supprimer ou modifier des stratégies ?

Des ressources sont disponibles pour vous aider à gérer vos stratégies d’ib.

- Pour modifier, arrêter ou supprimer des stratégies d’ib, consultez [Gérer les stratégies d’obstacles à l’information](information-barriers-edit-segments-policies.md).
- Si un problème se produit avec l’IB, consultez [Résolution des problèmes liés aux obstacles à l’information](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting).

## <a name="step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive"></a>Étape 5 : Configuration des obstacles à l’information sur SharePoint et OneDrive

Si vous configurez IB pour SharePoint et OneDrive, vous devez activer IB sur ces services. Vous devez également activer IB sur ces services si vous configurez IB pour Microsoft Teams. Lorsqu’une équipe est créée dans l’équipe Microsoft Teams, un site SharePoint est automatiquement créé et associé à Microsoft Teams pour l’expérience de fichiers. Les stratégies IB ne sont pas honorées par défaut sur ce nouveau site et fichiers SharePoint.

Pour activer IB dans SharePoint et OneDrive, suivez les instructions et les étapes de l’article [Utiliser les obstacles à l’information avec SharePoint](/sharepoint/information-barriers) .

## <a name="step-6-information-barriers-modes"></a>Étape 6 : Modes de barrières d’information

Les modes peuvent aider à renforcer l’accès, le partage et l’appartenance à une ressource Microsoft 365 en fonction du mode IB de la ressource. Les modes sont pris en charge sur les sites Groupes Microsoft 365, Microsoft Teams, OneDrive et SharePoint et sont automatiquement activés dans votre configuration IB nouvelle ou existante.

Les modes IB suivants sont pris en charge sur les ressources Microsoft 365 :

| **Mode** | **Description** | **Exemple** |
|:-----|:------------|:--------|
| **Ouvert** | Aucune stratégie ou segment IB n’est associé à la ressource Microsoft 365. N’importe qui peut être invité à être membre de la ressource. | Un site d’équipe créé pour l’événement de pique-nique pour votre organisation. |
| **Owner Moderated (préversion)** | La stratégie IB de la ressource Microsoft 365 est déterminée à partir de la stratégie IB du propriétaire de la ressource. Les propriétaires de ressources peuvent inviter n’importe quel utilisateur à la ressource en fonction de leurs stratégies IB. Ce mode est utile lorsque votre entreprise souhaite autoriser la collaboration entre les utilisateurs de segment incompatibles qui sont modérés par le propriétaire. Seul le propriétaire de la ressource peut ajouter de nouveaux membres en fonction de sa stratégie IB. | Le vice-président des ressources humaines souhaite collaborer avec les VPs of Sales and Research. Nouveau site SharePoint qui est défini avec le mode IB *Owner Moderated* pour ajouter les utilisateurs des segments Ventes et Recherche au même site. Il incombe au propriétaire de s’assurer que les membres appropriés sont ajoutés à la ressource. |
| **Implicite** | La stratégie ib ou les segments de la ressource Microsoft 365 sont hérités de la stratégie IB des membres de la ressource. Le propriétaire peut ajouter des membres tant qu’ils sont compatibles avec les membres existants de la ressource. Ce mode est le mode IB par défaut pour Microsoft Teams. | L’utilisateur du segment Ventes crée une équipe Microsoft Teams pour collaborer avec d’autres segments compatibles de l’organisation. |
| **Explicit** | La stratégie IB de la ressource Microsoft 365 correspond aux segments associés à la ressource. Le propriétaire de la ressource ou l’administrateur SharePoint peut gérer les segments de la ressource. | Un site créé uniquement pour permettre aux membres du segment Ventes de collaborer en associant le segment Ventes au site. |
| **Mixte (préversion)** | Applicable uniquement à OneDrive. La stratégie IB de OneDrive correspond aux segments associés à OneDrive. Le propriétaire de la ressource ou l’administrateur OneDrive peut gérer les segments de la ressource. | Un OneDrive créé pour permettre aux membres du segment Ventes de collaborer est autorisé à être partagé avec des utilisateurs non agrégés. |

Pour plus d’informations sur les modes IB et la façon dont ils sont configurés entre les services, consultez les articles suivants :

- [Modes d’obstacle à l’information et Microsoft Teams](/microsoftteams/information-barriers-in-teams)
- [Modes d’obstacle à l’information et OneDrive](/onedrive/information-barriers)
- [Modes d’obstacle à l’information et Microsoft Office SharePoint Online](/sharepoint/information-barriers)

## <a name="example-scenario-contosos-departments-segments-and-policies"></a>Exemple de scénario : services, segments et stratégies de Contoso

Pour voir comment une organisation peut aborder la définition de segments et de stratégies, prenez en compte l’exemple de scénario suivant.

### <a name="contosos-departments-and-plan"></a>Départements et plan de Contoso

Contoso compte cinq départements : *RH*, *Sales*, *Marketing*, *Research* et *Manufacturing*. Pour rester conformes aux réglementations du secteur, les utilisateurs de certains services ne sont pas censés communiquer avec d’autres services, comme indiqué dans le tableau suivant :

| **Segment** | **Peut communiquer avec** | **Impossible de communiquer avec** |
|:------------|:-------------------------|:---------------------------|
| HR | Tout le monde | (aucune restriction) |
| Ventes | RH, Marketing, Fabrication | Recherche |
| Marketing | Tout le monde | (aucune restriction) |
| Recherche | RH, Marketing, Fabrication | Ventes |
| Production | RH, Marketing | Toute autre personne que les RH ou le marketing |

Pour cette structure, le plan de Contoso comprend trois stratégies IB :

1. Une stratégie IB conçue pour empêcher sales de communiquer avec Research
2. Une autre stratégie de l’IB pour empêcher la recherche de communiquer avec sales.
3. Une stratégie d’IB conçue pour permettre à Manufacturing de communiquer uniquement avec les rh et le marketing.

Pour ce scénario, il n’est pas nécessaire de définir des stratégies IB pour *les RH* ou *le marketing*.

### <a name="contosos-defined-segments"></a>Segments définis par Contoso

Contoso utilisera l’attribut Department dans Azure Active Directory pour définir des segments, comme suit :

| Service | Définition de segment |
|:-------------|:---------------------|
| RH | `New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` |
| Ventes | `New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"` |
| Marketing | `New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"` |
| Recherche | `New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"` |
| Production | `New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"` |

Une fois les segments définis, Contoso procède à la définition des stratégies IB.

### <a name="contosos-ib-policies"></a>Stratégies IB de Contoso

Contoso définit trois stratégies IB, comme décrit dans le tableau suivant :

| Stratégie | Définition de la stratégie |
|:---------|:--------------------|
| **Stratégie 1 : empêcher le département des Ventes de communiquer avec la Recherche** | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> Dans cet exemple, la stratégie IB est appelée *Sales-Research*. Lorsque cette stratégie est active et appliquée, elle empêche les utilisateurs du segment Ventes de communiquer avec les utilisateurs du segment Recherche. Cette stratégie est unidirectionnelle; cela n’empêchera pas Research de communiquer avec Sales. Pour cela, la stratégie 2 est nécessaire. |
| **Stratégie 2 : empêcher la Recherche de communiquer avec le département des Ventes** | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> Dans cet exemple, la stratégie IB est appelée *Research-Sales*. Lorsque cette stratégie est active et appliquée, elle empêche les utilisateurs du segment Recherche de communiquer avec les utilisateurs du segment Ventes. |
| **Stratégie 3 : Autoriser la fabrication à communiquer uniquement avec les rh et le marketing** | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p> Dans ce cas, la politique de l’IB est appelée *Manufacturing-HRMarketing*. Lorsque cette stratégie est active et appliquée, la Production ne peut communiquer qu’avec les Ressources Humaines et le Marketing. Les ressources humaines et le marketing ne sont pas limités à la communication avec d’autres segments. |

Une fois les segments et les stratégies définis, Contoso applique les stratégies en exécutant l’applet de commande **Start-InformationBarrierPoliciesApplication** .

Une fois l’applet de commande terminée, Contoso est conforme aux exigences du secteur.

## <a name="resources"></a>Ressources

- [En savoir plus sur les obstacles aux informations](information-barriers.md)
- [En savoir plus sur les obstacles à l’information dans Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [En savoir plus sur les obstacles à l’information dans SharePoint Online](/sharepoint/information-barriers)
- [En savoir plus sur les obstacles à l’information dans OneDrive](/onedrive/information-barriers)
