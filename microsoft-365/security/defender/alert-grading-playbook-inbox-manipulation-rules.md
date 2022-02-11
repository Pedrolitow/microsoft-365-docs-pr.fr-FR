---
title: Notation des alertes pour les règles de manipulation de boîte de réception suspectes
description: Notation des alertes pour les règles de manipulation de boîte de réception suspectes pour passer en revue les alertes et prendre les mesures recommandées pour corriger l’attaque et protéger votre réseau.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, ordinateurs, appareils, utilisateurs, identités, identité, boîte aux lettres, courrier électronique, 365, microsoft, m365
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: e1bfb37ebf88ffd67a7fcfaddde46141583fb717
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/10/2022
ms.locfileid: "62524092"
---
# <a name="alert-grading-for-suspicious-inbox-manipulation-rules"></a>Notation des alertes pour les règles de manipulation de boîte de réception suspectes

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Les acteurs des menaces peuvent utiliser des comptes d’utilisateur compromis à de nombreuses fins malveillantes, notamment la lecture de messages électroniques dans la boîte de réception d’un utilisateur, la création de règles de boîte de réception pour transmettre des messages électroniques à des comptes externes, la suppression de suivis et l’envoi de messages de hameçonnage. Les règles de boîte de réception malveillantes sont courantes pendant les campagnes de compromission de courrier électronique et de hameçonnage, et il est important de les surveiller de manière cohérente. 

Ce manuel vous aide à examiner tout incident lié à des règles de manipulation de boîte de réception suspectes configurées par des attaquants et à prendre les mesures recommandées pour corriger l’attaque et protéger votre réseau. Ce manuel est pour les équipes de sécurité, y compris les analystes du centre d’opérations de sécurité (SOC) et les administrateurs informatiques qui examinent, examinent et classent les alertes. Vous pouvez rapidement classer les alertes en tant que vrai positif (TP) ou faux positif (TP) et prendre des mesures recommandées pour les alertes TP afin de corriger l’attaque. 

Les résultats de l’utilisation de ce manuel sont les :

- Vous avez identifié les alertes associées aux règles de manipulation de boîte de réception comme des activités malveillantes (TP) ou malveillantes (FP).

  Si vous êtes malveillant, vous avez supprimé les règles de manipulation de boîte de réception malveillantes.

- Vous avez pris les mesures nécessaires si les messages électroniques ont été transmis à une adresse de messagerie malveillante.

## <a name="inbox-manipulation-rules"></a>Règles de manipulation de boîte de réception

Les règles de boîte de réception sont définies pour gérer automatiquement les messages électroniques en fonction de critères prédéfin définis. Par exemple, vous pouvez créer une règle de boîte de réception pour déplacer tous les messages de votre responsable vers un autre dossier, ou pour déplacer les messages que vous recevez vers une autre adresse de messagerie.

### <a name="malicious-inbox-manipulation-rules"></a>Règles de manipulation de boîte de réception malveillante

Les attaquants peuvent configurer des règles de messagerie pour masquer les e-mails entrants dans la boîte aux lettres de l’utilisateur compromis afin d’masquer leurs activités malveillantes à l’utilisateur. Ils peuvent également définir des règles dans la boîte aux lettres utilisateur compromise pour supprimer des messages électroniques, les déplacer vers un autre dossier moins perceptible (rss, par exemple) ou les envoyer à un compte externe. Certaines règles peuvent déplacer tous les e-mails vers un autre dossier et les marquer comme « lus », tandis que certaines règles peuvent déplacer uniquement les messages électroniques qui contiennent des mots clés spécifiques dans le message électronique ou l’objet. 

Par exemple, la règle de boîte de réception peut être définie pour rechercher des mots clés tels que « facture », « hameçonnage », « ne pas répondre », « courrier suspect » ou « courrier indésirable » entre autres, et les déplacer vers un compte de messagerie externe. Les personnes malveillantes peuvent également utiliser la boîte aux lettres de l’utilisateur compromis pour distribuer du courrier indésirable, des e-mails de hameçonnage ou des programmes malveillants. 

## <a name="workflow"></a>Flux de travail

Voici le flux de travail permettant d’identifier les activités suspectes de règle de manipulation de boîte de réception.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png" alt-text="Flux de travail d’investigation d’alerte pour les règles de manipulation de boîte de réception" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png":::


## <a name="investigation-steps"></a>Étapes d’examen

Cette section contient des instructions détaillées pour répondre à l’incident et prendre les mesures recommandées pour protéger votre organisation contre d’autres attaques.

### <a name="1-review-the-alerts"></a>1. Passer en revue les alertes

Voici un exemple d’alerte de règle de manipulation de boîte de réception dans la file d’attente d’alertes.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png" alt-text="Exemple de règle de manipulation de boîte de réception" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png":::

Voici un exemple des détails d’une alerte déclenchée par une règle de manipulation de boîte de réception malveillante.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png" alt-text="Détails de l’alerte déclenchée par une règle de manipulation de boîte de réception malveillante" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png":::


### <a name="2-investigate-inbox-manipulation-rule-parameters"></a>2. Examiner les paramètres de règle de manipulation de boîte de réception 

Déterminez si les règles semblent suspectes en fonction des paramètres ou critères de règle suivants :

