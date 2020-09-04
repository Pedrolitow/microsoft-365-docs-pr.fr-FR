---
title: Configurer un connecteur pour archiver les données Symphony dans Microsoft 365
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
ROBOTS: NOINDEX, NOFOLLOW
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données à partir de Globanet Symphony dans Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 de sorte que vous puissiez utiliser les fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 29af0cda6d1f6b194c13047382ab7e01b6b200dc
ms.sourcegitcommit: a6625f76e8f19eebd9353ed70c00d32496ec06eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "47361795"
---
# <a name="set-up-a-connector-to-archive-symphony-data-preview"></a>Configurer un connecteur pour archiver les données Symphony (aperçu)

Utilisez un connecteur Globanet dans le centre de conformité Microsoft 365 pour importer et archiver des données Symphony vers des boîtes aux lettres utilisateur dans votre organisation Microsoft 365. Symphony est une plateforme de messagerie et de collaboration utilisée dans le secteur des services financiers. Globanet fournit un [connecteur de données Symphony](https://globanet.com/symphony) dans le centre de conformité Microsoft 365 que vous pouvez configurer pour capturer des éléments à partir de la source de données tierce (de manière régulière), puis les importer dans les boîtes aux lettres utilisateur. Le connecteur convertit le contenu d’un élément du compte Symphony en format de message électronique, puis importe l’élément dans une boîte aux lettres dans Microsoft 365.

Une fois que les communications Symphony sont stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention et la conformité des communications L’utilisation d’un connecteur Symphony pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-symphony-data"></a>Vue d’ensemble de l’archivage des données Symphony

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur de données pour archiver les communications Symphony dans Microsoft 365.

![Flux de travail d’archivage Symphony](../media/SymphonyConnectorWorkflow.png)

1. Votre organisation travaille avec Symphony pour installer et configurer un site Symphony.

2. Une fois toutes les 24 heures, les messages de conversation provenant d’Symphony sont copiés sur le site Globanet Merge1. Le connecteur convertit également le contenu d’un message de conversation au format d’un message électronique.

3. Le connecteur Symphony que vous créez dans le centre de conformité Microsoft 365, se connecte au site Merge1 Globanet tous les jours et transfère les messages vers un emplacement de stockage Azure sécurisé dans le Cloud Microsoft.

4. Le connecteur importe les éléments de message convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *email* du mappage utilisateur automatique, comme décrit à l’étape 3. Un nouveau sous-dossier dans le dossier boîte de réception nommé **Symphony** est créé dans les boîtes aux lettres utilisateur, et les éléments de message sont importés dans ce dossier. Le connecteur effectue cette opération à l’aide de la valeur de la propriété *email* . Chaque message de conversation contient cette propriété, qui est renseignée avec l’adresse de messagerie de chaque participant du message de conversation.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Globanet Merge1 en acceptant les conditions générales du connecteur Symphony. Pour ce faire, contactez le [support client Globanet](https://globanet.com/contact-us). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur Symphony à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle d’exportation d’importation de boîte aux lettres dans Exchange Online. Ce rôle est nécessaire pour ajouter des connecteurs sur la page **connecteurs de données** dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="step-1-set-up-the-symphony-connector"></a>Étape 1 : configurer le connecteur Symphony

La première étape consiste à accéder à la page **connecteurs de données** dans le centre de conformité Microsoft 365 et à créer un connecteur pour les données Symphony.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **connecteurs de données**  >  **Symphony**.

2. Sur la page Description du produit **Symphony** , cliquez sur **Ajouter un connecteur**.

3. Sur la page **conditions de service** , cliquez sur **accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="configure-the-symphony-connector-on-the-globanet-merge1-site"></a>Configurer le connecteur Symphony sur le site Merge1 Globanet

La deuxième étape consiste à configurer le connecteur Symphony sur le site Merge1. Pour plus d’informations sur la configuration du connecteur Symphony dans le site Globanet Merge1, voir [Merge1 le Guide de l’utilisateur des connecteurs tiers](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Symphony%20User%20Guide%20.pdf).

Une fois que vous avez cliqué sur **enregistrer & terminer**, vous êtes renvoyé au centre de conformité Microsoft 365 sur la page **mappage des utilisateurs** de l’Assistant connecteur.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : mapper les utilisateurs et terminer l’installation du connecteur

Pour mapper les utilisateurs et terminer le connecteur configuré dans le centre de conformité Microsoft 365, procédez comme suit :

1. Sur la page **connecter des utilisateurs externes à des utilisateurs de Microsoft 365** , activez le mappage utilisateur automatique. Les éléments Symphony incluent une propriété appelée *courrier électronique*, qui contient des adresses de messagerie pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur de Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Sur la page consentement de l' **administrateur** , cliquez sur le bouton **fournir le consentement** . Vous serez redirigé vers le site Microsoft. Cliquez sur **accepter** pour fournir le consentement.

   Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de boîte aux lettres dans votre organisation. Pour fournir le consentement de l’administrateur, vous devez être connecté avec les informations d’identification d’un administrateur général Microsoft 365, puis accepter la demande de consentement. Si vous n’êtes pas connecté en tant qu’administrateur général, vous pouvez accéder à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) et vous connecter à l’aide des informations d’identification d’administrateur général pour accepter la demande.

3. Cliquez sur **suivant**, vérifiez vos paramètres, puis accédez à la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-symphony-connector"></a>Étape 4 : surveiller le connecteur Symphony

Après avoir créé le connecteur Symphony, vous pouvez afficher l’état du connecteur dans le centre de conformité Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Cliquez sur l’onglet **connecteurs** , puis sélectionnez le connecteur **Symphony** pour afficher la page de menu volant, qui contient les propriétés et les informations relatives au connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’État du connecteur. Ce journal contient des informations sur les données qui ont été importées dans le Cloud Microsoft.

## <a name="known-issues"></a>Problèmes connus

- Pour le moment, nous ne prenons pas en charge l’importation de pièces jointes d’une taille supérieure à 10 Mo, mais la prise en charge des éléments plus importants sera disponible ultérieurement.
