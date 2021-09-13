---
title: Répertorier les appareils exposés d’une activité de correction
description: Retourne des informations sur les appareils exposés pour la tâche de correction spécifiée.
keywords: api, correction, api de correction, obtenir, tâches de correction, correction des appareils exposés
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 1ee64608e9ce6ce24dc40f1729303ef99b162cab
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59182009"
---
# <a name="list-exposed-devices-of-one-remediation-activity"></a>Répertorier les appareils exposés d’une activité de correction

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Retourne des informations sur les appareils exposés pour la tâche de correction spécifiée.

[En savoir plus sur les activités de correction.](tvm-remediation.md)

## <a name="list-exposed-devices-associated-with-a-remediation-task-id"></a>Liste des appareils exposés associés à une tâche de correction (ID)

**URL :** GET: /api/remediationTasks/ \{ id \} /machineReferences

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, voir Utiliser Microsoft Defender pour les API de point de [terminaison pour plus d’informations.](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|RemediationTasks.Read.All|\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'
Déléguée (compte professionnel ou scolaire)|RemediationTask.Read.Read|\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'

## <a name="properties-details"></a>Détails des propriétés

Propriété (id)|Type de données|Description|Exemple
:---|:---|:---|:---
id|Chaîne|ID d’appareil|w2957837fwda8w9ae7f023dba081059dw8d94503
computerDnsName|Chaîne|Nom du périphérique|PC-SRV2012R2Foo.UserNameVldNet.local
osPlatform|Chaîne|Système d’exploitation d’appareil|WindowsServer2012R2
rbacGroupName|Chaîne|Nom du groupe d’appareils associé à cet appareil|Serveurs

## <a name="example"></a>Exemple

### <a name="request-example"></a>Exemple de requête

```http
GET https://api-luna.securitycenter.windows.com/api/remediationtasks/03942ef5-aecb-4c6e-b555-d6a97013844c/machinereferences
```

### <a name="response-example"></a>Exemple de réponse

```json
{
    "@odata.context": "https://wpatdadi-luna-stg.cloudapp.net/api/$metadata#MachineReferences",
    "value": [
        {
            "id": "3cb5df6bb3640a2d37ad09fcd357b182d684fafc",
            "computerDnsName": "ComputerPII_2ea21b2d97c9df23c143ad9e3e454cb674232529.DomainPII_21eed80b086e79bdfa178eabfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2016",
            "rbacGroupName": "UnassignedGroup",

        },
        {
            "id": "3d9b1ca53e8f077199c7dcbfc9dbfa78f9bf1918",
            "computerDnsName": "ComputerPII_001d606fc149567c192747f48fae304b43c0ddba.DomainxPII_21eed80b086e79bdfa178eabfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2012R2",
            "rbacGroupName": "UnassignedGroup",

        },
        {
            "id": "3db8b27e6172951d7ea2e2d75945abec56feaf82",
            "computerDnsName": "ComputerPII_ce60cfbjj4b82a091deb5eae560332bba99a9bd7.DomainPII_0bc1aee0fa396d175e514bd61a9e7a5b2b07ee8e.corp.contoso.com",
            "osPlatform": "WindowsServer2016",
            "rbacGroupName": "UnassignedGroup",

        },
        {
            "id": "3bad326dcda5b53fab47408cd4a7080f3f3cc8ab",
            "computerDnsName": "ComputerPII_b6b35960dd6539d1d1cef5ada02e235e7b357408.DomainPII_21eed80b089e76bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2012R2",
            "rbacGroupName": "UnassignedGroup",

        }
]
}
```

## <a name="see-also"></a>Voir aussi

- [Méthodes et propriétés de correction](get-remediation-methods-properties.md)
- [Obtenir une activité de correction par son ID](get-remediation-one-activity.md)
- [Répertorier toutes les activités de correction](get-remediation-all-activities.md)
- [Menaces basées sur les risques & gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Vulnérabilités dans votre organisation](tvm-weaknesses.md)
