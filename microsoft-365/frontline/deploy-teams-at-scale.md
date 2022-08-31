---
title: Déployer des équipes à grande échelle pour les travailleurs de première ligne
author: LanaChin
ms.author: v-lanachin
ms.reviewer: rahuldey
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Découvrez comment déployer des équipes à grande échelle pour les employés de première ligne de votre organisation.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: e833def27e88a9f59c756bd769a09191e9b2dd5c
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67467380"
---
# <a name="deploy-teams-at-scale-for-frontline-workers-in-microsoft-teams"></a>Déployer des équipes à grande échelle pour les travailleurs de première ligne

> [!NOTE]
> Cette fonctionnalité est actuellement disponible en préversion publique. Si vous souhaitez participer, contactez-nous à [dscale@microsoft.com](mailto:dscale@microsoft.com).

## <a name="overview"></a>Vue d’ensemble
 
Votre organisation peut avoir un grand nombre d’équipes que vous utilisez pour favoriser la communication et la collaboration entre votre personnel de première ligne, qui sont réparties dans différents magasins, emplacements et rôles. Actuellement, il n’existe pas de solution simple pour déployer, configurer et gérer ces équipes et ces utilisateurs à grande échelle.

Nous créons une solution pour permettre aux administrateurs de déployer et de gérer des équipes à grande échelle.

Voici une vue d’ensemble des fonctionnalités disponibles aujourd’hui pour la création et la gestion d’un grand nombre d’équipes à la fois et de ce que nous prévoyons dans un avenir proche.

||Disponible aujourd’hui |Plus tard en 2022  |
|---------|---------|---------|
|**Nombre d’équipes que vous pouvez créer par lot**|Jusqu’à 100 Go |Jusqu’à 500|
|**Nombre d’utilisateurs que vous pouvez ajouter par équipe**|Jusqu’à 25 téraoctets (To) par locataire|Jusqu’à 25 téraoctets (To) par locataire|

Le déploiement d’équipes à grande échelle vous permet d’effectuer les opérations suivantes :

- Créez des équipes en utilisant des modèles préétablis ou vos propres modèles personnalisés.
- Ajoutez des utilisateurs aux équipes en tant que propriétaires ou membres.
- Gérez les équipes à grande échelle en ajoutant ou en supprimant des utilisateurs des équipes existantes.
- Restez informé par e-mail, y compris la saisie semi-automatique, l’état et les erreurs (le cas échéant). Vous pouvez choisir d’informer jusqu’à cinq personnes de l’état de chaque lot d’équipes que vous déployez. Les propriétaires et les membres de l’équipe sont automatiquement avertis lorsqu’ils sont ajoutés à une équipe.

## <a name="how-to-deploy-teams-at-scale"></a>Comment déployer des équipes à grande échelle

> [!NOTE]
> Avant de déployer vos équipes, assurez-vous que tous les propriétaires d’équipes disposent d’une licence Teams.

Suivez ces étapes pour déployer un grand nombre d’équipes à la fois.

### <a name="step-1-prepare-your-csv-files"></a>Étape 1 : Préparer vos fichiers CSV

Vous devez créer deux fichiers CSV pour chaque lot d’équipes que vous déployez :

- **Fichier CSV qui définit les équipes que vous créez**. Ce fichier doit contenir les colonnes requises, dans l’ordre suivant, en commençant par la première colonne :

    |Nom de colonne  |Description  |
    |---------|---------|
    |**Nom de l’équipe**|Nom de l’équipe.|
    |**ID d’équipe existant**|Si vous ajoutez ou supprimez des utilisateurs d’une équipe existante, spécifiez l’ID d’équipe de l’équipe.|
    |**Visibility**|Que l’équipe soit publique (toute personne de votre organisation peut participer) ou privée (les utilisateurs ont besoin de l’approbation des propriétaires de l’équipe pour rejoindre). Les options sont **publiques** et **privées**.|
    |**ID de modèle d’équipe**|Si vous créez une équipe à partir d'un modèle préétabli ou personnalisé, spécifiez l'ID du modèle d'équipe. Consultez [Démarrage avec des modèles d’équipe dans le Centre d’administration Teams](/microsoftteams/get-started-with-teams-templates-in-the-admin-console) pour obtenir une liste des ID et modèles d’équipe prédéfinie. Si vous souhaitez utiliser le modèle d’équipe par défaut standard, laissez ce champ vide.|

- **Fichier CSV qui mappe les utilisateurs que vous ajoutez à chaque équipe**. Ce fichier doit contenir les colonnes requises, dans l’ordre suivant, en commençant par la première colonne :

    |Nom de colonne  |Description  |
    |---------|---------|
    |**Nom complet de l’utilisateur**|Nom d’affichage de l’utilisateur.|
    |**UPN ou ID utilisateur**|Nom d’utilisateur principal (UPN) de l’utilisateur. Par exemple, contoso.com.|
    |**Nom de l’équipe**|Nom de l’équipe.|
    |**ActionType**|Si vous ajoutez ou supprimez l’utilisateur de l’équipe. Les options sont **AddMember** et **RemoveMember**.|
    |**Propriétaire ou membre**|Indique si l’utilisateur est un propriétaire d’équipe ou un membre de l’équipe. Les options sont **Propriétaire** et **Membre**.|

#### <a name="examples"></a>Exemples

Utilisez les exemples suivants pour vous aider à créer vos fichiers CSV. Ici, nous avons nommé les fichiers, Teams.csv et Users.csv.

**Teams.csv**

