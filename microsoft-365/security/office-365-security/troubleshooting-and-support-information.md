---
title: Dépannage et informations relatives au support
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
ms.assetid: 5d9f75f5-bb7f-458c-ad30-5c8eae0b0e4e
ms.collection:
- M365-security-compliance
description: Cette rubrique décrit les étapes de résolution des problèmes pour les utilisateurs finaux et les administrateurs, et fournit des informations sur la manière de contacter le support technique pour obtenir de l'aide.
ms.openlocfilehash: c87744608930603f70e6be1132a0b405e9646b57
ms.sourcegitcommit: cbf117a4cd92a907115c9f10752f3c557361e586
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2019
ms.locfileid: "37441191"
---
# <a name="troubleshooting-and-support-information"></a>Dépannage et informations relatives au support

Cette rubrique décrit les étapes de résolution des problèmes pour les utilisateurs finaux et les administrateurs, et fournit des informations sur la manière de contacter le support technique pour obtenir de l'aide.

## <a name="troubleshooting-for-users"></a>Résolution des problèmes pour les utilisateurs

Parfois, vous pouvez rencontrer des problèmes avec Microsoft Outlook après avoir ajouté le complément de création de rapports de courrier indésirable. Voici certains problèmes que vous pouvez rencontrer ainsi que des conseils pour les résoudre.

- Rien ne se passe quand vous cliquez sur **Signaler le courrier indésirable**.

- Outlook cesse de répondre après avoir sélectionné un message électronique

- Le courrier indésirable signalé ne peut pas être remis en raison d'une réponse « Non remis ».

Pour résoudre ce problème, procédez comme suit :

1. Fermez et redémarrez Outlook.

2. Vérifiez que vous êtes en mesure de créer et d'envoyer un message de test. Pour ce faire, vous pouvez envoyer un message de test à un autre compte de messagerie que vous gérez, puis vérifiez que ce message électronique vous est remis.

Si le problème persiste, contactez votre administrateur.

> [!TIP]
> Vous pouvez également envoyer directement des messages de courrier indésirable à Microsoft, à l'adresse électronique [junk@office365.microsoft.com](mailto:junk@office365.microsoft.com), et des messages faux positifs à l'adresse électronique [not_junk@office365.microsoft.com](mailto: not_junk@office365.microsoft.com). Pour plus d'informations, consultez la rubrique [Soumission des messages indésirables, légitimes ou des tentatives de hameçonnage à Microsoft pour analyse](submit-spam-non-spam-and-phishing-scam-messages-to-microsoft-for-analysis.md).

## <a name="troubleshooting-for-administrators"></a>Résolution des problèmes pour les administrateurs

En tant qu’administrateur, vous pouvez être confronté à des problèmes avec les utilisateurs qui utilisent le complément de création de rapports de courrier indésirable pour Outlook. Voici quelques conseils pour résoudre les problèmes que vous pourriez rencontrer.

### <a name="problem-an-error-message-asking-users-to-contact-their-system-administrator-continually-appears"></a>Problème : un message d’erreur demandant aux utilisateurs de contacter leur administrateur système apparaît continuellement.

1. Définissez la valeur de la clé de Registre suivante sur « Verbose » :

   - **32 bit Outlook installé sur un système d’exploitation 32 bits**:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Junk Email Reporting\Addins\LoggingLevel`

   - **32 bit Outlook installé sur un système d’exploitation 64 bits**:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Junk Email Reporting\Addins\LoggingLevel`

   - **64 bits Outlook (toujours installé sur un système d’exploitation 64 bits)**:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Junk Email Reporting\Addins\LoggingLevel`

2. Redémarrez Outlook et demandez aux utilisateurs de revenir en arrière lorsqu’ils voient le message d’erreur.

3. Collectez les informations de journal se trouvant à l'emplacement suivant :

   `%LOCALAPPDATA%\Microsoft\Junk Email Reporting Add-in\SpamReporterAddinLog.txt`

4. Contactez les techniciens du support Exchange Online Protection et fournissez-leur les informations du journal.

### <a name="problem-users-choose-not-to-receive-a-confirmation-when-they-submit-an-email-as-junk-and-now-they-want-the-option-back"></a>Problème : les utilisateurs choisissent de ne pas recevoir de confirmation lorsqu’ils envoient un message électronique comme courrier indésirable et qu’ils souhaitent réactiver cette option.

1. Définissez la valeur de clé de Registre suivante sur « true `HKEY_CURRENT_USER\Software\Microsoft\Junk E-mail Reporting\Preferences\ConfirmReportJunk`» :.

2. Redémarrez Outlook.

## <a name="support-information"></a>Informations concernant le support

Si vous avez besoin d’aide pour l’installation, la configuration ou la désinstallation du complément, veuillez contacter le support technique à l’aide du lien nouvelle demande de service sur la page support dans le centre d’administration 365 de Microsoft. Pour obtenir des options supplémentaires, notamment la soumission d’une demande de service via les options de téléphone et d’auto-assistance, consultez [l’aide et le support pour EOP](help-and-support-for-eop.md).

## <a name="for-more-information"></a>Pour plus d’informations

[Activer le complément Signaler le message](https://support.office.com/article/4250c4bc-6102-420b-9e0a-a95064837676)

[Signaler les messages de courrier indésirable à Microsoft](report-junk-email-messages-to-microsoft.md)
