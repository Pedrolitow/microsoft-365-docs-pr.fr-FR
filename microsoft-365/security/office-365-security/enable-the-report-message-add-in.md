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
description: Découvrez comment activer le message de rapport ou les modules de signalement du hameçonnage pour Outlook et Outlook sur le web, pour des utilisateurs individuels ou pour l’ensemble de votre organisation.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f7c077521700a8bd4c7d1997bb87bab0f214337d
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58563789"
---
# <a name="enable-the-report-message-or-the-report-phishing-add-ins"></a>Activer le message de rapport ou les modules de signalement du hameçonnage

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Si vous êtes un administrateur d’une organisation Microsoft 365 avec des boîtes aux lettres Exchange Online, nous vous recommandons d’utiliser la page **Soumissions** dans le portail Microsoft 365 Defender. Pour plus d’informations, voir Utiliser la soumission d’administrateur pour soumettre des messages suspects de courrier indésirable, d’hameçonnage, d’URL et [de fichiers à Microsoft.](admin-submission.md)

Les modules de signalement des messages et du hameçonnage pour Outlook et Outlook sur le web (anciennement appelés Outlook Web App) permettent aux utilisateurs de signaler facilement les faux positifs (messages électroniques de qualité marqués comme faux) ou les faux négatifs (courriers électroniques erronés autorisés) à Microsoft et à ses affiliés pour analyse.

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
  - Outlook 2016 pour Mac
  - Outlook incluses dans Microsoft 365 applications pour Enterprise
  - Outlook application pour iOS et Android

- Les deux modules ne sont pas disponibles pour les boîtes aux lettres partagées ou les boîtes aux lettres dans des organisations Exchange locales.

- Votre navigateur web existant doit fonctionner à la fois avec les add-ins Message de rapport et Signaler le hameçonnage. Toutefois, si vous remarquez que le module n’est pas disponible ou ne fonctionne pas comme prévu, essayez un autre navigateur.

- Pour les installation organisationnelles, l’organisation doit être configurée pour utiliser l’authentification OAuth. Pour plus d’informations, [voir Determine if Centralized Deployment of add-ins works for your organization](../../admin/manage/centralized-deployment-of-add-ins.md).

- Les administrateurs doivent être membres du groupe de rôles Administrateurs globaux. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

- Pour plus d’informations sur la façon de signaler un message à l’aide de la fonctionnalité Signaler un message, voir Signaler les faux positifs et les [faux négatifs dans Outlook](report-false-positives-and-false-negatives.md).

- Les organisations qui ont une solution de filtrage d’URL ou de sécurité (telle que Proxy et FireWall) doivent avoir des points de terminaison ipagave.azurewebsites.net et outlook.office.com autorisés à être atteints sur le protocole HTTPS.


> [!IMPORTANT]
> Nous vous déconseillons d’utiliser l’expérience de rapport intégrée dans Outlook car elle ne peut pas utiliser la stratégie de [soumission d’utilisateur.](./user-submission.md) Nous vous recommandons plutôt d’utiliser le add-in Report Message ou report Phishing.

## <a name="get-the-report-message-add-in"></a>Obtenir le add-in Message de rapport

### <a name="get-the-report-message-add-in-for-yourself"></a>Obtenir le add-in Message de rapport pour vous-même

1. Go to the Microsoft AppSource at <https://appsource.microsoft.com/marketplace/apps> and search for the Report Message add-in. To go directly to the Report Message add-in, go to <https://appsource.microsoft.com/product/office/wa104381180> .

2. Cliquez **sur GET IT NOW**.

   ![Message de rapport - Obtenez-le maintenant.](../../media/ReportMessageGETITNOW.png)

3. Dans la boîte de dialogue qui s’affiche, examinez les conditions d’utilisation et la politique de confidentialité, puis cliquez sur **Continuer**.

4. Connectez-vous à l’aide de votre compte scolaire ou scolaire (pour une utilisation professionnelle) ou de votre compte Microsoft (pour un usage personnel).

Une fois le add-in installé et activé, les icônes suivantes s’offrent à vous :

