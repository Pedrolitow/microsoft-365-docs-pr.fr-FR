---
title: Notation des alertes pour les connecteurs d’échange malveillants
description: Alerter les destinataires de l’activité des connecteurs d’échange malveillants et protéger leur réseau contre les attaques malveillantes.
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
- m365-security
- tier2
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 83f7bdc0ac44b84953f760f31b5615ce793311f0
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68770463"
---
# <a name="alert-grading-for-malicious-exchange-connectors"></a>Notation des alertes pour les connecteurs d’échange malveillants

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

Les acteurs des menaces utilisent des connecteurs d’échange compromis pour envoyer du courrier indésirable et des e-mails d’hameçonnage en bloc à des destinataires qui ne se méfient pas en masquant des e-mails légitimes. Étant donné que le connecteur est compromis, les e-mails sont généralement approuvés par les destinataires. Ces types d’e-mails de hameçonnage sont des vecteurs courants pour les campagnes d’hameçonnage et le scénario de compromission des e-mails professionnels (BEC). Par conséquent, ces e-mails doivent être surveillés de manière intensive en raison de la probabilité de compromission des destinataires réussis.

Le playbook permet d’examiner les instances où des connecteurs malveillants sont configurés/déployés par des acteurs malveillants. En conséquence, ils prennent les mesures nécessaires pour corriger l’attaque et atténuer les risques de sécurité qui en découlent. Le playbook est disponible pour les équipes de sécurité telles que le centre des opérations de sécurité (SOC) et les administrateurs informatiques, qui examinent, gèrent/gèrent et classent les alertes. Le playbook permet de noter les alertes en tant que vrai positif (TP) ou faux positif (FP). S’il existe un tp, le playbook prend les mesures recommandées nécessaires pour corriger l’attaque.

Voici les résultats de l’utilisation d’un playbook :

- Détermination de l’alerte comme étant malveillante (TP) ou bénigne (FP).
- S’il est malveillant, corrigez/supprimez le connecteur malveillant de l’environnement.

## <a name="exchange-connectors"></a>Connecteurs Exchange

Les connecteurs Exchange sont un ensemble d’instructions qui personnalisent la façon dont vos e-mails circulent vers et depuis votre organisation Microsoft 365 ou Office 365. En règle générale, la plupart des organisations Microsoft 365 et Office 365 n’ont pas besoin de connecteurs pour le flux de messagerie standard.

Les connecteurs sont utilisés pour acheminer le trafic de courrier entre les systèmes de messagerie distants et les systèmes de messagerie Office 365 (O365) ou O365, et les systèmes de messagerie locaux.

## <a name="malicious-exchange-connectors"></a>Connecteurs Exchange malveillants

Les attaquants peuvent compromettre un connecteur d’échange existant ou compromettre un administrateur, et configurer un nouveau connecteur en envoyant des hameçonnages ou du courrier indésirable ou des e-mails en bloc.

Les indicateurs typiques d’un connecteur malveillant peuvent être trouvés lors de l’examen du trafic de courrier électronique et de ses en-têtes. Par exemple, lorsque le trafic de courrier électronique est observé à partir d’un nœud de connecteur avec une incompatibilité dans les adresses de l’expéditeur P1 (expéditeur d’en-tête) et P2 (expéditeur d’enveloppe), sans aucune information sur accountObjectId de l’expéditeur.

Cette alerte tente d’identifier de telles instances de flux de courrier, où l’activité d’envoi de courrier semble suspecte, ce qui ajoute à ce que les informations pertinentes sur l’expéditeur ne sont pas disponibles.

## <a name="playbook-workflow"></a>Flux de travail du playbook

Vous devez suivre la séquence pour identifier les connecteurs d’échange malveillants :

- Identifiez les comptes qui envoient des e-mails :
  - Les comptes semblent-ils compromis ?
- Identifiez le relais du connecteur sur les e-mails à vérifier :
  - Si le connecteur est censé envoyer des e-mails à volume élevé ?
  - Si le connecteur a été modifié ou créé récemment ?
- Les e-mails sont-ils envoyés à des adresses e-mail internes ?
  - Les e-mails sont-ils envoyés à des adresses externes (spam de pulvérisation et de prière)?
  - Les e-mails sont-ils envoyés à des adresses externes appartenant à des clients ou des fournisseurs (attaque de type chaîne d’approvisionnement) ?
- Vérifiez si les domaines de l’en-tête FROM et de l’expéditeur d’enveloppe sont identiques ou différents.

## <a name="investigating-malicious-connectors"></a>Examen des connecteurs malveillants

