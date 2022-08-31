---
title: Classement des alertes pour les connecteurs d’échange malveillants
description: Alerte grading recipients from malicious exchange connectors activity and protect their network from malicious attack.
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
ms.openlocfilehash: 16f168fc772e4b4c9e7f48221dbd14039690ba83
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67480232"
---
# <a name="alert-grading-for-malicious-exchange-connectors"></a>Classement des alertes pour les connecteurs d’échange malveillants

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

Les acteurs des menaces utilisent des connecteurs Exchange compromis pour envoyer des courriers indésirables et de hameçonnage en bloc à des destinataires peu fiables en masquant des e-mails légitimes. Étant donné que le connecteur est compromis, les e-mails sont généralement approuvés par les destinataires. Ces types d’e-mails de hameçonnage sont des vecteurs courants pour les campagnes de hameçonnage et le scénario de compromission de la messagerie professionnelle (BEC). Par conséquent, ces e-mails doivent être fortement surveillés en raison de la probabilité que les compromis des destinataires réussis soient élevés.

Le playbook permet d’examiner les instances, où les connecteurs malveillants sont configurés/déployés par des acteurs malveillants. En conséquence, ils prennent les mesures nécessaires pour corriger l’attaque et atténuer les risques de sécurité qui en découlent. Le playbook est disponible pour les équipes de sécurité telles que le Centre des opérations de sécurité (SOC) et les administrateurs informatiques, qui examinent, gèrent/gèrent et classent les alertes. Le playbook vous aidera à noter les alertes en tant que Vrais Positifs (TP) ou Faux Positif (FP). S’il existe un protocole TP, le playbook prend les actions recommandées nécessaires pour corriger l’attaque.

Voici les résultats de l’utilisation d’un playbook :

- Détermination de l’alerte comme étant malveillante (TP) ou bénigne (FP). 
    - En cas de malveillance, corrigez/supprimez le connecteur malveillant de l’environnement.

## <a name="exchange-connectors"></a>Connecteurs Exchange

Les connecteurs Exchange sont une collection d’instructions qui personnalisent la façon dont vos e-mails circulent vers et depuis votre organisation Microsoft 365 ou Office 365. En règle générale, la plupart des organisations Microsoft 365 et Office 365 n’ont pas besoin de connecteurs pour un flux de courrier régulier.

Les connecteurs sont utilisés pour acheminer le trafic de messagerie entre les systèmes de messagerie distants et Office 365 (O365) ou O365, et les systèmes de messagerie locaux.

## <a name="malicious-exchange-connectors"></a>Connecteurs Exchange malveillants

Les attaquants peuvent compromettre un connecteur Exchange existant ou compromettre un administrateur, et configurer un nouveau connecteur en envoyant des e-mails phish ou spam/en bloc. 

Les indicateurs typiques d’un connecteur malveillant sont disponibles lorsque vous examinez le trafic de messagerie et ses en-têtes. Par exemple, lorsque le trafic de courrier électronique est observé à partir d’un nœud de connecteur avec une incompatibilité dans les adresses d’expéditeur P1 (expéditeur d’en-tête) et P2 (expéditeur d’enveloppe), sans aucune information sur AccountObjectId de l’expéditeur.

Cette alerte tente d’identifier de telles instances de flux de messagerie, dans lesquelles l’activité d’envoi de courrier semble suspecte et que l’ajout d’informations pertinentes sur l’expéditeur n’est pas disponible. 
 
## <a name="playbook-workflow"></a>Flux de travail de playbook

Vous devez suivre la séquence pour identifier les connecteurs d’échange malveillants :

- Identifiez les comptes qui envoient des e-mails :
  - Les comptes semblent-ils compromis ?
- Identifiez le connecteur relayant sur les e-mails à vérifier :
  - Si le connecteur est censé envoyer des e-mails à volume élevé ?
  - Si le connecteur a été modifié ou créé récemment ?
