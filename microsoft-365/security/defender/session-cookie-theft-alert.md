---
title: Notation d’alerte pour l’alerte de vol de cookie de session
description: Passez en revue, gérez et classez l’alerte de vol de cookie de session en tant que vrai positif (TP) ou faux positif (FP), et s’il y a tp, prenez les mesures recommandées pour corriger l’attaque et atténuer les risques de sécurité qui en découlent.
keywords: incidents, alertes, investigation, analyse, réponse, corrélation, attaque, ordinateurs, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365, vol de cookies, AiTM, Attaquant dans le milieu, Adversaire dans le milieu, vol de session, vol de cookies aïm, vol de session aitm.
search.appverid: met150
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
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.openlocfilehash: a3fb894a2ba2ce675b904d95df45a388e4c3100e
ms.sourcegitcommit: a250d043a2e42ecbc7b86147468d1660af5a6ba7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68673368"
---
# <a name="alert-grading-for-session-cookie-theft-alert"></a>Notation d’alerte pour l’alerte de vol de cookie de session 
 
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Cet article contient des informations sur la notation des alertes pour les alertes de vol de cookie de session dans Microsoft 365 Defender :

- **Le cookie de session volé a été utilisé**
- **Demande d’authentification à partir de la page d’hameçonnage liée à AiTM**

Les acteurs des menaces ont commencé à utiliser des méthodes innovantes pour infiltrer leurs environnements cibles. S’inspirant des attaques de l’adversaire dans le milieu, ce type d’attaque utilise l’hameçonnage pour voler des informations d’identification ou leur session de connexion afin d’effectuer des actions malveillantes. Les campagnes du BEC en sont un excellent exemple.

Cette attaque fonctionne en configurant un site intermédiaire (hameçonnage), fonctionnant efficacement comme une connexion proxy entre l’utilisateur et le site web légitime que l’attaquant emprunte l’identité. En agissant en tant qu’intermédiaire (proxy), l’attaquant est en mesure de voler le mot de passe et le cookie de session de la cible. L’attaquant est donc en mesure de s’authentifier auprès d’une session légitime au fur et à mesure qu’il s’authentifie pour le compte de l’utilisateur.

Ce playbook permet d’enquêter sur les cas où un comportement suspect est observé indiquant un type d’attaque de type AiTM (Attack-in-the-middle) pour le vol de cookies. Cela permet aux équipes de sécurité telles que le centre d’opérations de sécurité (SOC) et les administrateurs informatiques d’examiner, de gérer et de noter les alertes en tant que vrai positif (TP) ou faux positif (FP), et s’il s’agit de TP, prendre les mesures recommandées pour corriger l’attaque et atténuer les risques de sécurité qui en découlent. 

Les résultats de l’utilisation de ce playbook sont les suivants :

- Vous avez identifié les alertes associées à AiTM comme des activités malveillantes (TP) ou bénignes (FP).
- Si vous êtes identifié comme malveillant, vous avez pris les mesures nécessaires pour corriger l’attaque.

## <a name="investigating-steps"></a>Examen des étapes

1. Déterminez si l’utilisateur affecté a déclenché d’autres alertes de sécurité. 
 
    - Concentrez-vous sur les alertes basées sur des anomalies d’emplacement géographique pour les `[AadSignInEventsBeta or IdentityLogonEvents]`connexions .
    - Recherchez les événements de connexion pertinents en examinant les informations `[AadSignInEventsBeta]`d’ID de session .
        - Recherchez les événements associés à l’ID de session identifié (volé) pour suivre les activités effectuées à l’aide du cookie `[CloudAppEvents]`volé . 
        - Recherchez une différence de temps entre les activités de connexion où il existe une différence dans l’emplacement géographique. Plusieurs sessions ne doivent pas être possibles pour le même compte avec des emplacements différents (indiquant que la session peut être volée). 
    - Recherchez les alertes générées pour le compte à partir de l’hôte d’entreprise. 
        - Si le compte est compromis, il peut y avoir des alertes qui précèdent la compromission indiquant des attaques, par exemple, les alertes `[NetworkConnectionEvents]`SmartScreen . 

