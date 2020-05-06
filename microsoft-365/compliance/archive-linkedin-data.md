---
title: Configurer un connecteur pour archiver des données LinkedIn
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Configurez un connecteur pour importer des données LinkedIn vers Microsoft 365 afin de pouvoir utiliser des outils de conformité tels que la conservation légale, la recherche de contenu et les stratégies de rétention.
ms.openlocfilehash: 7d88d366ea19be7d158a04edc7d7fb11dca7bab9
ms.sourcegitcommit: e55e4747d3b838baacab8985aefc24aac245c431
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44043345"
---
# <a name="set-up-a-connector-to-archive-linkedin-data"></a>Configurer un connecteur pour archiver des données LinkedIn

Utilisez un connecteur dans le centre de conformité Microsoft 365 pour importer et archiver des données à partir des pages de la société LinkedIn. Une fois que vous avez configuré et configuré un connecteur, celui-ci se connecte au compte de la page de la société LinkedIn spécifique une fois toutes les 24 heures. Le connecteur convertit les messages publiés sur la page de l’entreprise en message électronique, puis importe ces éléments dans une boîte aux lettres dans Microsoft 365.

Une fois que les données de la page de la société LinkedIn sont stockées dans une boîte aux lettres, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, la recherche de contenu, l’archivage inaltérable, l’audit et les stratégies de rétention 365 Microsoft dans les données LinkedIn. Par exemple, vous pouvez rechercher ces éléments à l’aide de la recherche de contenu ou associer la boîte aux lettres de stockage à un dépositaire dans un cas avancé de découverte électronique. La création d’un connecteur pour importer et archiver des données LinkedIn dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="before-you--begin"></a>Avant de commencer

- Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de boîte aux lettres dans votre organisation. Pour accepter cette demande, accédez à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent), connectez-vous à l’aide des informations d’identification d’un administrateur général Microsoft 365, puis acceptez la demande.

- L’utilisateur qui crée un connecteur de page de société LinkedIn doit disposer du rôle d’exportation d’importation de boîte aux lettres dans Exchange Online. Cela est nécessaire pour ajouter des connecteurs dans la page **connecteurs de données** dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

- Vous devez disposer des informations d’identification de connexion (adresse de messagerie ou numéro de téléphone et mot de passe) d’un compte d’utilisateur de LinkedIn qui est administrateur de la page de la société LinkedIn que vous souhaitez archiver. Vous utilisez ces informations d’identification pour vous connecter à LinkedIn lors de la configuration du connecteur.

## <a name="create-a-linkedin-connector"></a>Créer un connecteur LinkedIn

1. Accédez à <https://compliance.microsoft.com> , puis cliquez sur **Data Connectors** > **LinkedIn Company pages**.

2. Sur la page produit de l' **entreprise LinkedIn** , cliquez sur **Ajouter un connecteur**.

3. Sur la page **conditions de service** , sélectionnez **accepter**.

4. Sur la page **se connecter avec LinkedIn** , cliquez sur **se connecter avec LinkedIn**.

   La page de connexion à LinkedIn s’affiche.

   ![Page de connexion à LinkedIn](../media/LinkedInSigninPage.png)

5. Sur la page de connexion LinkedIn, entrez l’adresse de messagerie (ou le numéro de téléphone) et le mot de passe du compte LinkedIn associé à la page de l’entreprise que vous souhaitez archiver, puis cliquez sur **se connecter**.

   Une page d’Assistant s’affiche avec la liste de toutes les pages de la société LinkedIn associées au compte auquel vous vous êtes connecté. Un connecteur ne peut être configuré que pour une seule page de la société. Si votre organisation dispose de plusieurs pages d’entreprise LinkedIn, vous devez créer un connecteur pour chacune d’entre elles.

   ![Une page avec une liste de pages de la société LinkedIn s’affiche.](../media/LinkedInSelectCompanyPage.png)

6. Sélectionnez la page de la société à partir de laquelle vous souhaitez archiver des éléments, puis cliquez sur **suivant**.

7. Dans la page **choisir l’emplacement de stockage** , cliquez dans la zone, sélectionnez l’adresse de messagerie d’une boîte aux lettres Microsoft 365 dans laquelle les éléments LinkedIn seront importés, puis cliquez sur **suivant**. Les éléments sont importés dans le dossier boîte de réception de cette boîte aux lettres.

8. Sur l' **autorisation fournir un administrateur**, cliquez sur **accorder le consentement** , puis suivez les étapes. Vous devez être un administrateur général pour accorder le consentement du service d’importation Office 365 pour accéder aux données de votre organisation.

9. Cliquez sur **suivant** pour passer en revue les paramètres du connecteur, puis cliquez sur **Terminer** pour terminer l’installation du connecteur.

Après avoir créé le connecteur, vous pouvez revenir à la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur (sélectionnez **Actualiser** si nécessaire pour mettre à jour la liste des connecteurs). La valeur dans la colonne d' **État** est en **attente de démarrage**. Le processus initial d’importation doit prendre jusqu’à 24 heures. Après la première exécution du connecteur et l’importation des éléments LinkedIn, le connecteur s’exécute une fois toutes les 24 heures et importe les nouveaux éléments créés sur la page de la société LinkedIn dans les 24 heures qui précèdent.

Pour afficher plus de détails, sélectionnez le connecteur dans la liste sur la page **connecteurs de données** pour afficher la page de menu volant. Sous **État**, la plage de dates affichée indique le filtre d’âge qui a été sélectionné lors de la création du connecteur.

## <a name="more-information"></a>Plus d’informations

Les éléments LinkedIn sont importés dans le sous-dossier LinkedIn de la boîte de réception de la boîte aux lettres de stockage dans Microsoft 365. Elles apparaissent sous forme de messages électroniques.
