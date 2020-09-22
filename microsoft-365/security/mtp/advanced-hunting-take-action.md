---
title: Effectuer des actions sur les résultats de la recherche avancée dans Microsoft Threat Protection
description: Résoudre rapidement les menaces et les ressources affectées dans vos résultats de recherche avancée de la chasse
keywords: chasse aux menaces, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, effectuer une action
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 14785e032d6e4a7a0868308f4029df623456af2a
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48197892"
---
# <a name="take-action-on-advanced-hunting-query-results"></a>Effectuer des actions sur les résultats de la recherche avancée de la chasse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Vous pouvez rapidement contenir des menaces ou des ressources d’adresses compromises que vous trouvez dans la recherche [avancée](advanced-hunting-overview.md) à l’aide d’actions puissantes et complètes. Avec ces options, vous pouvez :

- Effectuer différentes actions sur les appareils
- Mettre en quarantaine les fichiers

## <a name="required-permissions"></a>Autorisations requises
Pour pouvoir prendre des mesures par le biais de la chasse avancée, vous avez besoin d’un rôle dans Microsoft Defender ATP avec des [autorisations pour soumettre des actions de correction sur les appareils](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/user-roles#permission-options). Si vous ne pouvez pas agir, contactez un administrateur général pour obtenir l’autorisation suivante :

*Actions de correction actives > gestion des menaces et des vulnérabilités-gestion des corrections*

## <a name="take-various-actions-on-devices"></a>Effectuer différentes actions sur les appareils
Vous pouvez effectuer les actions suivantes sur les appareils identifiés par la `DeviceId` colonne dans les résultats de la requête :

- Isoler les appareils affectés pour contenir une infection ou empêcher les attaques de se déplacer plus tard
- Collecter les packages d’enquête pour obtenir des informations plus légales
- Exécuter une analyse antivirus pour rechercher et supprimer les menaces à l’aide des dernières mises à jour de l’intelligence de sécurité
- Lancer une enquête automatisée pour vérifier et corriger les menaces sur l’appareil et éventuellement sur d’autres appareils affectés
- Limiter l’exécution de l’application aux seuls fichiers exécutables signés par Microsoft, ce qui empêche les activités de menace ultérieures par des programmes malveillants ou d’autres fichiers exécutables non approuvés

Pour plus d’informations sur l’exécution de ces actions de réponse via Microsoft Defender ATP, lisez la rubrique [about Response actions on Devices](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts).
   
## <a name="quarantine-files"></a>Mettre en quarantaine les fichiers
Vous pouvez déployer l’action de *mise en quarantaine* sur les fichiers afin qu’ils soient automatiquement mis en quarantaine lorsqu’ils sont détectés. Lors de la sélection de cette action, vous pouvez choisir entre les colonnes suivantes pour identifier les fichiers de la requête à mettre en quarantaine :

- `SHA1` — Dans la plupart des tableaux de la chasse avancée, il s’agit du SHA-1 du fichier qui a été affecté par l’action enregistrée. Par exemple, si un fichier a été copié, il s’agit du fichier copié.
- `InitiatingProcessSHA1` — Dans la plupart des tableaux de la chasse avancée, il s’agit du fichier responsable de l’initialisation de l’action enregistrée. Par exemple, si un processus enfant a été lancé, il s’agit du processus parent. 
- `SHA256` — Il s’agit de l’équivalent SHA-256 du fichier identifié par la `SHA1` colonne.
- `InitiatingProcessSHA256` — Il s’agit de l’équivalent SHA-256 du fichier identifié par la `InitiatingProcessSHA1` colonne.

Pour en savoir plus sur la façon dont les actions de mise en quarantaine sont effectuées et sur la manière dont les fichiers peuvent être restaurés, consultez la rubrique [actions Response sur les fichiers](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts).

>[!NOTE]
>Pour localiser des fichiers et les mettre en quarantaine, les résultats de la requête doivent également inclure des `DeviceId` valeurs en tant qu’identificateurs d’appareil.  

## <a name="take-action"></a>Effectuer une action
Pour effectuer l’une des actions décrites, sélectionnez un ou plusieurs enregistrements dans les résultats de votre requête, puis sélectionnez **prendre les actions**. Un Assistant vous guide tout au long du processus de sélection et d’envoi de vos actions favorites.

![Image de l’enregistrement sélectionné avec le panneau pour inspecter l’enregistrement](../../media/mtp-ah/ah-take-actions.png)

## <a name="review-actions-taken"></a>Examiner les actions effectuées
Chaque action est enregistrée individuellement dans le [Centre de notifications](mtp-action-center.md) sous historique du **Centre de notifications**  >  **History** ([Security.Microsoft.com/Action-Center/History](https://security.microsoft.com/action-center/history)). Accédez au centre de notifications pour vérifier l’état de chaque action.
 
## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Travailler avec les résultats de la requête](advanced-hunting-query-results.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Vue d’ensemble du centre de notifications](mtp-action-center.md)
