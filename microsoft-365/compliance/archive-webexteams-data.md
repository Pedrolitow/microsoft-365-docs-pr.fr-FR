---
title: Configurer un connecteur pour les données Webex Teams dans Microsoft 365
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données à partir du connecteur Webex Teams de Veritas dans Microsoft 365. Ce connecteur vous permet d’archiver des données à partir de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier3
- purview-compliance
- data-connectors
ms.openlocfilehash: 3f98591f6c98397d3a3605faf537011ebc733f28
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68812116"
---
# <a name="set-up-a-connector-to-archive-webex-teams-data"></a>Configurer un connecteur pour archiver les données Webex Teams

Utilisez un connecteur Veritas dans le portail de conformité Microsoft Purview pour importer et archiver des données de Webex Teams dans des boîtes aux lettres utilisateur dans votre organisation Microsoft 365. Veritas fournit un connecteur [Webex Teams](https://globanet.com/webex-teams/) configuré pour capturer les éléments de communication Webex Teams et les importer dans Microsoft 365. Le connecteur convertit le contenu de Webex Teams, tel que les conversations 1:1, les conversations de groupe, les conversations de canal et les pièces jointes du compte Webex Teams de votre organisation, au format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois les données Webex Teams stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention et la conformité des communications. L’utilisation d’un connecteur Webex Teams pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="overview-of-archiving-webex-teams-data"></a>Vue d’ensemble de l’archivage des données Webex Teams

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver des données Webex Teams dans Microsoft 365.

![Flux de travail d’archivage pour les données Webex Teams.](../media/WebexTeamsConnectorWorkflow.png)

1. Votre organisation travaille avec Webex Teams pour configurer un site Webex Teams.

2. Une fois toutes les 24 heures, les éléments Webex Teams sont copiés sur le site Veritas Merge1. Le connecteur convertit également les éléments Webex Teams au format de message électronique.

3. Le connecteur Webex Teams que vous créez dans le portail de conformité se connecte à Veritas Merge1 tous les jours et transfère les éléments Webex Teams vers un emplacement de stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe des éléments dans les boîtes aux lettres d’utilisateurs spécifiques en utilisant la valeur de la propriété *Email* du mappage automatique d’utilisateurs, comme décrit à [l’étape 3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier dans le dossier Boîte de réception nommé **Webex Teams** est créé dans les boîtes aux lettres utilisateur, et les éléments sont importés dans ce dossier. Pour ce faire, le connecteur utilise la valeur de la propriété *Email*. Chaque élément Webex Teams contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Veritas Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez le [support technique Veritas](https://globanet.com/ms-connectors-contact). Vous vous connecterez à ce compte lorsque vous créerez le connecteur à l’étape 1.

- Créez une application sur [https://developer.webex.com/](https://developer.webex.com) pour extraire des données à partir de votre compte Webex Teams. Pour obtenir des instructions pas à pas sur la création de l’application, consultez [Merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf)

   Lorsque vous créez cette application, la plateforme Webex génère un ensemble d’informations d’identification uniques. Ces informations d’identification sont utilisées à l’étape 2 lorsque vous configurez le connecteur Webex Teams sur le site Global Merge1.

- L’utilisateur qui crée le connecteur Webex Teams à l’étape 1 (et l’exécute à l’étape 3) doit se voir attribuer le rôle de Administration connecteur de données. Ce rôle est requis pour ajouter des connecteurs dans la page **Connecteurs de données** du portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les portails defender et de conformité » dans [Rôles et groupes de rôles dans les portails de conformité Microsoft 365 Defender et Microsoft Purview](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-defender-and-compliance-portals). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle de Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données Veritas est en préversion publique dans les environnements GCC dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui se trouvent en dehors de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune déclaration selon laquelle l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes à FEDRAMP.

## <a name="step-1-set-up-the-webex-teams-connector"></a>Étape 1 : Configurer le connecteur Webex Teams

La première étape consiste à accéder aux **connecteurs de données** et à configurer le connecteur [Webex Teams](https://globanet.com/webex-teams/) .

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis sélectionnez **Connecteurs** >  de données **Webex Teams**.

2. Dans la page de description du produit **Webex Teams** , sélectionnez **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation du service** , sélectionnez **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis sélectionnez **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-webex-teams-connector-on-the-veritas-merge1-site"></a>Étape 2 : Configurer le connecteur Webex Teams sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur Webex Teams sur le site Merge1. Pour plus d’informations sur la configuration du connecteur Webex Teams, consultez [Merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf).

Une fois que vous avez sélectionné **Enregistrer & Terminer**, la page **Mappage des** utilisateurs de l’Assistant Connecteur dans le portail de conformité s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Mapper les utilisateurs et terminer la configuration du connecteur

Pour mapper les utilisateurs et terminer la configuration du connecteur dans le portail de conformité, procédez comme suit :

1. Dans la page **Mapper des utilisateurs Webex Teams aux utilisateurs Microsoft 365** , activez le mappage automatique des utilisateurs. Les éléments Webex Teams incluent une propriété appelée *Email*, qui contient les adresses e-mail des utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Sélectionnez **Suivant**, passez en revue vos paramètres, puis accédez à la page **Connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-webex-teams-connector"></a>Étape 4 : Surveiller le connecteur Webex Teams

Après avoir créé le connecteur Webex Teams, vous pouvez afficher l’état du connecteur dans le portail de conformité.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) et sélectionnez **Connecteurs de données** dans la navigation de gauche.

2. Sélectionnez l’onglet **Connecteurs** , puis sélectionnez le connecteur **Webex Teams** pour afficher la page de menu volant. Cette page contient les propriétés et les informations relatives au connecteur.

3. Sous **État du connecteur avec la source**, sélectionnez le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur les données importées dans le cloud Microsoft. Pour plus d’informations, consultez [Afficher les journaux d’activité d’administration pour les connecteurs de données](data-connector-admin-logs.md).

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments d’une taille supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.
