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
localization_priority: Normal
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Découvrez comment les administrateurs peuvent configurer & utiliser un connecteur natif pour importer des données à partir d’une page d’entreprise LinkedIn vers Microsoft 365.
ms.openlocfilehash: 9f6cb2c6d5c47559f1fda13b6d03bfed3afe6fa2
ms.sourcegitcommit: 7d4aa58ae9fc893825b6e648fa3f072c3ac59628
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2021
ms.locfileid: "49790178"
---
# <a name="set-up-a-connector-to-archive-linkedin-data"></a>Configurer un connecteur pour archiver des données LinkedIn

Utilisez un connecteur dans le Centre de conformité Microsoft 365 pour importer et archiver des données à partir de pages linkedIn Company. Une fois que vous avez configuré et configuré un connecteur, il se connecte au compte de la page de la société LinkedIn spécifique toutes les 24 heures. Le connecteur convertit les messages publiés dans la page Entreprise en un message électronique, puis importe ces éléments dans une boîte aux lettres dans Microsoft 365.

Une fois que les données de la page Société LinkedIn sont stockées dans une boîte aux lettres, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, la recherche de contenu, l’archivage In-Place, l’audit et les stratégies de rétention Microsoft 365 aux données LinkedIn. Par exemple, vous pouvez rechercher ces éléments à l’aide de la recherche de contenu ou associer la boîte aux lettres de stockage à un dépositaire dans un cas Advanced eDiscovery. La création d’un connecteur pour importer et archiver des données LinkedIn dans Microsoft 365 peut aider votre organisation à respecter les politiques gouvernementales et réglementaires.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Le rôle Importation/Exportation de boîte aux lettres doit être attribué à l’utilisateur qui crée un connecteur de page d’entreprise LinkedIn dans Exchange Online. Cela est nécessaire pour ajouter des connecteurs dans la page **Connecteurs de** données dans le Centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) [Créer](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ».

- Vous devez avoir les informations d’identification de connexion (adresse de messagerie, numéro de téléphone et mot de passe) d’un compte d’utilisateur LinkedIn qui est administrateur de la page de société LinkedIn que vous souhaitez archiver. Vous utilisez ces informations d’identification pour vous inscrire à LinkedIn lors de la configuration du connecteur.

- Le connecteur LinkedIn peut importer un total de 200 000 éléments en une seule journée. S’il y a plus de 200 000 éléments LinkedIn par jour, aucun de ces éléments ne sera importé dans Microsoft 365.

## <a name="create-a-linkedin-connector"></a>Créer un connecteur LinkedIn

1. Go to <https://compliance.microsoft.com> and then click Data **connectors**  >  **LinkedIn Company pages**.

2. Dans la page **produit des pages d’entreprise LinkedIn,** cliquez **sur Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** sélectionnez **Accepter.**

4. Dans la page **Se connectez avec LinkedIn,** cliquez **sur Se connectez avec LinkedIn.**

   La page de signature LinkedIn s’affiche.

   ![Page de sign-in LinkedIn](../media/LinkedInSigninPage.png)

5. Dans la page de signature LinkedIn, entrez l’adresse e-mail (ou le numéro de téléphone) et le mot de passe du compte LinkedIn associé à la page d’entreprise que vous souhaitez archiver, puis cliquez sur Se **connectez.**

   Une page de l’Assistant s’affiche avec la liste de toutes les pages de société LinkedIn associées au compte à qui vous vous êtes connecté. Un connecteur ne peut être configuré que pour une page d’entreprise. Si votre organisation possède plusieurs pages d’entreprise LinkedIn, vous devez créer un connecteur pour chacune d’elles.

   ![Une page avec une liste de pages d’entreprise LinkedIn s’affiche](../media/LinkedInSelectCompanyPage.png)

6. Sélectionnez la page de la société à partir de qui vous souhaitez archiver des éléments, puis cliquez sur **Suivant**.

7. Dans **la** page Choisir l’emplacement de stockage, cliquez dans la zone, sélectionnez l’adresse de messagerie d’une boîte aux lettres Microsoft 365 dans qui les éléments LinkedIn seront importés, puis cliquez sur **Suivant**. Les éléments sont importés dans le dossier de boîte de réception de cette boîte aux lettres.

8. Cliquez **sur Suivant** pour passer en revue les paramètres du connecteur, puis cliquez sur **Terminer** pour terminer la configuration du connecteur.

Après avoir créé le connecteur, vous pouvez revenir à la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur (sélectionnez **Actualiser** si nécessaire pour mettre à jour la liste des connecteurs). La valeur de la **colonne État** est En attente **de démarrage.** Le processus d’importation initial prend jusqu’à 24 heures. Après la première fois que le connecteur s’exécute et importe les éléments LinkedIn, le connecteur s’exécute une fois toutes les 24 heures et importe tous les nouveaux éléments créés sur la page de société LinkedIn au cours des 24 heures précédentes.

Pour afficher plus de détails, sélectionnez le connecteur dans la liste de la page **Connecteurs** de données pour afficher la page de présentation. Sous **État,** la plage de dates qui s’affiche indique le filtre d’âge qui a été sélectionné lors de la création du connecteur.

## <a name="more-information"></a>Plus d’informations

Les éléments LinkedIn sont importés dans le sous-foldeur LinkedIn dans la boîte de réception de la boîte aux lettres de stockage dans Microsoft 365. Ils s’affichent sous la mesure de messages électroniques.
