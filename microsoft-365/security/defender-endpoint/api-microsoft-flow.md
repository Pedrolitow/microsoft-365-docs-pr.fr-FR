---
title: Connecteur d’Flow Microsoft Defender for Endpoint
ms.reviewer: ''
description: Utilisez Microsoft Defender pour endpoint Flow connecteur pour automatiser la sécurité et créer un flux qui sera déclenché chaque fois qu’une nouvelle alerte se produit sur votre client.
keywords: flux, api pris en charge, api, flux Microsoft, requête, automatisation
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 1f61fa2e2d5231d6e9c6a879a0827144282f1285
ms.sourcegitcommit: 6c342a956b2dbc32be33bac1a23a5038490f1b40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58533254"
---
# <a name="microsoft-power-automate-formerly-microsoft-flow-and-azure-functions"></a>Microsoft Power Automate (anciennement Microsoft Flow) et Azure Functions

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


- Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

L’automatisation des procédures de sécurité est une exigence standard pour chaque centre d’opérations de sécurité moderne. L’absence de cyber-défenseurs professionnels force SOC à fonctionner de la manière la plus efficace et l’automatisation est une chose à faire. Microsoft Power Automate prend en charge différents connecteurs qui ont été créés exactement pour cela. Vous pouvez créer une automatisation de procédure de bout en bout en quelques minutes.

L’API Microsoft Defender dispose d’un connecteur Power Automate officiel avec de nombreuses fonctionnalités.

![Image de modification des informations d’identification1](images/api-flow-0.png)

> [!NOTE]
> Pour plus d’informations sur les conditions préalables de licence des connecteurs premium, voir [Licensing for premium connectors](/power-automate/triggers-introduction#licensing-for-premium-connectors).


## <a name="usage-example"></a>Exemple d'utilisation

L’exemple suivant montre comment créer une Flow qui est déclenchée chaque fois qu’une nouvelle alerte se produit sur votre client.

1. Connectez-vous [à Microsoft Power Automate](https://flow.microsoft.com).

2. Go to **My flows** \> **New** \> **Automated-from blank**.

    ![Image de modification des informations d’identification2](images/api-flow-1.png)

3. Choisissez un nom pour votre Flow, recherchez « Déclencheurs Microsoft Defender ATP » comme déclencheur, puis sélectionnez le nouveau déclencheur Alertes.

    ![Image de modification des informations d’identification3](images/api-flow-2.png)

Vous avez maintenant une Flow qui est déclenchée chaque fois qu’une nouvelle alerte se produit.

![Image de modification des informations d’identification4](images/api-flow-3.png)

Il vous suffit maintenant de choisir les étapes suivantes.
Par exemple, vous pouvez isoler l’appareil si la gravité de l’alerte est élevée et envoyer un e-mail à son sujet.
Le déclencheur d’alerte fournit uniquement l’ID d’alerte et l’ID de l’ordinateur. Vous pouvez utiliser le connecteur pour développer ces entités.

### <a name="get-the-alert-entity-using-the-connector"></a>Obtenir l’entité Alerte à l’aide du connecteur

1. Choisissez **Microsoft Defender ATP** pour la nouvelle étape.

2. Choose **Alerts - Get single alert API**.

3. Définissez **l’ID d’alerte** de la dernière étape en tant **qu’entrée.**

    ![Image de modification des informations d’identification5](images/api-flow-4.png)

### <a name="isolate-the-device-if-the-alerts-severity-is-high"></a>Isoler l’appareil si la gravité de l’alerte est élevée

1. Ajoutez **condition** en tant que nouvelle étape.

2. Vérifiez si la gravité de **l’alerte est égale à** Élevée.

   Si oui, ajoutez **l’action Microsoft Defender ATP - Isoler l’ordinateur** avec l’ID de l’ordinateur et un commentaire.

    ![Image de modification des informations d’identification6](images/api-flow-5.png)

3. Ajoutez une nouvelle étape pour l’envoi par courrier électronique de l’alerte et de l’isolation. Il existe plusieurs connecteurs de messagerie très faciles à utiliser, tels que Outlook ou Gmail.

4. Enregistrez votre flux.

Vous pouvez également créer un **flux programmé** qui exécute des requêtes de recherche avancée, et bien plus encore !

## <a name="related-topic"></a>Rubrique connexe
- [API Microsoft Defender pour point de terminaison](apis-intro.md)
