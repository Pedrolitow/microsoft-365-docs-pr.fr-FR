---
title: Résoudre les problèmes liés aux boîtes aux lettres partagées
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
description: Vous pouvez obtenir des erreurs lorsque vous définissez des boîtes aux lettres partagées. Essayez ces solutions si vous avez des problèmes avec les boîtes aux lettres partagées.
ms.openlocfilehash: 2ec294f4dfe1d15bc4acf2789a35285d1dca78881f30512f08d39fd0a02394e3
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53825930"
---
# <a name="resolve-issues-with-shared-mailboxes"></a>Résoudre les problèmes liés aux boîtes aux lettres partagées

Si vous voyez des messages d’erreur lors de la création ou de l’utilisation d’une boîte aux lettres partagée, essayez ces solutions possibles. 

## <a name="error-when-creating-shared-mailboxes"></a>Erreur lors de la création de boîtes aux lettres partagées
<a name="bkmk_Fix"> </a>

Si vous voyez le message d’erreur, l’adresse proxy « smtp:<shared mailbox name » est déjà utilisée par les adresses proxy ou **\> LegacyExchangeDN de « \<name> ». Choisissez une autre adresse proxy,** cela signifie que vous essayez de donner à la boîte aux lettres partagée un nom déjà utilisé. Par exemple, imaginons que vous vouliez donner les noms info@domaine1 et info@domaine2 à des boîtes aux lettres partagées. Il existe deux méthodes pour y parvenir :

  - Utiliser Windows PowerShell. Consultez ce billet de blog pour obtenir des instructions : Créer des boîtes aux lettres partagées [avec le même alias sur différents domaines](https://www.cogmotive.com/blog/office-365-tips/create-shared-mailboxes-with-same-alias-at-different-domains-in-office-365)
    
  - Nommez la deuxième boîte aux lettres partagée différemment du début pour contourner l’erreur. Ensuite, dans le Centre d’administration, renommez la boîte aux lettres partagée comme vous le souhaitez.

## <a name="error-about-not-having-send-permissions-when-using-a-shared-mailbox"></a>Erreur de non-envoi d’autorisations lors de l’utilisation d’une boîte aux lettres partagée

Si vous avez créé une boîte aux lettres partagée, puis que vous essayez d’envoyer un message à partir de celle-ci, vous pouvez obtenir ceci :

**Ce message n’a pas pu être envoyé. Vous n’êtes pas autorisé à envoyer le message au nom de l’utilisateur spécifié.**

Ce message s’affiche Microsoft 365 rencontre un problème de latence de réplication. Il devrait disparaître dans une heure ou deux, lorsque les informations sur votre nouvelle boîte aux lettres partagée (ou utilisateur ajouté) sont répliquées dans tous nos centres de données. Patientez une heure, puis tentez à nouveau d’envoyer un message.

## <a name="related-content"></a>Contenu associé

[À propos des boîtes aux lettres partagées](about-shared-mailboxes.md) (article)\
[Créer une boîte aux lettres partagée](create-a-shared-mailbox.md) (article)\
[Configurer une boîte aux lettres partagée](configure-a-shared-mailbox.md) (article)\
[Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md) (article)\
[Supprimer une licence d’une boîte aux lettres partagée](remove-license-from-shared-mailbox.md) (article)


    

