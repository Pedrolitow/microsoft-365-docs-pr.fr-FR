---
title: Diagnostic des problèmes de performances avec SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/19/2021
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: Cet article vous montre comment diagnostiquer des problèmes courants avec votre site SharePoint Online à l’aide des outils de développement Internet Explorer.
ms.openlocfilehash: a3ad33b147a20cd5b072f7f3ccc1b9272a58ef54
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321500"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a>Diagnostic des problèmes de performances avec SharePoint Online

Cet article vous montre comment diagnostiquer des problèmes courants avec votre site SharePoint Online à l’aide des outils de développement Internet Explorer.
  
Il existe quatre façons différentes d’identifier qu’une page d’un site SharePoint Online présente un problème de performances avec les personnalisations.

- Diagnostic des performances du site et de la page
  
- Moniteur réseau de la barre d’outils F12

- Comparaison à une ligne de base non personnalisée

- SharePoint en-tête de réponse en ligne

Cette rubrique décrit comment utiliser chacune de ces méthodes pour diagnostiquer les problèmes de performances. Une fois que vous avez compris la cause du problème, vous pouvez travailler à une solution à l’aide des articles sur l’amélioration des performances SharePoint que vous pouvez trouver sur https://aka.ms/tune.  

## <a name="use-the-site-and-page-performance-diagnostic-from-the-microsoft-365-admin-center"></a>Utiliser le diagnostic des performances du site et de la page à partir Administration Microsoft 365 site

