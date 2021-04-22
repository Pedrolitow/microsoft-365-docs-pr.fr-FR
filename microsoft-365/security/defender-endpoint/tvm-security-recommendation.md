---
title: Recommandations en matière de sécurité par gestion des menaces et des vulnérabilités
description: Obtenez des recommandations de sécurité actionnables prioritaires par menace, probabilité de violation et valeur dans la gestion des menaces et des vulnérabilités.
keywords: gestion des menaces et des vulnérabilités, recommandation sur la sécurité tvm de Microsoft Defender pour les points de terminaison, recommandation en matière de cybersécurité, recommandation de sécurité actionnable
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: af22bac911339de9c2e02df24a77c1889a33d43a
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51933732"
---
# <a name="security-recommendations---threat-and-vulnerability-management"></a>Recommandations en matière de sécurité : gestion des menaces et des vulnérabilités

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-portaloverview-abovefoldlink)

Les faiblesses de cybersécurité identifiées dans votre organisation sont mappées à des recommandations de sécurité actionnables et hiérarchisées par leur impact. Les recommandations hiérarchisées permettent de raccourcir le temps d'atténuation ou de correction des vulnérabilités et de stimuler la conformité.

Chaque recommandation de sécurité inclut des étapes de correction actionnables. Pour faciliter la gestion des tâches, vous pouvez également envoyer la recommandation à l'aide de Microsoft Intune et de Microsoft Endpoint Configuration Manager. Lorsque le paysage des menaces change, la recommandation change également lorsqu'elle collecte en permanence des informations à partir de votre environnement.

>[!TIP]
>Pour obtenir des e-mails sur les nouveaux événements de vulnérabilité, voir Configurer les notifications par courrier électronique de vulnérabilité [dans Microsoft Defender pour le point de terminaison](configure-vulnerability-email-notifications.md)

## <a name="how-it-works"></a>Mode de fonctionnement

Chaque appareil de l'organisation est marqué en fonction de trois facteurs importants pour aider les clients à se concentrer sur les bonnes choses au bon moment.

- **Menace** : caractéristiques des vulnérabilités et des exploits dans les appareils et l'historique des violations de votre organisation. En fonction de ces facteurs, les recommandations de sécurité indiquent les liens correspondants vers les alertes actives, les campagnes contre les menaces en cours et leurs rapports analytiques sur les menaces correspondants.

- **Probabilité de violation** : posture de sécurité et résilience de votre organisation contre les menaces

- **Valeur commerciale** : ressources de votre organisation, processus critiques et propriétés intellectuelles

## <a name="navigate-to-the-security-recommendations-page"></a>Accéder à la page Recommandations en matière de sécurité

Accédez à la page Recommandations de sécurité de différentes manières :

- Menu de navigation de gestion des menaces et des vulnérabilités dans le [Centre de sécurité Microsoft Defender](portal-overview.md)
- Principales recommandations en matière de sécurité dans le tableau de bord de gestion des [menaces et des vulnérabilités](tvm-dashboard-insights.md)

Affichez les recommandations de sécurité associées aux endroits suivants :

- Page de logiciels
- Page Appareil

### <a name="navigation-menu"></a>Menu de navigation

Go to the threat and vulnerability management navigation menu and select **Security recommendations**. La page contient une liste de recommandations de sécurité pour les menaces et les vulnérabilités trouvées dans votre organisation.

### <a name="top-security-recommendations-in-the-threat-and-vulnerability-management-dashboard"></a>Principales recommandations en matière de sécurité dans le tableau de bord de gestion des menaces et des vulnérabilités

Dans un jour donné en tant qu'administrateur [](tvm-dashboard-insights.md) de la sécurité, vous pouvez consulter le tableau de bord de gestion des menaces et des vulnérabilités pour voir votre [score](tvm-exposure-score.md) d'exposition côte à côte avec votre degré de sécurisation Microsoft pour les [appareils.](tvm-microsoft-secure-score-devices.md) L'objectif est **de** réduire l'exposition  de votre organisation contre les vulnérabilités et d'augmenter la sécurité des appareils de votre organisation afin d'être plus résiliente contre les attaques contre les menaces de cybersécurité. La liste des recommandations de sécurité les plus importantes peut vous aider à atteindre cet objectif.

