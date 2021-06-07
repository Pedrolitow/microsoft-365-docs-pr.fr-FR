---
title: Activer le message de rapport ou les modules de signalement du hameçonnage
f1.keywords:
- NOCSH
ms.author: siosulli
author: dansimp
manager: dansimp
audience: Admin
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 4250c4bc-6102-420b-9e0a-a95064837676
ms.collection:
- M365-security-compliance
description: Découvrez comment activer le message de rapport ou les add-ins Signaler le hameçonnage pour Outlook et Outlook sur le web, pour des utilisateurs individuels ou pour l’ensemble de votre organisation.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ff91cf4c99c9552ab5f5fecd7c6d2efee8d2d9a8
ms.sourcegitcommit: b09aee96a1e2266b33ba81dfe497f24c5300bb56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2021
ms.locfileid: "52789255"
---
# <a name="enable-the-report-message-or-the-report-phishing-add-ins"></a>Activer le message de rapport ou les modules de signalement du hameçonnage

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Si vous êtes un administrateur d’une organisation Microsoft 365 avec des boîtes aux lettres Exchange Online, nous vous recommandons d’utiliser le portail Soumissions dans le Centre de sécurité & conformité. Pour plus d’informations, voir Utiliser la soumission d’administrateur pour soumettre des messages suspects de courrier indésirable, d’hameçonnage, d’URL et [de fichiers à Microsoft.](admin-submission.md)

Les add-ins Signaler les messages et signaler le hameçonnage pour Outlook et Outlook sur le web (anciennement appelés Outlook Web App) permettent aux utilisateurs de signaler facilement les faux positifs (messages électroniques de qualité marqués comme faux) ou les faux négatifs (courriers électroniques erronés autorisés) à Microsoft et à ses affiliés pour analyse. 

Microsoft utilise ces soumissions pour améliorer l’efficacité des technologies de protection de la messagerie. Par exemple, supposons que des personnes signalent de nombreux messages à l’aide du module de signalement du hameçonnage. Ces informations sont disponibles dans le Tableau de bord de sécurité et d’autres rapports. L’équipe de sécurité de votre organisation peut utiliser ces informations pour indiquer que les stratégies anti-hameçonnage peuvent avoir besoin d’être mises à jour. 

Vous pouvez installer le module de rapport de message ou de signalement du hameçonnage. Si vous souhaitez que vos utilisateurs signalent à la fois le courrier indésirable et les messages de hameçonnage, déployez le add-in Signaler un message dans votre organisation. Pour plus d’informations, voir Enable the Report Message add-in. 

Le add-in Report Message offre la possibilité de signaler les messages de courrier indésirable et de hameçonnage. Les administrateurs peuvent activer le add-in Message de rapport pour l’organisation, et les utilisateurs individuels peuvent l’installer eux-mêmes. 

Le module de signalement du hameçonnage offre la possibilité de signaler uniquement les messages de hameçonnage. Les administrateurs peuvent activer le module de signalement du hameçonnage pour l’organisation, et les utilisateurs individuels peuvent l’installer eux-mêmes. 

Si vous êtes un utilisateur individuel, vous pouvez activer les deux modules pour vous-même.

