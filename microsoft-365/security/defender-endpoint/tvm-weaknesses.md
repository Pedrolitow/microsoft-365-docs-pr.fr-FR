---
title: 'Vulnérabilités dans mon organisation : Gestion des menaces et des vulnérabilités'
description: Répertorie les vulnérabilités courantes et l’ID d’exposition (CVE) des faiblesses trouvées dans le logiciel en cours d’exécution dans votre organisation. Détecté par Microsoft Defender pour endpoint Gestion des menaces et des vulnérabilités fonctionnalité.
keywords: Microsoft Defender for Endpoint threat & gestion des vulnérabilités, Gestion des menaces et des vulnérabilités, Microsoft Defender for Endpoint tvm weaknesses page, finding weaknesses through tvm, tvm vulnerability list, vulnerability details in tvm
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
ms.openlocfilehash: 552209e6a93ba70c0cf279694fdc703923bcc509
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2021
ms.locfileid: "61164753"
---
# <a name="vulnerabilities-in-my-organization---threat-and-vulnerability-management"></a>Vulnérabilités dans mon organisation : Gestion des menaces et des vulnérabilités

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Menaces et gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Les menaces et gestion des vulnérabilités utilisent les mêmes signaux dans Defender pour la protection des points de terminaison pour analyser et détecter les vulnérabilités.

La page **Faiblesses** répertorie les vulnérabilités logicielles que vos appareils sont exposés en répertoriant l’ID CVE (Common Vulnerabilities and Exposures). Vous pouvez également afficher la gravité, la notation des vulnérabilités courantes (CVSS), la prévalence dans votre organisation, la violation correspondante, les informations sur les menaces, etc.

> [!NOTE]
> Si aucun ID CVE officiel n’est affecté à une vulnérabilité, le nom de la vulnérabilité est attribué par Gestion des menaces et des vulnérabilités.

> [!TIP]
> Pour obtenir des e-mails sur les nouveaux événements de vulnérabilité, voir Configurer les notifications par courrier électronique de vulnérabilité [dans Microsoft Defender pour endpoint](configure-vulnerability-email-notifications.md)

## <a name="navigate-to-the-weaknesses-page"></a>Accéder à la page Faiblesses

Accédez à la page Faiblesses de différentes manières :

- Sélection des **faiblesses dans le** menu de **navigation** gestion des vulnérabilités dans le portail [Microsoft 365 Defender] (portal-overview.md)
- Recherche globale

### <a name="navigation-menu"></a>Menu de navigation

Go to the **Vulnerability management** navigation menu and select **Weaknesses** to open the list of CVEs.

### <a name="vulnerabilities-in-global-search"></a>Vulnérabilités dans la recherche globale

1. Go to the global search drop-down menu.
2. Sélectionnez **Vulnérabilité et** clé dans l’ID CVE (Common Vulnerabilities and Exposures) que vous recherchez, puis sélectionnez l’icône de recherche. La page **Faiblesses** s’ouvre avec les informations CVE que vous recherchez.
![Zone de recherche globale avec l’option « vulnérabilité » sélectionnée et un exemple CVE.](images/tvm-vuln-globalsearch.png)
3. Sélectionnez la CVE pour ouvrir un panneau volant avec plus d’informations, notamment la description de la vulnérabilité, les détails, les informations sur les menaces et les appareils exposés.

Pour voir le reste des vulnérabilités dans la page **Faiblesses,** tapez CVE, puis sélectionnez rechercher.

## <a name="weaknesses-overview"></a>Vue d’ensemble des faiblesses

Corriger les vulnérabilités des appareils exposés afin de réduire les risques pour vos ressources et votre organisation. Si la **colonne Appareils** exposés affiche 0, cela signifie que vous n’êtes pas en danger.

![Page d’accueil des faiblesses.](images/tvm-weaknesses-overview.png)

### <a name="breach-and-threat-insights"></a>Informations sur les violations et les menaces

Affichez les informations sur les violations et menaces associées dans la colonne **Menace** lorsque les icônes sont colorées en rouge.

 > [!NOTE]
 > Toujours hiérarchiser les recommandations associées aux menaces en cours. Ces recommandations sont marquées avec l’icône d’informations sur les menaces ![ Simple dessin d’un bogue rouge.](images/tvm_bug_icon.png) et l’icône d’informations sur la violation, dessin ![ simple d’une flèche qui atteint une cible. ](images/tvm_alert_icon.png) .

L’icône Informations sur les violations est mise en surbrillant si une vulnérabilité est trouvée dans votre organisation.
![Exemple de texte d’informations sur la violation qui peut s’afficher lorsque vous placez le pointage sur l’icône. Celle-ci indique « une alerte active possible est associée à cette recommandation.](images/tvm-breach-insights.png)

L’icône Informations sur les menaces est mise en évidence si la vulnérabilité trouvée dans votre organisation est associée à des exploits. Le pointage sur l’icône indique si la menace fait partie d’un kit d’exploitation ou est connectée à des campagnes avancées persistantes ou à des groupes d’activités spécifiques. Lorsqu’il est disponible, il existe un lien vers un rapport d’analyse des menaces avec les actualités sur l’exploitation zéro jour, les divulgations ou les conseils de sécurité associés.

![Texte d’informations sur les menaces qui peut s’afficher lorsque vous placez le pointage sur l’icône. Celle-ci possède plusieurs points de puce et du texte lié.](images/tvm-threat-insights.png)

### <a name="gain-vulnerability-insights"></a>Obtenir des informations sur les vulnérabilités

Si vous sélectionnez une CVE, un panneau volant s’ouvre avec plus d’informations telles que la description de la vulnérabilité, les détails, les informations sur les menaces et les appareils exposés.

