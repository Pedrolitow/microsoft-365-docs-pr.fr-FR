---
title: Suivi des messages dans le Centre de sécurité et de conformité
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
localization_priority: Normal
ms.assetid: 3e64f99d-ac33-4aba-91c5-9cb4ca476803
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent utiliser le suivi des messages dans le Centre de sécurité & conformité pour savoir ce qui est arrivé aux messages.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1ce26f7a6cdad15019e2b40eb6f8746e5723d4f0
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50290656"
---
# <a name="message-trace-in-the-security--compliance-center"></a>Suivi des messages dans le Centre de sécurité et de conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

## <a name="message-trace-features"></a>Fonctionnalités de suivi des messages

Le suivi des messages dans le Centre de sécurité & conformité suit les messages électroniques lors de leur déplacement dans votre organisation Exchange Online. Vous pouvez déterminer si un message a été reçu, rejeté, différé ou remis par le service. Cela indique également les actions entamées par rapport au message avant qu'il atteigne son statut final.

Le suivi des messages dans le Centre de sécurité & conformité améliore le suivi des messages d’origine qui était disponible dans le Centre d’administration Exchange (EAC). Vous pouvez utiliser les informations du suivi des messages pour répondre efficacement aux questions des utilisateurs sur ce qui est arrivé aux messages, résoudre les problèmes de flux de messagerie et valider les modifications de stratégie.

