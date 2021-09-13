---
title: Utiliser l’audit avancé pour analyser des comptes compromis
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Utilisez l’action d’audit de boîte aux lettres MailItemsAccessed pour effectuer des enquêtes légales sur des comptes d'utilisateur compromis.
ms.openlocfilehash: b0fac6e4ac5d6cc4bb20b6853cb67cf301c6295a
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59177972"
---
# <a name="use-advanced-audit-to-investigate-compromised-accounts"></a>Utiliser l’audit avancé pour analyser des comptes compromis

Un compte d’utilisateur compromis (également appelé *prise de contrôle de compte*) est un type d’attaque permettant à une personne malveillante d’accéder à un compte utilisateur et d'agir à sa place. Ces types d’attaques peuvent parfois occasionner des dommages plus importants que ceux que la personne malveillante a initialement prévu. Lors de l'analyse de comptes de messagerie compromis, considérez que beaucoup plus de données de courrier sont compromises par rapport à ce qui peut être indiqué en suivant la présence réelle de l’attaquant. Selon le type de données figurant dans les messages électroniques, vous devez supposer que les informations sensibles ont été compromises, ou font face à des sanctions pour infraction à un règlement, sauf si vous pouvez prouver que les informations sensibles n’ont pas été exposées. Par exemple, les organisations réglementées par le HIPAA sont confrontées à des amendes importantes s’il s'avère que des informations sur la santé des patients ont été exposées. Dans ces cas, il est peu probable que les personnes malveillantes s'intéressent aux dossiers contenant des renseignements médicaux protégés (PHI), mais les organisations doivent tout de même signaler les violations de données, sauf si elles peuvent prouver le cas contraire.

Pour faciliter votre enquête sur des comptes de courrier compromis, nous auditons désormais les accès aux données de messages par protocoles de courrier et clients avec l’action d’audit de boîte aux lettres *MailItemsAccessed*. Cette nouvelle action d’audit aidera les investigateurs à mieux comprendre les violations de données de messagerie et vous permettra d'identifier l’étendue des compromissions de certains éléments de courrier précis susceptibles d’être corrompus. La défendabilité légale est l'objectif de l'emploi de cette nouvelle action d'audit pour affirmer que des données précises d'un e-mail ne sont pas compromise. Si une personne malveillante accède à un message spécifique, Exchange Online audite l’événement, même si rien n'indique que le courrier a été véritablement lu.

## <a name="the-mailitemsaccessed-mailbox-auditing-action"></a>Action d’audit de boîte aux lettres MailItemsAccessed

La nouvelle action MailItemsAccessed fait partie de la récente fonctionnalité d’[audit avancé](advanced-audit.md)t. Elle fait partie de l'[audit de boîte aux lettres Exchange](/office365/securitycompliance/enable-mailbox-auditing#mailbox-auditing-actions) et est activée par défaut pour les utilisateurs auxquels une licence Office 365 ou Microsoft 365 E5 est attribuée ou pour les organisations disposant d’un abonnement au composant Microsoft 365 E5 Conformité.

L’action d’audit de boîte aux lettres MailItemsAccessed englobe tous les protocoles de messagerie : POP, IMAP, MAPI, EWS, Exchange ActiveSync et REST. Il prend en charge également les deux types d’accès aux courriers : *synchronisation* et *liaison*.

### <a name="auditing-sync-access"></a>Audit de l’accès à la synchronisation

Les opérations de synchronisation sont uniquement enregistrées lorsqu’une boîte aux lettres est consultée par une version de bureau du client Outlook pour Windows ou Mac. Pendant l’opération de synchronisation, ces clients téléchargent généralement un grand nombre de courriers du cloud vers un ordinateur local. Le volume d’audit pour les opérations de synchronisation est important. Par conséquent, au lieu de générer un enregistrement d’audit par courrier synchronisé, un événement d’audit est tout simplement créé pour le dossier de courrier contenant les éléments qui ont été synchronisés. Ainsi, l’hypothèse est que *tous* les éléments de courrier présents dans le dossier synchronisé sont corrompus. Le type d’accès est enregistré dans le champ OperationProperties de l’enregistrement d’audit.

