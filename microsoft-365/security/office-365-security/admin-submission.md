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
- m365-security
- m365initiative-defender-office365
ms.custom: seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser le portail Soumissions dans le portail Microsoft 365 Defender pour envoyer des e-mails légitimes bloqués, des e-mails suspects, des e-mails suspects de hameçonnage, du courrier indésirable, d’autres messages potentiellement dangereux, des URL et des pièces jointes à Microsoft pour la rescanning.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: a9b8c64e989c14d0e5bfd9c3b8ca03dbcd93ae20
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68072786"
---
# <a name="use-the-submissions-portal-to-submit-suspected-spam-phish-urls-legitimate-email-getting-blocked-and-email-attachments-to-microsoft"></a>Utilisez le portail Soumissions pour envoyer des courriers indésirables, des hameçonnages, des URL, des e-mails légitimes bloqués et des pièces jointes à Microsoft

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online, les administrateurs peuvent utiliser le portail Soumissions dans le portail Microsoft 365 Defender pour envoyer des e-mails, des URL et des pièces jointes à Microsoft à des fins d’analyse.

Lorsque vous envoyez un e-mail à des fins d’analyse, vous obtenez :

- **Email vérification de l’authentification** : détails sur la réussite ou l’échec de l’authentification par e-mail lors de sa remise.
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

## <a name="report-questionable-email-to-microsoft"></a>Signaler un e-mail douteux à Microsoft

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , vérifiez que l’onglet **e-mails** est sélectionné.

3. Sous l’onglet **e-mails** , cliquez sur ![l’icône Envoyer à Microsoft pour l’analyse.](../../media/m365-cc-sc-create-icon.png) **Envoyer à Microsoft pour analyse**.

4. Dans le menu volant **Envoyer à Microsoft pour analyse** qui s’affiche, entrez les informations suivantes :

   - **Sélectionnez le type de soumission** : vérifiez que la valeur **Email** est sélectionnée.

   - **Ajoutez l’ID de message réseau ou chargez le fichier e-mail** : sélectionnez l’une des options suivantes :

     - **Ajoutez l’ID de message réseau de messagerie** : il s’agit d’une valeur GUID disponible dans l’en-tête **X-MS-Exchange-Organization-Network-Message-Id** dans le message ou dans l’en-tête **X-MS-Office365-Filtering-Correlation-Id** dans les messages mis en quarantaine.

     - **Charger le fichier e-mail (.msg ou .eml)** : cliquez sur **Parcourir les fichiers**. Dans la boîte de dialogue qui s’ouvre, recherchez et sélectionnez le fichier .eml ou .msg, puis cliquez sur **Ouvrir**.

   - **Choisissez un destinataire qui a rencontré un problème** : spécifiez le destinataire sur lequel vous souhaitez exécuter une vérification de stratégie. La vérification de stratégie détermine si l’e-mail a contourné l’analyse en raison de stratégies d’utilisateur ou d’organisation.

   - **Sélectionnez une raison de soumission à Microsoft** : La vérification **ne doit pas avoir été bloquée (Faux positif)** est sélectionnée.

     - **L’e-mail doit avoir été classé comme suit** : Sélectionner **le hameçonnage**, les **programmes malveillants** ou **le courrier indésirable**. Si vous n’êtes pas sûr, utilisez votre meilleur jugement.

     - **Bloquer tous les e-mails de cet expéditeur ou domaine** : sélectionnez cette option pour créer une entrée de bloc pour l’expéditeur dans la liste d’autorisations/de blocs du locataire. Pour plus d’informations sur la liste d’autorisations/blocages du locataire, consultez [Gérer vos autorisations et blocs dans la liste d’autorisations/de blocs du locataire](manage-tenant-allow-block-list.md).

       Une fois cette option sélectionnée, les paramètres suivants sont disponibles :

       - Par défaut, **l’expéditeur** est sélectionné, mais vous pouvez sélectionner **Domaine** à la place.

       - **Supprimer l’entrée de bloc après** : la valeur par défaut est **30 jours**, mais vous pouvez sélectionner parmi les valeurs suivantes :
           - **1 jour**
           - **7 jours**
           - **30 jours**
           - **90 jours**
           - **N’expirez jamais**
           - **Date spécifique**

       - **Note d’entrée de bloc** : entrez des informations facultatives sur la raison pour laquelle vous autorisez cet e-mail.

   Lorsque vous avez terminé, cliquez sur **Envoyer**, puis sur **Terminé**.

