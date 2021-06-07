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
ms.openlocfilehash: dd0cc3c2da134750f905b1f80746d6ec65cc70b2
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52769702"
---
# <a name="microsoft-power-automate-formerly-microsoft-flow-and-azure-functions"></a>Microsoft Power Automate (anciennement Microsoft Flow) et Azure Functions

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


- Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

L’automatisation des procédures de sécurité est une exigence standard pour chaque centre des opérations de sécurité moderne. L’absence de cyber-défenseurs professionnels force SOC à fonctionner de la manière la plus efficace et l’automatisation est une chose à faire. Microsoft Power Automate prend en charge différents connecteurs qui ont été créés exactement pour cela. Vous pouvez créer une automatisation de procédure de bout en bout en quelques minutes.

L’API Microsoft Defender dispose d’un connecteur Flow officiel avec de nombreuses fonctionnalités.

![Image de modification des informations d’identification1](images/api-flow-0.png)

> [!NOTE]
> Pour plus d’informations sur les conditions préalables de licence des connecteurs premium, voir [Licensing for premium connectors](https://docs.microsoft.com/power-automate/triggers-introduction#licensing-for-premium-connectors).


## <a name="usage-example"></a>Exemple d'utilisation

L’exemple suivant montre comment créer une Flow qui est déclenchée chaque fois qu’une nouvelle alerte se produit sur votre client.

1. Connectez-vous [à Microsoft Power Automate](https://flow.microsoft.com).

2. Go to **My flows**  >  **New**  >  **Automated-from blank**.

    ![Image de modification des informations d’identification2](images/api-flow-1.png)

3. Choisissez un nom pour votre Flow, recherchez « déclencheurs Microsoft Defender ATP » comme déclencheur, puis sélectionnez le nouveau déclencheur Alertes.

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

   Si oui, ajoutez le Microsoft Defender ATP - Isoler l’action **de l’ordinateur** avec l’ID de l’ordinateur et un commentaire.

    ![Image de modification des informations d’identification6](images/api-flow-5.png)

3. Ajoutez une nouvelle étape pour l’envoi par courrier électronique de l’alerte et de l’isolation. Il existe plusieurs connecteurs de messagerie très faciles à utiliser, tels que Outlook ou Gmail.

4. Enregistrez votre flux.

Vous pouvez également créer un **flux programmé** qui exécute des requêtes de recherche avancée, et bien plus encore !

## <a name="related-topic"></a>Rubrique connexe
- [API Microsoft Defender pour point de terminaison](apis-intro.md)