Pour consulter un exemple d’affichage du type d’accès à la synchronisation dans un enregistrement d’audit, voir l’étape 2 de la section [Utiliser les enregistrements d’audit MailItemsAccessed pour des investigations criminalistiques](#use-mailitemsaccessed-audit-records-for-forensic-investigations).

### <a name="auditing-bind-access"></a>Audit de l’accès liaison

Une opération de liaison consiste en un accès individuel à un message électronique. Pour l’accès liaison, l’InternetMessageId des messages individuels est enregistré dans l’enregistrement d’audit. L’action d’audit MailItemsAccessed enregistre les opérations de liaison, puis les rassemble dans un seul enregistrement d’audit. Toutes les opérations de liaison effectuées au cours d’un intervalle de deux minutes sont regroupées dans un seul enregistrement d’audit dans le champ Dossiers de la propriété AuditData. Les messages consultés sont identifiés par leur InternetMessageId. Le nombre d’opérations de liaison regroupées dans l’enregistrement s’affiche dans le champ OperationCount de la propriété AuditData.

Pour consulter un exemple d’affichage du type d’accès à la liaison dans un enregistrement d’audit, voir l’étape 4 de la section [Utiliser les enregistrements d’audit MailItemsAccessed pour des investigations criminalistiques](#use-mailitemsaccessed-audit-records-for-forensic-investigations).

### <a name="throttling-of-mailitemsaccessed-audit-records"></a>Limitation des enregistrements d’audit MailItemsAccessed

Si plus de 1 000 enregistrements d’audit MailItemsAccessed sont générés en moins de 24 heures, Exchange Online stoppe la génération des enregistrements d’audit pour l’activité MailItemsAccessed. Lorsqu’une boîte aux lettres est limitée, l’activité MailItemsAccessed n’est pas enregistrée durant les 24 heures suivant la limitation de la boîte aux lettres. Si cela se produit, il est possible que la boîte aux lettres ait été compromise au cours de cette période. L’enregistrement de l’activité MailItemsAccessed reprend après un délai de 24 heures.

Voici quelques éléments à se rappeler sur la limitation :

- Moins de 1 % des boîtes aux lettres sont limitées dans Exchange Online
- Lorsqu’une boîte aux lettres est limitée, seuls les enregistrements d’audit pour l’activité MailItemsAccessed ne sont pas audités. Les autres actions d’audit de boîte aux lettres ne sont pas affectées.
- Les boîtes aux lettres sont uniquement limitées pour les opérations de liaison. Les enregistrements d’audit pour les opérations de synchronisation ne sont pas limités.
- Si une boîte aux lettres est limitée, vous pouvez considérer qu’une activité MailItemsAccessed n’a pas été enregistrée dans les journaux d’audit.

Pour consulter un exemple d’affichage de la propriété IsThrottled dans un enregistrement d’audit, voir l’étape 1 de la section [Utiliser les enregistrements d’audit MailItemsAccessed pour des investigations criminalistiques](#use-mailitemsaccessed-audit-records-for-forensic-investigations).

## <a name="use-mailitemsaccessed-audit-records-for-forensic-investigations"></a>Utiliser les enregistrements d’audit MailItemsAccessed pour des enquêtes légales

L’audit de boîte aux lettres génère des enregistrements d’audit pour l’accès aux courriers afin d'être certain que les messages n’ont pas été compromis. En conséquence, si des circonstances ne permettent pas d'affirmer qu'un accès aux données a eu lieu, nous supposons qu'il s'est produit en enregistrant toute l'activité d'accès au courrier.

L'enregistrement à l'aide d’audit MailItemsAccessed à des fins d’enquête légale est généralement effectué après la résolution d’une violation de données et l'éviction de la personne malveillante. Pour commencer votre enquête, vous devez identifier les boîtes aux lettres qui ont été compromises et déterminer la période durant laquelle la personne malveillante a eu accès aux boîtes aux lettres de votre organisation. Puis vous pouvez utiliser les applets de commande **Search-UnifiedAuditLog** ou **Search-MailboxAuditLog** dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) pour rechercher les enregistrements d’audit correspondant à la violation de données.

Vous pouvez exécuter l’une des commandes suivantes pour rechercher les enregistrements d’audit MailItemsAccessed :

**Journal d'audit unifié** :

```powershell
Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000
```

**Journal d'audit de boîte aux lettres** :

```powershell
Search-MailboxAuditLog -Identity <user> -StartDate 01/06/2020 -EndDate 01/20/2020 -Operations MailItemsAccessed -ResultSize 1000 -ShowDetails
```

> [!TIP]
> La principale différence entre ces deux applets de commande est que vous pouvez utiliser l’applet de commande **Search-UnifiedAuditLog** pour rechercher des enregistrements d’audit pour l’activité effectuée par un ou plusieurs utilisateurs. La raison est que *UserIds* est un paramètre à valeurs multiples. L’applet de commande **Search-MailboxAuditLog** fait une recherche dans le journal d’audit de boîtes aux lettres d'un utilisateur unique.

Voici les étapes à suivre pour utiliser les enregistrements d’audit MailItemsAccessed afin d'enquêter sur l'attaque d'un utilisateur compromis. Chacune de ces étapes présente la syntaxe de commande pour les applets de commande **Search-UnifiedAuditLog** ou **MailboxAuditLog**.

1. Vérifiez si la boîte aux lettres a été limitée. Dans l'affirmative, cela signifie que certains enregistrements d’audit de boîte aux lettres n’ont pas été enregistrés. Dans le cas où les enregistrements d’audit affichent le terme « IsThrottled » sur la valeur « True », vous devez supposer qu’au terme de la période de 24 heures suivant la création de l'enregistrement, l’accès à la boîte aux lettres n’a pas été audité et que toutes les données de courrier ont été compromises.

   Pour effectuer la recherche des enregistrements MailItemsAccessed dans lesquels la boîte aux lettres a été limitée, exécutez la commande suivante :

   **Journal d'audit unifié** :

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"IsThrottled","Value":"True"*'} | FL
   ```

   **Journal d'audit de boîte aux lettres** :

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*IsThrottled:True*"} | FL
   ```

2. Vérifier les activités de synchronisation. Si une personne malveillante utilise un client de courrier pour télécharger les messages d'une boîte aux lettres, il peut déconnecter l’ordinateur d’internet et accéder aux messages en local sans interagir avec le serveur. L'audit de boîtes aux lettres ne peut donc pas auditer ces activités.

   Pour effectuer la recherche des enregistrements MailItemsAccessed dans lesquels les courriers ont été consultés par une opération de synchronisation, exécutez la commande suivante :

   **Journal d'audit unifié** :

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 02/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"MailAccessType","Value":"Sync"*'} | FL
   ```

   **Journal d'audit de boîte aux lettres** :

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*MailAccessType:Sync*"} | FL
   ```

3. Vérifiez les activités de synchronisation pour déterminer si l’une d'entre elles s’est produite dans le même contexte que celle utilisée par l’attaquant qui a accédé à la boîte aux lettres. Le contexte est identifié et peut être distingué par l’adresse IP de l’ordinateur client utilisé pour accéder à la boîte aux lettres et au protocole de courrier. Pour plus d’informations, voir la section [Identification des contextes d’accès à d’autres enregistrements d’audit](#identifying-the-access-contexts-of-different-audit-records).

   Utilisez les propriétés répertoriées ci-dessous pour effectuer votre enquête. Ces propriétés sont situées dans la propriété AuditData ou OperationProperties. Si l’une des synchronisations se produit dans le même contexte que l’activité de la personne malveillante, vous devez supposer que l’attaquant a synchronisé tous les éléments de courrier vers leur client, ce qui signifie que la boîte aux lettres entière a probablement été compromise.

   <br>

   ****

   |Propriété|Description|
   |---|---|
   |ClientInfoString|Décrit le protocole, le client (inclut la version).|
   |ClientIPAddress|Adresse IP de l’ordinateur client.|
   |SessionId|ID de session vous permettant de différencier les activités de personnes malveillantes de celles des utilisateur au quotidien sur le même compte (dans le cas d’un compte compromis)|
   |UserId|Nom d’utilisateur principal (UPN) de l’utilisateur lisant le message.|
   |

4. Vérifier les activités de liaison. Après avoir suivi les étapes 2 et 3, vous êtes certain que tous les autres accès aux courriers électroniques par l’attaquant sont enregistrés dans les enregistrements d’audit MailItemsAccessed ayant une propriété MailAccessType avec la valeur « Liaison ».

   Pour effectuer la recherche des enregistrements MailItemsAccessed dans lesquels les courriers ont été consultés par une opération de liaison, exécutez la commande suivante.

   **Journal d'audit unifié** :

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"MailAccessType","Value":"Bind"*'} | FL
   ```

   **Journal d'audit de boîte aux lettres** :

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*MailAccessType:Bind*"} | FL
   ```

   Les messages électroniques consultés sont identifiés par leur ID de message Internet. Vous pouvez également vérifier si les enregistrements d’audit ont le même contexte que ceux destinés à d’autres activités de l’attaquant. Pour plus d’informations, voir la section [Identification des contextes d’accès à d’autres enregistrements d’audit](#identifying-the-access-contexts-of-different-audit-records).

   Vous pouvez utiliser les données d’audit pour les opérations de liaison de deux façon différentes :

   - Accéder ou recueillir tous les courriers électroniques auxquels la personne malveillante a eu accès en utilisant l’InternetMessageId pour les retrouver, puis vérifiez si l’un de ces messages contient des informations sensibles.
   - Utilisez l’InternetMessageId pour rechercher des enregistrements d’audit relatifs à un groupe de courriers électroniques potentiellement sensibles. Ceci est utile si un petit nombre de message vous préoccupe.

## <a name="filtering-of-duplicate-audit-records"></a>Filtrage des enregistrements d’audit dupliqués

Les enregistrements d’audit dupliqués pour les mêmes opérations de liaison qui se produisent au cours de la même heure sont filtrés pour supprimer les bruits d’audit. Les opérations de synchronisation sont également filtrées à intervalles d’une heure. L’exception à ce processus de déduplication se produit si, pour le même InternetMessageId, l'une des propriétés décrites dans le tableau suivant est différente. Si l’une de ces propriétés est différente dans une opération de duplication, un nouvel enregistrement d’audit est généré. Ce processus est décrit en détail dans la section suivante.

<br>

****

|Propriété|Description|
|---|---|
|ClientIPAddress|Adresse IP de l’ordinateur client.|
|ClientInfoString|Protocole client, client utilisé pour accéder à la boîte aux lettres.|
|ParentFolder|Le chemin d’accès complet du dossier de l’élément de courrier qui a été consulté.|
|Logon_type|Type de connexion de l'utilisateur qui a réalisé l'opération. Les types de connexion (et leur valeur enum correspondante) sont propriétaire (0), administrateur (1) ou délégué (2).|
|MailAccessType|Si l’accès est une liaison ou une opération de synchronisation.|
|MailboxUPN|Nom d’utilisateur principal (UPN) de la boîte aux lettres dans laquelle se trouve le message lu.|
|Utilisateur|Nom d’utilisateur principal (UPN) de l’utilisateur lisant le message.|
|SessionId|L’ID de session vous permet de différencier les actions de l’attaquant et les activités quotidiennes des utilisateurs au sein de la même boîte aux lettres (en cas de compromission d’un compte). pour plus d’informations sur les sessions, voir [Contextualiser l’activité des attaquants dans les sessions Exchange Online](https://techcommunity.microsoft.com/t5/exchange-team-blog/contextualizing-attacker-activity-within-sessions-in-exchange/ba-p/608801).|
|

## <a name="identifying-the-access-contexts-of-different-audit-records"></a>Identification des contextes d'accès des différents enregistrements d'audit

Il est fréquent qu’un attaquant puisse accéder à une boîte aux lettres en même temps que le propriétaire de la boîte aux lettres y accède. Pour différencier l’accès par la personne malveillante et le propriétaire de la boîte aux lettres, il existe des propriétés d’enregistrement d’audit qui définissent le contexte de l’accès. Comme expliqué précédemment, lorsque les valeurs de ces propriétés différentes, même lorsque l’activité se produit dans l’intervalle de cumul, des enregistrements d’audit distincts sont générés. L’exemple suivant présente trois enregistrements d’audit différents. Chacun d’eux se distingue par l’ID de session et les propriétés ClientIPAddress. Les messages consultés sont également identifiés.

<br>

****

|Enregistrement d’audit 1|Enregistrement d’audit 2|Enregistrement d’audit 3|
|---|---|---|
|ClientIPAddress **1**<br/>SessionId **2**|ClientIPAddress **2**<br/>SessionId **2**|ClientIPAddress **1**<br/>SessionId **3**|
|InternetMessageId **A**<br/>InternetMessageId **D**<br/>InternetMessageId **E**<br/>InternetMessageId **F**<br/>|InternetMessageId **A**<br/>InternetMessageId **C**|InternetMessageId **B**|
|

Si l’une des propriétés répertoriées dans le tableau de la [section précédente](#filtering-of-duplicate-audit-records) est différente, un enregistrement d’audit séparé est créé pour suivre le nouveau contexte. Les accès sont triés dans des enregistrements d’audit distincts en fonction du contexte dans lequel l’activité a eu lieu.

Par exemple, dans les enregistrements d’audit illustrés dans la capture d’écran suivante, bien que nous accédions simultanément au courrier à partir d’EWSEditor et d’OWA, l’activité d’accès est compilée dans différents enregistrements d’audit en fonction du contexte dans lequel l’accès a eu lieu. Dans ce cas, le contexte est défini par différentes valeurs pour la propriété ClientInfoString.

![Enregistrements d’audit différents basés sur le contexte.](../media/MailItemsAccessed4.png)

Voici la syntaxe de la commande présentée dans la capture d'écran précédente :

```powershell
Search-MailboxAuditLog -Identity admin -ShowDetails -Operations MailItemsAccessed -ResultSize 2000 | Select LastAccessed,Operation,AuditOperationsCountInAggregatedRecord,ClientInfoString
```
