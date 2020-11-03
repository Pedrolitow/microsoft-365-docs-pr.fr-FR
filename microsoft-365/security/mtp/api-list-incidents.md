---
title: API de liste des incidents dans Microsoft 365 Defender
description: Découvrez comment répertorier l’API des incidents dans Microsoft 365 Defender
keywords: liste, incident, incidents, API
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 9da6fdf04fd22767f3984229b7862f02b8293067
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48844995"
---
# <a name="list-incidents-api-in-microsoft-365-defender"></a>API de liste des incidents dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.


## <a name="api-description"></a>Description de l’API

L’API incident vous permet d’effectuer un tri dans les incidents afin de hiérarchiser et de créer une réponse Cybersecurity informée. Il expose une collection d’incidents marqués à partir des appareils, des comptes de messagerie et des utilisateurs de votre réseau, dans la plage de temps que vous avez spécifiée dans la stratégie de rétention de votre environnement. Les incidents les plus récents sont affichés en haut de la liste. Chaque incident contient un tableau des alertes associées et de leurs entités associées.

<br>L’API prend en charge les opérateurs **OData** suivants :
<br>```$filter``` activé : ```lastUpdateTime``` , ```createdTime``` ```status``` et ```assignedTo``` Propriétés.
<br>```$top``` avec une valeur maximale de **100**
<br>```$skip```

## <a name="limitations"></a>Limites

1. La taille de page maximale est de **100 incidents**.
2. Le taux maximal de demandes est de **50 appels par minute** et **1500 appels par heure**.

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, consultez la rubrique [Access Microsoft 365 Defender API](api-access.md)

Type d’autorisation |   Autorisation  |   Nom d’affichage des autorisations
:---|:---|:---
Application |   Incident. Read. All | « Lire tous les incidents »
Application |   Incident. ReadWrite. All | « Lire et écrire tous les incidents »
Déléguée (compte professionnel ou scolaire) | Incident. Read | « Incidents de lecture »
Déléguée (compte professionnel ou scolaire) | Incident. ReadWrite | « Incidents en lecture et en écriture »

> [!Note]
> Lors de l’obtention d’un jeton à l’aide des informations d’identification de l’utilisateur :
> - L’utilisateur doit disposer de l’autorisation Afficher pour les incidents dans le portail.
> - La réponse inclut uniquement les incidents auxquels l’utilisateur est exposé.

## <a name="http-request"></a>Requête HTTP

```
GET /api/incidents
```

## <a name="request-headers"></a>En-têtes de demande

Nom | Type | Description
:---|:---|:---
Autorisation | String | Porteur {token}. **Obligatoire**.


## <a name="request-body"></a>Corps de la demande
Aucun.

## <a name="response"></a>Réponse
Si elle réussit, cette méthode renvoie 200 OK et une liste d' [incidents](api-incident.md) dans le corps de la réponse.

## <a name="schema-mapping"></a>Mappage de schéma

