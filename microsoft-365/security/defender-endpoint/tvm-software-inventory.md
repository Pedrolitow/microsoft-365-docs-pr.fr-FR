---
title: Inventaire logiciel dans Gestion des menaces et des vulnérabilités
description: La page d’inventaire des logiciels du point de terminaison de Microsoft Defender Gestion des menaces et des vulnérabilités le nombre de faiblesses et de vulnérabilités détectées dans les logiciels.
keywords: Gestion des menaces et des vulnérabilités, Microsoft Defender pour le point de terminaison, Inventaire logiciel Microsoft Defender pour les points de terminaison, Microsoft Defender pour les menaces de point de terminaison & gestion des vulnérabilités, Microsoft Defender pour les menaces de point de terminaison & gestion des vulnérabilités  inventaire des logiciels, Inventaire logiciel Microsoft Defender pour endpoint tvm, inventaire des logiciels tvm
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: e6bf614730caa9060a334c0a01c2dfe64b24df78
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325269"
---
# <a name="software-inventory---threat-and-vulnerability-management"></a>Inventaire logiciel : Gestion des menaces et des vulnérabilités


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Menaces et gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

L’inventaire des logiciels Gestion des menaces et des vulnérabilités liste des logiciels connus de votre organisation. Le filtre par défaut de la page d’inventaire logiciel affiche tous les logiciels avec les [listes officielles de plateformes communes (CPE).](https://nvd.nist.gov/products/cpe) L’affichage inclut des détails tels que le nom du fournisseur, le nombre de faiblesses, les menaces et le nombre d’appareils exposés.

Vous pouvez supprimer le filtre **CPE** disponible, afin d’obtenir une meilleure visibilité et d’augmenter votre étendue de recherche sur tous les logiciels installés dans votre organisation. Cela signifie que tous les logiciels, y compris les logiciels sans CPE, s’affichent désormais dans la liste d’inventaire des logiciels.

> [!NOTE]
> Comme les processeurs sont utilisés par les gestion des vulnérabilités pour identifier le logiciel et les vulnérabilités, même si les produits logiciels sans CPE s’afficheront dans la page d’inventaire logiciel, ils ne seront pas pris en charge par les Gestion des menaces et des vulnérabilités  et les informations telles que les exploits, le nombre d’appareils exposés et les faiblesses ne seront pas disponibles pour eux.

## <a name="how-it-works"></a>Fonctionnement

Dans le domaine de la découverte, nous tirent parti du même ensemble de signaux responsable de l’évaluation de la détection et de la vulnérabilité dans Microsoft Defender pour les fonctionnalités de détection et de réponse des points de [terminaison](overview-endpoint-detection-response.md).

Dans la mesure où c’est en temps réel, en quelques minutes, vous verrez des informations de vulnérabilité au moment où elles sont découvertes. Le moteur prend automatiquement des informations à partir de plusieurs flux de sécurité. En fait, vous verrez si un logiciel particulier est connecté à une campagne contre les menaces en direct. Il fournit également un lien vers un rapport d’analyse des menaces dès qu’il est disponible.

## <a name="navigate-to-the-software-inventory-page"></a>Accéder à la page Inventaire logiciel

Accédez à la page d’inventaire  logiciel en sélectionnant Inventaire logiciel dans le menu Gestion des menaces et des vulnérabilités navigation dans le [portail Microsoft 365 Defender logiciels](portal-overview.md).

Afficher les logiciels sur des appareils spécifiques dans les pages des appareils individuels à partir de la [liste des appareils](machines-view-overview.md).

> [!NOTE]
> Si vous recherchez des logiciels à l’aide de la recherche globale de Microsoft Defender for Endpoint, veillez à placer un trait de soulignement au lieu d’un espace. Par exemple, pour obtenir les meilleurs résultats de recherche, écrivez « windows_10 » ou « windows_11 » au lieu de « Windows 10 » ou « Windows 11 ».

## <a name="software-inventory-overview"></a>Vue d’ensemble de l’inventaire logiciel

La **page Inventaire** logiciel s’ouvre avec une liste des logiciels installés dans votre réseau, y compris le nom du fournisseur, les faiblesses trouvées, les menaces qui y sont associées, les appareils exposés, l’impact sur le score d’exposition et les balises.

Par défaut, l’affichage est filtré par **code produit (CPE) : Disponible**. Vous pouvez également filtrer l’affichage liste en fonction des faiblesses trouvées dans le logiciel, des menaces qui lui sont associées et des balises telles que si le logiciel a atteint la fin de la prise en charge.

:::image type="content" alt-text="Exemple de page d’accueil pour l’inventaire logiciel." source="images/software-inventory-page.png" lightbox="images/tvm-software-inventory.png":::

Sélectionnez le logiciel que vous souhaitez examiner. Un panneau volant s’ouvre avec une vue plus compacte des informations sur la page. Vous pouvez soit approfondir l’examen et sélectionner la **page Ouvrir un** logiciel, soit signaler toute incohérence technique en sélectionnant **l’imprécision du rapport**.

### <a name="software-that-isnt-supported"></a>Logiciel non pris en charge

Les logiciels qui ne sont actuellement pas pris en charge par les menaces & gestion des vulnérabilités peuvent être présents dans la page d’inventaire logiciel. Comme elle n’est pas prise en charge, seules des données limitées seront disponibles. Filtrez selon les logiciels non pris en place avec l’option « Non disponible » dans la section « Faiblesse ».

:::image type="content" alt-text="Filtre logiciel non pris en temps et place." source="images/tvm-unsupported-software-filter.png" lightbox="images/tvm-unsupported-software-filter.png":::

Les informations suivantes indiquent que les logiciels ne sont pas pris en charge :

- Le champ Faiblesses indique « Non disponible »
- Le champ Appareils exposés affiche un tiret
- Texte d’information ajouté dans le panneau latéral et dans la page du logiciel
- La page logicielle ne contient pas les recommandations de sécurité, les vulnérabilités découvertes ou les sections de chronologie des événements

## <a name="software-inventory-on-devices"></a>Inventaire logiciel sur les appareils

À partir du Microsoft 365 Defender de navigation du portail, allez à l’inventaire **[des appareils](machines-view-overview.md)**. Sélectionnez le nom d’un appareil pour ouvrir la page de l’appareil (tel que  Computer1), puis sélectionnez l’onglet Inventaire logiciel pour voir la liste de tous les logiciels connus présents sur l’appareil. Sélectionnez une entrée de logiciel spécifique pour ouvrir le volant avec plus d’informations.

Le logiciel peut être visible au niveau de l’appareil même s’il n’est actuellement pas pris en charge par Gestion des menaces et des vulnérabilités. Toutefois, seules des données limitées seront disponibles. Vous savez si le logiciel n’est pas pris en compte, car il indique « Non disponible » dans la colonne « Faiblesse ».

Les logiciels sans CPE peuvent également s’afficher sous cet inventaire logiciel propre à l’appareil.

### <a name="software-evidence"></a>Preuve logicielle

Voir la preuve de l’endroit où nous avons détecté un logiciel spécifique sur un appareil à partir du Registre, du disque ou des deux. Vous pouvez le trouver sur n’importe quel appareil dans l’inventaire logiciel de l’appareil.

Sélectionnez un nom de logiciel pour ouvrir le volant et recherchez la section appelée « Preuve logicielle ».

:::image type="content" alt-text="Exemple de preuve logicielle de Windows 10 de la liste des appareils, montrant le chemin d’accès au Registre des preuves logicielles." source="images/tvm-software-evidence.png" lightbox="images/tvm-software-evidence.png":::

## <a name="software-pages"></a>Pages logicielles

Vous pouvez afficher les pages logicielles de différentes manières :

- Page Inventaire logiciel > sélectionner un nom de logiciel > **page** Sélectionner un logiciel ouvert dans le volant
- [Page Recommandations en matière](tvm-security-recommendation.md) de sécurité > sélectionner une recommandation > **page** Sélectionner un logiciel ouvert dans le volant
- Page chronologie [des événements](threat-and-vuln-mgt-event-timeline.md) > Sélectionnez un > Sélectionnez le nom du logiciel avec lien hypertexte (comme Visual Studio 2017) dans la section intitulée « Composant associé » dans le volant

 Une page complète s’affiche avec tous les détails d’un logiciel spécifique et les informations suivantes :

- Panneau latéral avec des informations sur le fournisseur, la prévalence du logiciel dans l’organisation (y compris le nombre d’appareils sur lesquels il est installé et les appareils exposés qui ne sont pas corrigés), si l’exploitation est disponible et l’impact sur le score d’exposition.
- Visualisations de données montrant le nombre et la gravité des vulnérabilités et des mauvaises configurations. En outre, les graphiques avec le nombre d’appareils exposés.
- Onglets affichant des informations telles que :
  - Recommandations de sécurité correspondantes pour les faiblesses et vulnérabilités identifiées.
  - Cv nommés des vulnérabilités découvertes.
  - Les appareils sur qui le logiciel est installé (ainsi que le nom de l’appareil, le domaine, le système d’exploitation, et bien plus encore).
  - Liste des versions des logiciels (y compris le nombre d’appareils sur lesquels la version est installée, le nombre de vulnérabilités découvertes et les noms des appareils installés).

    :::image type="content" alt-text="Page d’exemples de logiciels Visual Studio 2017 avec les détails logiciels, les faiblesses, les appareils exposés, etc." source="images/tvm-software-page-example.png" lightbox="images/tvm-software-page-example.png":::

## <a name="report-inaccuracy"></a>Inaccuracy de rapport

Signalez une imprécision lorsque vous voyez des informations de vulnérabilité et des résultats d’évaluation incorrects.

1. Ouvrez le programme volant sur la page Inventaire logiciel.
2. **Sélectionnez l’imprécision du rapport**.
3. Dans le volet volant, choisissez un problème à partir de :

    - un détail logiciel est faux
    - le logiciel n’est installé sur aucun appareil de mon organisation
    - le nombre d’appareils installés ou exposés est erroné

4. Remplissez les détails demandés sur l’imprécision. Cela varie en fonction du problème que vous signalez.

![Inaccuracy de rapport](images/report-inaccuracy-software.png)

5. Sélectionnez **Envoyer**. Vos commentaires sont immédiatement envoyés aux experts Gestion des menaces et des vulnérabilités de sécurité.

## <a name="related-articles"></a>Articles connexes

- [Vue d’ensemble gestion des vulnérabilités menaces et gestion des vulnérabilités menaces](next-gen-threat-and-vuln-mgt.md)
- [Recommandations de sécurité](tvm-security-recommendation.md)
- [Chronologie des événements](threat-and-vuln-mgt-event-timeline.md)
- [Afficher et organiser la liste Microsoft Defender pour les appareils de point de terminaison](machines-view-overview.md)
