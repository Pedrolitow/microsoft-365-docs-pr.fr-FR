---
title: Activez le complément Signaler un message
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
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
description: Découvrez comment activer le add-in Message de rapport pour Outlook et Outlook sur le web, pour des utilisateurs individuels ou pour l’ensemble de votre organisation.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4e85af902eaaa41eb82acf8d4b4baedc538e7888
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51204043"
---
# <a name="enable-the-report-message-add-in"></a>Activez le complément Signaler un message

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Si vous êtes un administrateur d’une organisation Microsoft 365 avec des boîtes aux lettres Exchange Online, nous vous recommandons d’utiliser le portail Soumissions dans le Centre de sécurité & conformité. Pour plus d’informations, voir Utiliser la soumission d’administrateur pour soumettre des messages suspects de courrier indésirable, d’hameçonnage, d’URL et [de fichiers à Microsoft.](admin-submission.md)

Les add-ins Signaler le message et Signaler le hameçonnage pour Outlook et Outlook sur le web (anciennement Outlook Web App) permettent aux utilisateurs de signaler facilement les faux positifs (messages électroniques de qualité marqués comme faux) ou les faux négatifs (courrier électronique non autorisé) à Microsoft et à ses affiliés pour analyse.

Microsoft utilise ces soumissions pour améliorer l’efficacité des technologies de protection de la messagerie. Par exemple, si des personnes signalent un grand nombre de messages marqués comme courrier indésirable à l’aide du add-in Signaler un message, l’équipe de sécurité de votre organisation devra peut-être ajuster les stratégies [anti-courrier](configure-your-spam-filter-policies.md)indésirable.

Vous pouvez installer le module de rapport de message ou de signalement du hameçonnage. Si vous souhaitez que vos utilisateurs signalent uniquement les messages de hameçonnage, déployez le module de signalement du hameçonnage dans votre organisation. Pour plus d’informations, [voir Enable the Report Phishing add-in](enable-the-report-phish-add-in.md).

Le add-in Report Message offre la possibilité de signaler les messages de courrier indésirable et de hameçonnage. Les administrateurs peuvent activer le add-in Message de rapport pour l’organisation, et les utilisateurs individuels peuvent l’installer eux-mêmes.

