---
title: Dépréciation de l’application visionneuse OME
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6336cabb-b06e-402f-9e85-8bb9eb4ce68f
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: L’application de visionneuse Office 365 Message Encryption (OME) a été supprimée des magasins Android et Apple en 2018.
ms.openlocfilehash: 2e1e0ead7d34761a3159b4b51368ea4460acb596
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630078"
---
# <a name="deprecating-message-encryption-viewer-app"></a>Dépréciation de l’application visionneuse de chiffrement des messages

Le 15 août 2018, nous avons supprimé l’application mobile OME (Message Encryption) Office 365 des magasins Android et Apple. L’application mobile Office 365 Message Encryption Viewer était nécessaire pour lire les messages électroniques et les pièces jointes chiffrés avec la version précédente d’OME sur les téléphones Apple et Android. Outre la suppression de l’application Visionneuse OME, nous n’apportons aucune autre modification à la version précédente d’OME.
  
## <a name="changes-from-august-2018"></a>Modifications à partir d’août 2018

Comme annoncé en septembre 2017, nous avons publié une nouvelle version de [Office 365 Chiffrement](https://aka.ms/ome2017) des messages afin que les utilisateurs puissent envoyer des messages chiffrés et protégés à toute personne à l’intérieur ou à l’extérieur de l’organisation sans avoir besoin de l’application mobile. Depuis, nous avons ajouté des fonctionnalités supplémentaires :
  
- [Chiffrer uniquement le modèle](https://aka.ms/encryptonly)

- [Contrôle de déchiffrement des pièces jointes](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Admin-control-for-attachments-now-available-in-Office-365/ba-p/204007)

Avec cette modification, les utilisateurs ne pourront plus télécharger l’application mobile Office 365 Message Encryption Viewer à compter du 1er août. Par conséquent, les destinataires de courrier peuvent ne pas être en mesure de lire les messages chiffrés avec la version précédente d’OME sur certains appareils mobiles Android et Apple. Toutefois, ils pourront toujours lire ces messages sur des ordinateurs personnels (via des navigateurs de bureau). Les utilisateurs qui ont déjà téléchargé l’application continueront de pouvoir l’utiliser.
  
## <a name="why-this-change-was-made"></a>Pourquoi cette modification a-t-elle été apportée ?

La nouvelle version d’OME n’a plus besoin d’une application mobile pour lire les courriers électroniques protégés et les pièces jointes. Les clients qui utilisent Chiffrement de messages Microsoft Purview peuvent afficher le message protégé dans Outlook mobile et les non-clients peuvent afficher les messages protégés dans un navigateur.
  
Obliger les utilisateurs à télécharger une application mobile est un autre obstacle pour les clients à afficher les messages protégés. Chiffrement de messages Microsoft Purview offre une meilleure expérience mobile.
  
## <a name="can-i-still-use-the-previous-version-of-office-365-message-encryption"></a>Puis-je toujours utiliser la version précédente de Office 365 Message Encryption ?

La version précédente de Office 365 Chiffrement des messages ne sera pas dépréciée pour l’instant. Toutefois, nous avons apporté des améliorations significatives à Chiffrement de messages Microsoft Purview, ce qui facilite le chiffrement et les droits de protection des données sensibles pour tout le monde et sur n’importe quel appareil, notamment la possibilité pour les utilisateurs de lire des messages protégés directement dans Outlook (bureau,  mobile et web).
  
## <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour préparer ce changement ?

Si votre organisation envoie actuellement des pièces jointes chiffrées aux destinataires qui nécessitent l’application Visionneuse OME, vous devez mettre à jour votre documentation et vos ressources de formation.
  
Nous vous recommandons de mettre à jour les règles de flux de messagerie Exchange existantes pour utiliser Chiffrement de messages Microsoft Purview afin que votre organisation puisse tirer parti des fonctionnalités nouvelles et améliorées. Une fois que vous avez configuré Chiffrement de messages Microsoft Purview, les destinataires n’ont pas besoin de l’application Visionneuse OME pour lire les messages chiffrés sur les appareils mobiles.
  
Microsoft vous recommande d’effectuer un plan pour passer à Chiffrement de messages Microsoft Purview dès qu’il est raisonnable pour votre organisation. Pour obtenir des instructions, consultez [Configurer Chiffrement de messages Microsoft Purview](set-up-new-message-encryption-capabilities.md). Si vous souhaitez en savoir plus sur le fonctionnement du chiffrement des messages en premier, consultez [Chiffrement](ome.md) des messages.
