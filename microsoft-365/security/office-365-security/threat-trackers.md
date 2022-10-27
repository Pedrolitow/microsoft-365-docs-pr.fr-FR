---
title: Suivis des menaces - Nouveautés et remarquables
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: a097f5ca-eac0-44a4-bbce-365f35b79ed1
ms.collection:
- m365-security
- m365initiative-defender-office365
ms.custom: ''
description: Découvrez les suivis des menaces, y compris les nouveaux suivis remarquables, pour aider votre organisation à rester au courant des problèmes de sécurité.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 5bc2bfb0d6592b9afd5dd1d6295b1bc1cf7d014a
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68728046"
---
# <a name="threat-trackers---new-and-noteworthy"></a>Suivis des menaces - Nouveautés et remarquables

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Office 365 fonctionnalités d’investigation et de réponse](office-365-ti.md) aux menaces permettent à l’équipe de sécurité de votre organisation de détecter et de prendre des mesures contre les menaces de cybersécurité. Office 365 fonctionnalités d’investigation et de réponse aux menaces incluent des fonctionnalités de suivi des menaces, notamment des suivis dignes d’intérêt. Lisez cet article pour obtenir une vue d’ensemble de ces nouvelles fonctionnalités et des étapes suivantes.

> [!IMPORTANT]
> Office 365 Threat Intelligence est désormais Microsoft Defender pour Office 365 Plan 2, ainsi que d’autres fonctionnalités de protection contre les menaces. Pour plus d’informations, consultez [Microsoft Defender pour Office 365 plans et tarification](https://products.office.com/exchange/advance-threat-protection) et la [description du service Microsoft Defender pour Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

## <a name="what-are-threat-trackers"></a>Que sont les suivis des menaces ?

Les suivis de menaces sont des widgets et des vues informatifs qui vous fournissent des informations sur différents problèmes de cybersécurité susceptibles d’impacter votre entreprise. Par exemple, vous pouvez afficher des informations sur les campagnes de programmes malveillants tendance à l’aide de suivi des menaces.

La plupart des pages de suivi incluent des numéros de tendance qui sont mis à jour régulièrement, des widgets pour vous aider à comprendre quels problèmes sont les plus importants ou qui ont le plus augmenté, et un lien rapide dans la colonne **Actions** qui vous dirige vers l’Explorateur, où vous pouvez afficher des informations plus détaillées.

:::image type="content" source="../../media/e426f220-fdcb-4dd9-99a2-db97dbcf71d5.png" alt-text="Exemple d’informations de campagne dans l’Explorateur" lightbox="../../media/e426f220-fdcb-4dd9-99a2-db97dbcf71d5.png":::

Les trackers ne sont que quelques-unes des nombreuses fonctionnalités que vous obtenez avec [Microsoft Defender pour Office 365 Plan 2](office-365-ti.md). Les suivis de menaces incluent [les suivis remarquables, les](#noteworthy-trackers) [suivis tendance, les](#trending-trackers) [requêtes suivies](#tracked-queries) et [les requêtes enregistrées](#saved-queries).

Pour afficher et utiliser vos traqueurs de menaces pour votre organisation, ouvrez le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com>, puis accédez à **Email & collaboration** \> **Suivi des menaces**. Pour accéder directement à la page **Suivi des menaces** , utilisez <https://security.microsoft.com/threattrackerv2>.

> [!NOTE]
> Pour utiliser des suivis de menaces, vous devez être administrateur général, administrateur de la sécurité ou lecteur de sécurité. Consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

### <a name="noteworthy-trackers"></a>Suivis remarquables

Les suivis remarquables sont l’endroit où vous trouverez des menaces et des risques importants et plus petits que nous pensons que vous devez connaître. Les suivis remarquables vous aident à déterminer si ces problèmes existent dans votre environnement Microsoft 365, ainsi qu’un lien vers des articles (comme celui-ci) qui vous donnent plus de détails sur ce qui se passe et comment ils auront un impact sur l’utilisation de Office 365 par votre organisation. Qu’il s’agisse d’une nouvelle menace importante (par exemple, Wannacry, Petya) ou d’une menace existante susceptible de créer de nouveaux défis (comme notre autre élément inaugural - Nemucod), c’est là que vous trouverez de nouveaux éléments importants que vous et votre équipe de sécurité devez examiner et examiner régulièrement.

En règle générale, les suivis dignes d’intérêt seront publiés pendant quelques semaines seulement lorsque nous identifierons de nouvelles menaces et pensons que vous aurez peut-être besoin de la visibilité supplémentaire que cette fonctionnalité offre. Une fois que le risque le plus important pour une menace est passé, nous allons supprimer cet élément notable. De cette façon, nous pouvons garder la liste à jour et à jour avec d’autres nouveaux éléments pertinents.

### <a name="trending-trackers"></a>Suivis de tendances

Les suivis de tendance (anciennement appelés campagnes) mettent en évidence les nouvelles menaces reçues dans les e-mails de votre organisation au cours de la semaine dernière. La vue Suivis des tendances fournit des évaluations dynamiques des menaces de messagerie qui ont un impact sur l’environnement Office 365 de votre organisation. Cette vue montre les tendances des programmes malveillants au niveau du locataire, en identifiant les familles de programmes malveillants à la hausse, à plat ou en déclin, ce qui permet aux administrateurs de mieux comprendre les menaces qui nécessitent une attention supplémentaire.

:::image type="content" source="../../media/d2ccc1a0-2a1d-4e36-99b5-6766c207772f.png" alt-text="L’exemple de widget de campagnes de programmes malveillants tendance" lightbox="../../media/d2ccc1a0-2a1d-4e36-99b5-6766c207772f.png":::

Les suivis tendances vous donnent une idée des nouvelles menaces que vous devez examiner pour vous assurer que votre environnement d’entreprise plus large est préparé contre les attaques.

### <a name="tracked-queries"></a>Requêtes suivies

Les requêtes suivies tirent parti de vos requêtes enregistrées pour évaluer régulièrement l’activité Microsoft 365 dans votre organisation. Cela vous donne une tendance aux événements, avec d’autres à venir dans les mois à venir. Les requêtes suivies s’exécutent automatiquement, ce qui vous donne des informations à jour sans avoir à vous rappeler de réexécuter vos requêtes.

:::image type="content" source="../../media/0c556174-06eb-4ae5-b32a-5ff76b9e4f13.png" alt-text="Exemple de requêtes suivies avec une sélectionnée" lightbox="../../media/0c556174-06eb-4ae5-b32a-5ff76b9e4f13.png":::

### <a name="saved-queries"></a>Requêtes enregistrées

Les requêtes enregistrées se trouvent également dans la section Suivis. Vous pouvez utiliser les requêtes enregistrées pour stocker les recherches courantes de l’Explorateur que vous souhaitez revenir plus rapidement et à plusieurs reprises, sans avoir à recréer la recherche à chaque fois.

:::image type="content" source="../../media/188cf3ff-58f1-41ea-81aa-76158d8f40c3.png" alt-text="Liste des requêtes suivies avec l’une sélectionnée" lightbox="../../media/188cf3ff-58f1-41ea-81aa-76158d8f40c3.png":::

Vous pouvez toujours enregistrer une requête de suivi notable ou l’une de vos propres requêtes Explorer à l’aide du bouton **Enregistrer la requête** en haut de la page Explorateur. Tout ce qui y est enregistré s’affiche dans la liste **Requêtes enregistrées** de la page Tracker.

## <a name="trackers-and-explorer"></a>Suivis et Explorateur

Que vous examiniez des e-mails, du contenu ou des activités Office (bientôt disponible), l’Explorateur et les suivis collaborent pour vous aider à examiner et à suivre les menaces et les risques de sécurité. Ensemble, les trackers vous fournissent des informations pour protéger vos utilisateurs en mettant en évidence les problèmes nouveaux, notables et fréquemment recherchés, garantissant ainsi que votre entreprise est mieux protégée à mesure qu’elle passe dans le cloud.

N’oubliez pas que vous pouvez toujours nous faire part de vos commentaires sur cette fonctionnalité de sécurité de Microsoft 365 ou sur d’autres fonctionnalités de sécurité de Microsoft 365 en cliquant sur le bouton **Commentaires** dans le coin inférieur droit.

:::image type="content" source="../../media/microsoft-365-defender-portal.png" alt-text="Portail Microsoft 365 Defender" lightbox="../../media/microsoft-365-defender-portal.png":::

## <a name="trackers-and-microsoft-defender-for-office-365"></a>Suivis et Microsoft Defender pour Office 365

Avec notre première menace notable, nous mettons en évidence les menaces de programmes malveillants avancées [détectées par les pièces jointes sécurisées](safe-attachments.md). Si vous êtes un client Office 365 Entreprise E5 et que vous n’utilisez pas [Microsoft Defender pour Office 365](defender-for-office-365.md), vous devez l’être : il est inclus dans votre abonnement. Defender pour Office 365 fournit de la valeur même si vous disposez d’autres outils de sécurité filtrant le flux de courrier électronique avec vos services Office 365. Toutefois, les fonctionnalités anti-courrier indésirable et [liens fiables](safe-links.md) fonctionnent mieux lorsque votre principale solution de sécurité de messagerie est via Office 365.

:::image type="content" source="../../media/policies.png" alt-text="Microsoft Defender pour Office 365 dans le portail Microsoft 365 Defender" lightbox="../../media/policies.png":::

Dans le monde d’aujourd’hui, le fait d’exécuter uniquement des analyses anti-programme malveillant traditionnelles signifie que vous n’êtes pas suffisamment protégé contre les attaques. Les attaquants plus sophistiqués d’aujourd’hui utilisent des outils couramment disponibles pour créer de nouvelles attaques, masquées ou retardées qui ne seront pas reconnues par les moteurs anti-programmes malveillants traditionnels basés sur des signatures. La fonctionnalité Pièces jointes sécurisées prend les pièces jointes des e-mails et les déclenche dans un environnement virtuel pour déterminer si elles sont sécurisées ou malveillantes. Ce processus de détonation ouvre chaque fichier dans un environnement d’ordinateur virtuel, puis surveille ce qui se passe après l’ouverture du fichier. Qu’il s’agisse d’un fichier PDF, d’un fichier compressé ou d’un document Office, le code malveillant peut être masqué dans un fichier, ne s’activant qu’une fois que la victime l’ouvre sur son ordinateur. En détonnant et en analysant le fichier dans le flux d’e-mail, Defender pour Office 365 fonctionnalités détectent ces menaces en fonction des comportements, de la réputation des fichiers et d’un certain nombre de règles heuristiques.

Le nouveau filtre de menaces notables met en évidence les éléments récemment détectés par le biais de pièces jointes fiables. Ces détections représentent des éléments qui sont de nouveaux fichiers malveillants, introuvables précédemment par Microsoft 365 dans votre flux de messagerie ou dans les e-mails d’autres clients. Faites attention aux éléments du dispositif de suivi des menaces dignes d’intérêt, voyez qui a été ciblé par eux et passez en revue les détails de la détonation affichés sous l’onglet Analyse avancée (trouvé en cliquant sur l’objet de l’e-mail dans l’Explorateur). Notez que vous ne trouverez cet onglet que sur les e-mails détectés par la fonctionnalité Pièces jointes fiables : ce dispositif de suivi notable inclut ce filtre, mais vous pouvez également utiliser ce filtre pour d’autres recherches dans l’Explorateur.

## <a name="next-steps"></a>Prochaines étapes

- Si votre organisation ne dispose pas déjà de ces fonctionnalités Office 365 d’investigation et de réponse aux menaces, consultez [Comment obtenir Office 365 fonctionnalités d’investigation et de réponse aux menaces ?](office-365-ti.md).

- Assurez-vous que votre équipe de sécurité dispose des rôles et autorisations appropriés. Vous devez être administrateur général ou disposer du rôle Administrateur de la sécurité ou Recherche et purge dans le portail Microsoft 365 Defender. Consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

- Surveillez les nouveaux trackers qui s’affichent dans votre environnement Microsoft 365. Le cas échéant, vous trouverez vos suivis sur la page **Suivi** des menaces dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com/threattracker>.

- Si vous ne l’avez pas déjà fait, découvrez et configurez [Microsoft Defender pour Office 365](defender-for-office-365.md) pour votre organisation, notamment [les liens fiables](safe-links.md) et [les pièces jointes fiables](safe-attachments.md).
