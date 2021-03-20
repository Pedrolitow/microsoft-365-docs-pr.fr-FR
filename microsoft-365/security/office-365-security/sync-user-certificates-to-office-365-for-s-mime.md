---
title: Synchronisation des certificats utilisateur vers Office 365 pour S/MIME
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 12/09/2016
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 351c932e-99c1-4512-a6e8-788e90b7838f
ms.custom:
- seo-marvel-apr2020
description: Dans cet article, vous allez apprendre à publier les certificats appropriés dans Office 365 avant d’envoyer des messages protégés par S/MIME dans Exchange Online.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 387f9f405afd45254c6568aa92334a7ee5b4171f
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50916453"
---
# <a name="sync-user-certificates-to-office-365-for-smime"></a>Synchronisation des certificats utilisateur vers Office 365 pour S/MIME

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Pour qu’une personne puisse envoyer des messages protégés par S/MIME dans Exchange Online, les certificats appropriés doivent être mis en place. Pour envoyer des messages chiffrés via Exchange Online, l’application de messagerie de l’expéditeur utilise le certificat public du destinataire pour chiffrer le message. Ce certificat X.509 public doit être publié sur Office 365.

## <a name="to-sync-certificates-that-support-smime"></a>Synchronisation de certificats prenant en charge S/MIME

Commencez la configuration de S/MIME en émettant des certificats et en les publiant dans votre service de domaine Active Directory local. Pour plus d'informations, reportez-vous à la rubrique [Vue d'ensemble des services de certificats Active Directory](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831740(v=ws.11)).

Une fois vos certificats publiés, utilisez l’outil Azure AD Connect pour synchroniser les données utilisateur de votre environnement Exchange local avec Office 365. Pour plus d’informations sur ce processus, voir synchronisation Azure AD Connect : [Comprendre et personnaliser la synchronisation.](/azure/active-directory/hybrid/how-to-connect-sync-whatis)

En plus de synchroniser d’autres données d’annuaire, à des fins S/MIME, l’outil synchronise les attributs  **userCertificate** et **userSMIMECertificate** pour chaque objet utilisateur afin que les données soient utilisées pour signer et chiffrer des messages.

## <a name="more-information"></a>Informations supplémentaires

[S/MIME pour la signature et le chiffrement des messages](s-mime-for-message-signing-and-encryption.md)

[Qu’est-ce qu’Azure AD Connect ?](/azure/active-directory/hybrid/whatis-azure-ad-connect)