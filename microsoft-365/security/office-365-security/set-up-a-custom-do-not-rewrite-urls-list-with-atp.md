---
title: Configurer une liste d’URL do-not-Rewrite personnalisée à l’aide de liens fiables Office 365 ATP
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 08/29/2019
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 35dbfd99-da5a-422b-9b0e-c6caf3b645fa
ms.collection:
- M365-security-compliance
description: Lorsque vous configurez vos stratégies de liens approuvés ATP, vous pouvez inclure une liste d’URL do-not-Rewrite’pour permettre à certaines personnes de votre organisation de visiter des sites que vous incluez dans votre liste.
ms.openlocfilehash: 1068f7e2ac75f9c4403475e1fa9bc4da57fabe51
ms.sourcegitcommit: 70e920f76526f47fc849df615de4569e0ac2f4be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38032049"
---
# <a name="set-up-a-custom-do-not-rewrite-urls-list-using-office-365-atp-safe-links"></a>Configurer une liste d’URL do-not-Rewrite personnalisée à l’aide de liens fiables Office 365 ATP

> [!IMPORTANT]
> Cet article est destiné aux entreprises qui ont [Office 365 – Protection avancée contre les menaces](office-365-atp.md). Si vous êtes un utilisateur à domicile et que vous recherchez des informations sur les liens fiables dans Outlook, consultez la rubrique [Advanced Outlook.com Security](https://support.office.com/article/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

Avec [Office 365 Advanced Threat Protection](office-365-atp.md) (ATP), votre organisation peut avoir une [URL bloquée personnalisée](set-up-a-custom-blocked-urls-list-wtih-atp.md), de telle sorte que lorsque des utilisateurs cliquent sur des adresses Web (URL) dans des messages électroniques ou certains documents Office, ils ne peuvent pas atteindre ces URL. Votre organisation peut également avoir des listes personnalisées « ne pas réécrire » pour des groupes spécifiques de votre organisation. Une liste « ne pas réécrire » permet à certaines personnes de visiter des URL qui sont bloquées par [des liens fiables ATP dans Office 365](atp-safe-links.md). 
  
Cet article explique comment spécifier une liste d’URL exclues de l’analyse des liens fiables ATP et quelques points importants à garder à l’esprit.

## <a name="set-up-a-do-not-rewrite-list"></a>Configurer une liste « ne pas réécrire »

ATP Safe Links protection utilise plusieurs listes, y compris la liste des URL bloquées de votre organisation et les listes « ne pas réécrire » pour les exceptions. Si vous disposez des autorisations nécessaires, vous pouvez configurer vos listes personnalisées de « ne pas réécrire ». Vous effectuez cette opération lorsque vous ajoutez ou modifiez des stratégies de liens fiables qui s’appliquent à des destinataires spécifiques de votre organisation. 

Pour modifier (ou définir) des stratégies ATP, vous devez disposer d’un rôle approprié. Le tableau suivant contient quelques exemples. Pour en savoir plus, consultez [la rubrique autorisations dans le centre de conformité & Office 365 Security](permissions-in-the-security-and-compliance-center.md).

|Role  |WHERE/How Assigned  |
|---------|---------|
|Administrateur général Office 365 |La personne qui s’inscrit pour acheter Office 365 est un administrateur global par défaut. (Pour en savoir plus, consultez la rubrique [à propos des rôles d’administrateur Office 365](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles) .)         |
|Administrateur de sécurité |Centre d’administration Azure Active Directory[https://aad.portal.azure.com](https://aad.portal.azure.com)()|
|Gestion d’Organisation Exchange Online |Centre d’administration Exchange[https://outlook.office365.com/ecp](https://outlook.office365.com/ecp)() <br>ou <br>  Applets de commande PowerShell (consultez la rubrique [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps)) |

> [!TIP]
> Pour en savoir plus sur les rôles et les autorisations, consultez [la rubrique autorisations &amp; dans le centre de sécurité conformité Office 365](permissions-in-the-security-and-compliance-center.md).

### <a name="to-view-or-edit-a-custom-do-not-rewrite-urls-list"></a>Pour afficher ou modifier une liste d’URL « ne pas réécrire » personnalisée
  
1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous avec votre compte professionnel ou scolaire. 
    
2. Dans le volet de navigation de gauche, sous **liens fiables**de **stratégie** \> de **gestion** \> des menaces.
    
3. Dans la section **stratégies qui s’appliquent à des destinataires spécifiques** , sélectionnez **nouveau** (le nouveau bouton ressemble à **+** un signe plus ()) pour créer une stratégie. (Vous pouvez également modifier une stratégie existante.)<br/>![Sélectionnez nouveau pour ajouter une stratégie de liens fiables à des destinataires de messagerie spécifiques.](../media/01073f42-3cec-4ddb-8c10-4d33ec434676.png)
  
4. Spécifiez un nom et une description pour votre stratégie.
    
5. Dans la section **ne pas réécrire les URL suivantes** , sélectionnez la zone **Entrez une URL valide** , puis tapez une URL, puis cliquez sur le signe plus (+). 
    
6. Dans la section **appliqué à** , choisissez **le destinataire est membre de**, puis choisissez le ou les groupes que vous souhaitez inclure dans votre stratégie. Choisissez **Ajouter**, puis choisissez **OK**.
    
7. Lorsque vous avez terminé d’ajouter des URL, dans le coin inférieur droit de l’écran, sélectionnez **Enregistrer**.
    
> [!NOTE]
> Veillez à consulter la liste personnalisée des URL bloquées de votre organisation. Consultez [la rubrique Configurer une liste d’URL bloquées personnalisées à l’aide de liens fiables ATP](set-up-a-custom-blocked-urls-list-wtih-atp.md). 
  
## <a name="important-points-to-keep-in-mind"></a>Points importants à garder à l’esprit

- Toutes les URL que vous spécifiez dans la liste « ne pas réécrire » sont exclues de la recherche de liens fiables ATP pour les destinataires que vous spécifiez.
 
- Si vous disposez déjà d’une liste d’URL dans la liste « ne pas réécrire », veillez à la consulter et à ajouter des caractères génériques, le cas échéant. Par exemple, si votre liste existante a une entrée like `https://contoso.com/a` et que vous souhaitez inclure des sous-chemins `https://contoso.com/a/b` comme dans votre stratégie, ajoutez un caractère générique à votre entrée afin qu' `https://contoso.com/a/*`elle se présente de la manière souhaitée.
    
- N’incluez pas une barre oblique (/) dans les URL que vous spécifiez dans la liste « ne pas réécrire ». Par exemple, au lieu d' `contoso.com/` entrer dans la liste « ne pas réécrire », `contoso.com`entrez.

- Lorsque vous spécifiez la liste « ne pas réécrire » pour une stratégie de liens approuvés ATP, vous pouvez inclure jusqu’à trois astérisques\*génériques (). Les caractères génériques\*() sont utilisés pour inclure explicitement des préfixes ou des sous `https://` - `https://`domaines, comme ou. Une entrée, telle que `contoso.com` n’est pas la même `*.contoso.com/*` que pour la liste « ne pas réécrire ». Vous devez disposer `*.contoso.com/*` de si vous voulez autoriser les utilisateurs à visiter un domaine et ses sous-domaines et chemins d’accès.
    
Le tableau suivant répertorie des exemples de ce que vous pouvez entrer et de l’effet de ces entrées.
    
|**Exemple d’entrée**|**Ce qu’il fait**|
|:-----|:-----|
|`contoso.com`|Permet aux destinataires de visiter un `https://contoso.com` site, mais pas des sous-domaines ou des chemins d’accès.|
|`*.contoso.com/*`  <br/> |Permet aux destinataires de visiter un domaine, des sous-domaines et des chemins `https://www.contoso.com`d' `https://www.contoso.com`accès `https://maps.contoso.com`, par exemple,, ou`https://www.contoso.com/a`  <br/> |
|`https://contoso.com/a`  <br/> |Permet à des destinataires spécifiques de visiter `https://contoso.com/a`un site, mais pas des sous-chemins comme`https://contoso.com/a/b`  <br/> |
|`https://contoso.com/a/*`  <br/> |Permet à des destinataires spécifiques de visiter `https://contoso.com/a` un site comme des sous-chemins comme`https://contoso.com/a/b`  <br/> |
   
 
