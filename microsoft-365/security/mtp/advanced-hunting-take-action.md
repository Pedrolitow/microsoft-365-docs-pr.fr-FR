---
title: Prendre des mesures sur les résultats de requête de recherche avancée dans Microsoft 365 Defender
description: Traiter rapidement les menaces et les ressources affectées dans vos résultats de requête de recherche avancée
keywords: recherche avancée, recherche de menace, recherche de cybermenace, protection microsoft contre les menaces, microsoft 365, mtp, m365, recherche, requête, télémétrie, prendre des mesures
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
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
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 9e8ad544cfe17d0d8e5c895e208b42ec56555565
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49932177"
---
# <a name="take-action-on-advanced-hunting-query-results"></a>Prendre des mesures sur les résultats de requête de recherche avancée

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Vous pouvez rapidement contenir des menaces ou [](advanced-hunting-overview.md) traiter les ressources compromises que vous trouvez dans le recherche avancée à l’aide d’options d’action puissantes et complètes. Avec ces options, vous pouvez :

- Prendre différentes mesures sur les appareils
- Fichiers de mise en quarantaine

## <a name="required-permissions"></a>Autorisations requises
Pour être en mesure d’agir par le biais d’une recherche avancée, vous avez besoin d’un rôle dans Microsoft Defender pour le point de terminaison avec des autorisations pour soumettre des actions de correction [sur les appareils.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/user-roles#permission-options) Si vous ne pouvez pas agir, contactez un administrateur général pour obtenir l’autorisation suivante :

*Actions de correction actives > gestion des menaces et des vulnérabilités : gestion des corrections*

## <a name="take-various-actions-on-devices"></a>Prendre différentes mesures sur les appareils
Vous pouvez prendre les mesures suivantes sur les appareils identifiés par la `DeviceId` colonne dans les résultats de la requête :

- Isoler les appareils affectés pour contenir une infection ou empêcher les attaques de se déplacer ultérieurement
- Collecter un package d’enquête pour obtenir plus d’informations d’investigation
- Exécuter une analyse antivirus pour rechercher et supprimer les menaces à l’aide des dernières mises à jour de l’intelligence de la sécurité
- Lancer un examen automatisé pour vérifier et corriger les menaces sur l’appareil et éventuellement sur d’autres appareils concernés
- Restreindre l’exécution de l’application uniquement aux fichiers exécutables signés par Microsoft, ce qui empêche toute activité de menace ultérieure par le biais de programmes malveillants ou d’autres fichiers exécutables non signés

Pour en savoir plus sur la façon dont ces actions de réponse sont effectuées via Microsoft Defender pour le point de terminaison, consultez les actions de [réponse sur les appareils.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts)
   
## <a name="quarantine-files"></a>Fichiers de mise en quarantaine
Vous pouvez déployer l’action *de* mise en quarantaine sur les fichiers afin qu’ils soient automatiquement mis en quarantaine lorsqu’ils sont rencontrés. Lorsque vous sélectionnez cette action, vous pouvez choisir entre les colonnes suivantes pour identifier les fichiers de votre requête qui sont mis en quarantaine :

- `SHA1` — Dans la plupart des tables de recherche avancées, il s’agit du SHA-1 du fichier affecté par l’action enregistrée. Par exemple, si un fichier a été copié, il s’agit du fichier copié.
- `InitiatingProcessSHA1` — Dans la plupart des tables de recherche avancées, il s’agit du fichier responsable de l’initiative de l’action enregistrée. Par exemple, si un processus enfant a été lancé, il s’agit du processus parent. 
- `SHA256` — Il s’agit de l’équivalent SHA-256 du fichier identifié par la `SHA1` colonne.
- `InitiatingProcessSHA256` — Il s’agit de l’équivalent SHA-256 du fichier identifié par la `InitiatingProcessSHA1` colonne.

Pour en savoir plus sur la façon dont les actions de mise en quarantaine sont prises et sur la façon dont les fichiers peuvent être restaurés, consultez les actions de [réponse sur les fichiers.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts)

>[!NOTE]
>Pour localiser des fichiers et les mettre en quarantaine, les résultats de la requête doivent également inclure des valeurs en tant `DeviceId` qu’identificateurs d’appareil.  

## <a name="take-action"></a>Prendre des mesures
Pour prendre l’une des actions décrites, sélectionnez un ou plusieurs enregistrements dans les résultats de votre requête, puis **sélectionnez Actions.** Un Assistant vous guide tout au long du processus de sélection, puis d’envoi de vos actions préférées.

![Image de l’enregistrement sélectionné avec panneau pour l’inspection de l’enregistrement](../../media/mtp-ah/ah-take-actions.png)

## <a name="review-actions-taken"></a>Examiner les actions entreprises
Chaque action est enregistrée individuellement dans le centre de [l’action](mtp-action-center.md) sous **Historique** du centre de security.microsoft.com/action-center/history  >   ).[](https://security.microsoft.com/action-center/history) Go to the action center to check the status of each action.
 
## <a name="related-topics"></a>Rubriques associées
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Travailler avec les résultats de la requête](advanced-hunting-query-results.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Vue d’ensemble du centre de données](mtp-action-center.md)
