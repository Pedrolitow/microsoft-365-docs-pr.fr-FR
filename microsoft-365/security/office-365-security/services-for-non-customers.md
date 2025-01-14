---
title: Services pour les non-clients qui envoient des messages à Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 19fd3e0f-8dbf-4049-a810-2c8ee6cefd48
ms.collection:
- m365-security
description: Pour préserver la confiance des utilisateurs dans l'utilisation de la messagerie électronique, Microsoft a mis en place diverses stratégies et technologies pour aider à protéger ses utilisateurs.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 428e1c0096811fa13674a47fec2cdf777642e12f
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68088462"
---
# <a name="services-for-non-customers-sending-mail-to-microsoft-365"></a>Services pour les non-clients qui envoient des messages à Microsoft 365

L'utilisation abusive de la messagerie électronique, les courriers indésirables et les e-mails frauduleux (hameçonnage) continuent à peser sur l'ensemble de l'écosystème de la messagerie. Pour aider à maintenir la confiance des utilisateurs dans l’utilisation de la messagerie électronique, Microsoft a mis en place différentes stratégies et technologies pour protéger nos utilisateurs. Cependant, Microsoft comprend que les e-mails légitimes ne doivent pas être affectés négativement. Par conséquent, nous avons créé une suite de services pour aider les expéditeurs à améliorer leur capacité à envoyer des e-mails aux utilisateurs de Microsoft 365 en gérant de manière proactive leur réputation d’envoi.

Cette vue d’ensemble fournit des informations sur les avantages que nous offrons à votre organisation, même si vous n’êtes pas un client.

## <a name="sender-solutions"></a>Solutions de l'expéditeur

|Service|Avantages|
|---|---|
|Ce contenu d'aide en ligne|Fournit : <ul><li>Point de départ pour toute question relative à la remise de communications aux utilisateurs EOP.</li><li>Inclut un guide en ligne simple avec nos stratégies et exigences.</li><li>Vue d’ensemble des filtres de courrier indésirable et des technologies d’authentification utilisées par Microsoft.</li><ul>|
|[Support technique Microsoft](#microsoft-support)|Offre un support autonome et de transmission à une instance supérieure pour les problèmes de remise.|
|[Portail de suppression d’adresses IP anti-courrier indésirable](#anti-spam-ip-delist-portal)|A tool to submit IP delist request. Before submitting this request it is the sender's responsibility to ensure that any further mail originating from the IP in question is not abusive or malicious.|
|[Création de rapport de courrier indésirable et de mauvaise utilisation pour le courrier indésirable provenant d'Exchange Online](#abuse-and-spam-reporting-for-junk-email-originating-from-exchange-online)|Empêche l’envoi de courrier indésirable et de courrier indésirable à partir de Exchange Online et encombre l’Internet et votre système de messagerie.|

## <a name="microsoft-support"></a>Support technique Microsoft

Microsoft offre plusieurs options de support pour les personnes ayant des problèmes d’envoi de courrier aux destinataires Microsoft 365. Nous vous recommandons d’effectuer les actions suivantes :

- Suivez les instructions fournies dans les rapports de non-remise que vous recevez.

- Consultez les problèmes les plus courants que rencontrent les non clients dans [Résolution des problèmes de messages envoyés à Office 365](troubleshooting-mail-sent-to-office-365.md).

- Utilisez le [portail Delist Microsoft 365](https://sender.office.com) pour envoyer une demande de suppression de votre adresse IP de la liste de l’expéditeur bloqué.

- Lisez les [forums de la communauté Microsoft](https://community.office365.com/f/).

- Contactez le client que vous essayez d’envoyer par e-mail à l’aide d’une autre méthode et demandez-lui de contacter Support Microsoft et d’ouvrir un ticket de support en votre nom. Dans certains cas, pour des raisons juridiques, le support Microsoft doit communiquer directement avec l'expéditeur qui possède l'espace IP qui est bloqué. Toutefois, les personnes qui ne sont pas des clients ne peuvent généralement pas demander de tickets d'assistance.

  Pour plus d'informations sur le support technique de Microsoft pour Office 365, voir [Prise en charge](/office365/servicedescriptions/office-365-platform-service-description/support).

## <a name="anti-spam-ip-delist-portal"></a>Portail de suppression d’adresses IP anti-courrier indésirable

Il s’agit d’un portail libre-service que vous pouvez utiliser pour vous supprimer de la liste des expéditeurs bloqués microsoft 365. Utilisez ce portail si vous recevez un message d’erreur lorsque vous essayez d’envoyer un e-mail à un destinataire dont l’adresse e-mail se trouve dans Microsoft 365 et que vous ne le pensez pas. Pour plus d'informations, voir [Utilisation du portail Supprimer de la liste pour vous supprimer de la liste des expéditeurs bloqués](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md).

## <a name="abuse-and-spam-reporting-for-junk-email-originating-from-exchange-online"></a>Création de rapport de courrier indésirable et de mauvaise utilisation pour le courrier indésirable provenant d'Exchange Online

Parfois, Microsoft 365 est utilisé par des tiers pour envoyer des courriers indésirables, en violation de nos conditions d’utilisation et de notre stratégie. Si vous recevez un courrier indésirable de Office 365, vous pouvez signaler ces messages à Microsoft. Pour obtenir des instructions, consultez [Les messages de rapport et les fichiers envoyés à Microsoft](report-junk-email-messages-to-microsoft.md).