Si vous êtes un utilisateur individuel, vous pouvez activer le add-in Message de rapport [pour vous-même.](#get-the-report-message-add-in-for-yourself)

Si vous êtes un administrateur général ou un administrateur Exchange Online et qu’Exchange est configuré pour utiliser l’authentification OAuth, vous pouvez activer le [add-in](#get-and-enable-the-report-message-add-in-for-your-organization)Message de rapport pour votre organisation. Le message de Add-In est désormais disponible via [le déploiement centralisé.](../../admin/manage/centralized-deployment-of-add-ins.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Le add-in Message de rapport fonctionne avec la plupart des abonnements Microsoft 365 et les produits suivants :

  - Outlook sur le web
  - Outlook 2013 SP1 ou une édition ultérieure
  - Outlook 2016 pour Mac
  - Outlook inclus dans les applications Microsoft 365 pour Entreprise
  - Application Outlook pour iOS et Android

- Le module de rapport de message n’est pas disponible pour les boîtes aux lettres partagées ou les boîtes aux lettres dans les organisations Exchange locales.

- Vous pouvez configurer la copie ou la redirection des messages signalés vers une boîte aux lettres que vous spécifiez. Pour plus d’informations, voir [Stratégies d’envoi des utilisateurs.](user-submission.md)

- Votre navigateur web existant doit fonctionner avec le add-in Message de rapport. Toutefois, si vous remarquez que le module n’est pas disponible ou ne fonctionne pas comme prévu, essayez un autre navigateur.

- Pour les installation organisationnelles, l’organisation doit être configurée pour utiliser l’authentification OAuth. Pour plus d’informations, [voir Determine if Centralized Deployment of add-ins works for your organization.](../../admin/manage/centralized-deployment-of-add-ins.md)

- Les administrateurs doivent être membres du groupe de rôles Administrateurs globaux. Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

## <a name="get-the-report-message-add-in-for-yourself"></a>Obtenir le add-in Message de rapport pour vous-même

1. Go to the Microsoft AppSource at <https://appsource.microsoft.com/marketplace/apps> and search for the Report Message add-in. To go directly to the Report Message add-in, go to <https://appsource.microsoft.com/product/office/wa104381180> .

2. Cliquez **sur GET IT NOW**.

   ![Message de rapport : l’obtenir maintenant](../../media/ReportMessageGETITNOW.png)

3. Dans la boîte de dialogue qui s’affiche, examinez les conditions d’utilisation et la politique de confidentialité, puis cliquez sur **Continuer**.

4. Connectez-vous à l’aide de votre compte scolaire ou scolaire (pour une utilisation professionnelle) ou de votre compte Microsoft (pour un usage personnel).

Une fois que le module est installé et activé, les icônes suivantes s’offrent à vous :

- Dans Outlook, l’icône ressemble à ceci :

  ![Icône signaler le add-in Message pour Outlook](../../media/OutlookReportMessageIcon.png)

- Dans Outlook sur le web, l’icône ressemble à ceci :

  ![Icône du add-in Message de rapport Outlook sur le web](../../media/d9326d0b-1769-4bc2-ae58-51f0ebc69a17.png)

Pour savoir comment utiliser le add-in, voir Utiliser le [add-in Message de rapport.](https://support.microsoft.com/office/b5caa9f1-cdf3-4443-af8c-ff724ea719d2)

## <a name="get-and-enable-the-report-message-add-in-for-your-organization"></a>Obtenir et activer le add-in Message de rapport pour votre organisation

> [!NOTE]
> L’apparition du module dans votre organisation peut prendre jusqu’à 12 heures.

1. Dans le Centre d’administration Microsoft 365, rendez-vous sur la page **Paramètres** des applications à l’adresse suivante : Si vous ne voyez pas la page Des applications \>  <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns> intégrées,   \>  \> **rendez-vous**  sur le lien Paramètres applications intégrées en haut de la page Applications intégrées.

2. Sélectionnez **Déployer le add-in** en haut de la page, puis sélectionnez **Suivant**.

   ![Page Services et modules dans le Centre d’administration Microsoft 365](../../media/ServicesAddInsPageNewM365AdminCenter.png)

3. Dans le **volant Déployer un** nouveau module complémentaire qui s’affiche, examinez les informations, puis cliquez sur **Suivant**.

4. Sur la page suivante, cliquez sur **Choisir dans le Store.**

   ![Déployer une nouvelle page de modules](../../media/NewAddInScreen2.png)

5. Dans la page **Sélectionner un add-in** qui s’affiche, cliquez dans la zone De recherche, entrez Message de rapport, puis cliquez sur **Icône**   ![ ](../../media/search-icon.png) Rechercher. Dans la liste des résultats, recherchez Message de **rapport,** puis cliquez sur **Ajouter.**

   ![Sélectionner les résultats de la recherche de add-in](../../media/NewAddInScreen3.png)

6. Dans la boîte de dialogue qui s’affiche, examinez les informations de licence et de confidentialité, puis cliquez sur **Continuer**.

7. Dans la page **Configurer le add-in** qui s’affiche, configurez les paramètres suivants :

   - **Utilisateurs affectés**: sélectionnez l’une des valeurs suivantes :

     - **Tout le monde** (par défaut)
     - **Utilisateurs/groupes spécifiques**
     - **Juste moi**

   - **Méthode de déploiement**: sélectionnez l’une des valeurs suivantes :

     - **Fixe (par défaut)**: le add-in est automatiquement déployé sur les utilisateurs spécifiés et ils ne peuvent pas le supprimer.
     - **Disponible**: les utilisateurs peuvent installer le add-in sur **home** \> **get add-ins** \> **admin-managed**.
     - **Facultatif**: le add-in est automatiquement déployé pour les utilisateurs spécifiés, mais ils peuvent choisir de le supprimer.

   ![Configurer la page de l’ajout](../../media/configure-add-in.png)

   Lorsque vous avez terminé, cliquez sur **Déployer.**

8. Dans la page Déployer le **message** de rapport qui s’affiche, vous verrez un rapport d’avancement suivi d’une confirmation du déploiement du module. Après avoir lu les informations, cliquez sur **Suivant**.

   ![Page Déployer le message de rapport](../../media/deploy-report-message-page.png)

9. Dans la page **Annoncer le add-in** qui s’affiche, examinez les informations, puis cliquez sur **Fermer**.

   ![Page Annoncer le add-in](../../media/announce-add-in-page.png)

## <a name="learn-how-to-use-the-report-message-add-in"></a>Découvrez comment utiliser le add-in Message de rapport

Les personnes à qui le add-in est affecté voient les icônes suivantes :

- Dans Outlook, l’icône ressemble à ceci :

  ![Icône Signaler le add-in de message pour Outlook](../../media/OutlookReportMessageIcon.png)

- Dans Outlook sur le web, l’icône ressemble à ceci :

  ![Icône De message Outlook sur le web](../../media/d9326d0b-1769-4bc2-ae58-51f0ebc69a17.png)

Lorsque vous informez les utilisateurs du add-in Message de rapport, incluez un lien pour utiliser le [add-in Message de rapport.](https://support.microsoft.com/office/b5caa9f1-cdf3-4443-af8c-ff724ea719d2)

## <a name="review-or-edit-settings-for-the-report-message-add-in"></a>Passer en revue ou modifier les paramètres du add-in Message de rapport

1. Dans le Centre d’administration Microsoft 365, rendez-vous sur la page **Paramètres** des applications à l’adresse suivante : Si vous ne voyez pas la page Des applications \>  <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns> intégrées,   \>  \> **rendez-vous**  sur le lien Paramètres applications intégrées en haut de la page Applications intégrées.

   ![Page Services et Add-Ins dans le nouveau Centre d’administration Microsoft 365](../../media/ServicesAddInsPageNewM365AdminCenter.png)

2. Recherchez et sélectionnez le add-in **Message** de rapport.

3. Dans le **volant Modifier le message** de rapport qui s’affiche, examinez et modifiez les paramètres selon le cas pour votre organisation. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   ![Paramètres du add-in Message de rapport](../../media/EditReportMessageAddIn.png)

## <a name="view-and-review-reported-messages"></a>Afficher et examiner les messages signalés

Pour passer en revue les messages que les utilisateurs signalent à Microsoft, vous avez les options ci-après :

- Utilisez le portail Soumissions d’administrateur. Pour plus d’informations, voir [Afficher les soumissions d’utilisateurs à Microsoft.](admin-submission.md#view-user-submissions-to-microsoft)

- Créez une règle de flux de messagerie (également appelée règle de transport) pour envoyer des copies des messages signalés. Pour obtenir des instructions, voir Utiliser des règles de flux de messagerie pour voir ce [que vos utilisateurs rapportent à Microsoft.](use-mail-flow-rules-to-see-what-your-users-are-reporting-to-microsoft.md)
