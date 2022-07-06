---
title: Configurer un connecteur pour archiver les données CellTrust dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données CellTrust de Veritas vers Microsoft 365. Ce connecteur vous permet d’archiver des données à partir de sources de données tierces dans Microsoft 365. Après avoir archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces.
ms.openlocfilehash: ce2aa6e9db07953e5b60eae4aa19777dd9edcd9e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632990"
---
# <a name="set-up-a-connector-to-archive-celltrust-data"></a>Configurer un connecteur pour archiver les données CellTrust

Utilisez un connecteur Veritas dans le portail de conformité Microsoft Purview pour importer et archiver des données de la plateforme CellTrust vers des boîtes aux lettres utilisateur de votre organisation Microsoft 365. Veritas fournit un connecteur [CellTrust](https://globanet.com/celltrust/) qui capture les éléments de la source de données tierce et importe ces éléments dans Microsoft 365. Le connecteur convertit le contenu des SMS des comptes CellTrust au format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois les données CellTrust stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation des litiges, la découverte électronique, les stratégies de rétention et les étiquettes de rétention, ainsi que la conformité des communications. L’utilisation d’un connecteur CellTrust pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-celltrust-data"></a>Vue d’ensemble de l’archivage des données CellTrust

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données CellTrust dans Microsoft 365.

![Flux de travail d’archivage pour les données CellTrust.](../media/CellTrustConnectorWorkflow.png)

1. Votre organisation travaille avec CellTrust pour configurer et configurer un site CellTrust.

2. Une fois toutes les 24 heures, les éléments CellTrust sont copiés sur le site Veritas Merge1. Le connecteur convertit également le contenu d’un message au format de message électronique.

3. Le connecteur CellTrust que vous créez dans le portail de conformité se connecte au site Veritas Merge1 tous les jours et transfère les messages vers un emplacement de stockage Azure sécurisé dans le cloud Microsoft.

4. Le mappage automatique d’utilisateurs en tant que connecteur importe des éléments dans les boîtes aux lettres de certains utilisateurs à l’aide de la valeur de la propriété *Email* de [l’étape 3](#step-3-map-users-and-complete-the-connector-setup) décrite. Un sous-dossier du dossier Boîte de réception nommé **CellTrust** est créé dans les boîtes aux lettres utilisateur et les éléments de message sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres vers laquelle importer des éléments à l’aide de la valeur de la propriété *Email* . Chaque élément CellTrust contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Merge1 pour les connecteurs Microsoft. Pour créer un compte, contactez [le support technique Veritas](https://www.veritas.com/content/support/). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur CellTrust à l’étape 1 (et le termine à l’étape 3) doit avoir le rôle de connecteur de données Administration. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données Veritas est en préversion publique dans les environnements GCC dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="step-1-set-up-the-celltrust-connector"></a>Étape 1 : Configurer le connecteur CellTrust

La première étape consiste à accéder aux **connecteurs de données** dans le portail de conformité et à créer un connecteur pour les données CellTrust.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) **CellTrust**, puis cliquez sur **Connecteurs** \> de données.

2. Dans la page de description du produit **CellTrust** , cliquez sur **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-celltrust-connector-on-the-veritas-merge1-site"></a>Étape 2 : Configurer le connecteur CellTrust sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur CellTrust sur le site Veritas Merge1. Pour plus d’informations sur la configuration du connecteur CellTrust, consultez le [Guide d’utilisation des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20CellTrust%20User%20Guide%20.pdf).

Une fois que vous avez cliqué sur **Enregistrer & Terminer**, la page De **mappage utilisateur** de l’Assistant Connecteur dans le portail de conformité s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Mapper les utilisateurs et terminer la configuration du connecteur

Pour mapper les utilisateurs et terminer la configuration du connecteur dans le portail de conformité, procédez comme suit :

1. Dans la page **Map CellTrust users to Microsoft 365 users** , activez le mappage automatique des utilisateurs. Les éléments CellTrust incluent une propriété appelée *Email*, qui contient des adresses e-mail pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez sur **Suivant**, passez en revue vos paramètres et accédez à la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur.

## <a name="step-4-monitor-the-celltrust-connector"></a>Étape 4 : Surveiller le connecteur CellTrust

Après avoir créé le connecteur CellTrust, vous pouvez afficher l’état du connecteur dans le portail de conformité.

1. Accédez et [https://compliance.microsoft.com](https://compliance.microsoft.com/) cliquez sur **Connecteurs de données** dans le volet de navigation gauche.

2. Cliquez sur l’onglet **Connecteurs** , puis sélectionnez le connecteur **CellTrust** pour afficher la page de menu volant, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur les données qui ont été importées dans le cloud Microsoft. Pour plus d’informations, consultez [Afficher les journaux d’administration pour les connecteurs de données](data-connector-admin-logs.md).

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments supérieurs à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.