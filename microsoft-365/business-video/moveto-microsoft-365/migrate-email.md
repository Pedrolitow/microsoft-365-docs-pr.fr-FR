---
title: Migrer le courrier électronique et le calendrier d’entreprise à partir de Google Workspace
f1.keywords:
- NOCSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
- admindeeplinkMAC
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment migrer le courrier électronique, les contacts et le calendrier de Google Workspace vers Microsoft 365 entreprise.
ms.openlocfilehash: 58037d033c35bad97d5b18dc408e5450340d0c25
ms.sourcegitcommit: f88a0ec621e7d9bc5f376eeaf70c8a9800711f88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2021
ms.locfileid: "59357193"
---
# <a name="migrate-business-email-and-calendar-from-google-workspace"></a>Migrer le courrier électronique et le calendrier d’entreprise à partir de Google Workspace

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LPt6?autoplay=false]

Vous pouvez utiliser une migration d’administration vers Exchange Online à partir de Google Workspace. Vous pouvez migrer le courrier en une seule fois ou par étapes. Les étapes suivantes montrent comment migrer les données de courrier à la fois. Pour plus d’informations, [voir Effectuer une migration G Suite.](/exchange/mailbox-migration/perform-g-suite-migration)

Le processus de migration prend plusieurs étapes et peut prendre de plusieurs heures à quelques jours en fonction de la quantité de données que vous migrez.

## <a name="try-it"></a>Essayez !

### <a name="create-a-google-service-account"></a>Créer un compte de service Google

