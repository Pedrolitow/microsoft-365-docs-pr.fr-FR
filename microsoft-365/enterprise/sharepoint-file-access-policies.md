---
title: Stratégies recommandées pour la sécurisation des e-mails -Microsoft 365 Entreprise | Microsoft Docs
description: Décrit les recommandations de Microsoft sur l’application de stratégies de sécurisation de l’accès aux fichiers SharePoint.
author: BrendaCarter
manager: laurawi
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.author: bcarter
ms.date: 06/07/2018
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.openlocfilehash: 2f5658146df3da7cc28c907b33e5035a84628fc5
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867124"
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>Recommandations de stratégies pour sécuriser les sites et les fichiers SharePoint
Cet article explique comment implémenter l’identité recommandée et les stratégies d’accès de périphérique pour protéger SharePoint Online et OneDrive for Business. Ce guide s’appuie sur l' [identité commune et des stratégies d’accès de périphérique](identity-access-policies.md). 


Ces recommandations sont basées sur trois différents niveaux de sécurité et protection pour les fichiers SharePoint qui peut être appliqué en fonction de la granularité de vos besoins : **planifié**, **sensibles**et **hautement régulé**. Pour plus d’informations sur les niveaux de sécurité et les systèmes d’exploitation client recommandé, référencés par ces recommandations dans [vue d’ensemble](microsoft-365-policies-configurations.md).

