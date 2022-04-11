---
title: Configurer un connecteur pour archiver Cisco Jabber sur les données Oracle dans Microsoft 365
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
description: Découvrez comment configurer et utiliser un connecteur dans le Centre de conformité Microsoft 365 pour importer et archiver des données de Cisco Jabber sur Oracle vers Microsoft 365.
ms.openlocfilehash: cf7665542393436ef71889fe755a6339087eeade
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64761260"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-oracle-data"></a>Configurer un connecteur pour archiver Cisco Jabber sur les données Oracle

Utilisez un connecteur Veritas dans le Centre de conformité Microsoft 365 pour importer et archiver des données de la plateforme Cisco Jabber sur Oracle vers des boîtes aux lettres utilisateur de votre organisation Microsoft 365. Veritas fournit un connecteur [Cisco Jabber sur Oracle](https://www.veritas.com/insights/merge1/jabber) configuré pour capturer des éléments à partir de la source de données tierce (régulièrement) et importer ces éléments dans Microsoft 365. Le connecteur convertit le contenu tel que les fichiers et les opérations de fichiers, les commentaires et le contenu partagé de Cisco Jabber sur Oracle au format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois les données Cisco Jabber sur Oracle stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer Microsoft 365 fonctionnalités de conformité telles que la conservation des litiges, eDiscovery, les stratégies de rétention et les étiquettes de rétention. L’utilisation d’un connecteur Cisco Jabber sur Oracle pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-cisco-jabber-on-oracle-data"></a>Vue d’ensemble de l’archivage de Cisco Jabber sur les données Oracle

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données Cisco Jabber sur Oracle dans Microsoft 365.

![Flux de travail d’archivage pour Cisco Jabber sur les données Oracle.](../media/CiscoJabberOnOracleConnectorWorkflow.png)

1. Votre organisation travaille avec Cisco Jabber sur Oracle pour configurer un site Cisco Jabber sur Oracle.

2. Une fois toutes les 24 heures, Cisco Jabber sur les éléments Oracle est copié sur le site Veritas Merge1. Le connecteur convertit également les éléments Cisco Jabber sur Oracle au format de message électronique.

3. Le connecteur Cisco Jabber sur Oracle que vous créez dans le Centre de conformité Microsoft 365, se connecte au site Veritas Merge1 tous les jours et transfère le contenu Jabber à un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email du mappage* automatique des utilisateurs, comme décrit à [l’étape 3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier Boîte de réception nommé **Cisco Jabber sur Oracle** est créé dans les boîtes aux lettres utilisateur et les éléments sont importés dans ce dossier. Pour ce faire, le connecteur utilise la valeur de la propriété *Email* . Chaque élément Jabber contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Merge1 pour les connecteurs Microsoft. Pour ce faire, contactez le [support technique veritas](https://www.veritas.com/content/support/en_US). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur Cisco Jabber sur Oracle à l’étape 1 (et le termine à l’étape 3) doit se faire attribuer le rôle d’administrateur du connecteur de données. Ce rôle est nécessaire pour ajouter des connecteurs sur la page **Connecteurs de données** dans le Centre de conformité Microsoft 365. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le Centre de conformité Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données Veritas est en préversion publique dans Cloud de la communauté du secteur public environnements dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de conformité et de protection des données Microsoft 365. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="step-1-set-up-the-cisco-jabber-on-oracle-connector"></a>Étape 1 : Configurer le connecteur Cisco Jabber sur Oracle

La première étape consiste à accéder à la page **Connecteurs de données** dans le Centre de conformité Microsoft 365 et à créer un connecteur pour les données Jabber.

1. Accédez, <https://compliance.microsoft.com> puis cliquez sur **Data connectorsCisco** >  **Jabber sur Oracle**.

2. Dans la page de description du produit **Cisco Jabber sur Oracle** , cliquez sur **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-cisco-jabber-on-oracle-on-the-veritas-merge1-site"></a>Étape 2 : Configurer Cisco Jabber sur Oracle sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur Cisco Jabber sur Oracle sur le site Veritas Merge1. Pour plus d’informations sur la configuration du connecteur Cisco Jabber sur Oracle, consultez le [Guide d’utilisation des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20Oracle%20User%20Guide.pdf).

Une fois que vous avez cliqué sur **Enregistrer & Terminer**, la page De **mappage d’utilisateurs** dans l’Assistant Connecteur de l’Centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Mapper les utilisateurs et terminer la configuration du connecteur

Pour mapper les utilisateurs et terminer la configuration du connecteur dans le Centre de conformité Microsoft 365, procédez comme suit :

1. Dans la page **Mapper Cisco Jabber sur Oracle pour Microsoft 365 page utilisateurs**, activez le mappage automatique des utilisateurs. Les éléments Cisco Jabber sur Oracle incluent une propriété appelée *Email*, qui contient des adresses e-mail pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez sur **Suivant**, passez en revue vos paramètres, puis accédez à la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur.

## <a name="step-4-monitor-the-cisco-jabber-on-oracle-connector"></a>Étape 4 : Surveiller le connecteur Cisco Jabber sur Oracle

Après avoir créé le connecteur Cisco Jabber sur Oracle, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Accédez et <https://compliance.microsoft.com/> cliquez sur **Connecteurs de données** dans le volet de navigation gauche.

2. Cliquez sur l’onglet **Connecteurs** , puis sélectionnez le connecteur **Cisco Jabber sur Oracle** pour afficher la page de menu volant, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments supérieurs à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.
