---
title: Archiver des données de la plateforme CellTrust SL2 vers Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Découvrez comment configurer et utiliser un connecteur de données CellTrust SL2 pour importer et archiver des données de communications mobiles.
ms.openlocfilehash: 8c31f349f25702e88a260025ef69475f44f96a0e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624706"
---
# <a name="archive-data-from-celltrust-sl2-to-microsoft-365"></a>Archiver des données de CellTrust SL2 vers Microsoft 365

CellTrust SL2 capture les données de communications mobiles et s’intègre aux technologies d’archivage de pointe pour répondre aux exigences de découverte électronique pour les réglementations telles que FINRA, HIPAA, FOIA et TCPA. Le connecteur de données SL2 importe des éléments de communication mobile vers Microsoft 365. Cet article décrit le processus d’intégration de SL2 à Microsoft 365 à l’aide du connecteur de données CellTrust SL2 pour l’archivage. L’exécution de ce processus suppose que vous êtes abonné au service CellTrust SL2 et que vous êtes familiarisé avec l’architecture SL2. Pour plus d’informations sur CellTrust SL2, consultez <https://www.celltrust.com>.

Une fois les données importées dans les boîtes aux lettres des utilisateurs dans Microsoft 365, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation des litiges, eDiscovery, les stratégies de rétention Microsoft 365 et la conformité des communications. L’utilisation du connecteur de données CellTrust SL2 pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-with-the-celltrust-sl2-data-connector"></a>Vue d’ensemble de l’archivage avec le connecteur de données CellTrust SL2

La plateforme SL2 de CellTrust capture les données de communication provenant de plusieurs sources. Les sources de données SL2 sont de personne à personne (P2P) ou d’application à personne (A2P). Le processus décrit dans cet article concerne uniquement les sources de données P2P. Pour toutes les sources de données P2P, au moins une partie de la collaboration est un utilisateur SL2 abonné au service SL2. La vue d’ensemble suivante explique le processus d’utilisation du connecteur de données CellTrust SL2 dans Microsoft 365.

![Flux de travail d’archivage pour le service CellTrust SL2.](../media/CellTrustSL2ConnectorWorkflow.png)

1. Les utilisateurs SL2 envoient et reçoivent des données vers et depuis des services SL2 dans Microsoft Azure.

2. Votre organisation dispose d’un domaine SL2 dans l’environnement de service cloud SL2 de CellTrust. Votre domaine peut avoir une ou plusieurs unités d’organisation. Le service cloud SL2 transfère vos données vers une zone hautement sécurisée de la plateforme Microsoft Azure, afin que vos données ne quittent jamais l’environnement Microsoft Azure. Selon votre plan SL2 (Entreprise, SMB ou Gouvernement), votre domaine est hébergé sur Microsoft Azure Global ou Microsoft Azure Government.

3. Après avoir créé le connecteur de données CellTrust SL2, votre domaine et vos unités d’organisation (quel que soit votre plan SL2), commencez à envoyer des données à Microsoft 365. Le flux de données est structuré pour prendre en charge les rapports basés sur des sources de données, des unités d’organisation ou le domaine par lui-même. Par conséquent, votre organisation n’a besoin que d’un seul connecteur pour alimenter toutes vos sources de données vers Microsoft 365.