1. À l’aide d’un navigateur Chrome, connectez-vous à votre console d’administration Google Workspace [admin.google.com](https://admin.google.com). 
1. Dans un nouvel onglet ou une nouvelle fenêtre, accédez à la page [Comptes de](https://console.developers.google.com/iam-admin/serviceaccounts) service. 
1. Sélectionnez **Créer un** projet, nommez le projet, puis choisissez **Créer.** 
1. Sélectionnez **Créer un compte de service,** entrez un nom, choisissez **Créer,** puis **Terminé**. 
1. Ouvrez le menu **Actions,** **sélectionnez Modifier** et prenez note de l’ID unique. Vous aurez besoin de cet ID plus tard dans le processus. 
1. Ouvrez la section **Afficher la délégation à l’échelle du** domaine. 
1. Sélectionnez Activer la délégation à l’échelle du domaine **G Suite,** entrez un nom de produit pour l’écran de consentement, puis sélectionnez **Enregistrer.** 

    > [!NOTE]
    > Le nom du produit n’est pas utilisé par le processus de migration, mais est nécessaire pour l’enregistrer dans la boîte de dialogue.     

1. Ouvrez **de nouveau le** menu Actions et **sélectionnez Créer une clé.** 
1. Choose **JSON,** then **Create**. 

     La clé privée est enregistrée dans le dossier de téléchargement de votre appareil.
 
1. Sélectionnez **Fermer**. 

### <a name="enable-api-usage-for-the-project"></a>Activer l’utilisation de l’API pour le projet

1. Accédez à [la page API.](https://console.developers.google.com/apis/library) 
1. Dans la barre de recherche, entrez **l’API Gmail.**
1. Sélectionnez-le, puis choisissez **Activer.**
1. Répétez ce processus pour l’API Calendrier Google, l’API Contacts et l’API Contacts. 

### <a name="grant-access-to-the-service-account"></a>Accorder l’accès au compte de service

1. Revenir à la console d’administration Google Workspace. 
1. Sélectionnez **Sécurité,** faites défiler vers le bas et ouvrez les **contrôles d’API.** 
1. Faites défiler vers le bas et **sélectionnez Gérer la délégation à l’échelle du domaine.**
1. Sélectionnez **Ajouter nouveau** et entrez l’ID client que vous avez pris note précédemment.
1. Entrez ensuite les étendues OAuth pour les API Google. Ceux-ci sont disponibles [aka.ms/GoogleWorkspaceMigration](/exchange/mailbox-migration/perform-g-suite-migration#grant-access-to-the-service-account-for-your-google-tenant) l’étape 5 et sont les suivantes :

    `https://mail.google.com/,https://www.googleapis.com/auth/calendar,https://www.google.com/m8/feeds/,https://www.googleapis.com/auth/gmail.settings.sharing`
 
1. Choose **Authorize**. 

### <a name="create-a-sub-domain-for-mail-going-to-microsoft-365"></a>Créer un sous-domaine pour les messages envoyés Microsoft 365

1. Revenir à la console **d’administration Google Workspace.**
1. Select **Domains**, **Manage domains**, then, **Add a domain alias**. 
1. Entrez un alias de domaine comme `m365.contoso.com` .
1. Ensuite, **sélectionnez Continuer et vérifiez la propriété du domaine.** 

    La vérification de domaine ne prend généralement que quelques minutes, mais elle peut prendre jusqu’à 48 heures.

1. Go to the [Centre d'administration Microsoft 365](https://admin.microsoft.com).
1. Dans la Centre d'administration Microsoft 365, dans le navigation gauche, sélectionnez Afficher tous les domaines  >  **Paramètres,** puis  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>Ajouter **un domaine.** 
1. Entrez le sous-domaine que vous avez créé précédemment, puis **sélectionnez Utiliser ce domaine.** 
1. Pour connecter le domaine, sélectionnez **Continuer.** 
1. Faites défiler vers le bas et prenez note des enregistrements MX, CNAME et TXT. 
1. Revenir à la **console d’administration Google.**
1. Select **Domains**, select **Manage domains**, **Verify Details** and then, **Manage domain**. 
1. Dans le navigation de gauche, choisissez **DNS et** faites défiler vers le bas **jusqu’aux enregistrements de ressources personnalisés.** 
1. Ouvrez la dropdown du type d’enregistrement et sélectionnez **MX,** entrez ou copiez-collez les informations d’enregistrement MX que vous avez précédemment notées, puis choisissez **Ajouter**. 
1. Répétez le processus pour l’enregistrement CNAME et l’enregistrement TXT. 

    L’application de ces modifications peut prendre un certain temps.  

1. Revenir à l’endroit où vous vous êtes Centre d'administration Microsoft 365, puis sélectionnez **Continuer**. 

Votre domaine est maintenant installé.  

### <a name="create-email-aliases-in-microsoft-365"></a>Créer des alias de messagerie dans Microsoft 365

Avant de commencer la migration, vous devez créer des alias de messagerie pour vos utilisateurs avec le nouveau sous-domaine. 

1. Pour commencer l’étape  suivante, dans l’Assistant Ajouter des domaines dans le Centre d'administration Microsoft 365, **sélectionnez Go to Active users**. 
1. Sélectionnez un utilisateur, puis **gérez le nom d’utilisateur et le courrier électronique.** 
1. Dans ladown **Domains (Domaines),** sélectionnez le sous-domaine que vous avez précédemment créé. 
1. Entrez un nom d’utilisateur, **sélectionnez Ajouter,** **Enregistrer les modifications** et fermer la fenêtre. 

    Répétez ce processus pour chaque utilisateur. 

### <a name="start-the-migration-process"></a>Démarrer le processus de migration

Une fois que vous avez terminé, vous êtes prêt à migrer. 

1. Dans le navigation gauche du <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365,</a>faites défiler vers le bas jusqu’aux centres d’administration, puis sélectionnez **Exchange**. 
1. Sous **les destinataires**, choisissez **la migration,** sélectionnez **Nouveau,** **Migrer vers Exchange Online,** choisissez **Migration G Suite,** puis **Suivant**. 
1. Créez un fichier CSV avec une liste des boîtes aux lettres que vous souhaitez migrer. Assurez-vous que le fichier suit ce format : 

    ```CSV
    EmailAddress
    will@fabrikaminc.net
    user123@fabrikaminc.net
    ```

      Pour plus [d’informations, voir aka.ms/GoogleWorkspaceMigration](/exchange/mailbox-migration/perform-g-suite-migration#start-a-g-suite-migration-batch-with-the-exchange-admin-center-eac). 

1. Sélectionnez **Choisir** un fichier, accédez au fichier CSV, choisissez-le, sélectionnez **Ouvrir,** puis **Suivant**. 
1. Vérifiez l’adresse de messagerie de l’administrateur que vous souhaitez utiliser pour le test. 
1. Sélectionnez **Choisir** un fichier, accédez au fichier JSON que vous avez créé précédemment (généralement dans le dossier Téléchargements de votre ordinateur), choisissez-le, sélectionnez **Ouvrir,** puis **Suivant**. 
1. Entrez un nom dans le **champ Nouveau nom de lot de migration.**
1. Entrez le sous-domaine que vous avez créé dans le champ de domaine de **remise** cible, sélectionnez **Suivant,** puis **Nouveau**. 
1. Une fois les informations enregistrées, sélectionnez **OK.** 

    Vous pouvez désormais afficher l’état de votre migration. 

1. Après un certain temps, en fonction du nombre d’utilisateurs que vous migrez, sélectionnez **Actualiser**. 
1. Une fois que l’état est **devenu Synchronisé,** **sélectionnez Terminer ce lot de migration,** puis **Oui**. 
1. Une fois le processus terminé, votre statut est **terminé.** 
1. Si vous le souhaitez, vous pouvez sélectionner **Afficher les détails** pour plus d’informations sur la migration. 
1. Sélectionnez **Fermer**. 
1. Ouvrez Outlook pour vérifier que tous les e-mails de Google Workspace ont été correctement migrés.
Vous pouvez également répéter cette situation pour les éléments de calendrier et les contacts.
