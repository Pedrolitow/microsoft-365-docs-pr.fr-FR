---
title: Configuration du Scheduler pour Microsoft 365.
ms.author: v-aiyengar
author: AshaIyengar21
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
localization_priority: Normal
description: Configuration du Scheduler pour Microsoft 365.
ms.openlocfilehash: 79e1596288836770c720cb312580fc706bb7b95f
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2021
ms.locfileid: "52286191"
---
# <a name="setting-up-scheduler-for-microsoft-365"></a>Configuration du Scheduler pour Microsoft 365

Pour configurer le Scheduler pour Microsoft 365, les conditions préalables sont les suivantes :

|**De quoi ai-je besoin ?** |**Description** |
|-------------------|-------------|
|Boîte aux lettres Cortana |Les administrateurs client doivent définir une boîte aux lettres pour qu’elle serve de boîte aux lettres « Cortana » (c’est-à-dire, cortana@yourdomain.com).         |
|Boîte aux lettres Exchange Online |Les utilisateurs doivent avoir un Exchange Online et le calendrier         |
|Licence du scheduleur |Pour plus d’informations sur les licences et les tarifs, voir [Scheduler for Microsoft 365](https://www.microsoft.com/microsoft-365/meeting-scheduler-pricing).        |

## <a name="create-a-mailbox-for-cortana"></a>Créer une boîte aux lettres pour Cortana
Une Exchange de votre client fait office de boîte aux lettres Cortana pour que votre client envoie et reçoie des courriers électroniques vers et depuis Cortana. Tous les messages électroniques envoyés à Cortana sont conservés dans la boîte aux lettres Cortana de votre client en fonction de votre stratégie de rétention.

- Utilisez le centre Microsoft 365'administration pour créer une boîte aux lettres. Une stratégie de rétention de 30 jours est recommandée. Utilisez le nom Cortana dans l’adresse SMTP principale de votre boîte aux lettres. Des noms tels que « Cortana@yourdomain.com », « CortanaScheduler@contoso.com » ou « Cortana.Scheduler@yourdomain.com » sont recommandés.
- Contactez Microsoft (scheduler_m365@microsoft.com) pour activer votre boîte aux lettres Cortana. 

> [!IMPORTANT]
> Vous devez contacter Microsoft pour configurer votre boîte aux lettres Cortana afin qu’elle utilise le service Scheduler en scheduler_m365@microsoft.com. L’activation de votre boîte aux lettres Cortana peut prendre jusqu’à deux semaines.

## <a name="exchange-online-mailbox"></a>Boîte aux lettres Exchange Online
Le programmeur est un module Microsoft 365. Les organisateurs de réunions doivent avoir une boîte Exchange Online et un calendrier pour que le Scheduler fonctionne.

## <a name="exchange-requirements"></a>Configuration requise pour Exchange

Outre le Programmeur de licences, vous devez avoir l’une des licences suivantes :

- Microsoft 365 E3, A3, E5, A5
- Business Basic, Business, Business Standard, Business Premium
- Office 365 E1, A1, E3, A3, E5, A5
- Business Essentials, Business Premium
- Exchange Online Plan 1 ou Plan 2. 

> [!Note]
> **Le programme d’Microsoft 365** n’est pas disponible pour les utilisateurs de Office 365 21Vianet en Chine. Il n’est pas non plus disponible pour les utilisateurs Microsoft 365 avec le cloud allemand qui utilise le groupe de sécurité des données Allemand Telekom. Nous le prenons en charge pour les utilisateurs situés en Allemagne dont les données ne résident pas dans le centre de données allemand.
>
>Cette fonctionnalité n’est pas non plus prise en charge pour les utilisateurs du cloud public, notamment GCC, Consumer, GCC de haut niveau ou DoD.
