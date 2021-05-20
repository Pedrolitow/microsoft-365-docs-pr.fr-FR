---
title: Liste des incidents API dans Microsoft 365 Defender
description: Découvrez comment énumérer les incidents API dans Microsoft 365 Defender
keywords: liste, incident, incidents, api
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 6f0c92371e7e9b7a3348f90df788ee8c3a46374b
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572152"
---
# <a name="list-incidents-api-in-microsoft-365-defender"></a>Liste des incidents API dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.


## <a name="api-description"></a>Description de l’API

L’API des incidents de liste vous permet de trier les incidents pour créer une réponse éclairée en matière de cybersécurité. Il expose une collection d’incidents qui ont été signalés dans votre réseau, dans la plage de temps que vous avez spécifiée dans votre politique de rétention de l’environnement. Les incidents les plus récents sont affichés en haut de la liste. Chaque incident contient un éventail d’alertes connexes et leurs entités connexes.

L’API prend en charge les **opérateurs OData** suivants :

- `$filter` sur le `lastUpdateTime` , , et les `createdTime` `status` `assignedTo` propriétés
- `$top`, d’une valeur maximale de **100**
- `$skip`

## <a name="limitations"></a>Limites

1. La taille maximale de la page **est de 100 incidents**.
2. Le taux maximum de demandes est **de 50 appels par minute** et de **1500 appels par heure.**

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour en savoir plus, y compris comment choisir les autorisations, [consultez access Microsoft 365 Defender API](api-access.md)

Type d’autorisation | Autorisation | Nom d’affichage d’autorisation
-|-|-
Application | Incident.Read.All | Lire tous les incidents
Application | Incident.ReadWrite.All | Lire et écrire tous les incidents
Déléguée (compte professionnel ou scolaire) | Incident.Read | Lire les incidents
Déléguée (compte professionnel ou scolaire) | Incident.ReadWrite | Lire et écrire les incidents

> [!Note]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
>
> - L’utilisateur doit avoir une autorisation de vue pour les incidents dans le portail.
> - La réponse ne comprendra que les incidents à qui l’utilisateur est exposé.

## <a name="http-request"></a>Requête HTTP

```HTTP
GET /api/incidents
```

## <a name="request-headers"></a>En-têtes de demande

Nom | Type | Description
-|-|-
Autorisation | String | Porteur {jeton}. **Obligatoire**


## <a name="request-body"></a>Corps de la demande

Aucun.

## <a name="response"></a>Réponse

En cas de succès, cette méthode `200 OK` revient, et une liste d’incidents [dans](api-incident.md) l’organisme d’intervention.

## <a name="schema-mapping"></a>Cartographie schema

### <a name="incident-metadata"></a>Métadonnées d’incident

Nom du champ | Description | Exemple de valeur
-|-|-
incidentId | Identificateur unique pour représenter l’incident | 924565
redirectIncidentId | Seulement peuplé dans le cas où un incident est regroupé avec un autre incident, dans le cadre de la logique de traitement des incidents. | 924569
incidentName | Valeur de chaîne disponible pour chaque incident. | Activité de rançongiciel
createdTime (en) | Heure à partir de la création de l’incident. | 2020-09-06T14:46:57.073333ZLa rédaction de 20H33
lastUpdateTime (en) | Heure à la dernière mise à jour de l’incident sur le backend.<br /><br /> Ce champ peut être utilisé lorsque vous définissez le paramètre de demande pour la plage de temps pendant que les incidents sont récupérés. | 2020-09-06T14:46:57.29ZLa rédaction de 20H00
assignedTo | Propriétaire de l’incident, ou *nul si aucun* propriétaire n’est affecté. | secop2@contoso.com
classification | Le détail de l’incident. Les valeurs de propriété sont *: Inconnu,* *FalsePositive,* *TruePositive* | Inconnu
détermination | Précise la détermination de l’incident. Les valeurs de propriété sont : *NotAvailable,* *Apt,* *Malware,* *SecurityPersonnel,* *SecurityTesting,* *UnwantedSoftware,* *Autres* | Non disponible
statut | Catégoriser les incidents *(comme actifs* ou *résolus).* Il peut vous aider à organiser et à gérer votre réponse aux incidents. | Actif
Sévérité  | Indique l’impact possible sur les actifs. Plus la gravité est élevée, plus l’impact est important. En règle générale, les éléments de gravité plus élevée nécessitent l’attention la plus immédiate.<br /><br />Une des valeurs suivantes: *Informational*, *Low*, *Medium, and *High*. | Moyenne
étiquettes | Tableau des balises personnalisées associées à un incident, par exemple pour signaler un groupe d’incidents ayant une caractéristique commune. | \[\]
commentaires | Tableau des commentaires créés par les secops lors de la gestion de l’incident, par exemple des informations supplémentaires sur la sélection de classification. | \[\]
alerts | Tableau contenant toutes les alertes liées à l’incident, ainsi que d’autres informations, telles que la gravité, les entités qui ont été impliquées dans l’alerte, et la source des alertes. | \[\] (voir les détails sur les champs d’alerte ci-dessous)

