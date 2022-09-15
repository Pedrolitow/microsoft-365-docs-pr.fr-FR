---
title: Classement des alertes pour les règles de transfert de boîte de réception suspectes
description: Classement des alertes pour les règles de transfert de boîte de réception suspectes pour passer en revue les alertes et prendre les mesures recommandées pour corriger l’attaque et protéger votre réseau.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365
ms.service: microsoft-365-security
ms.subservice: m365d
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
- met150
ms.openlocfilehash: 9d02727df9684e8c3da9f5abf003ef9a4c7012b6
ms.sourcegitcommit: b1ed6470645455c2f1fcf467450debc622c40147
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67711002"
---
# <a name="alert-grading-for-suspicious-inbox-forwarding-rules"></a>Classement des alertes pour les règles de transfert de boîte de réception suspectes

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Les acteurs des menaces peuvent utiliser des comptes d’utilisateur compromis à plusieurs fins malveillantes, notamment la lecture d’e-mails dans la boîte de réception d’un utilisateur, la création de règles de boîte de réception pour transférer des e-mails vers des comptes externes, l’envoi de messages de hameçonnage, entre autres. Les règles de boîte de réception malveillantes sont largement courantes pendant les campagnes de compromission de messagerie professionnelle (BEC) et de hameçonnage, et il est important de les surveiller de manière cohérente.

Ce playbook vous permet d’examiner les alertes de règles de transfert de boîte de réception suspectes et de les classer rapidement comme un vrai positif (TP) ou un faux positif (TP). Vous pouvez ensuite prendre les actions recommandées pour les alertes TP afin de corriger l’attaque.

Pour obtenir une vue d’ensemble de la notation des alertes pour Microsoft Defender pour Office 365 et Microsoft Defender for Cloud Apps, consultez [l’article d’introduction](alert-grading-playbooks.md).

Les résultats de l’utilisation de ce playbook sont les suivants :

- Vous avez identifié les alertes associées aux règles de transfert de boîte de réception comme étant des activités malveillantes (TP) ou bénignes (FP).

  En cas de malveillance, vous avez supprimé les règles de transfert de boîte de réception malveillantes.

- Vous avez pris les mesures nécessaires si des e-mails ont été transférés vers une adresse e-mail malveillante.

## <a name="inbox-forwarding-rules"></a>Règles de transfert de boîte de réception

Vous configurez des règles de boîte de réception pour gérer automatiquement les messages électroniques en fonction de critères prédéfinis. Par exemple, vous pouvez créer une règle de boîte de réception pour déplacer tous les messages de votre responsable vers un autre dossier, ou transférer les messages que vous recevez vers une autre adresse e-mail.

### <a name="suspicious-inbox-forwarding-rules"></a>Règle de transfert de boîte de réception suspect

Après avoir accédé aux boîtes aux lettres des utilisateurs, les attaquants créent souvent une règle de boîte de réception qui leur permet d’exfiltrer des données sensibles vers une adresse e-mail externe et de les utiliser à des fins malveillantes.

Les règles de boîte de réception malveillantes automatisent le processus d’exfiltration. Avec des règles spécifiques, chaque e-mail dans la boîte de réception de l’utilisateur cible qui correspond aux critères de règle est transféré vers la boîte aux lettres de l’attaquant. Par exemple, un attaquant peut vouloir collecter des données sensibles liées au financement. Ils créent une règle de boîte de réception pour transférer tous les e-mails contenant des mots clés, tels que « finance » et « invoice » dans l’objet ou le corps du message, à leur boîte aux lettres.

Les règles de transfert de boîte de réception suspectes peuvent être très difficiles à détecter, car la maintenance des règles de boîte de réception est une tâche courante effectuée par les utilisateurs. Par conséquent, il est important de surveiller les alertes.

## <a name="workflow"></a>Flux de travail

Voici le flux de travail permettant d’identifier les règles de transfert de courrier suspectes.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png" alt-text="Flux de travail d’investigation des alertes pour les règles de transfert de boîte de réception" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png":::

## <a name="investigation-steps"></a>Étapes d’investigation

Cette section contient des instructions détaillées pas à pas pour répondre à l’incident et prendre les mesures recommandées pour protéger votre organisation contre d’autres attaques.

### <a name="review-generated-alerts"></a>Passer en revue les alertes générées

Voici un exemple d’alerte de règle de transfert de boîte de réception dans la file d’attente d’alerte.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png" alt-text="Exemple de notification dans la file d’attente des alertes" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png":::

Voici un exemple des détails de l’alerte déclenchée par une règle de transfert de boîte de réception malveillante.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png" alt-text="Détails de l’alerte déclenchée par une règle de transfert de boîte de réception malveillante" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png":::

### <a name="investigate-rule-parameters"></a>Examiner les paramètres de règle

L’objectif de cette étape est de déterminer si les règles semblent suspectes selon certains critères :

Destinataires de la règle de transfert :

- Valider l’adresse e-mail de destination n’est pas une boîte aux lettres supplémentaire appartenant au même utilisateur (ce qui évite les cas où l’utilisateur transfère automatiquement des e-mails entre des boîtes aux lettres personnelles).
- Vérifiez que l’adresse e-mail de destination n’est pas une adresse interne ou un sous-domaine appartenant à l’entreprise.

