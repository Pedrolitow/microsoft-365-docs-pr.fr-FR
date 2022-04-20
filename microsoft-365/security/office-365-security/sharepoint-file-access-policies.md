---
title: Stratégies de document sécurisé recommandées - Microsoft 365 pour les | d’entreprise Microsoft Docs
description: Décrit les recommandations de Microsoft sur l’application de stratégies de sécurisation de l’accès aux fichiers SharePoint.
ms.author: dansimp
author: dansimp
manager: dansimp
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
ms.openlocfilehash: 3a2a8e5be8fb78824e8670f94a2e087da9538329
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972142"
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>Recommandations de stratégie pour la sécurisation des sites et fichiers SharePoint

Cet article explique comment implémenter les stratégies d’identité et d’accès aux appareils Confiance nulle recommandées pour protéger les SharePoint et les OneDrive Entreprise. Ce guide s’appuie sur les stratégies [d’accès aux identités et aux appareils courantes](identity-access-policies.md).

Ces recommandations sont basées sur trois niveaux de sécurité et de protection différents pour SharePoint fichiers qui peuvent être appliqués en fonction de la granularité de vos besoins : **point de départ**, **entreprise** et **sécurité spécialisée**. Vous pouvez en savoir plus sur ces niveaux de sécurité et les systèmes d’exploitation clients recommandés, référencés par ces recommandations dans [la vue d’ensemble](microsoft-365-policies-configurations.md).

En plus d’implémenter ces conseils, veillez à configurer SharePoint sites avec le niveau de protection approprié, notamment en définissant les autorisations appropriées pour le contenu de sécurité d’entreprise et spécialisé.

## <a name="updating-common-policies-to-include-sharepoint-and-onedrive-for-business"></a>Mise à jour des stratégies courantes pour inclure SharePoint et OneDrive Entreprise

Pour protéger les fichiers dans SharePoint et OneDrive, le diagramme suivant illustre les stratégies à mettre à jour à partir des stratégies d’accès aux identités et aux appareils courantes.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png" alt-text="Récapitulatif des mises à jour de stratégie pour la protection de l’accès à SharePoint" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png":::

Si vous avez inclus SharePoint lorsque vous avez créé les stratégies communes, vous devez uniquement créer les nouvelles stratégies. Pour les stratégies d’accès conditionnel, SharePoint inclut OneDrive.

Les nouvelles stratégies implémentent la protection des appareils pour le contenu de sécurité d’entreprise et spécialisé en appliquant des exigences d’accès spécifiques aux sites SharePoint que vous spécifiez.

Le tableau suivant répertorie les stratégies que vous devez examiner et mettre à jour ou créer pour SharePoint. Les stratégies courantes sont liées aux instructions de configuration associées dans l’article [Stratégies d’accès aux appareils et aux identités communes](identity-access-policies.md) .

