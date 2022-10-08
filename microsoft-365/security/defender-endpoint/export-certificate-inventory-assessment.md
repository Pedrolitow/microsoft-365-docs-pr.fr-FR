---
title: Méthodes et propriétés d’évaluation des certificats par appareil
description: Fournit des informations sur les API de certificats qui extraient des données « Gestion des vulnérabilités Microsoft Defender ». Il existe différents appels d’API pour obtenir différents types de données. En général, chaque appel d’API contient les données requises pour les appareils de votre organisation.
keywords: api, api, évaluation d’exportation, évaluation par appareil, évaluation par ordinateur, rapport d’évaluation des vulnérabilités, évaluation des vulnérabilités des appareils, rapport de vulnérabilité des appareils, évaluation de la configuration sécurisée, rapport de configuration sécurisée, évaluation des vulnérabilités logicielles, rapport de vulnérabilité logicielle, rapport de vulnérabilité par ordinateur,
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: article
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: c20f09fe95668d229ab9716ac43818bd0569a22d
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68200250"
---
# <a name="export-certificate-inventory-per-device"></a>Exporter l’inventaire des certificats par appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Gestion des vulnérabilités de Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Gestion des vulnérabilités Microsoft Defender ? En savoir plus sur la façon dont vous pouvez vous inscrire à la [Gestion des vulnérabilités Microsoft Defender préversion publique](../defender-vulnerability-management/get-defender-vulnerability-management.md).

Il existe différents appels d’API pour obtenir différents types de données. En général, chaque appel d’API contient les données requises pour les appareils de votre organisation.

- **Réponse JSON**  L’API extrait toutes les données de votre organisation en tant que réponses JSON. Cette méthode est idéale pour _les petites organisations avec moins de 100 K d’appareils_. La réponse étant paginée, vous pouvez utiliser le \@champ odata.nextLink de la réponse pour extraire les résultats suivants.

- **via des fichiers** Cette solution d’API permet d’extraire de plus grandes quantités de données plus rapidement et de manière plus fiable. Par conséquent, il est recommandé pour les grandes organisations, avec plus de 100 000 appareils. Cette API extrait toutes les données de votre organisation en tant que fichiers de téléchargement. La réponse contient des URL pour télécharger toutes les données à partir du stockage Azure. Vous pouvez télécharger des données à partir du Stockage Azure comme suit :
  - Appelez l’API pour obtenir la liste des URL de téléchargement avec toutes les données de votre organisation.
  - Téléchargez tous les fichiers à l’aide des URL de téléchargement et traitez les données comme vous le souhaitez.

Les données collectées à l’aide de la _« réponse JSON_ ou _par le biais de fichiers_ » sont l’instantané actuel de l’état actuel. Il ne contient pas de données historiques. Pour collecter des données historiques, les clients doivent enregistrer les données dans leurs propres stockages de données.

> [!NOTE]
> Sauf indication contraire, toutes les méthodes d’évaluation de la base de référence de sécurité d’exportation répertoriées sont **_des méthodes d’exportation complètes_** et **_par appareil_** (également appelées **_par appareil_**)

## <a name="1-export-certificate-assessment-json-response"></a>1. Exporter l’évaluation de certificat (réponse JSON)

### <a name="11-api-method-description"></a>Description de la méthode d’API 1.1

Retourne toutes les évaluations de certificats pour tous les appareils, par appareil. Elle retourne une table avec une entrée distincte pour chaque combinaison unique de DeviceId, Thumbprint et Path.

#### <a name="111-limitations"></a>1.1.1 Limitations

- La taille maximale de la page est de 200 000.
- Les limites de débit pour cette API sont de 30 appels par minute et de 1 000 appels par heure.

### <a name="12-permissions"></a>1.2 Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API pour plus d’informations.](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Software.Read.All|« Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités »
Déléguée (compte professionnel ou scolaire)|Software.Read|« Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités »

### <a name="13-url"></a>URL 1.3

```http
GET /api/machines/certificateAssessmentByMachine
```

### <a name="14-parameters"></a>1.4 Paramètres

- pageSize (valeur par défaut = 50 000) : nombre de résultats en réponse.
- $top : nombre de résultats à retourner (ne retourne pas @odata.nextLink et n’extrait donc pas toutes les données).


### <a name="15-properties-json-response"></a>1.5 Propriétés (réponse JSON)

