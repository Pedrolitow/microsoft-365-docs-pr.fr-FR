---
title: Configurer un connecteur pour archiver les données des réunions zoom dans Microsoft 365
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
ms.collection: M365-security-compliance
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données des réunions Veritas Zoom dans Microsoft 365. Cela vous permet d’archiver les données de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 87163a3bc0ce46a1ba50df8803a01bedea9bc3b4
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67820655"
---
# <a name="set-up-a-connector-to-archive-zoom-meetings-data"></a>Configurer un connecteur pour archiver les données des réunions zoom

Utilisez un connecteur Veritas dans le portail de conformité Microsoft Purview pour importer et archiver des données de Zoom Meetings vers des boîtes aux lettres utilisateur de votre organisation Microsoft 365. Veritas fournit un connecteur [Zoom Meetings](https://globanet.com/zoom/) configuré pour capturer des éléments à partir de la source de données tierce (régulièrement) et importer ces éléments dans Microsoft 365. Le connecteur convertit le contenu des réunions (y compris les conversations, les fichiers enregistrés et les métadonnées) du compte Zoom Meetings au format de message électronique, puis importe ces éléments dans des boîtes aux lettres utilisateur dans Microsoft 365.

Une fois les données des réunions zoom stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation des litiges, la découverte électronique, les stratégies de rétention et les étiquettes de rétention, ainsi que la conformité des communications. L’utilisation d’un connecteur Zoom Meetings pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-zoom-meetings-data"></a>Vue d’ensemble de l’archivage des données des réunions zoom

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données des réunions zoom dans Microsoft 365.

![Zoom sur le flux de travail d’archivage des réunions.](../media/ZoomMeetingsConnectorWorkflow.png)

1. Votre organisation travaille avec Zoom Meetings pour configurer et configurer un site Zoom Meetings.

2. Une fois toutes les 24 heures, les éléments de réunion des réunions Zoom sont copiés sur le site Veritas Merge1. Le connecteur convertit également le contenu des réunions au format de message électronique.

3. Le connecteur Zoom Meetings que vous créez dans le portail de conformité, se connecte au Veritas Merge1 tous les jours et transfère les messages de réunion vers un emplacement de stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments de réunion convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* et du mappage automatique des utilisateurs, comme décrit à l’étape 3. Un nouveau sous-dossier dans le dossier Boîte de réception nommé **Réunions de zoom** est créé dans les boîtes aux lettres utilisateur et les éléments de réunion sont importés dans ce dossier. Pour ce faire, le connecteur utilise la valeur de la propriété *Email*. Chaque élément de réunion contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de la réunion.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Veritas Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez le [support technique Veritas](https://globanet.com/ms-connectors-contact). Vous vous connecterez à ce compte lorsque vous créerez le connecteur à l’étape 1.

- Obtenez le nom d’utilisateur et le mot de passe du compte Zoom Business ou Zoom Entreprise de votre organisation. Vous devez vous connecter à ce compte à l’étape 2 lorsque vous configurez le connecteur Zoom Meetings.

- Créez les applications suivantes dans la [Place de marché Zoom](https://marketplace.zoom.us) :

  - Application OAuth

  - Application JWT

  Après avoir créé ces applications, la plateforme Zoom génère un ensemble d’informations d’identification uniques utilisées pour générer les jetons. Ces jetons sont utilisés pour authentifier le connecteur lorsqu’il se connecte à votre compte Zoom et copie les éléments vers le site Merge1. Vous utiliserez ces jetons lorsque vous configurerez le connecteur Zoom à l’étape 2.

  Pour obtenir des instructions pas à pas sur la création des applications OAuth et JWT, consultez le [Guide d’utilisation des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Zoom%20Meetings%20User%20Guide%20.pdf).

- L’utilisateur qui crée le connecteur Zoom Meetings à l’étape 1 (et le termine à l’étape 3) doit se voir attribuer le rôle de connecteur de données Administration. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données Veritas est en préversion publique dans les environnements GCC dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="step-1-set-up-the-zoom-meetings-connector"></a>Étape 1 : Configurer le connecteur Zoom Meetings

La première étape consiste à accéder aux **connecteurs de données** dans le portail de conformité et à créer un connecteur Zoom Meetings.

1. Accédez, [https://compliance.microsoft.com](https://compliance.microsoft.com/) puis cliquez sur **Réunions de zoom** **des connecteurs** >  de données.

2. Dans la page de description **du produit Zoom Meetings** , cliquez sur **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-zoom-meetings-connector"></a>Étape 2 : Configurer le connecteur Zoom Meetings

La deuxième étape consiste à configurer le connecteur Zoom Meetings sur le site Merge1. Pour plus d’informations sur la configuration du connecteur Zoom Meetings sur le site Veritas Merge1, consultez le [Guide utilisateur des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Zoom%20Meetings%20User%20Guide%20.pdf).

Une fois que vous avez cliqué sur **Enregistrer & Terminer**, la page De **mappage utilisateur** de l’Assistant Connecteur dans le portail de conformité s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Mapper les utilisateurs et terminer la configuration du connecteur

1. Dans la page **Mapper des utilisateurs externes à des utilisateurs Microsoft 365** , activez le mappage automatique des utilisateurs.

   Les éléments Zoom Meetings incluent une propriété appelée *Email* qui contient des adresses e-mail pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur

2. Cliquez sur **Suivant**, passez en revue vos paramètres et accédez à la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur.

## <a name="step-4-monitor-the-zoom-meetings-connector"></a>Étape 4 : Surveiller le connecteur Zoom Meetings

Après avoir créé le connecteur Zoom Meetings, vous pouvez afficher l’état du connecteur dans le portail de conformité.

1. Accédez et [https://compliance.microsoft.com](https://compliance.microsoft.com) cliquez sur **Connecteurs de données** dans le volet de navigation gauche.

2. Cliquez sur l’onglet **Connecteurs** , puis sélectionnez le connecteur **Zoom Meetings** pour afficher la page de menu volant. Cette page contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur les données qui ont été importées dans le cloud Microsoft. Pour plus d’informations, consultez [Afficher les journaux d’administration pour les connecteurs de données](data-connector-admin-logs.md).

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments supérieurs à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.

- Pour que le connecteur Zoom Meetings fonctionne, vous devez activer les enregistrements lors de la configuration des réunions de zoom.