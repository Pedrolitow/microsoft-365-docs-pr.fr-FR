---
title: Configurer un connecteur pour archiver des données LinkedIn
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Découvrez comment les administrateurs peuvent configurer & utiliser un connecteur natif pour importer des données à partir d’une page d’entreprise LinkedIn Microsoft 365.
ms.openlocfilehash: 944a8bcbd06a07653ccf5e98e28807d279b66023
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322196"
---
# <a name="set-up-a-connector-to-archive-linkedin-data"></a>Configurer un connecteur pour archiver des données LinkedIn

Utilisez un connecteur dans le Centre de conformité Microsoft 365 pour importer et archiver des données à partir de pages linkedIn Company. Une fois que vous avez configuré et configuré un connecteur, il se connecte au compte de la page de la société LinkedIn spécifique toutes les 24 heures. Le connecteur convertit les messages publiés dans la page Société en un message électronique, puis importe ces éléments dans une boîte aux lettres dans Microsoft 365.

Une fois que les données de la page Société LinkedIn sont stockées dans une boîte aux lettres, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, la recherche de contenu, l’archivage In-Place, l’audit et les stratégies de rétention Microsoft 365 aux données LinkedIn. Par exemple, vous pouvez rechercher ces éléments à l’aide de la recherche de contenu ou associer la boîte aux lettres de stockage à un dépositaire dans Advanced eDiscovery cas. La création d’un connecteur pour importer et archiver des données LinkedIn dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Le rôle d’administrateur du connecteur de données doit être attribué à l’utilisateur qui crée un connecteur de page d’entreprise LinkedIn. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le Centre de conformité Microsoft 365. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et conformité » dans Autorisations dans le Centre de sécurité [& conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le Centre de conformité Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Vous devez avoir les informations d’identification de connexion (adresse de messagerie, numéro de téléphone et mot de passe) d’un compte d’utilisateur LinkedIn qui est administrateur de la page de société LinkedIn que vous souhaitez archiver. Vous utilisez ces informations d’identification pour vous inscrire à LinkedIn lors de la configuration du connecteur.

- Le connecteur LinkedIn peut importer un total de 200 000 éléments en une seule journée. S’il y a plus de 200 000 éléments LinkedIn dans une journée, aucun de ces éléments n’est importé dans Microsoft 365.

## <a name="create-a-linkedin-connector"></a>Créer un connecteur LinkedIn

1. Go to <https://compliance.microsoft.com> and then click **Data connectorsLinkedIn** >  **Company pages**.

2. Dans la page **produit des pages d’entreprise LinkedIn** , cliquez **sur Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation** , sélectionnez **Accepter**.

4. Dans la page **Se connectez avec LinkedIn** , cliquez **sur Se connectez avec LinkedIn**.

   La page de signature LinkedIn s’affiche.

   ![Page de sign-in LinkedIn.](../media/LinkedInSigninPage.png)

5. Dans la page de signature LinkedIn, entrez l’adresse e-mail (ou le numéro de téléphone) et le mot de passe du compte LinkedIn associé à la page d’entreprise que vous souhaitez archiver, puis cliquez sur Se **connecter**.

   Une page de l’Assistant s’affiche avec la liste de toutes les pages d’entreprise LinkedIn associées au compte à qui vous vous êtes connecté. Un connecteur ne peut être configuré que pour une page d’entreprise. Si votre organisation possède plusieurs pages d’entreprise LinkedIn, vous devez créer un connecteur pour chacune d’elles.

   ![Une page avec une liste de pages d’entreprise LinkedIn s’affiche.](../media/LinkedInSelectCompanyPage.png)

6. Sélectionnez la page de l’entreprise dans qui vous souhaitez archiver des éléments, puis cliquez sur **Suivant**.

7. Dans **la page** Choisir l’emplacement de stockage, cliquez dans la zone, sélectionnez l’adresse de messagerie d’une boîte aux lettres Microsoft 365 dans qui les éléments LinkedIn seront importés, puis cliquez sur **Suivant**. Les éléments sont importés dans le dossier de boîte de réception de cette boîte aux lettres.

8. Cliquez **sur Suivant** pour passer en revue les paramètres du connecteur, puis cliquez sur **Terminer** pour terminer la configuration du connecteur.

Après avoir créé le connecteur, vous pouvez revenir à la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur (sélectionnez **Actualiser** si nécessaire pour mettre à jour la liste des connecteurs). La valeur de la colonne **État** est **En attente de démarrage**. Le processus d’importation initial prend jusqu’à 24 heures. Après la première fois que le connecteur s’exécute et importe les éléments LinkedIn, il s’exécute toutes les 24 heures et importe tous les nouveaux éléments créés sur la page de société LinkedIn au cours des 24 heures précédentes.

Pour afficher plus de détails, sélectionnez le connecteur dans la liste de la page **Connecteurs** de données pour afficher la page de présentation. Sous **État**, la plage de dates qui s’affiche indique le filtre d’âge qui a été sélectionné lors de la création du connecteur.

## <a name="more-information"></a>Informations supplémentaires

Les éléments LinkedIn sont importés dans le sous-foldeur LinkedIn dans la boîte de réception de la boîte aux lettres de stockage Microsoft 365. Ils s’affichent sous la mesure de messages électroniques.