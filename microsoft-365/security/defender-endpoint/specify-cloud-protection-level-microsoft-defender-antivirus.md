---
title: Spécifier le niveau de protection cloud pour les Antivirus Microsoft Defender
description: Définissez votre niveau de protection cloud pour les Antivirus Microsoft Defender.
keywords: Antivirus Microsoft Defender logiciel anti-programme malveillant, sécurité, defender, cloud, aggressiveness, niveau de protection
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.date: 10/26/2020
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.openlocfilehash: f441b1bd444cd70fb5b00dfcb5ebcddadf62b220
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52274903"
---
# <a name="specify-the-cloud-delivered-protection-level"></a>Spécifier le niveau de protection pour le cloud

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez spécifier votre niveau de protection offerte par le cloud Antivirus Microsoft Defender à l’aide de Microsoft Endpoint Manager (recommandé) ou d’une stratégie de groupe.

> [!TIP]
> La protection cloud n’est pas simplement une protection pour les fichiers stockés dans le cloud. Le service Antivirus Microsoft Defender cloud est un mécanisme permettant de fournir une protection mise à jour à votre réseau et à vos appareils (également appelés points de terminaison). La protection cloud avec Antivirus Microsoft Defender utilise des ressources distribuées et l’apprentissage automatique pour fournir une protection à vos points de terminaison à un taux beaucoup plus rapide que les mises à jour d’intelligence de sécurité traditionnelles. Microsoft Intune et Microsoft Endpoint Manager font désormais partie de [Microsoft Endpoint Manager](/mem/endpoint-manager-overview). 


## <a name="use-microsoft-endpoint-manager-to-specify-the-level-of-cloud-delivered-protection"></a>Utiliser Microsoft Endpoint Manager pour spécifier le niveau de protection cloud

1. Go to the Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ) and sign in.

2. Choisissez **l’Antivirus de sécurité des points de**  >  **terminaison.**

3. Sélectionnez un profil antivirus. (Si vous n’en avez pas encore, ou si vous souhaitez créer un profil, voir Configurer les [paramètres](/intune/device-restrictions-configure)de restriction d’appareil dans Microsoft Intune .

4. Sélectionnez **les propriétés.** Ensuite, en de côté **des paramètres de configuration,** choisissez **Modifier.**

5. Développez **la protection** cloud, puis dans la liste des niveaux de **protection** cloud, sélectionnez l’une des listes suivantes :

    1. **Élevé**: applique un niveau de détection élevé.
    2. **Plus élevé**: utilise le **niveau élevé** et applique des mesures de protection supplémentaires (peut avoir un impact sur les performances du client).
    3. **Tolérance zéro :** bloque tous les exécutables inconnus.

6. Choose **Review + save,** and then choose **Save**. 

> [!TIP]
> Vous avez besoin d’aide ? Consultez les ressources suivantes :
> - [Configurer Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure)
> - [Ajouter des paramètres de protection des points de terminaison dans Intune](/mem/intune/protect/endpoint-protection-configure)
  

## <a name="use-group-policy-to-specify-the-level-of-cloud-delivered-protection"></a>Utiliser une stratégie de groupe pour spécifier le niveau de protection cloud

1.  Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console de gestion des stratégies de groupe.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))

2. Cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

3.  Dans **l’Éditeur de gestion des stratégies de** groupe, allez aux   >  **modèles d’administration de configuration ordinateur.**

4.  Développez l’arborescence **Windows composants**  >  **Antivirus Microsoft Defender**  >  **MpEngine**.

5.  Double-cliquez sur le paramètre Sélectionner le **niveau de protection cloud** et définissez-le sur **Activé.** Sélectionnez le niveau de protection :
    - **Le niveau de blocage par défaut** offre une détection forte sans augmenter le risque de détection de fichiers légitimes.
    - **Un niveau de blocage modéré** fournit un niveau modéré uniquement pour les détections à niveau de confiance élevé
    - **Un niveau de blocage élevé** applique un niveau élevé de détection tout en optimisant les performances du client (mais peut également vous donner plus de chances de faux positifs).
    - **Un niveau élevé + de blocage applique** des mesures de protection supplémentaires (peut avoir un impact sur les performances du client et augmenter votre risque de faux positifs).
    - **Le niveau de blocage de tolérance zéro** bloque tous les exécutables inconnus.
    
    > [!WARNING]
    > Bien qu’il soit peu probable, la définition de ce commutateur sur **Élevé** ou Élevé **+** peut entraîner la détection de certains fichiers légitimes (bien que vous aurez la possibilité de débloquer ou de disputer cette détection).

6. Cliquez sur **OK**.

7. Déployez votre objet de stratégie de groupe mis à jour. Voir [La Console de gestion des stratégies de groupe](/windows/win32/srvnodes/group-policy)

> [!TIP]
> Utilisez-vous des objets de stratégie de groupe en local ? Découvrez comment ils traduisent dans le cloud. [Analysez vos objets de stratégie](/mem/intune/configuration/group-policy-analytics)de groupe en local à l’aide de l’analyse de stratégie de groupe dans Microsoft Endpoint Manager - Aperçu . 
  
## <a name="related-articles"></a>Articles connexes

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Comment créer et déployer des stratégies de logiciel anti-programme malveillant : service de protection cloud](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)