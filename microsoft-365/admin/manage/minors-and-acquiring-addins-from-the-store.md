---
title: Mineurs et acquisition de compléments à partir du Windows Store
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
- Tier3
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Découvrez les réglementations du Règlement général sur la protection des données (RGPD) qui régissent les données personnelles des mineurs.
ms.openlocfilehash: 3671d95cac7064a3254aa3fdc2ae5edbd0a33a83
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68718631"
---
# <a name="minors-and-acquiring-add-ins-from-the-store"></a>Mineurs et acquisition de compléments à partir du Windows Store

Le Règlement général sur la protection des données (RGPD) est un règlement de l’Union européenne qui entre en vigueur le 25 mai 2018. Il accorde aux utilisateurs des droits et la protection de leurs données. L’un des aspects du RGPD est que les mineurs ne peuvent pas avoir leurs données personnelles envoyées à des parties que leur parent ou tuteur n’a pas approuvées. L’âge spécifique défini comme mineur dépend de la région où se trouve l’individu.

Les régions qui ont des réglementations légales sur le consentement parental incluent le États-Unis, la Corée du Sud, le Royaume-Uni et l’Union européenne. Pour ces régions, un mineur est bloqué (via Azure Active Directory) pour obtenir de nouveaux compléments Office à partir du Store et exécuter des compléments précédemment acquis. Pour les pays sans réglementation légale, il n’y aura aucune restriction de téléchargement.

Un utilisateur est considéré comme mineur en fonction des données spécifiées dans Azure Active Directory. L’administrateur de l’organisation est chargé de déclarer le groupe d’âge légal et le consentement parental pour cet utilisateur.

Si le parent/tuteur donne son consentement à un mineur à l’aide d’un complément spécifique, l’administrateur de l’organisation peut utiliser le déploiement centralisé pour déployer ce complément sur tous les mineurs qui ont le consentement.

Pour être conforme au RGPD pour les mineurs, vous devez vous assurer que l’une des versions suivantes d’Office est déployée dans votre établissement scolaire/organisation.

 **Pour Word, Excel, PowerPoint et Project** :

|Plateforme|Numéro de build|
|---|---|
|Applications Microsoft 365 pour les grandes entreprises (canal actuel)|9001.2138|
|Applications Microsoft 365 pour les grandes entreprises (canal Entreprise semi-annuel)|8431.2159|
|Office 2016 pour Windows|16.0.4672.1000|
|Office 2013 pour Windows|15.0.5023.1000|
|Office 2016 pour Mac|16.11.18020200|
|Office pour le web|S/O|

 **Pour Outlook** :

|Plateforme|Numéro de build|
|---|---|
|Outlook 2016 pour Windows (MSI)|Build Aucun TBD|
|Outlook 2016 pour Windows (C2R)|16.0.9323.1000|
|Office 2016 pour Mac|16.0.9318.1000|
|Outlook Mobile pour iOS|2.75.0|
|Outlook Mobile pour Android|2.2.145|
|Outlook.com|S/O|

 **Configuration requise pour Office 2013**

Word, Excel et PowerPoint 2013 pour Windows prennent en charge les mêmes vérifications mineures si la bibliothèque d’authentification Active Directory (ADAL) est activée. Il existe deux options pour la conformité, comme expliqué ci-dessous.

- **Activez la bibliothèque ADAL**. Cet article explique comment activer la bibliothèque ADAL pour Office 2013 : [Utilisation de l’authentification moderne Microsoft 365 avec les clients Office](../../enterprise/modern-auth-for-office-2013-and-2016.md).<br/>Vous devez également définir les clés de Registre pour activer la bibliothèque ADAL, comme expliqué dans [Activer l’authentification moderne pour Office 2013 sur les appareils Windows](../security-and-compliance/enable-modern-authentication.md).<br/>En outre, vous devez installer les mises à jour d’avril suivantes pour Office 2013 :

  - [Description de la mise à jour de sécurité pour Office 2013 : 10 avril 2018](https://support.microsoft.com/help/4018330/description-of-the-security-update-for-office-2013-april-10-2018)

  - [Mise à jour du 3 avril 2018 pour Office 2013 (KB4018333)](https://support.microsoft.com/help/4018333/april-3-2018-update-for-office-2013-kb4018333)

- **N’activez pas la bibliothèque ADAL**. Si vous ne parvenez pas à activer la bibliothèque ADAL dans Office 2013, nous vous recommandons d’utiliser stratégie de groupe pour désactiver le Store pour les clients Office. Vous trouverez [ici](/previous-versions/office/office-2013-resource-kit/cc178992(v=office.15)) des informations sur la désactivation des paramètres de l’application pour Office.

## <a name="related-articles"></a>Articles connexes

[Déployer des compléments dans le centre d’administration](./manage-deployment-of-add-ins.md)

[Gérer des compléments dans le centre d’administration](./manage-addins-in-the-admin-center.md)
