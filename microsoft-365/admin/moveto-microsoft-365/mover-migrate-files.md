---
title: 'Migrer des fichiers Google vers Microsoft 365 entreprise '
f1.keywords:
- NOCSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment migrer des fichiers Google vers Microsoft 365 entreprise à l’aide de Mover.
ms.openlocfilehash: 4bec723d024468f76bdfcc60934eb42c445fe0f5
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2022
ms.locfileid: "62825639"
---
# <a name="migrate-google-files-to-microsoft-365-for-business"></a>Migrer des fichiers Google vers Microsoft 365 entreprise 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4MhaD?autoplay=false]

Lorsque vous migrez vers Microsoft 365 entreprise, vous souhaiterez migrer vos fichiers à partir de Google Drive. Vous pouvez utiliser l’application Mover pour déplacer des fichiers à partir de lecteurs personnels et partagés. Pour plus d’informations, [voir Migration cloud de Mover](/sharepointmigration/mover-plan-migration).

> [!NOTE]
> Mover effectuera une copie des fichiers et déplacera les copies vers Microsoft 365 entreprise. Les fichiers d’origine resteront également dans Google Drives.

## <a name="before-you-start"></a>Avant de commencer

Tous les utilisateurs doivent s’être Microsoft 365 pour les entreprises et configurer leur OneDrive Entreprise. Pour ce faire, [office.com,](https://office.com) connectez-vous à l’Microsoft 365 informations d’identification de votre entreprise, puis choisissez OneDrive.

## <a name="try-it"></a>Essayez !

### <a name="install-mover"></a>Installer Mover

1. Connectez-vous à votre console d’administration Google Workspace [admin.google.com](https://admin.google.com).

1. Choose **AppsGoogle** >  **Workspace Marketplace appsAdd** >  **app to Domain Install list**.

1. Recherchez Mover et sélectionnez-le.

1. Choisissez **l’installation du** domaine, puis **continuez**.

1. Examinez les autorisations, cochez la case pour accepter les termes, puis sélectionnez **Autoriser, choisir** **Suivant**, puis **Terminé**.

### <a name="create-connectors-and-run-the-migration"></a>Créer des connecteurs et exécuter la migration

1. Revenir aux **applications Google Workspace Marketplace**.
1. Actualisez votre navigateur et sélectionnez **l’application Mover** .
1. Faites défiler vers le bas et choisissez le lien de navigation universelle.
1. **Sélectionnez Autoriser un nouveau connecteur**, **recherchez G Suite (administrateur)** et choisissez **Autoriser**.
1. Modifiez **le nom complet**, si vous le souhaitez, puis **sélectionnez Autoriser**.
1. Choisissez un compte d’administrateur Google, examinez les autorisations, puis sélectionnez **Autoriser**.

    Mover affiche le nombre de lecteurs d’équipe et d’utilisateurs détectés. 

1. Sous **Sélectionner la destination**, choisissez **Autoriser un nouveau** connecteur, **Office 365** et **sélectionnez Autoriser**.
1. Pour accorder des autorisations à l’application Mover dans votre Azure Active Directory, accédez à [aka.ms/Office365MoverAuth](https://aka.ms/Office365MoverAuth).
1. **Sélectionnez Office 365 Mover**, **Autorisations**, **Accorder le consentement administrateur pour votre entreprise**.
1. Choisissez votre compte, examinez les autorisations, puis sélectionnez **Accepter**.
1. Choose **Properties** and verify that **User assignment required?** is turned on.
1. Revenir à l’application Mover, modifier le nom **complet, si** vous le souhaitez, choisir **Autoriser, puis** sélectionner un compte d’administrateur Microsoft.

    Mover vous informe du nombre de sites SharePoint Online (ou SPO) et d’utilisateurs qu’il a découverts.
1. Choisissez **Continuer le programme d’installation de** la migration, **sélectionnez Ajouter** des utilisateurs, **puis découvrir et ajouter automatiquement des utilisateurs**.

    L’application Mover tentera de maser les lecteurs du chemin d’accès source dans Google au chemin d’accès de destination dans Microsoft 365. 

    Si un lecteur ne maque pas automatiquement, ajoutez son chemin de destination à un fichier CSV, que nous utiliserons ultérieurement pour migrer le lecteur partagé vers une bibliothèque de documents SharePoint. 

1. Dans ce cas, nous avons ajouté un site SharePoint appelé Fichiers migrés et pris note de l’URL de la page de documents. 
1. Nous avons ensuite créé un fichier CSV au format Chemin d’accès source, Chemin de destination et Balises. 

    Pour plus [d’informations, voir aka.ms/movercsv](/sharepointmigration/mover-create-migration-csv).

    Lorsque vous ajoutez l’URL du chemin d’accès de destination, supprimez tout le texte après documents partagés. Par exemple, cette URL complète ne fonctionnera pas : `https://TENANT01.sharepoint.com/sites/SiteName/Shared Documents/Forms/AllItems.aspx`

    Remplacez-la par : `https://TENANT01.sharepoint.com/sites/SiteName/Shared Documents`

1. Une fois votre fichier CSV prêt, sélectionnez **Actions de migration**, Ajouter à **la migration**, **Choisir un fichier à télécharger**.
1. Accédez à votre fichier CSV, sélectionnez-le, puis choisissez **Ouvrir**.
1. Sélectionnez les lecteurs utilisateur dont vous souhaitez migrer les fichiers, puis **sélectionnez Démarrer la migration des utilisateurs**.
1. Examinez les informations de migration, choisissez quand commencer la migration, acceptez les conditions générales **, puis** sélectionnez **Continuer**.

L’application Mover vous informe lorsque le processus de migration est terminé.