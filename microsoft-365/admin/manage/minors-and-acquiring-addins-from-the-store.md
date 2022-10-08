---
title: Mineurs et acquisition de compléments à partir du Store
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
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Découvrez les réglementations du Règlement général sur la protection des données (RGPD) qui régissent les données personnelles des mineurs.
ms.openlocfilehash: a3effed0efb2dc03ba769dd8a9d0d8685f3b6f34
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68208455"
---
# <a name="minors-and-acquiring-add-ins-from-the-store"></a>Mineurs et acquisition de compléments à partir du Store

Le Règlement général sur la protection des données (RGPD) est un règlement de l’Union européenne qui entre en vigueur le 25 mai 2018. Il donne aux utilisateurs des droits et une protection de leurs données. L’un des aspects du RGPD est que les mineurs ne peuvent pas recevoir leurs données personnelles aux parties que leur parent ou tuteur n’a pas approuvées. L’âge spécifique défini comme mineur dépend de la région où se trouve la personne.

Les régions qui ont des réglementations légales sur le consentement parental incluent les États-Unis, la Corée du Sud, le Royaume-Uni et l’Union européenne. Pour ces régions, un mineur est empêché (via Azure Active Directory) d’obtenir de nouveaux compléments Office à partir du Store et d’exécuter des compléments précédemment acquis. Pour les pays sans réglementation légale, il n’y aura aucune restriction de téléchargement.

Un utilisateur est déterminé comme étant mineur en fonction des données spécifiées dans Azure Active Directory. L’administrateur de l’organisation est responsable de la déclaration du groupe d’âge légal et du consentement parental pour cet utilisateur.

Si le parent/tuteur consent à un mineur à l’aide d’un complément spécifique, l’administrateur de l’organisation peut utiliser le déploiement centralisé pour déployer ce complément sur tous les mineurs qui ont le consentement.

Pour être conforme au RGPD pour les mineurs, vous devez vous assurer que l’une des builds suivantes d’Office est déployée dans votre établissement scolaire/organisation.

 **Pour Word, Excel, PowerPoint et Project** :

|Plateforme|Numéro de build|
|---|---|
|Applications Microsoft 365 pour les grandes entreprises (canal actuel)|9001.2138|
|Applications Microsoft 365 pour les grandes entreprises (canal d’entreprise semi-annuel)|8431.2159|
|Office 2016 pour Windows|16.0.4672.1000|
|Office 2013 pour Windows|15.0.5023.1000|
|Office 2016 pour Mac|16.11.18020200|
|Office pour le web|S/O|

 **Pour Outlook** :

|Plateforme|Numéro de build|
|---|---|
|Outlook 2016 pour Windows (MSI)|Build No TBD|
|Outlook 2016 pour Windows (C2R)|16.0.9323.1000|
|Office 2016 pour Mac|16.0.9318.1000|
|Outlook Mobile pour iOS|2.75.0|
|Outlook Mobile pour Android|2.2.145|
|Outlook.com|S/O|

 **Conditions requises pour Office 2013**

Word, Excel et PowerPoint 2013 pour Windows prendront en charge les mêmes vérifications mineures si la bibliothèque d’authentification Active Directory (ADAL) est activée. Il existe deux options de conformité, comme expliqué ci-après.

- **Activez ADAL**. Cet article explique comment activer la bibliothèque ADAL pour Office 2013 : [Utilisation de l’authentification moderne Microsoft 365 avec les clients Office](../../enterprise/modern-auth-for-office-2013-and-2016.md).<br/>Vous devez également définir les clés de Registre pour activer ADAL, comme expliqué dans [Activer l’authentification moderne pour Office 2013 sur les appareils Windows](../security-and-compliance/enable-modern-authentication.md).<br/>En outre, vous devez installer les mises à jour d’avril suivantes pour Office 2013 :

  - [Description de la mise à jour de sécurité pour Office 2013 : 10 avril 2018](https://support.microsoft.com/help/4018330/description-of-the-security-update-for-office-2013-april-10-2018)

  - [Mise à jour du 3 avril 2018 pour Office 2013 (KB4018333)](https://support.microsoft.com/help/4018333/april-3-2018-update-for-office-2013-kb4018333)

- **N’activez pas ADAL**. Si vous ne parvenez pas à activer la bibliothèque ADAL dans Office 2013, nous vous recommandons d’utiliser stratégie de groupe pour désactiver le Windows Store pour les clients Office. Vous trouverez [ici](/previous-versions/office/office-2013-resource-kit/cc178992(v=office.15)) des informations sur la désactivation de l’application pour les paramètres Office.

## <a name="related-articles"></a>Articles connexes

[Déployer des compléments dans le centre d’administration](./manage-deployment-of-add-ins.md)

[Gérer des compléments dans le centre d’administration](./manage-addins-in-the-admin-center.md)
