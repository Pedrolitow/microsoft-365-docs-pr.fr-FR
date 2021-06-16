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
description: Les administrateurs peuvent apprendre à utiliser le portail Soumissions dans le portail Microsoft 365 Defender pour soumettre à Microsoft des messages suspects, des messages de hameçonnage suspects, du courrier indésirable et d’autres messages potentiellement dangereux, des URL et des pièces jointes de courrier électronique à Microsoft pour la réessuration.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b671ce5a44c7be61331a121b49e96658cf14bab1
ms.sourcegitcommit: 1c11035dd4432e34603022740baef0c8f7ff4425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2021
ms.locfileid: "52964800"
---
# <a name="use-admin-submission-to-submit-suspected-spam-phish-urls-and-files-to-microsoft"></a>Utilisez la soumission de l’administrateur pour soumettre des courriers indésirables, l’hameçonnage, des URL et des fichiers à Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)


Dans Microsoft 365 organisations ayant des boîtes aux lettres Exchange Online, les administrateurs peuvent utiliser le portail Soumissions dans le portail Microsoft 365 Defender pour envoyer des messages électroniques, des URL et des pièces jointes à Microsoft pour analyse.

Lorsque vous envoyez un message électronique, vous recevez les messages suivants :

- **Vérification de l’authentification du** courrier électronique : détails sur la réussi ou l’échec de l’authentification de messagerie lors de sa livraison.
- **Accès aux** stratégies : informations sur les stratégies qui ont autorisé ou bloqué le courrier entrant dans votre client, en remplacement de nos verdicts de filtre de service.
- **Réputation/détonation de la charge utile**: examen des URL et pièces jointes du message.
- **Analyse du gradeur**: révision effectuée par des élèves humains afin de confirmer si les messages sont malveillants ou non.

> [!IMPORTANT]
> L’analyse de réputation/détonation et de grader de la charge utile n’est pas effectuée dans tous les locataires. Les informations ne peuvent pas sortir de l’organisation lorsque les données ne sont pas supposées quitter la limite du client à des fins de conformité.

