---
title: Soumissions de l’administrateur
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser le portail d’envoi du centre de sécurité & conformité pour envoyer des e-mails suspects, des courriers électroniques de hameçonnage suspects, du courrier indésirable et d’autres messages potentiellement nuisibles, des URL et des fichiers à Microsoft à des fins d’analyse.
ms.openlocfilehash: 4d0737d881334db9cc4aeda43037ab89d7444618
ms.sourcegitcommit: c04f1207cfaddac2a9abef38967c17d689756a96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "46577869"
---
# <a name="use-admin-submission-to-submit-suspected-spam-phish-urls-and-files-to-microsoft"></a>Utilisez la soumission de l’administrateur pour soumettre des courriers indésirables, l’hameçonnage, des URL et des fichiers à Microsoft

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online, les administrateurs peuvent utiliser le portail d’envoi du centre de sécurité & conformité pour soumettre des messages électroniques, des URL et des pièces jointes à Microsoft pour analyse.

Lorsque vous soumettez un message électronique, vous obtenez des informations sur les stratégies susceptibles d’avoir autorisé le courrier entrant dans votre client, ainsi que sur l’examen de toutes les URL et pièces jointes du courrier. Les stratégies pouvant avoir autorisé un courrier incluent la liste des expéditeurs approuvés d’un utilisateur individuel, ainsi que des stratégies au niveau du client, telles que les règles de flux de messagerie Exchange (également appelées règles de transport).

Pour d’autres façons d’envoyer des messages électroniques, des URL et des pièces jointes à Microsoft, consultez la rubrique [signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page d' **envoi** , utilisez <https://protection.office.com/reportsubmission> .

- Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces procédures. décrites dans cette rubrique :

  - Pour envoyer des messages et des fichiers à Microsoft, vous devez être membre de l’un des groupes de rôles suivants :

    - **Gestion de l’organisation** ou **Administrateur de sécurité** dans le [Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).
    - **Gestion de l’organisation** ou **Gestion de l’hygiène** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups).

  - Pour un accès en lecture seule au portail des soumissions, vous devez être membre de l’un des groupes de rôles suivants :

    - **Lecteur de sécurité** dans le [Centre de conformité et sécurité](permissions-in-the-security-and-compliance-center.md).
    - **Gestion de l’organisation en affichage seul** dans[Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups).