- Dans Outlook, l’icône ressemble à ceci :

  > [!div class="mx-imgBorder"]
  > ![Icône signaler le Outlook.](../../media/OutlookReportMessageIcon.png)

- Dans Outlook sur le web, l’icône ressemble à ceci :

  > [!div class="mx-imgBorder"]
  > ![Outlook sur le web Icône Signaler le add-in Message.](../../media/owa-report-message-icon.png)

### <a name="get-the-report-message-add-in-for-your-organization"></a>Obtenir le add-in Message de rapport pour votre organisation

> [!NOTE]
> L’apparition du module dans votre organisation peut prendre jusqu’à 12 heures.

1. In the Centre d’administration Microsoft 365, go to the **Paramètres** \> **Add-ins** page at <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns> . Si vous ne voyez pas la page Des  applications intégrées, **rendez-vous** sur le lien Paramètres Applications intégrées en haut de la \>  \>  page **Applications intégrées.**

2. Sélectionnez **Déployer le add-in** en haut de la page, puis sélectionnez **Suivant**.

   ![Page Services et modules dans la Centre d’administration Microsoft 365.](../../media/ServicesAddInsPageNewM365AdminCenter.png)

3. Dans le **volant Déployer un** nouveau module complémentaire qui s’affiche, examinez les informations, puis cliquez sur **Suivant**.

4. Sur la page suivante, cliquez sur **Choisir dans le Store.**

   ![Déployez une nouvelle page de add-in.](../../media/NewAddInScreen2.png)

5. Dans la page Sélectionner **un add-in** qui s’affiche, cliquez  dans la zone De recherche, entrez Message de **rapport,** puis cliquez sur Icône  ![ Rechercher. ](../../media/search-icon.png) Dans la liste des résultats, recherchez Message de **rapport,** puis cliquez sur **Ajouter.**

   ![Sélectionnez les résultats de la recherche de add-in.](../../media/NewAddInScreen3.png)

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

   ![Configurez la page du module de recherche.](../../media/configure-add-in.png)

   Lorsque vous avez terminé, cliquez sur **Déployer.**

8. Dans la page Déployer le **message** de rapport qui s’affiche, vous verrez un rapport d’avancement suivi d’une confirmation du déploiement du module. Après avoir lu les informations, cliquez sur **Suivant**.

   ![Page Déployer le message de rapport.](../../media/deploy-report-message-page.png)

9. Dans la page **Annoncer le add-in** qui s’affiche, examinez les informations, puis cliquez sur **Fermer**.

   ![Page Annoncer le add-in.](../../media/announce-add-in-page.png)

## <a name="review-or-edit-settings-for-the-report-message-add-in"></a>Passer en revue ou modifier les paramètres du add-in Message de rapport

1. In the Centre d’administration Microsoft 365, go to the go to the **Paramètres** \> **Add-ins** page at <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns> . Si vous ne voyez pas la page Des  applications intégrées, **rendez-vous** sur le lien Paramètres Applications intégrées en haut de la \>  \>  page **Applications intégrées.**

   ![Services et Add-Ins page dans le nouveau centre Administration Microsoft 365 web.](../../media/ServicesAddInsPageNewM365AdminCenter.png)

2. Recherchez et sélectionnez le add-in **Message** de rapport.

3. Dans le **volant Modifier le message** de rapport qui s’affiche, examinez et modifiez les paramètres selon le cas pour votre organisation. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   ![Paramètres pour le add-in Report Message.](../../media/EditReportMessageAddIn.png)

## <a name="get-the-report-phishing-add-in"></a>Obtenir le module de signalement du hameçonnage

### <a name="get-the-report-phishing-add-in-for-yourself"></a>Obtenir le module de signalement du hameçonnage par vous-même

1. Go to the Microsoft AppSource at <https://appsource.microsoft.com/marketplace/apps> and search for the Report Phishing add-in.

2. Cliquez **sur GET IT NOW**.

3. Dans la boîte de dialogue qui s’affiche, examinez les conditions d’utilisation et la politique de confidentialité, puis cliquez sur **Continuer**.

4. Connectez-vous à l’aide de votre compte scolaire ou scolaire (pour une utilisation professionnelle) ou de votre compte Microsoft (pour un usage personnel).