| Nom du champ                                | Description                                                                                                                                                                                                                                                                                                                                                                                | Exemple de valeur                                                                                                                                                                                                                                     |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Métadonnées d’incident**                         |                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                                                   |
| incidentId                                | Identificateur unique qui représente l’incident.                                                                                                                                                                                                                                                                                                                                                | 924565                                                                                                                                                                                                                                            |
| redirectIncidentId                        | Renseigné uniquement si un incident est regroupé avec un autre incident, dans le cadre de la logique de traitement de l’incident.                                                                                                                                                                                                                                                           | 924569                                                                                                                                                                                                                                            |
| incidentName                              | Valeur de chaîne disponible pour chaque incident.                                                                                                                                                                                                                                                                                                                                                  | Activité ransomware                                                                                                                                                                                                                               |
| createdTime                               | Heure de la première création de l’incident.                                                                                                                                                                                                                                                                                                                                                      | 2020-09-06T14:46:57.0733333 Z                                                                                                                                                                                                                      |
| lastUpdateTime                            | Heure de la dernière mise à jour de l’incident sur le serveur principal.<br> Ce champ peut être utilisé lors de la définition du paramètre Request pour la plage de temps pendant laquelle les incidents sont récupérés.                                                                                                                                                                                                                      | 2020-09-06T14:46:57.29 Z                                                                                                                                                                                                                           |
| assignedTo                                | Propriétaire de l’incident ou *valeur null* si aucun propriétaire n’est affecté.                                                                                                                                                                                                                                                                                                                         | secop2@contoso.com                                                                                                                                                                                                |
| classification                            | Spécification de l’incident. Les valeurs de propriété sont les suivantes : *Unknown* , *FalsePositive* , *TruePositive*                                                                                                                                                                                                                                                                           | Inconnu                                                                                                                                                                                                                                           |
| indications                             | Indique la détermination de l’incident. Les valeurs de propriété sont les suivantes : *NotAvailable* , *apt* , *Malware* , *SecurityPersonnel* , *SecurityTesting* , *UnwantedSoftware* , *other*                                                                                                                                                                                                                | NotAvailable                                                                                                                                                                                                                                      |
| statut                                    | Catégoriser les incidents ( *actif* ou *résolu* ). Cela vous permet d’organiser et de gérer votre réponse aux incidents.                                                                                                                                                                                                                                                                  | Actif                                                                                                                                                                                                                                            |
| Sévérité                                   | Indique l’impact possible sur les ressources. Plus la gravité est élevée, plus l’impact est important. En règle générale, les éléments de gravité plus élevés nécessitent une attention immédiate.<br>L’une des valeurs suivantes : *informatif* , *Low* , * medium et *High*.                                                                                                                                | Moyen                                                                                                                                                                                                                                            |
| étiquettes                                      | Tableau de balises personnalisées associées à un incident, par exemple pour marquer un groupe d’incidents avec une caractéristique commune.                                                                                                                                                                                                                                                                  | \[\]                                                                                                                                                                                                                                              |
| alerts                                    | Tableau de toutes les alertes liées à l’incident et d’autres informations, telles que la gravité, les entités impliquées dans l’alerte, la source des alertes.                                                                                                                                                                                                                     | \[\] (voir détails dans les champs d’alerte ci-dessous)                                                                                                                                                                                                          |
| **Métadonnées d’alertes**                           |                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                                                   |
| IDAlerte                                   | Identificateur unique qui représente l’alerte.                                                                                                                                                                                                                                                                                                                                                   | caD70CFEE2-1F54-32DB-9988-3A868A1EBFAC                                                                                                                                                                                                            |
| incidentId                                | Identificateur unique représentant l’incident auquel cette alerte est associée.                                                                                                                                                                                                                                                                                                                  | 924565                                                                                                                                                                                                                                            |
| serviceSource                             | Service d’origine de l’alerte, comme Microsoft Defender pour le point de terminaison, sécurité de l’application Cloud Microsoft, Microsoft Defender pour l’identité ou Microsoft Defender pour Office 365.                                                                                                                                                                                                                                                                     | MicrosoftCloudAppSecurity                                                                                                                                                                                                                         |
| creationTime                              | Heure à laquelle l’alerte a été créée pour la première fois.                                                                                                                                                                                                                                                                                                                                                         | 2020-09-06T14:46:55.7182276 Z                                                                                                                                                                                                                      |
| lastUpdatedTime                           | Heure de la dernière mise à jour de l’alerte sur le serveur principal.                                                                                                                                                                                                                                                                                                                                           | 2020-09-06T14:46:57.2433333 Z                                                                                                                                                                                                                      |
| resolvedTime                              | Heure de la résolution de l’alerte.                                                                                                                                                                                                                                                                                                                                                              | 2020-09-10T05:22:59Z                                                                                                                                                                                                                              |
| firstActivity                             | Heure à laquelle l’alerte a signalé pour la première fois que l’activité a été mise à jour sur le serveur principal.                                                                                                                                                                                                                                                                                                                             | 2020-09-04T05:22:59Z                                                                                                                                                                                                                              |
| title                                     | Courte valeur de chaîne d’identification disponible pour chaque alerte.                                                                                                                                                                                                                                                                                                                                                     | Activité ransomware                                                                                                                                                                                                                               |
| description                               | Valeur de chaîne décrivant chaque alerte.                                                                                                                                                                                                                                                                                                                                                        | Le test de l’utilisateur utilisateur2 (testUser2@contoso.com) a manipulé 99 fichiers avec plusieurs extensions se terminant par l’extension *herunterladen*. Il s’agit d’un nombre inhabituel de manipulations de fichiers et indique une attaque par ransomware potentielle. |
| category                                  | Vue visuelle et numérique de la progression de l’attaque le long de la chaîne de terminaison. Aligné sur l' [infrastructure Mitre ATT&CK™](https://attack.mitre.org/).                                                                                                                                                                                                                           | Impact                                                                                                                                                                                                                                            |
| statut                                    | Catégoriser les alertes (en tant que *nouvelles* , *actives* ou *résolues* ). Cela vous permet d’organiser et de gérer votre réponse aux alertes.                                                                                                                                                                                                                                                                   | Nouveau                                                                                                                                                                                                                                               |
| Sévérité                                   | Indique l’impact possible sur les ressources. Plus la gravité est élevée, plus l’impact est important. En règle générale, les éléments de gravité plus élevés nécessitent une attention immédiate.<br>L’une des valeurs suivantes : *informatif* , *Low* , * medium et *High*.                                                                                                                                   | Moyen                                                                                                                                                                                                                                            |
| investigationId                           | ID d’enquête automatisé déclenché par cette alerte.                                                                                                                                                                                                                                                                                                                                | 1234                                                                                                                                                                                                                                              |
| investigationState                        | Informations sur l’état actuel de l’enquête. L’un des éléments suivants *: inconnu* , *terminé* , *SuccessfullyRemediated* , *bénigne* , *échec* , *PartiallyRemediated* , *en cours d’exécution* , *PendingApproval* , *PendingResource* , *PartiallyInvestigated* , *TerminatedByUser* , *TerminatedBySystem* , *mis en file d’attente* , *InnerFailure* , *PreexistingAlert* , non *pris en charge* , *UnsupportedAlertType* , *SuppressedAlert.* | UnsupportedAlertType                                                                                                                                                                                                                              |
| classification                            | Spécification de l’incident. Les valeurs de propriété sont les suivantes : *Unknown* , *FalsePositive* , *TruePositive* ou *null*                                                                                                                                                                                                                                                                   | Inconnu                                                                                                                                                                                                                                           |
| indications                             | Indique la détermination de l’incident. Les valeurs de propriété sont les suivantes : *NotAvailable* , *apt* , *Malware* , *SecurityPersonnel* , *SecurityTesting* , *UnwantedSoftware* , *other* ou  *null*                                                                                                                                                                                                     | Susceptibles                                                                                                                                                                                                                                               |
| assignedTo                                | Propriétaire de l’incident ou *valeur null* si aucun propriétaire n’est affecté.                                                                                                                                                                                                                                                                                                                            | secop2@contoso.com                                                                                                                                                                                                 |
| actorName                                 | Le groupe d’activités, le cas échéant, associé à cette alerte.                                                                                                                                                                                                                                                                                                                                        | DOSAGE                                                                                                                                                                                                                                             |
| threatFamilyName                          | Famille de menaces associée à cette alerte.                                                                                                                                                                                                                                                                                                                                                   | null                                                                                                                                                                                                                                              |
| mitreTechniques                           | Les techniques d’attaque, telles que alignées sur l’infrastructure [Mitre ATT&CK](https://attack.mitre.org/)™.                                                                                                                                                                                                                                                                                                                              | \[\]                                                                                                                                                                                                                                              |
| appareils                                   | Tous les appareils pour lesquels des alertes liées à l’incident ont été envoyées.                                                                                                                                                                                                                                                                                                     | \[\] (voir les détails sur les champs d’entité ci-dessous)                                                                                                                                                                                                         |
| **Format du périphérique**                             |                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                                                   |
| DeviceId                                  | ID de périphérique désigné dans Microsoft Defender pour le point de terminaison.                                                                                                                                                                                                                                                                                                                                                       | 24c222b0b60fe148eeece49ac83910cc6a7ef491                                                                                                                                                                                                          |
| aadDeviceId                               |  ID de périphérique désigné dans [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) (AAD). Disponible uniquement pour les appareils joints à un domaine.                                                                                                                                                                                                                                                                                                                              | null                                                                                                                                                                                                                                              |
| deviceDnsName                             | Nom de domaine complet du périphérique.                                                                                                                                                                                                                                                                                                                                                                        | user5cx.middleeast.corp.contoso.com                                                                                                                                                                                                    |
| osPlatform                                | Plateforme de système d’exploitation de l’appareil.                                                                                                                                                                                                                                                                                                                                                                     | WindowsServer2016                                                                                                                                                                                                                                 |
| osBuild                                   | Version de build pour le système d’exploitation sur lequel l’appareil est exécuté.                                                                                                                                                                                                                                                                                                                                                                | 14393                                                                                                                                                                                                                                             |
| rbacGroupName                             | Le groupe de [contrôle d’accès basé sur un rôle](https://docs.microsoft.com/azure/role-based-access-control/overview) (RBAC) associé au périphérique.                                                                                                                                                                                                                                                                                                                             | WDATP-Ring0                                                                                                                                                                                                                                       |
| firstSeen                                 | Heure du premier démarrage de l’appareil.                                                                                                                                                                                                                                                                                                                                                           | 2020-02-06T14:16:01.9330135 Z                                                                                                                                                                                                                      |
| healthStatus                              | État d’intégrité de l’appareil.                                                                                                                                                                                                                                                                                                                                                                        | Actif                                                                                                                                                                                                                                            |
| riskScore                                 | Score de risque de l’appareil.                                                                                                                                                                                                                                                                                                                                                                       | Élevé                                                                                                                                                                                                                                              |
| entités                                  | Toutes les entités identifiées comme faisant partie d’une alerte donnée ou associées à celle-ci.                                                                                                                                                                                                                                                                                | \[\] (voir les détails sur les champs d’entité ci-dessous)                                                                                                                                                                                                         |
| **Format d’entité**                             |                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                                                   |
| entityType                                | Entités identifiées comme faisant partie d’une alerte donnée ou associées à celle-ci.<br>Les valeurs des propriétés sont les suivantes : *User* , *IP* , *URL* , *file* , *Process* , *Mailbox* , *MailMessage* , *MailCluster* , *Registry*                                                                                                                                                                                                     | Utilisateur                                                                                                                                                                                                                                              |
| Algorithm                                      | Disponible si entityType est un *fichier*.<br>Hachage de fichier pour les alertes associées à un fichier ou à un processus.                                                                                                                                                                                                                                                                                    | 5de839186691aa96ee2ca6d74f0a38fb8d1bd6dd                                                                                                                                                                                                          |
| SHA256                                    | Disponible si entityType est un *fichier*.<br>Hachage de fichier pour les alertes associées à un fichier ou à un processus.                                                                                                                                                                                                                                                                                    | 28cb017dfc99073aa1b47c1b30f413e3ce774c4991eb4158de50f9dbb36d8043                                                                                                                                                                                  |
| fileName                                  | Disponible si entityType est un *fichier*.<br>Nom de fichier pour les alertes associées à un fichier ou à un processus                                                                                                                                                                                                                                                                                    | Detector.UnitTests.dll                                                                                                                                                                                                                            |
| PCF                                  | Disponible si entityType est un *fichier*.<br>Chemin d’accès de fichier pour les alertes associées à un fichier ou à un processus                                                                                                                                                                                                                                                                                    | C : \\ \\ travail de l’agent \\ \\ \_ \\ \\ \_ temp \\ \\ Deploy \_ System 2020-09-06 12 \_ 14 \_ 54 \\ \\ out                                                                                                                                                                    |
| processId                                 | Disponible si entityType est *Process*.                                                                                                                                                                                                                                                                                                                                                     | 24348                                                                                                                                                                                                                                             |
| processCommandLine                        | Disponible si entityType est *Process*.                                                                                                                                                                                                                                                                                                                                                     | « \\ Votre fichier est prêt à être téléchargé \_1911150169.exe\\ »                                                                                                                                                                                           |
| processCreationTime                       | Disponible si entityType est *Process*.                                                                                                                                                                                                                                                                                                                                                     | 2020-07-18T03:25:38.5269993 Z                                                                                                                                                                                                                      |
| parentProcessId                           | Disponible si entityType est *Process*.                                                                                                                                                                                                                                                                                                                                                   | 16840                                                                                                                                                                                                                                             |
| parentProcessCreationTime                 | Disponible si entityType est *Process*.                                                                                                                                                                                                                                                                                                                                                     | 2020-07-18T02:12:32.8616797 Z                                                                                                                                                                                                                      |
| ipAddress                                 | Disponible si entityType est *IP*. <br>Adresse IP pour les alertes associées à des événements réseau, comme *la communication avec une destination réseau malveillante*.                                                                                                                                                                                                                                   | 62.216.203.204                                                                                                                                                                                                                                    |
| url                                       | Disponible si entityType est *URL*. <br>URL pour les alertes associées aux événements réseau, comme *la communication à une destination réseau malveillante*.                                                                                                                                                                                                                                  | down.esales360.cn                                                                                                                                                                                                                                 |
| accountName                               | Disponible si entityType est *User*.                                                                                                                                                                                                                                                                                                                                                         | testUser2                                                                                                                                                                                                                                         |
| domainName                                | Disponible si entityType est *User*.                                                                                                                                                                                                                                                                                                                                                        | Europe. Corp. contoso                                                                                                                                                                                                                              |
| userSid                                   | Disponible si entityType est *User*.                                                                                                                                                                                                                                                                                                                                                        | S-1-5-21-1721254763-462695806-1538882281-4156657                                                                                                                                                                                                  |
| aadUserId                                 | Disponible si entityType est *User*.                                                                                                                                                                                                                                                                                                                                                        | fc8f7484-f813-4db2-afab-bc1507913fb6                                                                                                                                                                                                              |
| userPrincipalName                         | Disponible si EntityType est *User* la / *boîte aux lettres* utilisateur / *MailMessage*.                                                                                                                                                                                                                                                                                                                                | testUser2@contoso.com                                                                                                                                                                                      |
| mailboxDisplayName                        | Disponible si entityType est *Mailbox*.                                                                                                                                                                                                                                                                                                                                                     | test utilisateur2                                                                                                                                                                                                                                        |
| mailboxAddress                            | Disponible si EntityType est *User* la / *boîte aux lettres* utilisateur / *MailMessage*.                                                                                                                                                                                                                                                                                                                                | testUser2@contoso.com                                                                                                                                                                                      |
| clusterBy                                 | Disponible si entityType est  *MailCluster*.                                                                                                                                                                                                                                                                                                                                                 | Experts P2SenderDomain; ContentType                                                                                                                                                                                                                |
| sender                                    | Disponible si EntityType est *User* la / *boîte aux lettres* utilisateur / *MailMessage*.                                                                                                                                                                                                                                                                                                                                  | user.abc@mail.contoso.co.in                                                                                                                                                                 |
| destinataire                                 | Disponible si entityType est *MailMessage*.                                                                                                                                                                                                                                                                                                                                                | testUser2@contoso.com                                                                                                                                                                                       |
| sujet                                   | Disponible si entityType est *MailMessage*.                                                                                                                                                                                                                                                                                                                                                 | \[\]Attention externe                                                                                                                                                                                                                            |
| deliveryAction                            | Disponible si entityType est *MailMessage*.                                                                                                                                                                                                                                                                                                                                                 | Cmds                                                                                                                                                                                                                                         |
| securityGroupId                           | Disponible si entityType est  *SecurityGroup*.                                                                                                                                                                                                                                                                                                                                               | 301c47c8-e15f-4059-AB09-e2ba9ffd372b                                                                                                                                                                                                              |
| securityGroupName                         | Disponible si entityType est  *SecurityGroup*.                                                                                                                                                                                                                                                                                                                                               | Opérateurs de configuration réseau                                                                                                                                                                                                                   |
| registryHive                              | Disponible si entityType est  *Registry*.                                                                                                                                                                                                                                                                                                                                                    | HKEY \_ local \_ machine                                                                                                                                                                                                                              |
| registryKey                               | Disponible si entityType est  *Registry*.                                                                                                                                                                                                                                                                                                                                                     | LOGICIEL \\ \\ Microsoft \\ \\ Windows NT \\ \\ CurrentVersion \\ \\ Winlogon                                                                                                                                                                                 |
| registryValueType                         | Disponible si entityType est  *Registry*.                                                                                                                                                                                                                                                                                                                                                    | String                                                                                                                                                                                                                                            |
| registryValue                             | Disponible si entityType est  *Registry*.                                                                                                                                                                                                                                                                                                                                                    | 31-00-00-00                                                                                                                                                                                                                                       |
| deviceId                                  | ID, le cas échéant, de l’appareil associé à l’entité.                                                                                                                                                                                                                                                                                                                                           | 986e5df8b73dacd43c8917d17e523e76b13c75cd                                                                                                                                                                                                          |



## <a name="example"></a>Exemple

**Demande**

```
GET https://api.security.microsoft.com/api/incidents
```

**Response**
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

## <a name="related-topic"></a>Voir aussi
- [API d’incident](api-incident.md)
- [Incident de mise à jour](api-update-incidents.md)
