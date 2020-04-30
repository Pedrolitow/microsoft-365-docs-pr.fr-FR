---
title: Activez le complément Signaler un message
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 4250c4bc-6102-420b-9e0a-a95064837676
ms.collection:
- M365-security-compliance
description: Découvrez comment activer le complément de message de rapport pour Outlook et Outlook sur le Web, pour des utilisateurs individuels ou l’ensemble de votre organisation.
ms.openlocfilehash: 22ce1c8e8084cb0bcbcb2f9fa4c0c80e1a59bf9c
ms.sourcegitcommit: c7f11d851073ef14a69669f6c8b7e0c11e4bb7a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "43939474"
---
# <a name="enable-the-report-message-add-in"></a>Activez le complément Signaler un message

> [!NOTE]
> Si vous êtes administrateur d’une organisation avec des boîtes aux lettres Exchange Online, nous vous recommandons d’utiliser le portail d’envoi du centre de sécurité & conformité. Pour plus d’informations, consultez la rubrique [utiliser la soumission de l’administrateur pour envoyer des courriers indésirables, des hameçons, des URL et des fichiers à Microsoft](admin-submission.md).

Le complément de message de rapport pour Outlook et Outlook sur le Web (anciennement appelé Outlook Web App) permet aux utilisateurs de signaler facilement les faux positifs (courrier électronique marqué comme incorrect) ou les faux négatifs (courrier incorrect autorisé) à Microsoft et à ses filiales pour analyse. Microsoft utilise ces soumissions pour améliorer l’efficacité des technologies de protection de la messagerie.

Par exemple, supposons que des personnes signalent un grand nombre de messages comme hameçonnage. Ces informations sont représentées dans le [tableau de bord de sécurité](security-dashboard.md) et d’autres rapports. L’équipe de sécurité de votre organisation peut utiliser ces informations pour indiquer que les stratégies de détection d’hameçonnage doivent être mises à jour. Ou bien, si des personnes signalent un grand nombre de messages marqués comme légitimes comme légitimes à l’aide du complément de message de rapport, il se peut que l’équipe de sécurité de votre organisation doive ajuster les [stratégies de blocage du courrier](configure-your-spam-filter-policies.md)indésirable.

En outre, si votre organisation utilise [Office 365 Advanced Threat Protection Plan 1](office-365-atp.md) ou [plan 2](office-365-ti.md), le complément Report message fournit à l’équipe de sécurité de votre organisation des informations utiles qu’il peut utiliser pour examiner et mettre à jour les stratégies de sécurité.

Les administrateurs peuvent activer le complément de message de rapport pour l’organisation, et les utilisateurs individuels peuvent l’installer pour eux-mêmes.