|Nom de l’équipe|ID d’équipe existant|Visibilité|ID de modèle d’équipe|
|---------|---------|---------|---------|
|Contoso Store 1||Public|com.microsoft.teams.template.retailStore|
|Contoso Store 2||Public|com.microsoft.teams.template.retailStore|
|Contoso Store 3||Public|com.microsoft.teams.template.retailStore|
|Contoso Store 4||Public|com.microsoft.teams.template.retailStore|
|Contoso Store 5||Public|com.microsoft.teams.template.ManageAProject|
|Contoso Store 6||Public|com.microsoft.teams.template.ManageAProject|
|Contoso Store 7||Public||
|Contoso Store 8||Private|com.microsoft.teams.template.OnboardEmployees|
|Contoso Store 9||Private|com.microsoft.teams.template.OnboardEmployees|
|Contoso Store 10||Private|com.microsoft.teams.template.OnboardEmployees|

**Utilisateurs.csv**

|Nom complet de l’utilisateur |UPN ou ID utilisateur|Nom de l’équipe|ActionType|Propriétaire ou membre|
|---------|---------|---------|---------|---------|
|Avery Howard|averyh@contoso.com|Contoso Store 1|AddMember|Propriétaire|
|Casey Jensen|caseyj@contoso.com|Contoso Store 2|AddMember|Propriétaire|
|Jesse Irwin|jessiei@contoso.com|Contoso Store 3|AddMember|Propriétaire|
|Manjeet Bhatia|manjeetb@contoso.com|Contoso Store 4|AddMember|Propriétaire|
|Mikaela Lee|mikaelal@contoso.com|Contoso Store 5|AddMember|Propriétaire|
|Morgan Conners|morganc@contoso.com|Contoso Store 6|AddMember|Member|
|Oscar Ward|oscarw@contoso.com|Contoso Store 7|AddMember|Member|
|René Pelletier|renep@contoso.com|Contoso Store 8|AddMember|Member|
|Sydney Mattos|sydneym@contoso.com|Contoso Store 9|AddMember|Member|
|Violet Martinez|violetm@contoso.com|Contoso Store 10|AddMember|Member|

### <a name="step-2-deploy-your-teams"></a>Étape 2 : Déployer votre site isolé

Maintenant que vous avez créé vos fichiers CSV, vous êtes prêt à configurer votre environnement et à déployer vos équipes.

Vous utilisez l’applet ```New-CsBatchTeamsDeployment``` de commande pour envoyer un lot d’équipes à créer. Un ID d’orchestration est généré pour chaque lot. Vous pouvez ensuite utiliser l’applet ```Get-CsBatchTeamsDeployment``` de commande pour suivre la progression et l’état de chaque lot.

1. Installez PowerShell version 7 ou ultérieure. Pour obtenir des conseils pas à pas, consultez [l’installation de PowerShell sur Windows](/powershell/scripting/install/installing-powershell-on-windows).
1. Exécutez PowerShell en mode Administrateur.
1. Exécutez ce qui suit pour désinstaller tout module Teams PowerShell précédemment installé.

    ```powershell
    Uninstall-module -Name MicrosoftTeams -Force -Allversions
    ```

    Si vous recevez un message d’erreur, vous êtes déjà défini. Passez à l’étape suivante.
1. Téléchargez et installez la [dernière préversion du module Teams PowerShell](https://www.powershellgallery.com/packages/MicrosoftTeams). Vous devez exécuter la version 4.3.1 (préversion) ou une version ultérieure.  

1. Exécutez ce qui suit pour vous connecter à Teams.

    ```powershell
    Connect-MicrosoftTeams
    ```

    Lorsque vous y êtes invité, connectez-vous à l’aide de vos informations d’identification d’administrateur.

1. Exécutez la commande suivante pour obtenir une liste des commandes dans le module Teams PowerShell.

    ```powershell
    Get-Command -Module MicrosoftTeams
    ```

    Vérifiez cela ```New-CsBatchTeamsDeployment``` et ```Get-CsBatchTeamsDeploymentStatus``` sont répertoriés.

1. Exécutez la commande suivante pour déployer un lot d’équipes. Dans cette commande, vous spécifiez le chemin d’accès à vos fichiers CSV et les adresses e-mail de cinq destinataires maximum pour les informer de ce déploiement.

    ```powershell
    New-CsBatchTeamsDeployment -TeamsFilePath "Your CSV file path" -UsersFilePath "Your CSV file path" -UsersToNotify "Email addresses" 
    ```

    Par exemple :

    ```powershell
    New-CsBatchTeamsDeployment -TeamsFilePath "C:\dscale\Teams.csv" -UsersFilePath "C:\dscale\Users.csv" -UsersToNotify "adminteams@contoso.com,adelev@contoso.com"
    ```

    Les destinataires recevront des notifications par e-mail concernant l’état du déploiement. L’e-mail contient l’ID d’orchestration pour le lot que vous avez envoyé et toutes les erreurs qui se sont produites.

1. Exécutez ce qui suit pour vérifier l’état du lot que vous avez envoyé.

    ```powershell
    Get-CsBatchTeamsDeploymentStatus -OrchestrationId "OrchestrationId"
    ```

## <a name="send-us-feedback"></a>Nous envoyer des commentaires

Votre avis est important pour nous. Facilité d’utilisation, fiabilité, performances&mdash;nous accueillons tout !

Email [dscale@microsoft.com](mailto:dscale@microsoft.com) et incluez votre ID d’orchestration et votre fichier d’erreur, le cas échéant.

## <a name="related-articles"></a>Articles connexes

- [Aperçu de Teams PowerShell](/microsoftteams/teams-powershell-overview)
