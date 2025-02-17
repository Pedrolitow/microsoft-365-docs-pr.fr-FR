---
title: Connecteurs de Plannings
author: lanachin
ms.author: v-lanachin
ms.reviewer: aaku
manager: samanro
ms.topic: conceptual
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Découvrez les connecteurs Plannings et comment les utiliser pour connecter Plannings votre système de gestion de la main-d’œuvre.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
- highpri
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 0a84f78dead461069a45c3b0cd4e19c2c024fd66
ms.sourcegitcommit: 0ad7edcfdcdd11d02fa8a14ffe4b36e120d92deb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2022
ms.locfileid: "68786714"
---
# <a name="shifts-connectors"></a>Connecteurs de Plannings

## <a name="overview"></a>Vue d’ensemble

Les connecteurs Plannings vous permettent d’intégrer Plannings, l’outil de gestion des planifications dans Microsoft Teams, à votre système de gestion du personnel (WFM). Une fois la connexion établie, vos employés de première ligne peuvent afficher et gérer leurs horaires de manière transparente dans Blue Yonder WFM à partir de Plannings.

La connexion de votre système de WFM à Teams permet à votre personnel de première ligne de gérer les planifications plus efficacement et simplifie les processus quotidiens pour accroître l’engagement et la productivité. Vos employés de première ligne disposent d’un emplacement unique pour leurs besoins de planification, de communication et de collaboration pour accomplir leurs tâches, où que vous soyez, sur n’importe quel appareil.

Cet article vous donne une vue d’ensemble des connecteurs Plannings et de leur fonctionnement.

## <a name="how-shifts-connectors-work"></a>Fonctionnement des connecteurs Plannings

Les connecteurs synchronisent les données de planification entre votre système WFM et Plannings, en intégrant les planifications de votre organisation dans Teams. Les équipes sont l’endroit où vos employés de première ligne s’engagent pour leurs besoins en matière de planification. Votre système de WFM est le système d’enregistrement pour les règles d’entreprise, la conformité et l’intelligence.

Les flux de données via le connecteur permettent de s’assurer que les planifications sont toujours à jour. Les planifications de votre système WFM sont synchronisées avec Plannings. De plus, les modifications apportées aux planifications dans Shifts sont resynchronisées avec votre système WFM. En tant que système d’enregistrement, toutes les règles d’entreprise sont appliquées par votre système WFM avant l’enregistrement des données dans Plannings.

<a name="prereq"> </a>
<a name="schedules"> </a>
## <a name="managed-shifts-connectors"></a>Connecteurs Plannings managés

Les connecteurs Plannings managés sont des connecteurs développés en collaboration avec nos partenaires. Les connecteurs managés sont hébergés et gérés par nous ou nos partenaires. Avec les connecteurs managés, seule une configuration minimale est nécessaire.

