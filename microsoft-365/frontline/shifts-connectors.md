---
title: Connecteurs de Plannings
author: lanachin
ms.author: v-lanachin
ms.reviewer: aaku
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Découvrez les connecteurs Plannings et comment les utiliser pour connecter Plannings votre système de gestion de la main-d’œuvre.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: c211e066a1b5c6ad610c2f3be703d50be3ecf6af
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2022
ms.locfileid: "66992309"
---
# <a name="shifts-connectors"></a>Connecteurs de Plannings

## <a name="overview"></a>Vue d’ensemble

Les connecteurs Plannings vous permettent d’intégrer Plannings, l’outil de gestion des planifications dans Microsoft Teams, à votre système de gestion du personnel (WFM). Une fois la connexion établie, vos employés de première ligne peuvent afficher et gérer leurs horaires de manière transparente dans Blue Yonder WFM à partir de Plannings.

La connexion de votre système de WFM à Teams permet à votre personnel de première ligne de gérer les planifications plus efficacement et simplifie les processus quotidiens pour accroître l’engagement et la productivité. Vos employés de première ligne disposent d’un emplacement unique pour leurs besoins de planification, de communication et de collaboration pour accomplir leurs tâches, où que vous soyez, sur n’importe quel appareil.

Cet article vous donne une vue d’ensemble des connecteurs Plannings et de leur fonctionnement.

## <a name="how-shifts-connectors-work"></a>Fonctionnement des connecteurs Plannings

Les connecteurs synchronisent les données de planification entre votre système WFM et Plannings, en intégrant les planifications de votre organisation dans Teams. Les équipes sont l’endroit où vos employés de première ligne s’engagent pour leurs besoins en matière de planification. Votre système de WFM est le système d’enregistrement pour les règles d’entreprise, la conformité et l’intelligence.

Les flux de données via le connecteur permettent de s’assurer que les planifications sont toujours à jour. Les planifications de votre système WFM sont synchronisées avec Plannings. De plus, les modifications apportées aux planifications dans Plannings sont synchronisées avec votre système WFM en temps réel. En tant que système d’enregistrement, toutes les règles d’entreprise sont appliquées par votre système WFM avant l’enregistrement des données dans Plannings.

## <a name="managed-shifts-connectors"></a>Connecteurs Plannings managés

Les connecteurs Plannings managés sont des connecteurs développés en collaboration avec nos partenaires. Les connecteurs managés sont hébergés et gérés par nous ou nos partenaires. Avec les connecteurs managés, seule une configuration minimale est nécessaire.

### <a name="microsoft-teams-shifts-connector-for-blue-yonder"></a>Connecteur Microsoft Teams Plannings pour Blue Yonder
<a name="blue_yonder"> </a>

Le connecteur Teams Plannings pour Blue Yonder est une offre interne hébergée et gérée par Microsoft Corporation. Avec ce connecteur, vous pouvez intégrer Plannings à Blue Yonder Workforce Management (Blue Yonder WFM) versions 2020.3, 2021.1 ou 2021.2 pour gérer vos planifications et les tenir à jour.  

> [!NOTE]
> Si vous disposez de l'URL Blue Yonder WFM 2020.3 ou 2021.1, appliquez le correctif 2020.3.0.4 ou 2021.1.0.3. Ce correctif résout un problème où les utilisateurs reçoivent un message d'erreur persistant dans Shifts. Il résout également un problème qui empêche les utilisateurs de mettre à jour leur disponibilité dans Plannings.

:::image type="content" source="media/shifts-connector-blue-yonder.png" alt-text="Capture d’écran montrant une demande d’échange dans Planning sur un appareil mobile, une demande d’approbation dans Teams sur le bureau et une planification dans Blue Yonder WFM" lightbox="media/shifts-connector-blue-yonder.png":::

Les responsables de première ligne peuvent :

- Publier des décalages et des planifications dans blue Yonder WFM et les afficher dans Plannings;
- Créer, gérer et attribuer des décalages ouverts dans blue Yonder WFM et les afficher dans Plannings;
- Attribuer des décalages ouverts qui ont été créés dans blue Yonder WFM dans Plannings;
- Créer, modifier et supprimer des congés dans Blue Yonder WFM et les afficher dans Plannings;
- Afficher et approuver les demandes de planification des travailleurs dans blue Yonder WFM et Plannings;
- Définir et mettre à jour la disponibilité des workers dans blue Yonder WFM et les afficher dans Plannings.

Les travailleurs de première ligne peuvent :

- Consulter les horaires et les horaires de leur équipe et de leur équipe dans Plannings;
- Demander un congé, ouvrir et échanger des shifts dans Plannings;
- Définir leur disponibilité dans Plannings.

Les éléments suivants ne sont pas pris en charge actuellement :

