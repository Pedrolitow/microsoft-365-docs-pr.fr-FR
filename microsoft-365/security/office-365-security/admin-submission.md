---
title: Gérer les envois
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser le portail Soumissions dans le portail Microsoft 365 Defender pour envoyer des e-mails suspects, des courriers suspects de hameçonnage, du courrier indésirable et d’autres messages potentiellement dangereux, des URL et des pièces jointes à Microsoft pour la rescanning.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bd56ce39cbb1d48470742f80a8b07747dd52f33a
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66116033"
---
# <a name="use-the-submissions-portal-to-submit-suspected-spam-phish-urls-and-files-to-microsoft"></a>Utilisez le portail Soumissions pour envoyer des courriers indésirables, des hameçonnages, des URL et des fichiers suspects à Microsoft

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres Exchange Online, les administrateurs peuvent utiliser le portail Soumissions dans le portail Microsoft 365 Defender pour envoyer des e-mails, des URL et des pièces jointes à Microsoft à des fins d’analyse.

Lorsque vous envoyez un e-mail à des fins d’analyse, vous obtenez :

- **Vérification de l’authentification par e-mail** : détails sur la réussite ou l’échec de l’authentification par e-mail lors de sa remise.
- **Accès à** la stratégie : informations sur toutes les stratégies qui peuvent avoir autorisé ou bloqué l’e-mail entrant dans votre locataire, en remplaçant nos verdicts de filtre de service.
- **Réputation/détonation de la charge utile** : examen à jour des URL et pièces jointes du message.
- **Analyse** de la note : Passez en revue les analyses effectuées par les gradateurs humains afin de vérifier si les messages sont malveillants ou non.

> [!IMPORTANT]
> La réputation/détonation de la charge utile et l’analyse de la note ne sont pas effectuées dans tous les locataires. Les informations ne peuvent pas sortir de l’organisation lorsque les données ne sont pas censées quitter la limite du locataire à des fins de conformité.

Pour d’autres façons d’envoyer des e-mails, des URL et des pièces jointes à Microsoft, consultez [Les messages de rapport et les fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

Regardez cette courte vidéo pour découvrir comment utiliser les soumissions d’administrateurs dans Microsoft Defender pour Office 365 pour envoyer des messages à Microsoft à des fins d’évaluation. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBLPn]

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com/>. Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

