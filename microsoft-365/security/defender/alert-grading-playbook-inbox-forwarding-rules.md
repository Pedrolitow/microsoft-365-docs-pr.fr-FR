---
title: Notation des alertes pour les règles de forwarding de boîte de réception suspectes
description: Notation des alertes pour les règles de transport de boîte de réception suspectes pour passer en revue les alertes et prendre les mesures recommandées pour corriger l’attaque et protéger votre réseau.
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
ms.openlocfilehash: 9680c9c45441bc654103c11ea28c13f85859ee43
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2022
ms.locfileid: "62355176"
---
# <a name="alert-grading-for-suspicious-inbox-forwarding-rules"></a>Notation des alertes pour les règles de forwarding de boîte de réception suspectes

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Les acteurs des menaces peuvent utiliser des comptes d’utilisateur compromis à plusieurs fins malveillantes, notamment la lecture de messages électroniques dans la boîte de réception d’un utilisateur, la création de règles de boîte de réception pour transmettre des messages électroniques à des comptes externes, l’envoi de courriers de hameçonnage, entre autres. Les règles de boîte de réception malveillantes sont largement courantes pendant les campagnes de compromission de courrier électronique et de hameçonnage, et il est important de les surveiller de manière cohérente.

Ce manuel vous permet d’examiner les alertes pour les règles de forwarding de boîte de réception suspectes et de les classer rapidement en tant que vrai positif (TP) ou faux positif (TP). Vous pouvez ensuite prendre des mesures recommandées pour les alertes TP afin de corriger l’attaque. 

Pour obtenir une vue d’ensemble de la notation des alertes pour Microsoft Defender pour Office 365 et Microsoft Defender pour les applications cloud, consultez [l’article d’introduction](alert-grading-playbooks.md).

Les résultats de l’utilisation de ce manuel sont les :

- Vous avez identifié les alertes associées aux règles de forwarding de boîte de réception comme des activités malveillantes ou malveillantes (FP).

  Si vous êtes malveillant, vous avez supprimé les règles de forwarding de boîte de réception malveillantes.

- Vous avez pris les mesures nécessaires si les messages électroniques ont été transmis à une adresse de messagerie malveillante.

## <a name="inbox-forwarding-rules"></a>Règles de forwarding de boîte de réception

Vous configurez des règles de boîte de réception pour gérer automatiquement les messages électroniques en fonction de critères prédéfinie. Par exemple, vous pouvez créer une règle de boîte de réception pour déplacer tous les messages de votre responsable vers un autre dossier, ou pour déplacer les messages que vous recevez vers une autre adresse de messagerie.

### <a name="suspicious-inbox-forwarding-rules"></a>Règles de forwarding de boîte de réception suspectes

Après avoir accédé aux boîtes aux lettres des utilisateurs, les attaquants créent souvent une règle de boîte de réception qui leur permet d’exfiltrer des données sensibles vers une adresse de messagerie externe et de les utiliser à des fins malveillantes. 

Les règles de boîte de réception malveillantes automatisent le processus d’exfiltration. Avec des règles spécifiques, chaque courrier électronique de la boîte de réception de l’utilisateur cible qui correspond aux critères de règle est transmis à la boîte aux lettres de l’attaquant. Par exemple, un attaquant peut vouloir collecter des données sensibles liées à la finance. Ils créent une règle de boîte de réception pour transmettre tous les messages électroniques qui contiennent des mots clés, tels que « finance » et « facture » dans l’objet ou le corps du message, à leur boîte aux lettres.

Les règles de forwarding de boîte de réception suspectes peuvent être très difficiles à détecter, car la maintenance des règles de boîte de réception est une tâche courante effectuée par les utilisateurs. Par conséquent, il est important de surveiller les alertes. 

## <a name="workflow"></a>Flux de travail

Voici le flux de travail permettant d’identifier les règles de forwarding de courrier suspectes.
 
:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png" alt-text="Flux de travail d’investigation d’alerte pour les règles de forwarding de boîte de réception" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png":::

## <a name="investigation-steps"></a>Étapes d’examen

Cette section contient des instructions détaillées pour répondre à l’incident et prendre les mesures recommandées pour protéger votre organisation contre d’autres attaques.

### <a name="review-generated-alerts"></a>Passer en revue les alertes générées

Voici un exemple d’alerte de règle de forwarding de boîte de réception dans la file d’attente d’alertes.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png" alt-text="Exemple de notification dans la file d’attente d’alertes" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png":::

Voici un exemple des détails de l’alerte déclenchée par une règle de forwarding de boîte de réception malveillante.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png" alt-text="Détails de l’alerte déclenchée par une règle de forwarding de boîte de réception malveillante" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png":::

### <a name="investigate-rule-parameters"></a>Examiner les paramètres de règle 

L’objectif de cette étape est de déterminer si les règles semblent suspectes selon certains critères :

Destinataires de la règle de forwarding :

