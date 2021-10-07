---
title: Conformité de la communication avec les solutions SIEM
description: Découvrez l’intégration de la conformité des communications avec les solutions SIEM.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 0e49935ff1d280adf4c1567a2064496a475c6033
ms.sourcegitcommit: afee35210f8d68a7f20676ff2a829464b0b0adb2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2021
ms.locfileid: "60216945"
---
# <a name="communication-compliance-with-siem-solutions"></a>Conformité de la communication avec les solutions SIEM

[La conformité des communications](communication-compliance.md) est une solution à risque interne dans Microsoft 365 qui vous permet de minimiser les risques de communication en vous aidant à détecter, capturer et agir sur des messages inappropriés dans votre organisation. Les solutions de gestion des événements et des informations de sécurité (SIEM), telles [qu’Azure Sentinel](https://azure.microsoft.com/services/azure-sentinel) ou [Splunk,](https://www.splunk.com/) sont couramment utilisées pour agréger et suivre les menaces au sein d’une organisation.

Les organisations ont souvent besoin d’intégrer des alertes de conformité des communications et ces solutions SIEM. Avec cette intégration, les organisations peuvent afficher les alertes de conformité des communications dans leur solution SIEM, puis corriger les alertes dans le flux de travail de conformité des communications et l’expérience utilisateur. Par exemple, un employé envoie un message choquant à un autre employé et ce message est détecté par un contrôle de stratégie de conformité des communications pour un langage choquant. Ces événements sont suivis dans Microsoft 365 audit (également appelé « journal d’audit unifié ») par la solution de conformité des communications et importés dans la solution SIEM. Une alerte est ensuite déclenchée dans la solution SIEM de l’organisation à partir d’événements surveillés dans Microsoft 365 Audit associés aux alertes de conformité des communications. Les enquêteurs sont avertis de l’alerte dans les solutions SIEM, puis examinent et remédient à l’alerte dans la solution de conformité des communications.

## <a name="communication-compliance-alerts-in-microsoft-365-audit"></a>Alertes de conformité des communications dans Microsoft 365 audit

Toutes les correspondances de stratégie de conformité des communications sont capturées dans Microsoft 365 audit. Les exemples suivants montrent les détails disponibles pour les activités de correspondance de stratégie de conformité des communications sélectionnées :

**Exemple d’entrée de journal d’audit pour une correspondance de modèle de stratégie de langage choquant :**

```xml
RunspaceId: 5c7bc9b0-7672-4091-a112-0635bd5f7732
RecordType: ComplianceSupervisionExchange
CreationDate: 7/7/2021 5:30:11 AM
UserIds: user1@contoso.onmicrosoft.com
Operations: SupervisionRuleMatch
AuditData: {"CreationTime":"2021-07-07T05:30:11","Id":"44e98a7e-57fd-4f89-79b8-08d941084a35","Operation":"SupervisionRuleMatch","OrganizationId":"338397e6\-697e-4dbe-a66b-2ea3497ef15c","RecordType":68,"ResultStatus":"{\\"ItemClass\\":\\"IPM.Note\\",\\"CcsiResults\\":\\"\\"}","UserKey":"SupervisionStoreDeliveryAgent","UserType":0,"Version":1,"Workload":"Exchange","ObjectId":"\<HE1P190MB04600526C0524C75E5750C5AC61A9@HE1P190MB0460.EURP190.PROD.OUTLOOK.COM\>","UserId":"user1@contoso.onmicrosoft.com","IsPolicyHit":true,"SRPolicyMatchDetails":{"SRPolicyId":"53be0bf4-75ee-4315-b65d-17d63bdd53ae","SRPolicyName":"Adult images","SRRuleMatchDetails":\[\]}}
ResultIndex: 24
ResultCount: 48
Identity: 44e98a7e-57fd-4f89-79b8-08d941084a35
IsValid: True
ObjectState: Unchanged
```

**Exemple d’une entrée Microsoft 365 journal d’audit pour une stratégie avec correspondance de mot clé personnalisée (type d’informations sensibles personnalisé) :**

```xml
RunspaceId: 5c7bc9b0-7672-4091-a112-0635bd5f7732
RecordType: ComplianceSupervisionExchange
CreationDate: 7/6/2021 9:50:12 PM
UserIds: user2@contoso.onmicrosoft.com
Operations: SupervisionRuleMatch
AuditData: {"CreationTime":"2021-07-06T21:50:12","Id":"5c61aae5-26fc-4c8e-0791-08d940c8086f","Operation":"SupervisionRuleMatch","OrganizationId":"338397e6\-697e-4dbe-a66b-2ea3497ef15c","RecordType":68,"ResultStatus":"{\\"ItemClass\\":\\"IPM.Note\\",\\"CcsiResults\\":\\"public\\"}","UserKey":"SupervisionStoreDeliveryAgent","UserType":0,"Version":1,"Workload":"Exchange","ObjectId":"\<20210706174831.24375086.807067@sailthru.com\>","UserId":"user2@contoso.onmicrosoft.com","IsPolicyHit":true,"SRPolicyMatchDetails":{"SRPolicyId":"a97cf128-c0fc-42a1-88e3-fd3b88af9941","SRPolicyName":"Insiders","SRRuleMatchDetails":\[{"SRCategoryName":"New insiders lexicon"}\]}}
ResultIndex: 46
ResultCount: 48
Identity: 5c61aae5-26fc-4c8e-0791-08d940c8086f
IsValid: True
ObjectState: Unchanged
```

> [!NOTE]
> Actuellement, il peut y avoir un délai de 24 heures entre l’enregistrement d’une correspondance de stratégie dans Microsoft 365 Audit et l’heure à laquelle vous pouvez examiner les correspondances de stratégie dans la conformité des communications.

## <a name="configure-communication-compliance-and-azure-sentinel-integration"></a>Configurer la conformité des communications et l’intégration Azure Sentinel

Lorsque vous utilisez Azure Sentinel pour agréger les correspondances de stratégie de conformité des communications, Sentinel utilise Microsoft 365 Audit comme source de données. Pour intégrer des alertes de conformité des communications à Sentinel, complétez les étapes suivantes :

1. [Intégration à Azure Sentinel](/azure/sentinel/quickstart-onboard). Dans le cadre du processus d’intégration, vous allez configurer vos sources de données.
2. Configurez le connecteur de données Azure Sentinel [Microsoft Office 365 et](/azure/sentinel/data-connectors-reference#microsoft-office-365) sous la configuration du *connecteur, sélectionnez Exchange*.
3. Configurez la requête de recherche pour récupérer les alertes de conformité des communications. Par exemple :

    *| OfficeActivity | où OfficeWorkload == « Exchange » et Operation == « SupervisionRuleMatch » | trier par TimeGenerated*

    Pour filtrer un utilisateur spécifique, vous devez utiliser le format de requête suivant :

    *| OfficeActivity | où OfficeWorkload == « Exchange » et Operation == « SupervisionRuleMatch » et UserId == « User1@Contoso.com » | trier par TimeGenerated*

Pour plus d’informations sur les journaux Microsoft 365 audit pour les Office 365 collectés par Azure Sentinel, consultez la référence des journaux [Azure Monitor.](/azure/azure-monitor/reference/tables/OfficeActivity)

## <a name="configure-communication-compliance-and-splunk-integration"></a>Configurer la conformité des communications et l’intégration de Splunk

Pour intégrer des alertes de conformité des communications à Splunk, complétez les étapes suivantes :

1. Installer le [module Microsoft Office 365](https://docs.splunk.com/Documentation/AddOns/released/MSO365/ConfigureinputsmanagementAPI)
2. Configurer une application d’intégration dans Azure AD pour le module Microsoft Office 365
3. Configurez les requêtes de recherche dans votre solution Splunk. Utilisez l’exemple de recherche suivant pour identifier toutes les alertes de conformité des communications :

    *index= \* sourcetype="o365:management:activity » Workload=Exchange Operation=SupervisionRuleMatch*

Pour filtrer les résultats d’une stratégie de conformité des communications spécifique, vous pouvez utiliser le paramètre *SRPolicyMatchDetails.SRPolicyName.*

Par exemple, l’exemple de recherche suivant retournerait des alertes pour les correspondances à une stratégie de conformité des communications nommée *Langage choquant*:

  *index= \* sourcetype='o365:management:activity' Workload=Exchange Operation=SupervisionRuleMatch SRPolicyMatchDetails.SRPolicyName=\<Offensive language\>*

Le tableau suivant présente des exemples de résultats de recherche pour différents types de stratégie :

| Les types de stratégies | Exemple de résultats de recherche |
| :------------------ | :--------------------------------------- |
| Stratégie de détection d’une liste de mots clés de type d’informations sensibles personnalisée | { <br> CreationTime : 2021-09-17T16:29:57 <br> ID : 4b9ce23d-ee60-4f66-f38d-08d979f8631f <br> IsPolicyHit: true <br> ObjectId : <CY1PR05MB27158B96AF7F3AFE62E1F762CFDD9@CY1PR05MB2715.namprd05.prod.outlook.com> <br> Opération : SupervisionRuleMatch <br> OrganizationId: d6a06676-95e8-4632-b949-44bc00f0793f <br> RecordType : 68 <br> ResultStatus: {"ItemClass »:"IPM. Note »,"CcsiResults »:"leak"} <br> SRPolicyMatchDetails : { [+] } <br> UserId : user1@contoso. OnMicrosoft.com <br> UserKey : SupervisionStoreDeliveryAgent <br> UserType : 0 <br> Version : 1 <br> Charge de travail : Exchange <br> } |
| Stratégie de détection d’un langage inapproprié | { <br> CreationTime : 2021-09-17T23:44:35 <br> ID : e0ef6f54-9a52-4e4c-9584-08d97a351ad0 <br> IsPolicyHit: true <br> ObjectId : <BN6PR05MB3571AD9FBB85C4E12C1F66B4CCDD9@BN6PR05MB3571.namprd05.prod.outlook.com> <br> Opération : SupervisionRuleMatch <br> OrganizationId: d6a06676-95e8-4632-b949-44bc00f0793f <br> RecordType : 68 <br> ResultStatus: {"ItemClass »:"IPM.Yammer. Message »,"CcsiResults »:"}. <br> SRPolicyMatchDetails : { [+] } <br> UserId : user1@contoso.com <br> UserKey : SupervisionStoreDeliveryAgent <br> UserType : 0 <br> Version : 1 <br> }  |

## <a name="configure-communication-compliance-with-other-siem-solutions"></a>Configurer la conformité des communications avec d’autres solutions SIEM

Pour récupérer les correspondances de stratégie de conformité des communications à partir Microsoft 365 audit, vous pouvez utiliser PowerShell ou [l’API Office 365 gestion des communications.](/office/office-365-management-api/office-365-management-activity-api-reference)

Lorsque vous utilisez PowerShell, vous pouvez utiliser l’un de ces paramètres avec la cmdlet **Search-UnifiedAuditLog** pour filtrer les événements du journal d’audit pour les activités de conformité des communications.

| Paramètre du journal d’audit | Valeur du paramètre de conformité des communications |
| :------------------ | :--------------------------------------- |
| Opérations          | SupervisionRuleMatch                     |
| RecordType          | ComplianceSupervisionExchange            |

Par exemple, voici un exemple de recherche à l’aide du paramètre **Operations** et de la valeur *SupervisionRuleMatch* :

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionRuleMatch | ft CreationDate,UserIds,AuditData
```
Voici un exemple de recherche à l’aide du **paramètre RecordsType** et de la *valeur ComplianceSupervisionExchange* :

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType ComplianceSuperVisionExchange | ft CreationDate,UserIds,AuditData
```
## <a name="resources"></a>Ressources

- [Audit de la conformité des communications](communication-compliance-feature-reference.md#audit)
- [Audit avancé de Microsoft 365](advanced-audit.md)
- [Référence de l’API Activité de gestion Office 365](/office/office-365-management-api/office-365-management-activity-api-reference)
