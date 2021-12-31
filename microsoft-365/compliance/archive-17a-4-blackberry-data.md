---
title: Configurer un connecteur pour archiver les données BlackBerry dans Microsoft 365
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
description: Découvrez comment configurer et utiliser un connecteur BlackBerry DataParser 17a-4 pour importer et archiver des données BlackBerry dans Microsoft 365.
ms.openlocfilehash: 1c95a2b4f9a6a9e8054e92f27e8adbdb16aa53e3
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/30/2021
ms.locfileid: "61643017"
---
# <a name="set-up-a-connector-to-archive-blackberry-data"></a>Configurer un connecteur pour archiver les données BlackBerry

Utilisez [l’analyseur](https://www.17a-4.com/BlackBerry-dataparser/) de données BlackBerry de 17a-4 LLC pour importer et archiver des données d’entreprise BlackBerry dans les boîtes aux lettres des utilisateurs de Microsoft 365 organisation. DataParser inclut un connecteur BlackBerry configuré pour capturer des éléments à partir d’une source de données tierce et importer ces éléments dans Microsoft 365. Le connecteur BlackBerry DataParser convertit les données BlackBerry au format de message électronique, puis importe ces éléments dans les boîtes aux lettres des utilisateurs Microsoft 365.

Une fois que les données BlackBerry sont stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies et étiquettes de rétention et la conformité des communications. L’utilisation d’un connecteur BlackBerry pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-blackberry-data"></a>Vue d’ensemble de l’archivage des données BlackBerry

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur de données pour archiver les données BlackBerry dans Microsoft 365.

![Flux de travail d’archivage pour les données BlackBerry 17a-4.](../media/BlackBerryDataParserConnectorWorkflow.png)

1. Votre organisation travaille avec le 17a-4 pour configurer l’analyseur de données BlackBerry.

2. Régulièrement, les éléments BlackBerry sont collectés par DataParser. DataParser convertit également le contenu d’un message au format de message électronique.

3. Le connecteur BlackBerry DataParser que vous créez dans le Centre de conformité Microsoft 365 se connecte à DataParser et transfère les messages vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Un sous-dossier du dossier Boîte de réception nommé **BlackBerry DataParser** est créé dans les boîtes aux lettres utilisateur et les éléments BlackBerry sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer des éléments à l’aide de la valeur de la *propriété Email.* Chaque élément BlackBerry contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Créez un compte DataParser pour les connecteurs Microsoft. Pour ce faire, contactez [17a-4 LLC.](https://www.17a-4.com/contact/) Vous devez vous inscrire à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur BlackBerry DataParser à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs** de données dans la Centre de conformité Microsoft 365. Par défaut, ce rôle n’est pas attribué à un groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

- Ce connecteur de données 17a-4 est disponible dans les environnements Cloud de la communauté du secteur public dans le cloud Microsoft 365 gouvernement américain. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui sont en dehors de l’infrastructure Microsoft 365 et qui, par conséquent, ne sont pas couverts par les engagements en matière de conformité et de protection des données Microsoft 365. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="step-1-set-up-a-blackberry-dataparser-connector"></a>Étape 1 : Configurer un connecteur BlackBerry DataParser

La première étape consiste à accéder à la page Connecteurs de données dans le Centre de conformité Microsoft 365 et à créer un connecteur 17a-4 pour les données BlackBerry.

1. Go to <https://compliance.microsoft.com> and then click Data **connectors**  >  **BlackBerry DataParser**.

2. Dans la page de description du produit **BlackBerry DataParser,** cliquez **sur Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte 17a-4 et complétez les étapes de l’Assistant Connexion BlackBerry DataParser.

## <a name="step-2-configure-the-blackberry-dataparser-connector"></a>Étape 2 : Configurer le connecteur BlackBerry DataParser

Travaillez avec la prise en charge 17a-4 pour configurer le connecteur BlackBerry DataParser.

## <a name="step-3-map-users"></a>Étape 3 : Ma cartographier les utilisateurs

Le connecteur BlackBerry DataParser masquera automatiquement les utilisateurs à leurs adresses Microsoft 365 courrier avant d’importer des données dans Microsoft 365.

## <a name="step-4-monitor-the-blackberry-dataparser-connector"></a>Étape 4 : Surveiller le connecteur BlackBerry DataParser

Après avoir créé un connecteur BlackBerry DataParser, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to <https://compliance.microsoft.com> and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le connecteur BlackBerry DataParser que vous avez créé pour afficher la page de présentation, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes détectés

Pour l’instant, nous ne ons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.