---
title: Microsoft 365 Business Premium playbook d’évaluation
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.collection: m365-security-compliance
ms.service: microsoft-365-business
ms.subservice: business-premium
ms.localizationpriority: high
ms.date: 08/24/2022
search.appverid:
- MOE150
- MET150
description: Tirez le meilleur parti de votre version d’évaluation de Microsoft 365 Business Premium. Essayez certaines des principales fonctionnalités de productivité et de sécurité.
ms.openlocfilehash: 52b38d8145c43eac2eeef34b063a3a327f2d5a3f
ms.sourcegitcommit: 651610ca73bfd1d008d97311b59782790df664fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67611845"
---
# <a name="trial-playbook-microsoft-365-business-premium"></a>Playbook d’évaluation : Microsoft 365 Business Premium

Bienvenue dans le guide opérationnel d’évaluation Microsoft Business Premium. Ce guide opérationnel vous aidera à tirer le meilleur parti de votre essai gratuit de 30 jours en vous apprenant comment Microsoft 365 Business Premium augmente la productivité et contribue à protéger votre organisation avec des fonctionnalités de sécurité avancées. À l’aide des recommandations de Microsoft, découvrez comment configurer vos fonctionnalités de protection contre les menaces, analyser les menaces détectées et répondre aux cyberattaques.

## <a name="set-up-the-microsoft-365-business-premium-trial"></a>Configurer la version d’évaluation Microsoft 365 Business Premium

Lorsque vous [commencer une version d’évaluation ou acheter Microsoft 365 Business Premium](get-microsoft-365-business-premium.md), la première étape consiste à tout configurer.

> [!TIP]
> Enregistrez ce guide opérationnel dans les favoris de votre navigateur. Lorsque des liens dans le guide opérationnel vous éloignent de cet emplacement, revenez simplement à ce guide opérationnel pour continuer.

Tout d’abord, [configurez votre version d’évaluation](../business-premium/m365bp-setup.md) !

Une fois que vous avez lancé la version d’évaluation et terminé le processus d’installation, la prise en compte des modifications peut prendre jusqu’à deux heures.

Microsoft 365 Business Premium inclut des [stratégies de sécurité prédéfinies](/security/office-365-security/preset-security-policies.md) que vous pouvez utiliser dans votre environnement. Ces stratégies représentent un profil de protection de référence adapté à la plupart des utilisateurs. La protection standard inclut :

- [Liens fiables](../security/office-365-security/safe-links.md), [pièces jointes fiables](../security/office-365-security/safe-attachments.md)et stratégies [anti-hameçonnage](../security/office-365-security/anti-phishing-protection.md) qui s’appliquent à l’ensemble du locataire ou au sous-ensemble d’utilisateurs que vous avez peut-être choisis pendant le processus de configuration de l’évaluation. (Votre abonnement d’évaluation est destiné à un maximum de 25 utilisateurs.)

- Protection des applications de productivité, telles que [SharePoint](/sharepoint/introduction), [OneDrive](/onedrive/one-drive-quickstart-small-business), [Approsoft Office](/deployoffice/about-microsoft-365-apps) et [Microsoft Teams](/microsoftteams/teams-overview).

## <a name="add-a-domain"></a>Ajouter un domaine

Lorsque vous achetez la version d’évaluation Microsoft 365 Business Premium, vous avez la possibilité d’utiliser un domaine que vous possédez ou d’en acheter un pendant l’inscription.

> [!NOTE]
> Si vous avez acheté un nouveau domaine lorsque vous vous êtes inscrit, votre domaine est configuré et vous pouvez accéder à Ajouter des utilisateurs et attribuer des licences. Accédez au centre d’administration ([https://admin.microsoft.com](https://admin.microsoft.com)).

1. Dans le menu du Centre d’administration, choisissez **Configurer** pour démarrer l’Assistant.

2. Sélectionnez **Configurer l’e-mail avec un domaine personnalisé**, puis **utilisez un domaine que vous possédez déjà**, tel que contoso.com`contoso.com`.

3. Suivez les autres étapes de l’Assistant pour terminer le processus.

   > [!Important]
   > Si vous avez acheté un domaine pendant l’inscription, vous ne verrez pas l’étape **Ajouter** un domaine ici. Accédez à **Ajouter des utilisateurs** à la place.

4. Suivez les étapes de l’Assistant pour [Créer des enregistrements DNS auprès d’un fournisseur d’hébergement DNS pour Office 365](/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) qui vérifie que vous êtes le propriétaire du domaine. Si vous connaissez votre hôte de domaine, voir [Ajouter un domaine à Microsoft 365](/microsoft-365/admin/setup/add-domain).

5. Si votre fournisseur d’hébergement est GoDaddy ou un autre hôte activé avec la connexion au domaine, vous êtes invité à vous connecter et à laisser Microsoft s’authentifier automatiquement en votre nom.

## <a name="onboard-and-protect-devices"></a>Intégrer et protéger des appareils

Microsoft 365 Business Premium inclut Defender entreprise, une nouvelle solution de sécurité pour protéger les appareils. Consultez [Intégrer des appareils à Microsoft Defender pour les PME](../security/defender-business/mdb-onboard-devices.md).

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Exécutez l’[Assistant Installation](../security/defender-business/mdb-use-wizard.md).

3. [Intégration des appareils](../security/defender-business/mdb-onboard-devices.md).

4. [Évaluer vos stratégies de sécurité](../security/defender-business/mdb-configure-security-settings.md).

## <a name="use-microsoft-365-apps-on-devices"></a>Utiliser Microsoft 365 Apps sur les appareils

1. Tout d’abord, vous devez [installer Microsoft 365 Apps](m365bp-install-office-apps.md).

2. Accédez à [https://office.com](https://office.com) et connectez-vous. (Voir [Prise en main à Office.com](https://support.microsoft.com/office/get-started-at-office-com-91a4ec74-67fe-4a84-a268-f6bdf3da1804).)

3. Créez un document Office, tel qu’un [document Word](https://support.microsoft.com/office/basic-tasks-in-word-87b3243c-b0bf-4a29-82aa-09a681999fdc).

4. [Partagez un document](https://support.microsoft.com/office/share-your-documents-651e1cb9-9a51-46dc-8d32-bdb7d928eedd) avec un membre de l’équipe.

## <a name="start-using-the-microsoft-365-defender-portal"></a>Commencer à utiliser le portail Microsoft 365 Defender 

1. Accédez au portail Microsoft 365 Defender sur [https://security.microsoft.com](https://security.microsoft.com).

2. Prenez le temps de [vous familiariser avec le portail](../security/defender-business/mdb-get-started.md).

3. À présent, [évaluez votre posture de sécurité](../security/defender/microsoft-secure-score.md) et découvrez comment améliorer votre score.

4. Découvrez comment [répondre à un incident de sécurité](../security/defender-business/mdb-respond-mitigate-threats.md).

5. Enfin, [passez en revue les actions de correction](../security/defender-business/mdb-review-remediation-actions.md).

## <a name="see-also"></a>Voir aussi

- [Microsoft 365 Business Premium - cybersécurité pour les petites entreprises](index.md)
- [Qu’est-ce que Microsoft Defender pour entreprises ?](../security/defender-business/mdb-overview.md)
