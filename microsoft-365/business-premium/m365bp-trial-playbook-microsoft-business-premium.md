---
title: Guide opérationnel d’évaluation de Microsoft Defender pour Entreprise Premium
f1.keywords:
- NOCSH
ms.author: v-kcirillo
author: cirilk
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.collection: m365-security-compliance
ms.localizationpriority: high
ms.prod: m365-security
search.appverid:
- MOE150
- MET150
description: Tirez le meilleur parti de votre version d’évaluation de Microsoft 365 Business Premium. Essayez certaines des principales fonctionnalités de productivité et de sécurité.
ms.openlocfilehash: ba9d7764734ccf47d412b6f95864da737d09251d
ms.sourcegitcommit: c216ffa5da8f431e4380bb133a234ae7d94144c7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2022
ms.locfileid: "65893483"
---
# <a name="trial-playbook-microsoft-business-premium"></a>Guide opérationnel d’évaluation : Microsoft Business Premium

Bienvenue dans le guide opérationnel d’évaluation Microsoft Business Premium. Ce guide opérationnel vous aidera à tirer le meilleur parti de votre essai gratuit de 30 jours en vous apprenant comment Microsoft 365 Business Premium augmente la productivité et contribue à protéger votre organisation avec Defender pour les PME. À l'aide des recommandations de Microsoft, vous apprendrez comment Defender peut vous aider à définir des politiques de protection, à analyser les menaces qui pèsent sur votre organisation et à répondre aux attaques.

## <a name="set-up-the-microsoft-365-business-premium-trial"></a>Configurer la version d’évaluation Microsoft 365 Business Premium

Lorsque vous [commencer une version d’évaluation ou acheter Microsoft 365 Business Premium](get-microsoft-365-business-premium.md), la première étape consiste à tout configurer. 

> [!Tip]
> Lorsque des liens dans le guide opérationnel vous éloignent de cet emplacement, revenez simplement à ce guide opérationnel pour continuer.

Tout d’abord, [configurez votre version d’évaluation](../business-premium/m365bp-setup.md) !

Une fois que vous avez lancé la version d’évaluation et terminé le processus d’installation, l’application des modifications peut prendre jusqu’à 2 heures.

Nous avons configuré automatiquement des stratégies de sécurité [prédéfinies](/security/office-365-security/preset-security-policies.md) dans votre environnement. Ces stratégies représentent un profil de protection de référence adapté à la plupart des utilisateurs. La protection standard inclut :

- Coffre liens, Coffre pièces jointes et stratégies anti-hameçonnage qui sont limitées à l’ensemble du client ou du sous-ensemble d’utilisateurs que vous avez peut-être choisi au cours du processus de configuration de la version d’évaluation.

- Protection de toutes les fonctionnalités Microsoft 365 Business Premium telles que : SharePoint, OneDrive, les applications Office et Microsoft Teams.

## <a name="add-a-domain"></a>Ajouter un domaine

Lorsque vous achetez la version d’évaluation Microsoft 365 Business Premium, vous avez la possibilité d’utiliser un domaine que vous possédez ou d’en acheter un pendant l’inscription.

> [!Note]
> Si vous avez acheté un nouveau domaine lorsque vous vous êtes inscrit, votre domaine est configuré et vous pouvez accéder à Ajouter des utilisateurs et attribuer des licences. Accédez au centre d’administration ([https://admin.microsoft.com](https://admin.microsoft.com)).

1. Dans le menu du Centre d’administration, choisissez **Configurer** pour démarrer l’Assistant.

2. Sélectionnez **Configurer l’e-mail avec un domaine personnalisé**, puis **utilisez un domaine que vous possédez déjà**, tel que contoso.com.

3. Suivez les autres étapes de l’Assistant pour terminer le processus.

   > [!Important]
   > Si vous avez acheté un domaine pendant l’inscription, vous ne verrez pas l’étape Ajouter un domaine ici. Accédez à Ajouter des utilisateurs à la place.

4. Suivez les étapes de l’Assistant pour Créer des enregistrements DNS auprès d’un fournisseur d’hébergement DNS pour Office 365 qui vérifie que vous êtes le propriétaire du domaine. Si vous connaissez votre hôte de domaine, voir Ajouter un domaine à Microsoft 365.

5. Si votre fournisseur d’hébergement est GoDaddy ou si un autre hôte est activé avec connexion de domaine, le processus est simple et vous êtes automatiquement invité à vous connecter et à laisser Microsoft s’authentifier en votre nom.

## <a name="onboard-and-protect-devices"></a>Intégrer et protéger des appareils

1. Visitez le portail Defender sur security.microsoft.com.

2. Exécutez l’[Assistant Installation](../security/defender-business/mdb-use-wizard.md).

3. À présent, [intégrer des appareils](../security/defender-business/mdb-onboard-devices.md).

4. Ensuite, [passez en revue les stratégies de sécurité](../security/defender-business/mdb-configure-security-settings.md).

## <a name="use-office-apps-on-devices"></a>Utiliser les applications Office sur les appareils

1. Tout d’abord, vous devez [installer Office](m365bp-install-office-apps.md).

2. Accédez à office.com et [connectez-vous](https://support.microsoft.com/office/get-started-at-office-com-91a4ec74-67fe-4a84-a268-f6bdf3da1804).

3. Créez un document Office, tel qu’un [document Word](https://support.microsoft.com/office/basic-tasks-in-word-87b3243c-b0bf-4a29-82aa-09a681999fdc).

4. [Partagez un document](https://support.microsoft.com/office/share-your-documents-651e1cb9-9a51-46dc-8d32-bdb7d928eedd) avec un membre de l’équipe.

## <a name="start-using-the-microsoft-365-defender-portal"></a>Commencer à utiliser le portail Microsoft 365 Defender 

1. Accédez au portail Microsoft 365 Defender sur [https://security.microsoft.com](https://security.microsoft.com).

2. Prenez le temps de [vous familiariser avec le portail](../security/defender-business/mdb-get-started.md).

3. Maintenant, [évaluez votre posture de sécurité](../security/defender/microsoft-secure-score.md).

4. Familiarisez-vous avec [la façon de répondre à un incident de sécurité](../security/defender-business/mdb-respond-mitigate-threats.md).

5. Enfin, [passez en revue les actions de correction](../security/defender-business/mdb-review-remediation-actions.md).

## <a name="see-also"></a>Voir aussi

- [Cybersécurité Microsoft 365 Business Premium &mdash; pour les petites entreprises](index.md)