2. Examiner les comportements suspects.
    - Recherchez les événements indiquant des modèles inhabituels pour identifier les modèles suspects, tels que les propriétés inhabituelles `[CloudAppEvents]` pour les utilisateurs comme isp/pays/ville, etc.
    - Recherchez les événements qui indiquent des activités nouvelles ou précédemment invisibles, telles que des tentatives de connexion [réussite/échec] dans des services nouveaux ou jamais utilisés, une augmentation de l’activité d’accès à la messagerie, une modification de l’utilisation des ressources Azure, etc.
    - Examinez toutes les modifications récentes dans votre environnement à partir de :
        - Office 365 applications (telles que les modifications d’autorisation Exchange Online, le transfert automatique ou la redirection de courrier)  
        - PowerApps (comme la configuration de la transmission automatisée de données via PowerAutomate)
        - Environnements Azure (par exemple, modifications d’abonnement Portail Azure, etc.) 
        - SharePoint Online (accès à plusieurs sites, ou pour les fichiers qui ont du contenu sensible comme les informations d’identification ou les états financiers), etc.)
    - Inspectez les opérations observées sur plusieurs plateformes (EXO, SPO, Azure, etc.) dans un court laps de temps pour l’utilisateur concerné.
        - Par exemple, les chronologies des événements d’audit des opérations de lecture/d’envoi de messages et d’allocation/modifications de ressources Azure (provisionnement ou ajout d’une nouvelle machine à AAD) ne doivent pas coïncider entre elles.
             
3. Examiner les attaques de suivi possibles. Les attaques AiTM sont généralement un moyen de bout en bout et non un jeu final. Inspectez donc votre environnement à la recherche d’autres attaques qui suivent pour les comptes affectés.
    - Un exemple serait d’examiner les cas BEC 
        - Recherchez les activités de recherche affichées dans la boîte aux lettres `[CloudAppEvents]`du compte d’utilisateur alerté.
            - Les activités de recherche dans la boîte aux lettres peuvent avoir des mots clés observés dans des fraudes financières (par exemple, factures, paiements, etc.), qui sont suspects. 
            - Recherchez également les règles de boîte de réception créées avec l’intention de déplacer et de marquer comme lu (quelque chose sur les lignes actionType dans (New-InboxRule, UpdateInboxRules, Set-InboxRule) et RawEventData has_all (MarkAsRead, MoveToFolder, Archive)).
    - Recherchez les événements de flux de messagerie [EmailEvents & EmailUrlInfo sur NetworkMessageId] où les e-mails multiples sont envoyés avec la même URL.  
        - Vérifiez si une augmentation ou un volume élevé de suppression de courrier (ActivityType as Trash ou Delete) est observé `[CloudAppEvents]` pour le compte de boîte aux lettres. 
        - Le comportement de correspondance peut être considéré comme hautement suspect. 
    - Examinez les événements d’appareil pour les événements d’URL qui correspondent aux événements de clic pour les `[DeviceEvents on AccountName|AccountUpn]` e-mails Office365. 
        - La correspondance des événements pour les sources de clic (par exemple, différentes adresses IP pour la même URL) peut indiquer un comportement malveillant. 

## <a name="advanced-hunting-queries"></a>Requêtes de chasse avancées 

[La chasse avancée](advanced-hunting-overview.md) est un outil de repérage des menaces basé sur des requêtes qui vous permet d’inspecter les événements de votre réseau et de localiser les indicateurs de menace. Utilisez ces requêtes pour collecter plus d’informations relatives à l’alerte et déterminer si l’activité est suspecte.

Vérifiez que vous avez accès aux tables suivantes :

