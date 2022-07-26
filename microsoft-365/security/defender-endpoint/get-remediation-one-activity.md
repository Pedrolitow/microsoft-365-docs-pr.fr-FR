---
title: Obtenir une activité de correction par son ID
description: Retourne des informations pour l’activité de correction spécifiée.
keywords: api, correction, api de correction, get, tâches de correction, correction par ID,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 1d2d96ab3b2b2166fab70a324a0f3d22dab61cd7
ms.sourcegitcommit: 6e570b79944862c86735db455349b685d5b903b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2022
ms.locfileid: "67020052"
---
# <a name="get-one-remediation-activity-by-id"></a>Obtenir une activité de correction par son ID

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Gestion des vulnérabilités de Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> Vous voulez découvrir Gestion des vulnérabilités Microsoft Defender ? En savoir plus sur la façon dont vous pouvez vous inscrire à la [Gestion des vulnérabilités Microsoft Defender préversion publique](../defender-vulnerability-management/get-defender-vulnerability-management.md).

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Retourne des informations pour l’activité de correction spécifiée. Présente les mêmes colonnes que [l’activité d’obtention de toutes les corrections](get-remediation-all-activities.md), mais retourne les résultats _uniquement pour l’activité de correction spécifiée_.

[En savoir plus sur les activités de correction](tvm-remediation.md).

## <a name="list-a-specified-remediation-activity-for-id"></a>Répertorier une activité de correction spécifiée pour (ID)

**URL:** GET : /api/remediationTasks/\{id\}

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API pour plus d’informations.](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|RemediationTasks.Read.All|\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'
Déléguée (compte professionnel ou scolaire)|RemediationTask.Read.Read|\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'

## <a name="properties"></a>Propriétés

Propriété (ID)|Type de données|Description|Exemple de valeur retournée
:---|:---|:---|:---
Catégorie|String|Catégorie de l’activité de correction (configuration de logiciel/sécurité)|Logiciels
completerEmail|String|Si l’activité de correction a été effectuée manuellement par une personne, cette colonne contient son e-mail|Null
completerId|String|Si l’activité de correction a été effectuée manuellement par une personne, cette colonne contient son ID d’objet|Null
completionMethod|String|Une activité de correction peut être effectuée « automatiquement » (si tous les appareils sont corrigés) ou « manuellement » par une personne qui sélectionne « Marquer comme terminé »|Automatique
createdOn|Date/heure|Heure de création de cette activité de correction|2021-01-12T18:54:11.5499478Z
Description|String|Description de cette activité de correction|Mettez à jour Microsoft Silverlight vers une version ultérieure pour atténuer les vulnérabilités connues affectant vos appareils.
dueOn|Date/heure|Date d’échéance définie par le créateur pour cette activité de correction|2021-01-13T00:00:00Z
fixedDevices||Nombre d’appareils qui ont été corrigés|2
ID|String|ID de cette activité de correction|097d9735-5479-4899-b1b7-77398899df92
nameId|String|Nom du produit associé|Microsoft Silverlight
Priorité|String|Priorité définie par le créateur pour cette activité de correction (High\Medium\Low)|Élevé
Productid|String|ID de produit associé|microsoft-_-silverlight
productivityImpactRemediationType|String|Quelques modifications de configuration peuvent être demandées uniquement pour les appareils qui n’affectent pas les utilisateurs. Cette valeur indique la sélection entre « tous les appareils exposés » ou « uniquement les appareils sans impact utilisateur ».|AllExposedAssets
rbacGroupNames|String|Noms de groupes d’appareils associés|[ « Serveurs Windows », « Windows 11 », « Windows 10 » ]
recommendedProgram|String|Programme recommandé pour la mise à niveau vers|Null
recommendedVendor|String|Fournisseur recommandé pour la mise à niveau vers|Null
recommendedVersion|String|Version recommandée pour mettre à jour/mettre à niveau vers|Null
relatedComponent|String|Composant associé de cette activité de correction (similaire au composant associé pour une recommandation de sécurité)|Microsoft Silverlight
requesterEmail|String|Adresse e-mail du créateur|globaladmin@UserName.contoso.com
requesterId|String|ID d’objet Creator|r647211f-2e16-43f2-a480-16ar3a2a796r
requesterNotes|String|Les notes (texte libre) que le créateur a ajoutées pour cette activité de correction|Null
Scid|String|SCID de la recommandation de sécurité associée|Null
État|String|État de l’activité de correction (actif/terminé)|Actif
statusLastModifiedOn|Date/heure|Date de mise à jour du champ d’état|2021-01-12T18:54:11.5499487Z
targetDevices|Entier long|Nombre d’appareils exposés auxquels cette correction s’applique|43
Titre|Chaîne|Titre de cette activité de correction|Microsoft Silverlight
Type|String|Type de correction|Update
vendorId|String|Nom du fournisseur associé|Microsoft

## <a name="example"></a>Exemple

### <a name="request-example"></a>Exemple de requête

```http
GET https://api-luna.securitycenter.windows.com/api/remediationtasks/03942ef5-aecb-4c6e-b555-d6a97013844c
```

### <a name="response-example"></a>Exemple de réponse

```json
{
    "@odata.context": "https://wpatdadi-luna-stg.cloudapp.net/api/$metadata#RemediationTasks/$entity",
    "id": "03942ef5-aecb-4c6e-b555-d6a97013844c",
    "title": "Update Microsoft Silverlight",
    "createdOn": "2021-02-10T13:20:36.4718166Z",
    "requesterId": "65548a1d-efo0-4a7a-8d19-1b967b5c36f4",
    "requesterEmail": "user1@contoso.com",
    "status": "Active",
    "statusLastModifiedOn": "2021-02-10T13:20:36.4719698Z",
    "description": "Update Silverlight to a later version to mitigate 55 known vulnerabilities affecting your devices. Doing so can help lessen the security risk to your organization due to versions which have reached their end-of-support.",
    "relatedComponent": "Microsoft Silverlight",
    "targetDevices": 18511,
    "rbacGroupNames": [
        "UnassignedGroup",
        "hhh"
    ],
    "fixedDevices": 2866,
    "requesterNotes": "test",
    "dueOn": "2021-02-11T00:00:00Z",
    "category": "Software",
    "productivityImpactRemediationType": null,
    "priority": "Medium",
    "completionMethod": null,
    "completerId": null,
    "completerEmail": null,
    "scid": null,
    "type": "Update",
    "productId": "microsoft-_-silverlight",
    "vendorId": "microsoft",
    "nameId": "silverlight",
    "recommendedVersion": null,
    "recommendedVendor": null,
    "recommendedProgram": null
}
```

## <a name="see-also"></a>Voir aussi

- [Méthodes et propriétés de correction](get-remediation-methods-properties.md)
- [Répertorier toutes les activités de correction](get-remediation-all-activities.md)
- [Répertorier les appareils exposés d’une activité de correction](get-remediation-exposed-devices-activities.md)
- [Gestion des vulnérabilités & des menaces basées sur les risques](next-gen-threat-and-vuln-mgt.md)
- [Vulnérabilités dans votre organisation](tvm-weaknesses.md)