> [!NOTE]
>
> - Pour suivre les messages, vous devez être membre des groupes de rôles Gestion de l’organisation, Gestion de la conformité ou Service d’aide. Si vous souhaitez en savoir plus, veuillez consulter la rubrique [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).
>
> - Le nombre maximal de messages affichés dans les résultats dépend du type de rapport que vous avez sélectionné (voir la section Choisir le [type](#choose-report-type) de rapport pour plus d’informations). La [cmdlet Get-HistoricalSearch](https://docs.microsoft.com/powershell/module/exchange/get-historicalsearch) dans Exchange Online PowerShell ou EOP PowerShell autonome renvoie tous les messages dans les résultats.

## <a name="open-message-trace"></a>Ouvrir le suivi des messages

1. Ouvrez le Centre de sécurité & conformité sur <https://protection.office.com> .

2. Développez **le flux de** messagerie, puis sélectionnez Suivi des **messages.**

## <a name="message-trace-page"></a>Page de suivi des messages

À partir de là, vous pouvez démarrer un nouveau suivi par défaut en cliquant sur le bouton Démarrer **un suivi.** Cette opération permet de rechercher tous les messages de tous les expéditeurs et destinataires des deux derniers jours. Vous pouvez également utiliser l’une des requêtes stockées à partir des catégories de requête disponibles et les exécuter telles quelles ou les utiliser comme points de départ pour vos propres requêtes :

- **Requêtes par défaut**: requêtes intégrées fournies par Microsoft 365.

- **Requêtes personnalisées**: requêtes enregistrées par les administrateurs de votre organisation pour une utilisation ultérieure.

- **Requêtes d’avage automatique :** les dix dernières requêtes ont été exécutés. Cette liste facilite la sélection là où vous vous êtes laissé.

Cette page contient également une section de rapports **téléchargeables** pour les demandes que vous avez envoyées, ainsi que les rapports eux-mêmes lorsqu’ils sont disponibles en téléchargement.

## <a name="options-for-a-new-message-trace"></a>Options pour un nouveau suivi des messages

### <a name="filter-by-senders-and-recipients"></a>Filtrer par expéditeurs et destinataires

Les valeurs par défaut **sont Tous les expéditeurs** et **Tous les destinataires,** mais vous pouvez utiliser les champs suivants pour filtrer les résultats :

- **Par ces personnes :** Cliquez dans ce champ pour sélectionner un ou plusieurs expéditeurs de votre organisation. Vous pouvez également commencer à taper un nom et les éléments de la liste seront filtrés par ce que vous avez tapé, de la même manière qu’une page de recherche se comporte.

- **À ces personnes :** Cliquez dans ce champ pour sélectionner un ou plusieurs destinataires dans votre organisation.

> [!NOTE]
>
> - Vous pouvez également taper les adresses e-mail des expéditeurs et des destinataires externes. Les caractères génériques sont pris en charge (par exemple, ), mais vous ne pouvez pas utiliser plusieurs entrées génériques dans le même champ `*@contoso.com` en même temps.
>
> - Vous pouvez coller plusieurs listes d’expéditeurs ou de destinataires séparées par des points-virgules ( `;` ). espaces ( `\s` ), retours chariot ( `\r` ) ou lignes suivantes ( `\n` ).

### <a name="time-range"></a>Plage de temps

La valeur par défaut **est 2 jours,** mais vous pouvez spécifier des plages de date/heure de 90 jours au plus. Lorsque vous utilisez des plages de date/heure, prenons en compte les problèmes ci-après :

- Par défaut, vous sélectionnez l’plage de temps en mode **Curseur** à l’aide d’une ligne de temps. Vous pouvez uniquement sélectionner les paramètres de jour ou d’heure affichés. Si vous essayez de sélectionner une valeur entre les deux, la bulle de début/fin s’alignera sur le paramètre affiché le plus proche.

  ![Un curseur dans un nouveau suivi des messages dans le Centre de sécurité & conformité](../../media/55a9e9c1-f7d5-4047-b217-824e8b976bcb.png)

  Toutefois, vous pouvez  également passer en mode Personnalisé où vous pouvez spécifier les valeurs de **date** de début et de **fin** (y compris les heures), et vous pouvez également sélectionner le fuseau horaire pour la plage de date/heure.  Notez que le **paramètre de fuseau** horaire s’applique à la fois aux entrées de requête et aux résultats de votre requête.

  ![Une plage de temps personnalisée dans un nouveau suivi des messages dans le Centre de sécurité & conformité](../../media/ed4c8d50-9ea5-4694-93f9-ee3ab6660b4f.png)

  Pendant 10 jours ou moins, les résultats sont disponibles instantanément en tant que **rapport de** synthèse. Si vous spécifiez une plage de temps qui est même légèrement supérieure à 10 jours, les résultats seront retardés, car ils ne sont disponibles qu’en tant que fichier CSV téléchargeable **(synthèse** améliorée ou rapports étendus). 

  Pour plus d’informations sur les différents types de rapports, voir la section Choisir un [type](#choose-report-type) de rapport dans cet article.

  > [!NOTE]
  > Les rapports récapitulatifs et étendus améliorés sont préparés à l’aide de données de suivi des messages archivées, et le téléchargement de votre rapport peut prendre jusqu’à plusieurs heures. Selon le nombre d’autres administrateurs qui ont également soumis des demandes de rapport en même temps, vous remarquerez peut-être également un délai avant le début du traitement de votre demande en file d’attente.

- L’enregistrement d’une requête en affichage **Curseur** permet d’économiser la plage de temps relative (par exemple, 3 jours à partir d’aujourd’hui). L’enregistrement d’une requête en affichage personnalisé permet d’enregistrer la plage de date/heure absolue (par exemple, 2018-05-06 13:00 et 2018-05-08 18:00). 

### <a name="more-search-options"></a>Autres options de recherche

#### <a name="delivery-status"></a>État de remise

Vous pouvez laisser la valeur par défaut **Tous** sélectionné, ou vous pouvez sélectionner l’une des valeurs suivantes pour filtrer les résultats :

- **Remis :** le message a été remis avec succès à la destination prévue.

- **En attente**: la remise du message est en cours de tentative ou de tentative.

- **Étendu :** un destinataire de groupe de distribution a été étendu avant la remise aux membres individuels du groupe.

- **Échec :** le message n’a pas été remis.

- **Mis en quarantaine**: le message a été mis en quarantaine (comme courrier indésirable, courrier en masse ou hameçonnage). Pour plus d’informations, voir [Messages électroniques mis en quarantaine dans EOP.](quarantine-email-messages.md)

- **Filtré comme courrier indésirable**: le message a été identifié comme courrier indésirable et a été rejeté ou bloqué (non mis en quarantaine).

- **Obtention de l’état :** Le message a été reçu récemment par Microsoft 365, mais aucune autre donnée d’état n’est encore disponible. Revenir quelques minutes plus tard.

> [!NOTE]
> Les valeurs **En attente,** **Mis en quarantaine** et Filtrer comme courrier indésirable ne sont disponibles que pour les recherches de moins de 10 jours.  En outre, il peut y avoir un délai de 5 à 10 minutes entre l’état de remise réel et le statut de remise signalé.

#### <a name="message-id"></a>ID de message

Il s’agit de l’ID de message Internet (également appelé ID client) qui se trouve dans le champ **d’en-tête Message-ID:** dans l’en-tête du message. Les utilisateurs peuvent vous donner cette valeur pour examiner des messages spécifiques.

Cette valeur est constante pendant toute la durée de vie du message. Pour les messages créés dans Microsoft 365 ou Exchange, la valeur est au format, y compris les `<GUID@ServerFQDN>` crochets ( \< \> ). Par exemple, `<d9683b4c-127b-413a-ae2e-fa7dfb32c69d@DM3NAM06BG401.Eop-nam06.prod.protection.outlook.com>`. D’autres systèmes de messagerie peuvent utiliser une syntaxe ou des valeurs différentes. Cette valeur est supposée être unique, mais tous les systèmes de messagerie ne suivent pas strictement cette exigence. Si le **champ d’en-tête Message-ID:** n’existe pas ou est vide pour les messages entrants provenant de sources externes, une valeur arbitraire est affectée.

Lorsque vous utilisez **l’ID de message** pour filtrer les résultats, n’oubliez pas d’inclure la chaîne complète, y compris les crochets.

#### <a name="direction"></a>Direction

Vous pouvez laisser  la valeur par défaut Tous sélectionné, ou vous pouvez sélectionner Entrant **(messages** envoyés à des destinataires de votre organisation) ou Sortant **(messages** envoyés par des utilisateurs de votre organisation) pour filtrer les résultats.

#### <a name="original-client-ip-address"></a>Adresse IP du client d’origine

Vous pouvez filtrer les résultats par adresse IP du client pour examiner les ordinateurs malveillants qui envoient de grandes quantités de courrier indésirable ou de programmes malveillants. Bien que les messages semblent provenant de plusieurs expéditeurs, il est probable que le même ordinateur génère tous les messages.

> [!NOTE]
> Les informations sur l’adresse IP du client ne sont  disponibles que  pendant 10 jours et uniquement dans les rapports de synthèse ou étendus améliorés (fichiers CSV téléchargeables).

### <a name="choose-report-type"></a>Choisir le type de rapport

Les types de rapports disponibles sont :

- **Résumé :** Disponible si la période est inférieure à 10 jours et ne nécessite aucune option de filtrage supplémentaire. Les résultats sont disponibles presque immédiatement après que vous avez cliqué sur **Rechercher.** Le rapport renvoie jusqu’à 20 000 résultats.

-  Résumé amélioré ou Étendu : Ces rapports sont disponibles uniquement en tant que fichiers CSV téléchargeables et nécessitent une ou plusieurs des options de filtrage suivantes, quelle que soit la période : Par ces **personnes,** À ces personnes **ou** **ID** de message . Vous pouvez utiliser des caractères génériques pour les expéditeurs ou les destinataires (par exemple, \* @contoso.com). Le rapport de synthèse amélioré renvoie jusqu’à 50 000 résultats. Le rapport étendu renvoie jusqu’à 1 000 résultats.

> [!NOTE]
> 
> - Les rapports récapitulatifs et étendus améliorés sont préparés à l’aide de données de suivi des messages archivées, et le téléchargement de votre rapport peut prendre jusqu’à plusieurs heures. Selon le nombre d’autres administrateurs qui ont également soumis des demandes de rapport en même temps, vous remarquerez peut-être également un délai avant le traitement de votre demande en file d’attente.
> 
> - Bien que vous pouvez sélectionner un rapport de synthèse ou étendu amélioré pour une plage de dates/heures, les quatre dernières heures de données archivées ne sont généralement pas encore disponibles pour ces deux types de rapports.

Lorsque vous cliquez sur **Suivant,** une page récapitulatif répertorie les options de filtrage que vous avez sélectionnées, un titre unique (modifiable) pour le rapport et l’adresse de messagerie qui reçoit la notification lorsque le suivi des messages est terminé (également modifiable et doit se trouver dans l’un des domaines acceptés de votre organisation). Cliquez **sur Préparer le rapport** pour envoyer le suivi des messages. Dans la page principale **de suivi des** messages, vous pouvez voir l’état du rapport dans la section Rapports **téléchargeables.**

Pour plus d’informations sur les informations renvoyées dans les différents types de rapports, voir la section suivante.

## <a name="message-trace-results"></a>Résultats du suivi des messages

Les différents types de rapports retournent différents niveaux d’informations. Les informations disponibles dans les différents rapports sont décrites dans les sections suivantes.

### <a name="summary-report-output"></a>Résultat du rapport de synthèse

Après l’exécution du suivi des messages, les résultats sont répertoriés, triés par date/heure décro issues de la liste (date/heure la plus récente en premier).

![Résultats du rapport de synthèse pour le suivi des messages dans le Centre de sécurité & conformité](../../media/0664bafe-0b03-477b-b571-0b046ac8c977.png)

Le rapport récapitulatif contient les informations suivantes :

- **Date**: date et heure de réception du message par le service, à l’aide du fuseau horaire UTC configuré.

- **Sender**: l’adresse e-mail de l’expéditeur (*alias* @ *de domaine*).

- **Destinataire**: adresse de messagerie du ou des destinataires. Pour un message envoyé à plusieurs destinataires, il existe une ligne par destinataire. Si le destinataire est un groupe de distribution, un groupe de distribution dynamique ou un groupe de sécurité à messagerie, le groupe sera le premier destinataire, puis chaque membre du groupe se trouve sur une ligne distincte.

- **Objet**: les 256 premiers caractères du champ **Objet :** du message.

- **État**: ces valeurs sont décrites dans la section [État de](#delivery-status) remise.

Par défaut, les 250 premiers résultats sont chargés et facilement disponibles. Lorsque vous faites défiler vers le bas, il y a une légère pause lorsque le lot de résultats suivant est chargé. Au lieu de faire défiler, vous pouvez cliquer sur Charger tout pour charger tous les résultats jusqu’à un maximum de 10 000. 

Vous pouvez cliquer sur les en-têtes de colonne pour trier les résultats en fonction des valeurs de cette colonne dans l’ordre croissant ou décroit.

Vous pouvez cliquer **sur Filtrer les résultats** pour filtrer les résultats d’une ou plusieurs colonnes.

Vous pouvez exporter les résultats après avoir sélectionné une ou  plusieurs lignes en cliquant sur Exporter les résultats, puis en sélectionnant **Exporter** tous les résultats, **Exporter** les résultats chargés ou Exporter **sélectionné.**

#### <a name="find-related-records-for-this-message"></a>Rechercher les enregistrements associés à ce message

Les enregistrements de messages associés sont des enregistrements qui ont partagé le même ID de message. N’oubliez pas qu’un seul message envoyé entre deux personnes peut générer plusieurs enregistrements. Le nombre d’enregistrements augmente lorsque le message est affecté par le développement, le transport, les règles de flux de messagerie (également appelées règles de transport), etc.

Après avoir cocher une ligne, vous pouvez rechercher les enregistrements  associés au message en cliquant sur le bouton Rechercher les informations associées qui s’affiche ou en sélectionnant Plus **d’options** Rechercher les enregistrements associés pour ce ![ ](../../media/1ea52bbf-9d00-48ce-9362-307f7f6fb7fe.png) \> **message).**

Pour plus d’informations sur l’ID de message, voir la section ID de message plus tôt dans cet article.

#### <a name="message-trace-details"></a>Détails du suivi des messages

Dans le rapport de synthèse, vous pouvez afficher les détails d’un message en utilisant l’une des méthodes suivantes :

- Sélectionnez la ligne (cliquez n’importe où dans la ligne à l’exception de la case à cocher).

- Cochez la case de la ligne et cliquez sur **Plus d’options** ![ Plus afficher les ](../../media/1ea52bbf-9d00-48ce-9362-307f7f6fb7fe.png) \> **détails des messages.**

   ![Détails après un double-clic sur une ligne dans le suivi des messages du rapport de synthèse dans le Centre de sécurité & conformité](../../media/e50ee7cd-810a-4c06-8b58-e56ffd7028d1.png)

Les détails du suivi des messages contiennent les informations supplémentaires suivantes qui ne sont pas présentes dans le rapport récapitulatif :

- **Événements de** message : cette section contient des classifications qui permettent de catégoriser les actions que le service prend sur les messages. **Voici quelques-uns des événements** les plus intéressants que vous pouvez rencontrer :

  - **Réception**: le message a été reçu par le service.

  - **Envoyer**: le message a été envoyé par le service.

  - **Fail**: le message n’a pas réussi à être remis.

  - **Deliver**: le message a été remis à une boîte aux lettres.

  - **Expand**: le message a été envoyé à un groupe de distribution qui a été développé.

  - **Transfert**: les destinataires ont été déplacés vers un message bifurqué en raison de la conversion de contenu, des limites de destinataire de message ou des agents.

  - **Defer**: la remise du message a été reportée et peut faire l’être ultérieurement.

  - **Résolu :** le message a été redirigé vers une nouvelle adresse de destinataire basée sur une recherche Active Directory. Lorsque cela se produit, l'adresse du destinataire d'origine est répertoriée sur une ligne distincte dans le suivi des messages avec l'état de remise final du message.

  > [!NOTE]
  > 
  > - Un message sans événement correctement remis génère plusieurs entrées **d’événement** dans le suivi des messages.
  > 
  > - Cette liste n’est pas exhaustive. Pour obtenir des descriptions d’autres événements, voir [types d’événements dans le journal de suivi des messages.](https://docs.microsoft.com/Exchange/mail-flow/transport-logs/message-tracking#event-types-in-the-message-tracking-log) Notez que ce lien est une Exchange Server (Exchange local).

- **Plus d’informations**: Cette section contient les détails suivants :

  - **ID de message**: cette valeur est décrite dans la section [ID](#message-id) de message plus tôt dans cet article. Par exemple, `<d9683b4c-127b-413a-ae2e-fa7dfb32c69d@DM3NAM06BG401.Eop-nam06.prod.protection.outlook.com>`.

  - **Taille du message**

  - **À partir de l’adresse IP**: adresse IP de l’ordinateur qui a envoyé le message. Pour les messages sortants envoyés à partir d'Exchange Online, ce champ est vide.

  - **Adresse IP**: adresse IP ou adresses où le service a tenté de remettre le message. Si le message a plusieurs destinataires, ceux-ci sont affichés. Pour les messages entrants envoyés à Exchange Online, ce champ est vide.

### <a name="enhanced-summary-reports"></a>Rapports de synthèse améliorés

Les rapports de synthèse améliorés disponibles (terminés) sont disponibles dans la section **Rapports téléchargeables** au début du suivi des messages. Les informations suivantes sont disponibles dans le rapport :

- **origin_timestamp**: date et heure de réception initiale du message par le service, à l’aide du fuseau horaire <sup>*</sup> UTC configuré.

- **sender_address**: adresse de messagerie de l’expéditeur (*domaine* @ *d’alias*).

- **Recipient_status**: état de la remise du message au destinataire. Si le message a été envoyé à plusieurs destinataires, il affiche tous les destinataires et l’état correspondant pour chacun d’eux, au format : \<*email address*\> ## \<*status*\> . Par exemple :

  - **##Receive, Send** signifie que le message a été reçu par le service et envoyé à la destination prévue.

  - **##Receive, Fail signifie** que le message a été reçu par le service mais que la remise à la destination prévue a échoué.

  - **##Receive, Deliver signifie** que le message a été reçu par le service et a été remis à la boîte aux lettres du destinataire.

- **message_subject**: les 256 premiers caractères du champ **Objet du** message.

- **total_bytes**: taille du message en octets, pièces jointes compris.

- **message_id**: cette valeur est décrite dans la section [ID](#message-id) de message plus tôt dans cet article. Par exemple, `<d9683b4c-127b-413a-ae2e-fa7dfb32c69d@DM3NAM06BG401.Eop-nam06.prod.protection.outlook.com>`.

- **network_message_id**: valeur d’ID de message unique qui persiste dans toutes les copies du message qui peuvent être créées en raison de la bifurcation ou du développement du groupe de distribution. Un exemple de valeur est `1341ac7b13fb42ab4d4408cf7f55890f` .

- **original_client_ip**: adresse IP du client de l’expéditeur.

- **directionality**: indique si le message a été envoyé entrant (1) à votre organisation, ou s’il a été envoyé sortant (2) à partir de votre organisation.

- **connector_id**: nom du connecteur source ou de destination. Pour plus d’informations sur les connecteurs dans Exchange Online, voir Configurer le flux de messagerie à l’aide [de connecteurs dans Office 365.](https://docs.microsoft.com/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)

- **delivery_priority**: si le message a été envoyé avec une priorité <sup>*</sup> élevée, faible ou normale.  

<sup>*</sup> Ces propriétés sont disponibles uniquement dans les rapports de synthèse améliorés.

### <a name="extended-reports"></a>Rapports étendus

Les rapports étendus disponibles (terminés) sont disponibles dans la section **Rapports téléchargeables** au début du suivi des messages. Presque toutes les informations d’un rapport de synthèse amélioré sont disponibles dans un rapport étendu (à l’exception de origin_timestamp **et** **delivery_priority**). Les informations supplémentaires suivantes sont disponibles uniquement dans un rapport étendu :

- **client_ip**: adresse IP du serveur de messagerie ou du client de messagerie qui a envoyé le message.

- **client_hostname**: nom d’hôte ou nom de domaine complet du serveur de messagerie ou du client de messagerie qui a envoyé le message.

- **server_ip**: adresse IP du serveur source ou de destination.

- **server_hostname**: nom d’hôte ou nom de domaine complet du serveur de destination.

- **source_context**: informations supplémentaires associées au **champ source.** Par exemple :

  - `Protocol Filter Agent`

  - `3489061114359050000`

- **source**: composant Exchange Online responsable de l’événement. Par exemple :

  - `AGENT`

  - `MAILBOXRULE`

  - `SMTP`

- **event_id**: ces valeurs  correspondent aux valeurs d’événement message qui sont expliquées dans la section Rechercher des enregistrements [associés pour ce message.](#find-related-records-for-this-message)

- **internal_message_id**: identificateur de message attribué par le serveur Exchange Online qui traite actuellement le message.

- **recipient_address**: adresses de messagerie des destinataires du message. Les adresses de messagerie multiples sont séparées par des points-virgules (;).

- **recipient_count**: nombre total de destinataires dans le message.

- **related_recipient_address**: utilisé avec et événements pour afficher les autres adresses de messagerie des `EXPAND` `REDIRECT` `RESOLVE` destinataires associées au message.

- **référence**: ce champ contient des informations supplémentaires pour des types d’événements spécifiques. Par exemple :

  - **DSN**: contient le lien de rapport, qui est la valeur message_id de la notification d’état de remise associée (également appelée notification d’état de remise, notification d’non-remise ou notification de non-remise) si une notification d’état de remise **est** générée après cet événement. S’il s’agit d’un message de DSN, ce champ contient la message_id du message d’origine pour qui le DSN **a** été généré.

  - **EXPAND**: contient la **related_recipient_address** valeur des messages associés.

  - **RECEIVE**: peut contenir la **message_id** du message associé si le message a été généré par d’autres processus (par exemple, règles de boîte de réception).

  - **SEND**: contient la **valeur internal_message_id** de tous les messages de DSN.

  - **TRANSFER**: contient la **internal_message_id** du message qui est en cours de bifurcation (par exemple, par conversion de contenu, limites de destinataire de message ou agents).

  - **MAILBOXRULE**: contient la **internal_message_id** du message entrant qui a entraîné la création du message sortant par la règle de boîte de réception.

    Pour les autres types d’événements, ce champ est généralement vide.

- **return_path**: adresse de messagerie de retour spécifiée par la **commande MAIL FROM** qui a envoyé le message. Bien que ce champ ne soit jamais vide, il peut avoir la valeur d’adresse de l’expéditeur null représentée par `<>` .

- **message_info**: informations supplémentaires sur le message. Par exemple :

  - Date et heure d’origine du message au temps UTC pour `DELIVER` et les `SEND` événements. La date-heure d’origine est l’heure à laquelle le message est entré pour la première fois dans l’organisation Exchange Online. La date-heure UTC est représentée au format date-heure ISO 8601 : , où = année, = mois, = jour, indique le début du composant d’heure, `yyyy-mm-ddThh:mm:ss.fffZ` `yyyy` = `mm` `dd` `T` `hh` heure, = `mm` minute, = seconde, = fractions `ss` `fff` `Z` `Zulu` d’une seconde, et signifie , qui est une autre façon de désigner UTC.

  - Erreurs d'authentification. Par exemple, vous pouvez voir la valeur et le type d’authentification qui `11a` ont été utilisés lorsque l’erreur d’authentification s’est produite.

- **tenant_id**: valeur GUID qui représente l’organisation Exchange Online (par exemple, `39238e87-b5ab-4ef6-a559-af54c6b07b42` ).

- **original_server_ip**: adresse IP du serveur d’origine.

- **custom_data**: contient des données relatives à des types d’événements spécifiques. Pour plus d’informations, voir les sections suivantes.

#### <a name="custom_data-values"></a>custom_data valeurs

Le **custom_data** d’un événement est utilisé par divers agents Exchange Online pour enregistrer les détails du traitement `AGENTINFO` des messages. Certains des agents les plus intéressants sont décrits dans les sections suivantes.

#### <a name="spam-filter-agent"></a>Agent de filtrage du courrier indésirable

Une **custom_data** qui commence par `S:SFA` l’agent de filtrage du courrier indésirable. Les détails clés sont décrits dans le tableau suivant :

****

|Valeur|Description|
|---|---|
|`SFV=NSPM`|Le message a été marqué comme n’étant pas un courrier indésirable et a été envoyé aux destinataires appropriés.|
|`SFV=SPM`|Le message a été marqué comme courrier indésirable par le filtrage du courrier indésirable (également appelé filtrage de contenu).|
|`SFV=BLK`|Le filtrage a été ignoré et le message a été bloqué, car il provient d'un expéditeur bloqué.|
|`SFV=SKS`|Le message a été marqué comme courrier indésirable avant d’être traitée par le filtrage anti-courrier indésirable. Cela inclut les messages qui ont été marqués automatiquement comme étant des courriers indésirables par une règle de flux de courrier (également appelée règle de transport) et pour lesquels toutes les étapes de filtrage supplémentaires ont été contournées.|
|`SCL=<number>`|Pour plus d'informations sur les différentes valeurs de SCL et leur signification, voir [Seuils de probabilité de courrier indésirable](spam-confidence-levels.md).|
|`PCL=<number>`|Valeur du seuil de probabilité de courrier d'hameçonnage (PCL) du message. Ces valeurs peuvent être interprétées de la même façon que les valeurs SCL répertoriées dans [Seuils de probabilité de courrier indésirable](spam-confidence-levels.md).  |
|`DI=SB`|L'expéditeur du message a été bloqué.|
|`DI=SQ`|Le message a été mis en quarantaine.|
|`DI=SD`|Le message a été supprimé.|
|`DI=SJ`|Le message a été mis dans le dossier Courrier indésirable du destinataire.|
|`DI=SN`|Le message a été routé via le pool de remises normal pour les messages sortants.|
|`DI=SO`|Le message a été routé via le pool de remises à haut risque. Pour plus d’informations, voir [Pool de remise à risque élevé pour les messages sortants](high-risk-delivery-pool-for-outbound-messages.md).|
|`SFS=[a]|SFS=[b]`|Cela indique que des règles anti-spam ont été associées.|
|`IPV=CAL`|Le message n’a pas été bloqué par les filtres anti-spam car l’adresse IP se trouve dans une liste d’adresses IP autorisées du filtre des connexions.|
|`H=<EHLOstring>`|Chaîne HELO ou EHLO du serveur de courrier de connexion.|
|`PTR=<ReverseDNS>`|Enregistrement PTR de l'adresse IP d'envoi, également appelé adresse DNS inverse.|
|

Exemple **custom_data** valeur d’un message filtré pour le courrier indésirable comme ceci :

`S:SFA=SUM|SFV=SPM|IPV=CAL|SRV=BULK|SFS=470454002|SFS=349001|SCL=9|SCORE=-1|LIST=0|DI=SN|RD=ftmail.inc.com|H=ftmail.inc.com|CIP=98.129.140.74|SFP=1501|ASF=1|CTRY=US|CLTCTRY=|LANG=en|LAT=287|LAT=260|LAT=18;`

#### <a name="malware-filter-agent"></a>Agent de filtrage des programmes malveillants

Une **custom_data** qui commence par `S:AMA` l’agent de filtrage des programmes malveillants. Les détails clés sont décrits dans le tableau suivant :

****

|Valeur|Description|
|---|---|
|`AMA=SUM|v=1|` ou `AMA=EV|v=1`|Un programme malveillant a été détecté dans le message. `SUM` indique que le programme malveillant a pu être détecté par n’importe quel moteur. `EV` indique que le programme malveillant a été détecté par un moteur spécifique. Lorsqu'un programme malveillant est détecté par un moteur, les actions suivantes se produisent.|
|`Action=r`|Le message a été remplacé.|
|`Action=p`|Le message a été ignoré.|
|`Action=d`|Le message a été différé.|
|`Action=s`|Le message a été supprimé.|
|`Action=st`|Le message a été ignoré.|
|`Action=sy`|Le message a été ignoré.|
|`Action=ni`|Le message a été rejeté.|
|`Action=ne`|Le message a été rejeté.|
|`Action=b`|Le message a été bloqué.|
|`Name=<malware>`|Nom du programme malveillant détecté.|
|`File=<filename>`|Nom du fichier qui contenait le programme malveillant.|
|

Voici un **exemple custom_data** valeur d’un message contenant un programme malveillant :

`S:AMA=SUM|v=1|action=b|error=|atch=1;S:AMA=EV|engine=M|v=1|sig=1.155.974.0|name=DOS/Test_File|file=filename;S:AMA=EV|engine=A|v=1|sig=201707282038|name=Test_File|file=filename`

#### <a name="transport-rule-agent"></a>Agent de règles de transport

Une **custom_data** qui commence par l’agent de règles de transport pour les règles de flux de messagerie (également appelées `S:TRA` règles de transport). Les détails clés sont décrits dans le tableau suivant :

****

|Valeur|Description|
|---|---|
|`ETR|ruleId=<guid>`|ID de la règle qui s'applique.|
|`St=<datetime>`|Date et heure UTC à laquelle la correspondance de règle s’est produite.|
|`Action=<ActionDefinition>`|Action appliquée. Pour obtenir la liste des actions disponibles, voir Actions de règle [de flux de messagerie dans Exchange Online.](https://docs.microsoft.com/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions)|
|`Mode=<Mode>`|Mode de la règle. Les valeurs valides sont les suivantes :<ul><li>**Appliquer**: toutes les actions de la règle seront appliquées.</li><li>**Testez avec les conseils de stratégie**: toutes les actions de conseil de stratégie seront envoyées, mais les autres actions d’application ne seront pas entreprises.</li><li>**Test sans conseils** de stratégie : les actions sont répertoriées dans un fichier journal, mais les expéditeurs ne sont pas avertis d’aucune manière et les actions d’application ne sont pas prises en action.</li></ul>|
|

Un exemple **custom_data** valeur d’un message qui correspond aux conditions d’une règle de flux de messagerie ressemble à ceci :

`S:TRA=ETR|ruleId=19a25eb2-3e43-4896-ad9e-47b6c359779d|st=7/17/2017 12:31:25 AM|action=ApplyHtmlDisclaimer|sev=1|mode=Enforce`