Si vous êtes un utilisateur individuel, vous pouvez [activer le complément de rapport de message pour vous-même](#get-the-report-message-add-in-for-yourself).

Si vous êtes un administrateur général ou un administrateur Exchange Online et qu’Exchange est configuré pour utiliser l’authentification OAuth, vous pouvez [activer le complément de message de rapport pour votre organisation](#get-and-enable-the-report-message-add-in-for-your-organization). Le complément de message de rapport est désormais disponible via un [déploiement centralisé](https://docs.microsoft.com/office365/admin/manage/centralized-deployment-of-add-ins).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Le complément de message de rapport fonctionne avec la plupart des abonnements Microsoft 365 et les produits suivants :

  - Outlook sur le web
  - Outlook 2013 SP1 ou version ultérieure
  - Outlook 2016 pour Mac
  - Outlook inclus avec les applications Microsoft 365 pour les entreprises

- Le complément de message de rapport n’est pas disponible pour l’instant :

  - Boîtes aux lettres dans l’organisation Exchange locale
  - Abonnements GCC, GCC HIGH ou DoD

- Vous pouvez configurer la copie ou la redirection des messages signalés vers une boîte aux lettres que vous spécifiez. Pour plus d’informations, consultez [la rubrique spécifier une boîte aux lettres pour les soumissions utilisateur de messages de courrier indésirable et de hameçonnage dans Office 365](user-submission.md).

- Votre navigateur Web existant doit fonctionner avec le complément de message de rapport. Toutefois, si vous remarquez que le complément n’est pas disponible ou ne fonctionne pas comme prévu, essayez un autre navigateur.

- Pour les installations organisationnelles, l’organisation doit être configurée pour utiliser l’authentification OAuth. Pour plus d’informations, reportez-vous à [la rubrique déterminer si un déploiement centralisé de compléments fonctionne pour votre organisation](../../admin/manage/centralized-deployment-of-add-ins.md).

- Les administrateurs doivent être membres du groupe de rôles global admins. Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

## <a name="get-the-report-message-add-in-for-yourself"></a>Obtenir le complément de message de rapport pour vous-même

1. Accédez au site Microsoft AppSource à <https://appsource.microsoft.com/marketplace/apps> l’adresse et recherchez le complément de message de rapport. Pour accéder directement au complément de message de rapport, accédez à <https://appsource.microsoft.com/product/office/wa104381180>.

2. Cliquez sur **obtenir maintenant**.

   ![Message de rapport-Get it](../../media/ReportMessageGETITNOW.png)

3. Dans la boîte de dialogue qui s’affiche, passez en revue les conditions d’utilisation et la politique de confidentialité, puis cliquez sur **Continuer**.

4. Connectez-vous à l’aide de votre compte professionnel ou scolaire (pour une utilisation professionnelle) ou de votre compte Microsoft (pour une utilisation personnelle).

Une fois le complément installé et activé, les icônes suivantes s’affichent :

- Dans Outlook, l’icône se présente comme suit :

  ![Icône de complément de rapport de message pour Outlook](../../media/OutlookReportMessageIcon.png)

- Dans Outlook sur le Web, l’icône se présente comme suit :

  ![Icône de complément de message de rapport Web Outlook sur le Web](../../media/d9326d0b-1769-4bc2-ae58-51f0ebc69a17.png)

Pour savoir comment utiliser le complément, voir [use the Report message Add-in](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2).

## <a name="get-and-enable-the-report-message-add-in-for-your-organization"></a>Obtenir et activer le complément de message de rapport pour votre organisation

> [!NOTE]
> Le complément peut prendre jusqu’à 12 heures pour apparaître dans votre organisation.

1. Dans le centre d’administration Microsoft 365, accédez à la page <https://admin.microsoft.com/AdminPortal/Home#/Settings/ServicesAndAddIns>des **compléments de services &** , puis cliquez sur **déployer le complément**.

   ![Page services et compléments dans le centre d’administration Microsoft 365](../../media/ServicesAddInsPageNewM365AdminCenter.png)

2. Dans le menu **déroulant déployer un nouveau complément** qui s’affiche, passez en revue les informations, puis cliquez sur **suivant**.

3. Sur la page suivante, cliquez sur **choisir dans le Store**.

   ![Déployer une nouvelle page de complément](../../media/NewAddInScreen2.png)

4. Dans la page **Sélectionner un complément** qui s’affiche, cliquez sur dans la zone de **recherche** , entrez **message de rapport**, **puis cliquez sur** ![icône](../../media/search-icon.png)de recherche de recherche. Dans la liste des résultats, recherchez **message de rapport** , puis cliquez sur **Ajouter**.

   ![Sélectionner les résultats de la recherche de complément](../../media/NewAddInScreen3.png)

5. Dans la boîte de dialogue qui s’affiche, vérifiez les informations de licence et de confidentialité, puis cliquez sur **Continuer**.

6. Dans la page **configurer le complément** qui s’affiche, configurez les paramètres suivants :

   - **Utilisateurs affectés**: sélectionnez l’une des valeurs suivantes :

     - **Tout le monde** (par défaut)
     - **Utilisateurs/groupes spécifiques**
     - **Juste moi**

   - **Méthode de déploiement**: sélectionnez l’une des valeurs suivantes :

     - **Fixed (valeur par défaut)**: le complément est déployé automatiquement sur les utilisateurs spécifiés et ils ne peuvent pas le supprimer.
     - **Disponible**: les utilisateurs peuvent installer le complément à **leur domicile** \> **obtenir des compléments** \> **gérés par l’administrateur**.
     - **Facultatif**: le complément est déployé automatiquement sur les utilisateurs spécifiés, mais ils peuvent choisir de le supprimer.

   ![Page Configurer le complément](../../media/configure-add-in.png)

   Lorsque vous avez terminé, cliquez sur **déployer**.

7. Dans la page **déployer un message de rapport** qui s’affiche, vous verrez un rapport d’avancement suivi d’une confirmation de déploiement du complément. Une fois que vous avez lu les informations, cliquez sur **suivant**.

   ![Page déployer un message de rapport](../../media/deploy-report-message-page.png)

8. Sur la page **complément annonce** , vérifiez les informations, puis cliquez sur **Fermer**.

   ![Annoncer la page de complément](../../media/announce-add-in-page.png)

## <a name="learn-how-to-use-the-report-message-add-in"></a>En savoir plus sur l’utilisation du complément de message de rapport

Les personnes auxquelles le complément est attribué voient les icônes suivantes :

- Dans Outlook, l’icône se présente comme suit :

  ![Icône de complément de rapport de message pour Outlook](../../media/OutlookReportMessageIcon.png)

- Dans Outlook sur le Web, l’icône se présente comme suit :

  ![Icône de complément de message de rapport Web Outlook sur le Web](../../media/d9326d0b-1769-4bc2-ae58-51f0ebc69a17.png)

Lorsque vous informez les utilisateurs du complément Report message, incluez un lien permettant d' [utiliser le complément Report message](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2).

## <a name="review-or-edit-settings-for-the-report-message-add-in"></a>Vérifier ou modifier les paramètres du complément de message de rapport

1. Dans le centre d’administration Microsoft 365, accédez à la page des **compléments de Services &** à l’adresse <https://admin.microsoft.com/AdminPortal/Home#/Settings/ServicesAndAddIns>.

   ![Page services et compléments dans le nouveau centre d’administration Microsoft 365](../../media/ServicesAddInsPageNewM365AdminCenter.png)

2. Recherchez et sélectionnez le complément **Report message** .

3. Dans la fenêtre mobile **modifier un message** qui s’affiche, vérifiez et modifiez les paramètres en fonction de votre organisation. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   ![Paramètres du complément de message de rapport](../../media/EditReportMessageAddIn.png)

## <a name="view-and-review-reported-messages"></a>Afficher et consulter les messages signalés

Pour passer en revue les messages que les utilisateurs signalent à Microsoft, vous disposez des options suivantes :

- Utiliser le portail de soumission des administrateurs. Pour plus d’informations, consultez la rubrique [afficher les soumissions des utilisateurs à Microsoft](admin-submission.md#view-user-submissions-to-microsoft).

- Créer une règle de flux de messagerie (également appelée règle de transport) pour envoyer des copies des messages signalés. Pour obtenir des instructions, consultez [la rubrique utiliser des règles de flux de messagerie pour voir ce que vos utilisateurs signalent à Microsoft](use-mail-flow-rules-to-see-what-your-users-are-reporting-to-microsoft.md).
