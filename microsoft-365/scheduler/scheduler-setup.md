---
title: Configuration du Scheduler pour Microsoft 365.
ms.author: v-aiyengar
author: AshaIyengar21
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
ms.localizationpriority: medium
description: Configuration du Scheduler pour Microsoft 365.
ms.openlocfilehash: 3315c362a6e6ae1eb4fa9bf54d388a89dd667136
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60208036"
---
# <a name="setting-up-scheduler-for-microsoft-365"></a>Configuration du Planificateur pour Microsoft 365

Les administrateurs clients doivent configurer une boîte aux lettres de l’Assistant Planification et obtenir des licences de scheduler pour les organisateurs de réunions afin d’activer le Scheduler pour Microsoft 365 service. 

## <a name="licensing"></a>Licences

En savoir plus : [Scheduler for Microsoft 365 licensing](https://www.microsoft.com/microsoft-365/meeting-scheduler-pricing)

> [!Note]
> Les participants à la réunion n’ont pas besoin d’une licence scheduler Microsoft 365 licence. <br>La boîte aux lettres de l’Assistant Scheduler ne nécessite pas de licence Microsoft 365 ou scheduler.

## <a name="prerequisites"></a>Configuration requise

| Conditions préalables | Description |
|-------------------|-------------|
|Boîte aux lettres de l’Assistant Planification pour le client |Boîte aux Exchange ressource de type ressource de type équipement qui agit comme la boîte aux lettres de l’Assistant Planification pour que votre client envoie et reçoit des messages électroniques vers et depuis Cortana. Tous les messages électroniques envoyés Cortana sont conservés dans la boîte aux lettres Cortana de votre client en fonction de votre stratégie de rétention. La boîte aux lettres de l’Assistant Planification est généralement nommée « Cortana » ou « Cortana Scheduler », car tous les messages électroniques de l’Assistant seront signés Cortana.<ul><li>Créer un type d’Exchange boîte aux lettres de ressources</li><li>Nommez le nom complet de la boîte aux lettres et l’adresse SMTP `Cortana <cortana@yourdomain.com>` principale ou `Cortana Scheduler <cortana.scheduler@yourdomain.com>` .</li></ul>**Remarque :** La boîte aux lettres de l’Assistant Scheduler ne nécessite pas de licence Microsoft 365 ou scheduler.|
|Boîte aux lettres Exchange Online |Les organisateurs de réunion doivent avoir une boîte Exchange Online et un calendrier en général dans le cadre de leur licence Microsoft 365 réunion. En outre, les organisateurs de réunion doivent avoir une licence De planification. La licence Scheduler permet à l’Assistant Scheduler d’utiliser la boîte aux lettres et le calendrier de l’organisateur de la réunion pour planifier des réunions à leur place.<br/><br/> Voir Scheduler for Microsoft 365 for licensing and pricing information.  <br/><br/>**Remarque :** Les participants à la réunion n’ont pas besoin d’une licence scheduler Microsoft 365 licence. Les participants à la réunion peuvent être internes ou externes au client. Les participants à la réunion ont uniquement besoin d’accéder à une adresse de messagerie.|


## <a name="setting-up-the-scheduler-assistant-mailbox"></a>Configuration de la boîte aux lettres de l’Assistant Planification

La boîte aux lettres de l’Assistant Exchange de planification est une boîte aux lettres de type équipement qui ne nécessite aucune licence Microsoft 365 ou scheduler supplémentaire. Le nom d’affichage et l’adresse SMTP principale de la boîte aux lettres doivent contenir Cortana, car tous les messages électroniques provenant de l’Assistant Planification seront signés Cortana (c’est-à-dire, `Cortana <cortana@yourdomain.com>` ou `Cortana Scheduler <cortana.scheduler@yourdomain.com>` ). Une fois la boîte aux lettres de l’Assistant Planification créée, vous devez la désigner comme boîte aux lettres de l’Assistant Planification. Une fois que vous avez désigné la boîte aux lettres de l’Assistant Planification, Cortana sera disponible pour planifier des réunions pour le compte de vos utilisateurs.

- Utilisez le Centre d'administration Microsoft 365 pour créer une boîte aux lettres utilisateur. Une stratégie de rétention de 30 jours est recommandée. 
- Utilisez le nom Cortana dans l’adresse SMTP principale de votre boîte aux lettres. Les noms tels `Cortana@yourdomain.com` que , ou sont `CortanaScheduler@contoso.com` `Cortana.Scheduler@yourdomain.com` recommandés.

## <a name="designate-the-mailbox-as-the-scheduler-assistant"></a>Désigner la boîte aux lettres en tant qu’Assistant De planification

Une fois qu’une boîte aux lettres unique Cortana Scheduler a été créée, vous devez désigner la boîte aux lettres Microsoft 365 officiellement. Une fois que vous avez Cortana boîte aux lettres du Cortana, vous pouvez planifier des réunions pour le compte de vos utilisateurs.

#### <a name="connect-to-powershell"></a>Connecter à PowerShell

Utilisez le Centre d'administration Microsoft 365 pour créer une boîte aux lettres utilisateur. Une stratégie de rétention de 30 jours est recommandée.
Utilisez le nom Cortana dans l’adresse SMTP principale de votre boîte aux lettres. Les noms tels `Cortana@yourdomain.com` que , ou sont `CortanaScheduler@contoso.com` `Cortana.Scheduler@yourdomain.com` recommandés.

```PowerShell
$domain="yourdomain.com"
$tenantAdmin="<tenantadmin>@$domain"
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $tenantAdmin
```

#### <a name="create-the-scheduler-assistant-mailbox"></a>Créer la boîte aux lettres de l’Assistant De planification

```PowerShell
New-Mailbox -Name Cortana -Organization $domain -DisplayName "Cortana Scheduler" -Equipment 
Set-CalendarProcessing Cortana@$domain -DeleteNonCalendarItems $false 
```
    
#### <a name="designate-the-scheduler-assistant-mailbox"></a>Désigner la boîte aux lettres de l’Assistant De planification

```PowerShell
Set-mailbox cortana@$domain -SchedulerAssistant:$true
```

Après l’exécution de cette commande « set » sur la boîte aux lettres de l’Assistant de planification Cortana, une nouvelle fonctionnalité « PersistedCapability » est définie sur la boîte aux lettres pour noter que cette boîte aux lettres est « SchedulerAssistant ».

> [!Note]
> Pour découvrir comment connecter votre organisation à PowerShell, voir : [Connecter à Microsoft 365 avec PowerShell](/microsoft-365/enterprise/connect-to-microsoft-365-powershell)

### <a name="verifying-the-scheduler-assistant-mailbox"></a>Vérification de la boîte aux lettres de l’Assistant Planification

Pour vérifier que la boîte aux lettres de l’Assistant Planification a été créée

```PowerShell
Get-CalendarProcessing cortana@$domain | fl DeleteNonCalendarItems
```

Le résultat doit être « false ».

<br>

```PowerShell
Get-Mailbox -Identity cortana@$domain | fl *type*
```

Le résultat doit être
- ResourceType: Equipment
- RecipientType distant : Aucun
- RecipientType : UserMailbox
- RecipientTypeDetails : EquipmentMailbox

<br/>

### <a name="to-discover-which-mailbox-is-the-scheduler-assistant-mailbox"></a>Pour découvrir quelle boîte aux lettres est la boîte aux lettres de l’Assistant Planification

```PowerShell
Get-Mailbox -ResultSize Unlimited | where {$_.PersistedCapabilities -Match "SchedulerAssistant"}
```

> [!Important]
> L’approvisionnement complet de la boîte aux lettres de l’Assistant Planification peut prendre plusieurs heures pour définir la fonctionnalité SchedulerAssistant.


## <a name="exchange-online-mailbox"></a>Boîte aux lettres Exchange Online

Une licence De planification est un module Microsoft 365, qui permet à l’organisateur de la réunion de déléguer ses tâches de planification de réunion à son Assistant Planification. Outre la désignation d’une boîte aux lettres en tant que boîte aux lettres de l’Assistant Planification, les organisateurs de réunions ont également besoin d’une licence de planification et d’une boîte aux lettres et d’un calendrier Exchange Online, généralement via une licence Microsoft 365 pour que le Scheduler fonctionne. Les participants à la réunion n’ont pas besoin d’une licence De planification ou d Microsoft 365 licence.

Pour acheter le module de planification, vous avez besoin de l’une des licences suivantes :

- Microsoft 365 E3, A3, E5, A5
- Business Basic, Business, Business Standard, Business Premium
- Office 365 E1, A1, E3, A3, E5, A5
- Business Essentials, Business Premium
- Exchange Online Plan 1 ou Plan 2. 

> [!Note]
> Le programme de planification Microsoft 365 est disponible dans les environnements internationaux multi-clients en anglais uniquement. **Le programme d’Microsoft 365** n’est pas disponible pour les utilisateurs des :
> 
> - Microsoft 365 géré par 21Vianet en Chine
> - Microsoft 365 cloud allemand qui utilise le trustee de données German Telekom
> - Cloud pour le secteur public, Cloud de la communauté du secteur public, Consommateur, Cloud de la communauté du secteur public Élevé ou DoD
> 
> Scheduler prend en charge les utilisateurs situés en Allemagne dont l’emplacement de données n’est pas le centre de données allemand.
