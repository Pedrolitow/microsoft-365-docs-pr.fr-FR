---
title: Installer et utiliser le complément de création de rapports de courrier indésirable pour Microsoft Outlook
f1.keywords:
- NOCSH
ms.author: siosulli
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: 4650fec1-4ee3-4659-abbc-bf091718cb26
ms.collection:
- M365-security-compliance
description: Découvrez comment installer et utiliser le complément Microsoft Junk Email Reporting pour signaler les messages de courrier indésirable, de courrier indésirable et de hameçonnage à Microsoft.
ms.openlocfilehash: 6f08c72ae797825695c443848429dcfd2cd485a2
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49616427"
---
# <a name="install-and-use-the-junk-email-reporting-add-in-for-microsoft-outlook"></a>Installer et utiliser le complément de création de rapports de courrier indésirable pour Microsoft Outlook

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


> [!NOTE]
> Si vous n’utilisez pas actuellement le complément de création de rapports de courrier indésirable, nous vous recommandons d’utiliser le [complément de rapport de message](enable-the-report-message-add-in.md) . Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

Le complément de création de rapports de courrier indésirable pour Microsoft Outlook permet aux utilisateurs de soumettre des faux positifs (courrier électronique marqué comme courrier indésirable), des faux négatifs (courrier incorrect autorisé) et des messages de hameçonnage à Microsoft. Si votre organisation n’utilise pas Exchange Online Protection (par exemple, les services de messagerie ou Exchange locaux autres qu’Exchange Online), votre envoi de rapports de courrier indésirable n’affecte pas le filtrage du courrier indésirable.

Cette rubrique explique comment installer et utiliser le complément de création de rapports de courrier indésirable.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour installer le complément de création de rapports de courrier indésirable, voir la section relative à l' [installation du complément de création de rapports de courrier indésirable](#install-the-junk-email-reporting-add-in) plus loin dans cette rubrique.

- Le complément de création de rapports de courrier indésirable fonctionne avec les versions suivantes d’Outlook :

  - Outlook 2013 ou une version ultérieure
  - Outlook inclus avec les applications Microsoft 365 pour les entreprises