Filtres:

- Si la règle de boîte de réception contient des filtres qui recherchent des mots clés spécifiques dans l’objet ou le corps de l’e-mail, vérifiez si les mots clés fournis, tels que la finance, les informations d’identification et la mise en réseau, entre autres, semblent liés à une activité malveillante. Vous trouverez ces filtres sous les attributs suivants (qui s’affichent dans la colonne RawEventData de l’événement) : « BodyContainsWords », « SubjectContainsWords » ou « SubjectOrBodyContainsWords »
- Si l’attaquant choisit de ne pas définir de filtre pour les messages et que la règle de boîte de réception transfère tous les éléments de boîte aux lettres à la boîte aux lettres de l’attaquant, ce comportement est également suspect.

### <a name="investigate-ip-address"></a>Examiner l’adresse IP

Passez en revue les attributs liés à l’adresse IP qui a effectué l’événement pertinent de création de règle :

1. Recherchez d’autres activités cloud suspectes provenant de la même adresse IP dans le locataire. Par exemple, l’activité suspecte peut être plusieurs tentatives de connexion ayant échoué.
2. Le fournisseur de services Internet est-il courant et raisonnable pour cet utilisateur ?
3. L’emplacement est-il courant et raisonnable pour cet utilisateur ?

### <a name="investigate-any-suspicious-activity-with-the-user-inbox-before-creating-rules"></a>Examiner toute activité suspecte avec la boîte de réception de l’utilisateur avant de créer des règles

Vous pouvez examiner toutes les activités des utilisateurs avant de créer des règles, rechercher des indicateurs de compromission et examiner les actions utilisateur qui semblent suspectes. Par exemple, plusieurs connexions ayant échoué.

- Connexions :

  Vérifiez que l’activité de connexion avant l’événement de création de règle n’est pas suspecte (par exemple, l’emplacement commun, le fournisseur de services Internet ou l’agent utilisateur).

- Autres alertes ou incidents
  - D’autres alertes se sont-elle déclenchées pour l’utilisateur avant la création de la règle. Si c’est le cas, cela peut indiquer que l’utilisateur a été compromis.
  - Si l’alerte est corrélée à d’autres alertes pour indiquer un incident, l’incident contient-il d’autres alertes positives véritables ?

## <a name="advanced-hunting-queries"></a>Requêtes de repérage avancées

[La chasse avancée](advanced-hunting-overview.md) est un outil de chasse aux menaces basé sur une requête qui vous permet d’inspecter les événements de votre réseau et de localiser les indicateurs de menace.

Exécutez cette requête pour rechercher tous les nouveaux événements de règle de boîte de réception pendant une fenêtre de temps spécifique.

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

*RuleConfig* contiendra la configuration de la règle.

Exécutez cette requête pour vérifier si le fournisseur de services Internet est commun à l’utilisateur en examinant l’historique de l’utilisateur.

```kusto
let alert_date = now(); //enter alert date
let timeback = 30d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP
```

Exécutez cette requête pour vérifier si le pays est commun à l’utilisateur en examinant l’historique de l’utilisateur.

```kusto
let alert_date = now(); //enter alert date
let timeback = 30d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

Exécutez cette requête pour vérifier si l’agent utilisateur est courant pour l’utilisateur en examinant l’historique de l’utilisateur.

```kusto
let alert_date = now(); //enter alert date
let timeback = 30d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by UserAgent
```

Exécutez cette requête pour vérifier si d’autres utilisateurs ont créé une règle de transfert vers la même destination (peut indiquer que d’autres utilisateurs sont également compromis).

```kusto
let start_date = now(-10h);
let end_date = now();
let dest_email = ""; // enter here destination email as seen in the alert
CloudAppEvents
| where Timestamp between (start_date .. end_date)
| where ActionType in ("Set-Mailbox", "New-InboxRule", "Set-InboxRule") //set new inbox rule related operations
| project Timestamp, ActionType, CountryCode, City, ISP, IPAddress, RuleConfig = RawEventData.Parameters, RawEventData
| where RuleConfig has dest_email
```

## <a name="recommended-actions"></a>Actions recommandées

1. Désactivez la règle de boîte de réception malveillante.
2. Réinitialiser les informations d’identification du compte de l’utilisateur. Vous pouvez également vérifier si le compte d’utilisateur a été compromis avec Microsoft Defender for Cloud Apps, qui obtient les signaux de sécurité d’Azure Active Directory (Azure AD) Identity Protection.
3. Recherchez d’autres activités malveillantes effectuées par l’utilisateur concerné.
4. Recherchez d’autres activités suspectes dans le locataire provenant de la même adresse IP ou du même fournisseur de services Internet (si le fournisseur de services Internet est rare) pour trouver d’autres utilisateurs compromis.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du classement des alertes](alert-grading-playbooks.md)
- [Activité suspecte de transfert d’e-mail](alert-grading-playbook-email-forwarding.md)
- [Règles de manipulation de la boîte de réception suspectes](alert-grading-playbook-inbox-manipulation-rules.md)
- [Examiner des alertes](investigate-alerts.md)
