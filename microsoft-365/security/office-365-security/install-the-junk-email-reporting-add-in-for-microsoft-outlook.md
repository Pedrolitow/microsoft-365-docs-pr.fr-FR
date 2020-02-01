---
title: Installation du complément de création de rapports de courrier indésirable pour Microsoft Outlook
f1.keywords:
- NOCSH
ms.author: MSFTTracyP
author: tracyp
manager: dansimp
ms.date: 12/9/2016
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: 8dcc752f-e22e-44ce-a104-4cc4d7e439f3
ms.collection:
- M365-security-compliance
description: Dans cette articleSupported LanguagesInstall le dossier Junk Email Reporting Add-ununinstall the Junk Email Reporting Add-inFor more information
ms.openlocfilehash: 0f7a5a3cbaddf9aef5e518db38ffb36c397cd1f0
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41599151"
---
# <a name="install-the-junk-email-reporting-add-in-for-microsoft-outlook"></a>Installation du complément de création de rapports de courrier indésirable pour Microsoft Outlook

Cette rubrique explique comment installer (et désinstaller) le complément Microsoft de création de rapports de courrier indésirable pour Outlook sur des ordinateurs clients au sein de votre organisation. La version actuelle du complément (janvier 2016) inclut la prise en charge d’Outlook 2016, Outlook 2013 et Outlook 2010.

Le complément (pour toutes les langues prises en charge) vous permet de signaler du courrier indésirable directement à partir du ruban Outlook. La version anglaise du complément inclut des options supplémentaires pour signaler des problèmes liés à la messagerie à Microsoft directement à partir du ruban :

- Signaler les messages électroniques de hameçonnage que vous recevez

- Signalez les messages électroniques identifiés à tort comme du courrier indésirable.

## <a name="supported-languages"></a>Langues prises en charge
<a name="sectionSection0"> </a>

Le complément Junk Email Reporting prend en charge les langues suivantes :

- Chinois simplifié

- Chinois traditionnel

- Néerlandais

- Anglais

- Français

- Allemand

- Italien

- Japonais

- Coréen

- Portugais

- Portugais (Brésil)

- Espagnol

## <a name="install-the-junk-email-reporting-add-in"></a>Installation du complément Junk Email Reporting

Vous pouvez installer le complément de création de rapports de courrier indésirable de deux façons :