- Valider l’adresse e-mail de destination n’est pas une boîte aux lettres supplémentaire dont est propriétaire le même utilisateur (en évitant les cas où l’utilisateur a des courriers électroniques auto-transmis entre des boîtes aux lettres personnelles). 
- Validez que l’adresse e-mail de destination n’est pas une adresse interne ou un sous-domaine appartenant à la société.

Filtres :
 
- Si la règle de boîte de réception contient des filtres qui recherchent des mots clés spécifiques dans l’objet ou le corps de l’e-mail, vérifiez si les mots clés fournis, tels que finance, informations d’identification et réseau, entre autres, semblent liés à une activité malveillante. Vous pouvez trouver ces filtres sous les attributs suivants (qui s’affiche dans la colonne RawEventData) : « BodyContainsWords », « SubjectContainsWords » ou « SubjectOrBodyContainsWords »
- Si l’attaquant choisit de ne pas définir de filtre pour les messages électroniques, et que la règle de boîte de réception a pour effet de le faire, tous les éléments de boîte aux lettres sont transmis à la boîte aux lettres de l’attaquant, ce comportement est également suspect. 

### <a name="investigate-ip-address"></a>Examiner l’adresse IP

Examinez les attributs liés à l’adresse IP qui a exécuté l’événement pertinent de création de règle :

1. Recherchez d’autres activités cloud suspectes provenant de la même adresse IP dans le client. Par exemple, une activité suspecte peut être plusieurs tentatives d’ouverture de session qui ont échoué. 
2. Le isp est-il courant et raisonnable pour cet utilisateur ?
3. L’emplacement est-il commun et raisonnable pour cet utilisateur ?

### <a name="investigate-any-suspicious-activity-with-the-user-inbox-before-creating-rules"></a>Examiner toute activité suspecte avec la boîte de réception de l’utilisateur avant de créer des règles

Vous pouvez passer en revue toutes les activités des utilisateurs avant de créer des règles, rechercher des indicateurs de compromission et examiner les actions de l’utilisateur qui semblent suspectes. Par exemple, plusieurs tentatives de signature ont échoué.  

- Se connecte : 

  Vérifier que l’activité de se connectant avant l’événement de création de règle n’est pas suspecte (par exemple, l’emplacement commun, le isp ou l’agent utilisateur). 

- Autres alertes ou incidents 

   - D’autres alertes se sont-elles déclenchées pour l’utilisateur avant la création de la règle . Si tel est le cas, cela peut indiquer que l’utilisateur a été compromis. 

   - Si l’alerte est en corrélation avec d’autres alertes pour indiquer un incident, l’incident contient-il d’autres alertes positives réelles ? 

## <a name="advanced-hunting-queries"></a>Requêtes de recherche avancées

[Le recherche avancée](advanced-hunting-overview.md) est un outil de recherche de menace basé sur une requête qui vous permet d’inspecter les événements de votre réseau et de localiser les indicateurs de menace. 

Exécutez cette requête pour rechercher tous les nouveaux événements de règle de boîte de réception au cours d’une fenêtre de temps spécifique.  

```kusto
let start_date = now(-10h); 
let end_date = now();
let user_id = ""; // enter here the user id
CloudAppEvents
| where Timestamp between (start_date .. end_date)
| where AccountObjectId == user_id
| where ActionType in ("Set-Mailbox", "New-InboxRule", "Set-InboxRule") //set new inbox rule related operations
| project Timestamp, ActionType, CountryCode, City, ISP, IPAddress, RuleConfig = RawEventData.Parameters, RawEventData
```

*RuleConfig contiendra* la configuration de règle.

Exécutez cette requête pour vérifier si le isp est courant pour l’utilisateur en regardant l’historique de l’utilisateur.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 30d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP 
```

Exécutez cette requête pour vérifier si le pays est commun à l’utilisateur en regardant l’historique de l’utilisateur.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 30d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

Exécutez cette requête pour vérifier si l’agent utilisateur est courant pour l’utilisateur en regardant l’historique de l’utilisateur.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 30d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by UserAgent
```

Exécutez cette requête pour vérifier si d’autres utilisateurs ont créé la règle de avance vers la même destination (cela peut indiquer que d’autres utilisateurs sont également compromis).

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
2. Réinitialisez les informations d’identification du compte de l’utilisateur. Vous pouvez également vérifier si le compte d’utilisateur a été compromis avec Microsoft Defender pour les applications cloud, ce qui obtient des signaux de sécurité de Azure Active Directory (Azure AD) Identity Protection.
3. Recherchez d’autres activités malveillantes effectuées par l’utilisateur touché.
4. Recherchez d’autres activités suspectes dans le client provenant de la même adresse IP ou du même isp (si ce n’est pas le cas) pour rechercher d’autres utilisateurs compromis.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la notation des alertes](alert-grading-playbooks.md)
- [Activité suspecte de transfert d’e-mail](alert-grading-playbook-email-forwarding.md)
- [Règles de manipulation de la boîte de réception suspectes](alert-grading-playbook-inbox-manipulation-rules.md)
- [Examiner des alertes](investigate-alerts.md)
