---
title: Activer l’accès conditionnel pour mieux protéger les utilisateurs, les appareils et les données
description: Activez l’accès conditionnel pour empêcher l’exécution des applications si un appareil est considéré comme à risque et si une application est considérée comme non conforme.
keywords: accès conditionnel, bloquer les applications, niveau de sécurité, intune,
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 93b547718bca2fb157c3b4e0a4b08d383ec92e4f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60196992"
---
# <a name="enable-conditional-access-to-better-protect-users-devices-and-data"></a>Activer l’accès conditionnel pour mieux protéger les utilisateurs, les appareils et les données

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-conditionalaccess-abovefoldlink)

L’accès conditionnel est une fonctionnalité qui vous permet de mieux protéger vos utilisateurs et les informations d’entreprise en vous assurez que seuls les appareils sécurisés ont accès aux applications.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4byD1]

Avec l’accès conditionnel, vous pouvez contrôler l’accès aux informations d’entreprise en fonction du niveau de risque d’un appareil. Cela permet de conserver les utilisateurs de confiance sur des appareils de confiance à l’aide d’applications fiables.

Vous pouvez définir des conditions de sécurité dans lesquelles les appareils et les applications peuvent s’exécuter et accéder aux informations à partir de votre réseau en appliquant des stratégies pour empêcher l’exécution des applications jusqu’à ce qu’un appareil retrouve un état conforme.

L’implémentation de l’accès conditionnel dans Defender pour point de terminaison est basée sur les stratégies de conformité des appareils Microsoft Intune (Intune) et les stratégies d’accès conditionnel Azure Active Directory (Azure AD).

La stratégie de conformité est utilisée avec l’accès conditionnel pour autoriser uniquement les appareils qui respectent une ou plusieurs règles de stratégie de conformité des appareils à accéder aux applications.

## <a name="understand-the-conditional-access-flow"></a>Comprendre le flux d’accès conditionnel

L’accès conditionnel est mis en place de sorte que lorsqu’une menace est vue sur un appareil, l’accès au contenu sensible est bloqué jusqu’à ce que la menace soit corrigé.

Le flux commence par le fait que les appareils sont considérés comme ayant un risque faible, moyen ou élevé. Ces déterminations des risques sont ensuite envoyées à Intune.

En fonction de la configuration des stratégies dans Intune, l’accès conditionnel peut être configuré de sorte que lorsque certaines conditions sont remplies, la stratégie soit appliquée.

Par exemple, vous pouvez configurer Intune pour appliquer l’accès conditionnel sur les appareils à risque élevé.

Dans Intune, une stratégie de conformité des appareils est utilisée conjointement avec l’accès conditionnel Azure AD pour bloquer l’accès aux applications. En parallèle, un processus automatisé d’examen et de correction est lancé.

 Un utilisateur peut toujours utiliser l’appareil pendant l’examen et la correction automatisés, mais l’accès aux données d’entreprise est bloqué jusqu’à ce que la menace soit entièrement corrigé.

Pour résoudre le risque trouvé sur un appareil, vous devez le remettre à l’état conforme. Un appareil revient à un état conforme lorsqu’il n’y a aucun risque.

Il existe trois façons de résoudre un risque :

1. Utilisez la correction manuelle ou automatisée.
2. Résoudre les alertes actives sur l’appareil. Cela permet de supprimer le risque de l’appareil.
3. Vous pouvez supprimer l’appareil des stratégies actives et, par conséquent, l’accès conditionnel ne sera pas appliqué sur l’appareil.

La correction manuelle nécessite qu’un administrateur secops examine une alerte et adresse le risque visible sur l’appareil. La correction automatisée est configurée par le biais des paramètres de configuration fournis dans la section suivante, [Configurer l’accès conditionnel.](configure-conditional-access.md)

Lorsque le risque est supprimé par le biais d’une correction manuelle ou automatisée, l’appareil revient à un état conforme et l’accès aux applications est accordé.

L’exemple de séquence d’événements suivant explique l’accès conditionnel en action :

1. Un utilisateur ouvre un fichier malveillant et Defender for Endpoint signale l’appareil comme étant à risque élevé.
2. L’évaluation à risque élevé est transmise à Intune. En parallèle, une enquête automatisée est lancée pour corriger la menace identifiée. Une correction manuelle peut également être effectuée pour corriger la menace identifiée.
3. En fonction de la stratégie créée dans Intune, l’appareil est marqué comme non conforme. L’évaluation est ensuite communiquée à Azure AD par la stratégie d’accès conditionnel Intune. Dans Azure AD, la stratégie correspondante est appliquée pour bloquer l’accès aux applications.
4. L’examen et la correction manuels ou automatisés sont terminés et la menace est supprimée. Defender pour le point de terminaison constate qu’il n’y a aucun risque sur l’appareil et Intune évalue que l’appareil est dans un état conforme. Azure AD applique la stratégie qui autorise l’accès aux applications.
5. Les utilisateurs peuvent désormais accéder aux applications.

## <a name="related-topic"></a>Rubrique connexe

- [Configurer l’accès conditionnel dans Microsoft Defender pour le point de terminaison](configure-conditional-access.md)