- Pour plus d’informations sur la façon dont les utilisateurs peuvent envoyer des messages et des fichiers à Microsoft, consultez la rubrique [signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="report-suspicious-content-to-microsoft"></a>Signaler du contenu suspect à Microsoft

1. Dans le centre de sécurité & conformité, accédez à **gestion des menaces** - \> **vérifier** \> **les messages d’envoi**de l’administrateur.

2. Sur la page des **envois** qui s’affiche, cliquez sur le bouton **nouvelle soumission** .

3. Utilisez le menu volant **nouvelle soumission** qui apparaît pour envoyer le message, l’URL ou la pièce jointe, comme décrit dans les sections suivantes.

### <a name="submit-a-questionable-email-to-microsoft"></a>Envoyer un courrier électronique en question à Microsoft

1. Dans la section **type d’objet** , sélectionnez **courrier électronique**. Dans la section **format de soumission** , utilisez l’une des options suivantes :

   - **ID de message réseau**: il s’agit d’une valeur GUID qui est disponible dans l’en-tête **X-MS-Exchange-Organization-Network-message-ID** du message.

   - **Fichier**: cliquez sur **choisir un fichier**. Dans la boîte de dialogue qui s’ouvre, recherchez et sélectionnez le fichier. eml ou. MSG, puis cliquez sur **ouvrir**.

2. Dans la section **destinataires** , spécifiez un ou plusieurs destinataires sur lesquels vous souhaitez exécuter une vérification de stratégie. La vérification de stratégie détermine si l’analyse du courrier électronique a contourné les messages en raison des stratégies de l’utilisateur ou de l’organisation.

3. Dans la section **raison de l’envoi** , sélectionnez l’une des options suivantes :

   - **Ne doit pas avoir été bloqué**

   - **Doit avoir été bloqué**: sélectionnez **courrier indésirable**, **hameçonnage**ou **programme malveillant**. Si vous n’êtes pas sûr, utilisez votre meilleure appréciation.

4. Si le filtre a été contourné en raison de stratégies lors de l’envoi, vous verrez des informations sur cette stratégie.

   Si le filtre n’a pas été contourné en raison d’une ou de plusieurs stratégies, l’analyse se terminera en quelques minutes. Vous verrez des informations supplémentaires sur l’envoi en cliquant sur le lien État. Cela inclut les résultats de la vérification de stratégie et le verdict de nouvelle analyse. Remarque cela n’exécute pas de nouveau le courrier électronique via la pile de filtrage complet DAV d’Office 365 mais exécute une nouvelle analyse partielle en fonction de certains attributs de l’e-mail, de l’URL ou du fichier.

5. Lorsque vous avez terminé, cliquez sur le bouton **Envoyer** .

![Exemple de soumission d’URL](../../media/submission-flyout-email.PNG)

### <a name="send-a-suspect-url-to-microsoft"></a>Envoyer une URL suspecte à Microsoft

1. Dans la section **type d’objet** , sélectionnez **URL**. Dans la zone qui s’affiche, entrez l’URL complète (par exemple, <https://www.fabrikam.com/marketing.html> ).

2. Dans la section **raison de l’envoi** , sélectionnez l’une des options suivantes :

   - **Ne doit pas avoir été bloqué**

   - **Doit avoir été bloqué**: sélectionnez **hameçonnage** ou **programme malveillant**.

3. Lorsque vous avez terminé, cliquez sur le bouton **Envoyer** .

![Exemple de dépôt de courrier électronique](../../media/submission-url-flyout.png)

### <a name="submit-a-suspected-file-to-microsoft"></a>Envoyer un fichier suspect à Microsoft

1. Dans la section **type d’objet** , sélectionnez **pièce jointe**.

2. Cliquez sur **choisir un fichier**. Dans la boîte de dialogue qui s’ouvre, recherchez et sélectionnez le fichier, puis cliquez sur **ouvrir**.

3. Dans la section **raison de l’envoi** , sélectionnez l’une des options suivantes :

   - **Ne doit pas avoir été bloqué**

   - **Doit avoir été bloqué**: le **programme malveillant** est le seul choix et est automatiquement sélectionné..

4. Lorsque vous avez terminé, cliquez sur le bouton **Envoyer** .

![Exemple de soumission de pièces jointes](../../media/submission-file-flyout.PNG)

## <a name="view-admin-submissions"></a>Afficher les soumissions de l’administrateur

1. Dans le centre de sécurité & conformité, accédez à **gestion des menaces** - \> **vérifier** \> **les messages d’envoi**de l’administrateur.

2. Sur la page des **envois** qui s’affiche, vérifiez que l’onglet **soumissions** de l’administrateur est sélectionné.

En haut de la page, vous pouvez entrer une date de début, une date de fin et, par défaut, vous pouvez filtrer par **ID de soumission** (valeur Guid affectée à chaque envoi) en entrant une valeur dans la zone et en cliquant sur le ![ bouton actualiser ](../../media/scc-quarantine-refresh.png) . Update

Pour modifier les critères de filtre, cliquez sur le bouton **ID de soumission** , puis choisissez l’une des valeurs suivantes :

- **Sender**
- **Subject/URL/nom de fichier**
- **Soumis par**
- **Type d’envoi**
- **Status**

![Options de filtrage pour les soumissions d’administration](../../media/admin-submission-email-filter-options.png)

Pour exporter les résultats, cliquez sur **Exporter** vers le haut de la page, puis sélectionnez **données de graphique** ou **tableau**. Dans la boîte de dialogue qui s’affiche, enregistrez le fichier. csv.

Sous le graphique, il existe trois onglets : **e-mail** (par défaut), **URL**et **pièce jointe**.

### <a name="view-admin-email-submissions"></a>Afficher les envois de courrier de l’administrateur

Cliquez sur l’onglet **e-mail** .

Vous pouvez cliquer sur le bouton **options de colonne** dans la partie inférieure de la page pour ajouter ou supprimer des colonnes dans l’affichage :

- **Date**
- **ID de soumission**: valeur Guid assignée à chaque soumission.
- **Soumis par**<sup>\*</sup>
- **Sujet**<sup>\*</sup>
- **Sender**
- **IP de l’expéditeur**<sup>\*</sup>
- **Type d’envoi**
- **Motif de remise**
- **Originaire**<sup>\*</sup>
- **Type de contrôle**
- **Source du contrôle**

  <sup>\*</sup>Si vous cliquez sur cette valeur, des informations détaillées s’affichent dans un lanceur.

### <a name="view-admin-url-submissions"></a>Afficher les envois d’URL d’administrateur

Cliquez sur l’onglet **URL** .

Vous pouvez cliquer sur le bouton **options de colonne** dans la partie inférieure de la page pour ajouter ou supprimer des colonnes dans l’affichage :

- **Date**
- **ID de soumission**
- **Soumis par**<sup>\*</sup>
- **URL**<sup>\*</sup>
- **Type d’envoi**
- **Originaire**<sup>\*</sup>

  <sup>\*</sup>Si vous cliquez sur cette valeur, des informations détaillées s’affichent dans un lanceur.

### <a name="view-admin-attachment-submissions"></a>Afficher les envois de pièces jointes admin

Cliquez sur l’onglet **pièces jointes** .

Vous pouvez cliquer sur le bouton **options de colonne** dans la partie inférieure de la page pour ajouter ou supprimer des colonnes dans l’affichage :

- **Date**
- **ID de soumission**
- **Soumis par**<sup>\*</sup>
- **Nom de fichier**<sup>\*</sup>
- **Type d’envoi**
- **Originaire**<sup>\*</sup>

  <sup>\*</sup>Si vous cliquez sur cette valeur, des informations détaillées s’affichent dans un lanceur.

## <a name="view-user-submissions-to-microsoft"></a>Afficher les soumissions des utilisateurs à Microsoft

Si vous avez déployé le [complément de rapport de message](enable-the-report-message-add-in.md)ou que les utilisateurs utilisent la [création de rapports intégrée dans Outlook sur le Web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md), vous pouvez voir ce que les utilisateurs signalent sous l’onglet **soumissions** de l’utilisateur.

1. Dans le centre de sécurité & conformité, accédez à **gestion des menaces** - \> **vérifier** \> **les messages d’envoi**de l’administrateur.

2. Sur la page des **envois** qui s’affiche, cliquez sur l’onglet **soumissions** de l’utilisateur.

Vous pouvez cliquer sur le bouton **options de colonne** dans la partie inférieure de la page pour ajouter ou supprimer des colonnes dans l’affichage :

- **Soumis le**
- **Soumis par**<sup>\*</sup>
- **Sujet**<sup>\*</sup>
- **Sender**
- **IP de l’expéditeur**<sup>\*</sup>
- **Type d’envoi**

<sup>\*</sup>Si vous cliquez sur cette valeur, des informations détaillées s’affichent dans un lanceur.

En haut de la page, vous pouvez entrer une date de début, une date de fin et, par défaut, vous pouvez filtrer par **expéditeur** en entrant une valeur dans la zone, puis en cliquant sur le ![ bouton actualiser ](../../media/scc-quarantine-refresh.png) . Update

Pour modifier les critères de filtre, cliquez sur le bouton **expéditeur** , puis choisissez l’une des valeurs suivantes :

- **Domaine de l’expéditeur**
- **Subject**
- **Soumis par**
- **Type d’envoi**
- **IP de l’expéditeur**

![Options de filtrage pour les soumissions des utilisateurs](../../media/user-submissions-filter-options.png)

Pour exporter les résultats, cliquez sur **Exporter** vers le haut de la page, puis sélectionnez **données de graphique** ou **tableau**. Dans la boîte de dialogue qui s’affiche, enregistrez le fichier. csv.

## <a name="view-user-submissions-to-the-custom-mailbox"></a>Afficher les soumissions des utilisateurs à la boîte aux lettres personnalisée

Si vous avez [configuré une boîte aux lettres personnalisée](user-submission.md) pour recevoir des messages signalés par l’utilisateur, vous pouvez afficher et envoyer également les messages qui ont été remis à la boîte aux lettres de création de rapports.

1. Dans le centre de sécurité & conformité, accédez à **gestion des menaces** - \> **vérifier** \> **les messages d’envoi**de l’administrateur.

2. Sur la page des **envois** qui s’affiche, cliquez sur l’onglet **boîte aux lettres personnalisée** .

Vous pouvez cliquer sur le bouton **options de colonne** dans la partie inférieure de la page pour ajouter ou supprimer des colonnes dans l’affichage :

- **Soumis le**
- **Soumis par**<sup>\*</sup>
- **Sujet**<sup>\*</sup>
- **Sender**
- **IP de l’expéditeur**<sup>\*</sup>
- **Type d’envoi**

En haut de la page, vous pouvez entrer une date de début, une date de fin et un filtre par **envoyé par** en entrant une valeur dans la zone, puis en cliquant sur le ![ bouton actualiser ](../../media/scc-quarantine-refresh.png) . Update

Pour exporter les résultats, cliquez sur **Exporter** vers le haut de la page, puis sélectionnez **données de graphique** ou **tableau**. Dans la boîte de dialogue qui s’affiche, enregistrez le fichier. csv.

### <a name="submit-messages-to-microsoft-from-the-custom-mailbox"></a>Envoyer des messages à Microsoft à partir de la boîte aux lettres personnalisée

Si vous avez configuré la boîte aux lettres personnalisée de sorte qu’elle intercepte les messages signalés par l’utilisateur sans envoyer les messages à Microsoft, vous pouvez rechercher et envoyer des messages spécifiques à Microsoft pour analyse. Cela déplace effectivement une soumission d’utilisateur vers une soumission d’administrateur.

Sous l’onglet **boîte aux lettres personnalisée** , sélectionnez un message dans la liste, cliquez sur le bouton d' **action** , puis effectuez l’une des sélections suivantes :

- **État de la notification**
- **Signaler le hameçonnage**
- **Signaler un programme malveillant**
- **Signaler le courrier indésirable**

![Options du bouton d’action](../../media/user-submission-custom-mailbox-action-button.png)
