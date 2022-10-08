---
title: Afficher votre tableau de bord Gestion des vulnérabilités Microsoft Defender dans Microsoft Defender pour entreprises
description: Utilisez votre tableau de bord Gestion des vulnérabilités Microsoft Defender pour afficher les éléments importants à traiter dans Defender entreprise.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-security
ms.subservice: mdb
ms.localizationpriority: medium
ms.date: 08/02/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-security
- tier1
ms.custom: intro-get-started
ms.openlocfilehash: d3bfaa93e390a61d7c70e3763929247398a59481
ms.sourcegitcommit: 4dfb5de8c61847b8ddd10410ad20d34860eed8f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68110598"
---
# <a name="use-your-vulnerability-management-dashboard-in-microsoft-defender-for-business"></a>Utiliser votre tableau de bord de gestion des vulnérabilités dans Microsoft Defender pour entreprises

Defender entreprise inclut un tableau de bord de gestion des vulnérabilités conçu pour économiser du temps et des efforts de votre équipe de sécurité. En plus de fournir un score d’exposition, ce tableau de bord vous permet d’afficher des informations sur les appareils exposés et de consulter les recommandations de sécurité pertinentes. Vous pouvez utiliser votre tableau de bord Gestion des vulnérabilités Defender pour :

- Affichez votre score d’exposition, qui est associé aux appareils de votre entreprise.
- Affichez vos principales recommandations de sécurité, telles que la résolution des problèmes de communication avec les appareils, l’activation de la protection pare-feu ou la mise à jour Microsoft Defender définitions antivirus.
- Visualisez les activités de remédiation, comme les fichiers qui ont été envoyés en quarantaine ou les vulnérabilités trouvées sur les appareils.

## <a name="vulnerability-management-features-and-capabilities"></a>Fonctionnalités et fonctionnalités de gestion des vulnérabilités

Les fonctionnalités et fonctionnalités de gestion des vulnérabilités dans Microsoft Defender pour entreprises sont les suivantes :

- **Tableau de bord** : fournit des informations sur les vulnérabilités, l’exposition et les recommandations. Vous pouvez voir les activités de correction récentes, les appareils exposés et les moyens d’améliorer la sécurité globale de votre entreprise. Chaque carte du tableau de bord inclut un lien vers des informations plus détaillées ou vers une page dans laquelle vous pouvez effectuer une action recommandée.

    :::image type="content" source="media/mdb-mdvm-dashboard.png" alt-text="Capture d’écran du tableau de bord Gestion des vulnérabilités Microsoft Defender." lightbox="media/mdb-mdvm-dashboard.png":::

- **Recommandations** : répertorie les recommandations de sécurité actuelles et les informations relatives aux menaces à examiner et à prendre en compte. Lorsque vous sélectionnez un élément dans la liste, un panneau volant s’ouvre avec plus de détails sur les menaces et les actions que vous pouvez effectuer.

- **Correction** : répertorie toutes les actions de correction et leur état. Les activités de correction peuvent inclure l’envoi d’un fichier en quarantaine, l’arrêt de l’exécution d’un processus et le blocage de l’exécution d’une menace détectée. Les activités de correction peuvent également inclure la mise à jour d’un appareil, l’exécution d’une analyse antivirus, etc. 

    :::image type="content" source="media/mdb-mdvm-remediation.png" alt-text="Capture d’écran de Gestion des vulnérabilités Microsoft Defender-Remediation." lightbox="media/mdb-mdvm-remediation.png":::

- Inventaires : répertorie **les logiciels** et les applications actuellement utilisés dans votre organisation. Vous verrez des navigateurs, des systèmes d’exploitation et d’autres logiciels sur les appareils, ainsi que des faiblesses et des menaces identifiées.

- **Faiblesses** : répertorie les vulnérabilités ainsi que le nombre d’appareils exposés dans votre organisation. Si vous voyez « 0 » dans la colonne Appareils exposés, vous n’avez pas à prendre d’action immédiate. Toutefois, vous pouvez en savoir plus sur chaque vulnérabilité répertoriée sur cette page. Sélectionnez un élément pour en savoir plus à ce sujet et ce que vous pouvez faire pour atténuer la menace potentielle pour votre entreprise.

    :::image type="content" source="media/mdb-mdvm-weakness-details.png" alt-text="Capture d’écran de Gestion des vulnérabilités Microsoft Defender-Faiblesses." lightbox="media/mdb-mdvm-weakness-details.png":::

- **Chronologie des événements** : répertorie les vulnérabilités qui affectent votre organisation dans une vue de chronologie.   

[En savoir plus sur Gestion des vulnérabilités Microsoft Defender](../defender-vulnerability-management/defender-vulnerability-management.md).

## <a name="next-steps"></a>Prochaines étapes

- [Essayer des didacticiels et des simulations dans Defender entreprise](mdb-tutorials.md)
- [Transférer les appareils vers Defender pour entreprise](mdb-onboard-devices.md)
- [Afficher ou modifier des stratégies dans Defender entreprise](mdb-view-edit-create-policies.md)
