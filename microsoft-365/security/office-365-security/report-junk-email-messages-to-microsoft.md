---
title: Signaler les courriers indésirables, les courriers indésirables, le hameçonnage, les e-mails suspects et les fichiers à Microsoft
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: c31406ea-2979-4fac-9288-f835269b9d2f
ms.collection:
- m365-security
description: Comment faire signaler un e-mail ou un fichier suspect à Microsoft ? Signaler des messages, des URL, des pièces jointes et des fichiers à Microsoft à des fins d’analyse. Apprenez à signaler les courriers indésirables et les e-mails de hameçonnage.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: fddca0ff2c68f369910ebd048ed696c7cc7444bf
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68090506"
---
# <a name="how-do-i-report-a-suspicious-email-or-file-to-microsoft"></a>Comment faire signaler un e-mail ou un fichier suspect à Microsoft ?

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Vous vous demandez ce qu’il faut faire avec des e-mails ou des fichiers suspects ? Dans les organisations Microsoft 365 avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, *les utilisateurs* et *les administrateurs ont différentes* façons de signaler un message électronique suspect, une URL ou une pièce jointe à Microsoft.

En outre, les organisations Microsoft 365 avec des administrateurs Microsoft Defender pour point de terminaison disposent également de plusieurs méthodes de création de rapports de fichiers.

Regardez cette vidéo qui montre plus d’informations sur l’expérience des soumissions unifiées.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE50HhM]

## <a name="report-a-suspicious-email-to-microsoft"></a>Signaler un e-mail suspect à Microsoft

|Méthode|Type d’envoi|Description|
|---|---|---|
|[Utilisez le portail Soumissions pour envoyer à Microsoft des courriers indésirables, des hameçonnages, des URL et des pièces jointes suspectes](admin-submission.md)|Administrateur|Méthode de création de rapports recommandée pour les administrateurs des organisations avec des boîtes aux lettres Exchange Online (non disponibles dans EOP autonome).|
|[Activez les modules complémentaires Report Message ou Report Phishing.](enable-the-report-message-add-in.md)|Utilisateur|Fonctionne avec Outlook et Outlook sur le web (anciennement Outlook Web App). <br/><br/> Selon votre abonnement, les messages signalés par les utilisateurs avec les compléments sont disponibles dans [le portail Administration Soumissions](admin-submission.md), les [résultats air (Automated investigation and response),](air-view-investigation-results.md) le [rapport des messages signalés par l’utilisateur](view-email-security-reports.md#user-reported-messages-report) et [l’Explorateur](threat-explorer-views.md#email--submissions). <br/><br/> Vous pouvez configurer les messages signalés à copier ou rediriger vers une boîte aux lettres que vous spécifiez. Pour plus d’informations, consultez [les stratégies d’envoi des utilisateurs](user-submission.md).
|[Signaler les faux positifs et les faux négatifs dans Outlook](report-false-positives-and-false-negatives.md)|Utilisateur|Envoyez les faux positifs (e-mails fiables bloqués ou déplacés vers le dossier courrier indésirable) et les faux négatifs (courrier indésirable ou hameçonnage remis dans la boîte de réception) à Exchange Online Protection (EOP) à l’aide de la fonctionnalité Signaler un message.|
|[Utiliser des règles de flux de courriers pour afficher les comptes-rendus envoyés par les utilisateurs à Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft)|Administrateur|Découvrez comment créer une règle de flux de courrier (également appelée règle de transport) qui vous avertit lorsque les utilisateurs signalent des messages à Microsoft à des fins d’analyse.|
|[Envoyer des fichiers à analyser](../intelligence/submission-guide.md)|Administrateur|Envoyez des pièces jointes et d’autres fichiers suspects à Microsoft à des fins d’analyse.|

> [!NOTE]
> Lorsque vous signalez une entité de messagerie à Microsoft, une copie est effectuée de tout ce qui est associé à l’e-mail pour l’inclure dans les révisions. Cette copie inclut le contenu de l’e-mail, les en-têtes d’e-mail et les données associées sur le routage de l’e-mail. Les pièces jointes du message sont également incluses.
>
> Microsoft considère vos commentaires comme l’autorisation de votre organisation d’analyser toutes les informations et d’améliorer le processus de création de rapports et de révision de messages suspects. Votre message est stocké en toute sécurité jusqu’à ce qu’il soit supprimé au plus tard 30 jours après avoir été fourni. Microsoft peut lire vos messages et pièces jointes envoyés. Toutefois, votre e-mail est toujours traité comme confidentiel entre vous et Microsoft. Votre soumission n’est fournie à aucune autre partie pour le processus de révision.
