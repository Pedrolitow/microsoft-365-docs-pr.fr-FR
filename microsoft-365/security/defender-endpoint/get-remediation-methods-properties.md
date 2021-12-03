---
title: Méthodes et propriétés des activités de correction
description: La réponse d’API contient les & gestion des vulnérabilités de correction des menaces créées dans votre client. Vous pouvez demander toutes les activités de correction, une seule activité de correction ou des informations sur les appareils exposés pour une tâche de correction sélectionnée.
keywords: api, correction, api de correction, obtenir, tâches de correction, méthodes de correction, propriétés de correction,
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
ms.openlocfilehash: 8a6656f6a75c24a475e5b8788caf1e9b9ef5d743
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2021
ms.locfileid: "61300969"
---
# <a name="remediation-activity-methods-and-properties"></a>Méthodes et propriétés des activités de correction

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

La réponse de l’API [contient les & gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)de correction des menaces qui ont été   créées dans votre client.

## <a name="methods"></a>Méthodes

Méthode|Type de données|Description
:---|:---|:---
[Répertorier toutes les activités de correction](get-remediation-all-activities.md)|Collection d’examens|Retourne des informations sur toutes les activités de correction.
[Répertorier les appareils exposés d’une activité de correction](get-remediation-exposed-devices-activities.md)|Entité Investigation|Retourne des informations sur les appareils exposés pour l’activité de correction spécifiée.
[Obtenir une activité de correction par son ID](get-remediation-one-activity.md)|Entité Investigation|Renvoie des informations pour l’activité de correction spécifiée.

En savoir plus sur [les activités de correction.](tvm-remediation.md)

## <a name="properties"></a>Propriétés

ID de propriété|Type de données|Description
:---|:---|:---
Catégorie|String|Catégorie de l’activité de correction (configuration logicielle/sécurité)
completerEmail|Chaîne|Si l’activité de correction a été effectuée manuellement par une personne, cette colonne contient son courrier électronique
completerId|Chaîne|Si l’activité de correction a été effectuée manuellement par une personne, cette colonne contient son ID d’objet
completionMethod|String|Une activité de correction peut être effectuée « automatiquement » (si tous les appareils sont corrigés) ou « manuellement » par une personne qui sélectionne « marquer comme terminé ».
createdOn|Date/heure|Heure de création de cette activité de correction
Description|Chaîne|Description de cette activité de correction
dueOn|Date/heure|Date d’échéance définie par le créateur pour cette activité de correction
fixedDevices||Nombre d’appareils qui ont été corrigés
ID|String|ID de cette activité de correction
nameId|Chaîne|Nom du produit associé
Priorité|String|Priorité définie par le créateur pour cette activité de correction (High\Medium\Low)
productId|String|ID de produit associé
productivityImpactRemediationType|String|Quelques modifications de configuration peuvent être demandées uniquement pour les appareils qui n’affectent pas les utilisateurs. Cette valeur indique la sélection entre « tous les appareils exposés » ou « uniquement les appareils sans impact sur l’utilisateur ».
rbacGroupNames|String|Noms de groupes d’appareils associés
recommendedProgram|String|Programme recommandé pour la mise à niveau vers
recommendedVendor|String|Fournisseur recommandé pour la mise à niveau vers
recommendedVersion|Chaîne|Version recommandée pour la mise à jour/mise à niveau vers
relatedComponent|Chaîne|Composant connexe de cette activité de correction (similaire au composant associé pour une recommandation de sécurité)
requesterEmail|Chaîne|Adresse de messagerie du créateur
requesterId|String|ID d’objet Creator
requesterNotes|Chaîne|Notes (texte libre) ajoutées par le créateur pour cette activité de correction
Scid|String|SCID de la recommandation de sécurité associée
État|Chaîne|État de l’activité de correction (actif/terminé)
statusLastModifiedOn|Date/heure|Date de mise à jour du champ d’état
targetDevices|Entier long|Nombre d’appareils exposés à appliquer à cette correction
Titre|Chaîne|Titre de cette activité de correction
Type|String|Type de correction
vendorId|Chaîne|Nom du fournisseur associé

## <a name="see-also"></a>Voir aussi

- [Obtenir une activité de correction par son ID](get-remediation-one-activity.md)

- [Répertorier toutes les activités de correction](get-remediation-all-activities.md)

- [Répertorier les appareils exposés d’une activité de correction](get-remediation-exposed-devices-activities.md)

- [Menaces basées sur les risques & gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)

- [Vulnérabilités de votre organisation](tvm-weaknesses.md)