### <a name="alerts-metadata"></a>Métadonnées d’alertes

Nom du champ | Description | Exemple de valeur
-|-|-
alertId (en) | Identificateur unique pour représenter l’alerte | caD70CFEE2-1F54-32DB-9988-3A868A1EBFAC
incidentId | Identificateur unique pour représenter l’incident à qui cette alerte est associée | 924565
serviceSource | Le service d’alerte provient, comme Microsoft Defender pour Endpoint, Microsoft Cloud App Security, Microsoft Defender for Identity ou Microsoft Defender pour Office 365. | MicrosoftCloudAppSecurity
creationTime (en) | Heure à partir de la création de l’alerte. | 2020-09-06T14:46:55.7182276ZLa rédaction de 20H00
lastUpdatedTime (en) | Heure à partir de la dernière mise à jour de l’alerte au backend. | 2020-09-06T14:46:57.243333ZLa rédaction de 20H46
resolvedTime (en) | Heure à ce que l’alerte soit résolue. | 2020-09-10T05:22:59Z
firstActivité | Heure à partir de l’alerte a signalé pour la première fois que l’activité a été mise à jour au backend.| 2020-09-04T05:22:59Z
title | Brève valeur de chaîne d’identification disponible pour chaque alerte. | Activité de rançongiciel
description | Valeur de chaîne décrivant chaque alerte. | L’utilisateur Test User2 (testUser2@contoso.com) manipulé 99 fichiers avec des extensions multiples se terminant par l’extension *rare herunterladen*. Il s’agit d’un nombre inhabituel de manipulations de fichiers et est indicative d’une attaque ransomware potentiel.
category | Vue visuelle et numérique de la mesure dans quelle mesure l’attaque a progressé le long de la chaîne de mise à mort. Aligné sur le [cadre de&CK ™ MITRE ATT](https://attack.mitre.org/). | Impact
statut | Catégoriser les alertes *(comme nouvelles,* *actives* ou *résolues).* Il peut vous aider à organiser et gérer votre réponse aux alertes. | Nouveau
Sévérité  | Indique l’impact possible sur les actifs. Plus la gravité est élevée, plus l’impact est important. En règle générale, les éléments de gravité plus élevée nécessitent l’attention la plus immédiate.<br>Une des valeurs suivantes: *Informational*, *Low*, *Medium, and *High*. | Moyenne
investigationId | L’iD d’enquête automatisé déclenché par cette alerte. | 1234
enquêteState | Informations sur l’état actuel de l’enquête. Une des valeurs suivantes: *Unknown*, *Terminated*, *SuccessfullyRemediated*, *Benign*, *Failed*, *PartiallyRemediated*, *Running*, *PendingApproval*, *PendingResource*, *PartiallyInvestigated*, *TerminatedByUser*, *TerminatedBySystem*, *File d’attente*, *InnerFailure*, *PreexistingAlert*, *UnsupportedOs*, *UnsupportedAlertType*, *SuppressedAlert*. | Typealert non pris en charge
classification | Le détail de l’incident. Les valeurs de propriété sont *: Inconnu,* *FalsePositive,* *TruePositive,* ou *nul* | Inconnu
détermination | Précise la détermination de l’incident. Les valeurs de propriété sont : *NotAvailable,* *Apt,* *Malware,* *SecurityPersonnel,* *SecurityTesting,* *UnwantedSoftware,* *Autre*  *ou nul* | apte
assignedTo | Propriétaire de l’incident, ou *nul si aucun* propriétaire n’est affecté. | secop2@contoso.com
actorName (en anglais) | Le groupe d’activité, le cas échéant, l’associé à cette alerte. | bore
threatFamilyName | Famille de menaces associée à cette alerte. | null
mitreTechniques | Les techniques d’attaque, telles qu’alignées [avec le cadre&MITRE ATT ™ CK.](https://attack.mitre.org/) | \[\]
Dispositifs | Tous les appareils où des alertes liées à l’incident ont été envoyées. | \[\] (voir les détails sur les champs d’entités ci-dessous)

### <a name="device-format"></a>Format de l’appareil

Nom du champ | Description | Exemple de valeur
-|-|-
DeviceId DeviceId | L’iD de l’appareil tel que désigné dans Microsoft Defender pour Endpoint. | 24c222b0b60fe148eeece49ac83910cc6a7ef491
aadDeviceId |  L’id de l’appareil tel [qu’il est Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis). Uniquement disponible pour les périphériques connectés au domaine. | null
deviceDnsName | Le nom de domaine entièrement qualifié pour l’appareil. | user5cx.middleeast.corp.contoso.com
osPlatform (osPlatform) | La plate-forme OS de l’appareil est en cours d’exécution.| WindowsServer2016
osBuild (en) | La version de build pour l’OS l’appareil est en cours d’exécution. | 14393
rbacGroupName | Le [groupe de contrôle d’accès](/azure/role-based-access-control/overview) basé sur les fonctions (RBAC) associé à l’appareil. | WDATP-Ring0
firstSeen FirstSeen FirstSeen FirstS | Heure à quand l’appareil a été vu pour la première fois. | 2020-02-06T14:16:01.9330135ZLa rédaction de 20H16
santéStatus | L’état de santé de l’appareil. | Actif
riskScore (riskScore) | Le score de risque pour l’appareil. | Élevé
Entités | Toutes les entités qui ont été identifiées comme faisant partie d’une alerte donnée ou qui y sont liées. | \[\] (voir les détails sur les champs d’entités ci-dessous)

### <a name="entity-format"></a>Format d’entité

Nom du champ | Description | Exemple de valeur
-|-|-
entityType (entityType) | Entités qui ont été identifiées comme faisant partie d’une alerte donnée ou liées à celle-là.<br>Les valeurs de propriétés sont: *Utilisateur*, *Ip*, *Url*, *Fichier*, *Processus*, *Boîte aux lettres*, *MailMessage*, *MailCluster*, *Registre* | Utilisateur
sha1 (sha1) | Disponible si entityType est *Fichier*.<br>Le hachage de fichiers pour les alertes associées à un fichier ou un processus. | 5de839186691aa96ee2ca6d74f0a38fb8d1bd6dd
sha256 (sha256) | Disponible si entityType est *Fichier*.<br>Le hachage de fichiers pour les alertes associées à un fichier ou un processus. | 28cb017dfc99073aa1b47c1b30f413e3ce774c4991eb4158de50f9dbb36d8043
fileName | Disponible si entityType est *Fichier*.<br>Le nom du fichier pour les alertes associées à un fichier ou un processus | Detector.UnitTests.dll
filePath (en) | Disponible si entityType est *Fichier*.<br>Le chemin de fichier pour les alertes associées à un fichier ou un processus | C: \\ \agent_work_temp\Deploy\SYSTEM\2020-09-06 12_14_54\Out
processId | Disponible si entityType est *Process*. | 24348
processCommandLine | Disponible si entityType est *Process*. | « Votre fichier est prêt à télécharger \_1911150169.exe »
processCreationTime (en) | Disponible si entityType est *Process*. | 2020-07-18T03:25:38.5269993Z
parentProcessId | Disponible si entityType est *Process*. | 16840
parentProcessCreationTime | Disponible si entityType est *Process*. | 2020-07-18T02:12:32.8616797Z
ipAddress | Disponible si entityType est *Ip*. <br>Adresse IP pour les alertes associées à des événements réseau, tels que *la communication vers une destination réseau malveillante*. | 62.216.203.204
url | Disponible si entityType est *Url*. <br>Url pour les alertes associées aux événements réseau, tels que, *Communication à une destination réseau malveillante*. | down.esales360.cn
accountName | Disponible si entityType est *utilisateur*. | testUser2
domainName | Disponible si entityType est *utilisateur*. | europe.corp.contoso
userSid (en) | Disponible si entityType est *utilisateur*. | S-1-5-21-1721254763-462695806-1538882281-4156657
aadUserId | Disponible si entityType est *utilisateur*. | fc8f7484-f813-4db2-afab-bc1507913fb6 fc8f7484-f813-4db2-afab-bc1507913fb6 fc8f7444
userPrincipalName | Disponible si entityType est *User* / *MailBox* / *MailMessage*. | testUser2@contoso.com
boîte aux lettresDisplayName | Disponible si entityType est *MailBox*. | test Utilisateur2
boîte aux lettresAddress | Disponible si entityType est *User* / *MailBox* / *MailMessage*. | testUser2@contoso.com
clusterPar | Disponible si entityType est  *MailCluster*. | Sujet; P2SenderDomain; Type de contenu
expéditeur | Disponible si entityType est *User* / *MailBox* / *MailMessage*. | user.abc@mail.contoso.co.in
destinataire | Disponible si entityType est *MailMessage*. | testUser2@contoso.com
subject | Disponible si entityType est *MailMessage*. | \[\]Attention extérieure
deliveryAction (en) | Disponible si entityType est *MailMessage*. | livré
securityGroupId (en) | Disponible si entityType est  *SecurityGroup*. | 301c47c8-e15f-4059-ab09-e2ba9ffd372b
securityGroupName (en anglais) | Disponible si entityType est  *SecurityGroup*. | Opérateurs de configuration réseau
registryHive | Disponible si entityType est  *Registry*. | MACHINE LOCALE HKEY \_ \_ |
registryKey (registryKey) | Disponible si entityType est  *Registry*. | LOGICIEL\Microsoft\Windows NT\CurrentVersion\Winlogon
registryValueType | Disponible si entityType est  *Registry*. | String
registryValue (en) | Disponible si entityType est  *Registry*. | 31-00-00-00
deviceId | L’ID, le cas échéant, de l’appareil lié à l’entité. | 986e5df8b73dacd43c8917d17e523e76b13c75cd

## <a name="example"></a>Exemple

**Demande**

```HTTP
GET https://api.security.microsoft.com/api/incidents
```

**Réponse**

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Incidents",
    "value": [
            {
            "incidentId": 924565,
            "redirectIncidentId": null,
            "incidentName": "Ransomware activity",
            "createdTime": "2020-09-06T14:46:57.0733333Z",
            "lastUpdateTime": "2020-09-06T14:46:57.29Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Medium",
            "tags": [],
            "comments": [
                {
                    "comment": "test comment for docs",
                    "createdBy": "secop123@contoso.com",
                    "createdTime": "2021-01-26T01:00:37.8404534Z"
                }
            ],
            "alerts": [
                {
                    "alertId": "caD70CFEE2-1F54-32DB-9988-3A868A1EBFAC",
                    "incidentId": 924565,
                    "serviceSource": "MicrosoftCloudAppSecurity",
                    "creationTime": "2020-09-06T14:46:55.7182276Z",
                    "lastUpdatedTime": "2020-09-06T14:46:57.2433333Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-04T05:22:59Z",
                    "lastActivity": "2020-09-04T05:22:59Z",
                    "title": "Ransomware activity",
                    "description": "The user Test User2 (testUser2@contoso.com) manipulated 99 files with multiple extensions ending with the uncommon extension herunterladen. This is an unusual number of file manipulations and is indicative of a potential ransomware attack.",
                    "category": "Impact",
                    "status": "New",
                    "severity": "Medium",
                    "investigationId": null,
                    "investigationState": "UnsupportedAlertType",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "MCAS",
                    "assignedTo": null,
                    "actorName": null,
                    "threatFamilyName": null,
                    "mitreTechniques": [],
                    "devices": [],
                    "entities": [
                        {
                            "entityType": "User",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": "testUser2",
                            "domainName": "europe.corp.contoso",
                            "userSid": "S-1-5-21-1721254763-462695806-1538882281-4156657",
                            "aadUserId": "fc8f7484-f813-4db2-afab-bc1507913fb6",
                            "userPrincipalName": "testUser2@contoso.com",
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "Ip",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": "62.216.203.204",
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        }
                    ]
                }
            ]
        },
        {
            "incidentId": 924521,
            "redirectIncidentId": null,
            "incidentName": "'Mimikatz' hacktool was detected on one endpoint",
            "createdTime": "2020-09-06T12:18:03.6266667Z",
            "lastUpdateTime": "2020-09-06T12:18:03.81Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Low",
            "tags": [],
            "comments": [],
            "alerts": [
                {
                    "alertId": "da637349914833441527_393341063",
                    "incidentId": 924521,
                    "serviceSource": "MicrosoftDefenderATP",
                    "creationTime": "2020-09-06T12:18:03.3285366Z",
                    "lastUpdatedTime": "2020-09-06T12:18:04.2566667Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-06T12:15:07.7272048Z",
                    "lastActivity": "2020-09-06T12:15:07.7272048Z",
                    "title": "'Mimikatz' hacktool was detected",
                    "description": "Readily available tools, such as hacking programs, can be used by unauthorized individuals to spy on users. When used by attackers, these tools are often installed without authorization and used to compromise targeted machines.\n\nThese tools are often used to collect personal information from browser records, record key presses, access email and instant messages, record voice and video conversations, and take screenshots.\n\nThis detection might indicate that Windows Defender Antivirus has stopped the tool from being installed and used effectively. However, it is prudent to check the machine for the files and processes associated with the detected tool.",
                    "category": "Malware",
                    "status": "New",
                    "severity": "Low",
                    "investigationId": null,
                    "investigationState": "UnsupportedOs",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "WindowsDefenderAv",
                    "assignedTo": null,
                    "actorName": null,
                    "threatFamilyName": "Mimikatz",
                    "mitreTechniques": [],
                    "devices": [
                        {
                            "mdatpDeviceId": "24c222b0b60fe148eeece49ac83910cc6a7ef491",
                            "aadDeviceId": null,
                            "deviceDnsName": "user5cx.middleeast.corp.contoso.com",
                            "osPlatform": "WindowsServer2016",
                            "version": "1607",
                            "osProcessor": "x64",
                            "osBuild": 14393,
                            "healthStatus": "Active",
                            "riskScore": "High",
                            "rbacGroupName": "WDATP-Ring0",
                            "rbacGroupId": 9,
                            "firstSeen": "2020-02-06T14:16:01.9330135Z"
                        }
                    ],
                    "entities": [
                        {
                            "entityType": "File",
                            "sha1": "5de839186691aa96ee2ca6d74f0a38fb8d1bd6dd",
                            "sha256": null,
                            "fileName": "Detector.UnitTests.dll",
                            "filePath": "C:\\Agent\\_work\\_temp\\Deploy_SYSTEM 2020-09-06 12_14_54\\Out",
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": "24c222b0b60fe148eeece49ac83910cc6a7ef491"
                        }
                    ]
                }
            ]
        },
        {
            "incidentId": 924518,
            "redirectIncidentId": null,
            "incidentName": "Email reported by user as malware or phish",
            "createdTime": "2020-09-06T12:07:55.1366667Z",
            "lastUpdateTime": "2020-09-06T12:07:55.32Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Informational",
            "tags": [],
            "comments": [],
            "alerts": [
                {
                    "alertId": "faf8edc936-85f8-a603-b800-08d8525cf099",
                    "incidentId": 924518,
                    "serviceSource": "OfficeATP",
                    "creationTime": "2020-09-06T12:07:54.3716642Z",
                    "lastUpdatedTime": "2020-09-06T12:37:40.88Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-06T12:04:00Z",
                    "lastActivity": "2020-09-06T12:04:00Z",
                    "title": "Email reported by user as malware or phish",
                    "description": "This alert is triggered when any email message is reported as malware or phish by users -V1.0.0.2",
                    "category": "InitialAccess",
                    "status": "InProgress",
                    "severity": "Informational",
                    "investigationId": null,
                    "investigationState": "Queued",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "OfficeATP",
                    "assignedTo": "Automation",
                    "actorName": null,
                    "threatFamilyName": null,
                    "mitreTechniques": [],
                    "devices": [],
                    "entities": [
                        {
                            "entityType": "MailBox",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "testUser3@contoso.com",
                            "mailboxDisplayName": "test User3",
                            "mailboxAddress": "testUser3@contoso.com",
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailBox",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "testUser4@contoso.com",
                            "mailboxDisplayName": "test User4",
                            "mailboxAddress": "test.User4@contoso.com",
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailMessage",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "test.User4@contoso.com",
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": "user.abc@mail.contoso.co.in",
                            "recipient": "test.User4@contoso.com",
                            "subject": "[EXTERNAL] Attention",
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "Subject;P2SenderDomain;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "Subject;SenderIp;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "BodyFingerprintBin1;P2SenderDomain;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "BodyFingerprintBin1;SenderIp;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "Ip",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": "49.50.81.121",
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        }
                    ]
                }
            ]
        },
        ...
    ]
}
```

## <a name="related-articles"></a>Articles connexes

- [Accédez aux API Microsoft 365 Defender](api-access.md)
- [En savoir plus sur les limites de l’API et les licences](api-terms.md)
- [Comprendre les codes d’erreur](api-error-codes.md)
- [Vue d’ensemble des incidents](incidents-overview.md)
- [API d’incident](api-incident.md)
- [Mise à jour de l’API incident](api-update-incidents.md)
