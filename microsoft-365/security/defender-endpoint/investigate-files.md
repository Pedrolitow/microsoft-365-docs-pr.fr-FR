---
title: Examiner les fichiers Microsoft Defender pour les points de terminaison
description: Utilisez les options d’examen pour obtenir des détails sur les fichiers associés aux alertes, comportements ou événements.
keywords: examiner, examen, fichier, activité malveillante, motivation des attaques, analyse approfondie, rapport d’analyse approfondie
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: 0cb7523036d6660d4b5556fdfd07e443a359b208
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466232"
---
# <a name="investigate-a-file-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Examiner un fichier associé à une alerte Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatefiles-abovefoldlink)

Examinez les détails d’un fichier associé à une alerte, un comportement ou un événement spécifique pour déterminer si le fichier présente des activités malveillantes, identifier la motivation de l’attaque et comprendre l’étendue potentielle de la violation.

Il existe plusieurs façons d’accéder à la page de profil détaillée d’un fichier spécifique. Par exemple, vous pouvez utiliser la fonctionnalité de recherche, cliquer sur un lien à partir de l’arborescence du processus d’alerte **, du** graphique **d’incident****, de** la chronologie de l’artefact ou sélectionner un événement répertorié dans la chronologie de **l’appareil**.

Une fois sur la page de profil détaillée, vous pouvez basculer entre la nouvelle et l’ancienne mise en page en basant **la nouvelle page fichier**. Le reste de cet article décrit la mise en page la plus nouvelle.

Vous pouvez obtenir des informations à partir des sections suivantes dans l’affichage de fichier :

- Détails du fichier, détection des programmes malveillants, prévalence du fichier
- Analyse profonde
- Alertes
- Observé dans l’organisation
- Analyse profonde
- Noms de fichiers

Vous pouvez également agir sur un fichier à partir de cette page.

## <a name="file-actions"></a>Actions de fichier

En haut de la page de profil, au-dessus des cartes d’informations de fichier. Les actions que vous pouvez effectuer ici sont les suivantes :

- Arrêter et mettre en quarantaine
- Indicateur d’ajout/modification
- Télécharger un fichier
- Consulter un spécialiste des menaces
- Centre de notifications

Pour plus d’informations sur ces actions, voir [Action de réponse sur un fichier](respond-file-alerts.md).

## <a name="file-details-malware-detection-and-file-prevalence"></a>Détails du fichier, détection des programmes malveillants et prévalence du fichier

Les détails du fichier, les incidents, la détection des programmes malveillants et les cartes de prévalence de fichier affichent différents attributs sur le fichier.

Vous verrez des détails tels que le MD5 du fichier, le taux de détection du nombre total de virus et la détection de l’antivirus Microsoft Defender, le cas besoin, ainsi que la prévalence du fichier.

La carte de prévalence du fichier indique où le fichier a été vu sur les appareils de l’organisation et du monde entier.

> [!NOTE]
> Différents utilisateurs peuvent voir des valeurs différentes dans les appareils de *la section Organisation* de la carte de prévalence du fichier. En effet, la carte affiche des informations en fonction de l’étendue RBAC dont dispose un utilisateur. Cela signifie que si un utilisateur a obtenu une visibilité sur un ensemble spécifique d’appareils, il verra uniquement le fichier de prévalence organisationnelle sur ces appareils.

:::image type="content" source="images/atp-file-information.png" alt-text="Informations sur le fichier" lightbox="images/atp-file-information.png":::

## <a name="alerts"></a>Alertes

**L’onglet Alertes** fournit une liste des alertes associées au fichier. Cette liste couvre la plupart des informations de la file d’attente des alertes, à l’exception du groupe d’appareils, s’il y en a, à qui appartient l’appareil concerné. Vous pouvez choisir le type d’informations affiché en sélectionnant  Personnaliser les colonnes dans la barre d’outils au-dessus des en-têtes de colonne.

:::image type="content" source="images/atp-alerts-related-to-file.png" alt-text="Les alertes associées à la section de fichier" lightbox="images/atp-alerts-related-to-file.png":::

## <a name="observed-in-organization"></a>Observé dans l’organisation

**L’onglet Observé dans l’organisation** vous permet de spécifier une plage de dates pour voir quels appareils ont été observés avec le fichier.

> [!NOTE]
> Cet onglet affiche un nombre maximal de 100 appareils. Pour voir tous _les_ appareils avec le fichier, exportez l’onglet dans un fichier CSV en sélectionnant **Exporter** à partir du menu Actions au-dessus des en-têtes de colonne de l’onglet.

:::image type="content" source="images/atp-observed-machines.png" alt-text="Appareils les plus récemment observés avec le fichier" lightbox="images/atp-observed-machines.png":::

Utilisez le curseur ou le sélecteur de plage pour spécifier rapidement une période à vérifier pour les événements impliquant le fichier. Vous pouvez spécifier une fenêtre de temps aussi petite qu’un seul jour. Cela vous permettra de voir uniquement les fichiers qui ont communiqué avec cette adresse IP à ce moment-là, ce qui réduit considérablement les recherches et les défilements inutiles.

## <a name="deep-analysis"></a>Analyse profonde

**L’onglet** Analyse approfondie vous permet de soumettre le fichier pour analyse [approfondie, afin](respond-file-alerts.md#deep-analysis) de découvrir plus de détails sur le comportement du fichier, ainsi que l’effet qu’il a au sein de vos organisations. Une fois le fichier soumis, le rapport d’analyse approfondie s’affiche dans cet onglet une fois que les résultats sont disponibles. Si l’analyse approfondie n’a trouvé rien, le rapport est vide et l’espace de résultats reste vide.

:::image type="content" source="images/submit-file.png" alt-text="Onglet Analyse approfondie" lightbox="images/submit-file.png":::

## <a name="file-names"></a>Noms de fichiers

**L’onglet Noms** de fichiers répertorie tous les noms que le fichier a été observé pour utiliser, au sein de vos organisations.

:::image type="content" source="images/atp-file-names.png" alt-text="Onglet Noms de fichiers" lightbox="images/atp-file-names.png":::

## <a name="related-topics"></a>Sujets associés

- [Afficher et organiser la file d’attente de Microsoft Defender pour les points de terminaison](alerts-queue.md)
- [Gérer les alertes microsoft Defender pour les points de terminaison](manage-alerts.md)
- [Examiner microsoft Defender pour les alertes de point de terminaison](investigate-alerts.md)
- [Examiner les appareils de la liste Microsoft Defender pour les appareils de point de terminaison](investigate-machines.md)
- [Examiner une adresse IP associée à une alerte Microsoft Defender pour le point de terminaison](investigate-ip.md)
- [Examiner un domaine associé à une alerte Microsoft Defender pour le point de terminaison](investigate-domain.md)
- [Examiner un compte d’utilisateur dans Microsoft Defender pour le point de terminaison](investigate-user.md)
- [Prendre des mesures de réponse sur un fichier](respond-file-alerts.md)