- Les e-mails sont-ils envoyés à des adresses e-mail internes ?
  - Les e-mails sont-ils envoyés à des adresses externes (pulvériser et prier le courrier indésirable) ?
  - Les e-mails sont-ils envoyés à des adresses externes appartenant à des clients ou à des fournisseurs (attaque de type chaîne d’approvisionnement) ?
- Vérifiez si les domaines d’en-tête FROM et d’expéditeur d’enveloppe sont identiques ou différents.

## <a name="investigating-malicious-connectors"></a>Examen des connecteurs malveillants

Cette section décrit les étapes à suivre pour examiner une alerte et corriger le risque de sécurité dû à cet incident.

- Déterminez si le connecteur illustre un comportement incorrect (malveillant).
  - Recherchez les événements indiquant le trafic de courrier inhabituel et identifiez si un nouveau connecteur Exchange a été ajouté récemment.
    - Pour le trafic de courrier observé, déterminez si les comptes de messagerie sont compromis en inspectant si les comptes sont responsables du trafic de courrier inhabituel.
  - Recherchez le contenu du courrier contenant des artefacts malveillants (liens/pièces jointes incorrects).
  - Recherchez les domaines qui ne font pas partie de votre environnement. 
- Déterminez que les comptes de messagerie ne sont pas compromis. Identifiez le connecteur qui a été récemment ajouté ou modifié dans l’environnement.
- Rechercher : 
  - Les valeurs de champ dans l’expéditeur P1 (expéditeur d’en-tête d’e-mail) et l’expéditeur P2 (expéditeur d’enveloppe) et vérifient s’il existe une incompatibilité.
  - Valeurs vides dans le champ SenderObjectId.
- Utilisez les données de télémétrie pour noter :
  - NetworkMessageId (ID de message) des e-mails envoyés à partir du connecteur malveillant. 
  - Date de création du connecteur, date de dernière modification et dernière modification par date.
  - Adresse IP du connecteur à partir de laquelle le trafic de messagerie est observé.
  
## <a name="advanced-hunting-queries"></a>Requêtes de chasse avancées

Vous pouvez utiliser des requêtes de [chasse avancées](/microsoft-365/security/defender/advanced-hunting-overview?) pour collecter des informations relatives à une alerte et déterminer si l’activité est suspecte. 

Vérifiez que vous avez accès aux tableaux suivants :

|**Nom de la table**  |**Description**  |
|---------|---------|
|EmailEvents| Contient des informations relatives au flux de courrier électronique.|
|CloudAppEvents|Contient le journal d’audit des activités utilisateur.|
|IdentityLogonEvents|Contient des informations de connexion pour tous les utilisateurs.|

## <a name="references"></a>References

Exemples AHQs pour référence :

