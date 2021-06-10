---
title: 'Stratégies de document sécurisées recommandées : Microsoft 365 pour les | Documents Microsoft'
description: Décrit les recommandations de Microsoft sur l’application de stratégies de sécurisation de l’accès aux fichiers SharePoint.
ms.author: josephd
author: JoeDavies-MSFT
manager: Laurawi
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 1771f71e444233ffce60a4a56273d3062fe8b70d
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51203944"
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>Recommandations de stratégie pour la sécurisation SharePoint sites et fichiers

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- SharePoint Online 


Cet article explique comment implémenter les stratégies recommandées d’identité et d’accès aux appareils pour protéger SharePoint et OneDrive Entreprise. Ces instructions s’appuient sur les stratégies [communes d’accès aux identités et aux appareils.](identity-access-policies.md)

Ces recommandations sont basées sur trois niveaux différents de sécurité et de protection pour les fichiers SharePoint qui peuvent être appliqués en fonction de la granularité de vos besoins **:** base de **référence,** sensible et hautement réglementé **.** Vous pouvez en savoir plus sur ces niveaux de sécurité et les systèmes d’exploitation clients recommandés, référencés par ces recommandations [dans la vue d’ensemble.](microsoft-365-policies-configurations.md)

Outre la mise en œuvre de ces instructions, assurez-vous de configurer les sites SharePoint avec le niveau de protection approprié, y compris la définition des autorisations appropriées pour le contenu sensible et hautement réglementé.

## <a name="updating-common-policies-to-include-sharepoint-and-onedrive-for-business"></a>Mise à jour des stratégies courantes pour inclure SharePoint et OneDrive Entreprise

Pour protéger les fichiers dans SharePoint et OneDrive, le diagramme suivant illustre les stratégies à mettre à jour à partir des stratégies communes d’accès aux appareils et aux identités.

