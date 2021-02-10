---
title: Soumissions d’administrateur
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser le portail Soumissions dans le Centre de sécurité & conformité pour soumettre des messages suspects, des messages de hameçonnage suspects, du courrier indésirable et d’autres messages potentiellement dangereux, des URL et des fichiers à Microsoft pour analyse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7a822909c318cb336c179b299aa64cd71dcca4d8
ms.sourcegitcommit: 3dc795ea862b180484f76b3eb5d046e74041252b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/10/2021
ms.locfileid: "50175870"
---
# <a name="use-admin-submission-to-submit-suspected-spam-phish-urls-and-files-to-microsoft"></a>Utilisez la soumission de l’administrateur pour soumettre des courriers indésirables, l’hameçonnage, des URL et des fichiers à Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](https://go.microsoft.com/fwlink/?linkid=2148611)
- [Microsoft Defender pour Office 365 plan 1 et plan 2](https://go.microsoft.com/fwlink/?linkid=2148715)


Dans les organisations Microsoft 365 ayant des boîtes aux lettres dans Exchange Online, les administrateurs peuvent utiliser le portail Soumissions dans le Centre de sécurité & conformité pour envoyer des messages électroniques, des URL et des pièces jointes à Microsoft à des titres d’analyse.

Lorsque vous envoyez un message électronique, vous recevez les messages suivants :

1. **Vérification de l’authentification du** courrier électronique : détails sur la réussi ou l’échec de l’authentification de messagerie lors de sa livraison.
2. **Accès aux** stratégies : informations sur les stratégies qui ont autorisé ou bloqué le courrier entrant dans votre client, en remplacement de nos verdicts de filtre de service.
3. **Réputation/détonation de la charge utile**: examen des URL et pièces jointes du message.
4. **Analyse du gradeur**: révision effectuée par des élèves humains afin de confirmer si les messages sont malveillants ou non.

> [!IMPORTANT]
> L’analyse de réputation/détonation et de grader de la charge utile n’est pas effectuée dans tous les locataires. Les informations ne peuvent pas sortir de l’organisation lorsque les données ne sont pas supposées quitter la limite du client à des fins de conformité.

Pour d’autres façons de soumettre des messages électroniques, des URL et des pièces jointes à Microsoft, voir [Signaler des messages et des fichiers à Microsoft.](report-junk-email-messages-to-microsoft.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de sécurité et conformité sur <https://protection.office.com/>. Pour aller directement à la page **soumission,** utilisez <https://protection.office.com/reportsubmission> .

- Pour envoyer des messages et des fichiers à Microsoft, vous devez être membre de l’un des groupes de rôles suivants :

  - **Gestion de l’organisation** ou **Administrateur de sécurité** dans le [Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

  - **Gestion de l’organisation** [dans Exchange Online.](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups)

    Notez que l’appartenance à ce groupe de rôles est requise pour afficher les [envois](#view-user-submissions-to-the-custom-mailbox) d’utilisateurs à la boîte aux lettres personnalisée, comme décrit plus loin dans cet article.

- Pour plus d’informations sur la façon dont les utilisateurs peuvent envoyer des messages et des fichiers à Microsoft, voir [Signaler des messages et des fichiers à Microsoft.](report-junk-email-messages-to-microsoft.md)

## <a name="report-suspicious-content-to-microsoft"></a>Signaler du contenu suspect à Microsoft

1. Dans le Centre de sécurité &  conformité, allez à Soumissions de gestion des menaces, vérifiez que vous êtes sous \> l’onglet **Soumissions** d’administrateur, puis cliquez sur **Nouvelle soumission.**

2. Utilisez **le nouveau volant** de soumission qui apparaît pour envoyer le message, l’URL ou la pièce jointe, comme décrit dans les sections suivantes.

### <a name="submit-a-questionable-email-to-microsoft"></a>Envoyer un e-mail douteux à Microsoft

1. Dans la section **Type d’objet,** sélectionnez **Courrier électronique.** Dans la section **Format de** soumission, utilisez l’une des options suivantes :

   - **ID** de message réseau : il s’agit d’une valeur GUID disponible dans l’en-tête **X-MS-Exchange-Organization-Network-Message-Id** du message ou dans l’en-tête **X-MS-Office365-Filtering-Correlation-Id** dans les messages mis en quarantaine.

   - **Fichier**: cliquez **sur Choisir un fichier.** Dans la boîte de dialogue qui s’ouvre, recherchez et sélectionnez le fichier .eml ou .msg, puis cliquez sur **Ouvrir**.

   > [!NOTE]
   > Les administrateurs avec Defender pour Office 365 Plan 1 ou Plan 2 peuvent envoyer des messages d’une âge de 30 jours. Les autres administrateurs ne pourront revenir qu’à 7 jours.

2. Dans la section **Destinataires,** spécifiez un ou plusieurs destinataires pour qui vous souhaitez exécuter une vérification de stratégie. La vérification de stratégie détermine si le courrier électronique a contourné l’analyse en raison des stratégies utilisateur ou organisation.

3. Dans la section **Raison de la** soumission, sélectionnez l’une des options suivantes :

   - **Ne doit pas avoir été bloqué**

   - **Doit avoir été bloqué :** sélectionner le courrier **indésirable,** **le hameçonnage** ou les programmes **malveillants.** Si vous n’êtes pas sûr, faites votre meilleur choix.

4. Lorsque vous avez terminé, cliquez sur le **bouton** Envoyer.

   ![Exemple de soumission d’URL](../../media/submission-flyout-email.PNG)

### <a name="send-a-suspect-url-to-microsoft"></a>Envoyer une URL suspecte à Microsoft

1. Dans la section **Type d’objet,** sélectionnez **URL.** Dans la zone qui s’affiche, entrez l’URL complète (par exemple, `https://www.fabrikam.com/marketing.html` ).

2. Dans la section **Raison de la** soumission, sélectionnez l’une des options suivantes :

   - **Ne doit pas avoir été bloqué**

   - **Auraient dû être bloqués**: sélectionnez **Hameçonnage** ou **Programme malveillant.**

3. Lorsque vous avez terminé, cliquez sur le **bouton** Envoyer.

   ![Exemple d’envoi de courrier électronique](../../media/submission-url-flyout.png)

### <a name="submit-a-suspected-file-to-microsoft"></a>Soumettre un fichier suspect à Microsoft

1. Dans la section **Type d’objet,** sélectionnez **Pièce jointe.**

2. Cliquez **sur Choisir un fichier.** Dans la boîte de dialogue qui s’ouvre, recherchez et sélectionnez le fichier, puis cliquez sur **Ouvrir.**

3. Dans la section **Raison de la** soumission, sélectionnez l’une des options suivantes :

   - **Ne doit pas avoir été bloqué**

   - **Doit avoir été bloqué :** un **programme** malveillant est le seul choix et est automatiquement sélectionné.

4. Lorsque vous avez terminé, cliquez sur le **bouton** Envoyer.

   ![Exemple d’envoi de pièce jointe](../../media/submission-file-flyout.PNG)

## <a name="view-admin-submissions"></a>Afficher les soumissions d’administrateur

Dans le Centre de sécurité &  conformité, allez à Soumissions de gestion des menaces, vérifiez que vous êtes sous \> l’onglet **Soumissions** d’administrateur, puis cliquez sur **Nouvelle soumission.**

Dans la partie supérieure de la page, vous pouvez entrer une date de début, une date de fin et (par défaut) vous pouvez filtrer par **ID** de soumission (une valeur GUID affectée à chaque soumission) en entrant une valeur dans la zone et en cliquant sur le bouton ![ ](../../media/scc-quarantine-refresh.png) Actualiser. Update

Pour modifier les critères de filtre, cliquez sur le bouton **ID** de soumission et choisissez l’une des valeurs suivantes :

- **Sender**
- **Objet/URL/Nom de fichier**
- **Soumis par**
- **Type de soumission**
- **État**

![Options de filtrage pour les soumissions d’administrateurs](../../media/admin-submission-email-filter-options.png)

Pour exporter les résultats, cliquez sur **Exporter** en haut de la page et sélectionnez **Données du graphique** ou **Tableau.** Dans la boîte de dialogue qui s’affiche, enregistrez le fichier .csv.

Sous le graphique, il y a trois onglets : **e-mail** (par défaut), **URL** et **pièce jointe.**

### <a name="view-admin-email-submissions"></a>Afficher les envois de courriers électroniques d’administrateur

Cliquez sur **l’onglet** Courrier électronique.

Vous pouvez cliquer sur le **bouton Options** de colonne en bas de la page pour ajouter ou supprimer des colonnes de l’affichage :

- **Date**
- **ID de soumission**: valeur GUID attribuée à chaque soumission.
- **Soumis par**<sup>\*</sup>
- **Sujet**<sup>\*</sup>
- **Sender**
- **IP de l’expéditeur**<sup>\*</sup>
- **Type de soumission**
- **Raison de la remise**
- **État**<sup>\*</sup>

  <sup>\*</sup> Si vous cliquez sur cette valeur, des informations détaillées s’affichent dans un volant.

#### <a name="admin-submission-rescan-details"></a>Détails de la rescan de soumission de l’administrateur

Les messages envoyés dans les soumissions d’administrateur sont réassurés et les résultats sont affichés dans le volant de détails :

- En cas d’échec de l’authentification de messagerie de l’expéditeur au moment de la remise.
- Informations sur les occurrences de stratégie qui auraient pu avoir affecté ou inttérable le verdict d’un message.
- Résultats actuels de la détonation pour voir si les URL ou les fichiers contenus dans le message sont malveillants ou non.
- Commentaires des élèves.

Si une substitution a été trouvée, la rescan doit se terminer en quelques minutes. S’il n’y a pas de problème dans l’authentification ou la remise du courrier électronique n’a pas été affecté par une substitution, les commentaires des élèves peuvent prendre jusqu’à un jour.

### <a name="view-admin-url-submissions"></a>Afficher les soumissions d’URL d’administration

Cliquez sur **l’onglet URL.**

Vous pouvez cliquer sur le **bouton Options** de colonne en bas de la page pour ajouter ou supprimer des colonnes de l’affichage :

- **Date**
- **ID de soumission**
- **Soumis par**<sup>\*</sup>
- **URL**<sup>\*</sup>
- **Type de soumission**
- **État**<sup>\*</sup>

  <sup>\*</sup> Si vous cliquez sur cette valeur, des informations détaillées s’affichent dans un volant.

### <a name="view-admin-attachment-submissions"></a>Afficher les soumissions de pièces jointes d’administrateur

Cliquez sur **l’onglet Pièces jointes.**

Vous pouvez cliquer sur le **bouton Options** de colonne en bas de la page pour ajouter ou supprimer des colonnes de l’affichage :

- **Date**
- **ID de soumission**
- **Soumis par**<sup>\*</sup>
- **Nom de fichier**<sup>\*</sup>
- **Type de soumission**
- **État**<sup>\*</sup>

  <sup>\*</sup> Si vous cliquez sur cette valeur, des informations détaillées s’affichent dans un volant.

## <a name="view-user-submissions-to-microsoft"></a>Afficher les soumissions d’utilisateurs à Microsoft

Si vous avez déployé le [add-in](enable-the-report-message-add-in.md) [](enable-the-report-phish-add-in.md)Signaler un message, le module de signalement du hameçonnage ou que des personnes utilisent les rapports intégrés dans [Outlook sur le web,](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md)vous pouvez voir ce que les utilisateurs signalent sous l’onglet Soumissions des **utilisateurs.**

1. Dans le Centre de sécurité & conformité, allez aux soumissions **de gestion** \> **des menaces.**

2. Sélectionnez **l’onglet Soumissions utilisateur,** puis cliquez sur **Nouvelle soumission.**

Vous pouvez cliquer sur le **bouton Options** de colonne en bas de la page pour ajouter ou supprimer des colonnes de l’affichage :

- **Envoyé le**
- **Soumis par**<sup>\*</sup>
- **Sujet**<sup>\*</sup>
- **Sender**
- **IP de l’expéditeur**<sup>\*</sup>
- **Type de soumission**

<sup>\*</sup> Si vous cliquez sur cette valeur, des informations détaillées s’affichent dans un volant.

Dans la zone supérieure de la page, vous pouvez entrer une date de  début, une date de fin et (par défaut) vous pouvez filtrer par expéditeur en entrant une valeur dans la zone et en cliquant sur le bouton ![ ](../../media/scc-quarantine-refresh.png) Actualiser. Update

Pour modifier les critères de filtre, cliquez sur le bouton **Expéditeur** et choisissez l’une des valeurs suivantes :

- **Domaine de l’expéditeur**
- **Subject**
- **Soumis par**
- **Type de soumission**
- **IP de l’expéditeur**

![Options de filtrage pour les envois d’utilisateurs](../../media/user-submissions-filter-options.png)

Pour exporter les résultats, cliquez sur **Exporter** en haut de la page et sélectionnez **Données du graphique** ou **Tableau.** Dans la boîte de dialogue qui s’affiche, enregistrez le fichier .csv.

## <a name="view-user-submissions-to-the-custom-mailbox"></a>Afficher les envois d’utilisateurs à la boîte aux lettres personnalisée

**Si** vous avez configuré [une](user-submission.md) boîte aux lettres personnalisée pour recevoir les messages signalés par l’utilisateur, vous pouvez afficher et envoyer des messages qui ont été remis à la boîte aux lettres de création de rapports.

1. Dans le Centre de sécurité & conformité, allez aux soumissions **de gestion** \> **des menaces.**

2. Sélectionnez **l’onglet Boîte aux lettres** personnalisée.

Vous pouvez cliquer sur le **bouton Options** de colonne en bas de la page pour ajouter ou supprimer des colonnes de l’affichage :

- **Envoyé le**
- **Soumis par**<sup>\*</sup>
- **Sujet**<sup>\*</sup>
- **Sender**
- **IP de l’expéditeur**<sup>\*</sup>
- **Type de soumission**

Dans la zone supérieure de la page, vous pouvez entrer une  date de début, une date de fin et vous pouvez filtrer en entrant une valeur dans la zone et en cliquant sur le bouton ![ ](../../media/scc-quarantine-refresh.png) Actualiser. Update

Pour exporter les résultats, cliquez sur **Exporter** en haut de la page et sélectionnez **Données du graphique** ou **Tableau.** Dans la boîte de dialogue qui s’affiche, enregistrez le fichier .csv.

## <a name="undo-user-submissions"></a>Annuler les soumissions d’utilisateurs

Lorsqu’un utilisateur envoie un message suspect à la boîte aux lettres personnalisée, l’utilisateur et l’administrateur n’ont pas la possibilité d’annuler la soumission. Si l’utilisateur souhaite récupérer le courrier électronique, il sera disponible pour la récupération dans les dossiers Éléments supprimés ou Courrier indésirable.

### <a name="submit-messages-to-microsoft-from-the-custom-mailbox"></a>Envoyer des messages à Microsoft à partir de la boîte aux lettres personnalisée

Si vous avez configuré la boîte aux lettres personnalisée pour intercepter les messages signalés par l’utilisateur sans les envoyer à Microsoft, vous pouvez rechercher et envoyer des messages spécifiques à Microsoft pour analyse. Cela déplace efficacement une soumission d’utilisateur vers une soumission d’administrateur.

Sous **l’onglet Boîte** aux lettres personnalisée, sélectionnez un message dans la liste, cliquez sur le bouton **Action** et faites l’une des sélections suivantes :

- **Signaler propre**
- **Signaler le hameçonnage**
- **Signaler un programme malveillant**
- **Signaler le courrier indésirable**

![Options sur le bouton Action](../../media/user-submission-custom-mailbox-action-button.png)
