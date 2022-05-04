---
title: Signaler des messages de courrier indésirable, de courrier indésirable et de hameçonnage à Microsoft
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
- M365-security-compliance
description: Les administrateurs peuvent découvrir les différentes façons de signaler les messages et fichiers corrects et incorrects à Microsoft à des fins d’analyse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 56ef5cd5a376f4d10af1ad8c592dad02dbc8ef0a
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2022
ms.locfileid: "65188435"
---
# <a name="report-messages-and-files-to-microsoft"></a>Signaler les messages et fichiers à Microsoft Corporation

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, les utilisateurs et les administrateurs ont plusieurs méthodes différentes pour signaler des messages électroniques et des fichiers à Microsoft.

|Méthode|Description|
|---|---|
|[Utilisez le portail Soumissions pour envoyer des courriers indésirables, des hameçonnages, des URL et des fichiers suspects à Microsoft](admin-submission.md)|Méthode de création de rapports recommandée pour les administrateurs des organisations avec des boîtes aux lettres Exchange Online (non disponibles dans EOP autonome).|
|[Activez les modules complémentaires Report Message ou Report Phishing.](enable-the-report-message-add-in.md)|Fonctionne avec Outlook et Outlook sur le web (anciennement Outlook Web App). <br/><br/> Selon votre abonnement, les messages signalés par les utilisateurs avec les compléments sont disponibles dans [le portail Soumissions d’administrateurs](admin-submission.md), les [résultats air (Automated investigation and response),](air-view-investigation-results.md) le [rapport des messages signalés par l’utilisateur](view-email-security-reports.md#user-reported-messages-report) et [l’Explorateur](threat-explorer-views.md#email--submissions). <br/><br/> Vous pouvez configurer les messages signalés à copier ou rediriger vers une boîte aux lettres que vous spécifiez. Pour plus d’informations, consultez [les stratégies d’envoi des utilisateurs](user-submission.md).
|[Signaler les faux positifs et les faux négatifs dans Outlook](report-false-positives-and-false-negatives.md)|Envoyez les faux positifs (e-mails fiables bloqués ou déplacés vers le dossier courrier indésirable) et les faux négatifs (courrier indésirable ou hameçonnage remis dans la boîte de réception) à Exchange Online Protection (EOP) à l’aide de la fonctionnalité Signaler un message.|
|[Utiliser des règles de flux de courriers pour afficher les comptes-rendus envoyés par les utilisateurs à Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft)|Découvrez comment créer une règle de flux de courrier (également appelée règle de transport) qui vous avertit lorsque les utilisateurs signalent des messages à Microsoft à des fins d’analyse.|
|[Soumettre des programmes malveillants et non malveillants à Microsoft pour analyse](submitting-malware-and-non-malware-to-microsoft-for-analysis.md)|Utilisez le site Veille de sécurité Microsoft pour envoyer des pièces jointes et d’autres fichiers.|

> [!NOTE]
> Lorsque vous signalez une entité de messagerie à Microsoft, nous faisons une copie de tout ce qui est associé à l’e-mail pour l’inclure dans nos révisions d’algorithmes continues. Cette copie inclut le contenu de l’e-mail, les en-têtes d’e-mail et les données associées sur le routage de l’e-mail. Les pièces jointes du message sont également incluses.
>
> Microsoft considère vos commentaires comme l’autorisation de votre organisation pour nous d’analyser toutes les informations décrites précédemment et de travailler à affiner les algorithmes d’hygiène des messages. Nous tenons votre message dans nos centres de données audités sécurisés aux États-Unis jusqu’à ce que nous supprimions votre soumission au plus tard 30 jours après que vous nous l’avez fourni. Le personnel de Microsoft peut lire vos messages et pièces jointes envoyés, ce qui n’est normalement pas autorisé pour les e-mails dans Office 365. Toutefois, votre e-mail est toujours traité comme confidentiel entre vous et Microsoft, et nous ne fournirons votre soumission à aucune autre partie pour lire l’e-mail ou ses pièces jointes pour ce processus de révision.