- Exécutez ce KQL pour vérifier la création d’un nouveau connecteur.
  ```
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
- Run this KQL to check the volume of events from the alerted connector with time window of before and after the alerts.
  ```
  modifier timeWindow pour modifier la recherche.
  let timeWindow = now(-7d); let timeNow = now(); let connectorOperations = pack_array(« Set-OutboundConnector », « New-OutboundConnector », « Set-InboundConnector », « New-InboundConnector »); let mailThreshold = 100; définir un seuil pour l’inspection et le filtrage permet à myConnector= //d’utiliser ce bloc de code pour spécifier le ou les connecteurs cloudAppEvents appropriés | où Timestamp entre (timeWindow .. timeNow) | où ActionType has_any (connectorOperations) | propriété mv-expand = RawEventData.Parameters | where, propriété. Name == « Name » | summarize by ConnectorName=tostring(property. Valeur) ; EmailEvents | where isnotempty( toscalar (myConnector)) | où Timestamp entre (timeWindow .. timeNow) | where isnotempty( SenderObjectId) et isnotempty( Connectors) | où les connecteurs dans (toscalar (myConnector)) | summarize MailCount = dcount(NetworkMessageId) by Connectors, SenderObjectId, bin(Timestamp, 1h) | where MailCount >= mailThreshold
   ```
- Run this KQL to check whether emails are being sent to external domains.
  ```
  modifier timeWindow pour modifier la recherche.
  let timeWindow = now(-7d); let timeNow = now(); EmailEvents | où Timestamp entre (timeWindow .. timeNow) | where isnotempty( SenderObjectId) | extend RecipientDomain= split(RecipientEmailAddress, « @ »)[1] | where (SenderFromDomain != RecipientDomain) ou (SenderMailFromDomain != RecipientDomain) | où EmailDirection !in (« Intra-org », « Entrant ») //commentez cette ligne pour examiner toutes les directions de flux de courrier
  ```
  - If sent to external domains, who else in the environment is sending similar emails (Could indicate compromised user if recipient is unknown domain).
     ```
     modifier timeWindow pour modifier la recherche.
     let timeWindow = now(-7d); let timeNow = now(); let countThreshold= 100; modifier le seuil de nombre en conséquence EmailEvents | où Timestamp entre (timeWindow .. timeNow) | where isnotempty( SenderObjectId) | extend RecipientDomain= split(RecipientEmailAddress, « @ »)[1] | where (SenderFromDomain != RecipientDomain) ou (SenderMailFromDomain != RecipientDomain) | où EmailDirection !in (« Intra-org », « Entrant ») | summarize MailCount= dcount(NetworkMessageId) by SenderObjectId, SenderFromAddress, SenderMailFromAddress , bin(Timestamp, 1h) | où MailCount > countThreshold
     ```
    - Check the mail content for bad behavior
      - Look at URLs in the email or email having attachments.


## AHQ considerations

Following are the AHQ considerations for protecting the recipients from malicious attack.

- Check for admin logins for those who frequently manage connectors from unusual locations (generate stats and exclude locations from where most successful logins are observed).

  - Look for login failures from unusual locations.

  ```
  modifier timeWindow pour modifier la recherche.
  let timeWindow = now(-7d); let timeNow = now(); let logonFail= material ( IdentityLogonEvents | where Timestamp between (timeWindow .. timeNow) | where isnotempty(AccountObjectId) | where Application != « Active Directory » | où ActionType == « LogonFailed » | where ISP != « Microsoft Azure » | summarize failedLogonCount=count(), LatestTime = max(Timestamp), EarliestTime = min(Timestamp) by AccountObjectId, Application, ISP, CountryCode, bin(Timestamp, 60s) | où failedLogonCount > 100); let hasLogonFails = isnotempty(toscalar (logonFail)); let logonFailUsers = material (logonFail | distinct AccountObjectId | take 100); let hasLogonFails = isnotempty(toscalar (logonFailUsers)); let logonSuccess= IdentityLogonEvents | où hasLogonFails | où Timestamp entre (timeWindow .. timeNow) | où AccountObjectId in (logonFailUsers) | where Application != « Active Directory » | where ISP != « Microsoft Azure » | where ActionType == « LogonSuccess » | project SuccessTime= Timestamp, ReportId, AccountUpn, AccountObjectId, ISP, CountryCode, Application; logonFail | join kind = innerunique logonSuccess on AccountObjectId, ISP, Application | où SuccessTime entre (LatestTime .. (LatestTime + 10s)) | summarize arg_min(SuccessTime, ReportId), EarliestFailedTime=min (EarliestTime), LatestFailedTime=max(LatestTime), failedLogonCount= take_any(failedLogonCount), SuccessLogonCount=count(), ISPSet= make_set(ISP), CountrySet=make_set(CountryCode), AppSet=make_set (Application) par AccountObjectId, AccountUpn | project-rename Timestamp=SuccessTime
  ```

## Recommended actions

Once it’s determined that the observed alert activities are part of TP, classify those alerts and perform the actions below:

- Disable or remove the connector that was found to be malicious.
- If the admin account was compromised, reset the admin’s account credentials. Also, disable/revoke tokens for the compromised admin account and enable multi-factor authentication for all admin accounts.
  - Look for suspicious activities performed by the admin.
- Check for other suspicious activities across other connectors in the environment.