- Keywords

   L’attaquant peut appliquer la règle de manipulation uniquement aux e-mails contenant certains mots. Vous pouvez trouver ces mots clés sous certains attributs tels que : « BodyContainsWords », « SubjectContainsWords » ou « SubjectOrBodyContainsWords ». 

   S’il existe un filtrage par mots clés, vérifiez si les mots clés vous semblent suspects (les scénarios courants sont de filtrer les e-mails liés aux activités de l’attaquant, tels que « hameçonnage », « courrier indésirable », « ne pas répondre », entre autres).

   S’il n’existe aucun filtre, il peut également être suspect.

- Dossier de destination

   Pour éviter toute détection de sécurité, l’attaquant peut déplacer les e-mails vers un dossier moins perceptible et marquer les e-mails comme lus (par exemple, dossier « RSS »). Si l’attaquant applique les actions « MoveToFolder » et « MarkAsRead », vérifiez si le dossier de destination est en quelque sorte lié aux mots clés de la règle pour déterminer s’il semble suspect ou non. 

- Supprimer tout

   Certains attaquants suppriment simplement tous les e-mails entrants pour masquer leur activité. En règle générale, une règle de « suppression de tous les e-mails entrants » sans les filtrer avec des mots clés est un indicateur d’activité malveillante. 
 
Voici un exemple de configuration de règle « supprimer tous les e-mails entrants » (comme indiqué dans RawEventData.Parameters) du journal des événements approprié. 

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png" alt-text="Exemple de suppression de toutes les configurations de règle de courrier entrant" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png":::


### <a name="3-investigate-the-ip-address"></a>3. Examiner l’adresse IP

Examinez les attributs de l’adresse IP qui a effectué l’événement pertinent de création de règle :

- Recherchez d’autres activités cloud suspectes provenant de la même adresse IP dans le client. Par exemple, une activité suspecte peut être plusieurs tentatives de connexion qui ont échoué. 
- Le isp est-il courant et raisonnable pour cet utilisateur ?
- L’emplacement est-il commun et raisonnable pour cet utilisateur ?

### <a name="4-investigate-suspicious-activity-by-the-user-prior-to-creating-the-rules"></a>4. Examiner les activités suspectes de l’utilisateur avant de créer les règles

Vous pouvez passer en revue toutes les activités des utilisateurs avant la création de règles, rechercher des indicateurs de compromission et examiner les actions de l’utilisateur qui semblent suspectes. 

Par exemple, pour plusieurs connexions qui ont échoué, examinez : 

- Activité de connexion 

   Vérifier que l’activité de connexion avant la création de la règle n’est pas suspecte. (emplacement commun / ISP / agent utilisateur). 

- Alertes

   Vérifiez si l’utilisateur a reçu des alertes avant de créer les règles. Cela peut indiquer que le compte d’utilisateur peut être compromis. Par exemple, une alerte de voyage impossible, un pays rare, plusieurs connexions qui ont échoué, entre autres.)

- Incident

   Vérifiez si l’alerte est associée à d’autres alertes qui indiquent un incident. Si c’est le cas, vérifiez si l’incident contient d’autres alertes positives réelles.

## <a name="advanced-hunting-queries"></a>Requêtes de recherche avancées

[Le recherche avancée](advanced-hunting-overview.md) est un outil de recherche de menace basé sur une requête qui vous permet d’inspecter les événements de votre réseau pour localiser les indicateurs de menace. 

Utilisez cette requête pour rechercher tous les nouveaux événements de règle de boîte de réception pendant une période spécifique.  

```kusto
let start_date = now(-10h); 
let end_date = now();
let user_id = ""; // enter here the user id
CloudAppEvents
| where Timestamp between (start_date .. end_date)
| where AccountObjectId == user_id
| where Application == @"Microsoft Exchange Online"
| where ActionType in ("Set-Mailbox", "New-InboxRule", "Set-InboxRule") //set new inbox rule related operations
| project Timestamp, ActionType, CountryCode, City, ISP, IPAddress, RuleConfig = RawEventData.Parameters, RawEventData
```

La *colonne RuleConfig* fournit la nouvelle configuration de règle de boîte de réception.

Utilisez cette requête pour vérifier si le isp est courant pour l’utilisateur en regardant l’historique de l’utilisateur.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 60d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP 
```

Utilisez cette requête pour vérifier si le pays est commun pour l’utilisateur en regardant l’historique de l’utilisateur.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 60d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

Utilisez cette requête pour vérifier si l’agent utilisateur est courant pour l’utilisateur en regardant l’historique de l’utilisateur.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 60d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by UserAgent
```

## <a name="recommended-actions"></a>Actions recommandées

1. Désactivez la règle de boîte de réception malveillante.
2. Réinitialisez les informations d’identification du compte d’utilisateur. Vous pouvez également vérifier si le compte d’utilisateur a été compromis avec Microsoft Defender pour les applications cloud, ce qui obtient des signaux de sécurité de Azure Active Directory (Azure AD) Identity Protection.
3. Recherchez d’autres activités malveillantes effectuées par le compte d’utilisateur touché.
4. Recherchez dans le client d’autres activités suspectes provenant de la même adresse IP ou du même isp (si ce n’est pas le cas) pour rechercher d’autres comptes d’utilisateur compromis.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la notation des alertes](alert-grading-playbooks.md)
- [Activité suspecte de transfert d’e-mail](alert-grading-playbook-email-forwarding.md)
- [Règle de transfert de boîte de réception suspect](alert-grading-playbook-inbox-forwarding-rules.md)
- [Examiner des alertes](investigate-alerts.md)