|Connector|Description|Conditions requises|
|---------|---------|---------|
|[Connecteur Microsoft Teams Plannings pour Blue Yonder](#microsoft-teams-shifts-connector-for-blue-yonder)|Utilisez ce connecteur pour intégrer Shifts à Blue Yonder Workforce Management. Ce connecteur est hébergé et géré par Microsoft.|Conditions préalables à la configuration d’une connexion : <ul><li>Utilisation de [l’Assistant Connecteur Shifts](shifts-connector-wizard.md#prerequisites) dans le Centre d'administration Microsoft 365<br>Avant d’exécuter l’Assistant, [supprimez les planifications des équipes existantes que vous souhaitez mapper](shifts-connector-wizard.md#remove-schedules-from-teams-you-want-to-map).</li><li>Utilisation de [PowerShell](shifts-connector-blue-yonder-powershell-setup.md#prerequisites)</li></ul>|
|[Connecteur Microsoft Teams Shifts pour les dimensions UKG](#microsoft-teams-shifts-connector-for-ukg-dimensions)|Utilisez ce connecteur pour intégrer Shifts à UKG Dimensions. Ce connecteur est hébergé et géré par Microsoft.|Conditions préalables à la configuration d’une connexion : <ul><li>Utilisation de [l’Assistant Connecteur Shifts](shifts-connector-wizard-ukg.md#prerequisites) dans le Centre d'administration Microsoft 365<br>Avant d’exécuter l’Assistant, [supprimez les planifications des équipes existantes que vous souhaitez mapper](shifts-connector-wizard-ukg.md#remove-schedules-from-teams-you-want-to-map)</li><li>Utilisation de [PowerShell](shifts-connector-ukg-powershell-setup.md#prerequisites)</li></ul>|
|[Connecteur Reflexis Plannings pour Microsoft Teams](#reflexis-shifts-connector-for-microsoft-teams)|Utilisez ce connecteur pour intégrer Shifts à Reflexis Workforce Scheduler. Ce connecteur est hébergé et géré par Zebra. |Pour plus d'informations, accédez au <https://connect.zebra.com/microsoft-connectors>.|

<a name="blue_yonder"> </a>
### <a name="microsoft-teams-shifts-connector-for-blue-yonder"></a>Connecteur Microsoft Teams Plannings pour Blue Yonder

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

Alex doit prendre un peu de congé et demande un jour de congé à l’aide de Plannings. La demande est envoyée à Blue Yonder WFM via le connecteur. Blue Yonder WFM garantit que la demande est conforme aux règles d’entreprise et que la demande est créée. Eden voit et approuve la demande dans Blue Yonder WFM, et l’approbation est synchronisée avec Teams. (Eden peut également voir et approuver la demande dans Plannings). Alex est informé dans Teams que sa demande est approuvée et affiche son calendrier mis à jour.

Alex veut échanger un shift avec un collègue. Dans Shifts, Alex voit une liste de tous les shifts qui sont éligibles à un échange en fonction des règles d’entreprise dans Blue Yonder WFM. Alex choisit un shift actuellement attribué à Gena. Gena est averti dans Teams sur son appareil mobile et accepte la demande d’échange. Eden voit et approuve la demande dans Plannings, et l’approbation est synchronisée avec Blue Yonder WFM. (Eden peut également voir et approuver la demande dans Blue Yonder WFM). Alex et Gena sont avertis dans Teams et affichent leurs planifications mises à jour.

#### <a name="set-up-a-connection-to-blue-yonder-workforce-management"></a>Configurer une connexion à Blue Yonder Workforce Management

L’intégration de Plannings à Blue Yonder WFM à l’aide du connecteur ne prend que quelques étapes. Vous pouvez utiliser l’Assistant Connecteur Plannings dans le Centre d'administration Microsoft 365 pour configurer rapidement une connexion. L’Assistant configure le connecteur en fonction des paramètres que vous choisissez et crée la connexion. Si vous préférez utiliser PowerShell, nous fournissons également des scripts PowerShell que vous pouvez utiliser pour vous connecter.

Pour obtenir des conseils pas à pas, consultez :

- [Utiliser l’Assistant Connecteur Plannings pour connecter Plannings à Blue Yonder Workforce Management](shifts-connector-wizard.md)
- [Utiliser PowerShell pour connecter Shifts à Blue Yonder Workforce Management](shifts-connector-blue-yonder-powershell-setup.md)

Une fois qu’une connexion est configurée, vous pouvez mettre à jour et modifier les paramètres de connexion à tout moment, en fonction des besoins. Pour en savoir plus, reportez-vous à la rubrique :

- [Utilisez le Centre d'administration Microsoft 365 pour gérer votre connexion Shifts à Blue Yonder Workforce Management](shifts-connector-blue-yonder-admin-center-manage.md)
- [Utilisez PowerShell pour gérer votre connexion Shifts à Blue Yonder Workforce Management](shifts-connector-powershell-manage.md)

En ce qui concerne le connecteur lui-même, vous n’avez pas besoin de vous soucier des mises à niveau ou de la maintenance. On s’en occupe.

### <a name="microsoft-teams-shifts-connector-for-ukg-dimensions"></a>Connecteur Microsoft Teams Shifts pour les dimensions UKG

[!INCLUDE [preview-feature](includes/preview-feature.md)]

Le connecteur Teams Shifts pour UKG Dimensions est une offre interne hébergée et gérée par Microsoft. Avec ce connecteur, vous pouvez intégrer Shifts à UKG Dimensions pour gérer vos planifications et les tenir à jour.  

:::image type="content" source="media/shifts-connector-ukg-dimensions.png" alt-text="Capture d’écran montrant shifts sur un appareil mobile, une demande de congé et une planification dans UKG Dimensions." lightbox="media/shifts-connector-ukg-dimensions.png":::

Les responsables de première ligne peuvent :

- Publiez des shifts et des planifications dans les dimensions UKG et affichez-les dans Shifts.
- Créez, affichez, gérez et affectez des shifts ouverts dans ukG Dimensions and Shifts sur le bureau Teams et l’application web Teams. (Actuellement, les responsables ne peuvent pas afficher ou affecter des équipes ouvertes dans Shifts sur les appareils mobiles Teams.)
- Créez, modifiez et supprimez des congés dans les dimensions UKG et affichez-les dans Shifts.
- Affichez et approuvez les demandes de planification des travailleurs dans ukg Dimensions et Shifts.
- Définissez et mettez à jour la disponibilité des workers dans les dimensions UKG et affichez dans Shifts.

Les travailleurs de première ligne peuvent :

- Consulter les horaires et les horaires de leur équipe et de leur équipe dans Plannings;
- Demandez un congé, affichez les informations sur les congés et affichez les shifts ouverts de leur équipe dans Shifts.
- Affichez et publiez les entrées de carte de temps dans Shifts.
- Demandez des shifts ouverts et échangez des shifts dans Shifts.
- Définissez leur disponibilité dans Shifts sur teams mobile.

Les éléments suivants ne sont pas pris en charge actuellement :

- Ajouter, modifier, supprimer, enregistrer ou publier des décalages dans Plannings;
- Ajouter, modifier, supprimer, enregistrer ou publier des congés dans Plannings;
- Ajouter, modifier, supprimer, enregistrer ou publier des décalages ouverts dans Plannings.

Lorsqu’un responsable ou un travailleur de première ligne tente d’effectuer l’une de ces actions dans Plannings, il reçoit un message lui indiquant que l’action n’est pas prise en charge.

#### <a name="example-scenario"></a>Exemple de scénario

Ravi, un responsable, publie une planification dans UKG Dimensions, qui est synchronisée avec Shifts dans Teams via le connecteur. Camille, membre du personnel, est avertie dans Teams sur son appareil mobile et consulte son planning et l’horaire de son équipe. Dans les équipes affectées, Camille peut également voir des informations détaillées, telles que les tâches, définies par le responsable.

Camille a besoin de prendre un certain temps de congé et demande un jour de congé à l’aide de Shifts. La demande est envoyée à UKG Dimensions via le connecteur. UKG Dimensions garantit que la demande est conforme aux règles d’entreprise et que la demande est créée. Ravi voit et approuve la demande dans UKG Dimensions, et l’approbation est synchronisée avec Teams. (Ravi peut également voir et approuver la demande dans Shifts). Camille est avertie dans Teams que la demande est approuvée et affiche sa planification mise à jour.

Camille veut échanger un quart de travail avec un collègue. Dans Shifts, Camille voit une liste de tous les shifts éligibles pour un échange basé sur les règles d’entreprise dans UKG Dimensions. Camille choisit un quart de travail qui est actuellement affecté à Kristen. Kristen est avertie dans Teams sur son appareil mobile et accepte la demande d’échange. Ravi voit et approuve la demande dans Shifts, et l’approbation est synchronisée avec UKG Dimensions. (Ravi peut également voir et approuver la demande dans dimensions UKG). Camille et Kristen sont avertis dans Teams et affichent leurs plannings mis à jour.

#### <a name="set-up-a-connection-to-ukg-dimensions"></a>Configurer une connexion à UKG Dimensions

L’intégration de Shifts à UKG Dimensions à l’aide du connecteur ne nécessite que quelques étapes. Vous pouvez utiliser l’Assistant Connecteur Plannings dans le Centre d'administration Microsoft 365 pour configurer rapidement une connexion. L’Assistant configure le connecteur en fonction des paramètres que vous choisissez et crée la connexion. Si vous préférez utiliser PowerShell, nous fournissons également des scripts PowerShell que vous pouvez utiliser pour vous connecter.

Pour obtenir des conseils pas à pas, consultez :

- [Utiliser l’Assistant Connecteur Shifts pour connecter Shifts à UKG Dimensions](shifts-connector-wizard-ukg.md)
- [Utiliser PowerShell pour connecter Shifts à UKG Dimensions](shifts-connector-ukg-powershell-setup.md)

Une fois qu’une connexion est configurée, vous pouvez mettre à jour et modifier les paramètres de connexion à tout moment, en fonction des besoins. Pour en savoir plus, reportez-vous à la rubrique :

- [Utilisez le Centre d'administration Microsoft 365 pour gérer votre connexion Shifts aux dimensions UKG](shifts-connector-ukg-admin-center-manage.md)
- [Utiliser PowerShell pour gérer votre connexion Shifts aux dimensions UKG](shifts-connector-ukg-powershell-manage.md)

En ce qui concerne le connecteur lui-même, vous n’avez pas besoin de vous soucier des mises à niveau ou de la maintenance. On s’en occupe.

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

Pour plus d'informations, accédez au <https://connect.zebra.com/microsoft-connectors>.

## <a name="related-articles"></a>Articles connexes

- [Gérer l’application Shifts](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