![Exemple de carte recommandations de sécurité principales, avec quatre recommandations de sécurité.](images/top-security-recommendations350.png)

Les principales recommandations en matière de sécurité présentent les opportunités d'amélioration prioritaires en fonction des facteurs importants mentionnés dans la section précédente : menace, probabilité de violation et valeur. La sélection d'une recommandation vous permet d'accès à la page recommandations de sécurité avec plus de détails.

## <a name="security-recommendations-overview"></a>Vue d'ensemble des recommandations de sécurité

Afficher les recommandations, le nombre de faiblesses trouvées, les composants associés, les informations sur les menaces, le nombre d'appareils exposés, l'état, le type de correction, les activités de correction, l'impact sur votre score d'exposition et le score de sécurité Microsoft pour les appareils, ainsi que les balises associées.

La couleur du graphique **des appareils exposés** change à mesure que la tendance change. Si le nombre d'appareils exposés augmente, la couleur passe en rouge. En cas de diminution du nombre d'appareils exposés, la couleur du graphique change en vert.

>[!NOTE]
>La gestion des menaces et des vulnérabilités affiche les appareils qui étaient utilisés il y a **30** jours. Ceci est différent du reste de Microsoft Defender pour point de terminaison, où si un appareil n'a pas été utilisé pendant plus de 7 jours, il présente l'état « Inactif ».