- Pour envoyer des messages et des fichiers à Microsoft, vous devez avoir l’un des rôles suivants :
  - **Administrateur de sécurité** ou **Lecteur sécurité** dans le [portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

    Notez que l’un de ces rôles est requis pour [afficher les soumissions d’utilisateurs à la boîte aux lettres personnalisée](#view-user-submissions-to-microsoft) , comme décrit plus loin dans cet article.

- Les administrateurs peuvent envoyer des messages vieux de 30 jours s’ils sont toujours disponibles dans la boîte aux lettres et non purgés par l’utilisateur ou un autre administrateur.

- Administration soumissions sont limitées aux taux suivants :
  - Nombre maximal de soumissions sur une période de 15 minutes : 150 soumissions
  - Mêmes soumissions sur une période de 24 heures : 3 soumissions
  - Mêmes soumissions dans une période de 15 minutes : 1 soumission

- Pour plus d’informations sur la façon dont les utilisateurs peuvent envoyer des messages et des fichiers à Microsoft, consultez [Les messages de rapport et les fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="report-suspicious-content-to-microsoft"></a>Signaler du contenu suspect à Microsoft

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , vérifiez que l’onglet **Courriers électroniques** ou **pièces jointes** ou **URL**  est sélectionné en fonction du type de contenu que vous souhaitez signaler, puis cliquez sur ![Envoyer à Microsoft pour l’icône d’analyse.](../../media/m365-cc-sc-create-icon.png) **Envoyer à Microsoft pour analyse**.

3. Utilisez le menu volant **Envoyer à Microsoft pour l’analyse** qui semble soumettre le type de contenu respectif (e-mail, URL ou pièce jointe) comme décrit dans les sections suivantes.

   > [!NOTE]
   > Les soumissions de fichiers et d’URL ne sont pas disponibles dans les clouds qui ne permettent pas aux données de quitter l’environnement. La possibilité de sélectionner fichier ou URL est grisée.

### <a name="notify-users-from-within-the-portal"></a>Avertir les utilisateurs à partir du portail

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** à **l’adresse e-mail &** **les soumissions** de collaboration\>. Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , sélectionnez **l’onglet Messages signalés par l’utilisateur** , puis sélectionnez le message que vous souhaitez marquer et notifier.

3. Sélectionnez la **marque et notifiez** la liste déroulante, puis sélectionnez **Aucune menace détectée** \> **Par hameçonnage** ou **courrier indésirable**.

   :::image type="content" source="../../media/unified-submission-user-reported-message.png" alt-text="Page Soumissions" lightbox="../../media/unified-submission-user-reported-message.png":::

Le message signalé sera marqué comme un faux positif ou un faux négatif. Une notification par e-mail est envoyée automatiquement à partir du portail à l’utilisateur qui a signalé le message.

### <a name="submit-a-questionable-email-to-microsoft"></a>Envoyer un e-mail douteux à Microsoft

1. Dans la zone **Sélectionner le type de soumission** , vérifiez que **l’e-mail** est sélectionné dans la liste déroulante.

2. Dans la section **Ajouter l’ID de message réseau ou charger le fichier e-mail** , utilisez l’une des options suivantes :
   - **Ajoutez l’ID de message réseau de messagerie** : il s’agit d’une valeur GUID disponible dans l’en-tête **X-MS-Exchange-Organization-Network-Message-Id** dans le message ou dans l’en-tête **X-MS-Office365-Filtering-Correlation-Id** dans les messages mis en quarantaine.
   - **Télécharger le fichier e-mail (.msg ou .eml)** : cliquez sur **Parcourir les fichiers**. Dans la boîte de dialogue qui s’ouvre, recherchez et sélectionnez le fichier .eml ou .msg, puis cliquez sur **Ouvrir**.

3. Dans la zone **Choisir un destinataire qui a rencontré un problème** , spécifiez le destinataire sur lequel vous souhaitez exécuter une vérification de stratégie. La vérification de stratégie détermine si l’e-mail a contourné l’analyse en raison de stratégies d’utilisateur ou d’organisation.

4. Dans la section **Sélectionner une raison pour l’envoi à Microsoft** , sélectionnez l’une des options suivantes :
   - **N’aurait pas dû être bloqué (Faux positif)**
   - **Aurait dû être bloqué (faux négatif)** : dans **l’e-mail doit avoir été classé comme** section qui s’affiche, sélectionnez l’une des valeurs suivantes (si vous n’êtes pas sûr, utilisez votre meilleur jugement) :
     - **Hameçonnage**
     - **Programme malveillant**
     - **Courrier indésirable**

5. Lorsque vous avez terminé, cliquez sur **Envoyer**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/submission-flyout-email.png" alt-text="Processus de soumission d’une nouvelle URL" lightbox="../../media/submission-flyout-email.png":::

### <a name="send-a-suspect-url-to-microsoft"></a>Envoyer une URL suspecte à Microsoft

1. Dans la zone **Sélectionner le type de soumission** , sélectionnez **l’URL** dans la liste déroulante.

2. Dans la zone **URL** qui s’affiche, entrez l’URL complète (par exemple, `https://www.fabrikam.com/marketing.html`).

3. Dans la section **Sélectionner une raison pour l’envoi à Microsoft** , sélectionnez l’une des options suivantes :
   - **N’aurait pas dû être bloqué (Faux positif)**
   - **Aurait dû être bloqué (faux négatif)** : dans cette **URL, vous devriez avoir été catégorisé en tant** que section qui s’affiche, sélectionnez l’une des valeurs suivantes (si vous n’êtes pas sûr, utilisez votre meilleur jugement) :
     - **Hameçonnage**
     - **Programme malveillant**

4. Lorsque vous avez terminé, cliquez sur **Envoyer**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/submission-url-flyout.png" alt-text="Processus de soumission d’un nouvel e-mail" lightbox="../../media/submission-url-flyout.png":::

### <a name="submit-a-suspected-email-attachment-to-microsoft"></a>Envoyer une pièce jointe suspecte à Microsoft

1. Dans la zone **Sélectionner le type de soumission** , sélectionnez **La pièce jointe de l’e-mail** dans la liste déroulante.

2. Dans la section **Fichier** qui s’affiche, cliquez sur **Parcourir les fichiers**. Dans la boîte de dialogue qui s’ouvre, recherchez et sélectionnez le fichier, puis cliquez sur **Ouvrir**.

3. Dans la section **Sélectionner une raison pour l’envoi à Microsoft** , sélectionnez l’une des options suivantes :
   - **N’aurait pas dû être bloqué (Faux positif)**
   - **Aurait dû être bloqué (faux négatif)** : dans **ce fichier aurait dû être classé en tant** que section qui s’affiche, sélectionnez l’une des valeurs suivantes (si vous n’êtes pas sûr, utilisez votre meilleur jugement) :
     - **Hameçonnage**
     - **Programme malveillant**

4. Lorsque vous avez terminé, cliquez sur **Envoyer**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/submission-file-flyout.png" alt-text="Processus de soumission d’une nouvelle pièce jointe" lightbox="../../media/submission-file-flyout.png":::

> [!NOTE]
> Si le filtrage des programmes malveillants a remplacé les pièces jointes de message par le fichier d’alerte de programme malveillant Text.txt, vous devez envoyer le message d’origine à partir de la mise en quarantaine qui contient les pièces jointes d’origine. Pour plus d’informations sur la mise en quarantaine et la façon de publier des messages avec des faux positifs de programme malveillant, consultez [Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur](manage-quarantined-messages-and-files.md).

## <a name="view-email-admin-submissions-to-microsoft"></a>Afficher les soumissions d’administrateur de messagerie à Microsoft

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , vérifiez que l’onglet **e-mails** est sélectionné.

   - Vous pouvez trier les entrées en cliquant sur un en-tête de colonne disponible. Cliquez sur **Personnaliser les colonnes** pour sélectionner les colonnes dont vous avez besoin. Toutes les colonnes peuvent être sélectionnées et affichées dans la grille de soumission. Les valeurs par défaut sont marquées d'un astérisque (<sup>\*</sup>) :
     - **Nom de l’envoi**<sup>\*</sup>
     - **Expéditeur**<sup>\*</sup>
     - **Destinataire**
     - **Date d’envoi**<sup>\*</sup>
     - **Motif de l’envoi**<sup>\*</sup>
     - **Statut**<sup>\*</sup>
     - **Résultat**<sup>\*</sup>
     - **Filtrer le verdict**
     - **Motif de remise/blocage**
     - **ID de soumission**
     - **ID de message réseau/ID d’objet**
     - **Direction**
     - **IP de l’expéditeur**
     - **Niveau de conformité en bloc (BCL)**
     - **Destination**
     - **Action de stratégie**
     - **Soumis par**
     - **Simulation de hameçonnage**
     - **Étiquettes**<sup>\*</sup>
     - **Allow**

     Lorsque vous avez terminé, cliquez sur **Appliquer**.

     > [!div class="mx-imgBorder"]
     > :::image type="content" source="../../media/email-admin-submission-customize-columns.png" alt-text="Option Personnaliser la colonne pour les soumissions d’administrateur de courrier électronique." lightbox="../../media/email-admin-submission-customize-columns.png":::

   - Pour filtrer les entrées, cliquez sur **Filtrer**. Les filtres disponibles sont :
     - **Date d’envoi** : **Date de début** et **date de fin**.
     - **ID de soumission** : valeur GUID affectée à chaque soumission.
     - **ID de message réseau**
     - **Sender**
     - **Destinataire**
     - **Name**
     - **Soumis par**
     - **Motif de l’envoi**
     - **État**
     - **Tags**

     Lorsque vous avez terminé, cliquez sur **Appliquer**.

     > [!div class="mx-imgBorder"]
     > :::image type="content" source="../../media/email-admin-submission-filters.png" alt-text="Options de filtre pour les soumissions d’administrateur de courrier électronique." lightbox="../../media/email-admin-submission-filters.png":::

   - Pour regrouper les entrées, cliquez sur **Grouper** et sélectionnez l’une des valeurs suivantes dans la liste déroulante :
     - **Aucune**
     - **Raison**
     - **État**
     - **Résultat**
     - **Tags**

   - Pour exporter les entrées, cliquez sur **Exporter**. Dans la boîte de dialogue qui s’affiche, enregistrez le fichier .csv.

## <a name="view-email-attachment-admin-submissions-to-microsoft"></a>Afficher les soumissions d’administrateurs de pièces jointes à Microsoft

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , vérifiez que l’onglet **Pièces jointes de l’e-mail** est sélectionné.

   - Vous pouvez trier les entrées en cliquant sur un en-tête de colonne disponible. Cliquez sur **Personnaliser les colonnes** pour sélectionner les colonnes dont vous avez besoin. Toutes les colonnes peuvent être sélectionnées et affichées dans la grille de soumission. Les valeurs par défaut sont marquées d'un astérisque (<sup>\*</sup>) :
     - **Nom de la pièce jointe**<sup>\*</sup>
     - **Date d’envoi**<sup>\*</sup>
     - **Motif de l’envoi**<sup>\*</sup>
     - **Statut**<sup>\*</sup>
     - **Résultat**<sup>\*</sup>
     - **Filtrer le verdict**
     - **Motif de remise/blocage**
     - **ID de soumission**
     - **ID d’objet**
     - **Action de stratégie**
     - **Soumis par**
     - **Étiquettes**<sup>\*</sup>
     - **Allow**

     Lorsque vous avez terminé, cliquez sur **Appliquer**.

     :::image type="content" source="../../media/email-attachment-admin-submission-customize-columns.png" alt-text="Personnalisez les options de colonne pour les soumissions d’administrateurs de pièces jointes par e-mail.":::

   - Pour filtrer les entrées, cliquez sur **Filtrer**. Les filtres disponibles sont :
     - **Date d’envoi** : **Date de début** et **date de fin**.
     - **ID de soumission** : valeur GUID affectée à chaque soumission.
     - **Nom de fichier des pièces jointes**
     - **Soumis par**
     - **Motif de l’envoi**
     - **État**
     - **Tags**

     Lorsque vous avez terminé, cliquez sur **Appliquer**.

     :::image type="content" source="../../media/email-attachment-admin-submission-filters.png" alt-text="Options de filtre pour les soumissions d’administrateurs de pièces jointes par e-mail.":::

   - Pour regrouper les entrées, cliquez sur **Grouper** et sélectionnez l’une des valeurs suivantes dans la liste déroulante :
     - **Aucune**
     - **Raison**
     - **État**
     - **Résultat**
     - **Tags**

   - Pour exporter les entrées, cliquez sur **Exporter**. Dans la boîte de dialogue qui s’affiche, enregistrez le fichier .csv.

## <a name="view-urls-admin-submissions-to-microsoft"></a>Afficher les soumissions d’administrateur d’URL à Microsoft

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , vérifiez que l’onglet **URL** est sélectionné.

   - Vous pouvez trier les entrées en cliquant sur un en-tête de colonne disponible. Cliquez sur **Personnaliser les colonnes** pour sélectionner les colonnes dont vous avez besoin. Toutes les colonnes peuvent être sélectionnées et affichées dans la grille de soumission. Les valeurs par défaut sont marquées d'un astérisque (<sup>\*</sup>) :
     - **URL**<sup>\*</sup>
     - **Date d’envoi**<sup>\*</sup>
     - **Motif de l’envoi**<sup>\*</sup>
     - **Statut**<sup>\*</sup>
     - **Résultat**<sup>\*</sup>
     - **Filtrer le verdict**
     - **Motif de remise/blocage**
     - **ID de soumission**
     - **ID d’objet**
     - **Action de stratégie**
     - **Soumis par**
     - **Étiquettes**<sup>\*</sup>
     - **Allow**

     Lorsque vous avez terminé, cliquez sur **Appliquer**.

     :::image type="content" source="../../media/url-admin-submission-customize-columns.png" alt-text="Personnalisez les options de colonne pour les soumissions d’administrateur d’URL.":::

   - Pour filtrer les entrées, cliquez sur **Filtrer**. Les filtres disponibles sont :
     - **Date d’envoi** : **Date de début** et **date de fin**.
     - **ID de soumission** : valeur GUID affectée à chaque soumission.
     - **URL**
     - **Soumis par**
     - **Motif de l’envoi**
     - **État**
     - **Tags**

     Lorsque vous avez terminé, cliquez sur **Appliquer**.

     :::image type="content" source="../../media/url-admin-submission-customize-columns.png" alt-text="Options de filtre pour les soumissions d’administrateur d’URL.":::

   - Pour regrouper les entrées, cliquez sur **Grouper** et sélectionnez l’une des valeurs suivantes dans la liste déroulante :
     - **Aucune**
     - **Raison**
     - **État**
     - **Résultat**
     - **Tags**

   - Pour exporter les entrées, cliquez sur **Exporter**. Dans la boîte de dialogue qui s’affiche, enregistrez le fichier .csv.

### <a name="admin-submission-result-details"></a>Administration détails du résultat de la soumission

Les messages envoyés dans les soumissions d’administrateur sont examinés et les résultats sont affichés dans le menu volant détaillé des soumissions :

- En cas d’échec de l’authentification des e-mails de l’expéditeur au moment de la livraison.
- Informations sur les accès à la stratégie qui auraient pu affecter ou écraser le verdict d’un message.
- Résultats actuels de la détonation pour savoir si les URL ou fichiers contenus dans le message étaient malveillants ou non.
- Commentaires des diplômés.

Si un remplacement a été trouvé, le résultat doit être disponible en quelques minutes. S’il n’y a pas eu de problème dans l’authentification par e-mail ou la remise n’a pas été affectée par un remplacement, les commentaires des élèves peuvent prendre jusqu’à une journée.

## <a name="view-user-submissions-to-microsoft"></a>Afficher les soumissions d’utilisateurs à Microsoft

Si vous avez déployé le [complément Message](enable-the-report-message-add-in.md) de rapport, le [complément Report Phishing](enable-the-report-phish-add-in.md) ou si des personnes utilisent la [création de rapports intégrée dans Outlook sur le web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md), vous pouvez voir ce que les utilisateurs signalent sous l’onglet **Message signalé par l’utilisateur**.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , sélectionnez l’onglet **Messages signalés par l’utilisateur** .

   - Vous pouvez trier les entrées en cliquant sur un en-tête de colonne disponible. Cliquez sur **Personnaliser les colonnes** pour afficher les options. Les valeurs par défaut sont marquées d'un astérisque (<sup>\*</sup>) :

     - **Objet de l’e-mail**<sup>\*</sup>
     - **Signalé par**<sup>\*</sup>
     - **Date signalée**<sup>\*</sup>
     - **Expéditeur**<sup>\*</sup>
     - **Motif signalé**<sup>\*</sup>
     - **Résultat**<sup>\*</sup>
     - **ID signalé du message**
     - **ID de message réseau**
     - **IP de l’expéditeur**
     - **Signalé à partir de**
     - **Simulation de hameçonnage**
     - **Converti en soumission d’administrateur**
     - **Étiquettes**<sup>\*</sup>
     - **Marqué comme**<sup>\*</sup>
     - **Marqué par**
     - **Date marquée**

     Lorsque vous avez terminé, cliquez sur **Appliquer**.

   - Pour filtrer les entrées, cliquez sur **Filtrer**. Les filtres disponibles sont :
     - **Date signalée** : **date de début** et **date de fin**.
     - **Auteur du rapport**
     - **Sujet de l’e-mail**
     - **ID signalé du message**
     - **ID de message réseau**
     - **Sender**
     - **Motif signalé** : **non indésirable**, **hameçonnage** ou **courrier indésirable**
     - **Signalé à partir d’un** **complément Microsoft** ou d’un **complément tiers**
     - **Simulation de hameçonnage** : **Oui** ou **non**
     - **Converti en soumission d’administrateur** : **Oui** ou **Non**
     - **Tags**

     Lorsque vous avez terminé, cliquez sur **Appliquer**.

     > [!div class="mx-imgBorder"]
     > :::image type="content" source="../../media/admin-submission-reported-messages.png" alt-text="Options de nouveau filtre pour les soumissions d’utilisateurs" lightbox="../../media/admin-submission-reported-messages.png":::

   - Pour regrouper les entrées, cliquez sur **Grouper** et sélectionnez l’une des valeurs suivantes dans la liste déroulante :
     - **Aucune**
     - **Raison**
     - **Sender**
     - **Auteur du rapport**
     - **Résultat**
     - **Signalé à partir de**
     - **Simulation de hameçonnage**
     - **Converti en soumission d’administrateur**
     - **Tags**

   - Pour exporter les entrées, cliquez sur **Exporter**. Dans la boîte de dialogue qui s’affiche, enregistrez le fichier .csv.

> [!NOTE]
> Si les organisations sont configurées pour envoyer des messages signalés par l’utilisateur à la boîte aux lettres personnalisée uniquement, les messages signalés apparaissent dans les **messages signalés par l’utilisateur** , mais leurs résultats sont toujours vides (car ils n’auraient pas été réexécuter).

### <a name="undo-user-submissions"></a>Annuler les soumissions d’utilisateurs

Une fois qu’un utilisateur envoie un e-mail suspect à la boîte aux lettres personnalisée, l’utilisateur et l’administrateur n’ont pas la possibilité d’annuler l’envoi. Si l’utilisateur souhaite récupérer l’e-mail, il sera disponible pour la récupération dans les dossiers Éléments supprimés ou Courrier indésirable.

### <a name="convert-user-reported-messages-from-the-custom-mailbox-into-an-admin-submission"></a>Convertir les messages signalés par l’utilisateur de la boîte aux lettres personnalisée en soumission d’administrateur

Si vous avez configuré la boîte aux lettres personnalisée pour intercepter les messages signalés par l’utilisateur sans envoyer les messages à Microsoft, vous pouvez rechercher et envoyer des messages spécifiques à Microsoft à des fins d’analyse.

Sous **l’onglet Messages signalés par l’utilisateur** , sélectionnez un message dans la liste, cliquez sur **Envoyer à Microsoft pour analyse**, puis sélectionnez l’une des valeurs suivantes dans la liste déroulante :

- **Nettoyer le rapport**
- **Signaler le hameçonnage**
- **Signaler un programme malveillant**
- **Signaler le courrier indésirable**
- **Déclencher une enquête**

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/admin-submission-main-action-button.png" alt-text="Nouvelles options sur le bouton Action" lightbox="../../media/admin-submission-main-action-button.png":::

Si le message est signalé à Microsoft, la valeur **de soumission convertie en administrateur** passe de **non** à **oui**. Vous pouvez accéder directement à la soumission de l’administrateur en cliquant sur **Afficher la soumission administrateur convertie** à partir du menu de dépassement dans le menu volant de soumission du message signalé par l’utilisateur concerné.

:::image type="content" source="../../media/view-converted-admin-submission.png" alt-text="Option permettant d’afficher une soumission d’administrateur créée à partir d’un message signalé par l’utilisateur.":::