- En exécutant le package Windows Installer comme vous le feriez pour tout autre fichier. msi. Lorsque vous installez le complément, une interface GUI s’ouvre et vous invite à parcourir les écrans d’installation. Pour plus d’informations, consultez la rubrique [installer le complément de création de rapports de courrier indésirable à l’aide de l’Assistant Installation](#install-the-junk-email-reporting-add-in-using-the-setup-wizard).

OU

- En exécutant une installation sans assistance, c'est-à-dire sans interface utilisateur d'installation. Au lieu d'utiliser cette dernière, vous spécifiez des options de ligne de commande qui exécutent un script d'installation. Lorsque vous installez le complément, vous disposez d'options de configuration supplémentaires qui sont indisponibles dans l'interface GUI. Pour plus d'informations, consultez la rubrique relative à [Installation du complément de création de rapports de courrier indésirable en mode sans assistance](#install-the-junk-email-reporting-add-in-using-silent-mode).

### <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Voir la **Configuration requise** pour le complément Junk Email Reporting à [https://www.microsoft.com/download/details.aspx?id=18275](https://www.microsoft.com/download/details.aspx?id=18275)l’adresse.

> [!NOTE]
> Vous devez disposer de droits d'administrateur sur l'ordinateur sur lequel vous installez le complément.

### <a name="install-the-junk-email-reporting-add-in-using-the-setup-wizard"></a>Installer le complément de création de rapports de courrier indésirable à l’aide de l’Assistant Installation

1. Sur votre ordinateur, fermez Outlook.

2. Dans la section **Détails** du [complément Microsoft Junk Email Reporting pour Microsoft Outlook](https://www.microsoft.com/download/details.aspx?id=18275), téléchargez le fichier. msi approprié pour votre version d’Office.

3. Double-cliquez sur le fichier .msi.

4. Dans la page **Bienvenue à la configuration du complément Microsoft Junk Email Reporting**, cliquez sur **Suivant**.

5. Lisez le contrat de licence, puis, si vous consentez aux conditions d'installation, cliquez sur **J'accepte les termes du contrat de licence** (obligatoire pour continuer l'installation). Cliquez sur **Suivant** pour continuer.

6. Une fois l'exécution de l'Assistant terminée, cliquez sur **Terminer**.

7. Lancez Outlook.

8. Consultez le bouton **Courrier indésirable** sur votre ruban Outlook. Vous pouvez à présent signaler des messages de courrier indésirable à Microsoft en les sélectionnant dans votre boîte de réception, puis en cliquant sur le bouton permettant de **signaler le courrier indésirable**.

9. Cliquez sur la flèche vers le bas en regard du bouton **Courrier indésirable** pour plus d'options, telles que le **signalement en tant que hameçonnage** si vous souhaitez signaler des messages électroniques d'hameçonnage à Microsoft. Dans votre dossier de courrier indésirable, vous pouvez également sélectionner l'option de **signalement en tant que courrier non indésirable** si un message électronique a été identifié à tort comme courrier indésirable.

### <a name="install-the-junk-email-reporting-add-in-using-silent-mode"></a>Installation du complément de création de rapports de courrier indésirable en mode sans assistance

1. Sur votre ordinateur, fermez Outlook.

2. Ouvrez une invite de commandes.

3. Pour effectuer une installation simple du complément, sans paramètre facultatif, spécifiez ce qui suit :

   - Ordinateurs exécutant x86 Outlook :`msiexec /qn /i JunkReportingAdd-in.x86-en.msi`

   - Ordinateurs exécutant x64 Outlook :  `msiexec /qn /i JunkReportingAdd-in.x64-en.msi`

    Vous pouvez également spécifier les paramètres facultatifs MaxMessageSelection et BccEmailAddress :

   - MaxMessageSelection Permet aux administrateurs de définir le nombre maximal de messages que les utilisateurs peuvent sélectionner pour soumission en un seul clic. La plage s'étend de 1 à 50 messages, et la valeur par défaut est de 10 messages.

     Exemple : Si vous voulez définir le nombre maximal de messages qu'un utilisateur peut sélectionner pour soumission en un seul clic sur 16, utilisez l'option suivante dans la commande d'installation :  `MaxMessageSelection=16`

   - BccEmailAddress Permet aux administrateurs de configurer une boîte aux lettres pour recevoir une copie de toutes les soumissions de leurs utilisateurs en définissant une adresse de messagerie Cci. Après configuration de la boîte aux lettres, une copie des tous les messages électroniques soumis est envoyée à l'adresse BccEmailAddress. Autrement, le paramètre par défaut est « pas d'adresse de messagerie Cci ».

     Exemple : Si vous voulez utiliser junkReports@contoso.com comme adresse de messagerie Cci pour toutes les soumissions, utilisez la commande suivante :  `BccEmailAddress="junkReports@contoso.com"`

     > [!NOTE]
     > Vous pouvez entrer plusieurs adresses de messagerie Cci en les séparant par des points-virgules. Exemple :  `BccEmailAddress="junkReports@contoso.com; hollyd@treyresearch.net"`

     Pour ajouter ces deux paramètres facultatifs en fonction des exemples précédents, exécutez la commande suivante sur un ordinateur exécutant x86 Outlook :

     ```
     msiexec /qn /i JunkReportingAdd-in.x86-en.msi. MaxMessageSelection=16 BccEmailAddress="junkReports@contoso.com; hollyd@treyresearch.net"
     ```

4. Une fois l'installation terminée, lancez Outlook.

5. Consultez le bouton **Courrier indésirable** sur votre ruban Outlook. Vous pouvez à présent signaler des messages de courrier indésirable à Microsoft en les sélectionnant dans votre boîte de réception, puis en cliquant sur le bouton permettant de **signaler le courrier indésirable**.

6. Cliquez sur la flèche vers le bas en regard du bouton **Courrier indésirable** pour plus d'options, telles que le **signalement en tant que hameçonnage** si vous souhaitez signaler des messages électroniques d'hameçonnage à Microsoft. Dans votre dossier de courrier indésirable, vous pouvez également sélectionner l'option de **signalement en tant que courrier non indésirable** si un message électronique a été identifié à tort comme courrier indésirable.

## <a name="uninstall-the-junk-email-reporting-add-in"></a>Désinstallation du complément Junk Email Reporting

Utilisez l’une des options décrites dans la section suivante pour désinstaller le complément de création de rapports de courrier indésirable :

- Supprimez le complément à l’aide du panneau de configuration Windows.

- Exécutez le package Windows Installer, puis sélectionnez l'option de désinstallation.

- Exécutez une installation à l'aide de l'option de désinstallation.

> [!NOTE]
> Vous devez disposer de droits d'administrateur sur l'ordinateur sur lequel vous désinstallez le complément.

### <a name="uninstall-the-junk-email-reporting-add-in-from-control-panel"></a>Désinstallation du complément Junk Email Reporting à partir du Panneau de configuration

1. Sur votre ordinateur, fermez Outlook.

2. Dans le menu Démarrer de votre ordinateur, sélectionnez **Panneau de configuration**.

3. Sélectionnez **Programmes et fonctionnalités**.

4. Sélectionnez **Complément Microsoft Junk E-mail Reporting pour Microsoft Office Outlook**.

5. Sélectionnez **Désinstaller**.

6. Redémarrez Outlook pour vérifier que le complément ne s'affiche plus dans le ruban Outlook.

### <a name="uninstall-the-junk-email-reporting-add-in-by-running-the-windows-installer-package"></a>Désinstallation du complément Junk Email Reporting en exécutant le package Windows Installer

1. Sur votre ordinateur, fermez Outlook.

   > [!NOTE]
   > Si Outlook est en cours d'exécution durant le processus de désinstallation, vous devrez le redémarrer pour achever la désinstallation du complément.

2. Réexécutez le fichier .msi que vous avez précédemment exécuté pour installer le complément.

   (Dans la section **Détails** du [complément Microsoft Junk Email Reporting pour Microsoft Outlook](https://www.microsoft.com/download/details.aspx?id=18275), téléchargez le fichier. msi approprié pour votre version d’Office, puis double-cliquez sur le fichier. msi.)

3. Suivez les invites pour désinstaller le complément.

4. Redémarrez Outlook pour vérifier que le complément ne s'affiche plus dans le ruban Outlook.

### <a name="uninstall-the-junk-email-reporting-add-in-in-silent-mode"></a>Désinstallation du complément Junk Email Reporting en mode sans assistance

1. Sur votre ordinateur, fermez Outlook.

   > [!NOTE]
   > Si Outlook est en cours d'exécution durant le processus de désinstallation, vous devrez le redémarrer pour achever la désinstallation du complément.

2. Ouvrez une invite de commandes.

3. Spécifiez le paramètre de ligne de commande suivant :

   Outlook x86 :`msiexec /x JunkReportingAdd-in.x86-en.msi /qn MSIRESTARTMANAGERCONTROL="DisableShutdown"`

   Outlook x64 :`msiexec /x JunkReportingAdd-in.x64-en.msi /qn MSIRESTARTMANAGERCONTROL="DisableShutdown"`

4. Redémarrez Outlook pour vérifier que le complément ne s'affiche plus dans le ruban Outlook.

## <a name="for-more-information"></a>Pour plus d'informations

[Signaler les messages de courrier indésirable à Microsoft](report-junk-email-messages-to-microsoft.md)

[Résolution des problèmes et informations de support technique](troubleshooting-and-support-information.md)