Si vous êtes un administrateur général ou un administrateur Exchange Online et que Exchange est configuré pour utiliser l’authentification OAuth, vous pouvez activer le module de signalement des messages et le module de signalement du hameçonnage pour votre organisation. Les deux modules sont désormais disponibles via [le déploiement centralisé.](../../admin/manage/centralized-deployment-of-add-ins.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Le add-in Report Message et le add-in Report Phishing fonctionnent avec la plupart Microsoft 365 abonnements et les produits suivants :
  - Outlook sur le web
  - Outlook 2013 SP1 ou une ultérieure
  - Outlook 2016 pour Mac
  - Outlook incluses dans Microsoft 365 applications pour Enterprise
  - Outlook application pour iOS et Android

- Les deux modules ne sont pas disponibles pour les boîtes aux lettres partagées ou les boîtes aux lettres dans des organisations Exchange locales.

- Votre navigateur web existant doit fonctionner à la fois avec les modules de rapport de message et de signalement du hameçonnage. Toutefois, si vous remarquez que le module n’est pas disponible ou ne fonctionne pas comme prévu, essayez un autre navigateur.

- Pour les installation organisationnelles, l’organisation doit être configurée pour utiliser l’authentification OAuth. Pour plus d’informations, [voir Determine if Centralized Deployment of add-ins works for your organization](../../admin/manage/centralized-deployment-of-add-ins.md).

- Les administrateurs doivent être membres du groupe de rôles Administrateurs globaux. Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

- Pour plus d’informations sur la façon de signaler un message à l’aide de la fonctionnalité Signaler un message, voir Signaler les faux positifs et les [faux négatifs dans Outlook](report-false-positives-and-false-negatives.md).

> [!IMPORTANT]
> Nous ne recommandons pas l’expérience de rapport intégrée dans Outlook car elle ne peut pas utiliser la stratégie de [soumission d’utilisateur.](./user-submission.md) Nous vous recommandons plutôt d’utiliser le add-in Report Message ou report Phishing.

## <a name="get-the-report-message-add-in"></a>Obtenir le add-in Message de rapport

### <a name="get-the-add-in-for-yourself"></a>Obtenir le add-in pour vous-même

1. Go to the Microsoft AppSource at <https://appsource.microsoft.com/marketplace/apps> and search for the Report Message add-in. To go directly to the Report Message add-in, go to <https://appsource.microsoft.com/product/office/wa104381180> .

2. Cliquez **sur GET IT NOW**.

   ![Message de rapport : l’obtenir maintenant](../../media/ReportMessageGETITNOW.png)

3. Dans la boîte de dialogue qui s’affiche, examinez les conditions d’utilisation et la politique de confidentialité, puis cliquez sur **Continuer**.

4. Connectez-vous à l’aide de votre compte scolaire ou scolaire (pour une utilisation professionnelle) ou de votre compte Microsoft (pour un usage personnel).

Une fois que le module est installé et activé, les icônes suivantes s’offrent à vous :

- Dans Outlook, l’icône ressemble à ceci :

  > [!div class="mx-imgBorder"]
  > ![Icône signaler le Outlook](../../media/OutlookReportMessageIcon.png)

- Dans Outlook sur le web, l’icône ressemble à ceci :

  > [!div class="mx-imgBorder"]
  > ![Outlook sur l’icône du add-in Message de rapport web](../../media/owa-report-message-icon.png)

### <a name="get-the-add-in-for-your-organization"></a>Obtenir le add-in pour votre organisation

> [!NOTE]
> L’apparition du module dans votre organisation peut prendre jusqu’à 12 heures.

1. Dans le Microsoft 365 d’administration, allez à  la page Paramètres de l’utilisateur à \>  l’adresse <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns> suivante : Si vous ne voyez pas la page Des  applications intégrées, **rendez-vous** sur le lien Paramètres Applications intégrées en haut de la \>  \>  page **Applications intégrées.**

2. Sélectionnez **Déployer le add-in** en haut de la page, puis sélectionnez **Suivant**.

   ![Page Services et add-ins dans le centre d Microsoft 365'administration](../../media/ServicesAddInsPageNewM365AdminCenter.png)

3. Dans le **volant Déployer un** nouveau module complémentaire qui s’affiche, examinez les informations, puis cliquez sur **Suivant**.

4. Sur la page suivante, cliquez **sur Choisir dans le Store.**

   ![Déployer une nouvelle page de modules](../../media/NewAddInScreen2.png)

5. Dans la page **Sélectionner un add-in** qui s’affiche, cliquez dans la zone De recherche, entrez Message de rapport, puis cliquez sur **Icône**   ![ ](../../media/search-icon.png) Rechercher. Dans la liste des résultats, recherchez Message de **rapport,** puis cliquez sur **Ajouter.**

   ![Sélectionner des résultats de recherche de add-in](../../media/NewAddInScreen3.png)

6. Dans la boîte de dialogue qui s’affiche, examinez les informations de licence et de confidentialité, puis cliquez sur **Continuer**.

7. Dans la page **Configurer le add-in** qui s’affiche, configurez les paramètres suivants :

   - **Utilisateurs affectés**: sélectionnez l’une des valeurs suivantes :

     - **Tout le monde** (par défaut)
     - **Utilisateurs/groupes spécifiques**
     - **Juste moi**

   - **Méthode de déploiement**: sélectionnez l’une des valeurs suivantes :

     - **Fixe (par défaut)**: le add-in est automatiquement déployé sur les utilisateurs spécifiés et ils ne peuvent pas le supprimer.
     - **Disponible**: les utilisateurs peuvent installer le add-in sur **Home** \> **Get add-ins** \> **géré par l’administrateur.**
     - **Facultatif**: le add-in est automatiquement déployé pour les utilisateurs spécifiés, mais ils peuvent choisir de le supprimer.

   ![Configurer la page de l’ajout](../../media/configure-add-in.png)

   Lorsque vous avez terminé, cliquez sur **Déployer.**

8. Dans la page Déployer le **message** de rapport qui s’affiche, vous verrez un rapport d’avancement suivi d’une confirmation du déploiement du module. Après avoir lu les informations, cliquez sur **Suivant**.

   ![Page Déployer le message de rapport](../../media/deploy-report-message-page.png)

9. Dans la page **Annoncer le add-in** qui s’affiche, examinez les informations, puis cliquez sur **Fermer**.

   ![Page Annoncer le add-in](../../media/announce-add-in-page.png)

## <a name="review-or-edit-settings-for-the-report-message-add-in"></a>Passer en revue ou modifier les paramètres du add-in Message de rapport

1. Dans le Microsoft 365 d’administration, allez à  la page Paramètres de l’utilisateur à \>  l’adresse <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns> suivante : Si vous ne voyez pas la page Des  applications intégrées, **rendez-vous** sur le lien Paramètres Applications intégrées en haut de la \>  \>  page **Applications intégrées.**

   ![Page Services et Add-Ins dans le nouveau Centre Microsoft 365'administration](../../media/ServicesAddInsPageNewM365AdminCenter.png)

2. Recherchez et sélectionnez le add-in **Message** de rapport.

3. Dans le **volant Modifier le message** de rapport qui s’affiche, examinez et modifiez les paramètres selon le cas pour votre organisation. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   ![Paramètres pour le add-in Report Message](../../media/EditReportMessageAddIn.png)

## <a name="get-the-report-phishing-add-in"></a>Obtenir le module de signalement du hameçonnage

### <a name="get-the-add-in-for-yourself"></a>Obtenir le add-in pour vous-même

1. Go to the Microsoft AppSource at <https://appsource.microsoft.com/marketplace/apps> and search for the Report Phishing add-in.

2. Cliquez **sur GET IT NOW**.

3. Dans la boîte de dialogue qui s’affiche, examinez les conditions d’utilisation et la politique de confidentialité, puis cliquez sur **Continuer**.

4. Connectez-vous à l’aide de votre compte scolaire ou scolaire (pour une utilisation professionnelle) ou de votre compte Microsoft (pour un usage personnel).

Une fois que le module est installé et activé, les icônes suivantes s’offrent à vous :

- Dans Outlook, l’icône ressemble à ceci :

  ![Icône signaler le hameçonnage du Outlook](../../media/Outlook-ReportPhishing.png)

- Dans Outlook sur le web, l’icône ressemble à ceci :

  > [!div class="mx-imgBorder"]
  > ![Outlook sur l’icône du add-in Rapport de hameçonnage sur le web](../../media/OWA-ReportPhishing.png)

### <a name="get-the-add-in-for-your-organization"></a>Obtenir le add-in pour votre organisation

> [!NOTE]
> L’apparition du module dans votre organisation peut prendre jusqu’à 12 heures.

1. Dans le Microsoft 365 d’administration, allez à  la page Paramètres de l’utilisateur à \>  l’adresse <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns> suivante : Si vous ne voyez pas la page Des  applications intégrées, **rendez-vous** sur le lien Paramètres Applications intégrées en haut de la \>  \>  page **Applications intégrées.**

2. Sélectionnez **Déployer le add-in** en haut de la page, puis sélectionnez **Suivant**.

   ![Page Services et add-ins dans le centre d’administration Microsoft 365'administration](../../media/ServicesAddInsPageNewM365AdminCenter.png)

3. Dans le **volant Déployer un** nouveau module complémentaire qui s’affiche, examinez les informations, puis cliquez sur **Suivant**.

4. Sur la page suivante, cliquez sur **Choisir dans le Store.**

   ![Déployer une nouvelle page de modules](../../media/NewAddInScreen2.png)

5. Dans la page Sélectionner un **add-in** qui s’affiche, cliquez dans  la zone De recherche, entrez  **Hameçonnage** de rapport, puis cliquez sur Icône ![ ](../../media/search-icon.png) Recherche. Dans la liste des résultats, recherchez **l’hameçonnage** de rapport, puis cliquez sur **Ajouter.**

6. Dans la boîte de dialogue qui s’affiche, examinez les informations de licence et de confidentialité, puis cliquez sur **Continuer**.

7. Dans la page **Configurer le module de** configuration qui s’affiche, configurez les paramètres suivants :

   - **Utilisateurs affectés**: sélectionnez l’une des valeurs suivantes :

     - **Tout le monde** (par défaut)
     - **Utilisateurs/groupes spécifiques**
     - **Juste moi**

   - **Méthode de déploiement**: sélectionnez l’une des valeurs suivantes :

     - **Fixe (par défaut)**: le add-in est automatiquement déployé pour les utilisateurs spécifiés et ils ne peuvent pas le supprimer.
     - **Disponible**: les utilisateurs peuvent installer le add-in sur **home** \> **get add-ins** \> **admin-managed**.
     - **Facultatif**: le add-in est automatiquement déployé pour les utilisateurs spécifiés, mais ils peuvent choisir de le supprimer.

   Lorsque vous avez terminé, cliquez sur **Déployer.**

8. Dans la page **Déployer** le hameçonnage de rapport qui s’affiche, vous verrez un rapport d’avancement suivi d’une confirmation du déploiement du module. Après avoir lu les informations, cliquez sur **Suivant**.

9. Dans la page **Annoncer le add-in** qui s’affiche, examinez les informations, puis cliquez sur **Fermer**.

## <a name="review-or-edit-settings-for-the-report-phishing-add-in"></a>Examiner ou modifier les paramètres du module de signalement du hameçonnage

1. Dans le Microsoft 365 d’administration, allez à  la page Paramètres de l’utilisateur à \>  l’adresse <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns> suivante : Si vous ne voyez pas la page Des  applications intégrées, **rendez-vous** sur le lien Paramètres Applications intégrées en haut de la \>  \>  page **Applications intégrées.**

2. Recherchez et sélectionnez **le** module de signalement du hameçonnage.

3. Dans le flyout **Modifier le hameçonnage** du rapport qui s’affiche, examinez et modifiez les paramètres selon le cas pour votre organisation. Lorsque vous avez terminé, cliquez sur **Enregistrer**.
