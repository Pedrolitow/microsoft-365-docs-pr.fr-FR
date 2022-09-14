---
title: Activer l’accès conditionnel pour mieux protéger les utilisateurs, les appareils et les données
description: Activez l’accès conditionnel pour empêcher l’exécution d’applications si un appareil est considéré comme à risque et qu’une application est considérée comme non conforme.
keywords: accès conditionnel, bloquer les applications, niveau de sécurité, intune,
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: c1791285917beef8dc881eda2852edf91de2738b
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67679208"
---
# <a name="enable-conditional-access-to-better-protect-users-devices-and-data"></a>Activer l’accès conditionnel pour mieux protéger les utilisateurs, les appareils et les données

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-conditionalaccess-abovefoldlink)

L’accès conditionnel est une fonctionnalité qui vous aide à mieux protéger vos utilisateurs et les informations d’entreprise en veillant à ce que seuls les appareils sécurisés aient accès aux applications.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4byD1]

Avec l’accès conditionnel, vous pouvez contrôler l’accès aux informations d’entreprise en fonction du niveau de risque d’un appareil. Cela permet de conserver les utilisateurs approuvés sur les appareils approuvés à l’aide d’applications approuvées.

Vous pouvez définir des conditions de sécurité dans lesquelles les appareils et les applications peuvent s’exécuter et accéder aux informations à partir de votre réseau en appliquant des stratégies pour empêcher l’exécution des applications jusqu’à ce qu’un appareil retourne à un état conforme.

L’implémentation de l’accès conditionnel dans Defender pour point de terminaison est basée sur des stratégies de conformité d’appareil Microsoft Intune (Intune) et des stratégies d’accès conditionnel Azure Active Directory (Azure AD).

La stratégie de conformité est utilisée avec l’accès conditionnel pour autoriser uniquement les appareils qui remplissent une ou plusieurs règles de stratégie de conformité des appareils à accéder aux applications.

## <a name="understand-the-conditional-access-flow"></a>Comprendre le flux d’accès conditionnel

L’accès conditionnel est mis en place afin que, lorsqu’une menace est visible sur un appareil, l’accès au contenu sensible soit bloqué jusqu’à ce que la menace soit corrigée.

Le flux commence par le fait que les appareils présentent un risque faible, moyen ou élevé. Ces déterminations de risque sont ensuite envoyées à Intune.

Selon la façon dont vous configurez des stratégies dans Intune, l’accès conditionnel peut être configuré de sorte que lorsque certaines conditions sont remplies, la stratégie est appliquée.

Par exemple, vous pouvez configurer Intune pour appliquer l’accès conditionnel sur les appareils qui présentent un risque élevé.

Dans Intune, une stratégie de conformité des appareils est utilisée conjointement avec l’accès conditionnel Azure AD pour bloquer l’accès aux applications. En parallèle, un processus d’investigation et de correction automatisé est lancé.

 Un utilisateur peut toujours utiliser l’appareil pendant l’examen et la correction automatisés, mais l’accès aux données d’entreprise est bloqué jusqu’à ce que la menace soit complètement corrigée.

Pour résoudre le risque détecté sur un appareil, vous devez retourner l’appareil à un état conforme. Un appareil revient à un état conforme lorsqu’il n’y a aucun risque.

Il existe trois façons de traiter un risque :

1. Utilisez la correction manuelle ou automatisée.
2. Résolvez les alertes actives sur l’appareil. Cela supprime le risque de l’appareil.
3. Vous pouvez supprimer l’appareil des stratégies actives et, par conséquent, l’accès conditionnel ne sera pas appliqué sur l’appareil.

La correction manuelle nécessite qu’un administrateur d’étendues examine une alerte et réponde aux risques rencontrés sur l’appareil. La correction automatisée est configurée via les paramètres de configuration fournis dans la section suivante, [Configurer l’accès conditionnel](configure-conditional-access.md).

Lorsque le risque est supprimé via une correction manuelle ou automatisée, l’appareil revient à un état conforme et l’accès aux applications est accordé.

L’exemple suivant d’événements explique l’accès conditionnel en action :

1. Un utilisateur ouvre un fichier malveillant et Defender pour point de terminaison signale que l’appareil présente un risque élevé.
2. L’évaluation à haut risque est transmise à Intune. En parallèle, une enquête automatisée est lancée pour corriger la menace identifiée. Une correction manuelle peut également être effectuée pour corriger la menace identifiée.
3. En fonction de la stratégie créée dans Intune, l’appareil est marqué comme non conforme. L’évaluation est ensuite communiquée à Azure AD par la Intune stratégie d’accès conditionnel. Dans Azure AD, la stratégie correspondante est appliquée pour bloquer l’accès aux applications.
4. L’examen et la correction manuels ou automatisés sont terminés et la menace est supprimée. Defender pour point de terminaison voit qu’il n’y a aucun risque sur l’appareil et Intune évalue que l’appareil est dans un état conforme. Azure AD applique la stratégie qui autorise l’accès aux applications.
5. Les utilisateurs peuvent désormais accéder aux applications.

## <a name="related-topic"></a>Rubrique connexe

- [Configurer l’accès conditionnel dans Microsoft Defender pour point de terminaison](configure-conditional-access.md)
