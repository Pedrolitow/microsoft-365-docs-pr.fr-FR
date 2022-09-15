---
title: Alerte suspecte d’activité d’adresse IP liée à la pulvérisation de mots de passe
description: Classement des alertes pour l’activité suspecte d’adresse IP liée à la pulvérisation de mots de passe pour passer en revue les alertes et prendre les mesures recommandées pour corriger l’attaque et protéger votre réseau.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, appareils, utilisateurs, 365, microsoft, m365, mot de passe, pulvérisation, classification des alertes, classement des alertes, applications cloud, adresse IP suspecte
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: v-dgali
author: dgali297
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
ms.openlocfilehash: ac9e4b9618350d22461b1bd8452d8ca2dc6cf6a3
ms.sourcegitcommit: b1ed6470645455c2f1fcf467450debc622c40147
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67711086"
---
# <a name="suspicious-password-spray-related-ip-activity"></a>Activité d’adresse IP suspecte liée à la pulvérisation de mots de passe

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Les acteurs des menaces utilisent des techniques de devinage de mot de passe pour accéder aux comptes d’utilisateur. Dans une attaque par pulvérisation de mots de passe, l’acteur de menace peut recourir à quelques-uns des mots de passe les plus utilisés sur de nombreux comptes différents. Les attaquants compromettent correctement les comptes à l’aide de la pulvérisation de mots de passe, car de nombreux utilisateurs utilisent toujours des mots de passe par défaut et faibles.

Ce guide vous aide à examiner les instances où des adresses IP ont été étiquetées à risque ou associées à une attaque par pulvérisation de mots de passe, ou des activités suspectes inexpliquées ont été détectées, telles qu’un utilisateur se connectant à partir d’un emplacement inconnu ou un utilisateur qui reçoit des invites d’authentification multifacteur inattendues (MFA). Ce guide s’applique aux équipes de sécurité telles que le Centre des opérations de sécurité (SOC) et les administrateurs informatiques qui examinent, gèrent/gèrent et classifient les alertes. Ce guide permet de classer rapidement les alertes en tant que [vrais positifs (TP) ou faux positifs (FP)](investigate-alerts.md) et, dans le cas de TP, de prendre des mesures recommandées pour corriger l’attaque et atténuer les risques de sécurité.

Les résultats prévus de l’utilisation de ce guide sont les suivants :

- Vous avez identifié les alertes associées aux adresses IP de pulvérisation de mots de passe comme des activités malveillantes (TP) ou faux positifs (FP).

- Vous avez pris les mesures nécessaires si des adresses IP ont effectué des attaques par pulvérisation de mots de passe.

## <a name="investigation-steps"></a>Étapes d’investigation

Cette section contient des instructions pas à pas pour répondre à l’alerte et prendre les mesures recommandées pour protéger votre organisation contre d’autres attaques.

### <a name="1-review-the-alert"></a>1. Examiner l’alerte

Voici un exemple d’alerte de pulvérisation de mot de passe dans la file d’attente d’alertes :

:::image type="content" source="../../media/alert-grading-playbook-password-spray/fig1-password-spray-alert.png" alt-text="Capture d’écran de l’alerte Microsoft Defender 365." lightbox="../../media/alert-grading-playbook-password-spray/fig1-password-spray-alert.png":::

Cela signifie qu’il existe une activité utilisateur suspecte provenant d’une adresse IP qui peut être associée à une tentative de pulvérisation de force brute ou de mot de passe selon des sources de renseignement sur les menaces.