Outre l’implémentation de ce guide, veillez à configurer des sites SharePoint avec le montant de protection, y compris en vous assurant d’autorisations pour les contenus sensibles et réglementation sont appropriés. Pour plus d’informations sur la création de sites pour la protection sensibles et réglementation de planification, voir [fichiers et des sites d’informations sécurisé SharePoint Online](https://docs.microsoft.com/office365/enterprise/secure-sharepoint-online-sites-and-files). 

## <a name="updating-common-policies-to-include-sharepoint-and-onedrive-for-business"></a>Mise à jour des stratégies courantes pour inclure SharePoint et OneDrive entreprise
Le diagramme suivant illustre le jeu de stratégies recommandées pour la protection des fichiers dans SharePoint Online et OneDrive for Business. Elle indique quelles stratégies seront mis à jour ou nouvellement créés pour ajouter une protection pour SharePoint Online et OneDrive for Business.

![Résumé des stratégies de SharePoint Online et OneDrive](../images/identity-access-ruleset-sharepoint.png)

Si vous avez inclus SharePoint Online lorsque vous avez créé les stratégies courantes, vous devez uniquement créer les nouveau polcies. Lorsque vous configurez les règles d’accès conditionnel, SharePoint Online inclut OneDrive for Business.

Les nouvelles stratégies implémentent la protection de périphérique pour du contenu sensible et réglementation en appliquant les exigences d’accès spécifiques aux sites SharePoint que vous spécifiez. 

 Le tableau suivant répertorie les stratégies que vous devez vérifier et mettre à jour ou créer de nouveaux pour SharePoint Online. Les stratégies courantes lien vers les instructions de configuration associée dans l’article [identité commune et des périphériques accéder aux stratégies](identity-access-policies.md) (liens bientôt disponible).


|Niveau de protection|Policies|Plus d’informations|
|:---------------|:-------|:----------------|
|**Baseline**|[Exiger MFA lors de la connexion risque est *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Inclure SharePoint Online dans les affectations d’applications dans le nuage.|
|        |[Blocage des clients qui ne prennent pas en charge l’authentification moderne](identity-access-policies.md#block-clients-that-dont-support-modern-authentication)|Inclure SharePoint Online dans les affectations d’applications dans le nuage.|
|        |[Définir des stratégies de protection des applications](identity-access-policies.md#define-app-protection-policies)|Assurez-vous que toutes les applications recommandées sont incluses dans la liste des applications. Veillez à mettre à jour la stratégie pour chaque plateforme (iOS, Android, Windows).|
|        |[Exiger compatible PC](identity-access-policies.md#require-compliant-pcs-but-not-compliant-phones-and-tablets)|Inclure SharePoint Online dans la liste des applications dans le nuage.|
|        |[Utiliser les restrictions de l’application appliquée dans SharePoint Online](#use-app-enforced-restrictions-in-sharepoint-online)|Ajoutez cette nouvelle stratégie. Ceci indique à Azure AD pour utiliser les paramètres spécifiés dans SharePoint Online. Cette règle s’applique à tous les utilisateurs, mais n’affecte que l’accès aux sites inclus dans SharePoint Online stratégies d’accès.
|**Sensible**|[Exiger MFA lors de la connexion risque est *faible*, *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)| Inclure SharePoint Online dans les affectations d’applications dans le nuage.|
|         |[Exiger compatible PC *et* appareils mobiles](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Inclure SharePoint Online dans la liste des applications dans le nuage.|
||[Stratégie de contrôle d’accès SharePoint Online](#sharepoint-online-access-control-policies): autoriser l’accès navigateur uniquement à des sites SharePoint spécifiques à partir des périphériques non gérés|Ainsi, modifier et télécharger des fichiers. Utiliser PowerShell pour spécifier les sites.|
|**Hautement réglementé**|[*Toujours* requrie MFA](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Inclure SharePoint Online dans les affectations d’applications dans le nuage. |
||[Stratégie de contrôle d’accès SharePoint Online](#use-app-enforced-restrictions-in-sharepoint-online): Bloquez l’accès à des sites SharePoint spécifiques à partir des périphériques non gérés|Utilisation de PowerShell pour spécifier les sites.|

## <a name="use-app-enforced-restrictions-in-sharepoint-online"></a>Utiliser les restrictions de l’application appliquée dans SharePoint Online
Si vous implémentez des contrôles d’accès dans SharePoint Online, vous devez créer cette stratégie d’accès conditionnel dans Azure AD pour indiquer à Azure AD pour appliquer les stratégies que vous configurez dans SharePoint Online. Cette règle s’applique à tous les utilisateurs, mais n’affecte que l’accès aux sites que vous spécifiez à l’aide de PowerShell lorsque vous créez les contrôles d’accès dans SharePoint Online.

Pour configurer cette, consultez stratégie « bloquer ou limiter l’accès à des collections de sites SharePoint spécifiques ou de comptes OneDrive » dans cet article : [contrôler l’accès à partir des périphériques non gérés](https://support.office.com/article/Control-access-from-unmanaged-devices-5ae550c4-bd20-4257-847b-5c20fb053622).


## <a name="sharepoint-online-access-control-policies"></a>Stratégies de contrôle d’accès SharePoint Online
Microsoft recommande de que vous protégez le contenu dans des sites SharePoint avec un contenu sensible et hautement régulé avec les contrôles d’accès aux périphériques. Pour cela, en créant une stratégie qui spécifie le niveau de protection et des sites pour appliquer la protection. 
- Sites sensibles : autoriser l’accès navigateur uniquement. Cela empêche les utilisateurs de modifier et de télécharger des fichiers.
- Hautement régulé sites — bloquez l’accès à partir des périphériques non gérés.

Voir « bloquer ou limiter l’accès à des collections de sites SharePoint spécifiques ou de comptes OneDrive » dans cet article : [contrôler l’accès à partir des périphériques non gérés](https://support.office.com/article/Control-access-from-unmanaged-devices-5ae550c4-bd20-4257-847b-5c20fb053622) . 

## <a name="how-these-policies-work-together"></a>Comment ces stratégies fonctionnent ensemble
Il est important de comprendre que les autorisations de site SharePoint sont généralement basées sur les besoins de l’entreprise pour accéder aux sites. Ces autorisations sont gérées par les propriétaires de site et peuvent être très dynamiques. À l’aide de SharePoint, des stratégies d’accès périphérique assure la protection pour ces sites, quelle que soit si les utilisateurs sont affectés à un groupe d’Azure AD associé planifié, sensible, ou hautement régulé protection. 

L’illustration suivante fournit un exemple de protègent des accès aux sites SharePoint des stratégies d’accès périphérique.

![Comment protègent les sites SharePoint des stratégies d’accès périphérique](../images/SharePoint-rules-scenario.png)

Dans cette illustration :
- James est affecté aux stratégies d’accès conditionnel liés à la protection de base, mais il peut être indiquée accès aux sites SharePoint liés à la protection sensible ou réglementation. 
- Si James accède à un site sensible ou réglementation il appartient à l’aide de son PC, son accès est accordé tant que son ordinateur est conforme.
- Si James accède à un site sensible, qu'il est un membre de l’utilisation de son téléphone non géré, qui est autorisé pour les utilisateurs de base, il reçoit l’accès navigateur uniquement au site sensible en raison de la stratégie d’accès de périphériques configuré pour ce site. 
- Si James accède à un site réglementation il appartient à l’aide de son téléphone non managé, il sera bloqué en raison de la stratégie d’accès configurée pour ce site. Il peut uniquement accéder à ce site à l’aide de son PC géré et de conformité.


<!---
##Block access to content from unmanaged devices (SharePoint admin center)
In the case of SharePoint Online, when a conditional access policy is applied to enforce Intune app protection policies, this might not apply to all applications that access SharePoint Online. Some applications, such as Exchange, have access to some SharePoint resources. For example, Exchange allows attaching SharePoint files by default. Conditional access policies applied to SharePoint Online will not restrict this access. 

To ensure baseline protection is applied uniformly, regardless of which service is accessing SharePoint Online and OneDrive for Business, configure access controls directly in SharePoint admin center. We recommend you configure the following:
- Block access from unmanaged devices. This includes devices that aren't compliant or joined to a domain. 
- Block access from app that don't use modern authentication.

See [Control access from unmanaged devices](https://support.office.com/article/Control-access-from-unmanaged-devices-5ae550c4-bd20-4257-847b-5c20fb053622).
-->



## <a name="next-steps"></a>Étapes suivantes
[Sécuriser les fichiers et sites SharePoint Online](https://docs.microsoft.com/office365/enterprise/secure-sharepoint-online-sites-and-files)
