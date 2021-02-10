---
title: Installer et utiliser le add-in Junk Email Reporting pour Microsoft Outlook
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
ms.assetid: 4650fec1-4ee3-4659-abbc-bf091718cb26
ms.collection:
- M365-security-compliance
description: Découvrez comment installer et utiliser le add-in De rapport de courrier indésirable Microsoft pour signaler le courrier indésirable, le courrier non indésirable et le hameçonnage à Microsoft.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 171bdc43e565a0890cddcd1e48208b49774a5315
ms.sourcegitcommit: a1846b1ee2e4fa397e39c1271c997fc4cf6d5619
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2021
ms.locfileid: "50167346"
---
# <a name="install-and-use-the-junk-email-reporting-add-in-for-microsoft-outlook"></a>Installer et utiliser le add-in Junk Email Reporting pour Microsoft Outlook

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](https://go.microsoft.com/fwlink/?linkid=2148611)
- [Microsoft Defender pour Office 365 plan 1 et plan 2](https://go.microsoft.com/fwlink/?linkid=2148715)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!NOTE]
> Si vous n’utilisez pas actuellement le add-in Junk [](enable-the-report-message-add-in.md) E-mail Reporting, [](enable-the-report-phish-add-in.md) nous vous recommandons plutôt de le signaler ou de signaler le hameçonnage. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

Le junk email reporting Add-in pour Microsoft Outlook permet aux utilisateurs d’envoyer des faux positifs (message électronique de qualité marqué comme courrier indésirable), des faux négatifs (courrier indésirable autorisé) et des messages de hameçonnage à Microsoft. Si votre organisation n’utilise pas Exchange Online Protection (par exemple, Exchange local ou des services de messagerie autres qu’Exchange Online), l’envoi de votre rapport de courrier indésirable n’affecte pas votre filtrage du courrier indésirable.

Cette rubrique explique comment installer et utiliser le add-in Junk Email Reporting.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour installer le add-in Junk Email Reporting, consultez la section [Install the Junk Email Reporting add-in](#install-the-junk-email-reporting-add-in) later in this article.

- Le add-in Junk Email Reporting fonctionne avec les versions suivantes d’Outlook :

  - Outlook 2013 ou une version ultérieure
  - Outlook inclus avec Microsoft 365 Apps for enterprise

- Pour plus d’informations sur la notification des messages à Microsoft, voir [Signaler des messages et des fichiers à Microsoft.](report-junk-email-messages-to-microsoft.md)

## <a name="use-the-junk-email-reporting-add-in-to-report-spam-and-phishing-messages"></a>Utiliser le add-in Junk Email Reporting (Signalement du courrier indésirable) pour signaler les messages de courrier indésirable et de hameçonnage

1. Pour les messages dans la boîte de réception ou tout autre dossier de courrier électronique à l’exception du courrier indésirable, utilisez l’une des méthodes suivantes pour signaler le courrier indésirable et les messages de hameçonnage :

   - Sélectionnez le message ou ouvrez-le. Dans **l’onglet** Accueil **ou Message** du ruban,  cliquez sur Courrier **indésirable,** puis sélectionnez Signaler comme courrier indésirable ou Signaler **comme hameçonnage.**

     ![Signaler le courrier indésirable ou le hameçonnage à partir du ruban](../../media/junk-email-reporting-ribbon.png)

   - Cliquez avec le bouton droit sur le  message, **sélectionnez** Courrier indésirable, puis sélectionnez Signaler comme courrier indésirable **ou Signaler comme hameçonnage.**

     ![Signaler le courrier indésirable ou le hameçonnage à partir du clic droit](../../media/junk-email-reporting-right-click.png)

   - Sélectionnez plusieurs messages, cliquez avec le bouton droit, puis sélectionnez **Signaler comme** courrier indésirable ou Signaler **comme hameçonnage.**

     ![Signaler plusieurs messages électroniques de courrier indésirable ou de hameçonnage à partir du clic droit](../../media/junk-email-reporting-right-click-multiple.png)

2. Dans la boîte de dialogue qui s’affiche, lisez les informations et cliquez sur **Rapport.** Si vous changez d’avis, cliquez sur **Ne pas signaler.**

   ![Boîte de dialogue Signaler comme courrier indésirable](../../media/junk-email-reporting-report-as-junk-dialog.png)

   ![Boîte de dialogue Signaler comme hameçonnage](../../media/junk-email-reporting-report-as-phishing-dialog.png)

3. Les messages sélectionnés sont envoyés à Microsoft pour analyse et :

   - Déplacé vers le dossier Courrier indésirable s’il a été signalé comme courrier indésirable.
   - Supprimé s’il a été signalé comme hameçonnage.

   Pour confirmer que les messages ont été envoyés, ouvrez le dossier **Éléments envoyés** pour afficher les messages envoyés.

## <a name="use-the-junk-email-reporting-add-in-to-report-non-spam-and-phishing-messages-from-the-junk-email-folder"></a>Utiliser le add-in Junk Email Reporting (Signalement du courrier indésirable) pour signaler les messages de courrier non indésirable et de hameçonnage à partir du dossier Courrier indésirable

1. Dans le dossier Courrier indésirable, utilisez l’une des méthodes suivantes pour signaler les faux positifs du courrier indésirable ou les messages de hameçonnage :

   - Sélectionnez le message ou ouvrez-le. Dans **l’onglet** Accueil ou **Message** du ruban,  cliquez sur Ne pas courrier **indésirable,** puis sélectionnez Signaler comme courrier non indésirable ou Signaler **comme hameçonnage.**

     ![Signaler le courrier indésirable ou le hameçonnage à partir du ruban dans le dossier Courrier indésirable](../../media/junk-email-reporting-junk-folder-ribbon.png)

   - Cliquez avec le bouton droit sur le  message, **cliquez** sur Courrier indésirable, puis sélectionnez Signaler comme courrier non indésirable ou Signaler **comme hameçonnage.**

     ![Signaler le courrier indésirable ou le hameçonnage en cliquant avec le bouton droit dans le dossier Courrier indésirable](../../media/junk-email-reporting-junk-folder-right-click.png)

   - Sélectionnez plusieurs messages, cliquez avec le bouton droit, puis sélectionnez **Signaler comme** courrier non indésirable ou Signaler **comme hameçonnage.**

     ![Signaler plusieurs messages électroniques non indésirables ou de hameçonnage en cliquant avec le bouton droit dans le dossier Courrier indésirable](../../media/junk-email-reporting-junk-folder-right-click-multiple.png)

2. Dans la boîte de dialogue qui s’affiche, lisez les informations et cliquez sur **Rapport.** Si vous changez d’avis, cliquez sur **Ne pas signaler.**

   ![Boîte de dialogue Signaler comme courrier indésirable](../../media/junk-email-reporting-report-as-not-junk-dialog.png)

   ![Boîte de dialogue Signaler comme hameçonnage](../../media/junk-email-reporting-report-as-phishing-dialog.png)

3. Les messages sélectionnés sont envoyés à Microsoft pour analyse et :

   - Déplacé vers le dossier Courrier indésirable s’il a été signalé comme courrier indésirable.
   - Supprimé s’il a été signalé comme hameçonnage.

   Pour confirmer que les messages ont été envoyés, ouvrez le dossier **Éléments envoyés** pour afficher les messages envoyés.

## <a name="install-the-junk-email-reporting-add-in"></a>Installer le add-in Junk Email Reporting

- Vous devez avoir des privilèges d’administrateur sur l’ordinateur sur lequel vous installez le module.

- Go to <https://www.microsoft.com/download/details.aspx?id=18275> and download the appropriate .msi file for your version of Office to a location that’s easy to find:

  - **32 bits**: `Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (32-bit).msi`
  - **64 bits**: `Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (64-bit).msi`

- Pour Outlook 2013 ou une ultérieure, le seul prérequis est Microsoft .NET Framework 2.0. Dans Windows 10, vous n’installez pas .NET Framework 2.0 à partir d’un téléchargement.

### <a name="install-the-junk-email-reporting-add-in-using-the-setup-wizard"></a>Installer le add-in Junk Email Reporting à l’aide de l’Assistant Installation

1. Sur votre ordinateur, fermez Outlook.

2. Dans Windows 10, vérifiez que .NET Framework 2.0 est activé. Pour obtenir des instructions, voir [Activer .NET Framework 3.5 dans le Panneau de contrôle.](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10#enable-the-net-framework-35-in-control-panel)

3. Recherchez le fichier .msi que vous avez téléchargé et double-cliquez dessus.

4. Dans la page **Bienvenue à la configuration du complément Microsoft Junk Email Reporting**, cliquez sur **Suivant**.

5. Examinez le contrat de licence, cliquez **sur J’accepte** les termes du contrat de licence si vous acceptez les termes, puis cliquez sur **Suivant**.

6. Une fois l'exécution de l'Assistant terminée, cliquez sur **Terminer**.

Lancez Outlook.

Consultez le bouton **Courrier indésirable** sur votre ruban Outlook. Vous pouvez à présent signaler des messages de courrier indésirable à Microsoft en les sélectionnant dans votre boîte de réception, puis en cliquant sur le bouton permettant de **signaler le courrier indésirable**.

Cliquez sur la flèche vers le bas en regard du bouton **Courrier indésirable** pour plus d'options, telles que le **signalement en tant que hameçonnage** si vous souhaitez signaler des messages électroniques d'hameçonnage à Microsoft. Dans votre dossier de courrier indésirable, vous pouvez également sélectionner l'option de **signalement en tant que courrier non indésirable** si un message électronique a été identifié à tort comme courrier indésirable.

### <a name="install-the-junk-email-reporting-add-in-using-silent-mode"></a>Installation du complément de création de rapports de courrier indésirable en mode sans assistance

1. Sur votre ordinateur, fermez Outlook.

2. Dans Windows 10, installez .NET Framework 2.0 en exécutant la commande suivante :

   ```dos
   DISM /Online /Enable-Feature /FeatureName:NetFx3 /All
   ```

3. Pour installer le module sans intervention de l’utilisateur, ouvrez une invite de commandes et utilisez la syntaxe suivante :

   ```dos
   msiexec /qn /i "<PathToMSIFile>\<MSIFile>" [MaxMessageSelection=<1-50>] [BccEmailAddress="<EmailAddress1>; <EmailAddress2>"...]
   ```

   - `MaxMessageSelection` spécifie le nombre maximal de messages que vous pouvez sélectionner pour une soumission unique. Les valeurs valides sont de 1 à 50. Par défaut, la valeur 15 s’applique.

   - `BccEmailAddress` spécifie les destinataires Bcc supplémentaires qui recevront une copie de toutes les soumissions d’utilisateurs. La valeur par défaut est vide (aucun destinataire Bcc supplémentaire).

   Cet exemple installe la version 64 bits du module à partir du chemin d’accès spécifié avec les paramètres par défaut.

   ```dos
   msiexec /qn /i "C:\Downloads\Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (64-bit).msi"
   ```

   Cet exemple installe la version 32 bits du complément à partir du chemin d’accès spécifié avec les paramètres supplémentaires suivants :

   - Jusqu’à 20 messages peuvent être sélectionnés dans une seule soumission.
   - junkreports@contoso.com et hollyd@treyresearch.net recevoir des copies Bcc de toutes les soumissions.

   ```dos
   msiexec /qn /i "C:\Downloads\Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (32-bit).msi" MaxMessageSelection=20 BccEmailAddress="junkreports@contoso.com; hollyd@treyresearch.net"
   ```

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez correctement installé le add-in Junk Email Reporting, faites l’une des étapes suivantes dans Outlook :

- Sélectionnez le message ou ouvrez-le. Dans **l’onglet** Accueil **ou Message** du ruban, cliquez sur Courrier indésirable **et** vérifiez que les options suivantes sont disponibles :

  - **Signaler comme courrier indésirable**
  - **Signaler comme hameçonnage**
  - **Options de signalement du courrier indésirable**
  - **Signaler l’aide de Junk Online**

  ![Signaler le courrier indésirable ou le hameçonnage à partir du ruban](../../media/junk-email-reporting-ribbon.png)

- Cliquez avec le bouton droit sur le message, **sélectionnez** Courrier indésirable et vérifiez que les options suivantes sont disponibles :

  - **Signaler comme courrier indésirable**
  - **Signaler comme hameçonnage**
  - **Options de signalement du courrier indésirable**
  - **Signaler l’aide de Junk Online**

  ![Signaler le courrier indésirable ou le hameçonnage à partir du clic droit](../../media/junk-email-reporting-right-click.png)

- Sélectionnez plusieurs messages, cliquez avec le bouton droit et vérifiez que les options suivantes sont disponibles :

  - **Signaler comme courrier indésirable**
  - **Signaler comme hameçonnage**

  ![Signaler plusieurs messages électroniques de courrier indésirable ou de hameçonnage à partir du clic droit](../../media/junk-email-reporting-right-click-multiple.png)

- Faites les actions précédentes dans le **dossier Courrier** indésirable et vérifiez que les options **de** signalement de courrier indésirable précédentes sont désormais **non** indésirables.

  ![Signaler le courrier indésirable ou le hameçonnage à partir du ruban dans le dossier Courrier indésirable](../../media/junk-email-reporting-junk-folder-ribbon.png)

  ![Signaler le courrier indésirable ou le hameçonnage en cliquant avec le bouton droit dans le dossier Courrier indésirable](../../media/junk-email-reporting-junk-folder-right-click.png)

  ![Signaler plusieurs messages électroniques non indésirables ou de hameçonnage en cliquant avec le bouton droit dans le dossier Courrier indésirable](../../media/junk-email-reporting-junk-folder-right-click-multiple.png)

## <a name="uninstall-the-junk-email-reporting-add-in"></a>Désinstallation du complément Junk Email Reporting

Après avoir fermé Outlook, utilisez l’une des procédures suivantes pour désinstaller le add-in Junk Email Reporting :

- **Panneau de commande**: appuyez sur la touche Windows + R. Dans la **boîte de** dialogue Exécuter qui s’ouvre, `control appwiz.cpl` entrez, puis cliquez sur **OK.**

  Recherchez et **sélectionnez le** module de rapport de courrier indésirable Microsoft dans la liste, puis cliquez sur **Désinstaller.**

- **Package Windows Installer**: recherchez ou téléchargez le fichier .msi approprié, puis double-cliquez dessus.

  - **32 bits**: `Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (32-bit).msi`

  - **64 bits**: `Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (64-bit).msi`

  Dans la boîte de dialogue qui s’affiche, **sélectionnez Supprimer** le nouveau rapport de courrier indésirable Microsoft pour Outlook, puis cliquez sur **Suivant.**

- **Mode silencieux**: recherchez ou téléchargez le fichier .msi approprié. Dans une fenêtre d’invite de commandes, remplacez-la par l’emplacement du fichier .msi et exécutez l’une \<PathToFile\> des commandes suivantes :

  - **32 bits**:

    ```dos
    msiexec /x "<PathToFile>\Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (32-bit).msi" /qn MSIRESTARTMANAGERCONTROL="DisableShutdown"
    ```

  - **64 bits**:

    ```dos
    msiexec /x "<PathToFile>\Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (64-bit).msi" /qn MSIRESTARTMANAGERCONTROL="DisableShutdown"
    ```

Lorsque vous ouvrez Outlook après la désinstallation, les options de signalement du courrier indésirable, et non du courrier indésirable et du hameçonnage doivent avoir disparu.

## <a name="troubleshooting-the-junk-email-reporting-add-in"></a>Résolution des problèmes du add-in Junk Email Reporting

Parfois, vous pouvez avoir des difficultés avec Outlook après l’ajout du add-in Junk Email Reporting. Cette section décrit les problèmes que vous pouvez rencontrer, ainsi que des conseils pour résoudre ces problèmes.

### <a name="troubleshooting-for-users"></a>Résolution des problèmes pour les utilisateurs

Vous devez faire l’expérience d’un ou de plusieurs des problèmes suivants :

- Rien ne se passe quand vous cliquez sur **Signaler le courrier indésirable**.
- Outlook cesse de répondre après avoir sélectionné un message électronique
- Le courrier indésirable signalé ne peut pas être remis en raison d'une réponse « Non remis ».

Pour résoudre ce problème, faites les étapes suivantes :

1. Fermez et redémarrez Outlook.
2. Créez et envoyez un message de test, puis vérifiez que le destinataire a reçu le message.
3. Si le problème persiste, contactez votre administrateur.

Pour d’autres méthodes que vous pouvez utiliser pour envoyer des messages à Microsoft, voir Signaler les messages et [les fichiers à Microsoft.](report-junk-email-messages-to-microsoft.md)

### <a name="troubleshooting-for-admins"></a>Résolution des problèmes pour les administrateurs

#### <a name="problem-an-error-message-continually-appears-that-asks-users-to-contact-their-system-administrator"></a>Problème : un message d’erreur s’affiche en permanence pour demander aux utilisateurs de contacter leur administrateur système

1. Vérifiez ou définissez `LoggingLevel` la clé de Registre sur la valeur « Verbose » :

   - **Outlook 32 bits sur Windows 32 bits**:

     ```text
     Windows Registry Editor Version 5.00

     [HKEY_LOCAL_MACHINE\Software\Microsoft\Junk Email Reporting\Addins]
     "LoggingLevel"="Verbose"
     ```

   - **Outlook 32 bits sur Windows 64 bits**:

     ```text
     Windows Registry Editor Version 5.00

     [HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\Junk Email Reporting\Addins]
     "LoggingLevel"="Verbose"
     ```

   - **Outlook 64 bits**:

     ```text
     Windows Registry Editor Version 5.00

     [HKEY_LOCAL_MACHINE\Software\Microsoft\Junk E-mail Reporting\Addins]
     "LoggingLevel"="Verbose"
     ```

2. Redémarrez Outlook et demandez aux utilisateurs de les signaler lorsqu’ils voient le message d’erreur.

3. Collectez les informations de journal se trouvant à l'emplacement suivant :

   `%LOCALAPPDATA%\Microsoft\Junk Email Reporting Add-in\SpamReporterAddinLog.txt`

4. Contactez les techniciens du support Exchange Online Protection et fournissez-leur les informations du journal.

#### <a name="problem-users-selected-not-to-receive-a-confirmation-prompt-when-they-report-messages-and-now-they-want-the-prompt-back"></a>Problème : les utilisateurs ont choisi de ne pas recevoir d’invite de confirmation lorsqu’ils signalaient des messages, et veulent maintenant que l’invite soit de nouveau

1. Créez `ConfirmReportJunk` la clé de Registre avec la valeur « True » :

   ```text
   Windows Registry Editor Version 5.00

   HKEY_CURRENT_USER\Software\Microsoft\Junk E-mail Reporting\Preferences]
   "ConfirmReportJunk"="True"
   ```

2. Redémarrez Outlook.
