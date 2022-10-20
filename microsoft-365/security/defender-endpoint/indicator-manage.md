---
title: Gérer des indicateurs
ms.reviewer: ''
description: Gérer les indicateurs pour un hachage de fichier, une adresse IP, des URL ou des domaines qui définissent la détection, la prévention et l’exclusion des entités.
keywords: import, indicator, list, ioc, csv, manage, allowed, blocked, block, clean, malicious, file hash, ip address, urls, domain
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 938f3d67693cabb15049d5ba73c066fa949853bd
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68636647"
---
# <a name="manage-indicators"></a>Gérer des indicateurs

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

1. Dans le volet de navigation, sélectionnez **Paramètres** \> Points de **terminaison Indicateurs** \> (sous **Règles**).

2. Sélectionnez l’onglet du type d’entité que vous souhaitez gérer.

3. Mettez à jour les détails de l’indicateur, puis cliquez sur **Enregistrer** ou cliquez sur le bouton **Supprimer** si vous souhaitez supprimer l’entité de la liste.

## <a name="import-a-list-of-iocs"></a>Importer une liste d’E/S

Vous pouvez également choisir de charger un fichier CSV qui définit les attributs des indicateurs, l’action à effectuer et d’autres détails.

Téléchargez l’exemple de fichier CSV pour connaître les attributs de colonne pris en charge.

1. Dans le volet de navigation, sélectionnez **Paramètres** \> Points de **terminaison Indicateurs** \> (sous **Règles**).

2. Sélectionnez l’onglet du type d’entité pour lequel vous souhaitez importer des indicateurs.

3. Sélectionnez **Importer** \> **le fichier Choisir**.

4. Sélectionnez **Importer**. Effectuez cette opération pour tous les fichiers que vous souhaitez importer.

5. Sélectionnez **Terminé**.

> [!NOTE]
> Seuls 500 indicateurs peuvent être chargés pour chaque lot.

Le tableau suivant présente les paramètres pris en charge.

Paramètre|Type|Description
:---|:---|:---
indicatorType|Énum|Type de l’indicateur. Les valeurs possibles sont : « FileSha1 », « FileSha256 », « IpAddress », « DomainName » et « Url ». **Obligatoire**
indicatorValue|Chaîne|Identité de l’entité [Indicateur](ti-indicator.md) . **Obligatoire**
action|Énum|Action qui sera effectuée si l’indicateur est détecté dans l’organisation. Les valeurs possibles sont : « Alert », « AlertAndBlock » et « Allowed ». **Obligatoire**
title|Chaîne|Titre de l’alerte d’indicateur. **Obligatoire**
description|Chaîne| Description de l’indicateur. **Obligatoire**
expirationTime|DateTimeOffset|Heure d’expiration de l’indicateur au format suivant AAAA-MM-DDTHH:MM:SS.0Z. L’indicateur est supprimé si le délai d’expiration est écoulé et que tout ce qui se passe au moment de l’expiration se produit à la valeur de secondes (SS). **Optional**
Sévérité |Énum|Gravité de l’indicateur. Les valeurs possibles sont : « Informational », « Low », « Medium » et « High ». **Optional**
recommendedActions|Chaîne|Actions recommandées pour les alertes d’indicateur TI. **Optional**
rbacGroups|Chaîne|Liste séparée par des virgules des groupes RBAC auxquels l’indicateur serait appliqué. **Optional**
category|String|Catégorie de l’alerte. Exemples : l’exécution et l’accès aux informations d’identification. **Optional**
mitretechniques|Chaîne|Code/id des techniques MITRE (séparés par des virgules). Pour plus d’informations, consultez [Tactiques d’entreprise](https://attack.mitre.org/tactics/enterprise/). **Optionnel** Il est recommandé d’ajouter une valeur dans la catégorie lorsqu’une technique MITRE.
GenerateAlert|Chaîne|Indique si l’alerte doit être générée. Les valeurs possibles sont : True ou False. **Optional**

> [!NOTE]
> La notation de routage Inter-Domain sans classe (CIDR) pour les adresses IP n’est pas prise en charge.
Pour plus d’informations, consultez [Microsoft Defender pour point de terminaison catégories d’alertes sont désormais alignées sur MITRE ATT&CK!](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-atp-alert-categories-are-now-aligned-with/ba-p/732748).

Regardez cette vidéo pour découvrir comment Microsoft Defender pour point de terminaison offre plusieurs façons d’ajouter et de gérer des indicateurs de compromission (IOC). 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4qLVw]

## <a name="see-also"></a>Voir aussi

- [Créer des indicateurs](manage-indicators.md)
- [Créer des indicateurs pour les fichiers](indicator-file.md)
- [Créer des indicateurs pour les IP et URL/domaines](indicator-ip-domain.md)
- [Créer des indicateurs basés sur des certificats](indicator-certificates.md)
