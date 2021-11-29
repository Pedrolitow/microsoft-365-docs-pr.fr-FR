---
title: Gérer des indicateurs
ms.reviewer: ''
description: Gérer les indicateurs pour un hachage de fichier, une adresse IP, des URL ou des domaines qui définissent la détection, la prévention et l’exclusion des entités.
keywords: import, indicator, list, ioc, csv, manage, allowed, blocked, block, clean, malicious, file hash, ip address, urls, domain
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: fbed4f51fcd0b2154c46a88dc3d408330238ec63
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2021
ms.locfileid: "61217649"
---
# <a name="manage-indicators"></a>Gérer des indicateurs

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

1. Dans le volet de navigation, sélectionnez **Paramètres** \> **indicateurs de points** de \> **terminaison** (sous **Règles).**

2. Sélectionnez l’onglet du type d’entité que vous souhaitez gérer.

3. Mettez à jour les détails de  l’indicateur et cliquez sur Enregistrer ou cliquer sur le bouton Supprimer si vous souhaitez supprimer l’entité de la liste. 

## <a name="import-a-list-of-iocs"></a>Importer une liste d’IoCs

Vous pouvez également choisir de télécharger un fichier CSV qui définit les attributs des indicateurs, l’action à prendre et d’autres détails.

Téléchargez l’exemple CSV pour connaître les attributs de colonne pris en charge.

1. Dans le volet de navigation, sélectionnez **Paramètres** \> **indicateurs de points** de \> **terminaison** (sous **Règles).**

2. Sélectionnez l’onglet du type d’entité pour qui vous souhaitez importer des indicateurs.

3. Sélectionnez **Importer** \> **un fichier .**

4. Sélectionnez **Importer**. Faites-le pour tous les fichiers que vous souhaitez importer.

5. Sélectionnez **Terminé**.

> [!NOTE]
> Seuls 500 indicateurs peuvent être téléchargés pour chaque lot.

Le tableau suivant indique les paramètres pris en charge.

Paramètre|Type|Description
:---|:---|:---
indicatorType|Énum|Type de l’indicateur. Les valeurs possibles sont les suivantes : « FileSha1 », « FileSha256 », « IpAddress », « DomainName » et « Url ». **Obligatoire**
indicatorValue|String|Identité de [l’entité Indicateur.](ti-indicator.md) **Obligatoire**
action|Énum|Action qui sera entreprise si l’indicateur est détecté dans l’organisation. Les valeurs possibles sont : « Alert », « AlertAndBlock » et « Allowed ». **Obligatoire**
title|String|Titre de l’alerte de l’indicateur. **Obligatoire**
description|String| Description de l’indicateur. **Obligatoire**
expirationTime|DateTimeOffset|Heure d’expiration de l’indicateur au format suivant AAA-MM-JDTHH:MM:SS.0Z. **Optional**
Sévérité |Énum|Gravité de l’indicateur. Les valeurs possibles sont : « Informational », « Low », « Medium » et « High ». **Optional**
recommendedActions|String|Actions recommandées pour l’alerte d’indicateur TI. **Optional**
rbacGroupNames|String|Liste séparée par des virgules des noms de groupe RBAC à appliquer à l’indicateur. **Optional**
category|String|Catégorie de l’alerte. Exemples : exécution et accès aux informations d’identification. **Optional**
mitretechniques|String|MITRE techniques code/id (séparés par des virgules). Pour plus d’informations, [voir Enterprise tactiques.](https://attack.mitre.org/tactics/enterprise/) **Facultatif** Il est recommandé d’ajouter une valeur dans la catégorie lorsqu’une technique MITRE.
GenerateAlert|String|Si l’alerte doit être générée ou non. Les valeurs possibles sont : True ou False. **Optional**



> [!NOTE]
> La notation CIDR (Classless Inter-Domain Routing) pour les adresses IP n’est pas prise en charge.
Pour plus d’informations, consultez Microsoft Defender pour les catégories d’alerte de point de terminaison sont désormais alignées avec [MITRE ATT&CK!](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-atp-alert-categories-are-now-aligned-with/ba-p/732748).

## <a name="see-also"></a>Voir aussi

- [Créer des indicateurs](manage-indicators.md)
- [Créer des indicateurs pour les fichiers](indicator-file.md)
- [Créer des indicateurs pour les IP et URL/domaines](indicator-ip-domain.md)
- [Créer des indicateurs basés sur des certificats](indicator-certificates.md)
