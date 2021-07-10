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
ms.openlocfilehash: 924b25e3d921f402c97632f7475ed5beea98d5c7
ms.sourcegitcommit: f7fbf45af64c5c0727fd5eaab309d20ad097a483
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2021
ms.locfileid: "53362545"
---
# <a name="setting-up-scheduler-for-microsoft-365"></a>Configuration du Planificateur pour Microsoft 365


Pour configurer le Scheduler pour Microsoft 365, voici les conditions préalables :

| De quoi ai-je besoin ? | Description |
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
> Si vous ne l’avez pas fait précédemment, suivez ces étapes pour connecter votre organisation à PowerShell : Connecter à Microsoft 365 [avec PowerShell.](../enterprise/connect-to-microsoft-365-powershell.md)

Pour découvrir quelle boîte aux lettres de votre organisation est actuellement définie en tant qu’assistant Cortana Scheduler, exécutez la fonction Get :

```powershell
Get-mailbox | where {$_.PersistedCapabilities -Match "SchedulerAssistant"}
```

> [!IMPORTANT]
> La mise en service complète de la boîte aux lettres scheduler peut prendre jusqu’à deux heures pour définir la fonctionnalité SchedulerAssistant.

## <a name="exchange-online-mailbox"></a>Boîte aux lettres Exchange Online
Une licence De planification est un module Microsoft 365, qui permet à l’organisateur de la réunion de déléguer ses tâches de planification de réunion à son Assistant Planification. Pour que le Scheduler fonctionne, généralement par le biais Microsoft 365 licence, les organisateurs de réunions nécessitent les composants suivants :

- Boîte aux lettres désignée comme boîte aux lettres de l’Assistant Planification
- Licence du scheduleur
- Exchange Online boîte aux lettres et calendrier

Les participants à la réunion n’ont pas besoin de scheduler Microsoft 365 licence.

## <a name="scheduler-end-user-license-requirements"></a>Conditions requises pour la licence de l’utilisateur final du scheduler

Une licence de scheduler nécessite l’une des licences suivantes :

- Microsoft 365 E3, A3, E5, A5
- Business Basic, Business, Business Standard, Business Premium
- Office 365 E1, A1, E3, A3, E5, A5
- Business Essentials, Business Premium
- Exchange Online Plan 1 ou Plan 2. 

> [!Note]

> Le programme de planification Microsoft 365 est disponible dans les environnements internationaux multi-clients en anglais uniquement. **Le programme d’Microsoft 365** n’est pas disponible pour les utilisateurs des :

- Microsoft 365 géré par 21Vianet en Chine
- Microsoft 365 cloud allemand qui utilise le trustee de données German Telekom
- Cloud pour le secteur public, Cloud de la communauté du secteur public, Consommateur, Cloud de la communauté du secteur public Élevé ou DoD

Le programme de planification prend en charge les utilisateurs situés en Allemagne dont l’emplacement des données ne se trouve pas dans le centre de données allemand.
