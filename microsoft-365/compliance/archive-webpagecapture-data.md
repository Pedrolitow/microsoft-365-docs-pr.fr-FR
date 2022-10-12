---
title: Configurer un connecteur pour archiver les données de page web dans Microsoft 365
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données de capture de page web à partir de Veritas dans Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
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
ms.openlocfilehash: 472282e523bec6825da711aa463fb2631d29dcae
ms.sourcegitcommit: 8d3c027592a638f411f87d89772dd3d39e92aab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68533760"
---
# <a name="set-up-a-connector-to-archive-webpage-data"></a>Configurer un connecteur pour archiver les données de page web

Utilisez un connecteur Veritas dans le portail de conformité Microsoft Purview pour importer et archiver des données à partir de pages web vers des boîtes aux lettres utilisateur de votre organisation Microsoft 365. Veritas fournit un connecteur [de capture de pages web](https://globanet.com/webpage-capture) qui capture des pages web spécifiques (et tous les liens sur ces pages) dans un site web spécifique ou un domaine entier. Le connecteur convertit le contenu de la page web au format PDF, PNG ou fichier personnalisé, puis attache les fichiers convertis à un message électronique, puis importe ces éléments de courrier dans des boîtes aux lettres utilisateur dans Microsoft 365.

Une fois le contenu de la page web stocké dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation des litiges, eDiscovery, ainsi que des stratégies de rétention et des étiquettes de rétention. L’utilisation d’un connecteur De capture de page web pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="overview-of-archiving-webpage-data"></a>Vue d’ensemble de l’archivage des données de page web

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver le contenu d’une page web dans Microsoft 365.

![Flux de travail d’archivage pour les données de page web.](../media/WebPageCaptureConnectorWorkflow.png)

1. Votre organisation travaille avec la source de page web pour configurer et configurer un site de capture de pages web.

2. Une fois toutes les 24 heures, les éléments sources de la page web sont copiés sur le site Veritas Merge1. Le connecteur convertit et attache également le contenu d’une page web à un e-mail.

3. Le connecteur De capture de page web que vous créez dans le portail de conformité, se connecte au site Veritas Merge1 tous les jours et transfère les éléments de la page web vers un emplacement de stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments de page web convertis dans les boîtes aux lettres de certains utilisateurs à l’aide de la valeur de la propriété *Email* du mappage automatique d’utilisateurs, comme décrit à [l’étape 3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier dans le dossier Boîte de réception nommé **Capture de page web** est créé dans les boîtes aux lettres de l’utilisateur, et les éléments de la page web sont importés dans ce dossier. Pour ce faire, le connecteur utilise la valeur de la propriété *Email*. Chaque élément de page web contient cette propriété, qui est remplie avec les adresses e-mail fournies lorsque vous configurez le connecteur Capture de page web à [l’étape 2](#step-2-configure-the-webpage-capture-connector-on-the-veritas-merge1-site).

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Veritas Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez le [support technique Veritas](https://www.veritas.com/content/support/). Vous vous connecterez à ce compte lorsque vous créerez le connecteur à l’étape 1.

- Vous devez utiliser la prise en charge de Veritas pour configurer un format de fichier personnalisé dans lequel convertir les éléments de page web. Pour plus d’informations, consultez le [Guide de l’utilisateur des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Web%20Page%20Capture%20User%20Guide%20.pdf).

- L’utilisateur qui crée le connecteur De capture de page web à l’étape 1 (et le termine à l’étape 3) doit se faire attribuer le rôle de connecteur de données Administration. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données Veritas est en préversion publique dans les environnements GCC dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="step-1-set-up-the-webpage-capture-connector"></a>Étape 1 : Configurer le connecteur De capture de page web

La première étape consiste à accéder aux **connecteurs de données** et à créer un connecteur pour les données sources de page web.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) la page Web **des connecteurs** >  de données, puis **sélectionnez Capture**.

2. Dans la page de description du produit **Capture de page web** , sélectionnez **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation** , sélectionnez **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis sélectionnez **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-webpage-capture-connector-on-the-veritas-merge1-site"></a>Étape 2 : Configurer le connecteur De capture de page web sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur Webpage Capture sur le site Veritas Merge1. Pour plus d’informations sur la configuration du connecteur De capture de page web, consultez le [Guide d’utilisation des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Web%20Page%20Capture%20User%20Guide%20.pdf).

Une fois que vous avez sélectionné **Enregistrer & Terminer**, la page de **mappage utilisateur** de l’Assistant Connecteur dans le portail de conformité s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Mapper les utilisateurs et terminer la configuration du connecteur

Pour mapper les utilisateurs et terminer la configuration du connecteur dans le portail de conformité, suivez les étapes ci-dessous :

1. Dans la page **Capture de page Web de carte des utilisateurs vers les utilisateurs Microsoft 365** , activez le mappage automatique des utilisateurs. Les éléments de capture de page web incluent une propriété appelée *Email*, qui contient des adresses e-mail pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Sélectionnez **Suivant**, passez en revue vos paramètres et accédez à la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur.

## <a name="step-4-monitor-the-webpage-capture-connector"></a>Étape 4 : Surveiller le connecteur de capture de page web

Après avoir créé le connecteur Webpage Capture, vous pouvez afficher l’état du connecteur dans le portail de conformité.

1. Accédez aux [https://compliance.microsoft.com](https://compliance.microsoft.com) **connecteurs de données** et sélectionnez-les dans le volet de navigation gauche.

2. Sélectionnez l’onglet **Connecteurs** , puis sélectionnez le connecteur **Capture de page web** pour afficher la page de menu volant. Cette page contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source**, **sélectionnez** le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur les données qui ont été importées dans le cloud Microsoft. Pour plus d’informations, consultez [Afficher les journaux d’administration pour les connecteurs de données](data-connector-admin-logs.md).

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments supérieurs à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.