Pour d’autres façons de soumettre des messages électroniques, des URL et des pièces jointes à Microsoft, voir [Signaler des messages et des fichiers à Microsoft.](report-junk-email-messages-to-microsoft.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com/>. Pour aller directement à la page **Soumissions,** utilisez <https://security.microsoft.com/reportsubmission> .

- Pour envoyer des messages et des fichiers à Microsoft, vous devez être membre de l’un des groupes de rôles suivants :
  - **Lecteur Gestion de l’organisation** **ou Sécurité** dans [le portail Microsoft 365 Defender.](permissions-microsoft-365-security-center.md)
  - **Gestion de l’organisation** [dans Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups).

    Notez que l’appartenance à ce groupe de rôles est nécessaire pour afficher les [soumissions](#view-user-submissions-to-microsoft) d’utilisateurs à la boîte aux lettres personnalisée, comme décrit plus loin dans cet article.

- Pour plus d’informations sur la façon dont les utilisateurs peuvent envoyer des messages et des fichiers à Microsoft, voir Signaler des messages et [des fichiers à Microsoft.](report-junk-email-messages-to-microsoft.md)

## <a name="report-suspicious-content-to-microsoft"></a>Signaler du contenu suspect à Microsoft

1. Dans le portail Microsoft 365 Defender, go to **Email & collaboration** \> **Submissions**.

2. Dans la page **Soumissions,** vérifiez que l’onglet Soumis pour analyse est sélectionné, puis cliquez sur Icône Annonce Envoyer à Microsoft pour  ![ ](../../media/m365-cc-sc-create-icon.png) **analyse.**

3. Utilisez le **volant Envoyer à Microsoft** pour révision qui apparaît pour envoyer le message, l’URL ou la pièce jointe d’un e-mail, comme décrit dans les sections suivantes.

### <a name="submit-a-questionable-email-to-microsoft"></a>Envoyer un e-mail douteux à Microsoft

1. Dans la **zone Sélectionner le type de** soumission, vérifiez que l’e-mail est sélectionné dans la liste de listes. 

2. Dans la section **Ajouter l’ID de message** réseau ou télécharger le fichier de courrier électronique, utilisez l’une des options suivantes :
   - Ajoutez **l’ID** du message réseau de messagerie : il s’agit d’une valeur GUID disponible dans l’en-tête **X-MS-Exchange-Organization-Network-Message-Id** dans le message ou dans l’en-tête **X-MS-Office365-Filtering-Correlation-Id** dans les messages mis en quarantaine.
   - **Télécharger fichier e-mail (.msg ou .eml)**: cliquez **sur Parcourir les fichiers.** Dans la boîte de dialogue qui s’ouvre, recherchez et sélectionnez le fichier .eml ou .msg, puis cliquez sur **Ouvrir**.

   > [!NOTE]
   > La possibilité de soumettre des messages depuis 30 jours a été temporairement suspendue pour Defender pour Office 365 clients. Les administrateurs ne pourront revenir qu’à 7 jours.

3. Dans la **zone Choisir un destinataire qui a eu** un problème, spécifiez le destinataire sur qui vous souhaitez exécuter une vérification de stratégie. La vérification de stratégie détermine si le courrier électronique a contourné l’analyse en raison des stratégies utilisateur ou organisation.

4. Dans la section **Sélectionner une raison d’envoyer à Microsoft,** sélectionnez l’une des options suivantes :
   - **Ne doit pas avoir été bloqué (faux positif)**
   - **Doit avoir été bloqué**: dans l’e-mail doit avoir été catégorisé en tant que **section** qui s’affiche, sélectionnez l’une des valeurs suivantes (si vous n’êtes pas sûr, utilisez votre meilleur résultat) :
     - **Hameçonnage**
     - **Courrier indésirable**
     - **Programme malveillant**

5. Lorsque vous avez terminé, cliquez sur le **bouton** Envoyer.

   ![Exemple de soumission d’URL](../../media/submission-flyout-email.PNG)

### <a name="send-a-suspect-url-to-microsoft"></a>Envoyer une URL suspecte à Microsoft

1. Dans la **zone Sélectionner le type de** soumission, sélectionnez **l’URL** dans la liste bas.

2. Dans la **zone URL** qui s’affiche, entrez l’URL complète (par exemple, `https://www.fabrikam.com/marketing.html` ).

3. Dans la section **Sélectionner une raison d’envoyer à Microsoft,** sélectionnez l’une des options suivantes :
   - **Ne doit pas avoir été bloqué (faux positif)**
   - **Doit avoir été bloqué :** dans l’URL, cette URL doit **avoir** été classée en tant que section qui s’affiche, sélectionnez **Hameçonnage** ou **Programme malveillant**.

4. Lorsque vous avez terminé, cliquez sur le **bouton** Envoyer.

   ![Exemple d’envoi de nouveaux e-mails](../../media/submission-url-flyout.png)

### <a name="submit-a-suspected-email-attachment-to-microsoft"></a>Envoyer une pièce jointe suspecte à Microsoft

1. Dans la **zone Sélectionner le type de** soumission, **sélectionnez Fichier** dans la liste liste.

2. Dans la section **Fichier** qui s’affiche, cliquez **sur Parcourir les fichiers.** Dans la boîte de dialogue qui s’ouvre, recherchez et sélectionnez le fichier, puis cliquez sur **Ouvrir.**

3. Dans la section **Sélectionner une raison d’envoyer à Microsoft,** sélectionnez l’une des options suivantes :
   - **Ne doit pas avoir été bloqué (faux positif)**
   - **Doit avoir été bloqué**: dans l’URL qui s’affiche, le programme malveillant est le seul choix et est automatiquement sélectionné.  

4. Lorsque vous avez terminé, cliquez sur le **bouton** Envoyer.

   ![Exemple d’envoi de nouvelles pièces jointes](../../media/submission-file-flyout.PNG)

## <a name="view-admin-submissions-to-microsoft"></a>Afficher les soumissions d’administrateur à Microsoft

1. Dans le portail Microsoft 365 Defender, go to **Email & collaboration** \> **Submissions**.

2. Dans la page **Soumissions,** vérifiez que l’onglet Soumis **pour** analyse est sélectionné.

   - Vous pouvez trier les entrées en cliquant sur un en-tête de colonne disponible. Cliquez **sur Personnaliser les colonnes** pour afficher un maximum de sept colonnes. Les valeurs par défaut sont marquées d'un astérisque (<sup>\*</sup>) :
     - **Nom de la soumission**<sup>\*</sup>
     - **Expéditeur**<sup>\*</sup>
     - **Date d’soumise**<sup>\*</sup>
     - **Type de soumission**<sup>\*</sup>
     - **Raison de l’envoi**<sup>\*</sup>
     - **État rescan**<sup>\*</sup>
     - **Résultat rescan**<sup>\*</sup>
     - **Verdict du filtre**
     - **Raison de la remise/du blocage**
     - **ID de soumission**
     - **ID de message réseau/ID d’objet**
     - **Direction**
     - **IP de l’expéditeur**
     - **Niveau de conformité en bloc (BCL)**
     - **Destination**
     - **Action de stratégie**
     - **Soumis par**

     Lorsque vous avez terminé, cliquez sur **Appliquer.**

   - Pour filtrer les entrées, cliquez sur **Filtrer.** Les filtres disponibles sont :
     - **Date envoyée**: **date de début** et date de **fin.**
     - **Type de soumission**: **e-mail,** **URL** ou **fichier**.
     - **ID de soumission**: valeur GUID attribuée à chaque soumission.
     - **ID de message réseau**
     - **Sender**

     Lorsque vous avez terminé, cliquez sur **Appliquer.**

     ![Nouvelles options de filtre pour les soumissions d’administrateur](../../media/admin-submission-email-filter-options.png)

   - Pour grouper les entrées, cliquez sur **Grouper** et sélectionnez l’une des valeurs suivantes dans la liste suivante :
     - **Aucune**
     - **Type (Type)**
     - **Raison**
     - **État**
     - **Résultat rescan**

   - Pour exporter les entrées, cliquez sur **Exporter.** Dans la boîte de dialogue qui s’affiche, enregistrez .csv fichier.

### <a name="admin-submission-rescan-details"></a>Détails de la rescan de soumission de l’administrateur

Les messages envoyés dans les soumissions d’administrateur sont réassurés et les résultats sont affichés dans le flyout détaillé des soumissions :

- En cas d’échec de l’authentification des e-mails de l’expéditeur au moment de la livraison.
- Informations sur les accès à la stratégie qui auraient pu affecter ou écraser le verdict d’un message.
- Résultats actuels de la détonation pour savoir si les URL ou fichiers contenus dans le message étaient malveillants ou non.
- Commentaires des élèves.

Si le programme a trouvé un remplacement, la nouvelle analyse doit se terminer après plusieurs minutes. S’il n’y a pas de problème dans l’authentification ou la remise du courrier électronique n’a pas été affecté par une substitution, les commentaires des élèves peuvent prendre jusqu’à un jour.

## <a name="view-user-submissions-to-microsoft"></a>Afficher les soumissions d’utilisateurs à Microsoft

Si vous avez déployé le [add-in](enable-the-report-message-add-in.md) [](enable-the-report-phish-add-in.md)Signaler un message, le module de signalement du hameçonnage ou que des personnes utilisent les rapports intégrés dans  [Outlook sur le web,](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md)vous pouvez voir les utilisateurs qui signalent dans l’onglet Message signalé par l’utilisateur.

1. Dans le portail Microsoft 365 Defender, go to **Email & collaboration** \> **Submissions**.

2. Dans la page **Soumissions,** sélectionnez **l’onglet Messages signalés par l’utilisateur.**

   - Vous pouvez trier les entrées en cliquant sur un en-tête de colonne disponible. Cliquez **sur Personnaliser les colonnes** pour afficher un maximum de sept colonnes. Les valeurs par défaut sont marquées d'un astérisque (<sup>\*</sup>) :

     - **Objet de l’e-mail**<sup>\*</sup>
     - **Signalé par**<sup>\*</sup>
     - **Date de rapport**<sup>\*</sup>
     - **Expéditeur**<sup>\*</sup>
     - **Raison signalée**<sup>\*</sup>
     - **Résultat rescan**<sup>\*</sup>
     - **ID de message signalé**
     - **ID de message réseau**
     - **IP de l’expéditeur**
     - **Simulation de hameçonnage**

     Lorsque vous avez terminé, cliquez sur **Appliquer.**

   - Pour filtrer les entrées, cliquez sur **Filtrer.** Les filtres disponibles sont :
     - **Date signalée**: **date de début** et date de **fin.**
     - **Auteur du rapport**
     - **Sujet de l’e-mail**
     - **ID de message signalé**
     - **ID de message réseau**
     - **Sender**
     - **Raison signalée :** **pas de courrier indésirable,** **de hameçonnage** ou de **courrier indésirable.**
     - **Simulation de hameçonnage**: **Oui** ou **Non**

     Lorsque vous avez terminé, cliquez sur **Appliquer.**

    ![Nouvelles options de filtre pour les soumissions d’utilisateurs](../../media/user-submissions-filter-options.png)

   - Pour grouper les entrées, cliquez sur **Grouper** et sélectionnez l’une des valeurs suivantes dans la liste suivante :
     - **Aucune**
     - **Raison**
     - **Sender**
     - **Auteur du rapport**
     - **Résultat rescan**
     - **Simulation de hameçonnage**

   - Pour exporter les entrées, cliquez sur **Exporter.** Dans la boîte de dialogue qui s’affiche, enregistrez .csv fichier.

> [!NOTE]
> Si les organisations sont configurées pour envoyer des messages signalés par l’utilisateur à la boîte aux lettres personnalisée uniquement, les messages signalés ne seront pas envoyés pour réascan et les résultats dans les **messages** signalés par l’utilisateur seront toujours vides.

### <a name="undo-user-submissions"></a>Annuler les soumissions d’utilisateurs

Lorsqu’un utilisateur envoie un message suspect à la boîte aux lettres personnalisée, l’utilisateur et l’administrateur n’ont pas la possibilité d’annuler la soumission. Si l’utilisateur souhaite récupérer le courrier électronique, il pourra être récupéré dans les dossiers Éléments supprimés ou Courrier indésirable.

### <a name="submit-messages-to-microsoft-from-the-custom-mailbox"></a>Envoyer des messages à Microsoft à partir de la boîte aux lettres personnalisée

Si vous avez configuré la boîte aux lettres personnalisée pour intercepter les messages signalés par l’utilisateur sans les envoyer à Microsoft, vous pouvez rechercher et envoyer des messages spécifiques à Microsoft pour analyse. Cela déplace efficacement une soumission d’utilisateur vers une soumission d’administrateur.

Sous **l’onglet Messages** signalés par l’utilisateur, sélectionnez un message dans la liste, cliquez sur Envoyer à **Microsoft** pour analyse, puis sélectionnez l’une des valeurs suivantes dans la liste suivante :

- **Signaler propre**
- **Signaler le hameçonnage**
- **Signaler un programme malveillant**
- **Signaler le courrier indésirable**
- **Déclencher l’examen**

![Nouvelles options sur le bouton Action](../../media/user-submission-custom-mailbox-action-button.png)