:::image type="content" source="../../media/admin-submission-email-block.png" alt-text="Envoyez un e-mail faux négatif (incorrect) à Microsoft pour analyse sur la page Soumissions dans le portail Defender." lightbox="../../media/admin-submission-email-block.png":::

> [!NOTE]
> Pour les messages qui ont été bloqués de manière incorrecte par [l’intelligence d’usurpation](learn-about-spoof-intelligence.md) d’identité, une entrée de bloc pour la paire de domaines n’est pas créée dans la liste d’autorisations/de blocs du locataire.
>
> Pour les messages qui ont été bloqués de manière incorrecte par la protection d’emprunt d’identité de [domaine ou d’utilisateur](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365), une entrée de bloc pour le domaine ou l’expéditeur n’est pas créée dans la liste d’autorisation/de blocage du locataire. Au lieu de cela, le domaine ou l’expéditeur est ajouté à la **section Expéditeurs approuvés et domaines** dans la [stratégie anti-hameçonnage](configure-mdo-anti-phishing-policies.md#use-the-microsoft-365-defender-portal-to-modify-anti-phishing-policies) qui a détecté le message.

## <a name="report-questionable-email-attachments-to-microsoft"></a>Signaler des pièces jointes contestables à Microsoft

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions**, sélectionnez l’onglet **Email pièces jointes**.

3. Sous **l’onglet Email pièces jointes**, cliquez sur ![Icône Envoyer à Microsoft pour analyse.](../../media/m365-cc-sc-create-icon.png) **Envoyer à Microsoft pour analyse**.

4. Dans le menu volant **Envoyer à Microsoft pour analyse** qui s’affiche, entrez les informations suivantes :

   - **Sélectionnez le type d’envoi** : vérifiez la valeur **Email pièce jointe** est sélectionnée.

   - **Fichier** : cliquez sur **Parcourir les fichiers** pour rechercher et sélectionner le fichier à envoyer.

   - **Sélectionnez une raison pour l’envoi à Microsoft** : La vérification **doit avoir été bloquée (Faux négatif)** est sélectionnée.

     - **L’e-mail doit avoir été classé comme suit** : Sélectionner **hameçonnage** ou **programme malveillant**. Si vous n’êtes pas sûr, utilisez votre meilleur jugement.

     - **Bloquer ce fichier** : sélectionnez cette option pour créer une entrée de bloc pour l’expéditeur dans la liste d’autorisation/de blocage du locataire. Pour plus d’informations sur la liste d’autorisations/blocages du locataire, consultez [Gérer vos autorisations et blocs dans la liste d’autorisations/de blocs du locataire](manage-tenant-allow-block-list.md).

       Une fois cette option sélectionnée, les paramètres suivants sont disponibles :

       - **Supprimer l’entrée de bloc après** : la valeur par défaut est **30 jours**, mais vous pouvez sélectionner parmi les valeurs suivantes :
           - **1 jour**
           - **7 jours**
           - **30 jours**
           - **90 jours**
           - **N’expirez jamais**
           - **Date spécifique**

       - **Note d’entrée de bloc** : entrez des informations facultatives sur la raison pour laquelle vous autorisez cet e-mail.

   Lorsque vous avez terminé, cliquez sur **Envoyer**, puis sur **Terminé**.

:::image type="content" source="../../media/admin-submission-file-block.png" alt-text="Envoyez une fausse pièce jointe négative (incorrecte) à Microsoft pour analyse sur la page Soumissions dans le portail Defender." lightbox="../../media/admin-submission-file-block.png":::

## <a name="report-questionable-urls-to-microsoft"></a>Signaler des URL douteuses à Microsoft

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , sélectionnez l’onglet **URL** .

3. Sous l’onglet **URL** , cliquez sur ![Envoyer à Microsoft pour l’analyse, bouton Ajouter.](../../media/m365-cc-sc-create-icon.png) **Envoyer à Microsoft pour analyse**.

4. Dans le menu volant **Envoyer à Microsoft pour analyse** qui s’affiche, entrez les informations suivantes :

   - **Sélectionnez le type de soumission** : vérifiez que **l’URL** de la valeur est sélectionnée.

   - **URL** : entrez l’URL complète (par exemple, `https://www.fabrikam.com/marketing.html`), puis sélectionnez-la dans la zone qui s’affiche.

   - **Sélectionnez une raison pour l’envoi à Microsoft** : La vérification **doit avoir été bloquée (Faux négatif)** est sélectionnée.

     - **L’e-mail doit avoir été classé comme suit** : Sélectionner **hameçonnage** ou **programme malveillant**. Si vous n’êtes pas sûr, utilisez votre meilleur jugement.

     - **Bloquer cette URL** : sélectionnez cette option pour créer une entrée de bloc pour l’expéditeur dans la liste d’autorisations/de blocs du locataire. Pour plus d’informations sur la liste d’autorisations/blocages du locataire, consultez [Gérer vos autorisations et blocs dans la liste d’autorisations/de blocs du locataire](manage-tenant-allow-block-list.md).

       Une fois cette option sélectionnée, les paramètres suivants sont disponibles :

       - **Supprimer l’entrée de bloc après** : la valeur par défaut est **30 jours**, mais vous pouvez sélectionner parmi les valeurs suivantes :
           - **1 jour**
           - **7 jours**
           - **30 jours**
           - **90 jours**
           - **N’expirez jamais**
           - **Date spécifique**

       - **Note d’entrée de bloc** : entrez des informations facultatives sur la raison pour laquelle vous autorisez cet e-mail.

   Lorsque vous avez terminé, cliquez sur **Envoyer**, puis sur **Terminé**.

:::image type="content" source="../../media/admin-submission-url-block.png" alt-text="Envoyez une URL false négative (incorrecte) à Microsoft pour analyse sur la page Soumissions dans le portail Defender." lightbox="../../media/admin-submission-url-block.png":::

## <a name="report-good-email-to-microsoft"></a>Signaler un bon e-mail à Microsoft

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , vérifiez que l’onglet **e-mails** est sélectionné.

3. Sous l’onglet **e-mails** , cliquez sur ![l’icône Envoyer à Microsoft pour l’analyse.](../../media/m365-cc-sc-create-icon.png) **Envoyer à Microsoft pour analyse**.

4. Dans le menu volant **Envoyer à Microsoft pour analyse** qui s’affiche, entrez les informations suivantes :

   - **Sélectionnez le type de soumission** : vérifiez que la valeur **Email** est sélectionnée.

   - **Ajoutez l’ID de message réseau ou chargez le fichier e-mail** : sélectionnez l’une des options suivantes :

     - **Ajoutez l’ID de message réseau de messagerie** : il s’agit d’une valeur GUID disponible dans l’en-tête **X-MS-Exchange-Organization-Network-Message-Id** dans le message ou dans l’en-tête **X-MS-Office365-Filtering-Correlation-Id** dans les messages mis en quarantaine.

     - **Charger le fichier e-mail (.msg ou .eml)** : cliquez sur **Parcourir les fichiers**. Dans la boîte de dialogue qui s’ouvre, recherchez et sélectionnez le fichier .eml ou .msg, puis cliquez sur **Ouvrir**.

   - **Choisissez un destinataire qui a rencontré un problème** : spécifiez le destinataire sur lequel vous souhaitez exécuter une vérification de stratégie. La vérification de stratégie détermine si l’e-mail a été bloqué en raison de stratégies d’utilisateur ou d’organisation.

   - **Sélectionnez une raison pour l’envoi à Microsoft** : La sélection **ne doit pas avoir été bloquée (Faux positif),** puis configurez les paramètres suivants :

     - **Autoriser les e-mails avec des attributs similaires (URL, expéditeur, etc.)** : activez ce paramètre![.](../../media/scc-toggle-on.png)

         - **Supprimer l’entrée d’autorisation après** : la valeur par défaut est **30 jours**, mais vous pouvez sélectionner parmi les valeurs suivantes :
           - **1 jour**
           - **7 jours**
           - **30 jours**
           - **Date spécifique** : la valeur maximale est de 30 jours à compter d’aujourd’hui.

           Pour les expéditeurs usurpés, cette valeur n’a aucun sens, car les entrées des expéditeurs usurpés n’expirent jamais.

         - **Autoriser la note d’entrée** : entrez des informations facultatives sur la raison pour laquelle vous autorisez cet e-mail.

           Pour les expéditeurs usurpés, toute valeur que vous entrez ici n’est pas affichée dans l’entrée d’autorisation sous l’onglet **Expéditeurs usurpés** de **l’option Tenant Allow/Block List**.

   Lorsque vous avez terminé, cliquez sur **Envoyer**, puis sur **Terminé**.

   :::image type="content" source="../../media/admin-submission-email-allow.png" alt-text="Envoyez un e-mail faux positif (bon) à Microsoft pour analyse sur la page Soumissions dans le portail Defender." lightbox="../../media/admin-submission-email-allow.png":::

Après quelques instants, l’entrée d’autorisation s’affiche dans l’onglet **Domaines & adresses** ou **expéditeurs usurpés** sur la page **Autoriser/Bloquer la liste** des locataires.

> [!NOTE]
>
> - Lorsque vous remplacez le verdict dans l’insight d’intelligence de l’usurpation d’identité, l’expéditeur usurpé devient une entrée d’autorisation ou de blocage manuelle qui apparaît uniquement sous l’onglet **Expéditeurs usurpés** dans la liste d’autorisation/de blocage du locataire.
> - Si l’expéditeur n’a pas encore été bloqué, l’envoi de l’e-mail à Microsoft ne crée pas d’entrée d’autorisation dans la liste d’autorisation/de blocage du locataire.
> - Les autorisations sont ajoutées pendant le flux de messagerie, en fonction des filtres qui ont déterminé que le message était malveillant. Par exemple, si l’expéditeur et une URL du message ont été déterminés comme étant incorrects, une entrée d’autorisation est créée pour l’expéditeur et une entrée d’autorisation est créée pour l’URL.
> - Lorsque cette entité (adresse de domaine ou e-mail, URL, fichier) est à nouveau rencontrée, tous les filtres associés à cette entité sont ignorés.
> - Pendant le flux de courrier, si les messages du domaine ou de l’adresse e-mail passent d’autres vérifications dans la pile de filtrage, les messages sont remis. Par exemple, si [l’authentification par e-mail](email-validation-and-authentication.md) réussit, un message d’un expéditeur dans l’entrée d’autorisation est remis.

## <a name="report-good-email-attachments-to-microsoft"></a>Signaler de bonnes pièces jointes à Microsoft

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions**, sélectionnez l’onglet **Email pièces jointes**.

3. Sous l’onglet **Email pièces jointes**, cliquez sur ![l’icône Envoyer à Microsoft pour l’analyse.](../../media/m365-cc-sc-create-icon.png) **Envoyer à Microsoft pour analyse**.

4. Dans le menu volant **Envoyer à Microsoft pour analyse** qui s’affiche, entrez les informations suivantes :

   - **Sélectionnez le type d’envoi** : vérifiez la valeur **Email pièce jointe** est sélectionnée.

   - **Fichier** : cliquez sur **Parcourir les fichiers** pour rechercher et sélectionner le fichier à envoyer.

   - **Sélectionnez une raison pour l’envoi à Microsoft** : La sélection **ne doit pas avoir été bloquée (Faux positif),** puis configurez les paramètres suivants :

     - **Autoriser ce fichier** : activez ce paramètre ![activé](../../media/scc-toggle-on.png).

         - **Supprimer l’entrée d’autorisation après** : la valeur par défaut est **30 jours**, mais vous pouvez sélectionner parmi les valeurs suivantes :
           - **1 jour**
           - **7 jours**
           - **30 jours**
           - **Date spécifique** : la valeur maximale est de 30 jours à compter d’aujourd’hui.

         - **Note d’entrée d’autorisation** : entrez des informations facultatives sur la raison pour laquelle vous autorisez ce fichier.

   Lorsque vous avez terminé, cliquez sur **Envoyer**, puis sur **Terminé**.

   :::image type="content" source="../../media/admin-submission-file-allow.png" alt-text="Envoyez une pièce jointe de faux positif (bon) à Microsoft pour analyse sur la page Soumissions dans le portail Defender." lightbox="../../media/admin-submission-file-allow.png":::

Après quelques instants, une entrée d’autorisation s’affiche sous l’onglet **Fichiers** de la page **Autoriser/Bloquer** la liste des locataires.

> [!NOTE]
> Lorsque le fichier est à nouveau rencontré, il n’est pas envoyé pour la détonation des [pièces jointes sécurisées ou les vérifications](safe-attachments.md) de la réputation des fichiers, et tous les autres filtres basés sur des fichiers sont ignorés. Pendant le flux de courrier, si les messages contenant le fichier passent d’autres vérifications non liées aux fichiers dans la pile de filtrage, les messages sont remis.

## <a name="report-good-urls-to-microsoft"></a>Signaler de bonnes URL à Microsoft

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions**, sélectionnez l’onglet **URL**

3. Sous l’onglet **URL** , cliquez sur ![l’icône Envoyer à Microsoft pour analyse.](../../media/m365-cc-sc-create-icon.png) **Envoyer à Microsoft pour analyse**.

4. Dans le menu volant **Envoyer à Microsoft pour analyse** qui s’affiche, entrez les informations suivantes :

   - **Sélectionnez le type de soumission** : vérifiez que **l’URL** de la valeur est sélectionnée.

   - **URL** : entrez l’URL complète (par exemple, `https://www.fabrikam.com/marketing.html`), puis sélectionnez-la dans la zone qui s’affiche. Vous pouvez également fournir un domaine de niveau supérieur (par exemple), `https://www.fabrikam.com/*`puis le sélectionner dans la zone qui s’affiche. 


   - **Sélectionnez une raison pour l’envoi à Microsoft** : La sélection **ne doit pas avoir été bloquée (Faux positif),** puis configurez les paramètres suivants :

     - **Autoriser cette URL** : activez ce paramètre ![activé](../../media/scc-toggle-on.png).

         - **Supprimer l’entrée d’autorisation après** : la valeur par défaut est **30 jours**, mais vous pouvez sélectionner parmi les valeurs suivantes :
           - **1 jour**
           - **7 jours**
           - **30 jours**
           - **Date spécifique** : la valeur maximale est de 30 jours à compter d’aujourd’hui.

         - **Note d’entrée d’autorisation** : entrez des informations facultatives sur la raison pour laquelle vous autorisez cette URL.

   Lorsque vous avez terminé, cliquez sur **Envoyer**, puis sur **Terminé**.

   :::image type="content" source="../../media/admin-submission-url-allow.png" alt-text="Envoyez une URL false positive (bonne) à Microsoft pour analyse sur la page Soumissions dans le portail Defender." lightbox="../../media/admin-submission-url-allow.png":::

Après quelques instants, une entrée d’autorisation s’affiche sous l’onglet **URL** de la page **Autoriser/Bloquer** la liste des locataires. Pour plus d’informations sur la liste d’autorisations/blocages du locataire, consultez [Gérer vos autorisations et blocs dans la liste d’autorisations/de blocs du locataire](manage-tenant-allow-block-list.md).

> [!NOTE]
>
> - Lorsque l’URL est à nouveau détectée, elle n’est pas envoyée pour les vérifications de détonation des [liens fiables](safe-links.md) ou de réputation d’URL, et tous les autres filtres basés sur l’URL sont ignorés.
> - Pendant le flux de courrier, si les messages contenant l’URL passent d’autres vérifications non URL dans la pile de filtrage, les messages sont remis.

## <a name="view-email-admin-submissions-to-microsoft"></a>Afficher les soumissions d’administrateur de messagerie à Microsoft

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , vérifiez que l’onglet **e-mails** est sélectionné.

   - Vous pouvez trier les entrées en cliquant sur un en-tête de colonne disponible.

   - Cliquez sur l’icône ![Personnaliser les colonnes.](../../media/m365-cc-sc-customize-icon.png) **Personnalisez les colonnes** pour sélectionner les colonnes que vous souhaitez afficher. Les valeurs par défaut sont marquées d'un astérisque (\*) :
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

     :::image type="content" source="../../media/admin-submission-email-customize-columns.png" alt-text="Option Personnaliser les colonnes pour les soumissions d’administrateur de courrier électronique." lightbox="../../media/admin-submission-email-customize-columns.png":::

   - Pour filtrer les entrées, cliquez sur ![l’icône Filtrer.](../../media/m365-cc-sc-filter-icon.png) **Filtre**. Les valeurs suivantes sont disponibles dans le menu volant **Filtre** qui s’affiche :
     - **Date d’envoi** : **valeurs de date de début** et de **date de fin** .
     - **ID de soumission** : valeur GUID affectée à chaque soumission.
     - **ID de message réseau**
     - **Sender**
     - **Destinataire**
     - **Name**
     - **Soumis par**
     - **Motif de l’envoi** : Les valeurs **ne sont pas indésirables**, **phish**, **programmes malveillants** et **courrier indésirable**.
     - **État** : valeurs **en attente** et **terminées**.
     - **Balises** : la valeur par défaut est **Tout** ou sélectionnez une [balise utilisateur](user-tags.md) dans la liste déroulante.

     Lorsque vous avez terminé, cliquez sur **Appliquer**. Pour effacer les filtres existants, cliquez sur ![Effacer les filtres **dans**](../../media/m365-cc-sc-clear-filters-icon.png) le menu volant **Filtrer**.

     :::image type="content" source="../../media/admin-submission-email-filters.png" alt-text="Options de filtre pour les soumissions d’administrateur de courrier électronique." lightbox="../../media/admin-submission-email-filters.png":::

   - Pour regrouper les entrées, cliquez sur l’icône ![Groupe.](../../media/m365-cc-sc-group-icon.png) **Regroupez** et sélectionnez l’une des valeurs suivantes dans la liste déroulante :
     - **Aucune**
     - **Raison**
     - **État**
     - **Résultat**
     - **Tags**

   - Pour exporter les entrées, cliquez sur ![l’icône Exporter.](../../media/m365-cc-sc-download-icon.png) **Exporter**. Dans la boîte de dialogue qui s’affiche, enregistrez le fichier .csv.

## <a name="view-email-attachment-admin-submissions-to-microsoft"></a>Afficher les soumissions d’administrateurs de pièces jointes à Microsoft

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions**, vérifiez que l’onglet **Email pièces jointes** est sélectionné.

   - Vous pouvez trier les entrées en cliquant sur un en-tête de colonne disponible.

   - Cliquez sur l’icône ![Personnaliser les colonnes.](../../media/m365-cc-sc-customize-icon.png) **Personnalisez les colonnes** pour sélectionner les colonnes que vous souhaitez afficher. Les valeurs par défaut sont marquées d'un astérisque (\*) :
     - **Nom de fichier de pièce jointe**<sup>\*</sup>
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

     :::image type="content" source="../../media/admin-submission-file-customize-columns.png" alt-text="Personnalisez les options de colonne pour les soumissions d’administrateurs de pièces jointes par e-mail.":::

   - Pour filtrer les entrées, cliquez sur ![l’icône Filtrer.](../../media/m365-cc-sc-filter-icon.png) **Filtre**. Les valeurs suivantes sont disponibles dans le menu volant **Filtre** qui s’affiche :
     - **Date d’envoi** : **Date de début** et **date de fin**.
     - **ID de soumission** : valeur GUID affectée à chaque soumission.
     - **Nom de fichier des pièces jointes**
     - **Soumis par**
     - **Motif de l’envoi**
     - **État**
     - **Balises** : la valeur par défaut est **Tout** ou sélectionnez une [balise utilisateur](user-tags.md) dans la liste déroulante.

     Lorsque vous avez terminé, cliquez sur **Appliquer**.

     :::image type="content" source="../../media/admin-submission-file-filters.png" alt-text="Options de filtre pour les soumissions d’administrateurs de pièces jointes par e-mail.":::

   - Pour regrouper les entrées, cliquez sur l’icône ![Groupe.](../../media/m365-cc-sc-group-icon.png) **Regroupez** et sélectionnez l’une des valeurs suivantes dans la liste déroulante :
     - **Aucune**
     - **Raison**
     - **État**
     - **Résultat**
     - **Tags**

   - Pour exporter les entrées, cliquez sur ![l’icône Exporter.](../../media/m365-cc-sc-download-icon.png) **Exporter**. Dans la boîte de dialogue qui s’affiche, enregistrez le fichier .csv.

## <a name="view-urls-admin-submissions-to-microsoft"></a>Afficher les soumissions d’administrateur d’URL à Microsoft

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , vérifiez que l’onglet **URL** est sélectionné.

   - Vous pouvez trier les entrées en cliquant sur un en-tête de colonne disponible.

   - Cliquez sur l’icône ![Personnaliser les colonnes.](../../media/m365-cc-sc-customize-icon.png) **Personnalisez les colonnes** pour sélectionner les colonnes que vous souhaitez afficher. Les valeurs par défaut sont marquées d'un astérisque (\*) :
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

     :::image type="content" source="../../media/admin-submission-url-customize-columns.png" alt-text="Personnalisez les options de colonne pour les soumissions d’administrateur d’URL.":::

   - Pour filtrer les entrées, cliquez sur ![l’icône Filtrer.](../../media/m365-cc-sc-filter-icon.png) **Filtre**. Les valeurs suivantes sont disponibles dans le menu volant **Filtre** qui s’affiche :
     - **Date d’envoi** : **Date de début** et **date de fin**.
     - **ID de soumission** : valeur GUID affectée à chaque soumission.
     - **URL**
     - **Soumis par**
     - **Motif de l’envoi**
     - **État**
     - **Balises** : la valeur par défaut est **Tout** ou sélectionnez une [balise utilisateur](user-tags.md) dans la liste déroulante.

     Lorsque vous avez terminé, cliquez sur **Appliquer**. Pour effacer les filtres existants, cliquez sur ![Effacer les filtres **dans**](../../media/m365-cc-sc-clear-filters-icon.png) le menu volant **Filtrer**.

     :::image type="content" source="../../media/admin-submission-url-filters.png" alt-text="Options de filtre pour les soumissions d’administrateur d’URL.":::

   - Pour regrouper les entrées, cliquez sur l’icône ![Groupe.](../../media/m365-cc-sc-group-icon.png) **Regroupez** et sélectionnez l’une des valeurs suivantes dans la liste déroulante :
     - **Aucune**
     - **Raison**
     - **État**
     - **Résultat**
     - **Tags**

   - Pour exporter les entrées, cliquez sur ![l’icône Exporter.](../../media/m365-cc-sc-download-icon.png) **Exporter**. Dans la boîte de dialogue qui s’affiche, enregistrez le fichier .csv.

## <a name="admin-submission-result-details"></a>Administration détails du résultat de la soumission

Les messages envoyés dans les soumissions d’administrateur sont examinés par Microsoft et les résultats sont affichés dans le menu volant détaillé des soumissions :

- En cas d’échec de l’authentification des e-mails de l’expéditeur au moment de la livraison.
- Informations sur les accès à la stratégie qui auraient pu affecter ou écraser le verdict d’un message.
- Résultats actuels de la détonation pour savoir si les URL ou fichiers contenus dans le message étaient malveillants ou non.
- Commentaires des diplômés.

Si un remplacement a été trouvé, le résultat doit être disponible en quelques minutes. S’il n’y a pas eu de problème dans l’authentification par e-mail ou la remise n’a pas été affectée par un remplacement, les commentaires des élèves peuvent prendre jusqu’à une journée.

## <a name="view-user-submissions-to-microsoft"></a>Afficher les soumissions d’utilisateurs à Microsoft

Si vous avez déployé le [complément Message](enable-the-report-message-add-in.md) de rapport, le [complément Report Phishing](enable-the-report-phish-add-in.md) ou si des personnes utilisent la [création de rapports intégrée dans Outlook sur le web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md), vous pouvez voir ce que les utilisateurs signalent sous l’onglet **Message signalé par l’utilisateur**.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** dans **Actions & soumissions** \> **.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions** , sélectionnez l’onglet **Messages signalés par l’utilisateur** .

   - Cliquez sur l’icône ![Personnaliser les colonnes.](../../media/m365-cc-sc-customize-icon.png) **Personnalisez les colonnes** pour sélectionner les colonnes que vous souhaitez afficher. Les valeurs par défaut sont marquées d'un astérisque (\*) :
     - **Email sujet**<sup>\*</sup>
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

   - Pour filtrer les entrées, cliquez sur ![l’icône Filtrer.](../../media/m365-cc-sc-filter-icon.png) **Filtre**. Les valeurs suivantes sont disponibles dans le menu volant **Filtre** qui s’affiche :
     - **Date signalée** : **date de début** et **date de fin**.
     - **Auteur du rapport**
     - **Sujet de l’e-mail**
     - **ID signalé du message**
     - **ID de message réseau**
     - **Sender**
     - **Motif signalé** : les valeurs **ne sont pas indésirables**, **phish** ou **spam**.
     - **Signalé à partir de** : Valeurs du **complément Microsoft** ou **du complément tiers**.
     - **Simulation de hameçonnage** : Les valeurs **Oui** ou **Non**.
     - **Converti en soumission d’administrateur** : les valeurs **Oui** ou **Non**.
     - **Balises** : la valeur par défaut est **Tout** ou sélectionnez une [balise utilisateur](user-tags.md) dans la liste déroulante.

     Lorsque vous avez terminé, cliquez sur **Appliquer**. Pour effacer les filtres existants, cliquez sur ![Effacer les filtres **dans**](../../media/m365-cc-sc-clear-filters-icon.png) le menu volant **Filtrer**.

     > :::image type="content" source="../../media/admin-submission-user-reported-filters.png" alt-text="Options de filtre pour les soumissions d’utilisateurs." lightbox="../../media/admin-submission-user-reported-filters.png":::

   - Pour regrouper les entrées, cliquez sur l’icône ![Groupe.](../../media/m365-cc-sc-group-icon.png) **Regroupez** et sélectionnez l’une des valeurs suivantes dans la liste déroulante :
     - **Aucune**
     - **Raison**
     - **Sender**
     - **Auteur du rapport**
     - **Résultat**
     - **Signalé à partir de**
     - **Simulation de hameçonnage**
     - **Converti en soumission d’administrateur**
     - **Tags**

   - Pour exporter les entrées, cliquez sur ![l’icône Exporter.](../../media/m365-cc-sc-download-icon.png) **Exporter**. Dans la boîte de dialogue qui s’affiche, enregistrez le fichier .csv.

   - Pour avertir les utilisateurs, consultez [Administration Révision des messages signalés](admin-review-reported-message.md)

> [!NOTE]
> Si les organisations sont configurées pour envoyer des messages signalés par l’utilisateur [à la boîte aux lettres personnalisée uniquement](user-submission.md), les messages signalés apparaissent dans les **messages signalés par l’utilisateur** , mais leurs résultats sont toujours vides (car ils n’auraient pas été réexécuter).

## <a name="undo-user-submissions"></a>Annuler les soumissions d’utilisateurs

Une fois qu’un utilisateur envoie un e-mail suspect à la boîte aux lettres personnalisée, l’utilisateur et l’administrateur n’ont pas la possibilité d’annuler l’envoi. Si l’utilisateur souhaite récupérer l’e-mail, il est disponible pour la récupération dans ses dossiers Éléments supprimés ou Courrier indésirable Email.

## <a name="convert-user-reported-messages-from-the-custom-mailbox-into-an-admin-submission"></a>Convertir les messages signalés par l’utilisateur de la boîte aux lettres personnalisée en soumission d’administrateur

Si vous avez configuré la boîte aux lettres personnalisée pour intercepter les messages signalés par l’utilisateur sans envoyer les messages à Microsoft, vous pouvez rechercher et envoyer des messages spécifiques à Microsoft à des fins d’analyse.

Sous **l’onglet Messages signalés par l’utilisateur** , sélectionnez un message dans la liste, cliquez sur ![Envoyer à Microsoft pour l’ajout d’analyse.](../../media/m365-cc-sc-submit-user-reported-message-icon.png) **Soumettez à Microsoft pour analyse**, puis sélectionnez l’une des valeurs suivantes dans la liste déroulante :

- **Nettoyer le rapport**
- **Signaler le hameçonnage**
- **Signaler un programme malveillant**
- **Signaler le courrier indésirable**
- **Déclencher une enquête**

  :::image type="content" source="../../media/admin-submission-user-reported-submit-button-options.png" alt-text="Nouvelles options sur le bouton Action" lightbox="../../media/admin-submission-user-reported-submit-button-options.png":::

Si le message est signalé à Microsoft, la valeur **de soumission convertie en administrateur** passe de **non** à **oui**. Vous pouvez accéder directement à la soumission de l’administrateur en cliquant sur **Afficher la soumission administrateur convertie** à partir du menu de dépassement dans le menu volant de soumission du message signalé par l’utilisateur concerné.

:::image type="content" source="../../media/view-converted-admin-submission.png" alt-text="Option permettant d’afficher une soumission d’administrateur créée à partir d’un message signalé par l’utilisateur.":::

## <a name="view-associated-alert-for-user-and-admin-email-submissions"></a>Afficher l’alerte associée pour les envois de courriers électroniques utilisateur et administrateur

> [!IMPORTANT]
> Les informations contenues dans cette section s’appliquent uniquement à Defender pour Office 365 plan 2 ou supérieur.
>
> Actuellement, les soumissions d’utilisateurs génèrent des alertes uniquement pour les messages signalés comme hameçonnage.

Pour chaque message d’hameçonnage signalé par l’utilisateur et chaque envoi d’e-mail d’administrateur, une alerte correspondante est générée.

Pour afficher l’alerte correspondante pour un message d’hameçonnage signalé par l’utilisateur, sélectionnez l’onglet **Messages signalés par l’utilisateur** , puis double-cliquez sur le message pour ouvrir le menu volant de soumission. Cliquez sur l’icône ![Autres options.](../../media/m365-cc-sc-more-actions-icon.png) **Plus d’options** , puis sélectionnez  **Afficher l’alerte**.

:::image type="content" source="../../media/alert-from-user-submission.png" alt-text="Option permettant d’afficher l’alerte associée à partir d’un message d’hameçonnage signalé par l’utilisateur.":::

Pour afficher l’alerte correspondante pour les soumissions de courriers d’administration, sélectionnez l’onglet **e-mails** , puis double-cliquez sur le message pour ouvrir le menu volant de soumission. Sélectionnez **Afficher l’alerte** dans l’option **Ouvrir l’entité d’e-mail** .

:::image type="content" source="../../media/alert-from-admin-submission.png" alt-text="Option permettant d’afficher l’alerte associée à partir d’une soumission d’administrateur.":::
