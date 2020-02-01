---
title: Gérer les listes d'expéditeurs autorisés pour les vers de publipostage en bloc
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/17/2014
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: d48db4a3-9fbe-45e2-bbaa-1017ffdf96f8
ms.collection:
- M365-security-compliance
description: "Si vous souhaitez utiliser les listes d'expéditeurs autorisés, vous devez savoir qu'Exchange Online Protection (EOP) et Outlook gèrent différemment le traitement. Le service respecte les expéditeurs et les domaines autorisés en inspectant l'adresse RFC 5321.MailFrom, tandis qu'Outlook ajoute l'adresse RFC 5322.From à la liste des expéditeurs autorisés d'un utilisateur. (Remarque : Le service inspecte les adresses 5321.MailFrom et 5322.MailFrom pour les expéditeurs et les domaines bloqués.)"
ms.openlocfilehash: aaede7cab2e640603c20804f4015e19f61b6c2f3
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41598941"
---
# <a name="manage-safe-sender-lists-for-bulk-mailers"></a>Gérer les listes d’expéditeurs autorisés pour les vers de publipostage en bloc

Si vous souhaitez utiliser les listes d'expéditeurs autorisés, vous devez savoir qu'Exchange Online Protection (EOP) et Outlook gèrent différemment le traitement. Le service Office 365 respecte les expéditeurs et les domaines approuvés en inspectant l' `RFC 5321.MailFrom` adresse `RFC 5322.From` et l’adresse, tandis `RFC 5322.From` qu’Outlook ajoute l’adresse à la liste des expéditeurs approuvés d’un utilisateur. (Remarque : le service inspecte l’adresse `5321.MailFrom` et `5322.From` l’adresse pour les expéditeurs et les domaines bloqués.)

L' `SMTP MAIL FROM` adresse, appelée `RFC 5321.MailFrom address`,, est l’adresse de messagerie utilisée pour effectuer des vérifications SPF, et si le courrier ne peut pas être remis, le chemin d’accès vers lequel le message retourné est remis. Il s’agit de cette adresse de messagerie qui est `Return-Path` placée dans le dans les en-têtes de message par défaut, bien qu’il soit possible pour l' `Return-Path` expéditeur de désigner une autre adresse.

L' `From:` adresse dans les en-têtes de message, également appelée `RFC 5322.From` adresse, est l’adresse de messagerie qui est affichée dans le client de messagerie, tel qu’Outlook.

La plupart du temps, les `5321.MailFrom` adresses `5322.From` et sont identiques. C'est généralement le cas pour la communication entre deux-personnes. Toutefois, lorsqu'un courrier électronique est envoyé à la place d'une autre personne, les adresses sont souvent différentes. Cela se produit généralement avec les messages de courrier indésirable.

Par exemple, supposons que Blue Yonder Airlines a embauché Margie’s Travel pour envoyer sa publicité par courrier électronique. Vous obtenez alors un message dans votre boîte de réception provenant de l'expéditeur blueyonder@news.blueyonderairlines.com. Dans cet exemple :

- L' `5321.MailFrom` adresse est blueyonder.Airlines@margiestravel.com.

- L' `5322.From` adresse est blueyonder@news.blueyonderairlines.com, ce que vous verrez dans Outlook.

Pour empêcher le filtrage de ce message, vous pouvez :

- **En tant qu’utilisateur**: ajouter `RFC 5322.From` l’adresse en tant qu’expéditeur approuvé dans Outlook.

- **En tant qu’administrateur**: configurez une [règle de flux de messagerie](anti-spam-protection.md#beyond-the-basics-more-ways-to-prevent-spam-in-office-365) (également appelée règle de transport).
