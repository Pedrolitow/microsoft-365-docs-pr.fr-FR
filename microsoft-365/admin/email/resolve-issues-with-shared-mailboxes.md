---
title: Résoudre les problèmes liés aux boîtes aux lettres partagées
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
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
description: Vous pouvez obtenir des erreurs lorsque vous configurez des boîtes aux lettres partagées. Essayez ces solutions si vous rencontrez des problèmes avec les boîtes aux lettres partagées.
ms.openlocfilehash: 1658aa8f2fcb49dba600970bab7b406d928913eb
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68719871"
---
# <a name="resolve-issues-with-shared-mailboxes"></a>Résoudre les problèmes liés aux boîtes aux lettres partagées

Si vous voyez des messages d’erreur lors de la création ou de l’utilisation d’une boîte aux lettres partagée, essayez ces solutions possibles. 

## <a name="error-when-creating-shared-mailboxes"></a>Erreur lors de la création de boîtes aux lettres partagées

Si le message d’erreur s’affiche, **l’adresse proxy « smtp:<nom\> de boîte aux lettres partagée » est déjà utilisée par les adresses proxy ou LegacyExchangeDN de «\<name> ». Choisissez une autre adresse proxy**, cela signifie que vous essayez de donner à la boîte aux lettres partagée un nom déjà utilisé. Par exemple, imaginons que vous vouliez donner les noms info@domaine1 et info@domaine2 à des boîtes aux lettres partagées. Il existe deux méthodes pour y parvenir :

- Utilisez Exchange Online PowerShell. Consultez ce billet de blog pour obtenir des instructions : [Créer des boîtes aux lettres partagées avec le même alias dans différents domaines](https://blog.quadrotech-it.com/blog/create-shared-mailboxes-with-same-alias-at-different-domains-in-office-365/)

- Nommez la deuxième boîte aux lettres partagée différemment du début pour contourner l’erreur. Ensuite, dans le Centre d’administration, renommez la boîte aux lettres partagée comme vous le souhaitez.

## <a name="error-about-not-having-send-permissions-when-using-a-shared-mailbox"></a>Erreur concernant le fait de ne pas disposer des autorisations d’envoi lors de l’utilisation d’une boîte aux lettres partagée

Si vous avez créé une boîte aux lettres partagée, puis que vous essayez d’envoyer un message à partir de celle-ci, vous pouvez obtenir ce qui suit :

**Impossible d’envoyer ce message. Vous n’avez pas l’autorisation d’envoyer le message au nom de l’utilisateur spécifié.**

Ce message s’affiche lorsque Microsoft 365 rencontre un problème de latence de réplication. Elle devrait disparaître dans une heure environ, lorsque les informations relatives à votre nouvelle boîte aux lettres partagée (ou à l’utilisateur ajouté) sont répliquées dans tous nos centres de données. Attendez une heure, puis réessayez pour envoyer un message.

## <a name="related-content"></a>Contenu associé

[À propos des boîtes aux lettres partagées](about-shared-mailboxes.md) (article)\
[Créer une boîte aux lettres partagée](create-a-shared-mailbox.md) (article)\
[Configurer une boîte aux lettres partagée](configure-a-shared-mailbox.md) (article)\
[Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md) (article)\
[Supprimer une licence d’une boîte aux lettres partagée](remove-license-from-shared-mailbox.md) (article)
