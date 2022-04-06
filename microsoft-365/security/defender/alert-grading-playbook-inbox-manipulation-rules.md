---
title: Classement des alertes pour les règles de manipulation de boîte de réception suspectes
description: Classement des alertes pour les règles de manipulation de boîte de réception suspectes afin de passer en revue les alertes et de prendre les mesures recommandées pour corriger l’attaque et protéger votre réseau.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
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
ms.openlocfilehash: e663d02037633599b9dffc19e1ebbd174aa279e1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663179"
---
# <a name="alert-grading-for-suspicious-inbox-manipulation-rules"></a>Classement des alertes pour les règles de manipulation de boîte de réception suspectes

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Les acteurs des menaces peuvent utiliser des comptes d’utilisateur compromis à de nombreuses fins malveillantes, notamment la lecture des e-mails dans la boîte de réception d’un utilisateur, la création de règles de boîte de réception pour transférer des e-mails vers des comptes externes, la suppression de traces et l’envoi de messages de hameçonnage. Les règles de boîte de réception malveillantes sont courantes lors des campagnes de compromission de messagerie professionnelle (BEC) et de hameçonnage, et il est important de les surveiller de manière cohérente.

Ce playbook vous aide à examiner tout incident lié à des règles de manipulation de boîte de réception suspectes configurées par des attaquants et à prendre les mesures recommandées pour corriger l’attaque et protéger votre réseau. Ce playbook s’applique aux équipes de sécurité, notamment aux analystes du Centre des opérations de sécurité (SOC) et aux administrateurs informatiques qui examinent, examinent et classent les alertes. Vous pouvez rapidement classer les alertes comme un vrai positif (TP) ou un faux positif (TP) et prendre des mesures recommandées pour les alertes TP afin de corriger l’attaque.

Les résultats de l’utilisation de ce playbook sont les suivants :

- Vous avez identifié les alertes associées aux règles de manipulation de boîte de réception comme étant des activités malveillantes (TP) ou bénignes (FP).

  En cas de malveillance, vous avez supprimé les règles de manipulation de boîte de réception malveillantes.

- Vous avez pris les mesures nécessaires si des e-mails ont été transférés vers une adresse e-mail malveillante.

## <a name="inbox-manipulation-rules"></a>Règles de manipulation de boîte de réception

Les règles de boîte de réception sont définies pour gérer automatiquement les messages électroniques en fonction de critères prédéfinis. Par exemple, vous pouvez créer une règle de boîte de réception pour déplacer tous les messages de votre responsable vers un autre dossier, ou transférer les messages que vous recevez vers une autre adresse e-mail.

### <a name="malicious-inbox-manipulation-rules"></a>Règles de manipulation de boîte de réception malveillantes

Les attaquants peuvent configurer des règles de messagerie pour masquer les e-mails entrants dans la boîte aux lettres de l’utilisateur compromise afin de masquer leurs activités malveillantes à l’utilisateur. Ils peuvent également définir des règles dans la boîte aux lettres de l’utilisateur compromis pour supprimer les e-mails, déplacer les e-mails dans un autre dossier moins visible (comme RSS) ou transférer des messages vers un compte externe. Certaines règles peuvent déplacer tous les e-mails vers un autre dossier et les marquer comme « lus », tandis que certaines règles peuvent déplacer uniquement les messages contenant des mots clés spécifiques dans le message électronique ou l’objet.

Par exemple, la règle de boîte de réception peut être définie pour rechercher des mots clés tels que « facture », « hameçonnage », « ne pas répondre », « courrier suspect » ou « courrier indésirable », entre autres, et les déplacer vers un compte de messagerie externe. Les attaquants peuvent également utiliser la boîte aux lettres d’utilisateur compromise pour distribuer du courrier indésirable, des e-mails de hameçonnage ou des programmes malveillants.

## <a name="workflow"></a>Flux de travail

Voici le flux de travail permettant d’identifier les activités suspectes de règle de manipulation de boîte de réception.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png" alt-text="Flux de travail d’investigation des alertes pour les règles de manipulation de boîte de réception" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png":::

## <a name="investigation-steps"></a>Étapes d’investigation

Cette section contient des instructions détaillées pas à pas pour répondre à l’incident et prendre les mesures recommandées pour protéger votre organisation contre d’autres attaques.

### <a name="1-review-the-alerts"></a>1. Passer en revue les alertes

Voici un exemple d’alerte de règle de manipulation de boîte de réception dans la file d’attente des alertes.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png" alt-text="Exemple de règle de manipulation de boîte de réception" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png":::

Voici un exemple des détails d’une alerte déclenchée par une règle de manipulation de boîte de réception malveillante.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png" alt-text="Détails de l’alerte déclenchée par une règle de manipulation de boîte de réception malveillante" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png":::

### <a name="2-investigate-inbox-manipulation-rule-parameters"></a>2. Examiner les paramètres de règle de manipulation de boîte de réception

Déterminez si les règles semblent suspectes en fonction des paramètres ou des critères de règle suivants :

