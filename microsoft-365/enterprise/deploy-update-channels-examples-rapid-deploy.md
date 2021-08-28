---
title: Exemple de déploiement à grande échelle des dernières versions
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
ms.date: 07/21/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
ms.custom: ''
description: Découvrir comment une organisation qui déploie la dernière version utilise des canaux pour les applications Windows 10 et Microsoft 365.
ms.openlocfilehash: 025f6976fd578af4bf0c9a0c268f046f72ef6901
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58561085"
---
# <a name="example-of-broad-deployment-for-the-latest-releases"></a>Exemple de déploiement à grande échelle des dernières versions

Cet exemple de configuration de canal est destiné à une organisation qui utilise le déploiement rapide des dernières versions pour s’adapter aux priorités de l’entreprise :

- Assurez la continuité de l’activité grâce aux applications et services Microsoft.
- Optimisez la sécurité des appareils, services et données grâce aux derniers correctifs et fonctionnalités de Microsoft.
- Optimisez la productivité des utilisateurs grâce aux dernières fonctionnalités de Microsoft.

Ces objectifs convertissent la tâche informatique qui permet de trouver l’équilibre entre un déploiement rapide de production et un contrôle précoce avec un sous-ensemble représentatif d’utilisateurs et d’appareils pour valider les fonctionnalités avant un déploiement à grande échelle.

Notre exemple d’organisation compte 5 000 employés dans des bâtiments du monde entier en Europe, en Afrique, en Asie et en Amérique. 70 % des employés utilisent Microsoft 365 E3 et le reste de l’organisation utilise Microsoft 365 E5.

>[!Note]
>Cet exemple vous montre comment utiliser les étapes et groupes de déploiement, ce qui peut fonctionner pour les organisations de plusieurs types et tailles.
>

Cette infrastructure informatique de l’organisation : 

- Est largement homogène, avec Windows, les applications Microsoft 365 et les services Cloud de Microsoft qui incluent 60 % de la base installée. Certains systèmes existants subsistent après un effort intensif de plusieurs années pour simplifier et rationaliser l’infrastructure informatique.
- Est gérée par un personnel très expérimenté et chargé de maintenir la productivité et la sécurité des utilisateurs et de leurs appareils en suivant les versions de Microsoft.

## <a name="deployment-and-update-stages"></a>Phases de déploiement et de mise à jour

Dans le cadre des objectifs de déploiement rapide de la dernière version, cet exemple d’organisation utilise un processus de déploiement en deux étapes.

1. **Utilisez une préversion ou un déploiement pilote :** valider et faire des itérations avec les premiers utilisateurs, le personnel informatique, les utilisateurs ayant des configurations représentatives et le personnel de formation. 

   Les premiers utilisateurs, le personnel informatique, les utilisateurs ayant des configurations représentatives peuvent valider les fonctionnalités avec d’autres applications et sur des appareils avant que les nouvelles fonctionnalités soient déployées vers le reste de l’organisation.

   Les responsables des modifications ont un aperçu des nouvelles fonctionnalités avant leur déploiement généralisé et peuvent planifier leur messagerie et leur déploiement.

   Le personnel de formation peut planifier de nouveaux cours internes ou mettre à jour des cours existants pour les nouvelles fonctionnalités avant leur déploiement généralisé.

2. **Déploiement en production :** déployez vers tous les utilisateurs restants par région, service ou autre méthode de déploiement.

## <a name="deployment-configuration-for-windows-10"></a>Configuration de déploiement pour Windows 10

L’objectif global est d’effectuer un déploiement à grande échelle de la dernière version du Canal semi-annuel après la validation des modifications du Canal de la version préliminaire par un groupe d’utilisateurs représentatifs et leurs appareils.

Pour plus d’informations sur les méthodes et stratégies de déploiement de Windows 10, consultez la rubrique [Déploiement de Windows 10](/windows/deployment/).

| Phase | Canal | Groupe de déploiement |
|:-------|:-------|:-----|
| Pilote |  **Canal de la version préliminaire**  <ul><li>Objectif : déploiement de mises à jour de fonctionnalités auprès du personnel informatique et des utilisateurs précoces pour la validation sur les appareils et configurations représentatifs (langues, applications tierces). </li><li> État : entièrement conforme et pris en charge pour les clients commerciaux et qui ne sont pas pris en compte dans vos contrats de support. </li></ul> | **Win10ReleasePreviewChannel** (exemple de nom) <br><br> Les membres sont des groupes contenant : <ul><li> Passionnés de Windows dans tous les services et emplacements </li><li> Personnel avec des configurations nécessitant une validation </li><li> Administrateurs informatiques et personnel de déploiement informatique </li><li> Responsables des modifications </li><li> Personnel de formation interne </li></ul> |
| Production |  **Canal semi-annuel**  <ul><li>Objectif : déploiement à grande échelle des dernières mises à jour des fonctionnalités auprès du reste de l’organisation. </li><li> État : entièrement conforme et pris en charge. </li></ul> | **Win10SemiAnnualChannel** (exemple de nom) <br><br> Les membres sont tous les utilisateurs qui ne figurent pas dans le groupe Win10ReleasePreviewChannel. |
||||

