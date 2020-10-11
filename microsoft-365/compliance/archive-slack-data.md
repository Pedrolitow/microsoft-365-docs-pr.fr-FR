---
title: Configurer un connecteur pour archiver les données eDiscovery de la marge dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données à partir de la découverte 365 électronique Globanet. Ce connecteur de données vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 de sorte que vous puissiez utiliser les fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 93b3a84aea2144f7f3f83470303d0270681d9323
ms.sourcegitcommit: ae3aa7f29be16d08950cf23cad489bc069aa8617
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "48408634"
---
# <a name="set-up-a-connector-to-archive-slack-ediscovery-data"></a>Configurer un connecteur pour archiver les données eDiscovery de la marge

Utilisez un connecteur Globanet dans le centre de conformité Microsoft 365 pour importer et archiver des données tierces à partir de plateformes de réseau social, de messagerie instantanée et de collaboration sur des documents, vers des boîtes aux lettres de votre organisation Microsoft 365. Globanet fournit un connecteur de marge qui est configuré pour capturer des éléments à partir de la source de données tierce (de manière régulière), puis les importer dans Microsoft 365. La marge extrait les messages et les fichiers de l’API de marge et les convertit en format de message électronique, puis importe l’élément dans les boîtes aux lettres utilisateur.

Une fois les données de découverte électronique stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention et la conformité des communications. L’utilisation d’un connecteur de marge pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-slack-ediscovery-data"></a>Vue d’ensemble des données eDiscovery de la marge d’archivage

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur pour archiver les informations de marge dans Microsoft 365.

![Flux de travail d’archivage de marge](../media/SlackConnectorWorkflow.png)

1. Votre organisation travaille avec la marge pour installer et configurer un site de marge.

2. Une fois toutes les 24 heures, les messages de conversation provenant de la découverte électronique sont copiés sur le site Globanet Merge1. Le connecteur convertit également le contenu d’un message de conversation au format d’un message électronique.

3. Le connecteur eDiscovery de la marge que vous créez dans le centre de conformité 365 de Microsoft, se connecte au site Merge1 Globanet tous les jours et transfère les messages de conversation vers un emplacement de stockage Azure sécurisé dans le Cloud Microsoft.

4. Le connecteur importe les éléments de message de conversation converti dans les boîtes aux lettres d’utilisateurs spécifiques en utilisant la valeur de la propriété *email* et le mappage utilisateur automatique, comme décrit à l’étape 3. Un nouveau sous-dossier dans le dossier boîte de réception appelé **marge eDiscovery** est créé dans les boîtes aux lettres utilisateur, et les éléments de message de conversation sont importés dans ce dossier. Le connecteur effectue cette opération à l’aide de la valeur de la propriété *email* . Chaque message de conversation contient cette propriété, qui est renseignée avec l’adresse de messagerie de chaque participant du message de conversation.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Globanet Merge1 pour Microsoft Connectors. Pour ce faire, contactez le [support client Globanet](https://globanet.com/ms-connectors-contact). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- Obtenez le nom d’utilisateur et le mot de passe du compte d’entreprise marge de votre organisation. Vous devrez vous connecter à ce compte à l’étape 2 lorsque vous configurez la marge.

- L’utilisateur qui crée le connecteur eDiscovery de marge à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle exportation d’importation de boîtes aux lettres dans Exchange Online. Ce rôle est nécessaire pour ajouter des connecteurs sur la page **connecteurs de données** dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="step-1-set-up-the-slack-ediscovery-connector"></a>Étape 1 : configurer le connecteur eDiscovery de la marge

La première étape consiste à accéder à la page **connecteurs de données** dans le centre de conformité Microsoft 365 et à créer un connecteur pour les données de marge.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **Data Connectors**  >  **mou-eDiscovery**.

2. Sur la page Description du produit eDiscovery de la **marge** , cliquez sur **Ajouter un connecteur**.

3. Sur la page **conditions de service** , cliquez sur **accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-slack-ediscovery"></a>Étape 2 : configurer la découverte électronique des marges

La deuxième étape consiste à configurer le connecteur eDiscovery de la marge sur le site Merge1. Pour plus d’informations sur la configuration du connecteur eDiscovery de la marge sur le site Merge1 Globanet, voir [Merge1 le Guide de l’utilisateur des connecteurs tiers](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Slack%20eDiscovery%20User%20Guide.pdf).

Une fois que vous avez cliqué sur **enregistrer & terminer**, vous êtes redirigé vers le centre de conformité Microsoft 365, sur la page **mappage utilisateur** de l’Assistant connecteur.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : mapper les utilisateurs et terminer l’installation du connecteur

1. Sur la page **connecter des utilisateurs externes à des utilisateurs de Microsoft 365** , activez le mappage utilisateur automatique.

   Marge les éléments eDiscovery incluent une propriété appelée *courrier électronique*, qui contient des adresses de messagerie pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur de Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Sur la page consentement de l' **administrateur** , cliquez sur **fournir le consentement**. Vous serez redirigé vers le site Microsoft. Cliquez sur **accepter** pour fournir le consentement.

   Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de boîte aux lettres dans votre organisation. Pour fournir le consentement de l’administrateur, vous devez être connecté avec les informations d’identification d’un administrateur général Microsoft 365, puis accepter la demande de consentement. Si vous n’êtes pas connecté en tant qu’administrateur général, vous pouvez accéder à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) et vous connecter à l’aide des informations d’identification d’administrateur général pour accepter la demande.

3. Cliquez sur **suivant**, vérifiez vos paramètres, puis accédez à la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-slack-ediscovery-connector"></a>Étape 4 : surveiller le connecteur eDiscovery de la marge

Une fois que vous avez créé le connecteur eDiscovery de la marge, vous pouvez afficher l’état du connecteur dans le centre de conformité Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Cliquez sur l’onglet **connecteurs** , puis sélectionnez le connecteur eDiscovery de la **marge** pour afficher la page de menu volant, qui contient les propriétés et les informations relatives au connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’État du connecteur. Ce journal contient des informations sur les données qui ont été importées dans le Cloud Microsoft.

## <a name="known-issues"></a>Problèmes connus

- Pour le moment, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus importants sera disponible ultérieurement.
