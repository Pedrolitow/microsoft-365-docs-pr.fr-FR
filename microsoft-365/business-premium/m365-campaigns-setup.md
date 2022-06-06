---
title: Vue d’ensemble de la configuration de Microsoft 365 for Campaigns
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.date: 03/02/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: 496e690b-b75d-4ff5-bf34-cc32905d0364
description: Vue d’ensemble de la configuration de Microsoft 365 Entreprise pour les campagnes ou d’autres entreprises
ms.openlocfilehash: e16ef74f1815087a5cf777ed26ec8742600713ca
ms.sourcegitcommit: c216ffa5da8f431e4380bb133a234ae7d94144c7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2022
ms.locfileid: "65893498"
---
# <a name="setup-for-microsoft-365-business-for-campaigns"></a>Configuration de Microsoft 365 Entreprises

Maintenant que vous avez [abonné à Microsoft 365 pour Entreprises](get-microsoft-365-campaigns.md) l’étape suivante consiste à tout configurer.

## <a name="before-you-begin"></a>Avant de commencer

Assurez-vous de respecter les exigences suivantes avant de commencer votre processus d’installation :

| Conditions requises | Description |
|:---|:---|
| Abonnement | Microsoft 365 Business Premium ou Microsoft 365 campagnes <br/><br/> Pour démarrer une version d’évaluation ou acheter votre abonnement, consultez les articles suivants : <br/>- [Obtenir Microsoft 365 Business Premium](get-microsoft-365-business-premium.md)<br/>- [Obtenir Microsoft 365 campagnes](get-microsoft-365-campaigns.md) |
| Autorisations  | Pour terminer le processus de configuration initiale, vous devez être Administrateur général. [En savoir plus sur les rôles d’administrateur](../admin/add-users/about-admin-roles.md). |
| Configuration requise pour le navigateur | Microsoft Edge, Safari, Chrome ou Firefox. [En savoir plus sur les exigences du navigateur](https://www.microsoft.com/microsoft-365/microsoft-365-and-office-resources#coreui-heading-uyetipy).  |
| Système d’exploitation | **Windows** : Windows 11, Windows 10, Windows 8.1, Windows Server 2019 ou version ultérieure, ou Windows Server 2016<br/><br/>**macOS** : l’une des trois versions les plus récentes de macOS |

> [!TIP]
> Pour plus d’informations sur Microsoft 365, Office et la configuration système requise, consultez [Microsoft 365 et ressources Office](https://www.microsoft.com/microsoft-365/microsoft-365-and-office-resources).

## <a name="sign-in-to-microsoft-365-for-campaigns"></a>Connectez-vous, à Microsoft 365 pour les Campagnes

Si vous vous êtes inscrit à Microsoft 365 pour les Campagnes (ou Microsoft 365 Business Premium), vous êtes désigné en tant qu’administrateur Microsoft 365 (également appelé Administrateur général). Cela vous permet de vous connecter et de lancer le système.

Voici comment se connecter :

1. Recherchez le nom d’utilisateur et le mot de passe que nous avons envoyés à l’adresse e-mail que vous avez utilisée lorsque vous vous [êtes inscrit à Microsoft 365 pour Campagnes](m365-campaigns-sign-up.md).

2. Dans un navigateur, accédez au Centre d’administration Microsoft 365 à <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank"><https://admin.microsoft.com></a>

3. Entrez votre nom d’utilisateur et votre mot de passe d’administrateur de domaine, puis cliquez sur OK. Sélectionnez **Connexion**.

4. En haut à droite de la page, recherchez la **préversion sur le** contrôle. Sélectionnez **Aperçu** pour pouvoir utiliser tous les contrôles décrits dans [la protection bump up pour votre campagne](m365bp-security-overview.md).

### <a name="staff-sign-in"></a>Connexion du personnel

Les utilisateurs qui ont été ajoutés à votre abonnement Microsoft 365 pour Campagnes(ou Microsoft 365 Entreprise Premium) peuvent se connecter en procédant comme suit :

1. Accédez à <a href="https://office.com" target="_blank"><https://Office.com></a>.

2. Connectez-vous à l’aide du nom d’utilisateur et du mot de passe du compte. Les utilisateurs disposent de ces informations dans l’e-mail qu’ils reçoivent lorsqu’ils sont ajoutés en tant qu’utilisateurs. S’il ne trouve pas l’e-mail, vérifiez que [l’utilisateur n’a pas reçu d’e-mail d’invitation](../admin/simplified-signup/admin-invite-business-standard.md#i-shared-an-email-invite-but-the-user-didnt-receive-the-email).

> [!TIP]
> Fournissez à votre personnel un lien vers le [guide de configuration rapide des employés](../admin/setup/employee-quick-setup.md) pour obtenir de l’aide sur la connexion, l’obtention d’applications Office et l’enregistrement, la copie et le partage de fichiers.

### <a name="customize-your-sign-in-page-with-a-privacy-and-consent-notice"></a>Personnaliser votre page de connexion avec un avis de confidentialité et de consentement

Votre entreprise ou votre campagne peut permettre aux organismes chargés de l'application de la loi d'engager plus facilement des poursuites contre les cybercriminels en ajoutant un avis de confidentialité et de consentement sur votre page d'inscription.

Vous pouvez personnaliser votre page de connexion avec votre marque. Vous pouvez également ajouter du texte pour aider vos utilisateurs à se connecter, ou pour indiquer les exigences légales ou les restrictions d'accès aux ressources de Microsoft 365.

### <a name="customize-the-text-on-your-sign-in-page"></a>Personnaliser le texte de votre page de connexion

Pour mettre à jour les éléments personnalisables de la page de connexion, vous devez être un administrateur global. Pour des instructions spécifiques, [voir l'article sur l'ajout d'une marque d'entreprise](/azure/active-directory/fundamentals/customize-branding).

Les éléments que vous pouvez mettre à jour sont :

- Texte de la page de connexion (un endroit facile pour ajouter la déclaration de confidentialité et de consentement)
- Image de fond de la page de connexion
- Logo de la bannière
- Indication du nom d'utilisateur

Pour des exemples d'avis de confidentialité et de consentement, voir l'annexe A du document [Recherche et saisie d'ordinateurs et obtention de preuves électroniques dans le cadre d'enquêtes criminelles](https://www.justice.gov/sites/default/files/criminal-ccips/legacy/2015/01/14/ssmanual2009.pdf).

## <a name="next-objective"></a>Objectif suivant

Une fois que vous avez atteint ces objectifs, accédez à [augmentez les protections de sécurité](m365bp-security-overview.md).