Cette organisation utilise la meilleure pratique consistant à déployer la charge utile du Canal de la version préliminaire de la même manière qu’elle déploie les versions du Canal semi-annuel (par exemple, Windows Update ou Windows Server Update Services) et qu’elle applique les mêmes stratégies pour les deux mises à jour de canal.

Processus de mises à jour en cours :

1. Les modifications apportées au Canal de la version préliminaire sont déployées dans le groupe de déploiement Win10ReleasePreviewChannel (exemple de nom).
2. Les membres du groupe Win10ReleasePreviewChannel confirment que les modifications du Canal de la version préliminaire fonctionnent auprès du personnel de déploiement informatique, qui peut transmettre ses commentaires à Microsoft et attendre les prochaines modifications du Canal de la version préliminaire pour une validation supplémentaire.
3. Les modifications des fonctionnalités du Canal semi-annuel sont déployées dans le groupe déploiement Win10SemiAnnualChannel. 

>[!Note]
>Bien que le canal semi-annuel soit le canal recommandé, votre service informatique doit utiliser ses outils de gestion et déterminer le moment où déployer la dernière version de canal semi-annuel au sein de son organisation, puis la déployer sous la forme de vagues.
>

## <a name="deployment-configuration-for-microsoft-365-apps"></a>Configuration de déploiement pour les applications Microsoft 365

L’objectif global est d’effectuer un déploiement à grande échelle de la dernière version de canal actuel après la validation des modifications du Canal actuel (préversion) par un groupe d’utilisateurs représentatifs.

Si vous souhaitez en savoir plus sur les stratégies et méthodes de déploiement des applications Microsoft 365, veuillez consulter la rubrique [Déploiement d’applications Microsoft 365](/deployoffice/plan-office-365-proplus).

| Phase | Canal | Groupe de déploiement |
|:-------|:-------|:-----|
| Pilote |  **Canal actuel (préversion)** <ul><li> Objectif : {donner à un groupe d’utilisateurs représentatifs un aperçu des nouvelles fonctionnalités des applications Microsoft 365} Déploiement de mises à jour de fonctionnalités dès qu’elles sont testées avec les utilisateurs du Canal actuel (préversion) et prêtes pour la production. </li><li> État : entièrement conforme et pris en charge.</li><li> Fréquence : mise à jour de 2 à 3 fois par mois. </li></ul> | **AppsCurrentChannelPreview** (exemple de nom) <br><br> Les membres sont des groupes contenant : <ul><li> Les applications Office enthousiastes au sein des différents services et emplacements </li><li> Personnel avec des configurations nécessitant une validation </li><li> Administrateurs informatiques et personnel de déploiement informatique </li><li> Responsables des modifications </li><li> Personnel de formation interne </li></ul>|
| Production | **Canal Actuel** <ul><li> Objectif : déploiement à grande échelle des dernières mises à jour des fonctionnalités auprès du reste de l’organisation. </li><li> État : entièrement conforme et pris en charge. </li></ul> |  **AppsCurrentChannel** (exemple de nom) <br><br> Les membres sont tous les utilisateurs qui ne figurent pas dans le groupe AppsCurrentChannelPreview. |
|||

Processus de mises à jour en cours :

1. Les modifications du Canal actuel (préversion) sont déployées dans le groupe de déploiement AppsCurrentChannelPreview.
2. Les membres du groupe AppsCurrentChannelPreview confirment que les modifications du Canal actuel (préversion) fonctionnent auprès du personnel de déploiement informatique, qui peut transmettre ses commentaires à Microsoft et attendre la prochaine version du Canal actuel (préversion) pour une validation supplémentaire.
3. Les modifications du Canal actuel sont déployées dans le groupe de déploiement AppsCurrentChannel. 

## <a name="visual-summary"></a>Résumé visuel

Voici les produits, leurs canaux et les groupes de déploiement utilisés par cet exemple d’organisation. 

![Groupes de déploiement pour le déploiement à grande échelle des dernières mises à jour.](../media/deploy-update-channels-examples-rapid-deploy/group-summary.png)

## <a name="see-also"></a>Voir aussi

[Exemple de configurations de canal de mise à jour et de déploiement](deploy-update-channels-examples.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)