Cette section décrit les étapes à suivre pour examiner une alerte et corriger le risque de sécurité lié à cet incident.

- Déterminez si le connecteur présente un comportement incorrect (malveillant).
  - Recherchez les événements indiquant un trafic de courrier inhabituel et identifiez si un nouveau connecteur d’échange a été ajouté récemment.
    - Pour le trafic de courrier observé, déterminez si les comptes de messagerie sont compromis en vérifiant si les comptes sont responsables du trafic de courrier inhabituel.
  - Recherchez le contenu du courrier contenant des artefacts malveillants (liens/pièces jointes incorrects).
  - Recherchez les domaines qui ne font pas partie de votre environnement.
- Déterminez que les comptes de messagerie ne sont pas compromis. Identifiez le connecteur qui a été récemment ajouté ou modifié dans l’environnement.
- Rechercher :
  - Valeurs de champ dans l’expéditeur P1 (expéditeur d’en-tête d’e-mail) et l’expéditeur P2 (expéditeur d’enveloppe), et vérifiez s’il existe une incompatibilité.
  - Valeurs vides dans le champ SenderObjectId.
- Utilisez les données de télémétrie pour noter :
  - NetworkMessageId (ID de message) des e-mails envoyés à partir du connecteur malveillant.
  - La date de création du connecteur, la date de la dernière modification et la date de la dernière modification par date.
  - Adresse IP du connecteur à partir de laquelle le trafic de courrier électronique est observé.

## <a name="advanced-hunting-queries"></a>Requêtes de repérage avancées

Vous pouvez utiliser des requêtes [de repérage avancées](/microsoft-365/security/defender/advanced-hunting-overview?) pour collecter des informations relatives à une alerte et déterminer si l’activité est suspecte.

Vérifiez que vous avez accès aux tables suivantes :

|Nom de la table|Description|
|---|---|
|EmailEvents| Contient des informations relatives au flux de courrier électronique.|
|CloudAppEvents|Contient le journal d’audit des activités de l’utilisateur.|
|IdentityLogonEvents|Contient des informations de connexion pour tous les utilisateurs.|

## <a name="references"></a>References

Exemples AHQs pour référence :

- Exécutez ce KQL pour vérifier la création d’un nouveau connecteur.

  ```KQL
  //modify timeWindow to modify the lookback.
  let timeWindow = now(-7d); let timeNow = now();
  CloudAppEvents
  | where Timestamp between (timeWindow .. timeNow)
  | where isnotempty(AccountObjectId)
  | where ActionType == "New-InboundConnector"
  | mvexpand property = RawEventData.Parameters
  | extend ConnectorName = iff(property.Name == "Name", property.Value, ""), 
  IsEnabled = iff((property.Name == "Enabled" and property.Value == "True"), 
  true, false)
  | where isnotempty( ConnectorName) or IsEnabled
  | project-reorder ConnectorName, IsEnabled
  ```

- Exécutez ce KQL pour vérifier le volume d’événements du connecteur alerté avec la fenêtre de temps avant et après les alertes.

  ```KQL
  //modify timeWindow to modify the lookback.
  let timeWindow = now(-7d); let timeNow = now();
  let connectorOperations = pack_array("Set-OutboundConnector", 
  "New-OutboundConnector", "Set-InboundConnector", "New-InboundConnector");
  let mailThreshold = 100; //define threshold for inspection and filtering
  let myConnector= //use this code block to specify relevant connector(s)
  CloudAppEvents
  | where Timestamp between (timeWindow .. timeNow)
  | where ActionType has_any (connectorOperations)
  | mv-expand property = RawEventData.Parameters
  | where property.Name == "Name"
  | summarize by ConnectorName=tostring(property.Value)
  ;
  EmailEvents
  | where isnotempty( toscalar (myConnector))
  | where Timestamp between (timeWindow .. timeNow)
  | where isnotempty( SenderObjectId) and isnotempty( Connectors)
  | where Connectors in (toscalar (myConnector))
  | summarize MailCount = dcount(NetworkMessageId) by Connectors, 
  SenderObjectId, bin(Timestamp, 1h)
  | where MailCount >= mailThreshold
   ```

