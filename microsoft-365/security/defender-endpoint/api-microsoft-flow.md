---
title: Comment utiliser le connecteur Power Automate pour configurer un flux pour les événements
ms.reviewer: ''
description: Utilisez Microsoft Defender pour point de terminaison connecteur Flow pour créer un flux qui sera déclenché chaque fois qu’un nouvel événement se produit sur votre locataire.
keywords: flux, api prises en charge, api, flux Microsoft, requête, automatisation, automatisation de l’alimentation
ms.service: microsoft-365-security
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
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 0b90fd4ecade2f79cac895c61a4a7327de8aaf66
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67701959"
---
# <a name="how-to-use-power-automate-connector-to-set-up-a-flow-for-events"></a>Comment utiliser le connecteur Power Automate pour configurer un flux pour les événements

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

L’automatisation des procédures de sécurité est une exigence standard pour chaque centre d’opérations de sécurité (SOC) moderne. Pour que les équipes SOC fonctionnent de la manière la plus efficace, l’automatisation est indispensable. Utilisez Microsoft Power Automate pour vous aider à créer des workflows automatisés et à créer une automatisation de procédure de bout en bout en quelques minutes. Microsoft Power Automate prend en charge différents connecteurs qui ont été créés exactement pour cela.  

Utilisez cet article pour vous guider dans la création d’automatisations déclenchées par un événement, par exemple lorsqu’une nouvelle alerte est créée dans votre locataire. L’API Microsoft Defender dispose d’un connecteur Power Automate officiel avec de nombreuses fonctionnalités. 

:::image type="content" source="images/api-flow-0.png" alt-text="Page Actions dans le portail Microsoft Defender 365" lightbox="images/api-flow-0.png" :::

> [!NOTE]
> Pour plus d’informations sur les prérequis en matière de licence des connecteurs Premium, consultez [Licences pour les connecteurs Premium](/power-automate/triggers-introduction#licensing-for-premium-connectors).

## <a name="usage-example"></a>Exemple d'utilisation

L’exemple suivant montre comment créer un flux déclenché chaque fois qu’une nouvelle alerte se produit sur votre locataire. Vous serez guidé sur la définition de l’événement qui démarre le flux et de l’action suivante à effectuer lorsque ce déclencheur se produit.  

1. Connectez-vous à [Microsoft Power Automate](https://flow.microsoft.com).

2. Accédez à **Mes flux** \> **New** \> **Automated-from-blank**.

    :::image type="content" source="images/api-flow-1.png" alt-text="Volet Nouveau flux sous l’élément de menu Mes flux dans le portail Microsoft Defender 365" lightbox="images/api-flow-1.png":::

3. Choisissez un nom pour votre flux, recherchez « Déclencheurs Microsoft Defender ATP » comme déclencheur, puis sélectionnez le nouveau déclencheur d’alertes.

    :::image type="content" source="images/api-flow-2.png" alt-text=" Section Choisir le déclencheur de votre flux dans le portail Microsoft Defender 365" lightbox="images/api-flow-2.png" :::

Vous disposez maintenant d’un flux qui est déclenché chaque fois qu’une nouvelle alerte se produit.

:::image type="content" source="images/api-flow-3.png" alt-text="Description d’un déclencheur" lightbox="images/api-flow-3.png":::

Il vous suffit maintenant de choisir vos prochaines étapes.
Par exemple, vous pouvez isoler l’appareil si la gravité de l’alerte est élevée et envoyer un e-mail à ce sujet.
Le déclencheur d’alerte fournit uniquement l’ID d’alerte et l’ID de machine. Vous pouvez utiliser le connecteur pour développer ces entités.

### <a name="get-the-alert-entity-using-the-connector"></a>Obtenir l’entité Alert à l’aide du connecteur

1. Choisissez **Microsoft Defender ATP** pour la nouvelle étape.

2. Choisir **Alertes - Obtenir une API d’alerte unique**.

3. Définissez **l’ID d’alerte** de la dernière étape en tant **qu’entrée**.

    :::image type="content" source="images/api-flow-4.png" alt-text="Volet Alertes"  lightbox="images/api-flow-4.png":::

### <a name="isolate-the-device-if-the-alerts-severity-is-high"></a>Isoler l’appareil si la gravité de l’alerte est élevée

1. Ajouter **une condition** en tant que nouvelle étape.

2. Vérifiez si la gravité de **l’alerte est égale à** Élevé.

   Si oui, ajoutez l’action **Microsoft Defender ATP - Isoler l’ordinateur** avec l’ID d’ordinateur et un commentaire.

    :::image type="content" source="images/api-flow-5.png" alt-text="Volet Actions"  lightbox="images/api-flow-5.png":::

3. Ajoutez une nouvelle étape pour envoyer un e-mail sur l’alerte et l’isolation. Il existe plusieurs connecteurs de messagerie qui sont très faciles à utiliser, tels qu’Outlook ou Gmail.

4. Enregistrez votre flux.

Vous pouvez également créer un flux **planifié** qui exécute des requêtes Advanced Hunting et bien plus encore !

## <a name="related-topic"></a>Rubrique connexe
- [API Microsoft Defender pour point de terminaison](apis-intro.md)
