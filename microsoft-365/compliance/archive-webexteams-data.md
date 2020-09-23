---
title: Configurer un connecteur pour les données de WebEx teams dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données à partir du connecteur WebEx teams d’Globanet dans Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 de sorte que vous puissiez utiliser les fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 3d9693fd1baf990ba3ca956c8a24d8d796e80995
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48196563"
---
# <a name="set-up-a-connector-to-archive-webex-teams-data"></a>Configuration d’un connecteur pour l’archivage des données de teams WebEx

Utilisez un connecteur Globanet dans le centre de conformité Microsoft 365 pour importer et archiver des données d’une équipe WebEx vers des boîtes aux lettres utilisateur dans votre organisation Microsoft 365. Globanet fournit un connecteur [WebEx teams](https://globanet.com/webex-teams/) qui est configuré pour capturer des éléments de communication avec WebEx teams et les importer dans Microsoft 365. Le connecteur convertit le contenu de WebEx Teams, par exemple 1:1 conversations, les conversations de groupe, les conversations de canal et les pièces jointes du compte WebEx teams de votre organisation, vers un format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois que les données des équipes WebEx sont stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention et la conformité des communications. L’utilisation d’un connecteur WebEx teams pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-webex-teams-data"></a>Vue d’ensemble des données d’archivage WebEx teams

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur pour archiver les données des équipes WebEx dans Microsoft 365.

![Flux de travail d’archivage pour les données de WebEx teams](../media/WebexTeamsConnectorWorkflow.png)

1. Votre organisation travaille avec WebEx teams pour installer et configurer un site des équipes WebEx.

2. Une fois toutes les 24 heures, les éléments de teams WebEx sont copiés sur le site Merge1 Globanet. Le connecteur convertit également les éléments WebEx teams au format d’un message électronique.

3. Le connecteur WebEx teams que vous créez dans le centre de conformité Microsoft 365, se connecte au Merge1 Globanet tous les jours et transfère les éléments de teams WebEx à un emplacement de stockage Azure sécurisé dans le Cloud Microsoft.

4. Le connecteur importe des éléments dans les boîtes aux lettres d’utilisateurs spécifiques en utilisant la valeur de la propriété *email* du mappage utilisateur automatique, comme décrit à l' [étape 3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier boîte de réception nommé **WebEx teams** est créé dans les boîtes aux lettres des utilisateurs, et les éléments sont importés dans ce dossier. Le connecteur effectue cette opération à l’aide de la valeur de la propriété *email* . Chaque élément WebEx teams contient cette propriété, qui est renseignée avec l’adresse de messagerie de chaque participant de l’élément.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Globanet Merge1 pour Microsoft Connectors. Pour ce faire, contactez le [support client Globanet](https://globanet.com/ms-connectors-contact). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- Créez une application à [https://developer.webex.com/](https://developer.webex.com) pour extraire les données de votre compte WebEx Teams. Pour obtenir des instructions détaillées sur la création de l’application, reportez-vous au Guide de l' [utilisateur des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf)

   Lorsque vous créez cette application, la plateforme WebEx génère un ensemble d’informations d’identification uniques. Ces informations d’identification sont utilisées à l’étape 2 lorsque vous configurez le connecteur WebEx teams sur le site Merge1 global.

- L’utilisateur qui crée le connecteur WebEx teams à l’étape 1 (et la termine à l’étape 3) doit être affecté au rôle importation/exportation de boîte aux lettres dans Exchange Online. Ce rôle est nécessaire pour ajouter des connecteurs sur la page **connecteurs de données** dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="step-1-set-up-the-webex-teams-connector"></a>Étape 1 : configurer le connecteur WebEx teams

La première étape consiste à accéder aux connecteurs de **données** et à configurer le connecteur [WebEx teams](https://globanet.com/webex-teams/) .

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **connecteurs de données**  >  **WebEx teams**.

2. Sur la page Description du produit **WebEx teams** , cliquez sur **Ajouter un connecteur**.

3. Sur la page **conditions de service** , cliquez sur **accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-webex-teams-connector-on-the-globanet-merge1-site"></a>Étape 2 : configurer le connecteur WebEx teams sur le site Merge1 Globanet

La deuxième étape consiste à configurer le connecteur WebEx teams sur le site Merge1. Pour plus d’informations sur la configuration du connecteur WebEx Teams, reportez-vous au Guide de l' [utilisateur des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf).

Une fois que vous avez cliqué sur **enregistrer & terminer**, vous êtes redirigé vers le centre de conformité Microsoft 365, sur la page **mappage utilisateur** de l’Assistant connecteur.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : mapper les utilisateurs et terminer l’installation du connecteur

Pour mapper les utilisateurs et terminer l’installation du connecteur dans le centre de conformité Microsoft 365, procédez comme suit :

1. Sur la page **mapper les utilisateurs de teams WebEx aux utilisateurs de Microsoft 365** , activez le mappage utilisateur automatique. Les éléments de teams WebEx incluent une propriété appelée *courrier électronique*, qui contient des adresses de messagerie pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur de Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Sur la page consentement de l' **administrateur** , cliquez sur le bouton **fournir le consentement** . Vous serez redirigé vers le site Microsoft. Cliquez sur **accepter** pour fournir le consentement.
  
   Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de boîte aux lettres dans votre organisation. Pour fournir le consentement de l’administrateur, vous devez être connecté avec les informations d’identification d’un administrateur général Microsoft 365, puis accepter la demande de consentement. Si vous n’êtes pas connecté en tant qu’administrateur général, vous pouvez accéder à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) et vous connecter à l’aide des informations d’identification d’administrateur général pour accepter la demande.

3. Cliquez sur **suivant**, vérifiez vos paramètres, puis accédez à la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-webex-teams-connector"></a>Étape 4 : analyse du connecteur WebEx teams

Une fois que vous avez créé le connecteur WebEx Teams, vous pouvez afficher l’état du connecteur dans le centre de conformité Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Cliquez sur l’onglet **connecteurs** , puis sélectionnez le connecteur **WebEx teams** pour afficher la page de menu volant, qui contient les propriétés et les informations relatives au connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’État du connecteur. Ce journal contient des informations sur les données qui ont été importées dans le Cloud Microsoft.

## <a name="known-issues"></a>Problèmes connus

- Pour le moment, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus importants sera disponible ultérieurement.
