---
title: Obtention d'une erreur « boîte aux lettres introuvable » dans Outlook sur le web
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
ms.custom:
- AdminTemplateSet
- admindeeplinkMAC
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
ms.assetid: 7e453a40-66df-44ab-92a1-96786cb7fb34
description: Une erreur **Boîte aux lettres introuvable pour** signifie que le compte que vous avez utilisé pour vous connecter à Outlook sur le web ne possède pas de licence Exchange Online.
ms.openlocfilehash: a83219dbd22446d210d59b2c8613915129ecc1cb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60167977"
---
# <a name="getting-a-mailbox-not-found-error-in-outlook-on-the-web"></a>Obtention d'une erreur « boîte aux lettres introuvable » dans Outlook sur le web ?

Si vous utilisez Outlook sur le web et que vous obtenez l'erreur **Boîte aux lettres introuvable pour**, le compte que vous avez utilisé pour vous connecter à Outlook sur le web ne possède pas de licence Exchange Online et par conséquent, aucune boîte aux lettres n'est associée au compte. 

## <a name="assign-a-license-to-your-account"></a>Attribuer une licence à votre compte

Votre administrateur peut attribuer une licence à votre compte en suivant les étapes suivantes :

1. Ouvrez le [Centre d’administration Microsoft 365](https://admin.microsoft.com/adminportal/home#/homepage) et accédez à **Utilisateurs actifs** sous la section **Utilisateurs**, puis sélectionnez l’utilisateur qui voit l’erreur.
1. Dans la page utilisateur qui s’ouvre, allez à la section **Licences et applications**, sélectionnez la valeur **Emplacement** appropriée, puis attribuez une licence contenant Exchange Online (développez la licence pour afficher les détails). 
1. Lorsque vous avez terminé, cliquez sur **Enregistrer les modifications**.

## <a name="related-content"></a>Contenu associé

[Ajouter un autre alias de courrier pour un utilisateur](../email/add-another-email-alias-for-a-user.md) (article)\
[Configurer le transfert des e-mails dans Microsoft 365](../email/configure-email-forwarding.md) (article)\
[Créer une boîte aux lettres ](../email/create-a-shared-mailbox.md)partagée (article)