- Pour plus d’informations sur la création de rapports de messages à Microsoft, consultez la rubrique [signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="use-the-junk-email-reporting-add-in-to-report-spam-and-phishing-messages"></a>Utiliser le complément de création de rapports de courrier indésirable pour signaler les messages de courrier indésirable et de hameçonnage

1. Pour les messages de la boîte de réception ou de tout autre dossier de messagerie, à l’exception du courrier indésirable, utilisez l’une des méthodes suivantes pour signaler les messages de courrier indésirable et de hameçonnage :

   - Sélectionnez le message ou ouvrez le message. Dans l’onglet **Accueil** ou **message** du ruban, cliquez sur **courrier indésirable**, puis sélectionnez **signaler comme courrier indésirable** ou **signaler comme hameçonnage**.

     ![Signaler le courrier indésirable ou de hameçonnage à partir du ruban](../../media/junk-email-reporting-ribbon.png)

   - Cliquez avec le bouton droit sur le message, sélectionnez **courrier indésirable**, puis **signaler comme courrier indésirable** ou **signaler comme hameçonnage**.

     ![Signaler le courrier indésirable ou le courrier indésirable en cliquant avec le bouton droit](../../media/junk-email-reporting-right-click.png)

   - Sélectionnez plusieurs messages, cliquez avec le bouton droit, puis sélectionnez **signaler comme courrier indésirable** ou **signaler comme hameçonnage**.

     ![Signaler plusieurs messages de courrier indésirable ou de hameçonnage à partir d’un clic droit](../../media/junk-email-reporting-right-click-multiple.png)

2. Dans la boîte de dialogue qui s’affiche, lisez les informations, puis cliquez sur **rapport**. Si vous changez d’avis, cliquez sur **ne pas signaler**.

   ![Boîte de dialogue signaler comme courrier indésirable](../../media/junk-email-reporting-report-as-junk-dialog.png)

   ![Boîte de dialogue signaler en tant que hameçonnage](../../media/junk-email-reporting-report-as-phishing-dialog.png)

3. Les messages sélectionnés seront envoyés à Microsoft pour analyse et :

   - Déplacé vers le dossier courrier indésirable s’il a été signalé comme courrier indésirable.
   - Supprimé s’il a été signalé comme hameçonnage.

   Pour confirmer que les messages ont été envoyés, ouvrez le dossier **Éléments envoyés** pour afficher les messages envoyés.

## <a name="use-the-junk-email-reporting-add-in-to-report-non-spam-and-phishing-messages-from-the-junk-email-folder"></a>Utiliser le complément de création de rapports de courrier indésirable pour signaler les messages de courrier indésirable et de hameçonnage dans le dossier courrier indésirable

1. Dans le dossier courrier indésirable, utilisez l’une des méthodes suivantes pour signaler les fausses alertes de courrier indésirable ou les messages de hameçonnage :

   - Sélectionnez le message ou ouvrez le message. Dans l’onglet **Accueil** ou **message** du ruban, cliquez sur **légitime**, puis sélectionnez **signaler comme légitime** ou **signaler comme hameçonnage**.

     ![Signaler des courriers indésirables ou de hameçonnage à partir du ruban dans le dossier courrier indésirable](../../media/junk-email-reporting-junk-folder-ribbon.png)

   - Cliquez avec le bouton droit sur le message, cliquez sur **courrier indésirable**, puis sélectionnez **signaler comme légitime** ou **signaler comme hameçonnage**.

     ![Signaler le courrier indésirable ou le courrier indésirable dans le dossier courrier indésirable](../../media/junk-email-reporting-junk-folder-right-click.png)

   - Sélectionnez plusieurs messages, cliquez avec le bouton droit, puis sélectionnez **signaler comme légitime** ou **signaler comme hameçonnage**.

     ![Signaler plusieurs messages électroniques de courrier indésirable ou de hameçonnage dans le dossier courrier indésirable](../../media/junk-email-reporting-junk-folder-right-click-multiple.png)

2. Dans la boîte de dialogue qui s’affiche, lisez les informations, puis cliquez sur **rapport**. Si vous changez d’avis, cliquez sur **ne pas signaler**.

   ![Boîte de dialogue signaler comme légitime](../../media/junk-email-reporting-report-as-not-junk-dialog.png)

   ![Boîte de dialogue signaler en tant que hameçonnage](../../media/junk-email-reporting-report-as-phishing-dialog.png)

3. Les messages sélectionnés seront envoyés à Microsoft pour analyse et :

   - Déplacé vers le dossier courrier indésirable s’il a été signalé comme courrier indésirable.
   - Supprimé s’il a été signalé comme hameçonnage.

   Pour confirmer que les messages ont été envoyés, ouvrez le dossier **Éléments envoyés** pour afficher les messages envoyés.

## <a name="install-the-junk-email-reporting-add-in"></a>Installer le complément de création de rapports de courrier indésirable

- Vous devez disposer des privilèges d’administrateur sur l’ordinateur sur lequel vous installez le complément.

- Accédez au <https://www.microsoft.com/download/details.aspx?id=18275> fichier. msi approprié pour votre version d’Office et téléchargez-le dans un emplacement facile à trouver :

  - **32-bit**: `Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (32-bit).msi`
  - **64-bit**: `Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (64-bit).msi`

- Pour Outlook 2013 ou version ultérieure, la seule condition requise est Microsoft .NET Framework 2,0. Dans Windows 10, vous n’installez pas .NET Framework 2,0 à partir d’un téléchargement.

### <a name="install-the-junk-email-reporting-add-in-using-the-setup-wizard"></a>Installer le complément de création de rapports de courrier indésirable à l’aide de l’Assistant Installation

1. Sur votre ordinateur, fermez Outlook.

2. Dans Windows 10, vérifiez que .NET Framework 2,0 est activé. Pour obtenir des instructions, consultez [la rubrique activer le .NET Framework 3,5 dans le panneau de configuration](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10#enable-the-net-framework-35-in-control-panel).

3. Recherchez le fichier. msi que vous avez téléchargé et double-cliquez dessus.

4. Dans la page **Bienvenue à la configuration du complément Microsoft Junk Email Reporting**, cliquez sur **Suivant**.

5. Consultez le contrat de licence, cliquez sur **J’accepte les termes du contrat de licence** si vous acceptez les termes, puis cliquez sur **suivant**.

6. Une fois l'exécution de l'Assistant terminée, cliquez sur **Terminer**.

Lancez Outlook.

Consultez le bouton **Courrier indésirable** sur votre ruban Outlook. Vous pouvez à présent signaler des messages de courrier indésirable à Microsoft en les sélectionnant dans votre boîte de réception, puis en cliquant sur le bouton permettant de **signaler le courrier indésirable**.

Cliquez sur la flèche vers le bas en regard du bouton **Courrier indésirable** pour plus d'options, telles que le **signalement en tant que hameçonnage** si vous souhaitez signaler des messages électroniques d'hameçonnage à Microsoft. Dans votre dossier de courrier indésirable, vous pouvez également sélectionner l'option de **signalement en tant que courrier non indésirable** si un message électronique a été identifié à tort comme courrier indésirable.

### <a name="install-the-junk-email-reporting-add-in-using-silent-mode"></a>Installation du complément de création de rapports de courrier indésirable en mode sans assistance

1. Sur votre ordinateur, fermez Outlook.

2. Dans Windows 10, installez .NET Framework 2,0 en exécutant la commande suivante :

   ```dos
   DISM /Online /Enable-Feature /FeatureName:NetFx3 /All
   ```

3. Pour installer le complément sans intervention de l’utilisateur, ouvrez une invite de commandes et utilisez la syntaxe suivante :

   ```dos
   msiexec /qn /i "<PathToMSIFile>\<MSIFile>" [MaxMessageSelection=<1-50>] [BccEmailAddress="<EmailAddress1>; <EmailAddress2>"...]
   ```

   - `MaxMessageSelection` Spécifie le nombre maximal de messages que vous pouvez sélectionner pour une seule soumission. Les valeurs valides sont comprises entre 1 et 50. Par défaut, la valeur 15 s’applique.

   - `BccEmailAddress` spécifie les destinataires CCI supplémentaires qui recevront une copie de tous les envois de tous les utilisateurs. La valeur par défaut est vide (pas de destinataires CCI supplémentaires).

   Cet exemple installe la version 64 bits du complément à partir du chemin d’accès spécifié avec les paramètres par défaut.

   ```dos
   msiexec /qn /i "C:\Downloads\Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (64-bit).msi"
   ```

   Cet exemple installe la version 32 bits du complément à partir du chemin d’accès spécifié avec les paramètres supplémentaires suivants :

   - Vous pouvez sélectionner jusqu’à 20 messages en une seule soumission.
   - junkreports@contoso.com et hollyd@treyresearch.net reçoivent des copies CCI de toutes les soumissions.

   ```dos
   msiexec /qn /i "C:\Downloads\Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (32-bit).msi" MaxMessageSelection=20 BccEmailAddress="junkreports@contoso.com; hollyd@treyresearch.net"
   ```

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez correctement installé le complément de création de rapports de courrier indésirable, effectuez l’une des opérations suivantes dans Outlook :

- Sélectionnez le message ou ouvrez le message. Dans l’onglet **Accueil** ou **message** du ruban, cliquez sur **courrier indésirable** et vérifiez que les options suivantes sont disponibles :

  - **Signaler comme courrier indésirable**
  - **Signaler comme hameçonnage**
  - **Options de signalement de courrier indésirable**
  - **Signaler une aide en ligne indésirable**

  ![Signaler le courrier indésirable ou de hameçonnage à partir du ruban](../../media/junk-email-reporting-ribbon.png)

- Cliquez avec le bouton droit sur le message, sélectionnez **courrier indésirable** et assurez-vous que les options suivantes sont disponibles :

  - **Signaler comme courrier indésirable**
  - **Signaler comme hameçonnage**
  - **Options de signalement de courrier indésirable**
  - **Signaler une aide en ligne indésirable**

  ![Signaler le courrier indésirable ou le courrier indésirable en cliquant avec le bouton droit](../../media/junk-email-reporting-right-click.png)

- Sélectionnez plusieurs messages, cliquez avec le bouton droit et vérifiez que les options suivantes sont disponibles :

  - **Signaler comme courrier indésirable**
  - **Signaler comme hameçonnage**

  ![Signaler plusieurs messages de courrier indésirable ou de hameçonnage à partir d’un clic droit](../../media/junk-email-reporting-right-click-multiple.png)

- Effectuez les actions précédentes dans le dossier courrier **indésirable** et vérifiez que les options de signalement de **courrier** indésirable précédentes ne sont **pas des courriers indésirables**.

  ![Signaler des courriers indésirables ou de hameçonnage à partir du ruban dans le dossier courrier indésirable](../../media/junk-email-reporting-junk-folder-ribbon.png)

  ![Signaler le courrier indésirable ou le courrier indésirable dans le dossier courrier indésirable](../../media/junk-email-reporting-junk-folder-right-click.png)

  ![Signaler plusieurs messages électroniques de courrier indésirable ou de hameçonnage dans le dossier courrier indésirable](../../media/junk-email-reporting-junk-folder-right-click-multiple.png)

## <a name="uninstall-the-junk-email-reporting-add-in"></a>Désinstallation du complément Junk Email Reporting

Une fois que vous avez fermé Outlook, utilisez l’une des procédures suivantes pour désinstaller le complément de création de rapports de courrier indésirable :

- **Panneau de configuration**: Appuyez sur la touche Windows + R. Dans la boîte de dialogue **exécuter** qui s’ouvre, saisissez `control appwiz.cpl` puis cliquez sur **OK**.

  Recherchez et sélectionnez **complément Microsoft Junk Email Reporting** dans la liste, puis cliquez sur **désinstaller**.

- **Package Windows Installer**: recherchez ou téléchargez le fichier. msi approprié, puis double-cliquez dessus.

  - **32-bit**: `Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (32-bit).msi`

  - **64-bit**: `Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (64-bit).msi`

  Dans la boîte de dialogue qui s’affiche, sélectionnez **supprimer le complément Microsoft Junk Email Reporting pour Outlook** , puis cliquez sur **suivant**.

- **Mode silencieux**: recherchez ou téléchargez le fichier. msi approprié. Dans une fenêtre d’invite de commandes, remplacez \<PathToFile\> par l’emplacement du fichier. msi et exécutez l’une des commandes suivantes :

  - **32-bit**:

    ```dos
    msiexec /x "<PathToFile>\Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (32-bit).msi" /qn MSIRESTARTMANAGERCONTROL="DisableShutdown"
    ```

  - **64-bit**:

    ```dos
    msiexec /x "<PathToFile>\Junk Reporting Add-in for Office 2007, 2010, 2013, and 2016 (64-bit).msi" /qn MSIRESTARTMANAGERCONTROL="DisableShutdown"
    ```

Lorsque vous ouvrez Outlook après la désinstallation, les options de signalement de courrier indésirable, de courrier indésirable et de hameçonnage doivent être supprimées.

## <a name="troubleshooting-the-junk-email-reporting-add-in"></a>Dépannage du complément de création de rapports de courrier indésirable

Parfois, vous pouvez rencontrer des problèmes avec Outlook après avoir ajouté le complément de création de rapports de courrier indésirable. Cette section décrit les problèmes que vous pouvez rencontrer, ainsi que des conseils pour la résolution de ces problèmes.

### <a name="troubleshooting-for-users"></a>Résolution des problèmes pour les utilisateurs

Vous rencontrez un ou plusieurs des problèmes suivants :

- Rien ne se passe quand vous cliquez sur **Signaler le courrier indésirable**.
- Outlook cesse de répondre après avoir sélectionné un message électronique
- Le courrier indésirable signalé ne peut pas être remis en raison d'une réponse « Non remis ».

Pour résoudre ce problème, procédez comme suit :

1. Fermez et redémarrez Outlook.
2. Créez et envoyez un message de test, puis vérifiez que le destinataire a reçu le message.
3. Si le problème persiste, contactez votre administrateur.

Pour les autres méthodes que vous pouvez utiliser pour envoyer des messages à Microsoft, consultez la rubrique [signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

### <a name="troubleshooting-for-admins"></a>Résolution des problèmes liés aux administrateurs

#### <a name="problem-an-error-message-continually-appears-that-asks-users-to-contact-their-system-administrator"></a>Problème : un message d’erreur s’affiche en continu qui demande aux utilisateurs de contacter leur administrateur système.

1. Vérifiez ou définissez la `LoggingLevel` clé de Registre sur la valeur « verbose » :

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

2. Redémarrez Outlook et demandez aux utilisateurs de revenir en arrière lorsqu’ils voient le message d’erreur.

3. Collectez les informations de journal se trouvant à l'emplacement suivant :

   `%LOCALAPPDATA%\Microsoft\Junk Email Reporting Add-in\SpamReporterAddinLog.txt`

4. Contactez les techniciens du support Exchange Online Protection et fournissez-leur les informations du journal.

#### <a name="problem-users-selected-not-to-receive-a-confirmation-prompt-when-they-report-messages-and-now-they-want-the-prompt-back"></a>Problème : les utilisateurs sélectionnés ne reçoivent pas d’invite de confirmation lorsqu’ils signalent des messages, et souhaitent maintenant que l’invite se redirige.

1. Créez la `ConfirmReportJunk` clé de Registre avec la valeur « true » :

   ```text
   Windows Registry Editor Version 5.00

   HKEY_CURRENT_USER\Software\Microsoft\Junk E-mail Reporting\Preferences]
   "ConfirmReportJunk"="True"
   ```

2. Redémarrez Outlook.