4. Le connecteur crée un dossier sous chaque utilisateur mappé avec une licence Office 365 appropriée intitulée **CellTrust SL2**. Ce mappage connecte un utilisateur CellTrust SL2 à une boîte aux lettres Office 365 à l’aide d’une adresse e-mail. Si un ID d’utilisateur dans CellTrust SL2 n’a aucune correspondance dans Office 365, les données de l’utilisateur ne seront pas archivées.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Vérifiez que vous disposez d’un domaine dans l’environnement de service cloud CellTrust SL2. Pour plus d’informations sur l’obtention d’un domaine SL2 de production ou d’essai, [contactez CellTrust](https://www.celltrust.com/contact-us/#form).

- Obtenez les informations d’identification pour accéder au compte d’administrateur de votre domaine SL2.

- L’utilisateur qui crée le connecteur de données CellTrust SL2 à l’étape 1 (et le termine à l’étape 3) doit se faire attribuer le rôle de connecteur de données Administration. Ce rôle est nécessaire pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité Microsoft Purview. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données CellTrust est disponible dans les environnements GCC dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="step-1-create-a-celltrust-sl2-connector"></a>Étape 1 : Créer un connecteur CellTrust SL2

La première étape consiste à créer un connecteur de données dans le portail de conformité.

1. Accédez aux <https://compliance.microsoft.com> **connecteurs de données** dans le volet de navigation gauche et cliquez dessus.

2. Sous l’onglet **Vue d’ensemble** , cliquez sur **Filtrer** , sélectionnez **By CellTrust**, puis appliquez le filtre.

   ![Configurez le filtre pour afficher les connecteurs CellTrust.](../media/DataConnectorsFilter.png)

3. Cliquez sur **CellTrust SL2 (préversion).**

4. Dans la page de description du produit **CellTrust SL2 (préversion),** cliquez sur **Ajouter un connecteur**.

5. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

6. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**. Le nom que vous entrez identifie le connecteur dans la page **Connecteurs de données** une fois que vous l’avez créé.

7. Dans la page **Se connecter à votre compte CellTrust** , cliquez sur **Se connecter à CellTrust**. Vous serez redirigé vers le **portail CellTrust pour Microsoft 365** dans une nouvelle fenêtre de navigateur.

## <a name="step-2-select-the-domains-or-ous-to-archive"></a>Étape 2 : Sélectionner les domaines ou les unités d’organisation à archiver

L’étape suivante consiste à vous connecter à un compte d’administrateur pour votre domaine CellTrust SL2 et à sélectionner les domaines et les unités d’organisation à archiver dans Microsoft 365.

1. Dans la page CellTrust **Microsoft 365 Connector** , sélectionnez votre environnement dans le service cloud SL2 pour afficher une page de connexion.

   En règle générale, vous devez voir une option représentant votre environnement. Toutefois, si vous avez des domaines dans plusieurs environnements, vous verrez des options pour chaque environnement. Après avoir effectué une sélection, vous êtes redirigé vers la page de connexion SL2.

2. Connectez-vous avec vos informations d’identification de compte d’administrateur de domaine ou d’unité d’organisation.

   Si vous vous connectez en tant qu’administrateur de domaine SL2, vous verrez le nom de votre domaine et les unités d’organisation dans ce domaine. Si vous n’avez pas d’unités d’organisation, vous voyez uniquement le nom de votre domaine. Si vous vous connectez en tant qu’administrateur d’unité d’organisation, vous voyez uniquement le nom de votre unité d’organisation.

3. Activez les unités commerciales que vous souhaitez archiver. La sélection du domaine ne sélectionne pas automatiquement les unités d’organisation. Vous devez activer chaque unité d’organisation séparément pour l’archiver.

   ![Activez les unités d’organisation pour archiver.](../media/EnableCellTrustOUs.png)

4. Lorsque vous avez terminé vos sélections, fermez la fenêtre du navigateur et revenez à la page de l’Assistant dans le portail de conformité. Après quelques secondes, l’Assistant passe automatiquement à l’étape suivante du mappage des utilisateurs.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Mapper les utilisateurs et terminer la configuration du connecteur

La dernière étape consiste à mapper les utilisateurs et à terminer la configuration du connecteur dans le portail de conformité.

1. Dans la page **De mappage d’utilisateurs** , **sélectionnez Activer le mappage automatique des utilisateurs** si l’adresse e-mail des utilisateurs est identique dans SL2 et Microsoft 365. Sinon, vous devez charger manuellement des adresses e-mail utilisateur en chargeant un fichier CSV qui mappe l’adresse SL2 des utilisateurs à leur adresse Microsoft 365.

2. Cliquez sur **Suivant**, passez en revue vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

   Le nouveau connecteur est ajouté à la liste de la page **Connecteurs de données** .

## <a name="get-help-from-celltrust"></a>Obtenir de l’aide de CellTrust

Pour plus d’informations sur le contact avec CellTrust, consultez la [page Support client CellTrust](https://www.celltrust.com/contact-us/#support) pour obtenir de l’aide sur la configuration d’un connecteur de données CellTrust SL2.

## <a name="more-information"></a>Plus d’informations

- Un administrateur de domaine peut configurer un connecteur pour le domaine ou toutes les unités d’organisation de ce domaine. Si vous utilisez le compte Administrateur de l’unité d’organisation, vous pouvez uniquement configurer un connecteur pour cette unité d’organisation spécifique.

- Pour effectuer correctement les étapes ci-dessus, vous devez disposer d’une licence Microsoft 365 E5 et disposer des droits d’administrateur Microsoft Office appropriés.

- Pour tester le nouveau connecteur, envoyez un SMS à l’aide de votre application mobile SL2 ou de votre portail SL2. Accédez à votre boîte aux lettres Microsoft 365 et ouvrez le dossier **CellTrust SL2** dans votre boîte de réception. L’affichage des sms dans votre boîte aux lettres peut prendre quelques minutes.

- De nombreuses lois et règlements exigent que les communications électroniques soient conservées de telle sorte que, lorsqu’elles sont demandées, elles puissent être produites en tant que preuves. La découverte électronique (eDiscovery) est utilisée pour se conformer à la production de communications électroniques. Les solutions eIA (Enterprise Information Archiving) sont conçues pour effectuer eDiscovery et fournissent des fonctionnalités telles que la gestion des stratégies de rétention, la classification des données et la supervision du contenu. Microsoft 365 offre une solution de rétention à long terme pour la conformité aux réglementations et aux normes qui affectent votre organisation.

- Le terme *archivage* tel qu’il est utilisé dans ce document fait référence à l’archivage dans le contexte d’une utilisation au sein d’une solution d’archivage des informations d’entreprise (EIA). Les solutions EIA ont des fonctionnalités eDiscovery qui produisent des documents pour les procédures juridiques, les litiges, les audits et les enquêtes. L’archivage dans le contexte de la sauvegarde et de la restauration utilisés pour la récupération d’urgence et la continuité d’activité n’est pas l’utilisation prévue du terme dans ce document.
