---
title: Utiliser un script PowerShell pour effectuer une recherche dans le journal d’audit
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom: seo-marvel-apr2020
description: Utilisez un script PowerShell qui exécute l’applet de commande Search-UnifiedAuditLog dans Exchange Online pour effectuer des recherches dans le journal d’audit. Ce script est optimisé pour renvoyer les enregistrements d’un grand jeu d’audits (jusqu’à 50 000). Le script exporte ces enregistrements dans un fichier CSV que vous pouvez afficher ou transformer à l’aide de Power Query dans Excel.
ms.openlocfilehash: 8abea51bb1e7e1fa7bd513bea78708b06da62def
ms.sourcegitcommit: 5db5047c24b56f3af90c2bc5c830a7a13eeeccad
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2021
ms.locfileid: "53341007"
---
# <a name="use-a-powershell-script-to-search-the-audit-log"></a>Utiliser un script PowerShell pour effectuer une recherche dans le journal d’audit

La sécurité, la conformité et l’audit sont désormais une priorité absolue pour les administrateurs informatiques du monde actuel. Microsoft 365 offre plusieurs fonctionnalités intégrées pour aider les organisations à gérer la sécurité, la conformité et l’audit. En particulier, la journalisation d’audit unifiée peut vous aider à examiner les incidents de sécurité et les problèmes de conformité. Vous pouvez récupérer les journaux d’audit à l’aide des méthodes suivantes :

- [L’API Activité de gestion Office 365](/office/office-365-management-api/office-365-management-activity-api-reference)

- L’[outil de recherche dans le journal d’audit](search-the-audit-log-in-security-and-compliance.md) dans le Centre de conformité Microsoft 365

- La commande cmdlet [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) dans Exchange Online PowerShell

Si vous devez récupérer régulièrement les journaux d’audit, vous devez envisager une solution qui utilise l’API Activité de gestion Office 365, car elle peut offrir aux grandes organisations l’évolutivité et les performances nécessaires pour récupérer régulièrement des millions d’enregistrements d’audit. L'utilisation de l'outil de recherche du journal d'audit dans le Centre de conformité Microsoft 365 est un bon moyen de trouver rapidement les enregistrements d'audit pour des opérations spécifiques qui se produisent dans une plage de temps plus courte. L’utilisation de plages de temps plus longues dans l’outil de recherche dans le journal d’audit, en particulier pour les grandes organisations, peut renvoyer trop d’enregistrements pour être facilement gérables ou exportés.

Lorsque vous devez récupérer manuellement des données d’audit pour une enquête ou un incident spécifique, en particulier pour les plages de dates plus longues dans les grandes organisations, il peut être préférable d’utiliser la commande cmdlet **Search-UnifiedAuditLog**. Cet article inclut un script PowerShell qui utilise la commande cmdlet pour récupérer jusqu’à 50 000 enregistrements d’audit, puis les exporte dans un fichier CSV que vous pouvez mettre en forme à l’aide de Power Query dans Excel pour vous aider dans votre révision. L’utilisation du script décrit dans cet article réduit également le risque de délai d’utilisation des recherches importantes dans le journal d’audit dans le service.

## <a name="before-you-run-the-script"></a>Avant d’exécuter l’exemple de code :

- La journalisation d’audit doit être activée pour que votre organisation utilise le script pour renvoyer des enregistrements d’audit. Nous activons par défaut la journalisation d’audit pour les organisations d’entreprise Microsoft 365 et Office 365. Pour vérifier que vous avez activé la recherche dans le journal d’audit pour votre organisation, vous pouvez exécuter la commande suivante dans Exchange Online PowerShell :

  ```powershell
  Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
  ```

  La valeur `True` de la propriété **UnifiedAuditLogIn élémentsenabled** indique que vous avez activé la recherche dans le journal d’audit.

- Vous devez avoir le rôle Journaux d’audit en affichage seul ou Journaux d’audit dans Exchange Online pour exécuter correctement le script. Par défaut, ces rôles sont affectés aux groupes de rôles Gestion de la conformité et Gestion de l’organisation sur la page Autorisations dans le Centre d’administration Exchange. Pour plus d’informations, voir la section « Exigences pour effectuer une recherche dans le journal d’audit » dans [Effectuer des recherches dans le journal d’audit dans le Centre de conformité](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log).

- La fin du script peut prendre un certain temps. Le temps d’exécuter dépend de la plage de dates et de la taille de l’intervalle pour laquelle vous configurez le script afin de récupérer les enregistrements d’audit. Des plages de dates plus grandes et des intervalles plus petits entraînent une durée d’exécution longue. Pour plus d’informations sur la plage de dates et les intervalles, consultez le tableau de l’étape 2.

