---
title: Configurer un connecteur pour archiver des données LinkedIn
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/06/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Découvrez comment les administrateurs peuvent configurer & utiliser un connecteur natif pour importer des données à partir d’une page d’entreprise LinkedIn vers Microsoft 365.
ms.openlocfilehash: de39d0e3e95164a39f9aed1a227ab15f6e4fd7d6
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64937232"
---
# <a name="set-up-a-connector-to-archive-linkedin-data"></a>Configurer un connecteur pour archiver des données LinkedIn

Utilisez un connecteur dans le portail de conformité Microsoft Purview pour importer et archiver des données à partir de pages LinkedIn Company. Une fois que vous avez configuré et configuré un connecteur, il se connecte au compte pour la page LinkedIn Company spécifique une fois toutes les 24 heures. Le connecteur convertit les messages publiés sur la page Entreprise en message électronique, puis importe ces éléments dans une boîte aux lettres dans Microsoft 365.

Une fois les données de page LinkedIn Company stockées dans une boîte aux lettres, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation du litige, la recherche de contenu, l’archivage In-Place, l’audit et Microsoft 365 stratégies de rétention aux données LinkedIn. Par exemple, vous pouvez rechercher ces éléments à l’aide de la recherche de contenu ou associer la boîte aux lettres de stockage à un consignateur dans un cas de découverte électronique Microsoft Purview (Premium). La création d’un connecteur pour importer et archiver des données LinkedIn dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Le rôle Administrateur du connecteur de données doit être attribué à l’utilisateur qui crée un connecteur page d’entreprise LinkedIn. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Vous devez disposer des informations d’identification de connexion (adresse e-mail, numéro de téléphone et mot de passe) d’un compte d’utilisateur LinkedIn qui est administrateur de la page d’entreprise LinkedIn que vous souhaitez archiver. Vous utilisez ces informations d’identification pour vous connecter à LinkedIn lors de la configuration du connecteur.

- Le connecteur LinkedIn peut importer un total de 200 000 éléments en une seule journée. S’il y a plus de 200 000 éléments LinkedIn par jour, aucun de ces éléments n’est importé dans Microsoft 365.

## <a name="create-a-linkedin-connector"></a>Créer un connecteur LinkedIn

1. Accédez aux <https://compliance.microsoft.com> pages **de l’entreprise Data connectorsLinkedIn** > , puis cliquez dessus.

2. Dans la page produit **des pages d’entreprise LinkedIn** , cliquez sur **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation** , sélectionnez **Accepter**.

4. Dans la page **Se connecter avec LinkedIn** , cliquez sur **Se connecter avec LinkedIn**.

   La page de connexion LinkedIn s’affiche.

   ![Page de connexion LinkedIn.](../media/LinkedInSigninPage.png)

5. Dans la page de connexion LinkedIn, entrez l’adresse e-mail (ou le numéro de téléphone) et le mot de passe du compte LinkedIn associé à la page d’entreprise que vous souhaitez archiver, puis cliquez sur **Se connecter**.

   Une page d’Assistant s’affiche avec la liste de toutes les pages d’entreprise LinkedIn associées au compte auquel vous vous êtes connecté. Un connecteur ne peut être configuré que pour une seule page d’entreprise. Si votre organisation a plusieurs pages d’entreprise LinkedIn, vous devez créer un connecteur pour chacune d’elles.

   ![Une page contenant la liste des pages d’entreprise LinkedIn s’affiche.](../media/LinkedInSelectCompanyPage.png)

6. Sélectionnez la page d’entreprise à partir de laquelle vous souhaitez archiver les éléments, puis cliquez sur **Suivant**.

7. Dans la page **Choisir l’emplacement de stockage**, cliquez dans la zone, sélectionnez l’adresse e-mail d’une boîte aux lettres Microsoft 365 vers laquelle les éléments LinkedIn seront importés, puis cliquez sur **Suivant**. Les éléments sont importés dans le dossier de boîte de réception de cette boîte aux lettres.

8. Cliquez sur **Suivant** pour passer en revue les paramètres du connecteur, puis cliquez sur **Terminer** pour terminer la configuration du connecteur.

Après avoir créé le connecteur, vous pouvez revenir à la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur (sélectionnez **Actualiser** si nécessaire pour mettre à jour la liste des connecteurs). La valeur de la colonne **État** est **En attente de démarrage**. Le démarrage du processus d’importation initial prend jusqu’à 24 heures. Après la première exécution et l’importation des éléments LinkedIn par le connecteur, le connecteur s’exécute toutes les 24 heures et importe tous les nouveaux éléments créés sur la page d’entreprise LinkedIn au cours des 24 heures précédentes.

Pour afficher plus de détails, sélectionnez le connecteur dans la liste de la page **Connecteurs de données** pour afficher la page de menu volant. Sous **État**, la plage de dates affichée indique le filtre d’âge qui a été sélectionné lors de la création du connecteur.

## <a name="more-information"></a>Plus d’informations

Les éléments LinkedIn sont importés dans le sous-dossier LinkedIn dans la boîte de réception de la boîte aux lettres de stockage dans Microsoft 365. Ils apparaissent sous forme de messages électroniques.