> [!NOTE]
> Chaque enregistrement est d’environ 1 Ko de données. Vous devez en tenir compte lors du choix du paramètre pageSize correct.
>
> Certaines colonnes supplémentaires peuvent être retournées dans la réponse. Ces colonnes sont temporaires et peuvent être supprimées. Utilisez uniquement les colonnes documentées.
>
> Les propriétés définies dans le tableau suivant sont répertoriées par ordre alphabétique par ID de propriété. Lors de l’exécution de cette API, la sortie résultante ne sera pas nécessairement retournée dans le même ordre que celui répertorié dans ce tableau.

Propriété (ID)|Type de données|Description
:---|:---|:---
|DeviceId|Chaîne|Identificateur unique de l’appareil dans le service.
|DeviceName|Chaîne|Nom de domaine complet (FQDN) de l’appareil.
|Empreinte|Boolean|Identificateur unique du certificat.
|Path|Chaîne|Emplacement du certificat.
|SignatureAlgorithm|Chaîne|Algorithme de hachage et algorithme de chiffrement utilisés.
|KeySize|Chaîne|Taille de la clé utilisée dans l’algorithme de signature.
|ExpirationDate|Chaîne|Date et heure au-delà desquelles le certificat n’est plus valide.
|IssueDate|Chaîne|Date et heure les plus anciennes à laquelle le certificat est devenu valide.
|SubjectType|Chaîne|Indique si le titulaire du certificat est une autorité de certification ou une entité de fin.
|Numéro de série|Chaîne|Identificateur unique du certificat dans les systèmes d’une autorité de certification.
|IssuedTo|Objet|Entité à laquelle appartient un certificat ; peut être un appareil, un individu ou une organisation.
|IssuedBy|Objet|Entité qui a vérifié les informations et signé le certificat.
|KeyUsage|Chaîne|Utilisations de chiffrement valides de la clé publique du certificat.
|ExtendedKeyUsage|Chaîne|Autres utilisations valides pour le certificat.
|RbacGroupId|Chaîne|ID de groupe de contrôle d’accès en fonction du rôle (RBAC).
|RbacGroupName|Chaîne|Groupe de contrôle d’accès en fonction du rôle (RBAC). Si cet appareil n’est affecté à aucun groupe RBAC, la valeur est « Non attribué ». Si l’organisation ne contient aucun groupe RBAC, la valeur est « None ».

## <a name="16-example"></a>Exemple 1.6

### <a name="161-request-example"></a>Exemple de demande 1.6.1

```http
GET https://api.securitycenter.microsoft.com/api/machines/BaselineComplianceAssessmentByMachine
```

### <a name="162-response-example"></a>1.6.2 Exemple de réponse

```json

  {
     "@odata.context":"https://127.0.0.1/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetCertificateAssessment)",
      "value":[
        {
        "deviceId":"49126b9e4a5473b5229c73799e9e55c48668101b",
        "deviceName":"testmachine5",
        "thumbprint":"A4B37F4F6DE956922273D5CB8E7E0AAFB7033B90",
        "path":"LocalMachine\\TestSignRoot\\A4B37F4F6DE956922273D5CB8E7E0AAFB7033B90",
        "signatureAlgorithm":"sha384ECDSA",
        "keyLength":0,"notAfter":"0001-01-01T00:00:00Z",
        "notBefore":"0001-01-01T00:00:00Z",
        "subjectType":"CA",
        "serialNumber":"6086A185EAFA2B9943B4671603F40323",
        "subjectObject":null,
        "issuerObject":null,
        "keyUsageArray":null,
        "extendedKeyUsageArray":null,
        "isSelfSigned":false,
        "rbacGroupId":4226,
        "rbacGroupName":"testO6343398Gq31"}],
        "@odata.nextLink":"https://127.0.0.1/api/machines/CertificateAssessmentByMachine?pagesize=1&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMi0wMy0yMS8wNTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjF9"
  }
```

## <a name="2-export-certificate-assessment-via-files"></a>2. Exporter l’évaluation des certificats (via des fichiers)

### <a name="21-api-method-description"></a>Description de la méthode API 2.1

Retourne toutes les évaluations de certificats pour tous les appareils, par appareil. Elle retourne une table avec une entrée distincte pour chaque combinaison unique de DeviceId, Thumbprint et Path.