[![Résumé des mises à jour de stratégie pour la protection de l’accès à Teams et à ses services dépendants](../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png)

Si vous avez inclus SharePoint lorsque vous avez créé les stratégies communes, vous devez uniquement créer les nouvelles stratégies. Pour les stratégies d’accès conditionnel, SharePoint inclut OneDrive.

Les nouvelles stratégies implémentent la protection des appareils pour le contenu sensible et hautement réglementé en appliquant des exigences d’accès spécifiques SharePoint sites que vous spécifiez.

Le tableau suivant répertorie les stratégies que vous devez réviser et mettre à jour ou créer des stratégies pour SharePoint. Les stratégies courantes sont liées aux instructions de configuration associées dans l’article [Stratégies](identity-access-policies.md) communes d’identité et d’accès aux appareils.

|Niveau de protection|Stratégies|Plus d’informations|
|---|---|---|
|**Baseline**|[Exiger l’mf lorsque le risque de se connecte *est moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Incluez SharePoint dans l’affectation des applications cloud.|
||[Bloquer les clients ne prenant pas en charge l’authentification moderne](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Incluez SharePoint dans l’affectation des applications cloud.|
||[Appliquer des stratégies de protection des données APP](identity-access-policies.md#apply-app-data-protection-policies)|Assurez-vous que toutes les applications recommandées sont incluses dans la liste des applications. Assurez-vous de mettre à jour la stratégie pour chaque plateforme (iOS, Android, Windows).|
||[Exiger des PC conformes](identity-access-policies.md#require-compliant-pcs-but-not-compliant-phones-and-tablets)|Inclure SharePoint dans la liste des applications cloud.|
||[Utiliser les restrictions appliquées par l’application dans SharePoint](#use-app-enforced-restrictions-in-sharepoint)|Ajoutez cette nouvelle stratégie. Cela indique Azure Active Directory (Azure AD) d’utiliser les paramètres spécifiés dans SharePoint. Cette stratégie s’applique à tous les utilisateurs, mais affecte uniquement l’accès aux sites inclus SharePoint stratégies d’accès.|
|**Sensible**|[Exiger l’mf lorsque le risque de se connecte *est faible,* *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Incluez SharePoint dans les affectations des applications cloud.|
||[Exiger des PC et *des appareils* mobiles conformes](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Incluez SharePoint dans la liste des applications cloud.|
||[SharePoint de contrôle d’accès](#sharepoint-access-control-policies): autoriser l’accès par navigateur uniquement à des sites SharePoint spécifiques à partir d’appareils non utilisés.|Cela empêche la modification et le téléchargement des fichiers. Utilisez PowerShell pour spécifier des sites.|
|**Hautement réglementé**|[*Toujours exiger* l’mf d’fa](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Incluez SharePoint dans l’affectation des applications cloud.|
||[SharePoint de contrôle d’accès](#use-app-enforced-restrictions-in-sharepoint): bloquer l’accès à des sites SharePoint spécifiques à partir d’appareils non utilisés.|Utilisez PowerShell pour spécifier des sites.|
|

## <a name="use-app-enforced-restrictions-in-sharepoint"></a>Utiliser les restrictions appliquées par l’application dans SharePoint

Si vous implémentez des contrôles d’accès dans SharePoint, vous devez créer cette stratégie d’accès conditionnel dans Azure AD pour indiquer à Azure AD d’appliquer les stratégies que vous configurez dans SharePoint. Cette stratégie s’applique à tous les utilisateurs, mais affecte uniquement l’accès aux sites que vous spécifiez à l’aide de PowerShell lorsque vous créez les contrôles d’accès dans SharePoint.

Pour configurer cette stratégie, voir « Bloquer ou limiter l’accès à des collections de sites SharePoint ou des comptes OneDrive spécifiques » dans Contrôler l’accès à partir d’appareils non [utilisés.](/sharepoint/control-access-from-unmanaged-devices)

## <a name="sharepoint-access-control-policies"></a>SharePoint de contrôle d’accès

Microsoft vous recommande de protéger le contenu des sites SharePoint avec du contenu sensible et hautement réglementé avec des contrôles d’accès aux appareils. Pour ce faire, créez une stratégie qui spécifie le niveau de protection et les sites à appliquer à la protection.

- Sites sensibles : autoriser l’accès au navigateur uniquement. Cela empêche les utilisateurs de modifier et de télécharger des fichiers.
- Sites hautement réglementés : bloquer l’accès à partir d’appareils nonmanagés.

Voir « Bloquer ou limiter l’accès à des collections SharePoint sites ou des comptes OneDrive spécifiques » dans Contrôler l’accès à partir d’appareils non [utilisés.](/sharepoint/control-access-from-unmanaged-devices)

## <a name="how-these-policies-work-together"></a>Fonctionnement de ces stratégies ensemble

Il est important de comprendre que les autorisations SharePoint site sont généralement basées sur les besoins de l’entreprise pour accéder aux sites. Ces autorisations sont gérées par les propriétaires de site et peuvent être très dynamiques. L SharePoint des stratégies d’accès aux appareils garantit la protection de ces sites, que les utilisateurs soient affectés à un groupe Azure AD associé à une protection de référence, sensible ou hautement réglementée.

L’illustration suivante montre comment les stratégies SharePoint’accès aux appareils protègent l’accès aux sites d’un utilisateur.

[![Exemple de protection des sites SharePoint d’accès aux appareils](../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png)

[Voir une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png)

Des stratégies d’accès conditionnel de base sont affectées à Jean, mais il peut avoir accès à des sites SharePoint avec une protection sensible ou hautement réglementée.

- Si Jean accède à un site sensible ou hautement réglementé, il est membre de l’utilisation de son PC, son accès est accordé tant que son PC est conforme.
- Si Jean accède à un site sensible, il est membre de son téléphone non utilisé, ce qui est autorisé pour les utilisateurs de référence, il reçoit un accès en navigateur uniquement au site sensible en raison de la stratégie d’accès aux appareils configurée pour ce site.
- Si Jean accède à un site hautement réglementé, il est membre de son téléphone non utilisé, il sera bloqué en raison de la stratégie d’accès configurée pour ce site. Il peut accéder à ce site uniquement à l’aide de son PC géré et conforme.

## <a name="next-step"></a>Étape suivante

![Étape 4 : Stratégies pour Microsoft 365 applications cloud](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

Configurer des stratégies d’accès conditionnel pour :

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)