- Ajouter, modifier, supprimer, enregistrer ou publier des décalages dans Plannings;
- Ajouter, modifier, supprimer, enregistrer ou publier des congés dans Plannings;
- Ajouter, modifier, supprimer, enregistrer ou publier des décalages ouverts dans Plannings.

Lorsqu’un responsable ou un travailleur de première ligne tente d’effectuer l’une de ces actions dans Plannings, il reçoit un message lui indiquant que l’action n’est pas prise en charge.

#### <a name="example-scenario"></a>Exemple de scénario

Eden, un responsable, publie une planification dans Blue Yonder WFM, qui est synchronisée avec Plannings dans Teams via le connecteur. Alex, un membre du personnel, est averti dans Teams sur son appareil mobile, et affiche son horaire et les équipes attribuées.

Alex doit prendre un peu de congé et demande un jour de congé à l’aide de Plannings. La demande est envoyée à Blue Yonder WFM via le connecteur en temps réel. Blue Yonder WFM garantit que la demande est conforme aux règles d’entreprise et que la demande est créée. Eden voit et approuve la demande dans Blue Yonder WFM, et l’approbation est synchronisée avec Teams. (Eden peut également voir et approuver la demande dans Plannings). Alex est informé dans Teams que sa demande est approuvée et affiche son calendrier mis à jour.

Alex veut échanger un shift avec un collègue. Dans Shifts, Alex voit une liste de tous les shifts qui sont éligibles à un échange en fonction des règles d’entreprise dans Blue Yonder WFM. Alex choisit un shift actuellement attribué à Gena. Gena est averti dans Teams sur son appareil mobile et accepte la demande d’échange. Eden voit et approuve la demande dans Plannings, et l’approbation est synchronisée avec Blue Yonder WFM. (Eden peut également voir et approuver la demande dans Blue Yonder WFM). Alex et Gena sont avertis dans Teams et affichent leurs planifications mises à jour.

#### <a name="set-up-a-connection"></a>Configurer une connexion

L’intégration de Plannings à Blue Yonder WFM à l’aide du connecteur ne prend que quelques étapes. Vous pouvez utiliser l’Assistant Connecteur Plannings dans le Centre d'administration Microsoft 365 pour configurer rapidement une connexion. L’Assistant configure le connecteur en fonction des paramètres que vous choisissez et crée la connexion. Si vous préférez utiliser PowerShell, nous fournissons également des scripts PowerShell que vous pouvez utiliser pour vous connecter.

Pour obtenir des conseils pas à pas, consultez :

- [Utiliser l’Assistant Connecteur Plannings pour connecter Plannings à Blue Yonder Workforce Management](shifts-connector-wizard.md)
- [Utiliser PowerShell pour connecter Shifts à Blue Yonder Workforce Management](shifts-connector-blue-yonder-powershell-setup.md)

Une fois la connexion configurée, vous pouvez utiliser PowerShell pour mettre à jour et modifier les paramètres de connexion à tout moment, si nécessaire. En ce qui concerne le connecteur lui-même, vous n’avez pas besoin de vous soucier des mises à niveau ou de la maintenance. On s’en occupe.

### <a name="reflexis-shifts-connector-for-microsoft-teams"></a>Connecteur Reflexis Plannings pour Microsoft Teams

Le connecteur Reflexis Plannings pour Microsoft Teams est hébergé et géré par Zebra. Avec ce connecteur, vous pouvez intégrer Plannings au système Reflexis WFM pour gérer vos planifications et les tenir à jour.

Les employés de première ligne ont accès à leur horaire dans Planning in Teams, et leurs demandes sont synchronisées entre Plannings et Reflexis Workforce Scheduler (RWS). L’état des demandes et des décalages créés dans RWS est synchronisé avec Shifts dans Teams.

:::image type="content" source="media/shifts-connector-reflexis.png" alt-text="Capture d’écran montrant la liste des décalages sur un appareil mobile et une planification dans Reflexis" lightbox="media/shifts-connector-reflexis.png":::

Les responsables de première ligne peuvent :

- Publier des décalages et des planifications dans Reflexis et les afficher dans Plannings;
- Modifier les décalages dans reflexis et Plannings;
- Créer, gérer et attribuer des décalages ouverts dans Reflexis et Plannings;
- Afficher et approuver les demandes de planification des travailleurs dans Reflexis et Plannings.

Les travailleurs de première ligne peuvent :

- Consulter les horaires et les horaires de leur équipe et de leur équipe dans Plannings;
- Demander un congé, ouvrir des équipes, échanger et proposer des changements dans Plannings.

Pour plus d'informations, accédez au https://connect.zebra.com/microsoft-connectors.

## <a name="related-articles"></a>Articles connexes

- [Gérer l’application Shifts](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
