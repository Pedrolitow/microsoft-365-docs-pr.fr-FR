---
title: Configuration de Scheduler pour Microsoft 365.
ms.author: v-aiyengar
author: AshaIyengar21
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
ms.localizationpriority: medium
description: Configuration de Scheduler pour Microsoft 365.
ms.openlocfilehash: ef377393134e4d8028ab0e6e40ddcc3647f60695
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953845"
---
# <a name="setting-up-scheduler-for-microsoft-365"></a>Configuration du Planificateur pour Microsoft 365

Les administrateurs locataires doivent configurer une boîte aux lettres d’assistant Planificateur et obtenir des licences Scheduler pour les organisateurs de réunion afin d’activer le planificateur pour Microsoft 365 service. 

## <a name="licensing"></a>Gestion des licences

En savoir plus : [Scheduler pour la gestion des licences Microsoft 365](https://www.microsoft.com/microsoft-365/meeting-scheduler-pricing)

> [!NOTE]
> Les participants à la réunion n’ont pas besoin d’une licence Scheduler ou Microsoft 365.
>
> La boîte aux lettres de l’Assistant Planificateur ne nécessite pas de Microsoft 365 ou de licence Scheduler.

## <a name="prerequisites"></a>Configuration requise

|Conditions préalables|Description|
|---|---|
|Boîte aux lettres d’assistant Planificateur pour le locataire |Boîte aux lettres de ressources de type d’équipement Exchange qui fait office de boîte aux lettres d’assistant Planificateur pour que votre locataire envoie et reçoive des e-mails vers et depuis Cortana. Tous les e-mails envoyés à Cortana sont conservés dans la boîte aux lettres Cortana de votre locataire en fonction de votre stratégie de rétention. La boîte aux lettres de l’Assistant Planificateur est généralement nommée « Cortana » ou « Cortana Scheduler », car tous les e-mails de l’assistant sont signés Cortana. <ul><li>Créer un type d’équipement Exchange boîte aux lettres de ressources</li><li>Nommez le nom complet de la boîte aux lettres et l’adresse `Cortana <cortana@yourdomain.com>` SMTP principale ou `Cortana Scheduler <cortana.scheduler@yourdomain.com>`.</li></ul> <br/> **Note:** La boîte aux lettres de l’Assistant Planificateur ne nécessite pas de Microsoft 365 ou de licence Scheduler.|
|Boîte aux lettres Exchange Online |Les organisateurs de réunion doivent disposer d’une boîte aux lettres et d’un calendrier Exchange Online généralement dans le cadre de leur licence Microsoft 365. En outre, les organisateurs de réunion doivent disposer d’une licence Scheduler. La licence Scheduler permet à l’Assistant Planificateur d’utiliser la boîte aux lettres et le calendrier de l’organisateur de la réunion pour planifier des réunions pour eux. <br/><br/> Consultez Scheduler pour Microsoft 365 pour obtenir des informations sur les licences et les tarifs. <br/><br/> **Note:** Les participants à la réunion n’ont pas besoin d’une licence Scheduler ou Microsoft 365. Les participants à la réunion peuvent être internes ou externes au locataire. Les participants à la réunion ont uniquement besoin d’accéder à une adresse e-mail.|

## <a name="setting-up-the-scheduler-assistant-mailbox"></a>Configuration de la boîte aux lettres de l’Assistant Planificateur

La boîte aux lettres de l’assistant planificateur est une boîte aux lettres de type d’équipement Exchange qui ne nécessite pas de licence Microsoft 365 ou Scheduler supplémentaire. Le nom complet et l’adresse SMTP principale de la boîte aux lettres doivent contenir Cortana, car tous les e-mails de l’Assistant Planificateur sont signés Cortana (c’est-à-dire, `Cortana <cortana@yourdomain.com>` ou `Cortana Scheduler <cortana.scheduler@yourdomain.com>`). Une fois que la boîte aux lettres de l’Assistant Planificateur a été créée, vous devez désigner la boîte aux lettres comme boîte aux lettres de l’Assistant Planificateur. Une fois que vous avez désigné la boîte aux lettres de l’Assistant Planificateur, Cortana sera disponible pour planifier des réunions pour le compte de vos utilisateurs.

- Utilisez la Centre d'administration Microsoft 365 pour créer une boîte aux lettres utilisateur. Une stratégie de rétention de 30 jours est recommandée. 
- Utilisez le nom Cortana dans l’adresse SMTP principale de votre boîte aux lettres. Des noms tels que `Cortana@yourdomain.com`, `CortanaScheduler@contoso.com`ou `Cortana.Scheduler@yourdomain.com` sont recommandés.

## <a name="designate-the-mailbox-as-the-scheduler-assistant"></a>Désigner la boîte aux lettres en tant qu’Assistant Planificateur

Une fois qu’une boîte aux lettres unique pour Cortana Scheduler a été créée, vous devez désigner la boîte aux lettres pour Microsoft 365 formellement. Une fois que vous avez désigné la boîte aux lettres Cortana Scheduler, elle sera disponible pour planifier des réunions pour le compte de vos utilisateurs.

### <a name="connect-to-powershell"></a>Connecter à PowerShell

Utilisez la Centre d'administration Microsoft 365 pour créer une boîte aux lettres utilisateur. Une stratégie de rétention de 30 jours est recommandée.
Utilisez le nom Cortana dans l’adresse SMTP principale de votre boîte aux lettres. Des noms tels que `Cortana@yourdomain.com`, `CortanaScheduler@contoso.com`ou `Cortana.Scheduler@yourdomain.com` sont recommandés.

```PowerShell
$domain="yourdomain.com"
$tenantAdmin="<tenantadmin>@$domain"
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $tenantAdmin
```

### <a name="create-the-scheduler-assistant-mailbox"></a>Créer la boîte aux lettres de l’Assistant Planificateur

```PowerShell
New-Mailbox -Name Cortana -Organization $domain -DisplayName "Cortana Scheduler" -Equipment 
Set-CalendarProcessing Cortana@$domain -DeleteNonCalendarItems $false 
```

### <a name="designate-the-scheduler-assistant-mailbox"></a>Désigner la boîte aux lettres de l’Assistant Planificateur

```PowerShell
Set-mailbox cortana@$domain -SchedulerAssistant:$true
```

Après avoir exécuté cette commande « set » sur la boîte aux lettres de l’assistant Cortana Scheduler, une nouvelle « PersistedCapability » est définie sur la boîte aux lettres pour noter que cette boîte aux lettres est « SchedulerAssistant ».

> [!NOTE]
> Pour savoir comment connecter votre organisation à PowerShell, consultez : [Connecter à Microsoft 365 avec PowerShell](/microsoft-365/enterprise/connect-to-microsoft-365-powershell)

### <a name="verifying-the-scheduler-assistant-mailbox"></a>Vérification de la boîte aux lettres de l’Assistant Planificateur

Pour vérifier que la boîte aux lettres de l’Assistant Planificateur a été créée

```PowerShell
Get-CalendarProcessing cortana@$domain | fl DeleteNonCalendarItems
```

Le résultat doit être « false ».

```PowerShell
Get-Mailbox -Identity cortana@$domain | fl *type*
```

Le résultat doit être

- ResourceType : Équipement
- RecipientType distant : Aucun
- RecipientType : UserMailbox
- RecipientTypeDetails: EquipmentMailbox

### <a name="to-discover-which-mailbox-is-the-scheduler-assistant-mailbox"></a>Pour découvrir quelle boîte aux lettres est la boîte aux lettres de l’Assistant Planificateur

```PowerShell
Get-Mailbox -ResultSize Unlimited | where {$_.PersistedCapabilities -Match "SchedulerAssistant"}
```

> [!IMPORTANT]
> L’approvisionnement complet de la boîte aux lettres de l’Assistant Planificateur peut prendre plusieurs heures pour définir la fonctionnalité SchedulerAssistant.

## <a name="exchange-online-mailbox"></a>Boîte aux lettres Exchange Online

Une licence scheduler est un module complémentaire à Microsoft 365, qui permet à l’organisateur de la réunion de déléguer ses tâches de planification de réunion à son assistant planificateur. En plus de désigner une boîte aux lettres comme boîte aux lettres d’assistant Planificateur, les organisateurs de réunions auront également besoin d’une licence Scheduler et Exchange Online boîte aux lettres et calendrier, généralement via Microsoft 365 licence pour que Scheduler fonctionne. Les participants à la réunion n’ont pas besoin d’une licence Scheduler ou d’une licence Microsoft 365.

Pour acheter le module complémentaire Scheduler, vous avez besoin de l’une des licences suivantes :

- Microsoft 365 E3, A3, E5, A5
- Business Basic, Business, Business Standard, Business Premium
- Office 365 E1, A1, E3, A3, E5, A5
- Business Essentials, Business Premium
- Exchange Online licence Plan 1 ou Plan 2.

> [!NOTE]
> Scheduler pour Microsoft 365 est disponible uniquement en anglais dans les environnements multilocataires du monde entier. **Scheduler pour Microsoft 365** n’est pas disponible pour les utilisateurs de :
>
> - Microsoft 365 exploité par 21Vianet en Chine
> - Microsoft 365 avec le cloud allemand qui utilise le syndic de données German Telekom
> - Cloud du secteur public, y compris Cloud de la communauté du secteur public, consommateur, Cloud de la communauté du secteur public Élevé ou DoD
>
> Scheduler prend en charge les utilisateurs en Allemagne dont l’emplacement des données n’est pas le centre de données allemand.
