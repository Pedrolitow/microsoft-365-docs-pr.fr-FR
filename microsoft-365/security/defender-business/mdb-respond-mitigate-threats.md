---
title: Répondre aux menaces et les atténuer dans Microsoft Defender pour entreprises
description: Comme des menaces sont détectées dans Defender entreprise, vous pouvez prendre des mesures pour répondre à ces menaces. Découvrez comment utiliser la vue d’inventaire des appareils.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: microsoft-365-security
ms.subservice: mdb
ms.localizationpriority: medium
ms.date: 09/14/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-security
- m365-initiative-defender-business
- tier1
ms.openlocfilehash: 1ba8e1897e82feed3c3b7e7d585ad60534e2be31
ms.sourcegitcommit: 0283c436f3ba61a708b52b57a1955f5ea74376a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68097377"
---
# <a name="respond-to-and-mitigate-threats-in-microsoft-defender-for-business"></a>Répondre aux menaces et les atténuer dans Microsoft Defender pour entreprises

Le portail Microsoft 365 Defender permet à votre équipe de sécurité de répondre aux menaces détectées et de les atténuer. Cet article vous guide tout au long d’un exemple d’utilisation de Defender entreprise.


## <a name="view-detected-threats"></a>Afficher les menaces détectées

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Notez les cartes sur la page d’accueil. Les cartes vous indiquent en un coup d’œil le nombre de menaces détectées, ainsi que le nombre de comptes d’utilisateurs, de points de terminaison (appareils) et d’autres ressources qui ont été affectés. L’image suivante est un exemple de cartes que vous pouvez voir :

   :::image type="content" source="../../media/defender-business/mdb-examplecards.png" alt-text="Capture d’écran des cartes dans le portail Microsoft 365 Defender":::

3. Sélectionnez un bouton ou un lien sur la carte pour afficher plus d’informations et prendre des mesures. Par exemple, notre carte **Appareils à risque** comprend un bouton **Afficher les détails** . La sélection de ce bouton nous amène à la liste **des appareils** , comme illustré dans l’image suivante :

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Capture d'écran de l'inventaire des appareils":::

   La page **Appareils** répertorie les appareils d’entreprise, ainsi que leur niveau de risque et leur niveau d’exposition.

4. Sélectionnez un élément, tel qu’un appareil. Un volet déroulant s'ouvre et affiche plus d'informations sur les alertes et les incidents générés pour cet élément, comme illustré dans l'image suivante :  

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout.png" alt-text="Capture d'écran du volet déroulant pour un appareil sélectionné":::

5. Sur le menu déroulant, affichez les informations affichées. Sélectionnez les points de suspension (...) pour ouvrir un menu qui répertorie les actions disponibles, comme illustré dans l'image suivante : 

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout-menu.png" alt-text="Capture d'écran des actions disponibles pour un appareil sélectionné":::

6. Sélectionnez une action disponible. Par exemple, vous pouvez choisir **Exécuter une analyse antivirus**, ce qui entraînera le lancement d'une analyse rapide de l'antivirus Microsoft Defender sur l'appareil. Vous pouvez également sélectionner **Lancer une enquête automatisée** pour déclencher une enquête automatisée sur l'appareil.

## <a name="next-steps"></a>Prochaines étapes

- [Passer en revue les actions de correction dans le Centre d’actions](mdb-review-remediation-actions.md)
- [Gérer les appareils dans Defender entreprise](mdb-manage-devices.md)
- [Afficher et gérer les incidents dans Defender entreprise](mdb-view-manage-incidents.md)
