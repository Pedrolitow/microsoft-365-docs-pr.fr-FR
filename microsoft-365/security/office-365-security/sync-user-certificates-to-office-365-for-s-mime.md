---
title: Synchronisation des certificats utilisateur vers Office 365 pour S/MIME
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 12/09/2016
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 351c932e-99c1-4512-a6e8-788e90b7838f
description: Pour qu'une personne puisse envoyer des messages protégés par S/MIME, les certificats appropriés doivent être configurés. Pour envoyer des messages chiffrés par Exchange Online, le programme de messagerie de l'expéditeur utilise le certificat public du destinataire pour chiffrer le message. Ce certificat X.509 public doit être publié sur Office 365.
ms.openlocfilehash: e03d7be2a7a1fcb8c5ef56395b4046442802cf2a
ms.sourcegitcommit: 2468bcb01625f97a322459814d81b9faad717859
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "39872020"
---
# <a name="sync-user-certificates-to-office-365-for-smime"></a>Synchronisation des certificats utilisateur vers Office 365 pour S/MIME

Pour qu’une personne puisse envoyer des messages protégés par S/MIME dans Exchange Online, les certificats appropriés doivent être configurés. Pour envoyer des messages chiffrés via Exchange Online, l’application de messagerie de l’expéditeur utilise le certificat public du destinataire pour chiffrer le message. Ce certificat X.509 public doit être publié sur Office 365.

## <a name="to-sync-certificates-that-support-smime"></a>Synchronisation de certificats prenant en charge S/MIME

Commencez la configuration de S/MIME en émettant des certificats et en les publiant dans votre service de domaine Active Directory local. Pour plus d'informations, reportez-vous à la rubrique [Vue d'ensemble des services de certificats Active Directory](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831740(v=ws.11)).

Une fois vos certificats publiés, utilisez l'Outil de synchronisation Windows Azure Active Directory pour synchroniser les données utilisateur depuis votre environnement Exchange local sur Office 365. Pour plus d'informations sur ce processus, consultez la rubrique [DirSync : Historique des versions de l'outil de synchronisation d'annuaires](https://go.microsoft.com/fwlink/p/?LinkId=392587).

En plus de synchroniser d’autres données d’annuaire, pour des raisons de S/MIME, l’outil synchronisera les attributs **userCertificate** et **userSMIMECertificate** pour chaque objet utilisateur afin que les données puissent être utilisées pour signer et chiffrer les messages.

## <a name="more-information"></a>Plus d’informations

[S/MIME pour la signature et le chiffrement des messages](s-mime-for-message-signing-and-encryption.md)

[Outil de synchronisation Windows Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=392587).
