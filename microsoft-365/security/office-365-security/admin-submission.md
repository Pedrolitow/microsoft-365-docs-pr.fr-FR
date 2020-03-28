---
title: Soumissions d’administration dans Office 365, O365 envois, Office 365 courrier indésirable, O365 false negative, Submit phishing in Office 365, Submit e-mail for Scanning, suspect email in Office 365, Scan a mail, Microsoft Scan for hameçon, demandez à Microsoft d’analyser les courriers indésirables, envoyer courrier électronique, envoi de messages électroniques, courrier électronique Dodgy, courrier indésirable, suspect, non approuvé, signalement des courriers indésirables à Microsoft, signalez les courriers de hameçonnage à Microsoft, signalez les courriers électroniques malveillants à Microsoft, signalez les courriers électroniques frauduleux à Microsoft, signalez les courriers indésirables à Microsoft courrier électronique dans la boîte de réception Office 365, virus dans la messagerie Office 365
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
description: Découvrez comment envoyer des e-mails suspects, des courriers électroniques de hameçonnage suspects, du courrier indésirable et d’autres messages, URL et fichiers potentiellement dangereux de votre client Office 365 à Microsoft pour analyse.
ms.openlocfilehash: 539d09f03a8a9c5956f2d1e3584f893b0e4ffbb4
ms.sourcegitcommit: d00efe6010185559e742304b55fa2d07127268fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2020
ms.locfileid: "43033613"
---
# <a name="use-admin-submission-to-submit-suspected-spam-phish-urls-and-files-to-microsoft"></a>Utiliser la soumission de l’administrateur pour soumettre des courriers indésirables, des hameçons, des URL et des fichiers à Microsoft

Si vous êtes administrateur dans une organisation Office 365 avec des boîtes aux lettres dans Exchange Online, vous pouvez utiliser le portail d’envoi du centre de sécurité & de la sécurité Office 365 pour soumettre des messages électroniques, des URL et des pièces jointes à Microsoft pour analyse.

Lorsque vous soumettez un message électronique, vous obtenez des informations sur les stratégies susceptibles d’avoir autorisé le courrier entrant dans votre client, ainsi que sur l’examen de toutes les URL et pièces jointes du courrier. Les stratégies pouvant avoir autorisé un courrier incluent la liste des expéditeurs approuvés d’un utilisateur individuel, ainsi que des stratégies au niveau du client, telles que les règles de flux de messagerie Exchange (également appelées règles de transport).

Pour d’autres façons d’envoyer des messages électroniques, des URL et des pièces jointes à Microsoft, consultez la rubrique 

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de sécurité et conformité sur <https://protection.office.com/>. Pour accéder directement à la page d' **envoi** , <https://protection.office.com/reportsubmission>utilisez.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection autonome, voir [Se connecter à PowerShell d’Exchange Online Protection](https://docs.microsoft.com/powershell/exchange/exchange-eop/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces procédures. Pour ajouter, modifier et supprimer des stratégies de blocage du courrier indésirable, vous devez être membre des groupes de rôles gestion de l' **organisation**, administrateur de la **sécurité**ou **lecteur de sécurité** . Pour plus d’informations sur les groupes de rôles dans le Centre de sécurité et conformité, voir [Autorisations dans le Centre de sécurité et conformité Office 365](permissions-in-the-security-and-compliance-center.md).

- Pour plus d’informations sur la façon dont les utilisateurs peuvent envoyer des messages et des fichiers à Microsoft, consultez la rubrique [signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="how-to-direct-suspicious-content-to-microsoft-for-office-365-scanning"></a>Comment faire pour diriger du contenu suspect vers Microsoft pour Office 365, analyse

Pour envoyer du contenu à Microsoft, cliquez sur le bouton **nouvelle soumission** dans la partie supérieure gauche de la page soumissions. Un menu volant sur le côté droit de la page apparaît avec la possibilité d’envoyer un message électronique, une URL ou un fichier.

### <a name="submit-a-questionable-email-to-microsoft"></a>Envoyer un courrier électronique en question à Microsoft

![Exemple de dépôt de courrier électronique](../../media/submission-flyout-email.PNG)

1. Pour envoyer un message électronique, sélectionnez **courrier électronique** et spécifiez l' **ID de message réseau** de messagerie ou téléchargez le fichier de courrier électronique.

2. Spécifiez le ou les destinataires sur lesquels vous souhaitez exécuter la vérification de stratégie. La vérification de stratégie détermine si l’analyse du courrier électronique a contourné les messages en raison des stratégies de niveau utilisateur ou client.

3. Indiquez si l’e-mail doit avoir été bloqué ou non. Si la messagerie doit avoir été bloquée, indiquez si elle doit être bloquée en tant que courrier indésirable, hameçonnage ou programme malveillant. Si vous n’êtes pas sûr de son type, utilisez votre meilleure appréciation.

   - Si le filtre a été contourné en raison de stratégies lors de l’envoi, vous verrez des informations sur cette stratégie.

   - Si le filtre n’a pas été contourné en raison d’une ou de plusieurs stratégies, l’analyse se terminera en quelques minutes. Vous verrez des informations supplémentaires sur l’envoi en cliquant sur le lien État. Cela inclut les résultats de la vérification de stratégie et le verdict de nouvelle analyse. Remarque cela n’exécute pas de nouveau le courrier électronique via la pile de filtrage complet DAV d’Office 365 mais exécute une nouvelle analyse partielle en fonction de certains attributs de l’e-mail, de l’URL ou du fichier.

4. Cliquez sur le bouton **Envoyer** .

### <a name="send-a-suspect-url-to-microsoft"></a>Envoyer une URL suspecte à Microsoft

![Exemple de dépôt de courrier électronique](../../media/submission-url-flyout.png)

1. Pour soumettre une URL, sélectionnez **URL** dans le menu volant. Tapez l’URL complète, y compris le protocole (**https://**).

   Si vous avez sélectionné **doit avoir été filtré**, spécifiez si l’URL est un hameçonnage ou un programme malveillant.

2. Cliquez sur le bouton **Envoyer** .

### <a name="submit-a-suspected-file-to-microsoft"></a>Envoyer un fichier suspect à Microsoft

![Exemple de dépôt de courrier électronique](../../media/submission-file-flyout.PNG)

1. Pour soumettre un fichier, sélectionnez **fichier** dans le menu volant et téléchargez le fichier que vous souhaitez analyser.

2. Cliquez sur le bouton **Envoyer** .
