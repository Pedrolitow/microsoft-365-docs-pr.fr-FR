---
title: Synchronisation des certificats utilisateur vers Office 365 pour S/MIME
f1.keywords:
- NOCSH
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
ms.openlocfilehash: a62af3b176f29ec2bd8c97ae02178c87b7a63544
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41598191"
---
# <a name="sync-user-certificates-to-office-365-for-smime"></a>Synchronisation des certificats utilisateur vers Office 365 pour S/MIME

Pour qu’une personne puisse envoyer des messages protégés par S/MIME dans Exchange Online, les certificats appropriés doivent être configurés. Pour envoyer des messages chiffrés via Exchange Online, l’application de messagerie de l’expéditeur utilise le certificat public du destinataire pour chiffrer le message. Ce certificat X.509 public doit être publié sur Office 365.

## <a name="to-sync-certificates-that-support-smime"></a>Synchronisation de certificats prenant en charge S/MIME

Commencez la configuration de S/MIME en émettant des certificats et en les publiant dans votre service de domaine Active Directory local. Pour plus d'informations, reportez-vous à la rubrique [Vue d'ensemble des services de certificats Active Directory](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831740(v=ws.11)).

Une fois vos certificats publiés, utilisez l’outil Azure AD Connect pour synchroniser les données utilisateur de votre environnement Exchange local avec Office 365. Pour plus d’informations sur ce processus, reportez-vous à la rubrique session de [synchronisation Azure ad Connect : comprendre et personnaliser la synchronisation](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sync-whatis).

En plus de synchroniser d’autres données d’annuaire, pour des raisons de S/MIME, l’outil synchronisera les attributs **userCertificate** et **userSMIMECertificate** pour chaque objet utilisateur afin que les données puissent être utilisées pour signer et chiffrer les messages.

## <a name="more-information"></a>Plus d’informations

[S/MIME pour la signature et le chiffrement des messages](s-mime-for-message-signing-and-encryption.md)

[Qu’est-ce que Azure AD Connect ?](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-azure-ad-connect)