- L’exemple de script fourni dans cet article n’est pris en charge dans aucun programme de support ou service standard de Microsoft. L’exemple de script est fourni en l’état, sans garantie d’aucune sorte. Microsoft exclut toute garantie implicite, y compris, sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. Vous assumez tous les risques liés à l’utilisation ou à l’exécution de l’exemple de script et de la documentation. En aucun cas, Microsoft, ses auteurs ou toute personne impliquée dans la création, la production ou la livraison du script ne sont responsables de dommages quelconques (y compris, sans limitation, pertes de bénéfices, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser l’exemple de script ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

## <a name="step-1-connect-to-exchange-online-powershell"></a>Étape 1 : Connexion à Exchange Online PowerShell

La première étape consiste à se connecter à Exchange Online PowerShell. Vous pouvez vous connecter à l’aide de l’authentification moderne ou de l’authentification multifacteur. Pour obtenir des instructions, consultez [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="step-2-modify-and-run-the-script-to-retrieve-audit-records"></a>Étape 2 : modifier et exécuter le script pour récupérer les enregistrements d’audit

Une fois que vous êtes connecté à Exchange Online PowerShell, l’étape suivante consiste à créer, modifier et exécuter le script afin de récupérer les données d’audit. Les sept premières lignes du script de recherche dans le journal d’audit contiennent les variables suivantes que vous pouvez modifier pour configurer votre recherche. Consultez le tableau à l’étape 2 pour obtenir une description de ces variables.

1. Enregistrez le texte suivant dans un fichier de script Windows PowerShell à l’aide du suffixe de nom de fichier .ps1. Par exemple, SearchAuditLog.ps1.

   ```powershell
   #Modify the values for the following variables to configure the audit log search.
   $logFile = "d:\AuditLogSearch\AuditLogSearchLog.txt"
   $outputFile = "d:\AuditLogSearch\AuditLogRecords.csv"
   [DateTime]$start = [DateTime]::UtcNow.AddDays(-1)
   [DateTime]$end = [DateTime]::UtcNow
   $record = "AzureActiveDirectory"
   $resultSize = 5000
   $intervalMinutes = 60
   
   #Start script
   [DateTime]$currentStart = $start
   [DateTime]$currentEnd = $start
   
   Function Write-LogFile ([String]$Message)
   {
       $final = [DateTime]::Now.ToUniversalTime().ToString("s") + ":" + $Message
       $final | Out-File $logFile -Append
   }
   
   Write-LogFile "BEGIN: Retrieving audit records between $($start) and $($end), RecordType=$record, PageSize=$resultSize."
   Write-Host "Retrieving audit records for the date range between $($start) and $($end), RecordType=$record, ResultsSize=$resultSize"
   
   $totalCount = 0
   while ($true)
   {
       $currentEnd = $currentStart.AddMinutes($intervalMinutes)
       if ($currentEnd -gt $end)
       {
           $currentEnd = $end
       }
   
       if ($currentStart -eq $currentEnd)
       {
           break
       }
   
       $sessionID = [Guid]::NewGuid().ToString() + "_" +  "ExtractLogs" + (Get-Date).ToString("yyyyMMddHHmmssfff")
       Write-LogFile "INFO: Retrieving audit records for activities performed between $($currentStart) and $($currentEnd)"
       Write-Host "Retrieving audit records for activities performed between $($currentStart) and $($currentEnd)"
       $currentCount = 0
   
       $sw = [Diagnostics.StopWatch]::StartNew()
       do
       {
           $results = Search-UnifiedAuditLog -StartDate $currentStart -EndDate $currentEnd -RecordType $record -SessionId $sessionID -SessionCommand ReturnLargeSet -ResultSize $resultSize
   
           if (($results | Measure-Object).Count -ne 0)
           {
               $results | export-csv -Path $outputFile -Append -NoTypeInformation
   
               $currentTotal = $results[0].ResultCount
               $totalCount += $results.Count
               $currentCount += $results.Count
               Write-LogFile "INFO: Retrieved $($currentCount) audit records out of the total $($currentTotal)"
   
               if ($currentTotal -eq $results[$results.Count - 1].ResultIndex)
               {
                   $message = "INFO: Successfully retrieved $($currentTotal) audit records for the current time range. Moving on!"
                   Write-LogFile $message
                   Write-Host "Successfully retrieved $($currentTotal) audit records for the current time range. Moving on to the next interval." -foregroundColor Yellow
                   ""
                   break
               }
           }
       }
       while (($results | Measure-Object).Count -ne 0)
   
       $currentStart = $currentEnd
   }
   
   Write-LogFile "END: Retrieving audit records between $($start) and $($end), RecordType=$record, PageSize=$resultSize, total count: $totalCount."
   Write-Host "Script complete! Finished retrieving audit records for the date range between $($start) and $($end). Total count: $totalCount" -foregroundColor Green
   ```

2. Modifiez les variables répertoriées dans le tableau suivant pour configurer les critères de recherche. Le script inclut des exemples de valeurs pour ces variables, mais vous devez les modifier (sauf indication contraire) pour répondre à vos exigences spécifiques.

   <br>

   ****

   |Variable|Exemple de valeur|Description|
   |---|---|---|
   |`$logFile`|"d:\temp\AuditSearchLog.txt"|Indique le nom et l’emplacement du fichier journal qui contient des informations sur la progression de la recherche dans le journal d’audit effectuée par le script. Le script écrit les horodatages UTC sur le fichier journal.|
   |`$outputFile`|"d:\temp\AuditRecords.csv"|Indique le nom et l’emplacement du fichier CSV contenant les enregistrements d’audit renvoyés par le script.|
   |`[DateTime]$start` et `[DateTime]$end`|[DateTime]::UtcNow.AddDays(-1) <br/>[DateTime]::UtcNow|Spécifie la plage de dates pour la recherche dans le journal d’audit. Le script retourne les enregistrements des activités d’audit qui se sont produites dans la plage de dates spécifiée. Par exemple, pour renvoyer les activités effectuées en janvier 2021, vous pouvez utiliser une date de début de `"2021-01-01"` et une date de fin de `"2021-01-31"` (n’oubliez pas d’entourer les valeurs de guillemets doubles) La valeur d’exemple dans le script renvoie les enregistrements des activités effectuées au cours des 24 heures précédentes. si vous n’incluez pas d’horodatage dans la valeur, l’horodatage par défaut est 00:00 (minuit) pour la date spécifiée.|
   |`$record`|« AzureActiveDirectory »|Spécifie le type d’enregistrement des activités d’audit (également *opérations*) à rechercher. Cette propriété indique le service ou la fonctionnalité dans qui une activité a été déclenchée. Pour obtenir la liste des types d’enregistrement que vous pouvez utiliser pour cette variable, consultez [Type d’enregistrement journal d’audit](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype). Vous pouvez utiliser le nom du type d’enregistrement ou la valeur ENUM. <br/><br/>**Conseil :** pour renvoyer les enregistrements d'audit pour tous les types d'enregistrements, utilisez la valeur `$null` (sans guillemets doubles).|
   |`$resultSize`|5000|Spécifie le nombre de résultats renvoyés chaque fois que la commande cmdlet **Search-UnifiedAuditLog** est appelée par le script (appelé *jeu de résultats*). La valeur de 5 000 est la valeur maximale prise en charge par la commande cmdlet. Laissez cette valeur telle qu’elle est.|
   |`$intervalMinutes`|60|Pour dépasser la limite de 5 000 enregistrements renvoyés, cette variable prend la plage de données que vous avez spécifiée et la découpe en intervalles de temps plus courts. Chaque intervalle, et non la plage de dates entière, est soumis à la limite de sortie de l’enregistrement de 5 000 de la commande. La valeur par défaut de 5 000 enregistrements par intervalle de 60 minutes dans la plage de dates doit être suffisante pour la plupart des organisations. Toutefois, si le script renvoie une erreur qui indique `maximum results limitation reached`, diminuez l’intervalle de temps (par exemple, à 30 minutes, voire 15 minutes) et réexécutez le script.|
   ||||

   La plupart des variables répertoriées dans le tableau précédent correspondent aux paramètres de la commande cmdlet **Search-UnifiedAuditLog**. Pour plus d'informations sur ces paramètres, voir [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

3. Sur votre ordinateur local, ouvrez Windows PowerShell et allez dans le dossier dans lequel vous avez enregistré le script modifié.

4. Dans Exchange Online PowerShell, exécutez le script suivant par exemple :

   ```powershell
   .\SearchAuditLog.ps1
   ```

Le script affiche les messages de progression pendant son exécution. Une fois l’exécution du script terminée, il crée le fichier journal et le fichier CSV qui contient les enregistrements d’audit et les enregistre dans les dossiers définis par les variables `$logFile` et `$outputFile`.

> [!IMPORTANT]
> Il existe une limite de 50 000 pour le nombre maximal d’enregistrements d’audit renvoyés chaque fois que vous exécutez ce script. Si vous exécutez ce script et qu’il renvoie 50 000 résultats, il est probable que les enregistrements d’audit pour les activités qui se sont produites dans la plage de dates n’ont pas été inclus. Dans ce cas, nous vous recommandons de diviser la plage de dates en plus petites durées, puis de réexécuter le script pour chaque plage de dates. Par exemple, si une plage de dates de 90 jours renvoie 50 000 résultats, vous pouvez réexécuter le script deux fois, une fois pour les 45 premiers jours de la plage de dates, puis de nouveau pour les 45 prochains jours.

## <a name="step-3-format-and-view-the-audit-records"></a>Étape 3 : formater et afficher les enregistrements d’audit

Après avoir exécuté le script et exporté les enregistrements d’audit dans un fichier CSV, vous souhaitez peut-être mettre en forme le fichier CSV afin de faciliter l’examen et l’analyse des enregistrements d’audit. Une des façons de cela consiste à transformer JavaScript Object Notation Power Query dans Excel pour fractionner chaque propriété de l’objet JSON dans la colonne **AuditData** dans sa propre colonne. Pour obtenir des instructions détaillées, consultez « Étape 2 : mise en forme du journal d’audit exporté à l’aide de l’Éditeur Power Query » dans [Exporter, configurer et afficher des enregistrements du journal d’audit](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).