|Niveau de protection|Stratégies|Informations supplémentaires|
|---|---|---|
|**Point de départ**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Incluez SharePoint dans l’attribution d’applications cloud.|
||[Bloquer les clients ne prenant pas en charge l’authentification moderne](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Incluez SharePoint dans l’attribution d’applications cloud.|
||[Appliquer des stratégies de protection des données APP](identity-access-policies.md#apply-app-data-protection-policies)|Assurez-vous que toutes les applications recommandées sont incluses dans la liste des applications. Veillez à mettre à jour la stratégie pour chaque plateforme (iOS, Android, Windows).|
||[Utiliser des restrictions appliquées par l’application dans SharePoint](#use-app-enforced-restrictions-in-sharepoint)|Ajoutez cette nouvelle stratégie. Cela indique à Azure Active Directory (Azure AD) d’utiliser les paramètres spécifiés dans SharePoint. Cette stratégie s’applique à tous les utilisateurs, mais affecte uniquement l’accès aux sites inclus dans SharePoint stratégies d’accès.|
|**Enterprise**|[Exiger l’authentification multifacteur lorsque le risque de connexion est *faible*, *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Incluez SharePoint dans les affectations d’applications cloud.|
||[Exiger des PC *et* des appareils mobiles conformes](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Incluez SharePoint dans la liste des applications cloud.|
||[SharePoint stratégie de contrôle d’accès](#sharepoint-access-control-policies) : autoriser l’accès par navigateur uniquement à des sites SharePoint spécifiques à partir d’appareils non gérés.|Cela empêche la modification et le téléchargement de fichiers. Utilisez PowerShell pour spécifier des sites.|
|**Sécurité spécialisée**|[*Toujours* exiger l’authentification multifacteur](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Incluez SharePoint dans l’attribution d’applications cloud.|
||[SharePoint stratégie de contrôle d’accès](#use-app-enforced-restrictions-in-sharepoint) : bloquez l’accès à des sites SharePoint spécifiques à partir d’appareils non gérés.|Utilisez PowerShell pour spécifier des sites.|

## <a name="use-app-enforced-restrictions-in-sharepoint"></a>Utiliser des restrictions appliquées par l’application dans SharePoint

Si vous implémentez des contrôles d’accès dans SharePoint, des stratégies d’accès conditionnel sont créées dans Azure AD pour indiquer à Azure AD d’appliquer les stratégies que vous configurez dans SharePoint. Par défaut, cette stratégie s’applique à tous les utilisateurs, mais affecte uniquement l’accès aux sites que vous spécifiez à l’aide de PowerShell lorsque vous créez les contrôles d’accès dans SharePoint. La stratégie peut également être étendue pour des utilisateurs, des groupes ou des sites spécifiques.

Pour configurer cette stratégie, consultez « Bloquer ou limiter l’accès à des collections de sites SharePoint spécifiques ou à des comptes OneDrive » dans [Contrôler l’accès à partir d’appareils non gérés](/sharepoint/control-access-from-unmanaged-devices).

## <a name="sharepoint-access-control-policies"></a>SharePoint stratégies de contrôle d’accès

Microsoft vous recommande de protéger le contenu dans SharePoint sites avec du contenu de sécurité d’entreprise et spécialisé avec des contrôles d’accès aux appareils. Pour ce faire, vous créez une stratégie qui spécifie le niveau de protection et les sites auxquels appliquer la protection.

- Enterprise sites : autorisez l’accès uniquement au navigateur. Cela empêche les utilisateurs de modifier et de télécharger des fichiers.
- Sites de sécurité spécialisés : bloquer l’accès à partir d’appareils non gérés.

Consultez « Bloquer ou limiter l’accès à des collections de sites SharePoint spécifiques ou à des comptes OneDrive » dans [Contrôler l’accès à partir d’appareils non gérés](/sharepoint/control-access-from-unmanaged-devices).

## <a name="how-these-policies-work-together"></a>Fonctionnement de ces stratégies

Il est important de comprendre que SharePoint autorisations de site sont généralement basées sur les besoins de l’entreprise en matière d’accès aux sites. Ces autorisations sont gérées par les propriétaires de site et peuvent être très dynamiques. L’utilisation de SharePoint stratégies d’accès aux appareils garantit la protection de ces sites, que les utilisateurs soient affectés à un groupe Azure AD associé au point de départ, à l’entreprise ou à une protection de sécurité spécialisée.

L’illustration suivante montre comment SharePoint stratégies d’accès aux appareils protègent l’accès aux sites pour un utilisateur.

:::image type="content" source="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png" alt-text="Exemple de la façon dont SharePoint stratégies d’accès aux appareils protègent les sites" lightbox="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png":::

James a des stratégies d’accès conditionnel de point de départ affectées, mais il peut avoir accès à SharePoint sites avec une protection de sécurité d’entreprise ou spécialisée.

- Si James accède à un site dont il est membre avec une protection de sécurité d’entreprise ou spécialisée à l’aide de son PC, son accès est accordé.
- Si James accède à un site de protection d’entreprise, il est membre de l’utilisation de son téléphone non managé, ce qui est autorisé pour les utilisateurs de point de départ, il recevra l’accès par navigateur uniquement au site d’entreprise en raison de la stratégie d’accès aux appareils configurée pour ce site.
- Si James accède à un site de sécurité spécialisé, il est membre de l’utilisation de son téléphone non managé, il sera bloqué en raison de la stratégie d’accès configurée pour ce site. Il ne peut accéder à ce site qu’à l’aide de son PC managé.

## <a name="next-step"></a>Étape suivante

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Étape 4 : stratégies pour les applications cloud Microsoft 365" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Configurer des stratégies d’accès conditionnel pour :

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
