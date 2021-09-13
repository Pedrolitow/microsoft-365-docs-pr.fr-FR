---
title: Choisir le domaine à utiliser lors de la création de Microsoft 365 groupes
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 7cf5655d-e523-4bc3-a93b-3ccebf44a01a
recommendations: false
description: Apprenez à choisir le domaine à utiliser lors de la création de groupes Microsoft 365 en configurant des stratégies d’adresse de messagerie à l’aide de PowerShell.
ms.openlocfilehash: 4d620c3344f83f56afd05c00d78615331dd413ed
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59207068"
---
# <a name="choose-the-domain-to-use-when-creating-microsoft-365-groups"></a>Choisir le domaine à utiliser lors de la création de Microsoft 365 groupes

Certaines organisations utilisent des domaines de messagerie distincts pour segmenter différentes parties de leurs activités. Vous pouvez spécifier le domaine à utiliser lorsque vos utilisateurs créent Microsoft 365 groupes.
  
Si votre organisation a besoin que les utilisateurs créent leurs groupes dans des domaines autres que le domaine accepté par défaut de votre entreprise, vous pouvez l’autoriser en configurant des stratégies d’adresse de messagerie (EAP) à l’aide de PowerShell.

Avant de pouvoir exécuter les cmdlets PowerShell, téléchargez et installez un module qui vous permettra de parler à votre organisation. Consultez les [Connecter à Exchange Online à l’aide de PowerShell à distance.](/powershell/exchange/connect-to-exchange-online-powershell)

## <a name="example-scenarios"></a>Exemples de scénarios

Supposons que le domaine principal de votre entreprise soit Contoso.com. Toutefois, le domaine accepté par défaut de votre organisation est service.contoso.com. Cela signifie que les groupes seront créés dans service.contoso.com (par exemple, jimsteam@service.contoso.com).
  
Supposons que des sous-domaines sont également configurés dans votre organisation. Vous souhaitez également créer des groupes dans ces domaines :
  
- students.contoso.com pour les étudiants
    
- faculty.contoso.com pour les membres du corps enseignant
    
Les deux scénarios suivants expliquent comment effectuer cette tâche.

> [!NOTE]
> Lorsque vous avez des projets DPE, ils sont évalués dans l’ordre de priorité. Une valeur de 1 signifie la priorité la plus élevée. Une fois qu’un EAP correspond, aucun autre EAP n’est évalué et les adresses qui sont marqués sur le groupe sont conformes à l’EAP. > si aucun eaps ne correspond aux critères spécifiés, le groupe est provisioné dans le domaine accepté par défaut de l’organisation. Consultez [Gérer les domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) dans Exchange Online pour plus d’informations sur l’ajout d’un domaine accepté.
  
### <a name="scenario-1"></a>Scénario 1

L’exemple suivant vous montre comment mettre en service Microsoft 365 groupes de votre organisation dans groups.contoso.com domaine.
  
```
New-EmailAddressPolicy -Name Groups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@groups.contoso.com" -Priority 1
```

### <a name="scenario-2"></a>Scénario 2

Supposons que vous vouliez contrôler dans quels sous-domaines Microsoft 365 groupes sont créés. Vous souhaitez :
  
- Groupes créés par des étudiants (utilisateurs dont le service **est** réservé aux **étudiants)** dans students.groups.contoso.com domaine. Utilisez la commande suivante :
    
  ```
  New-EmailAddressPolicy -Name StudentsGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Students'} -Priority 1
  ```

- Groupes créés par des membres  du corps enseignant (les utilisateurs dont le service est définie sur Enseignant ou l’adresse **e-mail** contient faculty.contoso.com) ) dans le faculty.groups.contoso.com domaine. Utilisez la commande suivante :
    
  ```
  New-EmailAddressPolicy -Name FacultyGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@faculty.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Faculty' -or EmailAddresses -like "*faculty.contoso.com*"} -Priority 2
  ```

- Les groupes créés par d’autres personnes sont créés dans groups.contoso.com domaine. Utilisez la commande suivante :
    
  ```
  New-EmailAddressPolicy -Name OtherGroups -IncludeUnifiedGroupRecipients -EnabledPrimarySMTPAddressTemplate "SMTP:@groups.contoso.com" -Priority 3
  ```

## <a name="change-email-address-policies"></a>Modifier les stratégies d’adresse de messagerie

Pour modifier les modèles de priorité ou d’adresse de messagerie d’un EAP existant, utilisez la cmdlet Set-EmailAddressPolicy de messagerie.
  
```
Set-EmailAddressPolicy -Name StudentsGroups -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com", "smtp:@students.contoso.com" ManagedByFilter {Department -eq 'Students'} -Priority 2

```

La modification d’un EAP n’a aucun impact sur les groupes qui ont déjà été mis en service.
  
## <a name="delete-email-address-policies"></a>Supprimer des stratégies d’adresse de messagerie

Pour supprimer un EAP, utilisez l'Remove-EmailAddressPolicy cmdlet.
  
```
Remove-EmailAddressPolicy -Identity StudentsGroups
```

La modification d’un EAP n’a aucun impact sur les groupes qui ont déjà été mis en service.
  
## <a name="hybrid-requirements"></a>Exigences hybrides

Si votre organisation est configurée dans un scénario hybride, consultez Configurer des groupes [Microsoft 365](/exchange/hybrid-deployment/set-up-microsoft-365-groups) avec Exchange hybride local pour vous assurer que votre organisation répond aux exigences de création de groupes Microsoft 365. 
  
## <a name="additional-info-about-using-email-address-policies-groups"></a>Informations supplémentaires sur l’utilisation de groupes de stratégies d’adresse de messagerie :

Il y a d’autres choses à savoir :
  
- La rapidité de création des groupes dépend du nombre de P EAP configurés dans votre organisation.
    
- Les administrateurs et les utilisateurs peuvent également modifier des domaines lorsqu’ils créent des groupes.
    
- Le groupe d’utilisateurs est déterminé à l’aide des requêtes standard (propriétés utilisateur) qui sont déjà disponibles. Consultez [propriétés filtrables pour le paramètre -RecipientFilter](/powershell/exchange/recipientfilter-properties) pour les propriétés filtrables pris en charge. 
    
- Si vous ne configurez pas de PNE pour les groupes, le domaine accepté par défaut est sélectionné pour la création de groupes.
    
- Si vous supprimez un domaine accepté, vous devez d’abord mettre à jour les PED, sinon la mise en service de groupe sera impactée.
    
- Une limite maximale de 100 stratégies d’adresse de messagerie peut être configurée pour une organisation.
    
## <a name="related-content"></a>Contenu associé

[Planification pas à pas de la gouvernance de](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step) la collaboration (article)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md) (article)

[Créer un groupe Microsoft 365 dans le Centre d’administration](../admin/create-groups/create-groups.md) (article)