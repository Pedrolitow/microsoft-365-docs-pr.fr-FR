---
title: Prendre des mesures sur les résultats de la requête de chasse avancée dans Microsoft 365 Defender
description: Résoudre rapidement les menaces et les ressources affectées dans vos résultats de requête de repérage avancés
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, prendre des mesures
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier1
ms.topic: conceptual
ms.openlocfilehash: 50695e5fbbcda4dfdee1c5debd921c019be1e003
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68625300"
---
# <a name="take-action-on-advanced-hunting-query-results"></a>Prendre des mesures sur les résultats de la requête de chasse avancée

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Vous pouvez rapidement contenir des menaces ou traiter les ressources compromises que vous trouvez dans la [chasse avancée](advanced-hunting-overview.md) à l’aide d’options d’action puissantes et complètes. Avec ces options, vous pouvez :

- Effectuer différentes actions sur les appareils
- Fichiers de quarantaine

## <a name="required-permissions"></a>Autorisations requises
Pour prendre des mesures sur les appareils par le biais de la chasse avancée, vous avez besoin d’un rôle dans Microsoft Defender pour point de terminaison avec [les autorisations nécessaires pour envoyer des actions de correction sur les appareils](/windows/security/threat-protection/microsoft-defender-atp/user-roles#permission-options). Si vous ne pouvez pas prendre d’action, contactez un administrateur général pour obtenir l’autorisation suivante :

*Actions de correction actives > gestion des menaces et des vulnérabilités - Gestion des corrections*

Pour prendre des mesures sur les e-mails par le biais d’une chasse avancée, vous avez besoin d’un rôle dans Microsoft Defender pour Office 365 pour [rechercher et vider les e-mails](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center).

## <a name="take-various-actions-on-devices"></a>Effectuer différentes actions sur les appareils
Vous pouvez effectuer les actions suivantes sur les appareils identifiés par la `DeviceId` colonne dans les résultats de votre requête :

- Isoler les appareils affectés pour contenir une infection ou empêcher les attaques de se déplacer latéralement
- Collecter un package d’enquête pour obtenir plus d’informations d’investigation
- Exécuter une analyse antivirus pour rechercher et supprimer les menaces à l’aide des dernières mises à jour du renseignement de sécurité
- Lancer une enquête automatisée pour vérifier et corriger les menaces sur l’appareil et éventuellement sur d’autres appareils affectés
- Restreindre l’exécution de l’application aux seuls fichiers exécutables signés par Microsoft, ce qui empêche toute activité de menace ultérieure par le biais de programmes malveillants ou d’autres exécutables non approuvés

Pour en savoir plus sur la façon dont ces actions de réponse sont effectuées via Microsoft Defender pour point de terminaison, [consultez les actions de réponse sur les appareils](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts).
   
### <a name="quarantine-files"></a>Fichiers de quarantaine
Vous pouvez déployer l’action de *mise en quarantaine* sur les fichiers afin qu’ils soient automatiquement mis en quarantaine lorsqu’ils sont rencontrés. Lorsque vous sélectionnez cette action, vous pouvez choisir entre les colonnes suivantes pour identifier les fichiers de vos résultats de requête à mettre en quarantaine :

- `SHA1`: Dans la plupart des tables de chasse avancées, cette colonne fait référence au SHA-1 du fichier affecté par l’action enregistrée. Par exemple, si un fichier a été copié, il s’agit du fichier copié.
- `InitiatingProcessSHA1`: Dans la plupart des tables de chasse avancées, cette colonne fait référence au fichier responsable du lancement de l’action enregistrée. Par exemple, si un processus enfant était lancé, ce fichier initiateur ferait partie du processus parent. 
- `SHA256`: cette colonne est l’équivalent SHA-256 du fichier identifié par la `SHA1` colonne.
- `InitiatingProcessSHA256`: cette colonne est l’équivalent SHA-256 du fichier identifié par la `InitiatingProcessSHA1` colonne.

Pour en savoir plus sur la façon dont les actions de quarantaine sont effectuées et sur la façon dont les fichiers peuvent être restaurés, [consultez les actions de réponse sur les fichiers](/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts).

>[!NOTE]
>Pour localiser les fichiers et les mettre en quarantaine, les résultats de la requête doivent également inclure `DeviceId` des valeurs en tant qu’identificateurs d’appareil.  

Pour effectuer l’une des actions décrites, sélectionnez un ou plusieurs enregistrements dans les résultats de votre requête, puis **sélectionnez Effectuer des actions**. Un Assistant vous guide tout au long du processus de sélection, puis d’envoi de vos actions préférées.

:::image type="content" source="../../media/take-action-multiple.png" alt-text="Option Effectuer des actions dans le portail Microsoft 365 Defender" lightbox="../../media/take-action-multiple.png":::


## <a name="take-various-actions-on-emails"></a>Effectuer différentes actions sur les e-mails
Outre les étapes de correction axées sur l’appareil, vous pouvez également effectuer certaines actions sur les e-mails provenant des résultats de votre requête. Sélectionnez les enregistrements sur lesquels vous souhaitez effectuer une action, **sélectionnez Effectuer des actions**, puis, sous **Choisir des actions, sélectionnez** votre choix parmi les éléments suivants :
- `Move to mailbox folder` - Sélectionnez cette option pour déplacer les messages électroniques vers le dossier Courrier indésirable, Boîte de réception ou Éléments supprimés

   :::image type="content" source="../../media/advanced-hunting-take-actions-email.png" alt-text="L’option Effectuer des actions dans le portail Microsoft 365 Defender" lightbox="../../media/advanced-hunting-take-actions-email.png":::

- `Delete email` - Sélectionnez cette option pour déplacer les messages électroniques vers le dossier Éléments supprimés (**suppression réversible**) ou les supprimer définitivement (**Suppression** définitive)

   :::image type="content" source="../../media/advanced-hunting-take-actions-email-del.png" alt-text="Option Prendre des mesures dans le portail Microsoft 365 Defender" lightbox="../../media/advanced-hunting-take-actions-email-del.png":::

Vous pouvez également fournir un nom de correction et une brève description de l’action prise pour le suivre facilement dans l’historique du centre d’actions. Vous pouvez également utiliser l’ID d’approbation pour filtrer ces actions dans le centre d’actions. Cet ID est fourni à la fin de l’Assistant :

:::image type="content" source="../../media/choose-email-actions-entities.png" alt-text="Assistant Effectuer des actions montrant les actions de sélection pour les entités" lightbox="../../media/choose-email-actions-entities.png":::

Ces actions de messagerie s’appliquent également aux [détections personnalisées](custom-detections-overview.md) .


## <a name="review-actions-taken"></a>Passer en revue les actions effectuées
Chaque action est enregistrée individuellement dans le [centre d’action](m365d-action-center.md) sous **Historique** du **centre** >  d’actions ([security.microsoft.com/action-center/history](https://security.microsoft.com/action-center/history)). Accédez au centre d’actions pour vérifier l’état de chaque action.
 
>[!NOTE]
>Certaines tables de cet article peuvent ne pas être disponibles dans Microsoft Defender pour point de terminaison. [Activez Microsoft 365 Defender](m365d-enable.md) pour rechercher des menaces à l’aide de sources de données supplémentaires. Vous pouvez déplacer vos flux de travail de chasse avancés de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender en suivant les étapes de migration [des requêtes de chasse avancées à partir de Microsoft Defender pour point de terminaison](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser les résultats d’une requête](advanced-hunting-query-results.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Vue d’ensemble du Centre d’actions](m365d-action-center.md)
