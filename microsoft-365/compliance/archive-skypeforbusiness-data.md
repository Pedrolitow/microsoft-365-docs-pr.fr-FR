---
title: Configurer un connecteur pour archiver des Skype Entreprise de données dans Microsoft 365
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
description: Découvrez comment configurer et utiliser un connecteur dans le Centre de conformité Microsoft 365 pour importer et archiver des données de Skype Entreprise à Microsoft 365.
ms.openlocfilehash: 3f772bfa7b59eac7292cd869aee2688ac1a132b6
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59176100"
---
# <a name="set-up-a-connector-to-archive-skype-for-business-data"></a>Configurer un connecteur pour archiver les Skype Entreprise données

Utilisez un connecteur Veritas dans le Centre de conformité Microsoft 365 pour importer et archiver des données à partir de la plateforme Skype Entreprise vers les boîtes aux lettres des utilisateurs de Microsoft 365 organisation. Veritas fournit un connecteur [Skype Entreprise](https://www.veritas.com/en/au/insights/merge1/skype-for-business) qui est configuré pour capturer des éléments à partir de la source de données tierce (régulièrement) et importer ces éléments dans Microsoft 365. Le connecteur convertit le contenu tel que les messages entre les utilisateurs, les conversations permanentes et les messages de conférence de Skype Entreprise au format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois Skype Entreprise données stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention. L’utilisation d’Skype Entreprise pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-skype-for-business-data"></a>Vue d’ensemble de l’archivage Skype Entreprise données

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données Skype Entreprise dans Microsoft 365.

![Flux de travail d’archivage pour Skype Entreprise données.](../media/SkypeforBusinessConnectorWorkflow.png)

1. Votre organisation collabore avec Skype Entreprise pour configurer et configurer un site Skype Entreprise web.

2. Toutes les 24 heures, les Skype Entreprise sont copiés sur le site Veritas Merge1. Le connecteur convertit également les Skype Entreprise au format de message électronique.

3. Le connecteur Skype Entreprise que vous créez dans le Centre de conformité Microsoft 365, se connecte au site Veritas Merge1 tous les jours et transfère le contenu Skype Entreprise vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage automatique des utilisateurs, comme décrit à l’étape [3.](#step-3-map-users-and-complete-the-connector-setup) Un sous-dossier du dossier Boîte de réception nommé **Skype Entreprise** est créé dans les boîtes aux lettres utilisateur et les éléments sont importés dans ce dossier. Pour ce faire, le connecteur utilise la valeur de la *propriété Email.* Chaque Skype Entreprise contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Créez un compte Merge1 pour les connecteurs Microsoft. Pour ce faire, contactez le support [technique Veritas.](https://www.veritas.com/form/requestacall/ms-connectors-contact.html) Vous devez vous inscrire à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur Skype Entreprise à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres à l’Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs** de données dans la Centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="step-1-set-up-the-skype-for-business-connector"></a>Étape 1 : Configurer le connecteur Skype Entreprise de connexion

La première étape consiste à accéder à la page **Connecteurs** de données dans la Centre de conformité Microsoft 365 et à créer un connecteur pour Skype Entreprise données.

1. Go to <https://compliance.microsoft.com> and click **Data connectors**  >  **Skype Entreprise**.

2. Dans la page **Skype Entreprise** description du produit, cliquez **sur Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-skype-for-business-on-the-veritas-merge1-site"></a>Étape 2 : Configurer le Skype Entreprise sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur Skype Entreprise sur le site Veritas Merge1. Pour plus d’informations sur la configuration du connecteur Skype Entreprise, voir [merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Skype%20for%20Business%20%20User%20Guide.pdf).

Une fois que vous avez **cliqué sur &** terminé, la **page** Mappage de l’utilisateur dans l’Assistant connecteur du Centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Masons les utilisateurs et terminez la configuration du connecteur

Pour maîtr les utilisateurs et terminer la configuration du connecteur dans le Centre de conformité Microsoft 365, suivez les étapes suivantes :

1. Dans la **page Ma Skype Entreprise aux utilisateurs Microsoft 365 utilisateurs,** activez le mappage utilisateur automatique. Les Skype Entreprise incluent une propriété appelée *Email*, qui contient les adresses de messagerie des utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez **sur** Suivant, examinez vos paramètres, puis allez à la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-skype-for-business-connector"></a>Étape 4 : Surveiller le connecteur Skype Entreprise de connexion

Après avoir créé le connecteur Skype Entreprise, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to <https://compliance.microsoft.com/> and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le **connecteur Skype Entreprise** pour afficher la page de présentation, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.
