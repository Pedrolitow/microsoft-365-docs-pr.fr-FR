---
title: Comment utiliser Power Automate Connector pour configurer une Flow pour les événements
ms.reviewer: ''
description: Utilisez Microsoft Defender for Endpoint Flow pour créer un flux qui sera déclenché chaque fois qu’un nouvel événement se produit sur votre client.
keywords: flux, api pris en charge, api, flux Microsoft, requête, automatisation, automatisation de l’alimentation
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
ms.topic: how-to
MS.technology: mde
ms.custom: api
ms.openlocfilehash: fdb3876de6f74c95858dee01aba9615198282b16
ms.sourcegitcommit: bcea69bacd1b48827bd60af2880909593a1609a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2022
ms.locfileid: "62202196"
---
# <a name="how-to-use-power-automate-connector-to-set-up-a-flow-for-events"></a>Comment utiliser Power Automate Connector pour configurer une Flow pour les événements

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


L’automatisation des procédures de sécurité est une exigence standard pour chaque centre d’opérations de sécurité moderne. Pour que les équipes SOC fonctionnent de la manière la plus efficace, l’automatisation est un must. Utilisez Microsoft Power Automate pour vous aider à créer des flux de travail automatisés et à créer une automatisation de procédure de bout en bout en quelques minutes. Microsoft Power Automate prend en charge différents connecteurs qui ont été créés exactement pour cela.  

Utilisez cet article pour vous guider dans la création d’automatisations déclenchées par un événement, par exemple lorsqu’une nouvelle alerte est créée dans votre client. L’API Microsoft Defender dispose d’un connecteur Power Automate officiel avec de nombreuses fonctionnalités. 



:::image type="content" alt-text="Image de modification des informations d’identification1." source="images/api-flow-0.png":::

> [!NOTE]
> Pour plus d’informations sur les conditions préalables de licence des connecteurs premium, voir [Licensing for premium connectors](/power-automate/triggers-introduction#licensing-for-premium-connectors).


## <a name="usage-example"></a>Exemple d'utilisation

L’exemple suivant montre comment créer une Flow qui est déclenchée chaque fois qu’une nouvelle alerte se produit sur votre client. Vous serez guidé sur la définition de l’événement qui démarre le flux et de l’action suivante à prendre lorsque ce déclencheur se produit.  

1. Connectez-vous [à Microsoft Power Automate](https://flow.microsoft.com).

2. Go to **My flows** \> **New** \> **Automated-from blank**.

    :::image type="content" alt-text="Image de modification des informations d’identification2." source="images/api-flow-1.png":::

3. Choisissez un nom pour votre Flow, recherchez « Déclencheurs Microsoft Defender ATP » comme déclencheur, puis sélectionnez le nouveau déclencheur Alertes.

    :::image type="content" alt-text="Image de modification des informations d’identification3." source="images/api-flow-2.png":::

Vous avez maintenant une Flow qui est déclenchée chaque fois qu’une nouvelle alerte se produit.

:::image type="content" alt-text="Image de modification des informations d’identification4." source="images/api-flow-3.png":::

Il vous suffit maintenant de choisir les étapes suivantes.
Par exemple, vous pouvez isoler l’appareil si la gravité de l’alerte est élevée et envoyer un e-mail à son sujet.
Le déclencheur d’alerte fournit uniquement l’ID d’alerte et l’ID de l’ordinateur. Vous pouvez utiliser le connecteur pour développer ces entités.

### <a name="get-the-alert-entity-using-the-connector"></a>Obtenir l’entité Alerte à l’aide du connecteur

1. Choisissez **Microsoft Defender ATP** pour la nouvelle étape.

2. Choose **Alerts - Get single alert API**.

3. Définissez **l’ID d’alerte** de la dernière étape en tant **qu’entrée.**

    :::image type="content" alt-text="Image de modification des informations d’identification5." source="images/api-flow-4.png" lightbox="images/api-flow-4.png":::

### <a name="isolate-the-device-if-the-alerts-severity-is-high"></a>Isoler l’appareil si la gravité de l’alerte est élevée

1. Ajoutez **condition** en tant que nouvelle étape.

2. Vérifiez si la gravité de **l’alerte est égale à** Élevée.

   Si oui, ajoutez **l’action Microsoft Defender ATP - Isoler l’ordinateur** avec l’ID de l’ordinateur et un commentaire.

    :::image type="content" alt-text="Image de modification des informations d’identification6." source="images/api-flow-5.png" lightbox="images/api-flow-5.png":::

3. Ajoutez une nouvelle étape pour l’envoi par courrier électronique de l’alerte et de l’isolation. Il existe plusieurs connecteurs de messagerie très faciles à utiliser, tels que Outlook ou Gmail.

4. Enregistrez votre flux.

Vous pouvez également créer un **flux programmé** qui exécute des requêtes de recherche avancée, et bien plus encore !

## <a name="related-topic"></a>Rubrique connexe
- [API Microsoft Defender pour point de terminaison](apis-intro.md)
