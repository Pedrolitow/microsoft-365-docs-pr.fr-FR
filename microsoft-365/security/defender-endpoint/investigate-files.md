---
title: Examiner les fichiers Microsoft Defender pour point de terminaison
description: Utilisez les options d’investigation pour obtenir des détails sur les fichiers associés aux alertes, aux comportements ou aux événements.
keywords: examiner, investigation, fichier, activité malveillante, motivation d’attaque, analyse approfondie, rapport d’analyse approfondie
ms.service: microsoft-365-security
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
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 9d7d3bd2636ff877c36656cc5769cb655e48f53b
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67688942"
---
# <a name="investigate-a-file-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Examiner un fichier associé à une alerte de Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatefiles-abovefoldlink)

Examinez les détails d’un fichier associé à une alerte, un comportement ou un événement spécifique pour déterminer si le fichier présente des activités malveillantes, identifier la motivation de l’attaque et comprendre l’étendue potentielle de la violation.

Il existe de nombreuses façons d’accéder à la page de profil détaillée d’un fichier spécifique. Par exemple, vous pouvez utiliser la fonctionnalité de recherche, cliquer sur un lien à partir de **l’arborescence du processus d’alerte**, **du graphe d’incidents**, de la **chronologie des artefacts** ou sélectionner un événement répertorié dans la **chronologie de l’appareil**.

Une fois sur la page de profil détaillée, vous pouvez basculer entre les mises en page nouvelles et anciennes en basculant la **nouvelle page fichier**. Le reste de cet article décrit la mise en page la plus récente.

Vous pouvez obtenir des informations à partir des sections suivantes dans l’affichage des fichiers :

- Détails du fichier, détection des programmes malveillants, prévalence des fichiers
- Métadonnées PE de fichier (le cas échéant)
- Analyse profonde
- Alertes
- Observé dans l’organisation
- Analyse profonde
- Noms de fichiers

Vous pouvez également agir sur un fichier à partir de cette page.

## <a name="file-actions"></a>Actions de fichier

En haut de la page de profil, au-dessus des cartes d’informations de fichier. Les actions que vous pouvez effectuer ici sont les suivantes :

- Arrêter et mettre en quarantaine
- Ajouter/modifier un indicateur
- Télécharger un fichier
- Consulter un spécialiste des menaces
- Centre de notifications

Pour plus d’informations sur ces actions, consultez [Prendre une action de réponse sur un fichier](respond-file-alerts.md).

## <a name="file-details-malware-detection-and-file-prevalence"></a>Détails du fichier, détection des programmes malveillants et prévalence des fichiers

Les détails du fichier, l’incident, la détection des programmes malveillants et les cartes de prévalence de fichier affichent différents attributs sur le fichier.

Vous verrez des détails tels que le MD5 du fichier, le taux de détection du nombre total de virus et la détection de l’antivirus Microsoft Defender s’il est disponible, ainsi que la prévalence du fichier.

La carte de prévalence du fichier indique où le fichier a été vu dans les appareils de l’organisation et dans le monde entier. Vous pouvez facilement pivoter vers les premiers et derniers appareils sur lesquels le fichier a été vu, et poursuivre l’investigation dans la chronologie de l’appareil. 

> [!NOTE]
> Différents utilisateurs peuvent voir des valeurs différentes dans les *appareils dans* la section organisation de la carte de prévalence de fichier. Cela est dû au fait que la carte affiche des informations en fonction de l’étendue RBAC dont dispose un utilisateur. Autrement dit, si une visibilité a été accordée à un utilisateur sur un ensemble spécifique d’appareils, il ne verra que la prévalence de l’organisation de fichiers sur ces appareils.

:::image type="content" source="images/atp-file-information.png" alt-text="Informations sur le fichier" lightbox="images/atp-file-information.png":::

## <a name="alerts"></a>Alertes

L’onglet **Alertes** fournit une liste des alertes associées au fichier, ainsi que l’incident auquel l’alerte est liée. Cette liste couvre la plupart des mêmes informations que la file d’attente d’alertes, à l’exception du groupe d’appareils auquel appartient l’appareil concerné, le cas échéant. Vous pouvez choisir le type d’informations affiché en sélectionnant **Personnaliser les colonnes** dans la barre d’outils au-dessus des en-têtes de colonne.

:::image type="content" source="images/atp-alerts-related-to-file.png" alt-text="Alertes liées à la section fichier" lightbox="images/atp-alerts-related-to-file.png":::

## <a name="observed-in-organization"></a>Observé dans l’organisation

**L’onglet Observé dans l’organisation** vous permet de spécifier une plage de dates pour voir quels appareils ont été observés avec le fichier.

> [!NOTE]
> Cet onglet affiche un nombre maximal de 100 appareils. Pour afficher _tous les_ appareils avec le fichier, exportez l’onglet vers un fichier CSV en sélectionnant **Exporter** dans le menu Action au-dessus des en-têtes de colonne de l’onglet.

:::image type="content" source="images/atp-observed-machines.png" alt-text="Les appareils observés les plus récents avec le fichier" lightbox="images/atp-observed-machines.png":::

Utilisez le curseur ou le sélecteur de plage pour spécifier rapidement une période que vous souhaitez vérifier pour les événements impliquant le fichier. Vous pouvez être aidé par l’indication des alertes sur la plage. Vous pouvez spécifier une fenêtre de temps aussi petite qu’une seule journée. Cela vous permet de voir uniquement les fichiers qui ont communiqué avec cette adresse IP à ce moment-là, ce qui réduit considérablement le défilement et la recherche inutiles.

## <a name="deep-analysis"></a>Analyse profonde

L’onglet **Analyse approfondie** vous permet de [soumettre le fichier pour une analyse approfondie](respond-file-alerts.md#deep-analysis), afin de découvrir plus de détails sur le comportement du fichier, ainsi que l’effet qu’il a au sein de vos organisations. Une fois le fichier soumis, le rapport d’analyse approfondie s’affiche dans cet onglet une fois les résultats disponibles. Si l’analyse approfondie n’a rien trouvé, le rapport est vide et l’espace des résultats reste vide.

:::image type="content" source="images/submit-file.png" alt-text="Onglet Analyse approfondie" lightbox="images/submit-file.png":::

## <a name="file-names"></a>Noms de fichiers

**L’onglet Noms** de fichiers répertorie tous les noms que le fichier a été observé à utiliser, au sein de vos organisations.

:::image type="content" source="images/atp-file-names.png" alt-text="Onglet Noms de fichiers" lightbox="images/atp-file-names.png":::

## <a name="action-center"></a>Centre de notifications

Le **Centre d’actions** affiche le centre d’actions filtré sur un fichier spécifique, afin que vous puissiez voir les actions en attente et l’historique des actions effectuées sur le fichier.

## <a name="related-topics"></a>Voir aussi

- [Afficher et organiser la file d’attente Microsoft Defender pour point de terminaison](alerts-queue.md)
- [Gérer les alertes Microsoft Defender pour point de terminaison](manage-alerts.md)
- [Examiner les alertes Microsoft Defender pour point de terminaison](investigate-alerts.md)
- [Examiner les appareils dans la liste des appareils Microsoft Defender pour point de terminaison](investigate-machines.md)
- [Examiner une adresse IP associée à une alerte Microsoft Defender pour point de terminaison](investigate-ip.md)
- [Examiner un domaine associé à une alerte de Microsoft Defender pour point de terminaison](investigate-domain.md)
- [Examiner un compte d’utilisateur dans Microsoft Defender pour point de terminaison](investigate-user.md)
- [Prendre des mesures de réponse sur un fichier](respond-file-alerts.md)
