---
title: Stratégies recommandées pour la sécurisation des documents-Microsoft 365 pour les entreprises | Microsoft docs
description: Décrit les recommandations de Microsoft sur l’application de stratégies de sécurisation de l’accès aux fichiers SharePoint.
ms.author: josephd
author: JoeDavies-MSFT
manager: Laurawi
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
ms.openlocfilehash: 3235046a9c3decf441a14fb05519ddd5806ba8f0
ms.sourcegitcommit: cd17328baa58448214487e3e68c37590ab9fd08d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "48399713"
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>Recommandations de stratégie pour sécuriser les sites et les fichiers SharePoint

Cet article explique comment implémenter les stratégies d’identité et d’accès aux appareils recommandées pour protéger SharePoint et OneDrive entreprise. Ce guide s’appuie sur les [stratégies courantes d’identité et d’accès aux appareils](identity-access-policies.md).

Ces recommandations sont basées sur trois niveaux de sécurité et de protection pour les fichiers SharePoint qui peuvent être appliqués en fonction de la granularité de vos besoins : **ligne de base**, **sensibles**et **hautement réglementés**. Pour en savoir plus sur ces niveaux de sécurité et sur les systèmes d’exploitation clients recommandés, ces recommandations sont indiquées dans [la vue d’ensemble](microsoft-365-policies-configurations.md).

En plus de mettre en œuvre ces instructions, veillez à configurer les sites SharePoint avec le bon niveau de protection, notamment en définissant les autorisations appropriées pour le contenu sensible et hautement réglementé.

## <a name="updating-common-policies-to-include-sharepoint-and-onedrive-for-business"></a>Mise à jour de stratégies communes pour inclure SharePoint et OneDrive entreprise

Pour protéger les fichiers dans SharePoint et OneDrive, le diagramme suivant illustre les stratégies à mettre à jour à partir des stratégies courantes d’identité et d’accès aux appareils.

