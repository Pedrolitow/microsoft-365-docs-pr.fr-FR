---
title: Supprimer un ancien employé - Vue d’ensemble
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- adminvideo
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- m365solution-removeemployee
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
description: Bloquez l’accès à Microsoft 365 afin qu’un ancien employé ne puisse pas se connecter, sécurise les données de l’organisation et autorise les autres employés à accéder à leurs e-mails et à leurs données OneDrive.
ms.openlocfilehash: 6d30438f156a888f43fbf51b13f797450bd4097c
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68205198"
---
# <a name="overview-remove-a-former-employee-and-secure-data"></a>Vue d’ensemble : Supprimer un ancien employé et sécuriser les données

Consultez [l’aide de Microsoft 365 petite entreprise](https://go.microsoft.com/fwlink/?linkid=2197659) sur YouTube.

Une question que nous obtenons souvent est la suivante : « Que dois-je faire pour sécuriser les données et protéger l’accès lorsqu’un employé quitte mon organisation ? » Cette série d’articles explique comment bloquer l’accès à Microsoft 365 afin que ces utilisateurs ne puissent pas se connecter à Microsoft 365, les étapes à suivre pour sécuriser les données de l’organisation et comment autoriser d’autres employés à accéder à la messagerie et aux données OneDrive.

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de [collaborer avec un spécialiste des petites entreprises Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Aide aux entreprises, vos employés et vous avez accès 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être administrateur général pour effectuer les étapes de cette solution.

Pour effectuer les étapes de cette série, vous utilisez ces fonctionnalités et fonctionnalités De Microsoft 365.

|Produit ou composant|Fonctionnalité|
|---|---|
|Centre d’administration Microsoft 365|Convertir la boîte aux lettres, transférer l’e-mail, révoquer l’accès, supprimer l’utilisateur |
|Centre d’administration Exchange|Bloquer l’accès aux e-mails, réinitialiser l’appareil |
|OneDrive et SharePoint |Accorder l’accès à d’autres utilisateurs |
|Outlook|Importer des fichiers pst, ajouter une boîte aux lettres |
|Active Directory|Supprimer des utilisateurs dans des environnements hybrides |


## <a name="solution-remove-a-former-employee"></a>Solution : Supprimer un ancien employé

> [!IMPORTANT]
> Bien que nous ayons numéroté les étapes de cette solution et que vous n’ayez pas à effectuer la solution à l’aide de l’ordre exact, nous vous recommandons d’effectuer les étapes de cette façon.

:::image type="content" source="../../media/delete-user-account.png" alt-text="Capture d’écran : Étapes de suppression d’un ancien employé de votre organisation":::

<br>

****

|Étape|Raison|
|---|---|
|[Étape 1 : empêcher un ancien employé de se connecter et de bloquer l’accès aux services Microsoft 365](remove-former-employee-step-1.md)|Cela empêche votre ancien employé de se connecter à Microsoft 365 et empêche la personne d’accéder aux services Microsoft 365.|
|[Étape 2 : enregistrer le contenu de la boîte aux lettres d’un ancien employé](remove-former-employee-step-2.md)|Cela est utile pour la personne qui va reprendre le travail de l’employé, ou en cas de litige.|
|[Étape 3 : réinitialiser et bloquer l’appareil mobile d’un ancien employé](remove-former-employee-step-3.md)|Cette étape supprime vos données professionnelles du téléphone ou de la tablette.|
|[Étape 4 : transférer l’e-mail d’un ancien employé à un autre employé ou convertir en boîte aux lettres partagée](remove-former-employee-step-4.md)|This lets you keep the former employee's email address active. If you have customers or partners still sending email to the former employee's address, this gets them to the person taking over the work.|
|[Étape 5 : accorder à un autre employé l’accès aux données OneDrive et Outlook](remove-former-employee-step-5.md)|Si vous supprimez uniquement la licence d'un utilisateur, mais pas le compte, vous pouvez toujours accéder au contenu enregistré dans l'espace OneDrive de l'utilisateur même après 30 jours. <p> Avant de supprimer le compte, vous devez donner accès à oneDrive et Outlook à un autre utilisateur. Après avoir supprimé le compte d’un employé, le contenu dans onedrive et Outlook est conservé pendant **30** jours. Toutefois, au cours de ces 30 jours, vous pouvez restaurer le compte de l’utilisateur et accéder à son contenu. Si vous restaurez le compte de l’utilisateur, le contenu OneDrive et Outlook reste accessible même après 30 jours.| 
|[Étape 6 : Supprimer et supprimer la licence Microsoft 365 d’un ancien employé](remove-former-employee-step-6.md)|When you remove a license, you can assign it to someone else. Or, you can delete the license so you don't pay for it until you hire another person. <p> When you remove or delete a license, the user's old email, contacts, and calendar are retained for **30 days**, then permanently deleted. If you remove or delete a license but don't delete the account, the content in the user's OneDrive will remain accessible to you even after 30 days.|
|[Étape 7 : Supprimer le compte d’utilisateur d’un ancien employé](remove-former-employee-step-7.md)|Cela supprime le compte de votre centre d’administration. Ainsi, les choses restent claires et bien organisées.|

## <a name="watch-delete-a-user"></a>Regarder : Supprimer un utilisateur

Regardez cette vidéo et d’autres encore sont disponibles sur notre [chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2198203).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR?autoplay=false]

Lorsqu’un employé quitte l’entreprise, vous devez le supprimer de Microsoft 365 pour les entreprises. Avant de le faire, vous devez les empêcher d’accéder aux fichiers d’entreprise, conserver les documents qu’ils ont créés et effectuer plusieurs autres tâches d’administration associées à la suppression d’un utilisateur.

1. Dans le Centre d’administration, sélectionnez **Utilisateurs**, puis choisissez **Utilisateurs actifs**.
1. Sélectionnez l’utilisateur à supprimer, puis **sélectionnez Supprimer l’utilisateur**.
1. Cochez la case pour supprimer leur licence, puis cochez la case pour supprimer leurs alias de messagerie.
1. Cochez la case pour accorder à un autre utilisateur l’accès à l’e-mail de l’ancien employé, puis **sélectionnez Sélectionner un utilisateur et définissez les options de courrier** électronique.
1. Pour supprimer les alias de messagerie associés, sélectionnez **X** en regard de leurs alias.
1. Passez en revue les informations de boîte aux lettres partagées, puis sélectionnez **Terminer**.
1. Vérifiez que vos options sont définies correctement, puis **choisissez Affecter et convertir**.
1. Passez en revue vos résultats, puis sélectionnez **Fermer**.

Après avoir supprimé un utilisateur, vous avez jusqu’à 30 jours pour restaurer son compte.
## <a name="related-content"></a>Contenu associé

[Restaurer un utilisateur](restore-user.md) (article)\
[Ajouter un nouvel employé dans Microsoft 365](add-new-employee.md) (article)\
[Attribuer des licences aux utilisateurs](../manage/assign-licenses-to-users.md) (article)\
[Remove-CalendarEvents](/powershell/module/exchange/remove-calendarevents)\
[Annuler l’affectation des licences des utilisateurs](../manage/remove-licenses-from-users.md) (article)
