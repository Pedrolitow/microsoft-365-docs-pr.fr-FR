---
title: Spécifier le niveau de protection cloud pour Antivirus Microsoft Defender
description: Définissez votre niveau de protection cloud pour Antivirus Microsoft Defender.
keywords: Antivirus Microsoft Defender logiciel anti-programme malveillant, sécurité, defender, cloud, aggressiveness, niveau de protection
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: normal
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.date: 08/26/2021
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.openlocfilehash: 8adb0be672c20b8e51c4178df63d7b25332455ce
ms.sourcegitcommit: f88a0ec621e7d9bc5f376eeaf70c8a9800711f88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2021
ms.locfileid: "59356467"
---
# <a name="specify-the-cloud-protection-level"></a>Spécifier le niveau de protection cloud

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)
- Antivirus Microsoft Defender

La protection cloud fonctionne avec Antivirus Microsoft Defender pour fournir une protection à vos points de terminaison beaucoup plus rapidement que par le biais de mises à jour d’informations de sécurité traditionnelles. Vous pouvez configurer votre niveau de protection cloud à l’aide de Microsoft Endpoint Manager (recommandé) ou d’une stratégie de groupe.

> [!NOTE]
> La sélection **d’une** tolérance **élevée, élevée +** **ou** zéro peut entraîner la détection de certains fichiers légitimes. Si cela se produit, vous pouvez débloquer le fichier détecté ou en faire la demande dans le portail Microsoft 365 Defender.

## <a name="use-microsoft-endpoint-manager-to-specify-the-level-of-cloud-protection"></a>Utiliser Microsoft Endpoint Manager pour spécifier le niveau de protection cloud

1. Go to the Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ) and sign in.

2. Choisissez **l’Antivirus de sécurité des points de** \> **terminaison.**

3. Sélectionnez un profil antivirus. (Si vous n’en avez pas encore, ou si vous souhaitez créer un profil, voir Configurer les [paramètres](/intune/device-restrictions-configure)de restriction d’appareil dans Microsoft Intune .

4. Sélectionnez **propriétés**. Ensuite, en de côté **des paramètres de configuration,** choisissez **Modifier.**

5. Développez **La protection** cloud, puis dans la liste des niveaux de **protection** cloud, sélectionnez l’une des listes suivantes :

    - **Élevé**: applique un niveau de détection élevé.
    - **Plus élevé**: utilise le **niveau élevé** et applique des mesures de protection supplémentaires (peut affecter les performances du client).
    - **Tolérance zéro :** bloque tous les exécutables inconnus.

6. Choose **Review + save,** and then choose **Save**.

> [!TIP]
> Vous avez besoin d’aide ? Consultez les ressources suivantes :
>
> - [Configurer Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure)
> - [Ajouter des paramètres de protection des points de terminaison dans Intune](/mem/intune/protect/endpoint-protection-configure)

## <a name="use-group-policy-to-specify-the-level-of-cloud-protection"></a>Utiliser une stratégie de groupe pour spécifier le niveau de protection cloud

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console de gestion des stratégies de groupe.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))

2. Cliquez avec le bouton droit sur l’objet de stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier.**

3. Dans **l’Éditeur de gestion des stratégies de** groupe, allez **aux** \> **modèles d’administration de configuration ordinateur.**

4. Développez l’arborescence **Windows composants** \> **Antivirus Microsoft Defender** \> **MpEngine**.

5. Double-cliquez sur le paramètre Sélectionner le **niveau de protection cloud** et définissez-le sur **Activé.** Sélectionnez le niveau de protection :
    - **Le niveau de blocage par défaut** offre une détection forte sans augmenter le risque de détection de fichiers légitimes.
    - **Un niveau de blocage modéré** fournit un niveau modéré uniquement pour les détections à niveau de confiance élevé
    - **Un niveau de blocage élevé** applique un niveau élevé de détection tout en optimisant les performances du client (mais peut également vous donner plus de chances de faux positifs).
    - **Un niveau élevé + de blocage applique** des mesures de protection supplémentaires (peut affecter les performances du client et augmenter votre risque de faux positifs).
    - **Le niveau de blocage de tolérance zéro** bloque tous les exécutables inconnus.

6. Sélectionnez **OK**.

7. Déployez votre objet de stratégie de groupe mis à jour. Voir [La Console de gestion des stratégies de groupe](/windows/win32/srvnodes/group-policy)

> [!TIP]
> Utilisez-vous des objets de stratégie de groupe en local ? Découvrez comment ils traduisent dans le cloud. [Analysez vos objets de stratégie](/mem/intune/configuration/group-policy-analytics)de groupe en local à l’aide de l’analyse de stratégie de groupe dans Microsoft Endpoint Manager - Aperçu . 
  
## <a name="see-also"></a>Voir aussi

[Pourquoi la protection cloud doit-elle être activée pour Antivirus Microsoft Defender](why-cloud-protection-should-be-on-mdav.md)