### <a name="2-investigate-the-ip-address"></a>2. Examiner l’adresse IP
-   Examinez les [activités](microsoft-365-security-center-defender-cloud-apps.md) qui proviennent de l’adresse IP :

    - **S’agit-il principalement d’échecs de connexion ?**

    - **L’intervalle entre les tentatives de connexion est-il suspect ?** Les attaques par pulvérisation de mots de passe automatisées ont tendance à avoir un intervalle de temps régulier entre les tentatives.

    - **Existe-t-il des tentatives réussies de connexion d’un utilisateur/de plusieurs utilisateurs avec des invites [MFA](/microsoft-365/admin/security-and-compliance/multi-factor-authentication-microsoft-365) ?** L’existence de ces tentatives peut indiquer que l’adresse IP n’est pas malveillante.

    - **Les protocoles hérités sont-ils utilisés ?** L’utilisation de protocoles tels que POP3, IMAP et SMTP peut indiquer une tentative d’attaque par pulvérisation de mot de passe. La recherche `Unknown(BAV2ROPC)` dans l’agent utilisateur (type d’appareil) dans le [journal d’activité](/defender-cloud-apps/activity-filters#ip-address-insights) indique l’utilisation de protocoles hérités. Vous pouvez vous reporter à l’exemple ci-dessous lorsque vous examinez le journal d’activité. Cette activité doit être corrélée à d’autres activités.

        :::image type="content" source="../../media/alert-grading-playbook-password-spray/fig2-password-spray-alert.png" alt-text="Capture d’écran de l’interface Microsoft Defender 365 montrant le type d’appareil." lightbox="../../media/alert-grading-playbook-password-spray/fig2-password-spray-alert.png":::

        _Figure 1. Le champ Type d’appareil affiche `Unknown(BAV2ROPC)` l’agent utilisateur dans Microsoft 365 Defender._ 
    - **Vérifiez l’utilisation de proxys anonymes ou du réseau Tor.** Les acteurs de menace utilisent souvent ces proxys alternatifs pour masquer leurs informations, ce qui les rend difficiles à tracer. Toutefois, l’utilisation de ces proxys n’est pas toutes corrélées avec des activités malveillantes. Vous devez examiner d’autres activités suspectes susceptibles de fournir de meilleurs indicateurs d’attaque.
    - L’adresse IP provient-elle d’un réseau privé virtuel (VPN) ? Le VPN est-il digne de confiance ? **Vérifiez si l’adresse IP provient d’un VPN et examinez l’organisation derrière elle à l’aide d’outils** tels [que RiskIQ](https://community.riskiq.com/learn-more/enterprise). 
    - **Vérifiez les autres adresses IP avec le même sous-réseau/fournisseur d’identité.** Parfois, les attaques par pulvérisation de mot de passe proviennent de nombreuses adresses IP différentes au sein du même sous-réseau/fournisseur d’identité.
-   **L’adresse IP est-elle commune pour le locataire ?** Vérifiez le journal d’activité pour voir si le locataire a vu l’adresse IP au cours des 30 derniers jours.
-   **Recherchez d’autres activités suspectes ou alertes provenant de l’adresse IP dans le locataire.** Les exemples d’activités à rechercher peuvent inclure la suppression d’e-mail, la création de règles de transfert ou les téléchargements de fichiers après une tentative de connexion réussie.
-   **Vérifiez le score de risque de l’adresse IP** à l’aide d’outils tels que RiskIQ.
    
### <a name="3-investigate-suspicious-user-activity-after-signing-in"></a>3. Examiner l’activité suspecte des utilisateurs après la connexion
Une fois qu’une adresse IP suspecte est reconnue, vous pouvez examiner les comptes qui se sont connectés. Il est possible qu’un groupe de comptes ait été compromis et utilisé avec succès pour se connecter à partir de l’adresse IP ou d’autres adresses IP similaires.

Filtrez toutes les tentatives de connexion réussies à partir de l’adresse IP autour et peu après l’heure des alertes. Recherchez ensuite les activités malveillantes ou inhabituelles dans ces comptes après la connexion. 
-   Activités de compte d’utilisateur

    **Vérifiez que l’activité dans le compte précédant l’activité de pulvérisation de mot de passe n’est pas suspecte.** Par exemple, vérifiez s’il existe une activité anormale en fonction de l’emplacement commun ou du fournisseur de services Internet, si le compte utilise un agent utilisateur qu’il n’a pas utilisé auparavant, si d’autres comptes invités ont été créés, si d’autres informations d’identification ont été créées après la connexion du compte à partir d’une adresse IP malveillante, entre autres.
-   Alertes
    
    **Vérifiez si l’utilisateur a reçu d’autres alertes précédant l’activité de pulvérisation de mot de passe.** Ces alertes indiquent que le compte d’utilisateur peut être compromis. Il peut s’agir, entre autres, d’une alerte de voyage impossible, d’une activité provenant d’un pays peu fréquent et d’une activité suspecte de suppression de courrier électronique.
-   Incident

    **Vérifiez si l’alerte est associée à d’autres alertes qui indiquent un incident.** Si c’est le cas, vérifiez si l’incident contient d’autres alertes positives vraies.

## <a name="advanced-hunting-queries"></a>Requêtes de repérage avancées

[La chasse avancée](/microsoft-365/security/defender/advanced-hunting-overview) est un outil de chasse aux menaces basé sur une requête qui vous permet d’inspecter les événements de votre réseau et de localiser les indicateurs de menace.

Utilisez cette requête pour rechercher les comptes qui tentent de se connecter avec les scores de risque les plus élevés provenant de l’adresse IP malveillante. Cette requête filtre également toutes les tentatives de connexion réussies avec les scores de risque correspondants.
```kusto
let start_date = now(-7d);
let end_date = now();
let ip_address = ""; // enter here the IP address
AADSignInEventsBeta
| where Timestamp between (start_date .. end_date)
| where IPAddress == ip_address
| where isnotempty(RiskLevelDuringSignIn)
| project Timestamp, IPAddress, AccountObjectId, RiskLevelDuringSignIn, Application, ResourceDisplayName, ErrorCode
| sort by Timestamp asc
| sort by AccountObjectId, RiskLevelDuringSignIn
| partition by AccountObjectId ( top 1 by RiskLevelDuringSignIn ) // remove line to view all successful logins risk scores
```
Utilisez cette requête pour vérifier si l’adresse IP suspecte a utilisé des protocoles hérités pour tenter de se connecter.
```kusto
let start_date = now(-8h);
let end_date = now();
let ip_address = ""; // enter here the IP address
AADSignInEventsBeta
| where Timestamp between (start_date .. end_date)
| where IPAddress == ip_address
| summarize count() by UserAgent
```
Utilisez cette requête pour passer en revue toutes les alertes des sept derniers jours associées à l’adresse IP suspecte.
```kusto
let start_date = now(-7d);
let end_date = now();
let ip_address = ""; // enter here the IP address
let ip_alert_ids = materialize ( 
        AlertEvidence
            | where Timestamp between (start_date .. end_date)
            | where RemoteIP == ip_address
            | project AlertId);
AlertInfo
| where Timestamp between (start_date .. end_date)
| where AlertId in (ip_alert_ids)
```
Utilisez cette requête pour examiner l’activité du compte pour les comptes suspectés compromis.
```kusto
let start_date = now(-8h);
let end_date = now();
let ip_address = ""; // enter here the IP address
let compromise_users = 
    materialize ( AADSignInEventsBeta
                    | where Timestamp between (start_date .. end_date)
                    | where IPAddress == ip_address
                    | where ErrorCode == 0
                    | distinct AccountObjectId);
CloudAppEvents
    | where Timestamp between (start_date .. end_date)
    | where AccountObjectId in (compromise_users)
    | summarize ActivityCount = count() by AccountObjectId, ActivityType
    | extend ActivityPack = pack(ActivityType, ActivityCount)
    | summarize AccountActivities = make_bag(ActivityPack) by AccountObjectId
```
Utilisez cette requête pour examiner toutes les alertes pour les comptes suspectés compromis.
```kusto
let start_date = now(-8h); // change time range
let end_date = now();
let ip_address = ""; // enter here the IP address
let compromise_users = 
    materialize ( AADSignInEventsBeta
                    | where Timestamp between (start_date .. end_date)
                    | where IPAddress == ip_address
                    | where ErrorCode == 0
                    | distinct AccountObjectId);
let ip_alert_ids = materialize ( AlertEvidence
    | where Timestamp between (start_date .. end_date)
    | where AccountObjectId in (compromise_users)
    | project AlertId, AccountObjectId);
AlertInfo
| where Timestamp between (start_date .. end_date)
| where AlertId in (ip_alert_ids)
| join kind=innerunique ip_alert_ids on AlertId
| project Timestamp, AccountObjectId, AlertId, Title, Category, Severity, ServiceSource, DetectionSource, AttackTechniques
| sort by AccountObjectId, Timestamp
```
## <a name="recommended-actions"></a>Actions recommandées

1. [Bloquez l’adresse IP de l’attaquant.](/azure/active-directory/conditional-access/block-legacy-authentication)
2. Réinitialiser les informations d’identification des comptes d’utilisateur. 
3. Révoquez les jetons d’accès des comptes compromis.
4. [Bloquer l’authentification héritée.](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy) 
5. [Exiger l’authentification multifacteur pour les utilisateurs](/microsoft-365/business-premium/m365bp-conditional-access) , si possible, afin [d’améliorer la sécurité du compte](/azure/active-directory/authentication/tutorial-enable-azure-mfa) et de rendre difficile la compromission du compte par une attaque par pulvérisation de mots de passe pour l’attaquant. 
6. Empêchez le compte d’utilisateur compromis de se connecter si nécessaire.
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du classement des alertes](alert-grading-playbooks.md)
- [Examiner des alertes](investigate-alerts.md)