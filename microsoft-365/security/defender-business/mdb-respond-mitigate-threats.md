---
title: Répondre aux menaces et les atténuer dans Microsoft Defender pour entreprises
description: Comme des menaces sont détectées dans Defender entreprise, vous pouvez prendre des mesures pour répondre à ces menaces. Découvrez comment utiliser la vue d’inventaire des appareils.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: b7a911991935407f9d512213c9d76c92106b74c8
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089559"
---
# <a name="respond-to-and-mitigate-threats-in-microsoft-defender-for-business"></a>Répondre aux menaces et les atténuer dans Microsoft Defender pour entreprises

Le portail Microsoft 365 Defender permet à votre équipe de sécurité de répondre aux menaces détectées et de les atténuer. Cet article vous guide tout au long d’un exemple d’utilisation de Defender entreprise.


## <a name="view-detected-threats"></a>Afficher les menaces détectées

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Notez les cartes sur la page d’accueil. Les cartes vous indiquent en un coup d’œil le nombre de menaces détectées, ainsi que le nombre de comptes d’utilisateurs, de points de terminaison (appareils) et d’autres ressources qui ont été affectés. L’image suivante est un exemple de cartes que vous pouvez voir :

   :::image type="content" source="../../media/defender-business/mdb-examplecards.png" alt-text="Capture d’écran des cartes dans le portail Microsoft 365 Defender":::

3. Sélectionnez un bouton ou un lien sur la carte pour afficher plus d’informations et prendre des mesures. Par exemple, notre carte **Appareils à risque** comprend un bouton **Afficher les détails** . Si vous sélectionnez ce bouton, nous accédons à la page **d’inventaire** des appareils, comme illustré dans l’image suivante :

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Capture d’écran de l’inventaire des appareils":::

   La page **Inventaire des** appareils répertorie les appareils d’entreprise, ainsi que leur niveau de risque et leur niveau d’exposition.

4. Sélectionnez un élément, tel qu’un appareil. Un volet volant s’ouvre et affiche plus d’informations sur les alertes et les incidents générés pour cet élément, comme illustré dans l’image suivante :  

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout.png" alt-text="Capture d’écran du volet volant d’un appareil sélectionné":::

5. Dans le menu volant, affichez les informations affichées. Sélectionnez les points de suspension (...) pour ouvrir un menu qui répertorie les actions disponibles, comme illustré dans l’image suivante : 

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout-menu.png" alt-text="Capture d’écran des actions disponibles pour un appareil sélectionné":::

6. Sélectionnez une action disponible. Par exemple, vous pouvez choisir **Exécuter l’analyse antivirus**, ce qui Antivirus Microsoft Defender démarrera une analyse rapide sur l’appareil. Vous pouvez également sélectionner **Lancer une investigation automatisée** pour déclencher une enquête automatisée sur l’appareil.

## <a name="next-steps"></a>Prochaines étapes

- [Passer en revue les actions de correction dans le Centre d’actions](mdb-review-remediation-actions.md)
- [Gérer les appareils dans Microsoft Defender pour entreprises](mdb-manage-devices.md)
- [Afficher et gérer les incidents dans Microsoft Defender pour entreprises](mdb-view-manage-incidents.md)
