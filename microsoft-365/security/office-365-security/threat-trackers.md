---
title: 'Suivis des menaces : nouveautés et remarques'
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: overview
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: a097f5ca-eac0-44a4-bbce-365f35b79ed1
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Découvrez les suivis des menaces, y compris les nouveaux suivis à prendre en compte, pour aider votre organisation à rester au fait des problèmes de sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a734085e9bc341424ee40757a21b855442605bcd
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50287388"
---
# <a name="threat-trackers---new-and-noteworthy"></a>Suivis des menaces : nouveautés et remarques

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

Les fonctionnalités d’examen et de réponse aux menaces [Office 365](office-365-ti.md) permettent à l’équipe de sécurité de votre organisation de découvrir et de prendre des mesures contre les menaces de cybersécurité. Les fonctionnalités d’examen et de réponse aux menaces Office 365 incluent des fonctionnalités de suivi des menaces, notamment des suivis à noter. Lisez cet article pour obtenir une vue d’ensemble de ces nouvelles fonctionnalités et des étapes suivantes.

> [!IMPORTANT]
> Office 365 Threat Intelligence est désormais Microsoft Defender pour Office 365 Plan 2, ainsi que des fonctionnalités de protection contre les menaces supplémentaires. Pour en savoir plus, consultez les plans et tarifs de Microsoft Defender pour [Office 365,](https://products.office.com/exchange/advance-threat-protection) ainsi que la description du [service Microsoft Defender pour Office 365.](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)

## <a name="what-are-threat-trackers"></a>Que sont les suivis des menaces ?

Les suivis des menaces sont des widgets et des vues informatifs qui vous fournissent des renseignements sur différents problèmes de cybersécurité qui peuvent avoir un impact sur votre entreprise. Par exemple, vous pouvez afficher des informations sur les tendances des campagnes anti-programme malveillant à l’aide des suivis des menaces.

![Exemple de suivi des menaces affichant les campagnes anti-programme malveillant](../../media/a883b5ac-8e2b-469a-90e0-f8ad39bb63b7.png)

La plupart des pages de suivi incluent des numéros de tendance mis à jour régulièrement, des widgets pour vous aider à comprendre les problèmes les plus importants ou les plus importants, ainsi qu’un lien rapide dans la colonne **Actions** qui vous permet d’afficher des informations plus détaillées.

![Exemple d’informations de campagne dans l’Explorateur](../../media/e426f220-fdcb-4dd9-99a2-db97dbcf71d5.png)

Les suivis ne sont que quelques-unes des nombreuses fonctionnalités intéressantes que vous obtenez [avec Microsoft Defender pour Office 365 Plan 2.](office-365-ti.md) Les suivis des menaces incluent [des suivis notables,](#noteworthy-trackers) [des suivis](#trending-trackers)de [tendance,](#tracked-queries)des requêtes suivis et des [requêtes enregistrées.](#saved-queries)

Pour afficher et utiliser vos suivis des menaces pour votre organisation, go to the Security & Compliance Center ( <https://protection.office.com> ) and choose Threat **management** \> **Threat Tracker**.

> [!NOTE]
> Pour utiliser les suivis des menaces, vous devez être administrateur général, administrateur de sécurité ou lecteur de sécurité. Voir [autorisations dans le Centre de sécurité & conformité.](permissions-in-the-security-and-compliance-center.md)

### <a name="noteworthy-trackers"></a>Suivis notables

Les suivis sont là où vous trouverez des menaces et des risques de taille et de taille moindre que nous pensons que vous devriez connaître. Les suivis notables vous aident à déterminer si ces problèmes existent dans votre environnement Microsoft 365, ainsi qu’un lien vers des articles (comme celui-ci) qui vous donnent plus de détails sur ce qui se passe et sur leur impact sur l’utilisation d’Office 365 par votre organisation. Qu’il s’agit d’une grande nouvelle menace (par exemple, Wannacry, Petya) ou d’une menace existante qui peut créer de nouveaux défis (comme notre autre élément important - Nemucod), c’est là que vous trouverez les nouveaux éléments importants que vous et votre équipe de sécurité devez examiner et examiner régulièrement.

En règle générale, des suivis notables sont publiés pendant quelques semaines seulement lorsque nous identifions les nouvelles menaces et pensons que vous aurez peut-être besoin de la visibilité supplémentaire que fournit cette fonctionnalité. Une fois que le risque le plus élevé pour une menace est passé, nous allons supprimer cet élément à noter. De cette façon, nous pouvons maintenir la liste à jour et à jour avec d’autres nouveaux éléments pertinents.

### <a name="trending-trackers"></a>Suivis des tendances

Les suivis de tendance (anciennement appelés campagnes) mettent en évidence les nouvelles menaces reçues dans le courrier électronique de votre organisation au cours de la semaine précédente.

![Exemple de widget de campagnes anti-programme malveillant à la tendance](../../media/d2ccc1a0-2a1d-4e36-99b5-6766c207772f.png)

Les suivis de tendance vous donnent une idée des nouvelles menaces que vous devez examiner pour vous assurer que votre environnement d’entreprise plus large est préparé contre les attaques.

### <a name="tracked-queries"></a>Requêtes de suivi

Les requêtes de suivi tirent parti de vos requêtes enregistrées pour évaluer régulièrement l’activité de Microsoft 365 dans votre organisation. Cela vous donne une tendance des événements, avec d’autres informations à venir dans les mois à venir. Le suivi des requêtes s’exécute automatiquement, ce qui vous donne des informations à jour sans avoir à vous souvenir de ré-exécuter vos requêtes.

![Exemple de requêtes de suivi avec une requête sélectionnée](../../media/0c556174-06eb-4ae5-b32a-5ff76b9e4f13.png)

### <a name="saved-queries"></a>Requêtes enregistrées

Les requêtes enregistrées se trouvent également dans la section Suivis. Vous pouvez utiliser des requêtes enregistrées pour stocker les recherches courantes dans l’Explorateur que vous souhaitez revenir plus rapidement et à plusieurs reprises, sans avoir à re-créer la recherche à chaque fois.

![Exemple de requêtes enregistrées avec une requête sélectionnée](../../media/188cf3ff-58f1-41ea-81aa-76158d8f40c3.png)

Vous pouvez toujours enregistrer une requête de suivi à noter  ou l’une de vos propres requêtes Explorer à l’aide du bouton Enregistrer la requête en haut de la page De l’Explorateur. Tout ce qui est enregistré s’affiche dans la liste des requêtes **enregistrées** sur la page Suivi.

## <a name="trackers-and-explorer"></a>Suivis et Explorateur

Que vous examinez le courrier électronique, le contenu ou les activités d’Office (bientôt disponible), l’Explorateur et les suivis fonctionnent ensemble pour vous aider à examiner et à suivre les risques et menaces de sécurité. Ensemble, les suivis vous fournissent des informations pour protéger vos utilisateurs en mettant en évidence les problèmes nouveaux, notables et fréquemment recherchés, ce qui garantit que votre entreprise est mieux protégée lors de son déplacement vers le cloud.

N’oubliez pas que vous pouvez toujours nous faire part de vos  commentaires sur cette fonctionnalité ou sur d’autres fonctionnalités de sécurité Microsoft 365 en cliquant sur le bouton Commentaires dans le coin inférieur droit de la vue d’ensemble du Centre de sécurité [&](https://support.microsoft.com/office/a5f2fd18-b029-4257-b5a8-ae83e7768c85)conformité.

![Centre de sécurité et de conformité](../../media/86c330db-8132-4150-8475-220258fe04fb.png)

## <a name="trackers-and-microsoft-defender-for-office-365"></a>Suivis et Microsoft Defender pour Office 365

Avec notre menace importante, nous allons mettre en évidence les menaces de programmes malveillants avancées détectées par les [pièces jointes sécurisées.](atp-safe-attachments.md) Si vous êtes un client Office 365 Entreprise E5 et que vous n’utilisez pas Microsoft Defender pour [Office 365,](office-365-atp.md)vous devez l’être : il est inclus dans votre abonnement. Defender pour Office 365 offre une valeur ajoutée même si vous disposez d’autres outils de sécurité qui filtrent le flux de messagerie avec vos services Office 365. Toutefois, les [](atp-safe-links.md) fonctionnalités anti-courrier indésirable et liens sécurisés fonctionnent mieux lorsque votre solution de sécurité du courrier électronique principale est via Office 365.

![Microsoft Defender pour Office 365 dans le Centre de sécurité & conformité](../../media/cee70d07-f0c1-459b-843c-2d10c253349f.png)

Dans le monde actuel aux menaces, l’exécution des analyses anti-programme malveillant traditionnelles uniquement signifie que vous n’êtes pas suffisamment protégé contre les attaques. Aujourd’hui, les attaquants plus sophistiqués utilisent des outils couramment disponibles pour créer des attaques nouvelles, obscurcies ou retardées qui ne seront pas reconnues par les moteurs anti-programme malveillant basés sur les signatures traditionnels. La fonctionnalité Pièces jointes sécurisées prend les pièces jointes des e-mails et les détone dans un environnement virtuel pour déterminer s’ils sont sûrs ou malveillants. Ce processus de détonation ouvre chaque fichier dans un environnement d’ordinateur virtuel, puis surveille ce qui se produit après l’ouverture du fichier. Qu’il s’agit d’un fichier PDF et compressé, ou d’un document Office, du code malveillant peut être masqué dans un fichier, en l’activant uniquement une fois que la victime l’ouvre sur son ordinateur. En détonant et en analysant le fichier dans le flux de messagerie, les fonctionnalités de Defender pour Office 365 trouvent ces menaces en fonction des comportements, de la réputation des fichiers et d’un certain nombre de règles heuristiques.

Le nouveau filtre de menaces à noter met en évidence les éléments qui ont été récemment détectés par le biais de pièces jointes sécurisées. Ces détections représentent des éléments qui sont de nouveaux fichiers malveillants, qui n’ont pas été trouvés précédemment par Microsoft 365 dans votre flux de messagerie ou dans le courrier d’autres clients. Faites attention aux éléments du suivi des menaces à prendre en compte, consultez les personnes ciblées par ces derniers et examinez les détails de détonation affichés sous l’onglet Analyse avancée (en cliquant sur l’objet de l’e-mail dans l’Explorateur). Notez que vous trouverez cet onglet uniquement sur les e-mails détectés par la fonctionnalité Pièces jointes sécurisées . Ce suivi important inclut ce filtre, mais vous pouvez également utiliser ce filtre pour d’autres recherches dans l’Explorateur.

## <a name="next-steps"></a>Étapes suivantes

- Si votre organisation ne comprend pas déjà ces fonctionnalités d’examen et de réponse aux menaces Office 365, consultez comment obtenir les fonctionnalités d’Examen et de réponse aux [menaces Office 365 ?](office-365-ti.md)

- Assurez-vous que les rôles et autorisations corrects sont attribués à votre équipe de sécurité. Vous devez être administrateur général ou avoir le rôle Administrateur de la sécurité ou Recherche et purge attribué dans le Centre de sécurité & conformité. Voir [autorisations dans le Centre de sécurité & conformité.](permissions-in-the-security-and-compliance-center.md)

- Observez les nouveaux suivis à afficher dans votre environnement Microsoft 365. Si disponible, vous trouverez vos suivis [ici.](https://protection.office.com/) Allez aux **suivis des menaces de gestion** \> **des menaces.**

- Si vous ne l’avez pas déjà fait, découvrez et configurez Microsoft Defender [](atp-safe-links.md) pour [Office 365](office-365-atp.md) pour votre organisation, y compris les liens sécurisés et les pièces [jointes sécurisées.](atp-safe-attachments.md)