> [!NOTE]
> Si vous êtes un administrateur et que vous avez des difficultés avec les performances dans SharePoint, sélectionnez Exécuter les **tests** ci-dessous, qui remplit le diagnostic des performances du site et de la page dans le Centre Administration Microsoft 365. Ces tests vérifient votre configuration et recommandent rapidement les étapes suivantes pour améliorer SharePoint performances de votre client.
>> [!div class="nextstepaction"]
>> [Exécuter des tests : vérifier SharePoint performances](https://aka.ms/PillarSiteandPagePerf)

> [!NOTE] 
> Cette fonctionnalité n’est pas disponible pour Microsoft 365 administration, Microsoft 365 géré par 21Vianet ou Microsoft 365 Germany.
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a>Utilisation de la barre d’outils F12 pour diagnostiquer les performances dans SharePoint Online
<a name="F12ToolInfo"> </a>

Dans cet article, nous utilisons Internet Explorer 11. Les versions des outils de développement F12 sur d’autres navigateurs ont des fonctionnalités similaires, bien qu’elles semblent légèrement différentes. Pour plus d’informations sur les outils de développement F12, voir :
  
- [Nouveautés des outils F12](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182632(v=vs.85))

- [Utilisation des outils de développement F12](/previous-versions/windows/internet-explorer/ie-developer/samples/bg182326(v=vs.85))

Pour faire monter les outils de développement, appuyez **sur F12** , puis cliquez sur Wi-Fi icône :
  
![Capture d’écran de l’icône Wifi des outils de développement F12.](../media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
Sous **l’onglet** Réseau, appuyez sur le bouton vert pour charger une page. L’outil renvoie tous les fichiers demandés par le navigateur afin d’obtenir la page que vous avez demandé. La capture d’écran suivante montre une liste de ce type.
  
![Capture d’écran de la liste de fichiers renvoyés avec une demande de page.](../media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
Vous pouvez également voir les heures de téléchargement des fichiers sur le côté droit, comme illustré dans cette capture d’écran.
  
![Diagramme montrant le temps nécessaire au chargement des pages demandées à partir de SharePoint.](../media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
Cela vous donne une représentation visuelle de la durée de chargement du fichier. La ligne verte représente le moment où la page est prête à être rendue par le navigateur. Cela peut vous donner un aperçu rapide des différents fichiers qui peuvent être à l’origine de chargements de page lents sur votre site.
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a>Configuration d’une planification non personnalisée pour SharePoint Online
<a name="F12ToolInfo"> </a>

La meilleure façon de déterminer les points faibles en terme de performances de votre site consiste à configurer une collection de sites complète dans SharePoint Online. De cette façon, vous pouvez comparer tous les différents aspects de votre site avec ce que vous obtenez sans personnalisation sur la page. La OneDrive Entreprise page d’accueil est un bon exemple d’une collection de sites distincte qui n’a probablement pas de personnalisations.
  
## <a name="viewing-sharepoint-response-header-information"></a>Affichage des SharePoint d’en-tête de réponse
<a name="F12ToolInfo"> </a>

Dans SharePoint Online, vous pouvez accéder aux informations renvoyées au navigateur dans l’en-tête de réponse pour chaque fichier. La valeur la plus utile pour diagnostiquer les problèmes de performances est **SPRequestDuration**, qui affiche la durée de traitement de la demande sur le serveur. Cela peut aider à déterminer si la demande est très lourde et demande beaucoup de ressources. Il s’agit de la meilleure information que vous avez sur la quantité de travail que le serveur fait pour servir la page.

### <a name="to-view-sharepoint-response-header-information"></a>Pour afficher les SharePoint’en-tête de réponse
  
1. Assurez-vous que les outils F12 sont installés. Pour plus d’informations sur le téléchargement et l’installation de ces outils, voir Nouveautés [des outils F12](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182632(v=vs.85)).

2. Dans les outils F12, **sous l’onglet** Réseau, appuyez sur le bouton vert pour charger une page.

3. Cliquez sur l’un des fichiers .aspx renvoyés par l’outil, puis cliquez sur **DÉTAILS**.

    ![Affiche les détails de l’en-tête de réponse.](../media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. Cliquez sur **En-têtes de réponse**.

    ![Diagramme montrant l’URL de l’en-tête de réponse.](../media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a>Qu’est-ce qui provoque des problèmes de performances dans SharePoint Online ?
<a name="F12ToolInfo"> </a>

L’article Options de navigation pour [SharePoint Online](navigation-options-for-sharepoint-online.md) montre un exemple d’utilisation de la valeur SPRequestDuration pour déterminer que la navigation structurelle compliquée a provoqué un long processus de la page sur le serveur. En prenant une valeur pour un site de référence (sans personnalisation), il est possible de déterminer si le chargement d’un fichier donné prend beaucoup de temps. L’exemple utilisé dans [les options de navigation SharePoint Online](navigation-options-for-sharepoint-online.md) est le fichier .aspx principal. Ce fichier contient la plupart du code ASP.NET qui s’exécute pour le chargement de votre page. Selon le modèle de site que vous utilisez, il peut s’agit de start.aspx, home.aspx, default.aspx ou d’un autre nom si vous personnalisez la page d’accueil. Si ce nombre est beaucoup plus élevé que votre site de référence, cela indique qu’un problème de performances est à l’origine d’un problème dans votre page.
  
Une fois que vous avez identifié qu’un problème spécifique à votre site est identifié, la meilleure façon de déterminer ce qui provoque des performances médiocres consiste à éliminer toutes les causes possibles, telles que les personnalisations de page, puis à les rajouter au site une par une. Une fois que vous avez supprimé suffisamment de personnalisations pour que la page s’exécute bien, vous pouvez rajouter des personnalisations spécifiques une par une.
  
Par exemple, si vous avez une navigation très complexe, essayez de modifier la navigation pour ne pas afficher les sous-sites, puis vérifiez les outils de développement pour voir si cela fait une différence. Ou si vous avez une grande quantité de roll-ups de contenu, essayez de les supprimer de votre page et de voir si cela améliore les choses. Si vous éliminez toutes les causes possibles et que vous les ajoutez une par une, vous pouvez facilement identifier les fonctionnalités qui sont le problème le plus important, puis travailler à une solution.
