---
title: Configuration d’un connecteur pour l’archivage des données de réunions zoom dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données à partir de réunions zoom Globanet dans Microsoft 365. Cela vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 de sorte que vous puissiez utiliser les fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: ef153ec0a14a257f1f46b011e4c15d2b3b704ed3
ms.sourcegitcommit: ae3aa7f29be16d08950cf23cad489bc069aa8617
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "48408942"
---
# <a name="set-up-a-connector-to-archive-zoom-meetings-data"></a>Configuration d’un connecteur pour l’archivage des données de réunions zoom

Utilisez un connecteur Globanet dans le centre de conformité Microsoft 365 pour importer et archiver des données à partir de réunions de zoom vers des boîtes aux lettres utilisateur dans votre organisation Microsoft 365. Globanet fournit un connecteur de [réunions avec zoom](https://globanet.com/zoom/) qui est configuré pour capturer des éléments à partir de la source de données tierce (de manière régulière) et les importer dans Microsoft 365. Le connecteur convertit le contenu des réunions (y compris les conversations, les fichiers enregistrés et les métadonnées) du compte de réunions zoom en un format de message électronique, puis importe ces éléments dans les boîtes aux lettres utilisateur dans Microsoft 365.

Une fois le zoom sur les données de réunions stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention et la conformité des communications L’utilisation d’un connecteur de réunions zoom pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-zoom-meetings-data"></a>Vue d’ensemble des données de réunions zoom sur l’archivage

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur pour archiver des données de réunions zoom dans Microsoft 365.

![Flux de travail d’archivage des réunions zoom](../media/ZoomMeetingsConnectorWorkflow.png)

1. Votre organisation travaille avec des réunions zoom pour installer et configurer un site de réunions zoom.

2. Une fois toutes les 24 heures, les éléments de réunion provenant de réunions de zoom sont copiés sur le site Globanet Merge1. Le connecteur convertit également le contenu des réunions au format d’un message électronique.

3. Le connecteur de réunions de zoom que vous créez dans le centre de conformité 365 de Microsoft, se connecte au Merge1 Globanet tous les jours et transfère les messages de réunion vers un emplacement de stockage Azure sécurisé dans le Cloud Microsoft.

4. Le connecteur importe les éléments de réunion convertis dans les boîtes aux lettres d’utilisateurs spécifiques en utilisant la valeur de la propriété *email* et le mappage utilisateur automatique, comme décrit à l’étape 3. Un nouveau sous-dossier dans le dossier boîte de réception nommé **réunions de zoom** est créé dans les boîtes aux lettres utilisateur, et les éléments de réunion sont importés dans ce dossier. Le connecteur effectue cette opération à l’aide de la valeur de la propriété *email* . Chaque élément de réunion contient cette propriété, qui est renseignée avec l’adresse de messagerie de chaque participant de la réunion.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Globanet Merge1 pour Microsoft Connectors. Pour ce faire, contactez le [support client Globanet](https://globanet.com/ms-connectors-contact). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- Obtenir le nom d’utilisateur et le mot de passe du compte d’entreprise zoom ou zoom de votre organisation. Vous devrez vous connecter à ce compte à l’étape 2 lorsque vous configurez le connecteur de réunions zoom.

- Créez les applications suivantes dans le [marché du zoom](https://marketplace.zoom.us):

  - Application OAuth

  - Application JWT

  Une fois ces applications créées, la plateforme de zoom génère un ensemble d’informations d’identification uniques utilisées pour générer les jetons. Ces jetons sont utilisés pour authentifier le connecteur lorsqu’il se connecte à votre compte de zoom et copie des éléments sur le site Merge1. Vous utiliserez ces jetons lors de la configuration du connecteur de zoom à l’étape 2.

  Pour obtenir des instructions pas à pas sur la création des applications OAuth et JWT, consultez le Guide de l' [utilisateur des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Zoom%20Meetings%20User%20Guide%20.pdf).

- L’utilisateur qui crée le connecteur de réunions zoom à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle d’exportation d’importation de boîte aux lettres dans Exchange Online. Ce rôle est nécessaire pour ajouter des connecteurs sur la page **connecteurs de données** dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="step-1-set-up-the-zoom-meetings-connector"></a>Étape 1 : configurer le connecteur de réunions zoom

La première étape consiste à accéder aux **connecteurs de données** dans le centre de conformité Microsoft 365 et à créer un connecteur de réunions zoom.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur les **connecteurs de données**zoom sur les  >  **réunions**.

2. Dans la page zoom sur les **réunions des réunions** , cliquez sur Ajouter un **connecteur**.

3. Sur la page **conditions de service** , cliquez sur **accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-zoom-meetings-connector"></a>Étape 2 : configurer le connecteur de réunions zoom

La deuxième étape consiste à configurer le connecteur de réunions zoom sur le site Merge1. Pour plus d’informations sur la configuration du connecteur de réunions zoom sur le site Merge1 Globanet, voir Merge1 le Guide de l' [utilisateur des connecteurs tiers](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Zoom%20Meetings%20User%20Guide%20.pdf).

Une fois que vous avez cliqué sur **enregistrer & terminer**, vous êtes redirigé vers le centre de conformité Microsoft 365, sur la page **mappage utilisateur** de l’Assistant connecteur.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : mapper les utilisateurs et terminer l’installation du connecteur

1. Sur la page **connecter des utilisateurs externes à des utilisateurs de Microsoft 365** , activez le mappage utilisateur automatique.

   Zoom les éléments de réunion incluent une propriété appelée *courrier électronique* qui contient des adresses de messagerie pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur de Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Sur la page consentement de l' **administrateur** , cliquez sur **fournir le consentement**. Vous serez redirigé vers le site Microsoft. Cliquez sur **accepter** pour fournir le consentement.
  
   Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de boîte aux lettres dans votre organisation. Pour fournir le consentement de l’administrateur, vous devez être connecté avec les informations d’identification d’un administrateur général Microsoft 365, puis accepter la demande de consentement. Si vous n’êtes pas connecté en tant qu’administrateur général, vous pouvez accéder à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) et vous connecter à l’aide des informations d’identification d’administrateur général pour accepter la demande.

3. Cliquez sur **suivant**, vérifiez vos paramètres, puis accédez à la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-zoom-meetings-connector"></a>Étape 4 : Surveillez le lien zoom sur les réunions

Une fois que vous avez créé le connecteur de réunions zoom, vous pouvez afficher l’état du connecteur dans le centre de conformité Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Cliquez sur l’onglet **connecteurs** , puis sélectionnez le connecteur zoom sur les **réunions** pour afficher la page de menu volant, qui contient les propriétés et les informations relatives au connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’État du connecteur. Ce journal contient des informations sur les données qui ont été importées dans le Cloud Microsoft.

## <a name="known-issues"></a>Problèmes connus

- Pour le moment, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus importants sera disponible ultérieurement.

- Pour que le connecteur de réunions avec zoom fonctionne, vous devez activer les enregistrements lors de la configuration des réunions zoom.
