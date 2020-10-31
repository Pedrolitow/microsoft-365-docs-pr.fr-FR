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
localization_priority: Normal
ms.collection: M365-security-compliance
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données de tableau croisé dynamique à partir de Globanet dans Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 de sorte que vous puissiez utiliser les fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: f9c0925856ffb9c43fa985c9da4bcd17485a5e39
ms.sourcegitcommit: 3c39866865c8c61bce2169818d8551da65033cfe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "48816577"
---
# <a name="set-up-a-connector-to-archive-pivot-data"></a>Configurer un connecteur pour archiver les données de tableau croisé dynamique

Utilisez un connecteur Globanet dans le centre de conformité Microsoft 365 pour importer et archiver des données à partir de la plateforme de tableau croisé dynamique vers des boîtes aux lettres utilisateur dans votre organisation Microsoft 365. Globanet fournit un connecteur de [tableau croisé dynamique](https://globanet.com/pivot/) qui est configuré pour capturer des éléments à partir de la source de données tierce (de manière régulière), puis les importer dans Microsoft 365. Le tableau croisé dynamique est une plateforme de messagerie instantanée qui permet la collaboration avec les participants au marché financier. Le connecteur convertit des éléments tels que des messages de conversation, des comptes de tableau croisé dynamique d’un utilisateur en un format de message électronique, puis importe ces éléments dans les boîtes aux lettres utilisateur dans Microsoft 365.

Une fois les données de tableau croisé dynamique stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention et la conformité des communications L’utilisation d’un connecteur de tableau croisé dynamique pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-pivot-data"></a>Vue d’ensemble des données de tableau croisé dynamique d’archivage

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur pour archiver les données de tableau croisé dynamique dans Microsoft 365.

![Flux de travail d’archivage pour les données de tableau croisé dynamique](../media/PivotConnectorWorkflow.png)

1. Votre organisation fonctionne avec le tableau croisé dynamique pour installer et configurer un site de source de tableau croisé dynamique.

2. Une fois toutes les 24 heures, les éléments de tableau croisé dynamique sont copiés sur le site Merge1 Globanet. Le connecteur convertit également les éléments de tableau croisé dynamique en un format de message électronique.

3. Le connecteur de tableau croisé dynamique que vous créez dans le centre de conformité 365 de Microsoft, se connecte au site Merge1 Globanet tous les jours et transfère les éléments de tableau croisé dynamique vers un emplacement de stockage Azure sécurisé dans le Cloud Microsoft.

4. Le connecteur importe les éléments de tableau croisé dynamique vers les boîtes aux lettres d’utilisateurs spécifiques en utilisant la valeur de la propriété *email* du mappage utilisateur automatique, comme décrit à l' [étape 3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier boîte de réception nommé **tableau croisé dynamique** est créé dans les boîtes aux lettres utilisateur, et les éléments sont importés dans ce dossier. Le connecteur effectue cette opération à l’aide de la valeur de la propriété *email* . Chaque élément de tableau croisé dynamique contient cette propriété, qui est renseignée avec l’adresse de messagerie de chaque participant de l’élément.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Globanet Merge1 pour Microsoft Connectors. Pour créer ce compte, contactez le [support client Globanet](https://globanet.com/ms-connectors-contact/). Vous vous connecterez à ce compte lors de la création du connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur de tableau croisé dynamique à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle d’exportation d’importation de boîte aux lettres dans Exchange Online. Ce rôle est nécessaire pour ajouter des connecteurs sur la page connecteurs de données dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est pas affecté à un groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="step-1-set-up-the-pivot-connector"></a>Étape 1 : configurer le connecteur de tableau croisé dynamique

La première étape consiste à accéder à la page **connecteurs de données** dans le centre de conformité Microsoft et à créer un connecteur pour les données de tableau croisé dynamique.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez **Data connectors** sur  >  **tableau de croisé dynamique** des connecteurs de données.

2. Dans la page Description du produit de **tableau croisé dynamique** , cliquez sur **Ajouter un connecteur** .

3. Sur la page **conditions de service** , cliquez sur **accepter** .

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **suivant** .

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-pivot-connector-on-the-globanet-merge1-site"></a>Étape 2 : configurer le connecteur de tableau croisé dynamique sur le site Merge1 Globanet

La deuxième étape consiste à configurer le connecteur de tableau croisé dynamique sur le site Merge1. Pour plus d’informations sur la configuration du connecteur de tableau croisé dynamique sur le site Merge1 Globanet, voir Merge1 le Guide de l' [utilisateur des connecteurs tiers](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Pivot%20User%20Guide%20.pdf).

Une fois que vous avez cliqué sur **enregistrer & terminer** , la page de **mappage utilisateur** de l’Assistant connecteur dans le centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : mapper les utilisateurs et terminer l’installation du connecteur

Pour mapper les utilisateurs et terminer l’installation du connecteur dans le centre de conformité Microsoft 356, procédez comme suit :

1. Sur la page **mapper les utilisateurs pivot sur les utilisateurs de Microsoft 365** , activez le mappage utilisateur automatique. Les éléments de tableau croisé dynamique incluent une propriété appelée *courrier électronique* , qui contient des adresses de messagerie pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur de Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Sur la page consentement de l' **administrateur** , cliquez sur **fournir le consentement** . Vous serez redirigé vers le site Microsoft. Cliquez sur **accepter** pour fournir le consentement.

   Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de boîte aux lettres dans votre organisation. Pour fournir le consentement de l’administrateur, vous devez être connecté avec les informations d’identification d’un administrateur général Microsoft 365, puis accepter la demande de consentement. Si vous n’êtes pas connecté en tant qu’administrateur général, vous pouvez accéder à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) et vous connecter à l’aide des informations d’identification d’administrateur général pour accepter la demande.

3. Cliquez sur **suivant** , vérifiez vos paramètres, puis accédez à la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-pivot-connector"></a>Étape 4 : Surveillez le connecteur de tableau croisé dynamique

Après avoir créé le connecteur de tableau croisé dynamique, vous pouvez afficher l’état du connecteur dans le centre de conformité Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Cliquez sur l’onglet **connecteurs** , puis sélectionnez le connecteur de **tableau croisé dynamique** pour afficher la page de menu volant. Cette page contient les propriétés et les informations relatives au connecteur.

3. Sous **État du connecteur avec source** , cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’État du connecteur. Ce journal contient des données qui ont été importées dans Microsoft Cloud.

## <a name="known-issues"></a>Problèmes connus

- Pour le moment, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus importants sera disponible ultérieurement.