#### <a name="211-limitations"></a>2.1.1 Limitations

- Les limites de débit pour cette API sont de 5 appels par minute et de 20 appels par heure.

### <a name="22-permissions"></a>2.2 Autorisations

L’une des autorisations suivantes est requise pour appeler cette API. Pour plus d’informations, notamment sur le choix des autorisations, consultez [Utiliser Microsoft Defender pour point de terminaison API pour plus d’informations.](apis-intro.md)

Type d’autorisation|Autorisation|Nom d’affichage de l’autorisation
:---|:---|:---
Application|Software.Read.All|« Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités »
Déléguée (compte professionnel ou scolaire)|Software.Read|« Lire les informations sur les logiciels de gestion des menaces et des vulnérabilités »

### <a name="23-url"></a>URL 2.3

```http
GET /api/machines/certificateAssessmentExport
```

### <a name="24-parameters"></a>2.4 Paramètres

- sasValidHours : nombre d’heures pendant lesquelles les URL de téléchargement sont valides (maximum 24 heures).

### <a name="25-properties-json-response"></a>2.5 Propriétés (réponse JSON)

> [!NOTE]
> Les fichiers sont compressés par gzip & au format Json multiligne.
>
> Les URL de téléchargement ne sont valides que pendant 3 heures ; sinon, vous pouvez utiliser le paramètre.
>
> Pour optimiser les vitesses de téléchargement, assurez-vous que vous téléchargez les données à partir de la même région Azure où se trouvent vos données.
>
> Chaque enregistrement est d’environ 1 Ko de données. Vous devez en tenir compte lors du choix du paramètre pageSize qui vous convient.
>
> Certaines colonnes supplémentaires peuvent être retournées dans la réponse. Ces colonnes sont temporaires et peuvent être supprimées. Utilisez uniquement les colonnes documentées.

Propriété (ID)|Type de données|Description
:---|:---|:---
|Exporter des fichiers|String[array]|Liste des URL de téléchargement pour les fichiers contenant l’instantané actuel de l’organisation.
|GeneratedTime|Date/heure|Heure à laquelle l’exportation a été générée.


## <a name="26-example"></a>2.6 Exemple

### <a name="261-request-example"></a>2.6.1 Exemple de requête

```http
GET https://api.securitycenter.contoso.com/api/machines/certificateAssessmentExport
```

### <a name="262-response-example"></a>2.6.2 Exemple de réponse

```json
    {
        "@odata.context":"https://127.0.0.1/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
        "exportFiles":["https://tvmexportexternalstgeus.blob.core.windows.net/temp-5c080622-f613-42bb-9fee-e17ccdff90d3/2022-03-20/1318/CertificateAssessmentExport/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=4226/part-00000-65a62a9d-7a01-4d78-bbdb-6d3e07b34cc9.c000.json.gz?sv=2020-02-10&st=2022-03-20T13%3A35%3A37Z&se=2022-03-20T16%3A35%3A37Z&sr=b&sp=r&sig=IMmwTOYmGvU0ei5AHLNAxnFCmZkE2jvBHzRmuAu9xaA%3D","https://tvmexportexternalstgeus.blob.core.windows.net/temp-5c080622-f613-42bb-9fee-e17ccdff90d3/2022-03-20/1318/CertificateAssessmentExport/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=4414/part-00000-65a62a9d-7a01-4d78-bbdb-6d3e07b34cc9.c000.json.gz?sv=2020-02-10&st=2022-03-20T13%3A35%3A37Z&se=2022-03-20T16%3A35%3A37Z&sr=b&sp=r&sig=2r0y74WZsATa0DjQTwfBxNqL5vN2Wl0AZKHMNrxuJ30%3D","https://tvmexportexternalstgeus.blob.core.windows.net/temp-5c080622-f613-42bb-9fee-e17ccdff90d3/2022-03-20/1318/CertificateAssessmentExport/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=75/part-00000-65a62a9d-7a01-4d78-bbdb-6d3e07b34cc9.c000.json.gz?sv=2020-02-10&st=2022-03-20T13%3A35%3A37Z&se=2022-03-20T16%3A35%3A37Z&sr=b&sp=r&sig=uVdY4%2BBpMdPMwaD3G0RJTZkS4R9J8oN8I3tu%2FOcG35c%3D"],
        "generatedTime":"2022-03-20T13:18:00Z"
   }
```
