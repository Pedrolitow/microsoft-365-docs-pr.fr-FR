---
title: Choisir le domaine à utiliser lors de la création de groupes Microsoft 365
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7cf5655d-e523-4bc3-a93b-3ccebf44a01a
description: 'Découvrez comment choisir le domaine à utiliser lors de la création de groupes Microsoft 365 en configurant des stratégies d’adresse de messagerie à l’aide de PowerShell. '
ms.openlocfilehash: 19caa4f4dfdef4895fa58f8bf5c198269844044f
ms.sourcegitcommit: 9550298946f8accb90cd59be7b46b71d4bf4f8cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2020
ms.locfileid: "46597376"
---
# <a name="choose-the-domain-to-use-when-creating-microsoft-365-groups"></a>Choisir le domaine à utiliser lors de la création de groupes Microsoft 365

 Certaines organisations utilisent des domaines de messagerie distincts pour segmenter différentes parties de leurs activités. Vous pouvez spécifier le domaine à utiliser lorsque vos utilisateurs créent des groupes Microsoft 365.
  
Si votre organisation a besoin que les utilisateurs créent leurs groupes dans des domaines autres que le domaine accepté par défaut de votre entreprise, vous pouvez autoriser cela en configurant des stratégies d’adresse de messagerie (EAPs) à l’aide de PowerShell.
  
Avant de pouvoir exécuter les applets de commande PowerShell, téléchargez et installez un module qui vous permettra de communiquer avec votre organisation. Consultez [connexion à Exchange Online à l’aide de Remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=785881).
  
## <a name="example-scenarios"></a>Exemples de scénarios

Supposons que le domaine principal de votre entreprise est Contoso.com. Mais le domaine accepté par défaut de votre organisation est service.contoso.com. Cela signifie que les groupes seront créés dans service.contoso.com (par exemple, jimsteam@service.contoso.com).
  
Imaginons que vous avez également des sous-domaines configurés dans votre organisation. Vous souhaitez créer des groupes dans ces domaines également :
  
- students.contoso.com pour les étudiants
    
- faculty.contoso.com pour les membres du corps enseignant
    
Les deux scénarios suivants expliquent comment effectuer cette procédure.
  
> [!NOTE]
> Lorsque vous avez plusieurs EAPs, elles sont évaluées dans l’ordre de priorité. La valeur 1 correspond à la priorité la plus élevée. Une fois qu’un EAP répond, aucune autre EAP n’est évaluée et les adresses qui sont marquées sur le groupe sont telles que le protocole EAP correspondant. > si aucune EAPs ne correspond aux critères spécifiés, le groupe est mis en service dans le domaine accepté par défaut de l’organisation. Consultez la [gestion des domaines acceptés dans Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=785428) pour plus d’informations sur l’ajout d’un domaine accepté. 
  
### <a name="scenario-1"></a>Scénario 1

L’exemple suivant montre comment mettre en service tous les groupes Microsoft 365 de votre organisation dans le domaine groups.contoso.com.
  
```
New-EmailAddressPolicy -Name Groups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@groups.contoso.com" -Priority 1
```

### <a name="scenario-2"></a>Scénario 2

Supposons que vous souhaitez contrôler les sous-domaines dans lesquels les groupes Microsoft 365 sont créés. Vous souhaitez :
  
- Groupes créés par les étudiants (utilisateurs dont le **service** est défini sur les **étudiants**) dans le domaine students.groups.contoso.com. Utilisez la commande suivante :
    
  ```
  New-EmailAddressPolicy -Name StudentsGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Students'} -Priority 1
  ```

- Groupes créés par les membres de l’Université (les utilisateurs dont le **service** est défini sur **Université ou adresse e-mail contiennent Faculty.contoso.com)**) dans le domaine Faculty.groups.contoso.com. Utilisez la commande suivante :
    
  ```
  New-EmailAddressPolicy -Name FacultyGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@faculty.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Faculty' -or EmailAddresses -like "*faculty.contoso.com*"} -Priority 2
  ```

- Tous les autres utilisateurs du domaine groups.contoso.com. Utilisez la commande suivante :
    
  ```
  New-EmailAddressPolicy -Name OtherGroups -IncludeUnifiedGroupRecipients -EnabledPrimarySMTPAddressTemplate "SMTP:@groups.contoso.com" -Priority 3
  ```

## <a name="change-email-address-policies"></a>Modifier les stratégies d’adresse de messagerie

Pour modifier les modèles de priorité ou d’adresse de messagerie d’un protocole EAP existant, utilisez la cmdlet Set-EmailAddressPolicy.
  
```
Set-EmailAddressPolicy -Name StudentsGroups -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com", "smtp:@students.contoso.com" ManagedByFilter {Department -eq 'Students'} -Priority 2

```

La modification d’un protocole EAP n’a pas d’impact sur les groupes qui ont déjà été configurés.
  
## <a name="delete-email-address-policies"></a>Supprimer des stratégies d’adresse de messagerie

Pour supprimer un protocole EAP, utilisez la cmdlet Remove-EmailAddressPolicy.
  
```
Remove-EmailAddressPolicy -Identity StudentsGroups
```

La modification d’un protocole EAP n’a pas d’impact sur les groupes qui ont déjà été configurés.
  
## <a name="hybrid-requirements"></a>Exigences hybrides

Si votre organisation est configurée dans un scénario hybride, consultez [configurer les groupes microsoft 365 avec l’environnement Exchange hybride local](https://docs.microsoft.com/exchange/hybrid-deployment/set-up-microsoft-365-groups) pour vous assurer que votre organisation remplit les conditions requises pour la création de groupes Microsoft 365. 
  
## <a name="additional-info-about-using-email-address-policies-groups"></a>Informations supplémentaires sur l’utilisation des groupes de stratégies d’adresse de messagerie :

Voici quelques éléments à prendre en compte :
  
- La manière dont les groupes rapides sont créés dépend du nombre de EAPs configurés dans votre organisation.
    
- Les administrateurs et les utilisateurs peuvent également modifier les domaines lorsqu’ils créent des groupes.
    
- Le groupe d’utilisateurs est déterminé à l’aide des requêtes standard (propriétés de l’utilisateur) qui sont déjà disponibles. Consultez [les propriétés filtrables pour le paramètre-RecipientFilter pour les](https://go.microsoft.com/fwlink/p/?LinkId=785918) propriétés filtrables prises en charge. 
    
- Si vous ne configurez aucun EAPs pour les groupes, le domaine accepté par défaut est sélectionné pour la création de groupe.
    
- Si vous supprimez un domaine accepté, vous devez d’abord mettre à jour le EAPs, sinon la mise en service de groupe sera affectée.
    
- Une limite maximale de 100 stratégies d’adresse de messagerie peut être configurée pour une organisation.
    
## <a name="related-articles"></a>Articles connexes

[Créer un groupe Microsoft 365 dans le centre d’administration](create-groups.md)
