---
title: Répertorier toutes les activités de correction
description: Retourne des informations sur toutes les activités de correction.
keywords: api, correction, api de correction, obtenir, tâches de correction, toutes les corrections,
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
ms.openlocfilehash: e1d8b3f8d43bb1323ddc703cb4041ecaa5536d68f7c83acb1140f9158ae3774d
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53793765"
---
# <a name="list-all-remediation-activities"></a>Répertorier toutes les activités de correction

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>Description de l’API

Retourne des informations sur toutes les activités de correction.

[En savoir plus sur les activités de correction.](tvm-remediation.md)

**URL :** GET: /api/remediationTasks

## <a name="permissions"></a>Autorisations

L’une des autorisations suivantes est nécessaire pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, voir Utiliser Microsoft Defender pour les API de point de [terminaison pour plus d’informations.](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|RemediationTask.Read.All|\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'
Déléguée (compte professionnel ou scolaire)|RemediationTask.Read|\'Lire les informations sur les vulnérabilités de gestion des menaces et des vulnérabilités\'

## <a name="properties"></a>Propriétés

Propriété (id)|Type de données|Description|Exemple de valeur renvoyée
:---|:---|:---|:---
category|String|Catégorie de l’activité de correction (configuration logicielle/sécurité)|Logiciels
completerEmail|Chaîne|Si l’activité de correction a été effectuée manuellement par une personne, cette colonne contient son courrier électronique|null
completerId|Chaîne|Si l’activité de correction a été effectuée manuellement par une personne, cette colonne contient son ID d’objet|null
completionMethod|Chaîne|Une activité de correction peut être effectuée « automatiquement » (si tous les appareils sont corrigés) ou « manuellement » par une personne qui sélectionne « marquer comme terminé »|Automatic
createdOn|Date/heure|Heure de création de cette activité de correction|2021-01-12T18:54:11.5499478Z
description|Chaîne|Description de cette activité de correction|Mettez à jour Microsoft Silverlight vers une version ultérieure pour atténuer les vulnérabilités connues affectant vos appareils.
dueOn|Date/heure|Date d’échéance définie par le créateur pour cette activité de correction|2021-01-13T00:00:00Z
fixedDevices|.|Nombre d’appareils qui ont été corrigés|2
id|Chaîne|ID de cette activité de correction|097d9735-5479-4899-b1b7-77398899df92
nameId|Chaîne|Nom du produit associé|Microsoft Silverlight
priorité|Chaîne|Priorité définie par le créateur pour cette activité de correction (Haute\Moyenne\Faible)|Élevé
productId|Chaîne|ID de produit associé|microsoft-_-silverlight
productivityImpactRemediationType|Chaîne|Quelques modifications de configuration peuvent être demandées uniquement pour les appareils sans impact sur l’utilisateur. Cette valeur indique la sélection entre « tous les appareils exposés » ou « uniquement les appareils sans impact sur l’utilisateur ».|AllExposedAssets
rbacGroupNames|Chaîne|Noms de groupes d’appareils associés|[ « Windows Servers », « Windows 10 » ]
recommendedProgram|Chaîne|Programme recommandé pour la mise à niveau vers|null
recommendedVendor|Chaîne|Fournisseur recommandé pour la mise à niveau vers|null
recommendedVersion|Chaîne|Version recommandée pour la mise à jour/mise à niveau vers|null
relatedComponent|Chaîne|Composant connexe de cette activité de correction (similaire au composant associé pour une recommandation de sécurité)|Microsoft Silverlight
requesterEmail|Chaîne|Adresse de messagerie du créateur|globaladmin@UserName.contoso.com
requesterId|Chaîne|ID d’objet Creator|r647211f-2e16-43f2-a480-16ar3a2a796r
requesterNotes|Chaîne|Notes (texte libre) ajoutées par le créateur pour cette activité de correction|null
scid|Chaîne|SCID de la recommandation de sécurité associée|null
status|Chaîne|État de l’activité de correction (actif/terminé)|Actif
statusLastModifiedOn|Date/heure|Date de mise à jour du champ d’état|2021-01-12T18:54:11.5499487Z
targetDevices|Entier long|Nombre d’appareils exposés pour qui cette correction s’applique|43
title|Chaîne|Titre de cette activité de correction|Mettre à jour Microsoft Silverlight
type|Chaîne|Type de correction|Update
vendorId|Chaîne|Nom du fournisseur associé|Microsoft

## <a name="example"></a>Exemple

### <a name="request-example"></a>Exemple de requête

```http
GET https://api-luna.securitycenter.windows.com/api/remediationtasks/
```

### <a name="response-example"></a>Exemple de réponse

```json
{
    "@odata.context": "https://wpatdadi-luna-stg.cloudapp.net/api/$metadata#RemediationTasks",
    "value": [
        {
            "id": "03942ef5-aewb-4w6e-b555-d6a97013844w",
            "title": "Update Microsoft Silverlight",
            "createdOn": "2021-02-10T13:20:36.4718166Z",
            "requesterId": "65548a1d-ef00-4a7a-8d19-1b967b5c36f4",
            "requesterEmail": "user1@contoso.com",
            "status": "Active",
            "statusLastModifiedOn": "2021-02-10T13:20:36.4719698Z",
            "description": "Update Silverlight to a later version  to mitigate 55 known vulnerabilities affecting your devices. Doing so can help lessen the security risk to your organization due to versions which have reached their end-of-support.  ",
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
    ]
}
```

## <a name="see-also"></a>Voir aussi

- [Méthodes et propriétés de correction](get-remediation-methods-properties.md)
- [Obtenir une activité de correction par son ID](get-remediation-one-activity.md)
- [Répertorier les appareils exposés d’une activité de correction](get-remediation-exposed-devices-activities.md)
- [Menaces basées sur les risques & gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Vulnérabilités dans votre organisation](tvm-weaknesses.md)