Une fois le add-in installé et activé, les icônes suivantes s’offrent à vous :

- Dans Outlook, l’icône ressemble à ceci :

  ![Signaler l’icône du Outlook.](../../media/Outlook-ReportPhishing.png)

- Dans Outlook sur le web, l’icône ressemble à ceci :

  > [!div class="mx-imgBorder"]
  > ![Outlook sur le web Icône Signaler le module de hameçonnage.](../../media/OWA-ReportPhishing.png)

### <a name="get-the-report-phishing-add-in-for-your-organization"></a>Obtenir le module de signalement du hameçonnage pour votre organisation

> [!NOTE]
> L’apparition du module dans votre organisation peut prendre jusqu’à 12 heures.

1. In the Centre d’administration Microsoft 365, go to the go to the **Paramètres** \> **Add-ins** page at <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns> . Si vous ne voyez pas la page Des  applications intégrées, **rendez-vous** sur le lien Paramètres Applications intégrées en haut de la \>  \>  page **Applications intégrées.**

2. Sélectionnez **Déployer le add-in** en haut de la page, puis sélectionnez **Suivant**.

   ![Page Services et modules dans la Centre d’administration Microsoft 365.](../../media/ServicesAddInsPageNewM365AdminCenter.png)

3. Dans le **volant Déployer un** nouveau module complémentaire qui s’affiche, examinez les informations, puis cliquez sur **Suivant**.

4. Sur la page suivante, cliquez sur **Choisir dans le Store.**

   ![Déployez une nouvelle page de add-in.](../../media/NewAddInScreen2.png)

5. Dans la page Sélectionner **un add-in** qui s’affiche, cliquez dans la zone de recherche, entrez **Signaler** le hameçonnage, puis cliquez sur  l’icône  ![ Rechercher. ](../../media/search-icon.png) Dans la liste des résultats, recherchez **l’hameçonnage** de rapport, puis cliquez sur **Ajouter.**

6. Dans la boîte de dialogue qui s’affiche, examinez les informations de licence et de confidentialité, puis cliquez sur **Continuer**.

7. Dans la page **Configurer le module de** configuration qui s’affiche, configurez les paramètres suivants :

   - **Utilisateurs affectés**: sélectionnez l’une des valeurs suivantes :
     - **Tout le monde** (par défaut)
     - **Utilisateurs/groupes spécifiques**
     - **Juste moi**

   - **Méthode de déploiement**: sélectionnez l’une des valeurs suivantes :
     - **Fixe (par défaut)**: le add-in est automatiquement déployé sur les utilisateurs spécifiés et ils ne peuvent pas le supprimer.
     - **Disponible**: les utilisateurs peuvent installer le add-in sur **home** \> **get add-ins** \> **admin-managed**.
     - **Facultatif**: le add-in est automatiquement déployé pour les utilisateurs spécifiés, mais ils peuvent choisir de le supprimer.

   Lorsque vous avez terminé, cliquez sur **Déployer.**

8. Dans la page **Déployer** le hameçonnage de rapport qui s’affiche, vous verrez un rapport d’avancement suivi d’une confirmation du déploiement du module. Après avoir lu les informations, cliquez sur **Suivant**.

9. Dans la page **Annoncer le add-in** qui s’affiche, examinez les informations, puis cliquez sur **Fermer**.

## <a name="review-or-edit-settings-for-the-report-phishing-add-in"></a>Examiner ou modifier les paramètres du module de signalement du hameçonnage

1. In the Centre d’administration Microsoft 365, go to the go to the **Paramètres** \> **Add-ins** page at <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns> . Si vous ne voyez pas la page Des  applications intégrées, **rendez-vous** sur le lien Paramètres Applications intégrées en haut de la \>  \>  page **Applications intégrées.**

2. Recherchez et sélectionnez **le** module de signalement du hameçonnage.

3. Dans le volant **Modifier le hameçonnage** du rapport qui s’affiche, examinez et modifiez les paramètres selon les cas de votre organisation. Lorsque vous avez terminé, cliquez sur **Enregistrer**.
