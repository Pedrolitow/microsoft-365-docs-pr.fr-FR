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
ms.openlocfilehash: f09d1f51ed8a868712c22fbd7a641b35f5d29073
ms.sourcegitcommit: b6e63febe24ef1f1793dfb3ecc5ed41a4e730578
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2021
ms.locfileid: "53309345"
---
# <a name="setting-up-scheduler-for-microsoft-365"></a>Configuration du Planificateur pour Microsoft 365


Pour configurer le Scheduler pour Microsoft 365, voici les conditions préalables :

|**De quoi ai-je besoin ?** |**Description** |
|-------------------|-------------|
|Cortana boîte aux lettres |Les administrateurs client doivent définir une boîte aux lettres pour qu’elle serve de boîte aux lettres « Cortana » (c’est-à-dire, cortana@yourdomain.com).         |
|Boîte aux lettres Exchange Online |Les utilisateurs doivent avoir un Exchange Online et un calendrier         |
|Licence du scheduleur |Pour plus d’informations sur les licences et les tarifs, voir [Scheduler for Microsoft 365](https://www.microsoft.com/en-us/microsoft-365/meeting-scheduler-pricing).        |

## <a name="create-a-mailbox-for-cortana"></a>Créer une boîte aux lettres pour Cortana
Une Exchange dans votre client agit comme la boîte aux lettres Cortana pour que votre client envoie et reçoit des courriers électroniques vers et depuis Cortana. Tous les messages électroniques envoyés Cortana sont conservés dans la boîte aux lettres Cortana de votre client en fonction de votre stratégie de rétention.

- Utilisez le Centre d’administration Microsoft 365 pour créer une boîte aux lettres utilisateur. Une stratégie de rétention de 30 jours est recommandée. 
- Utilisez le nom Cortana dans l’adresse SMTP principale de votre boîte aux lettres. Noms tels que « Cortana@yourdomain.com », « CortanaScheduler@contoso.com » ou « Cortana ». Scheduler@yourdomain.com' sont recommandés.

## <a name="designate-the-mailbox-as-the-scheduler-assistant"></a>Désigner la boîte aux lettres en tant qu’Assistant De planification

Une fois qu’une boîte aux lettres unique Cortana Scheduler a été créée, vous devez désigner la boîte aux lettres Microsoft 365 officiellement. Une fois que vous avez Cortana boîte aux lettres du scheduleur, elle sera disponible pour planifier des réunions au nom de vos utilisateurs.

Pour désigner la boîte Cortana scheduler, un administrateur autorisé doit exécuter une commande PowerShell d’une ligne. 

1. Connecter’Microsoft 365 l’espace d’exécuter PowerShell distant pour votre organisation.
2. Exécutez le script PowerShell suivant pour désigner la boîte aux lettres du Scheduler :

```powershell

Set-mailbox cortana@contoso.com -SchedulerAssistant:$true

```

Après l’exécution de cette commande « set » sur la boîte aux lettres du Cortana Scheduler, une nouvelle « PersistedCapability » est définie sur la boîte aux lettres pour noter que cette boîte aux lettres est « SchedulerAssistant ».

> [!NOTE]
> Suivez ces étapes pour connecter votre organisation à PowerShell si vous ne l’avez pas fait précédemment : Connecter à Microsoft 365 [avec PowerShell - Microsoft 365 Entreprise | Documents Microsoft](../enterprise/connect-to-microsoft-365-powershell.md)

Pour découvrir quelle boîte aux lettres de votre organisation est actuellement définie en tant qu’assistant Cortana Scheduler, exécutez la fonction Get :
 
```powershell

Get-mailbox | where {$_.PersistedCapabilities -Match "SchedulerAssistant"}

```

> [!IMPORTANT]
> La mise en service complète de la boîte aux lettres scheduler peut prendre jusqu’à deux heures pour définir la fonctionnalité SchedulerAssistant.

## <a name="exchange-online-mailbox"></a>Boîte aux lettres Exchange Online
Scheduler est un module Microsoft 365. Les organisateurs de réunion doivent avoir une boîte Exchange Online et un calendrier pour que le Scheduler fonctionne.

## <a name="exchange-requirements"></a>Configuration requise pour Exchange

Outre le Programmeur de licences, vous devez avoir l’une des licences suivantes :

- Microsoft 365 E3, A3, E5, A5
- Business Basic, Business, Business Standard, Business Premium
- Office 365 E1, A1, E3, A3, E5, A5
- Business Essentials, Business Premium
- Exchange Online Plan 1 ou Plan 2. 

> [!Note]
> **Le programme d’Microsoft 365** est actuellement disponible pour les clients internationaux multi-clients, en anglais uniquement.</br>
>
>Il n’est pas disponible pour les utilisateurs de Office 365 gérés par 21Vianet en Chine ou les utilisateurs de Microsoft 365 avec le cloud allemand qui utilise le groupe de sécurité des données Allemand Telekom. Nous le prenons en charge pour les utilisateurs situés en Allemagne dont les données ne résident pas dans le centre de données allemand.
>
>Cette fonctionnalité n’est pas non plus prise en charge pour les utilisateurs du cloud public, notamment GCC, Consumer, GCC de haut niveau ou DoD.
