---
title: Utiliser l’outil Diagnostics de page pour SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/03/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
f1.keywords:
- NOCSH
description: Utilisez l’outil Diagnostics de page pour SharePoint pour analyser SharePoint portail moderne en ligne et les pages de publication classiques par rapport à un ensemble prédéfini de critères de performances.
ms.openlocfilehash: a4d2c0f6d298578290d9f7daf850c4744e2f8dff
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621839"
---
# <a name="use-the-page-diagnostics-for-sharepoint-tool"></a>Utiliser l’outil Diagnostics de page pour SharePoint

Cet article explique comment utiliser **l’outil Diagnostics de page pour SharePoint** pour analyser SharePoint pages de site en ligne modernes et classiques par rapport à un ensemble prédéfini de critères de performances.

L’outil Diagnostics de page pour SharePoint peut être installé pour :

- **Microsoft Edge** [(extension Edge)](https://microsoftedge.microsoft.com/addons/detail/ocemkolpnamjcacndljdfmhlpcaoipji)
- **Chrome** [(extension Chrome)](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi)

>[!TIP]
>La version **2.0.0** et ultérieure inclut la prise en charge des pages modernes en plus des pages de site classiques. Si vous ne savez pas quelle version de l’outil que vous utilisez, vous pouvez sélectionner le lien **About** ou les points de suspension (...) pour vérifier votre version. **Toujours mettre à jour vers la dernière version** lors de l’utilisation de l’outil.

L’Outil Diagnostic de page pour SharePoint est une extension de navigateur pour le nouveau Microsoft Edge (les navigateurs https://www.microsoft.com/edge) et Chrome que vous pouvez utiliser pour analyser les pages de sites de publication SharePoint classiques et les portails modernes. Cet outil fonctionne uniquement pour SharePoint Online et ne peut pas être utilisé sur une page système SharePoint.

L’outil génère un rapport pour chaque page analysée montrant comment la page fonctionne par rapport à un ensemble prédéfini de règles et affiche des informations détaillées lorsque les résultats d’un test se trouvent en dehors de la valeur de référence. SharePoint Les administrateurs et concepteurs en ligne peuvent utiliser l’outil pour résoudre les problèmes de performances et s’assurer que les nouvelles pages sont optimisées avant la publication.

L’outil Diagnostics de page est conçu pour analyser SharePoint pages de site uniquement, et non les pages système telles que *allitems.aspx* ou *sharepoint.aspx*. Si vous tentez d’exécuter l’outil sur une page système ou toute autre page non-site, vous recevez un message d’erreur indiquant que l’outil ne peut pas être exécuté pour ce type de page.

> [!div class="mx-imgBorder"]
> ![Doit s’exécuter sur une page SharePoint.](../media/page-diagnostics-for-spo/pagediag-Error-StartPage.png)

Il ne s’agit pas d’une erreur dans l’outil, car il n’y a aucune valeur dans l’évaluation des bibliothèques ou des pages système. Accédez à une page SharePoint site pour utiliser l’outil. Si cette erreur se produit sur une page SharePoint, vérifiez la page maître pour vous assurer que les métatags SharePoint n’ont pas été supprimés.

Pour fournir des commentaires sur l’outil, sélectionnez les points de suspension dans le coin supérieur droit de l’outil, puis [sélectionnez Donner des commentaires](https://go.microsoft.com/fwlink/?linkid=874109).

> [!div class="mx-imgBorder"]
> ![Faites part de vos commentaires.](../media/page-diagnostics-for-spo/pagediag-feedback.png)
  
## <a name="install-the-page-diagnostics-for-sharepoint-tool"></a>Installer l’outil Diagnostics de page pour SharePoint

La procédure d’installation de cette section fonctionne pour les navigateurs Chrome et Microsoft Edge.

> [!IMPORTANT]
> Microsoft ne lit pas les données ou le contenu de page analysés par l’outil Diagnostics de page pour SharePoint, et nous ne capturons pas d’informations personnelles, de site web ou de téléchargement. Les seules informations identifiables consignées dans Microsoft par l’outil sont le nom du locataire, le nombre de règles ayant échoué et la date et l’heure d’exécution de l’outil. Ces informations sont utilisées par Microsoft pour mieux comprendre le portail moderne et les tendances d’utilisation des sites de publication et les problèmes de performances courants.

1. Installez l’outil Diagnostics de page pour SharePoint pour **Microsoft Edge** [(extension Edge)](https://microsoftedge.microsoft.com/addons/detail/ocemkolpnamjcacndljdfmhlpcaoipji) ou **Chrome** [(extension Chrome).](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) Consultez la politique de confidentialité de l’utilisateur fournie dans la page de description du magasin. Lorsque vous ajoutez l’outil à votre navigateur, vous verrez l’avis d’autorisations suivant.

    > [!div class="mx-imgBorder"]
    > ![Autorisations d’extension.](../media/page-diagnostics-for-spo/pagediag-add-to-edge.png)

    Cet avis est en place, car une page peut contenir du contenu provenant d’emplacements en dehors de SharePoint en fonction des composants WebPart et des personnalisations de la page. Cela signifie que l’outil lit les demandes et les réponses lorsque l’on clique sur le bouton Démarrer et uniquement pour l’onglet SharePoint actif où l’outil est en cours d’exécution. Ces informations sont capturées localement par le navigateur web et sont disponibles via le bouton **Exporter vers JSON** ou **Exporter vers HAR** dans l’onglet _Suivi réseau_ de l’outil. **Les informations ne sont pas envoyées ou capturées par Microsoft.** (L’outil respecte la politique de confidentialité De Microsoft accessible [ici](https://go.microsoft.com/fwlink/p/?linkid=857875).)

    L’autorisation _Gérer vos téléchargements_ couvre l’utilisation de la fonctionnalité **Exporter vers JSON** de l’outil. Suivez les instructions de confidentialité de votre entreprise avant de partager le fichier JSON en dehors de votre organisation, car les résultats contiennent des URL et peuvent être classés comme piI (informations d’identification personnelle).
1. Si vous souhaitez utiliser l’outil en mode Incognito ou InPrivate, suivez la procédure de votre navigateur :
    1. Dans Microsoft Edge, accédez à **Extensions** ou tapez _edge://extensions_ dans la barre d’URL, puis sélectionnez **Détails** de l’extension. Dans les paramètres d’extension, cochez la case **autoriser inPrivate**.
    1. Dans Chrome, accédez à **Extensions** ou tapez _chrome://extensions_ dans la barre d’URL, puis sélectionnez **Détails** de l’extension. Dans les paramètres d’extension, sélectionnez le curseur pour **autoriser incognito**.
1. Accédez à la page SharePoint site sur SharePoint Online que vous souhaitez consulter. Nous avons autorisé le « chargement différé » des éléments sur les pages ; par conséquent, l’outil ne s’arrête pas automatiquement (c’est par conception pour prendre en charge tous les scénarios de chargement de page). Pour arrêter la collecte, **sélectionnez Arrêter**. Assurez-vous que le chargement de la page est terminé avant d’arrêter la collecte de données ou que vous ne capturerez qu’une trace partielle.
1. Cliquez sur le bouton de barre d’outils de l’extension ![Diagnostics de page pour SharePoint logo.](../media/page-diagnostics-for-spo/pagediag-icon32.png) pour charger l’outil, la fenêtre contextuelle d’extension suivante s’affiche :

    ![Fenêtre contextuelle de l’outil Diagnostics de page.](../media/page-diagnostics-for-spo/pagediag-Landing.png)

Sélectionnez **Démarrer** pour commencer à collecter des données à des fins d’analyse.

## <a name="what-youll-see-in-the-page-diagnostics-for-sharepoint-tool"></a>Ce que vous verrez dans l’outil Diagnostics de page pour SharePoint

1. Cliquez sur les points de suspension (...) dans le coin supérieur droit de l’outil pour trouver les liens suivants :
   1. Le lien **Ressources supplémentaires** fournit des instructions générales et des détails sur l’outil, y compris un lien vers cet article.
   1. Le lien **Envoyer des commentaires** fournit un lien vers le site _user voice SharePoint sites et collaboration_.
   1. Le lien **À propos** inclut la version actuellement installée de l’outil et un lien direct vers l’avis tiers de l’outil.  
1. **L’ID de corrélation, SPRequestDuration, SPIISLatency**, **le temps de chargement** de la page et les détails de l’URL sont informatifs et peuvent être utilisés à quelques fins.

    > [!div class="mx-imgBorder"]
    > ![Détails des diagnostics de page.](../media/page-diagnostics-for-spo/pagediag-details.PNG)

   - **CorrelationID** est un élément important lors de l’utilisation de Support Microsoft, car il leur permet de collecter plus de données de diagnostic pour la page spécifique.
   - **SPRequestDuration** est le temps nécessaire à SharePoint pour traiter la page. La navigation structurelle, les images volumineuses, un grand nombre d’appels d’API peuvent tous contribuer à des durées plus longues.
   - **SPIISLatency** est le temps en millisecondes pris pour SharePoint Online commencent à charger la page. Cette valeur n’inclut pas le temps nécessaire à l’application web pour répondre.
   - **Le temps de chargement** de la page est la durée totale enregistrée par la page entre l’heure de la demande et l’heure à laquelle la réponse a été reçue et affichée dans le navigateur. Cette valeur est affectée par différents facteurs, notamment la latence du réseau, les performances de l’ordinateur et le temps nécessaire au navigateur pour charger la page.
   - **L’URL de page** (Uniform Resource Locator) est l’adresse web de la page active.

1. [**L’onglet Tests de diagnostic**](#how-to-use-the-diagnostic-tests-tab) affiche les résultats de l’analyse dans trois catégories ; **Aucune action n’est requise**, **les possibilités d’amélioration** et **l’attention requise**. Chaque résultat de test est représenté par un élément dans l’une de ces catégories, comme décrit dans le tableau suivant :

    |Catégorie  |Couleur  |Description  |
    |---------|---------|---------|
    |**Attention requise** |Rouge |Le résultat du test dépasse la valeur de référence et affecte les performances de la page. Suivez les instructions de correction.|
    |**Opportunités d’amélioration** |Jaune |Le résultat du test ne correspond pas à la valeur de référence et peut contribuer à des problèmes de performances. Des critères spécifiques aux tests peuvent s’appliquer.|
    |**Aucune action n'est requise** |Vert |Le résultat du test se situe dans la valeur de base du test.|

    > [!div class="mx-imgBorder"]
    > ![Diagnostics de page.](../media/page-diagnostics-for-spo/pagediag-results-general.PNG)

1. Un onglet [**Suivi réseau**](#how-to-use-the-network-trace-tab-and-how-to-export-a-har-file) fournit des détails sur les demandes de génération de page et les réponses.

## <a name="how-to-use-the-diagnostic-tests-tab"></a>Comment utiliser l’onglet Tests de diagnostic

Lorsque vous analysez une page SharePoint portail moderne ou une page de site de publication classique avec l’outil Diagnostics de page pour SharePoint, les résultats sont analysés à l’aide de règles prédéfinies qui comparent les résultats par rapport aux valeurs de base de référence et affichées sous l’onglet **Tests de diagnostic**. Les règles de certains tests peuvent utiliser différentes valeurs de base de référence pour le portail moderne et les sites de publication classiques en fonction des performances spécifiques  caractéristiques différentes entre les deux.

Les résultats des tests qui apparaissent dans les catégories **Possibilités d’amélioration** ou **Attention requises** indiquent les domaines qui doivent être examinés par rapport aux pratiques recommandées et peuvent être sélectionnés pour afficher des informations supplémentaires sur le résultat. Les détails de chaque élément incluent un lien _En savoir plus_ , qui vous guidera directement vers les conseils appropriés liés au test. Les résultats des tests qui apparaissent dans la catégorie **Aucune action requise** indiquent la conformité à la règle appropriée et n’affichent pas de détails supplémentaires lorsqu’ils sont sélectionnés.

Les informations de l’onglet Tests de diagnostic ne vous indiquent pas comment concevoir des pages, mais mettent en évidence les facteurs susceptibles d’impacter les performances de la page. Certaines fonctionnalités et personnalisations de page ont un impact inévitable sur les performances de la page, et doivent être examinées pour rechercher des corrections ou des omissions potentielles de la page si leur impact est important.

Les résultats rouges ou jaunes peuvent également indiquer des composants WebPart qui actualisent les données trop fréquemment. Par exemple, les actualités d’entreprise ne sont pas mises à jour toutes les secondes, mais les composants WebPart personnalisés sont souvent conçus pour extraire les dernières nouvelles toutes les secondes au lieu d’implémenter des éléments de mise en cache susceptibles d’améliorer l’expérience utilisateur globale. Gardez à l’esprit lors de l’inclusion de composants WebPart sur une page qu’il existe souvent des moyens simples de réduire leur impact sur les performances en évaluant la valeur de chaque paramètre disponible pour s’assurer qu’il est correctement défini pour son objectif.

>[!NOTE]
>Les sites d’équipe classiques qui n’ont pas la fonctionnalité de publication activée ne peuvent pas utiliser de CDN. Lorsque vous exécutez l’outil sur ces sites, le test CDN est censé échouer et peut être ignoré, mais tous les tests restants sont applicables. Les fonctionnalités supplémentaires de la fonctionnalité de publication SharePoint peuvent augmenter les temps de chargement des pages. Elle ne doit donc pas être activée uniquement pour autoriser CDN fonctionnalité.

>[!IMPORTANT]
>Les règles de test sont ajoutées et mises à jour régulièrement. Reportez-vous donc à la dernière version de l’outil pour plus d’informations sur les règles actuelles et des informations spécifiques incluses dans les résultats des tests. Vous pouvez vérifier la version en gérant vos extensions et l’extension indique si une mise à jour est disponible.

## <a name="how-to-use-the-network-trace-tab-and-how-to-export-a-har-file"></a>Comment utiliser l’onglet Suivi réseau et comment exporter un fichier HAR

**L’onglet Suivi réseau** fournit des informations détaillées sur les demandes de création de la page et les réponses reçues de SharePoint.

1. **Recherchez les temps de chargement des éléments marqués comme rouges**. Chaque requête et réponse est codée en couleur pour indiquer son impact sur les performances globales de la page à l’aide des métriques de latence suivantes :
    - Vert: \< 500ms
    - Jaune: 500-1000ms
    - Rouge : \> 1 000 ms

    > [!div class="mx-imgBorder"]
    > ![Trace réseau.](../media/page-diagnostics-for-spo/pagediag-networktrace-red.png)

    Dans l’image ci-dessus, l’élément rouge se rapporte à la page par défaut. Il s’affiche toujours en rouge, sauf si la page se charge en \< 1 000 ms (moins d’une seconde).

2. **Tester les temps de chargement des éléments**. Dans certains cas, il n’y aura pas d’indicateur de temps ou de couleur, car les éléments ont déjà été mis en cache par le navigateur. Pour tester cela correctement, ouvrez la page, **effacez** le cache du navigateur, puis cliquez sur Démarrer comme cela forcera un chargement de page « froid » et sera une véritable réflexion du chargement initial de la page. Cela doit ensuite être comparé au chargement de page « chaud », car cela permet également de déterminer les éléments mis en cache sur la page.

3. **Partagez les détails pertinents avec d’autres personnes qui peuvent vous aider à examiner les problèmes**. Pour partager les détails ou les informations fournis dans l’outil avec vos développeurs ou une personne de support technique, l’utilisation de l’option **Activer l’exportation vers l’archive HTTP (HAR)** est l’approche recommandée. 

   > [!div class="mx-imgBorder"]
   > ![Activer l’exportation vers HAR.](../media/page-diagnostics-for-spo/pagediag-submithar.png)

Cette option doit être activée avant de cliquer sur Démarrer, ce qui active le mode débogage dans votre navigateur. Il génère un fichier d’archive HTTP (HAR) accessible via l’onglet « Trace réseau ». Cliquez sur « Exporter vers HAR » pour télécharger le fichier sur votre ordinateur et vous pouvez ensuite le partager en conséquence. Le fichier peut être ouvert dans différents outils de débogage, tels que F12 Developer Tools et Fiddler.

> [!div class="mx-imgBorder"]
> ![Trace réseau.](../media/page-diagnostics-for-spo/pagediag-networktracehar.png)

> [!IMPORTANT]
> Ces résultats contiennent des URL qui peuvent être classées comme piI (informations d’identification personnelle). Veillez à suivre les instructions de votre organisation avant de distribuer ces informations.

## <a name="engaging-with-microsoft-support"></a>Utilisation de Support Microsoft

Nous avons inclus une **fonctionnalité de niveau Support Microsoft** qui ne doit être utilisée que lorsque vous travaillez directement sur un cas de support. L’utilisation de cette fonctionnalité ne vous apportera aucun avantage lorsqu’elle est utilisée sans engagement de l’équipe de support et peut ralentir considérablement les performances de la page. Il n’existe aucune information supplémentaire lors de l’utilisation de cette fonctionnalité dans l’outil, car les informations supplémentaires sont ajoutées à la journalisation dans le service.

Aucune modification n’est visible, sauf que vous serez averti que vous l’avez activé et que les performances de votre page seront considérablement dégradées de 2 à 3 fois les performances plus lentes quand elles sont activées. Elle ne s’applique qu’à la page particulière et à cette session active. Pour cette raison, cela doit être utilisé avec parcimonie et uniquement lorsqu’il est activement engagé avec le support.

### <a name="to-enable-the-microsoft-support-level-feature"></a>Pour activer la fonctionnalité de niveau Support Microsoft

1. Ouvrez l’outil Diagnostics de page pour SharePoint.
2. Sur votre clavier, **appuyez sur Alt-Shift-L**. La case à cocher **Activer la journalisation de la prise en charge** s’affiche.
3. Cochez la case, puis cliquez sur **Démarrer** pour recharger la page et générer une journalisation détaillée.

   > [!div class="mx-imgBorder"]
   > ![Option de support activée.](../media/page-diagnostics-for-spo/pagediag-support.png)
  
    Notez l’ID de corrélation (affiché en haut de l’outil) et fournissez-le à votre représentant de support pour lui permettre de recueillir des informations supplémentaires sur la session de diagnostic.

## <a name="related-topics"></a>Voir aussi

[Optimisation des performances SharePoint Online](tune-sharepoint-online-performance.md)

[Optimisation des performances Office 365](tune-microsoft-365-performance.md)

[Performances offertes par l’expérience moderne de SharePoint](/sharepoint/modern-experience-performance)

[Réseaux de distribution de contenu](content-delivery-networks.md)

[Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online](use-microsoft-365-cdn-with-spo.md)