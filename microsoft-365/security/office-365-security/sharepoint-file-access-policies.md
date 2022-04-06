---
title: 'Stratégies de document sécurisées recommandées : Microsoft 365 pour les | Microsoft Docs'
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
ms.openlocfilehash: 6effe1ffefaf7faeb90258163c539cdddcec2679
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569994"
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>Recommandations de stratégie pour la sécurisation SharePoint sites et fichiers

Cet article explique comment implémenter les stratégies Confiance nulle’identité et d’accès aux appareils recommandées pour protéger SharePoint et OneDrive Entreprise. Ces instructions s’appuient sur les stratégies [communes d’accès aux identités et aux appareils](identity-access-policies.md).

Ces recommandations sont basées sur trois niveaux différents de sécurité et de protection pour les fichiers SharePoint qui peuvent être appliqués en fonction de la granularité de vos **besoins : point** de **départ, entreprise** et sécurité **spécialisée.** Vous pouvez en savoir plus sur ces niveaux de sécurité et les systèmes d’exploitation clients recommandés, référencés par ces recommandations [dans la vue d’ensemble](microsoft-365-policies-configurations.md).

Outre l’application de ces instructions, assurez-vous de configurer les sites SharePoint avec le niveau de protection approprié, y compris la définition des autorisations appropriées pour l’entreprise et le contenu de sécurité spécialisé.

## <a name="updating-common-policies-to-include-sharepoint-and-onedrive-for-business"></a>Mise à jour des stratégies courantes SharePoint et OneDrive Entreprise

Pour protéger les fichiers dans SharePoint et OneDrive, le diagramme suivant illustre les stratégies à mettre à jour à partir des stratégies communes d’accès aux appareils et aux identités.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png" alt-text="Résumé des mises à jour de stratégie pour la protection de l’accès aux SharePoint" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png":::

Si vous avez inclus SharePoint lorsque vous avez créé les stratégies communes, vous devez uniquement créer les nouvelles stratégies. Pour les stratégies d’accès conditionnel, SharePoint inclut OneDrive.

Les nouvelles stratégies implémentent la protection des appareils pour les entreprises et le contenu de sécurité spécialisé en appliquant des exigences d’accès spécifiques SharePoint sites que vous spécifiez.

Le tableau suivant répertorie les stratégies que vous devez réviser et mettre à jour ou créer des stratégies pour SharePoint. Les stratégies courantes sont liées aux instructions de configuration associées dans l’article Des stratégies communes d’accès aux appareils [et aux](identity-access-policies.md) identités.