![Exemple de page d'accueil pour les recommandations de sécurité.](images/tvmsecrec-updated.png)

### <a name="icons"></a>Icônes

Les icônes utiles peuvent également attirer rapidement votre attention sur :
- ![flèche tapant une cible](images/tvm_alert_icon.png) alertes actives possibles
- ![bogue rouge](images/tvm_bug_icon.png) exploits publics associés
- ![light light light](images/tvm_insight_icon.png) informations sur les recommandations

### <a name="explore-security-recommendation-options"></a>Explorer les options de recommandation de sécurité

Sélectionnez la recommandation de sécurité que vous souhaitez examiner ou traiter.

![Exemple de page de recommandation de sécurité.](images/secrec-flyouteolsw.png)

Dans le volant, vous pouvez choisir l'une des options suivantes :

- **Page Ouvrir un logiciel** : ouvrez la page du logiciel pour obtenir plus de contexte sur le logiciel et la façon dont il est distribué. Les informations peuvent inclure le contexte des menaces, les recommandations associées, les faiblesses découvertes, le nombre d'appareils exposés, les vulnérabilités découvertes, les noms et les détails des appareils sur lequel le logiciel est installé et la distribution des versions.

- [**Options de**](tvm-remediation.md) correction : envoyez une demande de correction pour ouvrir un ticket dans Microsoft Intune pour que votre administrateur informatique le sélectionne et l'adresse. Suivre l'activité de correction dans la page Correction.

- [**Options d'exception**](tvm-exception.md) : soumettre une exception, fournir une justification et définir la durée de l'exception si vous ne pouvez pas encore résoudre le problème.

>[!NOTE]
>Lorsqu'une modification logicielle est réalisée sur un appareil, il faut généralement 2 heures pour que les données soient reflétées dans le portail de sécurité. Toutefois, cela peut parfois prendre plus de temps. Les modifications de configuration peuvent prendre entre 4 et 24 heures.

### <a name="investigate-changes-in-device-exposure-or-impact"></a>Examiner les modifications apportées à l'exposition ou à l'impact de l'appareil

S'il y a une augmentation importante du nombre d'appareils exposés ou une forte augmentation de l'impact sur le score d'exposition de votre organisation et le score de sécurité Microsoft pour les appareils, cette recommandation de sécurité vaut la peine d'être étudier.

1. Sélectionnez la page Recommandation **et Ouvrir le logiciel**
2. Sélectionnez **l'onglet Chronologie** des événements pour afficher tous les événements qui ont un impact sur ce logiciel, tels que les nouvelles vulnérabilités ou les nouvelles exploitations publiques. [En savoir plus sur la chronologie des événements](threat-and-vuln-mgt-event-timeline.md)
3. Décider comment faire face à l'augmentation ou à l'exposition de votre organisation, par exemple envoyer une demande de correction

## <a name="request-remediation"></a>Demander la correction

La fonctionnalité de correction de la gestion des menaces et des vulnérabilités relie les administrateurs informatiques et de sécurité par le biais du flux de travail de demande de correction. Les administrateurs de sécurité comme vous pouvez demander à l'administrateur informatique de corriger une vulnérabilité à partir de la **page** recommandations de sécurité vers Intune. [En savoir plus sur les options de correction](tvm-remediation.md)

### <a name="how-to-request-remediation"></a>Comment demander des corrections

Sélectionnez une recommandation de sécurité pour qui vous souhaitez demander des corrections, puis sélectionnez **Options de correction.** Remplissez le formulaire et sélectionnez **Envoyer la demande.** Go to the [**Remediation**](tvm-remediation.md) page to view the status of your remediation request. [En savoir plus sur la demande de correction](tvm-remediation.md#request-remediation)

## <a name="file-for-exception"></a>Fichier d'exception

En remplacement d'une demande de correction lorsqu'une recommandation n'est pas pertinente pour le moment, vous pouvez créer des exceptions pour les recommandations. [En savoir plus sur les exceptions](tvm-exception.md)

Seuls les utilisateurs ayant des autorisations de « gestion des exceptions » peuvent ajouter des exceptions. [En savoir plus sur les rôles RBAC.](user-roles.md)

Lorsqu'une exception est créée pour une recommandation, elle n'est plus active. L'état de recommandation change en **Exception complète ou** Exception **partielle** (par groupe d'appareils).

### <a name="how-to-create-an-exception"></a>Comment créer une exception

Sélectionnez une recommandation de sécurité pour la création d'une exception, puis sélectionnez **Options d'exception.**  

![Affichage de l'emplacement du bouton « options d'exception » dans un volant de recommandations de sécurité.](images/tvm-exception-options.png)

Remplissez le formulaire et soumettez-le. Pour afficher toutes vos exceptions (actuelles et passées), accédez à la [page](tvm-remediation.md) Correction sous le menu Gestion des vulnérabilités des menaces **&** et sélectionnez l'onglet **Exceptions.** En savoir plus sur la création d'une [exception](tvm-exception.md#create-an-exception)

## <a name="report-inaccuracy"></a>Report inaccuracy

Vous pouvez signaler un faux positif lorsque vous voyez des informations de recommandation de sécurité vagues, inexactes, incomplètes ou déjà corrigés.

1. Ouvrez la recommandation sécurité.

2. Sélectionnez les trois points en dehors de la recommandation de sécurité que vous souhaitez signaler, puis sélectionnez **L'imprécision du rapport.**

    ![Affichage de l'endroit où le bouton « Signaler l'imprécision » se trouve dans un volant de recommandations de sécurité.](images/report-inaccuracy500.png)

3. Dans le volet de menu volant, sélectionnez la catégorie d'imprécision dans le menu déroulant, remplissez votre adresse e-mail et les détails concernant l'imprécision.

4. Sélectionnez **Envoyer**. Vos commentaires sont immédiatement envoyés aux experts en gestion des menaces et des vulnérabilités.

## <a name="related-articles"></a>Articles connexes

- [Vue d'ensemble de la gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Tableau de bord](tvm-dashboard-insights.md)
- [Score d'exposition](tvm-exposure-score.md)
- [Niveau de sécurité Microsoft pour les appareils](tvm-microsoft-secure-score-devices.md)
- [Corriger des vulnérabilités](tvm-remediation.md)
- [Créer et afficher des exceptions pour les recommandations de sécurité](tvm-exception.md)
- [Chronologie des événements](threat-and-vuln-mgt-event-timeline.md)
