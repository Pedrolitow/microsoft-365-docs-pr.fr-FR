---
title: Configurer un connecteur pour archiver des données LinkedIn
description: Découvrez comment les administrateurs peuvent configurer & utiliser un connecteur natif pour importer des données d’une page d’entreprise LinkedIn vers Microsoft 365.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 04/06/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- tier3
- purview-compliance
- data-connectors
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e8ce0b5223fe57f6496a59545daf6458406b5db4
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68813172"
---
# <a name="set-up-a-connector-to-archive-linkedin-data"></a>Configurer un connecteur pour archiver des données LinkedIn

Utilisez un connecteur dans le portail de conformité Microsoft Purview pour importer et archiver des données à partir des pages LinkedIn Company. Une fois que vous avez configuré et configuré un connecteur, il se connecte au compte de la page Entreprise LinkedIn spécifique une fois toutes les 24 heures. Le connecteur convertit les messages publiés dans la page Entreprise en message électronique, puis importe ces éléments dans une boîte aux lettres dans Microsoft 365.

Une fois que les données de la page LinkedIn Company sont stockées dans une boîte aux lettres, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation pour litige, la recherche de contenu, l’archivage In-Place, l’audit et les stratégies de rétention Microsoft 365 aux données LinkedIn. Par exemple, vous pouvez rechercher ces éléments à l’aide de la recherche de contenu ou associer la boîte aux lettres de stockage à un dépositaire dans un cas Microsoft Purview eDiscovery (Premium). La création d’un connecteur pour importer et archiver des données LinkedIn dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- L’utilisateur qui crée un connecteur page d’entreprise LinkedIn doit se voir attribuer le rôle Connecteur de données Administration. Ce rôle est requis pour ajouter des connecteurs dans la page **Connecteurs de données** du portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les portails defender et de conformité » dans [Rôles et groupes de rôles dans les portails de conformité Microsoft 365 Defender et Microsoft Purview](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-defender-and-compliance-portals). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle de Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Vous devez disposer des informations d’identification de connexion (adresse e-mail ou numéro de téléphone et mot de passe) d’un compte d’utilisateur LinkedIn administrateur de la page d’entreprise LinkedIn que vous souhaitez archiver. Vous utilisez ces informations d’identification pour vous connecter à LinkedIn lors de la configuration du connecteur.

- Le connecteur LinkedIn peut importer un total de 200 000 éléments en une seule journée. S’il y a plus de 200 000 éléments LinkedIn par jour, aucun de ces éléments n’est importé dans Microsoft 365.

## <a name="create-a-linkedin-connector"></a>Créer un connecteur LinkedIn

1. Accédez à <https://compliance.microsoft.com> , puis sélectionnez **Connecteurs** >  de données Pages **LinkedIn Company**.

2. Dans la page de produit **des pages d’entreprise LinkedIn** , sélectionnez **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation du service** , sélectionnez **Accepter**.

4. Dans la page **Se connecter avec LinkedIn** , sélectionnez **Se connecter avec LinkedIn**.

   La page de connexion LinkedIn s’affiche.

   ![Page de connexion LinkedIn.](../media/LinkedInSigninPage.png)

5. Dans la page de connexion LinkedIn, entrez l’adresse e-mail (ou le numéro de téléphone) et le mot de passe du compte LinkedIn associé à la page d’entreprise que vous souhaitez archiver, puis sélectionnez **Se connecter**.

   Une page de l’Assistant s’affiche avec la liste de toutes les pages d’entreprise LinkedIn associées au compte auquel vous vous êtes connecté. Un connecteur ne peut être configuré que pour une page d’entreprise. Si votre organisation a plusieurs pages d’entreprise LinkedIn, vous devez créer un connecteur pour chacune d’elles.

   ![Une page avec une liste de pages d’entreprise LinkedIn s’affiche.](../media/LinkedInSelectCompanyPage.png)

6. Sélectionnez la page d’entreprise à partir de laquelle vous souhaitez archiver les éléments, puis sélectionnez **Suivant**.

7. Dans la page **Choisir l’emplacement de stockage** , sélectionnez dans la zone, sélectionnez l’adresse e-mail d’une boîte aux lettres Microsoft 365 dans laquelle les éléments LinkedIn seront importés, puis sélectionnez **Suivant**. Les éléments sont importés dans le dossier boîte de réception de cette boîte aux lettres. La boîte aux lettres utilisée doit avoir une licence Exchange Online Plan 1 ou Plan 2.

8. Sélectionnez **Suivant** pour passer en revue les paramètres du connecteur, puis sélectionnez **Terminer** pour terminer la configuration du connecteur.

Après avoir créé le connecteur, vous pouvez revenir à la page **Connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur (sélectionnez **Actualiser** si nécessaire pour mettre à jour la liste des connecteurs). La valeur de la colonne **État** est **En attente de démarrage**. Le processus d’importation initial prend jusqu’à 24 heures. Après la première exécution et l’importation des éléments LinkedIn, le connecteur s’exécute toutes les 24 heures et importe tous les nouveaux éléments créés dans la page Entreprise LinkedIn au cours des 24 heures précédentes.

Pour afficher plus de détails, sélectionnez le connecteur dans la liste de la page **Connecteurs de données** pour afficher la page de menu volant. Sous **État**, la plage de dates affichée indique le filtre d’âge sélectionné lors de la création du connecteur.

## <a name="more-information"></a>Plus d’informations

Les éléments LinkedIn sont importés dans le sous-dossier LinkedIn dans la boîte de réception de la boîte aux lettres de stockage dans Microsoft 365. Ils apparaissent sous forme de messages électroniques.
