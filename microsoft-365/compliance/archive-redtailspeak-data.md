---
title: Configurer un connecteur pour archiver les données Red tail Speak dans Microsoft 365
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver les données Red tail Speak de Veritas vers Microsoft 365. Ce connecteur vous permet d’archiver des données à partir de sources de données tierces dans Microsoft 365. Après avoir archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces.
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
ms.openlocfilehash: 2dce46b01a35ee653c107840f430f890fde419f4
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68812700"
---
# <a name="set-up-a-connector-to-archive-redtail-speak-data"></a>Configurer un connecteur pour archiver les données Redtail Speak

Utilisez un connecteur Veritas dans le portail de conformité Microsoft Purview pour importer et archiver des données à partir de Redtail Speak dans les boîtes aux lettres utilisateur de votre organisation Microsoft 365. Veritas vous fournit un connecteur [Redtail Speak](https://globanet.com/redtail/) configuré pour capturer des éléments à partir du serveur SFTP de votre organisation où les éléments sont reçus de Redtail. Le connecteur convertit le contenu de Redtail Speak au format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois que les données Redtail Speak sont stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation pour litige, l’eDiscovery, les stratégies de rétention et les étiquettes de rétention. L’utilisation d’un connecteur Redtail Speak pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="overview-of-archiving-the-redtail-speak-data"></a>Vue d’ensemble de l’archivage des données Redtail Speak

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données Redtail Speak dans Microsoft 365.

![Flux de travail d’archivage pour les données Redtail Speak.](../media/RedtailSpeakConnectorWorkflow.png)

1. Votre organisation utilise Redtail Speak pour configurer et configurer une passerelle SMTP où les messages sont transférés quotidiennement de Redtail Speak au serveur SFTP de votre organisation.

2. Une fois toutes les 24 heures, les éléments Redtail Speak sont copiés sur le site Veritas Merge1. Le connecteur convertit également les éléments Redtail Speak au format de message électronique.

3. Le connecteur Redtail Speak que vous créez dans le portail de conformité se connecte au site Veritas Merge1 chaque jour et transfère les messages vers un emplacement de stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments Redtail Speak convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage automatique d’utilisateurs, comme décrit à [l’étape 3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier dans le dossier Boîte de réception nommé **Redtail Speak** est créé dans les boîtes aux lettres utilisateur, et les éléments sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer les éléments à l’aide de la valeur de la propriété *Email*. Chaque élément Redtail Speak contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Veritas Merge1 pour les connecteurs Microsoft. Pour créer un compte, contactez le [support technique Veritas](https://www.veritas.com/content/support/). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- À l’étape 2, vous devez spécifier le serveur SFTP de votre organisation. Cette étape est nécessaire pour que Veritas Merge1 puisse le contacter pour collecter des données Redtail Speak via SFTP.

- L’utilisateur qui crée le connecteur Redtail Speak Importer à l’étape 1 (et le termine à l’étape 3) doit se voir attribuer le rôle de Administration connecteur de données. Ce rôle est requis pour ajouter des connecteurs dans la page **Connecteurs de données** du portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les portails defender et de conformité » dans [Rôles et groupes de rôles dans les portails de conformité Microsoft 365 Defender et Microsoft Purview](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-defender-and-compliance-portals). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle de Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données Veritas est en préversion publique dans les environnements GCC dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui se trouvent en dehors de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune déclaration selon laquelle l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes à FEDRAMP.

## <a name="step-1-set-up-the-redtail-speak-connector"></a>Étape 1 : Configurer le connecteur Redtail Speak

La première étape consiste à accéder à la page **Connecteurs de données** dans le portail de conformité et à créer un connecteur pour les données Redtail Speak.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) et sélectionnez **Connecteurs** &gt; de données **Redtail Speak**.

2. Dans la page de description du produit **Redtail Speak** , sélectionnez **Ajouter un nouveau connecteur**.

3. Dans la page **Conditions d’utilisation du service** , sélectionnez **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis sélectionnez **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-redtail-speak-connector-on-the-veritas-merge1-site"></a>Étape 2 : Configurer le connecteur Redtail Speak sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur Redtail Speak sur le site Merge1. Pour plus d’informations sur la configuration du connecteur Redtail Speak, consultez [Merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Redtail%20Speak%20User%20Guide%20.pdf).

Une fois que vous avez sélectionné **Enregistrer & Terminer**, la page **Mappage des** utilisateurs de l’Assistant Connecteur dans le portail de conformité s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Mapper les utilisateurs et terminer la configuration du connecteur

Pour mapper les utilisateurs et terminer la configuration du connecteur, procédez comme suit :

1. Dans la page **Mapper les utilisateurs Redtail Speak aux utilisateurs Microsoft 365** , activez le mappage automatique des utilisateurs. Les éléments Redtail Speak incluent une propriété appelée *Email*, qui contient des adresses e-mail pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Sélectionnez **Suivant**, passez en revue vos paramètres et accédez à la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur.

## <a name="step-4-monitor-the-redtail-speak-connector"></a>Étape 4 : Surveiller le connecteur Redtail Speak

Après avoir créé le connecteur Redtail Speak, vous pouvez afficher l’état du connecteur dans le portail de conformité.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) et sélectionnez **Connecteurs de données** dans la navigation de gauche.

2. Sélectionnez l’onglet **Connecteurs** , puis sélectionnez le connecteur **Redtail Speak** pour afficher la page de menu volant. Cette page affiche les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec la source**, sélectionnez le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur les données importées dans le cloud Microsoft. Pour plus d’informations, consultez [Afficher les journaux d’activité d’administration pour les connecteurs de données](data-connector-admin-logs.md).

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments d’une taille supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.
