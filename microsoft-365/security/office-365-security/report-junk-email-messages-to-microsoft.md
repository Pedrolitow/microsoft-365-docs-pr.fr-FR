---
title: Signaler le courrier indésirable, le non-courrier indésirable, l’hameçonnage, les e-mails suspects et les fichiers à Microsoft
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
ms.openlocfilehash: 3d27b7d3e76454245c7d429fc025237b1c84f690
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68662970"
---
# <a name="how-do-i-report-a-suspicious-email-or-file-to-microsoft"></a>Comment faire signaler un e-mail ou un fichier suspect à Microsoft ?

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Vous vous demandez quoi faire avec des e-mails ou des fichiers suspects ? Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, *les utilisateurs et les* *administrateurs* disposent de différentes façons de signaler un e-mail, une URL ou une pièce jointe suspecte à Microsoft.

En outre, les organisations Microsoft 365 avec des administrateurs Microsoft Defender pour point de terminaison ont également plusieurs méthodes pour créer des rapports sur les fichiers.

Regardez cette vidéo qui montre plus d’informations sur l’expérience des soumissions unifiées.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE50HhM]

## <a name="report-a-suspicious-email-to-microsoft"></a>Signaler un e-mail suspect à Microsoft

|Méthode|Type de soumission|Description|
|---|---|---|
|[Utiliser le portail Soumissions pour envoyer des courriers indésirables, des hameçonnages, des URL et des pièces jointes à Microsoft](admin-submission.md)|Administrateur|Méthode de création de rapports recommandée pour les administrateurs des organisations disposant de boîtes aux lettres Exchange Online (non disponible dans EOP autonome).|
|[Activez les modules complémentaires Report Message ou Report Phishing.](enable-the-report-message-add-in.md)|Utilisateur|Fonctionne avec Outlook et Outlook sur le web (anciennement Outlook Web App). <br/><br/> En fonction de votre abonnement, les messages signalés par les utilisateurs avec les compléments sont disponibles dans [le portail soumissions Administration](admin-submission.md), les [résultats de l’examen et de la réponse automatisés (AIR),](air-view-investigation-results.md) le [rapport messages signalés par l’utilisateur](view-email-security-reports.md#user-reported-messages-report) et [l’Explorateur](threat-explorer-views.md#email--submissions). <br/><br/> Vous pouvez configurer les messages signalés pour qu’ils soient copiés ou redirigés vers une boîte aux lettres que vous spécifiez. Pour plus [d’informations, consultez Stratégies de soumission d’utilisateurs](user-submission.md).
|[Signaler les faux positifs et les faux négatifs dans Outlook](report-false-positives-and-false-negatives.md)|Utilisateur|Envoyez les faux positifs (e-mails fiables bloqués ou déplacés vers le dossier courrier indésirable) et les faux négatifs (courrier indésirable ou hameçonnage remis dans la boîte de réception) à Exchange Online Protection (EOP) à l’aide de la fonctionnalité Signaler un message.|
|[Utiliser des règles de flux de courriers pour afficher les comptes-rendus envoyés par les utilisateurs à Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft)|Administrateur|Découvrez comment créer une règle de flux de courrier (également appelée règle de transport) qui vous avertit lorsque les utilisateurs signalent des messages à Microsoft pour analyse.|
|[Envoyer des fichiers à analyser](../intelligence/submission-guide.md)|Administrateur|Envoyez des pièces jointes et d’autres fichiers suspects à Microsoft à des fins d’analyse.|

> [!NOTE]
> Lorsque vous signalez une entité de messagerie à Microsoft, nous copieons tout ce qui est associé à l’e-mail pour l’inclure dans nos révisions continues d’algorithmes. Cette copie inclut le contenu de l’e-mail, les en-têtes d’e-mail et les données associées sur le routage des e-mails. Toutes les pièces jointes de message sont également incluses.
>
> Microsoft considère vos commentaires comme l’autorisation de votre organisation d’analyser toutes les informations décrites précédemment afin d’affiner les algorithmes d’hygiène des messages. Nous détenons votre message dans nos centres de données audités sécurisés aux États-Unis. La soumission est supprimée au plus tard 30 jours après que vous nous l’avez envoyée. Le personnel Microsoft peut lire vos messages et pièces jointes envoyés, ce qui n’est normalement pas autorisé pour les e-mails dans Microsoft 365. Toutefois, votre courrier électronique est toujours traité comme confidentiel entre vous et Microsoft, et nous ne fournirons pas vos e-mails ou pièces jointes à une autre partie dans le cadre du processus de révision.
