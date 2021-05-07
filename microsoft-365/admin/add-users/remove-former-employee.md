---
title: Supprimer un ancien employé - Vue d’ensemble
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: Suivez les étapes de cette solution pour supprimer un ancien employé de Microsoft 365 et sécuriser les données de votre organisation.
ms.openlocfilehash: 4b4cf59fdce81b3098ee333095daa8e1af1cd5c5
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52241735"
---
# <a name="overview-remove-a-former-employee-and-secure-data"></a>Vue d’ensemble : supprimer un ancien employé et sécuriser les données

Nous avons souvent la question suivante : « Que dois-je faire pour sécuriser les données et protéger l’accès lorsqu’un employé quitte mon organisation ? » Cette série d’articles explique comment bloquer l’accès à Microsoft 365, les étapes à suivre pour sécuriser vos données et comment autoriser d’autres employés à accéder aux données.

Regardez une courte vidéo sur la suppression d’un employé. <br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR] 

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](../../business-video/index.yml).

Pour empêcher un employé de se connecter :

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez la case à côté du nom de l’utilisateur, puis sélectionnez **Réinitialiser le mot de passe.**
3. Entrez un nouveau mot de passe, puis sélectionnez **Réinitialiser.** (Ne leur envoyez pas de message.)
4. Sélectionnez le nom de l’utilisateur pour aller  dans le volet de propriétés, puis sous l’onglet Compte, sélectionnez Lancer **la signature.**

> [!NOTE]
> Vous devez être un administrateur général pour lancer la signature.

Dans l’heure qui s’affiche( ou après avoir quitté la page de Microsoft 365 en cours), ils sont invités à se ré-inscrire. Un jeton d’accès est bon pendant une heure, donc la chronologie dépend du temps qui reste sur ce jeton et de la façon dont il quitte la page web actuelle.

> [!IMPORTANT]
> Même si nous avons numéroé les étapes de cette solution et que vous n’avez pas besoin d’effectuer la solution dans l’ordre exact, nous vous recommandons d’effectuer les étapes de cette façon.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être administrateur général pour effectuer les étapes de cette solution.

|||
|:-----|:-----|
|**Étape** <br/> |**Raison** <br/> |
|[Étape 1 : empêcher un ancien employé de se connecter et bloquer l’accès Microsoft 365 services](remove-former-employee-step-1.md) <br/> |Cela empêche votre ancien employé de se connecter à Microsoft 365 et empêche la personne d’accéder Microsoft 365 services. <br/> |
|[Étape 2 : enregistrer le contenu de la boîte aux lettres d’un ancien employé](remove-former-employee-step-2.md) <br/> |Cela est utile pour la personne qui va reprendre le travail de l’employé, ou en cas de litige. <br/> |
|[Étape 3 : Forward a former employee’s email to another employee or convert to a shared mailbox](remove-former-employee-step-3.md) <br/> |Cette étape vous permet de conserver l'adresse e-mail de l'ancien employé. Si certains de vos clients ou partenaires continuent d'envoyer du courrier à l'adresse de l'ancien employé, celui-ci est reçu par son remplaçant. <br/> |
|[Étape 4 : donner à un autre employé l’accès OneDrive données Outlook données](remove-former-employee-step-6.md) <br/> |Si vous supprimez uniquement la licence d'un utilisateur, mais pas le compte, vous pouvez toujours accéder au contenu enregistré dans l'espace OneDrive de l'utilisateur même après 30 jours. <br/><br/> Avant de supprimer le compte, vous devez accorder l’accès à ses OneDrive et Outlook à un autre utilisateur. Après avoir supprimé le compte d’un employé, le contenu de ses OneDrive et Outlook est conservé **pendant 30** jours. Toutefois, pendant ces 30 jours, vous pouvez restaurer le compte de l’utilisateur et accéder à son contenu. Si vous restituer le compte de l’utilisateur, les OneDrive et Outlook restent accessibles même après 30 jours. <br/> |
|[Étape 5 : effacer et bloquer l’appareil mobile d’un ancien employé](remove-former-employee-step-4.md) <br/> |Cette étape supprime vos données professionnelles du téléphone ou de la tablette.  <br/> |
|[Étape 6 : Supprimer et supprimer la licence Microsoft 365 d’un ancien employé](remove-former-employee-step-7.md) <br/> |Si vous retirez une licence, vous pouvez l'affecter à quelqu'un d'autre. Vous pouvez également supprimer la licence pour ne plus payer pour celle-ci jusqu'à ce que vous embauchiez une autre personne.  <br/><br/> Lorsque vous retirez ou supprimez une licence, les anciens courriers, les contacts et le calendrier de l'utilisateur sont conservés pendant **30 jours** avant d'être supprimés définitivement. Si vous retirez ou supprimez une licence, mais pas le compte, vous pouvez toujours accéder au contenu enregistré dans l'espace OneDrive de l'utilisateur même après 30 jours.  <br/> |
|[Étape 7 : supprimer le compte d’utilisateur d’un ancien employé](remove-former-employee-step-7.md) <br/> |Cela supprime le compte de votre centre d’administration. Ainsi, les choses restent claires et bien organisées. <br/> |

## <a name="related-articles"></a>Articles connexes

[Restaurer un utilisateur](restore-user.md)