- Exécutez ce KQL pour vérifier si les e-mails sont envoyés à des domaines externes.

  ```KQL
  //modify timeWindow to modify the lookback.
  let timeWindow = now(-7d); let timeNow = now();
  EmailEvents
  | where Timestamp between (timeWindow .. timeNow)
  | where isnotempty( SenderObjectId)
  | extend RecipientDomain= split(RecipientEmailAddress, "@")[1]
  | where (SenderFromDomain != RecipientDomain) or (SenderMailFromDomain 
  != RecipientDomain)
  | where EmailDirection !in ("Intra-org" , "Inbound") //comment this line to 
  look across all mailflow directions
  ```

  - En cas d’envoi à des domaines externes, qui d’autre dans l’environnement envoie des e-mails similaires (peut indiquer l’utilisateur compromis si le destinataire est un domaine inconnu).

     ```KQL
     //modify timeWindow to modify the lookback.
     let timeWindow = now(-7d); let timeNow = now();
     let countThreshold= 100; //modify count threshold accordingly 
     EmailEvents
     | where Timestamp between (timeWindow .. timeNow)
     | where isnotempty( SenderObjectId)
     | extend RecipientDomain= split(RecipientEmailAddress, "@")[1]
     | where (SenderFromDomain != RecipientDomain) or (SenderMailFromDomain 
     != RecipientDomain)
     | where EmailDirection !in ("Intra-org" , "Inbound")
     | summarize MailCount= dcount(NetworkMessageId) by SenderObjectId, 
     SenderFromAddress, SenderMailFromAddress , bin(Timestamp, 1h)
     | where MailCount > countThreshold
     ```

    - Vérifier le contenu du courrier à l’aide d’un comportement incorrect
    - Examinez les URL dans l’e-mail ou l’e-mail contenant des pièces jointes.

## <a name="ahq-considerations"></a>Considérations relatives à AHQ

Voici les considérations relatives à AHQ pour la protection des destinataires contre les attaques malveillantes.

- Recherchez les connexions d’administrateur pour ceux qui gèrent fréquemment des connecteurs à partir d’emplacements inhabituels (générer des statistiques et exclure les emplacements où la plupart des connexions réussies sont observées).

- Recherchez les échecs de connexion à partir d’emplacements inhabituels.

  ```
  //modify timeWindow to modify the lookback.
  let timeWindow = now(-7d); let timeNow = now();
  let logonFail= materialize (
  IdentityLogonEvents
  | where Timestamp between (timeWindow .. timeNow)
  | where isnotempty(AccountObjectId)
  | where Application != "Active Directory"
  | where ActionType == "LogonFailed"
  | where ISP != "Microsoft Azure"
  | summarize failedLogonCount=count(), LatestTime = max(Timestamp), 
  EarliestTime = min(Timestamp) by AccountObjectId, Application, ISP, 
  CountryCode, bin(Timestamp, 60s)
  | where failedLogonCount > 100);
  // let hasLogonFails = isnotempty(toscalar (logonFail));
  let logonFailUsers = materialize ( logonFail | distinct AccountObjectId | 
  take 100);
  let hasLogonFails = isnotempty(toscalar (logonFailUsers));
  let logonSuccess=
  IdentityLogonEvents
  | where hasLogonFails
  | where Timestamp between (timeWindow .. timeNow)
  | where AccountObjectId in (logonFailUsers)
  | where Application != "Active Directory"
  | where ISP != "Microsoft Azure"
  | where ActionType == "LogonSuccess"
  | project SuccessTime= Timestamp, ReportId, AccountUpn, AccountObjectId, 
  ISP, CountryCode, Application;
  logonFail
  | join kind = innerunique logonSuccess on AccountObjectId, ISP, Application
  | where SuccessTime between (LatestTime .. (LatestTime + 10s))
  | summarize arg_min(SuccessTime, ReportId), EarliestFailedTime=min
  (EarliestTime), LatestFailedTime=max(LatestTime), failedLogonCount=
  take_any(failedLogonCount), SuccessLogonCount=count(), ISPSet=
  make_set(ISP), CountrySet=make_set(CountryCode), AppSet=make_set
  (Application) by AccountObjectId, AccountUpn
  | project-rename Timestamp=SuccessTime
  ```

## <a name="recommended-actions"></a>Actions recommandées

Une fois qu’il est déterminé que les activités d’alerte observées font partie de TP, classifiez ces alertes et effectuez les actions ci-dessous :

- Désactivez ou supprimez le connecteur qui s’est avéré malveillant.
- Si le compte administrateur a été compromis, réinitialisez les informations d’identification du compte de l’administrateur. En outre, désactivez/révoquez les jetons pour le compte administrateur compromis et activez l’authentification multifacteur pour tous les comptes d’administrateur.
- Recherchez les activités suspectes effectuées par l’administrateur.
- Recherchez d’autres activités suspectes sur d’autres connecteurs dans l’environnement.
