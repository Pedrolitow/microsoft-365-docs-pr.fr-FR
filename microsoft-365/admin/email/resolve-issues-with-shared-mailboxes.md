---
title: Résoudre les problèmes liés aux boîtes aux lettres partagées
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
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
search.appverid:
- BCS160
- MET150
- MOE150
description: Essayez ces solutions si vous rencontrez des problèmes avec les boîtes aux lettres partagées.
ms.openlocfilehash: 52aac8ab6936dfeba2ae4b5b7a80c45029ec6105
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43628746"
---
# <a name="resolve-issues-with-shared-mailboxes"></a>Résoudre les problèmes liés aux boîtes aux lettres partagées

Si des messages d’erreur s’affichent lors de la création ou de l’utilisation d’une boîte aux lettres partagée, essayez ces solutions possibles. 

## <a name="error-when-creating-shared-mailboxes"></a>Erreur lors de la création de boîtes aux lettres partagées
<a name="bkmk_Fix"> </a>

Si le message d’erreur s’affiche, **l’adresse proxy « SMTP : <nom\>de la boîte aux lettres partagée » est déjà utilisée par les adresses proxy\<ou legacyExchangeDN de « Name> ». Veuillez choisir une autre adresse proxy**, ce qui signifie que vous essayez de donner à la boîte aux lettres partagée un nom qui est déjà utilisé. Par exemple, imaginons que vous vouliez donner les noms info@domaine1 et info@domaine2 à des boîtes aux lettres partagées. Vous pouvez procéder de deux manières :

  - Utiliser Windows PowerShell. Consultez ce billet de blog pour obtenir des instructions : [créer des boîtes aux lettres partagées avec le même alias sur des domaines différents](https://www.cogmotive.com/blog/office-365-tips/create-shared-mailboxes-with-same-alias-at-different-domains-in-office-365)
    
  - Nommez la deuxième boîte aux lettres partagée quelque part du début pour contourner l’erreur. Ensuite, dans le centre d’administration, renommez la boîte aux lettres partagée comme vous le souhaitez.

## <a name="error-about-not-having-send-permissions-when-using-a-shared-mailbox"></a>Erreur de n’avoir pas les autorisations d’envoi lors de l’utilisation d’une boîte aux lettres partagée

Si vous avez créé une boîte aux lettres partagée et essayez d’envoyer un message à partir de celle-ci, vous pouvez obtenir ce qui suit :

**Ce message n’a pas pu être envoyé. Vous n’êtes pas autorisé à envoyer le message au nom de l’utilisateur spécifié.**

Ce message s’affiche lorsque Microsoft 365 rencontre un problème de latence de réplication. Elle doit disparaître au bout d’une heure, lorsque les informations sur votre nouvelle boîte aux lettres partagée (ou utilisateur ajouté) sont répliquées sur l’ensemble de nos centres de données. Patientez une heure, puis réessayez d’envoyer un message.

## <a name="related-articles"></a>Articles connexes

[À propos des boîtes aux lettres partagées](about-shared-mailboxes.md)

[Créer une boîte aux lettres partagée](create-a-shared-mailbox.md)

[Configurer une boîte aux lettres partagée](configure-a-shared-mailbox.md)

[Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md)

[Supprimer une licence à partir d’une boîte aux lettres partagée](remove-license-from-shared-mailbox.md)


    