- La catégorie « Fonctionnalité du système d’exploitation » s’affiche dans les scénarios pertinents
- Vous pouvez passer à la recommandation de sécurité associée pour chaque CVE avec appareil exposé

 ![Exemple de volant de faiblesse.](images/tvm-weakness-flyout400.png)

### <a name="software-that-isnt-supported"></a>Logiciel non pris en charge

Les VC pour les logiciels qui ne sont actuellement pas pris en charge par les menaces & gestion des vulnérabilités sont toujours présents dans la page Faiblesses. Étant donné que le logiciel n’est pas pris en charge, seules des données limitées seront disponibles.

Les informations sur l’appareil exposé ne seront pas disponibles pour les VC avec des logiciels non pris en cas de non-gestion. Filtrez en sélectionnant l’option « Non disponible » dans la section « Appareils exposés ».

:::image type="content" alt-text="Filtre des appareils exposés." source="images/tvm-exposed-devices-filter.png":::

## <a name="view-common-vulnerabilities-and-exposures-cve-entries-in-other-places"></a>Afficher les entrées CVE (Common Vulnerabilities and Exposures) à d’autres endroits

### <a name="top-vulnerable-software-in-the-dashboard"></a>Logiciels les plus vulnérables dans le tableau de bord

1. Go to the [Gestion des menaces et des vulnérabilités dashboard](tvm-dashboard-insights.md) and scroll down to the Top **vulnerable software** widget. Vous verrez le nombre de vulnérabilités trouvées dans chaque logiciel, ainsi que des informations sur les menaces et une vue d’exposition de haut niveau de l’appareil au fil du temps.

    ![Carte logicielle la plus vulnérable avec quatre colonnes : logiciels, faiblesses, menaces, appareils exposés.](images/tvm-top-vulnerable-software500.png)

2. Sélectionnez le logiciel que vous souhaitez examiner pour aller à une page d’exercice.

3. Sélectionnez **l’onglet Vulnérabilités découvertes.**

4. Sélectionnez la vulnérabilité que vous souhaitez examiner pour plus d’informations sur les détails de la vulnérabilité

    ![Windows vue d’ensemble de l’accès à l’avant vers le bas pour Server 2019.](images/windows-server-drilldown.png)

### <a name="discover-vulnerabilities-in-the-device-page"></a>Découvrir les vulnérabilités dans la page d’appareil

Afficher les informations sur les faiblesses associées dans la page de l’appareil.

1. Go to the Microsoft 365 Defender navigation menu bar, then select the device icon. La page **Inventaire des** appareils s’ouvre.

2. Dans la page **Inventaire des** appareils, sélectionnez le nom de l’appareil que vous souhaitez examiner.

    ![Liste des appareils avec l’appareil sélectionné à examiner.](images/tvm_machinetoinvestigate.png)

3. La page de l’appareil s’ouvre avec des détails et des options de réponse pour l’appareil que vous souhaitez examiner.

4. Sélectionnez **vulnérabilités découvertes.**

   :::image type="content" alt-text="Page Appareil avec détails et options de réponse." source="images/tvm-discovered-vulnerabilities.png" lightbox="images/tvm-discovered-vulnerabilities.png":::

5. Sélectionnez la vulnérabilité que vous souhaitez examiner pour ouvrir un panneau volant avec les détails CVE, tels que : description de la vulnérabilité, informations sur les menaces et logique de détection.

#### <a name="cve-detection-logic"></a>Logique de détection CVE

Comme pour la preuve logicielle, nous montrons maintenant la logique de détection que nous avons appliquée sur un appareil afin de l’afficher comme vulnérable. La nouvelle section est appelée « Logique de détection » (dans toute vulnérabilité détectée dans la page de l’appareil) et affiche la logique et la source de détection.

La catégorie « Fonctionnalité du système d’exploitation » est également affichée dans les scénarios pertinents. Une CVE affecterait les appareils qui exécutent un système d’exploitation vulnérable uniquement si un composant de système d’exploitation spécifique est activé. Supposons que Windows Server 2019 ou Windows Server 2022 présente une vulnérabilité dans son composant DNS. Avec cette nouvelle fonctionnalité, nous n’attacherons cette CVE qu’aux appareils Windows Server 2019 et Windows Server 2022 avec la fonctionnalité DNS activée dans leur système d’exploitation.

:::image type="content" alt-text="Exemple de logique de détection qui répertorie les logiciels détectés sur l’appareil et les ko." source="images/tvm-cve-detection-logic.png":::

## <a name="report-inaccuracy"></a>Inaccuracy de rapport

Signalez un faux positif lorsque vous voyez des informations vagues, inexactes ou incomplètes. Vous pouvez également signaler les recommandations de sécurité qui ont déjà été corrigés.

1. Ouvrez la CVE sur la page Faiblesses.
2. Select **Report inaccuracy** and a flyout pane will open.
3. Sélectionnez la catégorie d’imprécision dans le menu déroulant et remplissez votre adresse e-mail et les détails d’imprécision.
4. Sélectionnez **Envoyer**. Vos commentaires sont immédiatement envoyés aux experts Gestion des menaces et des vulnérabilités de sécurité.

## <a name="related-articles"></a>Articles connexes

- [Vue d’ensemble gestion des vulnérabilités menaces et gestion des vulnérabilités menaces](next-gen-threat-and-vuln-mgt.md)
- [Recommandations de sécurité](tvm-security-recommendation.md)
- [Inventaire des logiciels](tvm-software-inventory.md)
- [Tableau de bord des informations](tvm-dashboard-insights.md)
- [Afficher et organiser la liste Microsoft Defender pour les appareils de point de terminaison](machines-view-overview.md)
