---
title: Spécifier le niveau de protection cloud pour Antivirus Microsoft Defender
description: Définissez votre niveau de protection cloud pour Antivirus Microsoft Defender.
keywords: Antivirus Microsoft Defender, logiciel anti-programme malveillant, sécurité, défenseur, cloud, agressivité, niveau de protection
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.date: 08/26/2021
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 6e24be40b4ff9e57d896cf53769b578c482a2c6e
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787531"
---
# <a name="specify-the-cloud-protection-level"></a>Spécifier le niveau de protection cloud

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

La protection cloud fonctionne en collaboration avec Antivirus Microsoft Defender pour fournir une protection à vos points de terminaison beaucoup plus rapidement que par le biais de mises à jour de renseignement de sécurité traditionnelles. Vous pouvez configurer votre niveau de protection cloud à l’aide de Microsoft Endpoint Manager (recommandé) ou stratégie de groupe.

> [!NOTE]
> La sélection d’une tolérance **élevée**, **élevée +** ou **zéro** peut entraîner la détection de certains fichiers légitimes. Si cela se produit, vous pouvez débloquer le fichier détecté ou contester cette détection dans le portail Microsoft 365 Defender.

## <a name="use-microsoft-endpoint-manager-to-specify-the-level-of-cloud-protection"></a>Utiliser Microsoft Endpoint Manager pour spécifier le niveau de protection cloud

1. Accédez au centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous.

2. Choisissez **l’antivirus de sécurité de point de terminaison**\>.

3. Sélectionnez un profil antivirus. (Si vous n’en avez pas encore, ou si vous souhaitez créer un profil, consultez [Configurer les paramètres de restriction d’appareil dans Microsoft Intune](/intune/device-restrictions-configure).

4. Sélectionnez **Propriétés**. Ensuite, en regard **des paramètres de configuration**, choisissez **Modifier**.

5. Développez **la protection cloud**, puis, dans la liste des **niveaux de protection fournis par le cloud** , sélectionnez l’une des options suivantes :

    - **Non configuré** : état par défaut.
    - **Élevé** : applique un niveau de détection fort.
    - **Plus élevé** : utilise le **niveau élevé** et applique des mesures de protection supplémentaires (peuvent affecter les performances du client).
    - **Tolérance zéro** : bloque tous les exécutables inconnus.

6. Choisissez **Vérifier + enregistrer**, puis **Enregistrer**.

> [!TIP]
> Vous avez besoin d’aide ? Consultez les ressources suivantes :
>
> - [Configurer Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure)
> - [Ajouter des paramètres endpoint protection dans Intune](/mem/intune/protect/endpoint-protection-configure)

## <a name="use-group-policy-to-specify-the-level-of-cloud-protection"></a>Utilisez stratégie de groupe pour spécifier le niveau de protection cloud

1. Sur votre ordinateur de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

3. Dans **l’éditeur de gestion stratégie de groupe**, accédez aux **modèles d’administration** **de configuration** \> par ordinateur.

4. Développez l’arborescence pour **Windows Composants** \> **Antivirus Microsoft Defender** \> **MpEngine**.

5. Double-cliquez sur le paramètre **Sélectionner le niveau de protection cloud et définissez-le** sur **Activé**. Sélectionnez le niveau de protection :

    - **Non configuré** : état par défaut.
    - **Le niveau de blocage par défaut** fournit une détection forte sans augmenter le risque de détection de fichiers légitimes.
    - **Le niveau de blocage modéré** fournit un niveau modéré uniquement pour les détections de confiance élevée
    - **Un niveau de blocage élevé** applique un niveau élevé de détection tout en optimisant les performances du client (mais peut également vous donner plus de chances de faux positifs).
    - **Le niveau élevé + bloquant** applique des mesures de protection supplémentaires (peut affecter les performances du client et augmenter votre risque de faux positifs).
    - **Le niveau de blocage de la tolérance zéro** bloque tous les exécutables inconnus.

6. Sélectionnez **OK**.

7. Déployez votre objet stratégie de groupe mis à jour. Voir [stratégie de groupe Console de gestion](/windows/win32/srvnodes/group-policy)

> [!TIP]
> Utilisez-vous des objets stratégie de groupe localement ? Découvrez comment ils se traduisent dans le cloud. [Analysez vos objets de stratégie de groupe locaux à l’aide de l’analytique stratégie de groupe dans Microsoft Endpoint Manager - Préversion](/mem/intune/configuration/group-policy-analytics).

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison sur les fonctionnalités Android](android-configure.md)
> - [Configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)
  
## <a name="see-also"></a>Voir aussi

[Pourquoi la protection cloud doit être activée pour Antivirus Microsoft Defender](why-cloud-protection-should-be-on-mdav.md)