|Niveau de protection|Stratégies|Informations supplémentaires|
|---|---|---|
|**Point de départ**|[Exiger une mfmf lorsque le risque de se connecte *est moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Incluez SharePoint dans l’affectation des applications cloud.|
||[Bloquer les clients ne prenant pas en charge l’authentification moderne](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Incluez SharePoint dans l’affectation des applications cloud.|
||[Appliquer des stratégies de protection des données APP](identity-access-policies.md#apply-app-data-protection-policies)|Assurez-vous que toutes les applications recommandées sont incluses dans la liste des applications. Assurez-vous de mettre à jour la stratégie pour chaque plateforme (iOS, Android, Windows).|
||[Utiliser les restrictions appliquées par l’application dans SharePoint](#use-app-enforced-restrictions-in-sharepoint)|Ajoutez cette nouvelle stratégie. Cela indique Azure Active Directory (Azure AD) d’utiliser les paramètres spécifiés dans SharePoint. Cette stratégie s’applique à tous les utilisateurs, mais affecte uniquement l’accès aux sites inclus SharePoint stratégies d’accès.|
|**Enterprise**|[Exiger l’mf lorsque le risque de se connecte *est faible*, *moyen* ou *élevé*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Incluez SharePoint dans les affectations des applications cloud.|
||[Exiger des PC et *des appareils* mobiles conformes](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Incluez SharePoint dans la liste des applications cloud.|
||[SharePoint de contrôle d’accès](#sharepoint-access-control-policies) : autoriser l’accès par navigateur uniquement à des sites SharePoint spécifiques à partir d’appareils non utilisés.|Cela empêche la modification et le téléchargement de fichiers. Utilisez PowerShell pour spécifier des sites.|
|**Sécurité spécialisée**|[*Toujours exiger* l’mf d’fa](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Incluez SharePoint dans l’affectation des applications cloud.|
||[SharePoint de contrôle d’accès](#use-app-enforced-restrictions-in-sharepoint) : bloquer l’accès à des sites SharePoint spécifiques à partir d’appareils non utilisés.|Utilisez PowerShell pour spécifier des sites.|

## <a name="use-app-enforced-restrictions-in-sharepoint"></a>Utiliser les restrictions appliquées par l’application dans SharePoint

Si vous implémentez des contrôles d’accès dans SharePoint, des stratégies d’accès conditionnel sont créées dans Azure AD pour indiquer à Azure AD d’appliquer les stratégies que vous configurez dans SharePoint. Par défaut, cette stratégie s’applique à tous les utilisateurs, mais affecte uniquement l’accès aux sites que vous spécifiez à l’aide de PowerShell lorsque vous créez les contrôles d’accès dans SharePoint. La stratégie peut également être étendue à des utilisateurs, des groupes ou des sites spécifiques.

Pour configurer cette stratégie, voir « Bloquer ou limiter l’accès à des collections de sites SharePoint ou des comptes OneDrive spécifiques » dans Contrôler l’accès à partir d’appareils non [utilisés](/sharepoint/control-access-from-unmanaged-devices).

## <a name="sharepoint-access-control-policies"></a>SharePoint de contrôle d’accès

Microsoft vous recommande de protéger le contenu des sites SharePoint avec du contenu d’entreprise et un contenu de sécurité spécialisé avec des contrôles d’accès aux appareils. Pour ce faire, créez une stratégie qui spécifie le niveau de protection et les sites à appliquer à la protection.

- Enterprise sites : autoriser l’accès par navigateur uniquement. Cela empêche les utilisateurs de modifier et de télécharger des fichiers.
- Sites de sécurité spécialisés : bloquer l’accès à partir d’appareils nonmanagés.

Voir « Bloquer ou limiter l’accès à des collections SharePoint sites ou des comptes OneDrive spécifiques » dans Contrôler l’accès à partir d’appareils [non utilisés](/sharepoint/control-access-from-unmanaged-devices).

## <a name="how-these-policies-work-together"></a>Fonctionnement de ces stratégies ensemble

Il est important de comprendre que les autorisations SharePoint site sont généralement basées sur les besoins de l’entreprise pour accéder aux sites. Ces autorisations sont gérées par les propriétaires de site et peuvent être hautement dynamiques. L’SharePoint des stratégies d’accès aux appareils garantit la protection de ces sites, que les utilisateurs soient affectés à un groupe Azure AD associé au point de départ, à l’entreprise ou à une protection de sécurité spécialisée.

L’illustration suivante montre comment les stratégies SharePoint’accès aux appareils protègent l’accès aux sites d’un utilisateur.

:::image type="content" source="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png" alt-text="Exemple de la façon dont les stratégies SharePoint’accès aux appareils protègent les sites" lightbox="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png":::

Il dispose de stratégies d’accès conditionnel de point de départ affectées, mais il peut avoir accès à des sites SharePoint avec une protection de sécurité spécialisée ou d’entreprise.

- Si Jean accède à un site dont il est membre avec une protection de sécurité d’entreprise ou spécialisée à l’aide de son PC, son accès est accordé.
- Si Jean accède à un site de protection d’entreprise, il est membre de son téléphone non utilisé, ce qui est autorisé pour les utilisateurs de point de départ, il recevra un accès par navigateur uniquement au site d’entreprise en raison de la stratégie d’accès aux appareils configurée pour ce site.
- Si Jean accède à un site de sécurité spécialisé, il est membre de son téléphone non utilisé, il sera bloqué en raison de la stratégie d’accès configurée pour ce site. Il peut accéder à ce site uniquement à l’aide de son PC géré.

## <a name="next-step"></a>Étape suivante

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Étape 4 : stratégies pour Microsoft 365 applications cloud" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::


Configurer des stratégies d’accès conditionnel pour :

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