[![Résumé des mises à jour de stratégie pour protéger l’accès à teams et à ses services dépendants](../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png)

[Afficher une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png)

Si vous avez inclus SharePoint lorsque vous avez créé les stratégies communes, il vous suffit de créer les nouvelles stratégies. Pour les stratégies d’accès conditionnel, SharePoint inclut OneDrive.

Les nouvelles stratégies mettent en œuvre la protection des appareils pour le contenu sensible et hautement réglementé en appliquant des exigences d’accès spécifiques aux sites SharePoint que vous spécifiez.

Le tableau suivant répertorie les stratégies dont vous avez besoin pour vérifier et mettre à jour ou créer des éléments pour SharePoint. Les stratégies courantes lient aux instructions de configuration associées dans l’article [Common Identity and Device Access Policies](identity-access-policies.md) .

|Niveau de protection|Stratégies|Plus d’informations|
|:---------------|:-------|:----------------|
|**Baseline**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Incluez SharePoint dans l’affectation d’applications Cloud.|
|        |[Bloquer les clients ne prenant pas en charge l’authentification moderne](identity-access-policies.md#block-clients-that-dont-support-modern-authentication)|Incluez SharePoint dans l’affectation d’applications Cloud.|
|        |[Appliquer des stratégies de protection des données d’application](identity-access-policies.md#apply-app-data-protection-policies)|Assurez-vous que toutes les applications recommandées sont incluses dans la liste des applications. Veillez à mettre à jour la stratégie pour chaque plateforme (iOS, Android, Windows).|
|        |[Exiger des PC conformes](identity-access-policies.md#require-compliant-pcs-but-not-compliant-phones-and-tablets)|Incluez SharePoint dans la liste des applications Cloud.|
|        |[Utiliser des restrictions appliquées par l’application dans SharePoint](#use-app-enforced-restrictions-in-sharepoint)|Ajoutez cette nouvelle stratégie. Cette option indique à Azure Active Directory (Azure AD) d’utiliser les paramètres spécifiés dans SharePoint. Cette stratégie s’applique à tous les utilisateurs, mais elle affecte uniquement l’accès aux sites inclus dans les stratégies d’accès SharePoint.|
|**Sensible**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *faible*, *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Incluez SharePoint dans les affectations d’applications Cloud.|
|         |[Exiger des PC conformes *et des* appareils mobiles](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Incluez SharePoint dans la liste des applications Cloud.|
||[Stratégie de contrôle d’accès SharePoint](#sharepoint-access-control-policies): autoriser uniquement le navigateur à accéder à des sites SharePoint spécifiques à partir d’appareils non gérés.|Cela empêche la modification et le téléchargement de fichiers. Utiliser PowerShell pour spécifier des sites.|
|**Hautement réglementé**|[*Toujours* exiger l’authentification multifacteur](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Incluez SharePoint dans l’affectation d’applications Cloud.|
||[Stratégie de contrôle d’accès SharePoint](#use-app-enforced-restrictions-in-sharepoint): bloquer l’accès à des sites SharePoint spécifiques à partir d’appareils non gérés.|Utiliser PowerShell pour spécifier des sites.|

## <a name="use-app-enforced-restrictions-in-sharepoint"></a>Utiliser des restrictions appliquées par l’application dans SharePoint

Si vous implémentez des contrôles d’accès dans SharePoint, vous devez créer cette stratégie d’accès conditionnel dans Azure AD pour indiquer à Azure AD d’appliquer les stratégies que vous configurez dans SharePoint. Cette stratégie s’applique à tous les utilisateurs, mais affecte uniquement l’accès aux sites que vous spécifiez à l’aide de PowerShell lorsque vous créez les contrôles d’accès dans SharePoint.

Pour configurer cette stratégie, voir « bloquer ou limiter l’accès à des collections de sites SharePoint ou des comptes OneDrive spécifiques » dans [contrôler l’accès à partir d’appareils non gérés](https://docs.microsoft.com/sharepoint/control-access-from-unmanaged-devices).

## <a name="sharepoint-access-control-policies"></a>Stratégies de contrôle d’accès SharePoint

Microsoft vous recommande de protéger le contenu des sites SharePoint avec du contenu sensible et hautement réglementé avec des contrôles d’accès aux appareils. Pour ce faire, vous devez créer une stratégie qui spécifie le niveau de protection et les sites auxquels appliquer la protection.

- Sites sensibles : autoriser l’accès au navigateur uniquement. Cela empêche les utilisateurs de modifier et de télécharger des fichiers.
- Sites hautement réglementés : bloquer l’accès à partir des appareils non gérés.

Voir « bloquer ou limiter l’accès à des collections de sites SharePoint ou des comptes OneDrive spécifiques » dans [contrôler l’accès à partir d’appareils non gérés](https://docs.microsoft.com/sharepoint/control-access-from-unmanaged-devices).

## <a name="how-these-policies-work-together"></a>Collaboration de ces stratégies

Il est important de comprendre que les autorisations de site SharePoint sont généralement basées sur les besoins de l’entreprise en matière d’accès aux sites. Ces autorisations sont gérées par les propriétaires de site et peuvent être hautement dynamiques. L’utilisation des stratégies d’accès aux appareils SharePoint assure la protection de ces sites, que les utilisateurs soient affectés à un groupe Azure AD associé à une protection de base, sensible ou hautement réglementée.

L’illustration suivante fournit un exemple de la façon dont les stratégies d’accès aux appareils SharePoint protègent l’accès aux sites pour un utilisateur.

[![Exemple de la façon dont les stratégies d’accès aux appareils SharePoint protègent les sites](../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png)

[Afficher une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png)

James a des stratégies d’accès conditionnel de base affectées, mais il peut avoir accès à des sites SharePoint avec une protection sensible ou hautement réglementée.

- Si James accède à un site sensible ou hautement réglementé qu’il est membre de son PC, son accès est accordé tant que son PC est conforme.
- Si Jean accède à un site sensible qu’il est membre de l’utilisation de son téléphone non géré, qui est autorisé pour les utilisateurs de base, il bénéficiera d’un accès navigateur uniquement au site sensible en raison de la stratégie d’accès aux appareils configurée pour ce site.
- Si Jean accède à un site hautement réglementé qu’il est membre de l’utilisation de son téléphone non géré, il sera bloqué en raison de la stratégie d’accès configurée pour ce site. Il peut accéder à ce site uniquement à l’aide de son PC géré et conforme.

## <a name="next-step"></a>Étape suivante

![Étape 4 : stratégies pour les applications Cloud Microsoft 365](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

Configurez les stratégies d’accès conditionnel pour :

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)

