---
title: Choisir le domaine à utiliser lors de la création de groupes Microsoft 365
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 7cf5655d-e523-4bc3-a93b-3ccebf44a01a
recommendations: false
description: Apprenez à choisir le domaine à utiliser lors de la création de groupes Microsoft 365 en configurant des stratégies d’adresse e-mail à l’aide de PowerShell.
ms.openlocfilehash: 7e24df7e508f3ebfd09fce26bc8ebb98faefb72d
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67730460"
---
# <a name="choose-the-domain-to-use-when-creating-microsoft-365-groups"></a>Choisir le domaine à utiliser lors de la création de groupes Microsoft 365

Certaines organisations utilisent des domaines de messagerie distincts pour segmenter différentes parties de leurs activités. Vous pouvez spécifier le domaine à utiliser lorsque vos utilisateurs créent des groupes Microsoft 365.
  
Si votre organisation a besoin que les utilisateurs créent leurs groupes dans des domaines autres que le domaine accepté par défaut de votre entreprise, vous pouvez l’autoriser en configurant des stratégies d’adresse e-mail (EAP) à l’aide de PowerShell.

Avant de pouvoir exécuter les applets de commande PowerShell, téléchargez et installez un module qui vous permettra de communiquer avec votre organisation. Consultez [Se connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="example-scenarios"></a>Exemples de scénarios

Supposons que le domaine principal de votre entreprise est Contoso.com. Mais le domaine accepté par défaut de votre organisation est service.contoso.com. Cela signifie que des groupes seront créés dans service.contoso.com (par exemple, jimsteam@service.contoso.com).
  
Supposons que vous avez également des sous-domaines configurés dans votre organisation. Vous souhaitez également créer des groupes dans ces domaines :
  
- students.contoso.com pour les étudiants
    
- faculty.contoso.com pour les membres du corps professoral
    
Les deux scénarios suivants expliquent comment procéder.

> [!NOTE]
> Lorsque vous avez des paillis EAP, ils sont évalués dans l’ordre de priorité. Une valeur de 1 signifie la priorité la plus élevée. Une fois qu’un EAP correspond, aucun EAP supplémentaire n’est évalué et les adresses qui sont estampillées sur le groupe sont conformes à l’EAP correspondant. > Si aucun contrat EAP ne correspond aux critères spécifiés, le groupe est approvisionné dans le domaine accepté par défaut de l’organisation. Pour plus d’informations sur l’ajout d’un domaine [accepté, consultez Gérer les domaines acceptés dans Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
  
### <a name="scenario-1"></a>Scénario 1

L’exemple suivant vous montre comment approvisionner tous les groupes Microsoft 365 de votre organisation dans le domaine groups.contoso.com.
  
```
New-EmailAddressPolicy -Name Groups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@groups.contoso.com" -Priority 1
```

### <a name="scenario-2"></a>Scénario 2

Supposons que vous souhaitez contrôler les sous-domaines dans lesquels les groupes Microsoft 365 sont créés. Vous souhaitez :
  
- Groupes créés par les étudiants (utilisateurs dont **le service** est défini sur **Étudiants**) dans le domaine students.groups.contoso.com. Utilisez la commande suivante :
    
  ```
  New-EmailAddressPolicy -Name StudentsGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Students'} -Priority 1
  ```

- Groupes créés par les membres du corps professoral (utilisateurs dont **le département** est défini sur **Faculty ou adresse e-mail contient faculty.contoso.com)**) dans le domaine faculty.groups.contoso.com. Utilisez la commande suivante :
    
  ```
  New-EmailAddressPolicy -Name FacultyGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@faculty.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Faculty' -or EmailAddresses -like "*faculty.contoso.com*"} -Priority 2
  ```

- Les groupes créés par toute autre personne sont créés dans le domaine groups.contoso.com. Utilisez la commande suivante :
    
  ```
  New-EmailAddressPolicy -Name OtherGroups -IncludeUnifiedGroupRecipients -EnabledPrimarySMTPAddressTemplate "SMTP:@groups.contoso.com" -Priority 3
  ```
> [!NOTE]
> Ce scénario ne fonctionne pas lorsque l’enregistrement MX pointe vers un filtrage de courrier indésirable tiers.
 
## <a name="change-email-address-policies"></a>Modifier les stratégies d’adresse e-mail

Pour modifier les modèles de priorité ou d’adresse e-mail d’un EAP existant, utilisez l’applet de commande Set-EmailAddressPolicy.
  
```
Set-EmailAddressPolicy -Name StudentsGroups -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com", "smtp:@students.contoso.com" ManagedByFilter {Department -eq 'Students'} -Priority 2

```

La modification d’un EAP n’a aucun impact sur les groupes qui ont déjà été approvisionnés.
  
## <a name="delete-email-address-policies"></a>Supprimer des stratégies d’adresse e-mail

Pour supprimer un EAP, utilisez l’applet de commande Remove-EmailAddressPolicy.
  
```
Remove-EmailAddressPolicy -Identity StudentsGroups
```

La modification d’un EAP n’a aucun impact sur les groupes qui ont déjà été approvisionnés.
  
## <a name="hybrid-requirements"></a>Configuration hybride requise

Si votre organisation est configurée dans un scénario hybride, consultez [Configurer des groupes Microsoft 365 avec Exchange hybride local](/exchange/hybrid-deployment/set-up-microsoft-365-groups) pour vous assurer que votre organisation répond aux exigences de création de groupes Microsoft 365. 
  
## <a name="additional-info-about-using-email-address-policies-groups"></a>Informations supplémentaires sur l’utilisation des groupes de stratégies d’adresse e-mail :

Il y a quelques autres choses à savoir :
  
- La rapidité de création des groupes dépend du nombre de eaps configurés dans votre organisation.
    
- Les administrateurs et les utilisateurs peuvent également modifier des domaines lorsqu’ils créent des groupes.
    
- Le groupe d’utilisateurs est déterminé à l’aide des requêtes standard (propriétés utilisateur) qui sont déjà disponibles. Consultez [les propriétés filtrables du paramètre -RecipientFilter](/powershell/exchange/recipientfilter-properties) pour les propriétés filtrables prises en charge. 
    
- Si vous ne configurez pas de eaps pour les groupes, le domaine accepté par défaut est sélectionné pour la création de groupe.
    
- Si vous supprimez un domaine accepté, vous devez d’abord mettre à jour les eaps. Sinon, l’approvisionnement de groupe sera affecté.
    
- Une limite maximale de 100 stratégies d’adresse e-mail peut être configurée pour une organisation.
    
## <a name="related-content"></a>Contenu associé

[Recommandations de planification de la gouvernance de collaboration](collaboration-governance-overview.md#collaboration-governance-planning-recommendations) (article)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md) (article)

[Créer un groupe Microsoft 365 dans le centre d’administration](../admin/create-groups/create-groups.md) (article)
