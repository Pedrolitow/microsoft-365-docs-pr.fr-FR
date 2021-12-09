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
ms.localizationpriority: medium
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
- AdminTemplateSet
- m365solution-removeemployee
search.appverid:
- BCS160
- MET150
- MOE150
description: Suivez les étapes de cette solution pour supprimer un ancien employé de Microsoft 365 et sécuriser les données de votre organisation.
ms.openlocfilehash: 15ef426892bcabe0af71c52f1664255cb82b6637
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61370247"
---
# <a name="overview-remove-a-former-employee-and-secure-data"></a>Vue d’ensemble : supprimer un ancien employé et sécuriser les données

Nous avons souvent la question suivante : « Que dois-je faire pour sécuriser les données et protéger l’accès lorsqu’un employé quitte mon organisation ? » Cette série d’articles explique comment bloquer l’accès à Microsoft 365 afin que ces utilisateurs ne se connectent pas aux Microsoft 365, les étapes à suivre pour sécuriser les données de l’organisation et permettre aux autres employés d’accéder aux données de messagerie et de OneDrive.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être administrateur général pour effectuer les étapes de cette solution.

Pour effectuer les étapes de cette série, vous devez utiliser Microsoft 365 fonctionnalités et fonctionnalités.

|Produit ou composant|Fonctionnalité|
|---|---|
|Centre d’administration Microsoft 365|Convertir une boîte aux lettres, forward email, révoquer l’accès, supprimer un utilisateur |
|Centre d’administration Exchange|Bloquer l’utilisateur, bloquer l’accès au courrier électronique, effacer l’appareil |
|OneDrive et SharePoint |Accorder l’accès à d’autres utilisateurs |
|Outlook|Importer des fichiers pst, ajouter une boîte aux lettres |
|Active Directory|Supprimer des utilisateurs dans des environnements hybrides |

## <a name="watch-delete-a-user"></a>Regarder : supprimer un utilisateur

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR?autoplay=false]

Lorsqu’un employé quitte l’entreprise, vous devez le supprimer de Microsoft 365 entreprise. Avant cela, vous devez les empêcher d’accéder aux fichiers de l’entreprise, conserver les documents qu’ils ont créés et effectuer plusieurs autres tâches d’administration associées à la suppression d’un utilisateur.

1. Dans le Centre d’administration, **sélectionnez Utilisateurs** et sélectionnez **Utilisateurs actifs.**
1. Sélectionnez l’utilisateur à supprimer, puis sélectionnez **Supprimer l’utilisateur.**
1. Cochez la case pour supprimer leur licence, puis cochez la case pour supprimer leurs alias de messagerie.
1. Cochez la case pour accorder à un autre utilisateur l’accès au courrier électronique de l’ancien employé, puis sélectionnez Sélectionner un utilisateur **et définir les options de messagerie.**
1. Pour supprimer les alias de messagerie associés, **sélectionnez X** en côté de leurs alias.
1. Examinez les informations de boîte aux lettres partagées, puis sélectionnez **Terminer.**
1. Confirmez que vos options sont définies correctement, puis choisissez **Affecter et convertir.**
1. Examinez vos résultats, puis sélectionnez **Fermer.**

Après avoir supprimé un utilisateur, vous avez jusqu’à 30 jours pour restaurer son compte.

## <a name="solution-remove-a-former-employee"></a>Solution : supprimer un ancien employé

> [!IMPORTANT]
> Même si nous avons numéroé les étapes de cette solution et que vous n’avez pas besoin d’effectuer la solution dans l’ordre exact, nous vous recommandons d’effectuer les étapes de cette façon.

:::image type="content" source="../../media/delete-user-account.png" alt-text="Capture d’écran : Étapes de suppression d’un ancien employé de votre organisation":::

<br>

****

|Étape|Raison|
|---|---|
|[Étape 1 : empêcher un ancien employé de se connecter et bloquer l’accès Microsoft 365 services](remove-former-employee-step-1.md)|Cela empêche votre ancien employé de se connecter à Microsoft 365 et empêche la personne d’accéder Microsoft 365 services.|
|[Étape 2 : enregistrer le contenu de la boîte aux lettres d’un ancien employé](remove-former-employee-step-2.md)|Cela est utile pour la personne qui va reprendre le travail de l’employé, ou en cas de litige.|
|[Étape 3 : forward a former employee’s email to another employee or convert to a shared mailbox](remove-former-employee-step-3.md)|Cette étape vous permet de conserver l'adresse e-mail de l'ancien employé. Si certains de vos clients ou partenaires continuent d'envoyer du courrier à l'adresse de l'ancien employé, celui-ci est reçu par son remplaçant.|
|[Étape 4 : donner à un autre employé l’accès OneDrive données Outlook données](remove-former-employee-step-4.md)|Si vous supprimez uniquement la licence d'un utilisateur, mais pas le compte, vous pouvez toujours accéder au contenu enregistré dans l'espace OneDrive de l'utilisateur même après 30 jours. <p> Avant de supprimer le compte, vous devez accorder l’accès à ses OneDrive et Outlook à un autre utilisateur. Une fois que vous avez supprimé le compte d’un employé, le contenu de ses OneDrive et Outlook est conservé **pendant 30** jours. Toutefois, pendant ces 30 jours, vous pouvez restaurer le compte de l’utilisateur et accéder à son contenu. Si vous restituer le compte de l’utilisateur, les OneDrive et Outlook restent accessibles même après 30 jours.|
|[Étape 5 : effacer et bloquer l’appareil mobile d’un ancien employé](remove-former-employee-step-5.md)|Cette étape supprime vos données professionnelles du téléphone ou de la tablette.|
|[Étape 6 : Supprimer et supprimer la licence Microsoft 365 d’un ancien employé](remove-former-employee-step-6.md)|Si vous retirez une licence, vous pouvez l'affecter à quelqu'un d'autre. Vous pouvez également supprimer la licence pour ne plus payer pour celle-ci jusqu'à ce que vous embauchiez une autre personne.  <p> Lorsque vous retirez ou supprimez une licence, les anciens courriers, les contacts et le calendrier de l'utilisateur sont conservés pendant **30 jours** avant d'être supprimés définitivement. Si vous retirez ou supprimez une licence, mais pas le compte, vous pouvez toujours accéder au contenu enregistré dans l'espace OneDrive de l'utilisateur même après 30 jours.  |
|[Étape 7 : supprimer le compte d’utilisateur d’un ancien employé](remove-former-employee-step-7.md)|Cela supprime le compte de votre centre d’administration. Ainsi, les choses restent claires et bien organisées.|
|

## <a name="related-content"></a>Contenu associé

[Restaurer un utilisateur](restore-user.md) (article)\
[Ajouter un nouvel employé dans Microsoft 365](add-new-employee.md) (article)\
[Attribuer des licences aux utilisateurs](../manage/assign-licenses-to-users.md) (article)\
[Désattribuer des licences à des utilisateurs](../manage/remove-licenses-from-users.md) (article)