- Mots clés

   L’attaquant peut appliquer la règle de manipulation uniquement aux e-mails qui contiennent certains mots. Vous pouvez trouver ces mots clés sous certains attributs tels que : « BodyContainsWords », « SubjectContainsWords » ou « SubjectOrBodyContainsWords ».

   S’il existe un filtrage par mots clés, vérifiez si les mots clés vous semblent suspects (les scénarios courants sont de filtrer les e-mails liés aux activités de l’attaquant, comme « phish », « spam », « ne pas répondre », entre autres).

   S’il n’existe aucun filtre, il peut également être suspect.

- Dossier de destination

   Pour échapper à la détection de sécurité, l’attaquant peut déplacer les e-mails vers un dossier moins visible et marquer les e-mails comme lus (par exemple, le dossier « RSS »). Si l’attaquant applique l’action « MoveToFolder » et « MarkAsRead », vérifiez si le dossier de destination est en quelque sorte lié aux mots clés de la règle pour déterminer s’il semble suspect ou non.

- Supprimer tout

   Certains attaquants suppriment simplement tous les e-mails entrants pour masquer leur activité. En général, une règle de « suppression de tous les e-mails entrants » sans les filtrer avec des mots clés est un indicateur d’activité malveillante.

Voici un exemple de configuration de règle « Supprimer tous les e-mails entrants » (comme indiqué sur RawEventData.Parameters) du journal des événements approprié.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png" alt-text="Exemple de configuration de règle supprimer tous les e-mails entrants" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png":::

### <a name="3-investigate-the-ip-address"></a>3. Examiner l’adresse IP

Passez en revue les attributs de l’adresse IP qui a effectué l’événement pertinent de création de règle :

- Recherchez d’autres activités cloud suspectes provenant de la même adresse IP dans le locataire. Par exemple, une activité suspecte peut être plusieurs tentatives de connexion ayant échoué.
- Le fournisseur de services Internet est-il courant et raisonnable pour cet utilisateur ?
- L’emplacement est-il courant et raisonnable pour cet utilisateur ?

### <a name="4-investigate-suspicious-activity-by-the-user-prior-to-creating-the-rules"></a>4. Examiner les activités suspectes de l’utilisateur avant de créer les règles

Vous pouvez examiner toutes les activités des utilisateurs avant la création des règles, rechercher des indicateurs de compromission et examiner les actions utilisateur qui semblent suspectes.

Par exemple, pour plusieurs connexions ayant échoué, examinez :

- Activité de connexion

   Vérifiez que l’activité de connexion avant la création de la règle n’est pas suspecte. (emplacement commun / fournisseur de services Internet / user-agent).

- Alertes

   Vérifiez si l’utilisateur a reçu des alertes avant de créer les règles. Cela peut indiquer que le compte d’utilisateur peut être compromis. Par exemple, une alerte de voyage impossible, un pays peu fréquent, plusieurs échecs de connexion, entre autres.)

- Incident

   Vérifiez si l’alerte est associée à d’autres alertes qui indiquent un incident. Si c’est le cas, vérifiez si l’incident contient d’autres alertes positives vraies.

## <a name="advanced-hunting-queries"></a>Requêtes de repérage avancées

[La chasse avancée](advanced-hunting-overview.md) est un outil de chasse aux menaces basé sur une requête qui vous permet d’inspecter les événements de votre réseau pour localiser les indicateurs de menace.

Utilisez cette requête pour rechercher tous les nouveaux événements de règle de boîte de réception pendant une fenêtre de temps spécifique.

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

La colonne *RuleConfig* fournit la nouvelle configuration de règle de boîte de réception.

Utilisez cette requête pour vérifier si le fournisseur de services Internet est courant pour l’utilisateur en examinant l’historique de l’utilisateur.

```kusto
let alert_date = now(); //enter alert date
let timeback = 60d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP
```

Utilisez cette requête pour vérifier si le pays est commun à l’utilisateur en examinant l’historique de l’utilisateur.

```kusto
let alert_date = now(); //enter alert date
let timeback = 60d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

Utilisez cette requête pour vérifier si l’agent utilisateur est courant pour l’utilisateur en examinant l’historique de l’utilisateur.

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
2. Réinitialiser les informations d’identification du compte d’utilisateur. Vous pouvez également vérifier si le compte d’utilisateur a été compromis avec Microsoft Defender for Cloud Apps, qui obtient les signaux de sécurité de Azure Active Directory (Azure AD) Identity Protection.
3. Recherchez d’autres activités malveillantes effectuées par le compte d’utilisateur concerné.
4. Recherchez d’autres activités suspectes dans le locataire provenant de la même adresse IP ou du même fournisseur de services Internet (si le fournisseur de services Internet est rare) pour trouver d’autres comptes d’utilisateur compromis.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du classement des alertes](alert-grading-playbooks.md)
- [Activité suspecte de transfert d’e-mail](alert-grading-playbook-email-forwarding.md)
- [Règle de transfert de boîte de réception suspect](alert-grading-playbook-inbox-forwarding-rules.md)
- [Examiner des alertes](investigate-alerts.md)
