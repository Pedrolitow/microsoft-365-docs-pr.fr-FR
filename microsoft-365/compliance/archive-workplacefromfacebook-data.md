---
title: Configurer un connecteur pour archiver un espace de travail à partir de données Facebook dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données à partir de l’espace de travail à partir de Facebook, qui est archivé sur le site Merge1 de Globanet, dans Microsoft 365. La configuration d’un connecteur nécessite que vous utilisiez Globanet ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 de sorte que vous puissiez utiliser les fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: cea8f7549bbf1ed19bc3de6fe4d1e1c63f1be4cd
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48195581"
---
# <a name="set-up-a-connector-to-archive-workplace-from-facebook-data"></a>Configurer un connecteur pour archiver un espace de travail à partir de données Facebook

Utilisez un connecteur Globanet dans le centre de conformité Microsoft 365 pour importer et archiver des données à partir de l’espace de travail de Facebook vers des boîtes aux lettres utilisateur dans votre organisation 365 Microsoft. Globanet fournit un [espace de travail à partir d'](https://globanet.com/workplace/) un connecteur Facebook configuré pour capturer des éléments à partir de la source de données tierce (de manière régulière) et les importer dans Microsoft 365. Le connecteur convertit le contenu tel que les conversations, les pièces jointes, les publications et les vidéos de l’espace de travail en format de message électronique, puis importe ces éléments dans les boîtes aux lettres utilisateur dans Microsoft 365.

Une fois que les données de l’espace de travail sont stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention L’utilisation de l’espace de travail à partir du connecteur Facebook pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-workplace-from-facebook-data"></a>Vue d’ensemble de l’archivage d’espace de travail à partir de données Facebook

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur pour archiver les données de l’espace de travail dans Microsoft 365.

![Flux de travail d’archivage pour Workplace à partir de données Facebook](../media/WorkplaceConnectorWorkflow.png)

1. Votre organisation travaille avec Workplace à partir de Facebook pour installer et configurer un site d’espace de travail.

2. Une fois toutes les 24 heures, les éléments de l’espace de travail sont copiés sur le site Merge1 Globanet. Le connecteur convertit également le contenu de ces éléments au format d’un message électronique.

3. Le lieu de travail à partir du connecteur Facebook que vous créez dans le centre de conformité 365 de Microsoft, se connecte au Merge1 Globanet tous les jours et transfère les éléments de l’espace de travail à un emplacement de stockage Azure sécurisé dans le Cloud Microsoft.

4. Le connecteur importe les éléments convertis dans les boîtes aux lettres d’utilisateurs spécifiques en utilisant la valeur de la propriété *email* du mappage utilisateur automatique, comme décrit à l’étape 3. Un sous-dossier du dossier boîte de réception nommé **Workplace from Facebook** est créé, et les éléments de l’espace de travail sont importés dans ce dossier. Le connecteur effectue cette opération à l’aide de la valeur de la propriété *email* . Chaque élément de l’espace de travail contient cette propriété, qui est renseignée avec l’adresse de messagerie de chaque participant de conversation ou de billet.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Globanet Merge1 pour Microsoft Connectors. Pour ce faire, contactez le [support client Globanet](https://globanet.com/ms-connectors-contact). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- Créez une intégration personnalisée à https://my.workplace.com/work/admin/apps/ pour récupérer des données à partir du lieu de travail via des API à des fins de conformité et de découverte électronique.

   Lors de la création de l’intégration, la plateforme de l’espace de travail génère un ensemble d’informations d’identification uniques utilisées pour générer des jetons utilisés pour l’authentification. Ces jetons sont utilisés dans l’Assistant de configuration de l’espace de travail à partir du connecteur Facebook à l’étape 2. Pour obtenir des instructions pas à pas sur la création des applications, consultez la rubrique [Merge1 tiers Connector User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Workplace%20from%20Facebook%20User%20Guide%20.pdf).

- L’utilisateur qui crée l’espace de travail à partir d’un connecteur Facebook à l’étape 1 (et la termine à l’étape 3) doit être affecté au rôle exportation d’importation de boîtes aux lettres dans Exchange Online. Ce rôle est nécessaire pour ajouter des connecteurs sur la page **connecteurs de données** dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="step-1-set-up-the-workplace-from-facebook-connector"></a>Étape 1 : configurer l’espace de travail à partir du connecteur Facebook

La première étape consiste à accéder à la page **connecteurs de données** dans le centre de conformité Microsoft 365 et à créer un connecteur pour les données de l’espace de travail.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez **Data connectors**sur  >  **espace de travail des connecteurs de données à partir de Facebook**.

2. Sur la page **espace de travail à partir de** la description du produit Facebook, cliquez sur **Ajouter un connecteur**.

3. Sur la page **conditions de service** , cliquez sur **accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-workplace-from-facebook-connector-on-the-globanet-merge1-site"></a>Étape 2 : configurer l’espace de travail à partir du connecteur Facebook sur le site Merge1 Globanet

La deuxième étape consiste à configurer l’espace de travail à partir d’un connecteur Facebook sur le site Merge1. Pour plus d’informations sur la configuration de l’espace de travail à partir du connecteur Facebook, voir [Merge1 tiers](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Workplace%20from%20Facebook%20User%20Guide%20.pdf).

Une fois que vous avez cliqué sur **enregistrer & terminer**, vous êtes redirigé vers le centre de conformité Microsoft 365, sur la page **mappage utilisateur** de l’Assistant connecteur.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : mapper les utilisateurs et terminer l’installation du connecteur

Pour mapper les utilisateurs et terminer l’installation du connecteur dans le centre de conformité Microsoft 365, procédez comme suit :

1. Sur la page **connecter des utilisateurs externes à des utilisateurs de Microsoft 365** , activez le mappage utilisateur automatique. Les éléments de l’espace de travail incluent une propriété appelée *courrier électronique* qui contient des adresses de messagerie pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur de Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Sur la page consentement de l' **administrateur** , cliquez sur le bouton **fournir le consentement** . Vous serez redirigé vers le site Microsoft. Cliquez sur **accepter** pour fournir le consentement.
  
   Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de boîte aux lettres dans votre organisation. Pour fournir le consentement de l’administrateur, vous devez être connecté avec les informations d’identification d’un administrateur général Microsoft 365, puis accepter la demande de consentement. Si vous n’êtes pas connecté en tant qu’administrateur général, vous pouvez accéder à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) et vous connecter à l’aide des informations d’identification d’administrateur général pour accepter la demande.

3. Cliquez sur **suivant**, vérifiez vos paramètres, puis accédez à la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-workplace-from-facebook-connector"></a>Étape 4 : surveiller l’espace de travail à partir d’un connecteur Facebook

Une fois que vous avez créé l’espace de travail à partir du connecteur Facebook, vous pouvez afficher l’état du connecteur dans le centre de conformité Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Cliquez sur l’onglet **connecteurs** , puis sélectionnez l' **espace de travail à partir du connecteur Facebook** pour afficher la page de menu volant, qui contient les propriétés et les informations relatives au connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’État du connecteur. Ce journal contient des informations sur les données qui ont été importées dans le Cloud Microsoft.

## <a name="known-issues"></a>Problèmes connus

- Pour le moment, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus importants sera disponible ultérieurement.
