---
title: Microsoft 365 Defender paramètres de fuseau horaire
description: Utilisez les informations contenues ici pour configurer les paramètres de fuseau horaire Microsoft 365 Defender et afficher les informations de licence.
keywords: paramètres, Microsoft Defender, renseignement sur les menaces de cybersécurité, Microsoft Defender pour point de terminaison, fuseau horaire, utc, heure locale, licence
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
ms.openlocfilehash: 5b749294989d3b7f5f6303f924e7718dc26c9cb0
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67580572"
---
# <a name="microsoft-365-defender-time-zone-settings"></a>Microsoft 365 Defender paramètres de fuseau horaire

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)


> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-settings-abovefoldlink)

Utilisez le menu **Fuseau** horaire pour configurer le fuseau horaire et afficher les informations de licence.
:::image type="content" source="images/atp-time-zone.png" alt-text="Paramètres du fuseau horaire-1" lightbox="images/atp-time-zone.png":::

## <a name="time-zone-settings"></a>Paramètres de fuseau horaire

L’aspect du temps est important dans l’évaluation et l’analyse des cyberattaques perçues et réelles.

Les enquêtes cyberforensiques s’appuient souvent sur des horodatages pour rassembler la séquence d’événements. Il est important que votre système reflète les paramètres de fuseau horaire appropriés.

Microsoft Defender pour point de terminaison pouvez afficher le temps universel coordonné (UTC) ou l’heure locale.

Votre paramètre de fuseau horaire actuel s’affiche dans le menu Microsoft Defender pour point de terminaison. Vous pouvez modifier le fuseau horaire affiché dans le menu **Fuseau horaire** .

:::image type="content" source="images/atp-time-zone-menu.png" alt-text="Paramètres du fuseau horaire-2" lightbox="images/atp-time-zone-menu.png":::

### <a name="utc-time-zone"></a>Fuseau horaire UTC

Microsoft Defender pour point de terminaison utilise l’heure UTC par défaut.

La définition du fuseau horaire Microsoft Defender pour point de terminaison sur UTC affiche tous les horodatages système (alertes, événements et autres) en UTC pour tous les utilisateurs. Cela peut aider les analystes de sécurité travaillant dans différents emplacements à travers le monde à utiliser les mêmes horodatages lors de l’examen des événements.

### <a name="local-time-zone"></a>Fuseau horaire local

Vous pouvez choisir d’avoir Microsoft Defender pour point de terminaison utiliser les paramètres de fuseau horaire local. Toutes les alertes et événements s’affichent à l’aide de votre fuseau horaire local.

Le fuseau horaire local est extrait des paramètres régionaux de votre appareil. Si vous modifiez vos paramètres régionaux, le fuseau horaire Microsoft Defender pour point de terminaison change également. Le choix de ce paramètre signifie que les horodatages affichés dans Microsoft Defender pour point de terminaison sont alignés sur l’heure locale pour tous les utilisateurs Microsoft Defender pour point de terminaison. Les analystes situés dans différents emplacements globaux voient désormais les alertes Microsoft Defender pour point de terminaison en fonction de leurs paramètres régionaux.

Le choix d’utiliser l’heure locale peut être utile si les analystes se trouvent dans un emplacement unique. Dans ce cas, il peut être plus facile de mettre en corrélation les événements avec l’heure locale, par exemple, lorsqu’un utilisateur local clique sur un lien d’e-mail suspect.

### <a name="set-the-time-zone"></a>Définir le fuseau horaire

Le fuseau horaire Microsoft Defender pour point de terminaison est défini par défaut sur UTC. La définition du fuseau horaire modifie également l’heure de toutes les vues Microsoft Defender pour point de terminaison.

Pour définir le fuseau horaire :

1. Cliquez sur le menu **Fuseau horaire** .
   :::image type="content" source="images/atp-time-zone.png" alt-text="Paramètres du fuseau horaire-3" lightbox="images/atp-time-zone.png":::
1. Sélectionnez l’indicateur **UTC du fuseau horaire** .
1. Sélectionnez **Timezone UTC** ou votre fuseau horaire local, par exemple -7:00.

### <a name="regional-settings"></a>Paramètres régionaux

Pour appliquer différents formats de date pour Microsoft Defender pour point de terminaison, utilisez des paramètres régionaux pour Internet Explorer (IE) et Microsoft Edge (Edge). Si vous utilisez un autre navigateur tel que Google Chrome, suivez les étapes requises pour modifier les paramètres d’heure et de date de ce navigateur. 

#### <a name="internet-explorer-ie-and-microsoft-edge"></a>Internet Explorer (IE) et Microsoft Edge

IE et Microsoft Edge utilisent les paramètres **de région** configurés dans l’option **Horloges, Langue et Région** dans le panneau de configuration. 

#### <a name="known-issues-with-regional-formats"></a>Problèmes connus avec les formats régionaux

##### <a name="date-and-time-formats"></a>Formats de date et d'heure

Il existe des problèmes connus avec les formats d’heure et de date. Si vous configurez vos paramètres régionaux sur d’autres formats que les formats pris en charge, le portail peut ne pas refléter correctement vos paramètres.

Les formats de date et d’heure suivants sont pris en charge :

- Format de date MM/dd/aaaa
- Format de date dd/MM/aaaa
- Format d’heure hh:mm:ss (format de 12 heures)

Les formats de date et d’heure suivants ne sont actuellement pas pris en charge :

- Format de date aaaa-MM-jj
- Format de date dd-MMM-yy
- Format de date dd/MM/yy
- Date format MM/dd/yy
- Format de date avec yy. Affichera seulement yyyyy.
- Format d’heure HH:mm:ss (format 24 heures)

##### <a name="decimal-symbol-used-in-numbers"></a>Symbole décimal utilisé dans les nombres

Le symbole décimal utilisé est toujours un point, même si une virgule est sélectionnée dans les paramètres de format **Nombres** dans les paramètres **de région** . Par exemple, 15,5 Ko s’affichent sous la forme de 15,5 Ko.
