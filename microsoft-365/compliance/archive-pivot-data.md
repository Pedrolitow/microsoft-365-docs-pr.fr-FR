---
title: Configurer un connecteur pour archiver les données de tableau croisé dynamique dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données de tableau croisé dynamique à partir de Veritas dans Microsoft 365. Ce connecteur vous permet d’archiver les données de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 7719dabb59180d6c3dc579c02fbc76b0d77ec1a7
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "65001651"
---
# <a name="set-up-a-connector-to-archive-pivot-data"></a>Configurer un connecteur pour archiver les données de tableau croisé dynamique

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Utilisez un connecteur Veritas dans le portail de conformité Microsoft Purview pour importer et archiver des données de la plateforme Pivot vers les boîtes aux lettres utilisateur de votre organisation Microsoft 365. Veritas vous fournit un connecteur de tableau [croisé](https://globanet.com/pivot/) dynamique configuré pour capturer des éléments à partir de la source de données tierce (régulièrement), puis importer ces éléments dans Microsoft 365. Pivot est une plateforme de messagerie instantanée qui permet la collaboration avec les participants au marché financier. Le connecteur convertit les éléments tels que les messages de conversation, des comptes Pivot d’un utilisateur au format de message électronique, puis importe ces éléments dans les boîtes aux lettres utilisateur dans Microsoft 365.

Une fois les données de tableau croisé dynamique stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation des litiges, la découverte électronique, les stratégies de rétention et les étiquettes de rétention, ainsi que la conformité des communications. L’utilisation d’un connecteur pivot pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-pivot-data"></a>Vue d’ensemble de l’archivage des données de tableau croisé dynamique

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données de tableau croisé dynamique dans Microsoft 365.

![Flux de travail d’archivage pour les données de tableau croisé dynamique.](../media/PivotConnectorWorkflow.png)

1. Votre organisation travaille avec Pivot pour configurer et configurer un site source pivot.

2. Une fois toutes les 24 heures, les éléments de tableau croisé dynamique sont copiés sur le site Veritas Merge1. Le connecteur convertit également les éléments de tableau croisé dynamique au format de message électronique.

3. Le connecteur de tableau croisé dynamique que vous créez dans le portail de conformité, se connecte au site Veritas Merge1 tous les jours et transfère les éléments de tableau croisé dynamique à un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments de tableau croisé dynamique dans les boîtes aux lettres de certains utilisateurs à l’aide de la valeur de la propriété *Email du mappage* automatique d’utilisateurs, comme décrit à [l’étape 3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier Boîte de réception nommé **Pivot** est créé dans les boîtes aux lettres utilisateur et les éléments sont importés dans ce dossier. Pour ce faire, le connecteur utilise la valeur de la propriété *Email* . Chaque élément de tableau croisé dynamique contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Veritas Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez le [support technique Veritas](https://www.veritas.com/content/support/). Vous vous connecterez à ce compte lorsque vous créerez le connecteur à l’étape 1.

- Le rôle Administrateur du connecteur de données doit être attribué à l’utilisateur qui crée le connecteur Pivot à l’étape 1 (et le termine à l’étape 3). Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données Veritas est en préversion publique dans Cloud de la communauté du secteur public environnements dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="step-1-set-up-the-pivot-connector"></a>Étape 1 : Configurer le connecteur pivot

La première étape consiste à accéder à la page **Connecteurs de données** dans le Centre de conformité Microsoft et à créer un connecteur pour les données de tableau croisé dynamique.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) Data **connectorsPivot**, puis cliquez **dessus** > .

2. Dans la page de description du produit **Pivot** , cliquez sur **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-pivot-connector-on-the-veritas-merge1-site"></a>Étape 2 : Configurer le connecteur Pivot sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur Pivot sur le site Merge1. Pour plus d’informations sur la configuration du connecteur Pivot sur le site Veritas Merge1, consultez le [Guide utilisateur des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Pivot%20User%20Guide%20.pdf).

Une fois que vous avez cliqué sur **Enregistrer & Terminer**, la page De **mappage utilisateur** de l’Assistant Connecteur dans le portail de conformité s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Mapper les utilisateurs et terminer la configuration du connecteur

Pour mapper les utilisateurs et terminer la configuration du connecteur dans le Centre de conformité Microsoft 356, procédez comme suit :

1. Dans la page **Microsoft 365 utilisateurs**, activez le mappage automatique des utilisateurs. Les éléments de tableau croisé dynamique incluent une propriété appelée *Email*, qui contient des adresses e-mail pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez sur **Suivant**, passez en revue vos paramètres et accédez à la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur.

## <a name="step-4-monitor-the-pivot-connector"></a>Étape 4 : Surveiller le connecteur pivot

Après avoir créé le connecteur pivot, vous pouvez afficher l’état du connecteur dans le portail de conformité.

1. Accédez et [https://compliance.microsoft.com](https://compliance.microsoft.com) cliquez sur **Connecteurs de données** dans le volet de navigation gauche.

2. Cliquez sur l’onglet **Connecteurs** , puis sélectionnez le connecteur **Pivot** pour afficher la page de menu volant. Cette page contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments supérieurs à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.