- AadSignInEventsBeta : contient des informations de connexion pour les utilisateurs.
- IdentityLogonEvents : contient des informations de connexion pour les utilisateurs.
- CloudAppEvents : contient les journaux d’audit des activités utilisateur.
- EmailEvents : contient des informations sur le flux/le trafic de messagerie.
- EmailUrlInfo : contient les informations d’URL contenues dans les e-mails.
- UrlClickEvents : contient des journaux de clic d’URL pour les URL qui ont été cliquées dans les e-mails.
- DeviceEvents : contient les événements d’audit de l’activité de l’appareil.

Utilisez la requête ci-dessous pour identifier un comportement d’ouverture de session suspect :

```kusto
let OfficeHomeSessionIds = 
AADSignInEventsBeta
| where Timestamp > ago(1d)
| where ErrorCode == 0
| where ApplicationId == "4765445b-32c6-49b0-83e6-1d93765276ca" //OfficeHome application 
| where ClientAppUsed == "Browser" 
| where LogonType has "interactiveUser" 
| summarize arg_min(Timestamp, Country) by SessionId;
AADSignInEventsBeta
| where Timestamp > ago(1d)
| where ApplicationId != "4765445b-32c6-49b0-83e6-1d93765276ca"
| where ClientAppUsed == "Browser" 
| project OtherTimestamp = Timestamp, Application, ApplicationId, AccountObjectId, AccountDisplayName, OtherCountry = Country, SessionId
| join OfficeHomeSessionIds on SessionId
| where OtherTimestamp > Timestamp and OtherCountry != Country
```
Utilisez la requête ci-dessous pour identifier les pays rares : 

```kusto
AADSignInEventsBeta 
| where Timestamp > ago(7d) 
| where ApplicationId == "4765445b-32c6-49b0-83e6-1d93765276ca" //OfficeHome application 
| where ClientAppUsed == "Browser" 
| where LogonType has "interactiveUser" 
| summarize Countries = make_set(Country) by AccountObjectId, AccountDisplayName
```
Utilisez cette requête pour rechercher les nouvelles règles de boîte de réception de courrier électronique créées pendant une session de connexion suspecte : 

```kusto
//Find suspicious tokens tagged by AAD "Anomalous Token" alert
let suspiciousSessionIds = materialize(
AlertInfo
| where Timestamp > ago(7d)
| where Title == "Anomalous Token"
| join (AlertEvidence | where Timestamp > ago(7d) | where EntityType == "CloudLogonSession") on AlertId
| project sessionId = todynamic(AdditionalFields).SessionId);
//Find Inbox rules created during a session that used the anomalous token
let hasSuspiciousSessionIds = isnotempty(toscalar(suspiciousSessionIds));
CloudAppEvents
| where hasSuspiciousSessionIds
| where Timestamp > ago(21d)
| where ActionType == "New-InboxRule"
| where RawEventData.SessionId in (suspiciousSessionIds)
```

## <a name="recommended-actions"></a>Actions recommandées 

Une fois que vous avez déterminé que les activités d’alerte sont malveillantes, classifiez ces alertes comme étant vraies positives (TP) et effectuez les actions suivantes :

- Réinitialisez les informations d’identification du compte de l’utilisateur. En outre, désactivez/révoquez des jetons pour le compte compromis.
- Si les artefacts trouvés étaient liés à la messagerie, configurez le bloc en fonction de l’adresse IP de l’expéditeur et des domaines de l’expéditeur.
    - Les domaines qui sont typo-squattés peuvent soit effacer les stratégies DMARC, DKIM, SPF (car le domaine est complètement différent), soit retourner des résultats « null » (car il n’est probablement pas configuré par l’acteur de menace).
- Bloquez les URL ou adresses IP (sur les plateformes de protection réseau) qui ont été identifiées comme malveillantes pendant l’enquête.  

## <a name="see-also"></a>Voir aussi

[Du vol de cookie au BEC](https://www.microsoft.com/security/blog/2022/07/12/from-cookie-theft-to-bec-attackers-use-aitm-phishing-sites-as-entry-point-to-further-financial-fraud/)

   
