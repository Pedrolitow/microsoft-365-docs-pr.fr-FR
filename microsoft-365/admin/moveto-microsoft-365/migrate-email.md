---
title: Migrer la messagerie professionnelle et le calendrier à partir de Google Workspace
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
- highpri
- M365-subscription-management
- Adm_O365
ms.custom:
- VSBFY23
- AdminSurgePortfolio
- adminvideo
- admindeeplinkMAC
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment migrer le courrier électronique, les contacts et le calendrier de Google Workspace vers Microsoft 365 pour les entreprises.
ms.openlocfilehash: b0e2350c91b19e8a4097723efcfb6a34e674448b
ms.sourcegitcommit: 37e137535c4f70702afe1a5eeaa899c75ee02cfd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2022
ms.locfileid: "67661350"
---
# <a name="migrate-business-email-and-calendar-from-google-workspace"></a>Migrer la messagerie professionnelle et le calendrier à partir de Google Workspace

Consultez [l’aide de Microsoft 365 petite entreprise](https://go.microsoft.com/fwlink/?linkid=2197659) sur YouTube.

## <a name="watch-migrate-business-email-and-calendar-from-google-workspace"></a>Regarder : Migrer la messagerie et le calendrier professionnels à partir de Google Workspace

Regardez cette vidéo et d’autres encore sont disponibles sur notre [chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2198034).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LPt6?autoplay=false]

Vous pouvez utiliser une migration exécutée par l’administrateur vers Exchange Online à partir de Google Workspace. Vous pouvez migrer le courrier à la fois ou par étapes. Les étapes suivantes montrent comment migrer les données de messagerie à la fois. Pour plus d’informations, consultez [Effectuer une migration G Suite](/exchange/mailbox-migration/perform-g-suite-migration).

Le processus de migration prend plusieurs étapes et peut prendre plusieurs heures à quelques jours en fonction de la quantité de données que vous migrez.

### <a name="create-a-google-service-account"></a>Créer un compte de service Google

1. À l’aide d’un navigateur Chrome, connectez-vous à votre console d’administration Google Workspace à [admin.google.com](https://admin.google.com). 
1. Dans un nouvel onglet ou une nouvelle fenêtre, accédez à la page [Comptes de service](https://console.developers.google.com/iam-admin/serviceaccounts) . 
1. Sélectionnez **Créer un projet**, nommez le projet, puis **choisissez Créer**. 
1. Sélectionnez **Créer un compte de service**, entrez un nom, **choisissez Créer** , puis **Terminé**. 
1. Ouvrez le menu **Actions** , **sélectionnez Modifier** et prenez note de l’ID unique. Vous aurez besoin de cet ID plus tard dans le processus. 
1. Ouvrez la section **Afficher la délégation à l’échelle du domaine** . 
1. Sélectionnez **Activer la délégation À l’échelle du domaine G Suite**, entrez un nom de produit pour l’écran de consentement, puis **sélectionnez Enregistrer**. 

    > [!NOTE]
    > Le nom du produit n’est pas utilisé par le processus de migration, mais il est nécessaire d’enregistrer dans la boîte de dialogue.     

1. Rouvrez le menu **Actions** et **sélectionnez Créer une clé**. 
1. Choisissez **JSON**, puis **Créez**. 

     La clé privée est enregistrée dans le dossier de téléchargement sur votre appareil.
 
1. Sélectionnez **Fermer**. 

### <a name="enable-api-usage-for-the-project"></a>Activer l’utilisation de l’API pour le projet

1. Accédez à la [page API](https://console.developers.google.com/apis/library). 
1. Dans la barre de recherche, **entrez l’API Gmail**.
1. Sélectionnez-la, puis **choisissez Activer**.
1. Répétez ce processus pour l’API Google Calendar, l’API Personnes et l’API Contacts. 

### <a name="grant-access-to-the-service-account"></a>Accorder l’accès au compte de service

1. Revenez à la console d’administration de l’espace de travail Google. 
1. Sélectionnez **Sécurité**, faites défiler vers le bas et ouvrez **les contrôles d’API**. 
1. Faites défiler vers le bas et sélectionnez **Gérer la délégation à l’échelle du domaine**.
1. Sélectionnez **Ajouter nouveau** et entrez l’ID client que vous avez noté précédemment.
1. Entrez ensuite les étendues OAuth pour les API Google. [Celles-ci](/exchange/mailbox-migration/perform-g-suite-migration#grant-access-to-the-service-account-for-your-google-tenant) sont disponibles à aka.ms/GoogleWorkspaceMigration à l’étape 5 et sont les suivantes :

    `https://mail.google.com/,https://www.googleapis.com/auth/calendar,https://www.google.com/m8/feeds/,https://www.googleapis.com/auth/gmail.settings.sharing`
 
1. Choisissez **Autoriser**. 

### <a name="create-a-sub-domain-for-mail-going-to-microsoft-365"></a>Créer un sous-domaine pour la messagerie vers Microsoft 365

1. Revenez à la console **d’administration de l’espace de travail Google** .
1. Sélectionnez **Domaines**, **Gérer les domaines**, puis **Ajoutez un alias de domaine**. 
1. Entrez un alias de domaine comme `m365.contoso.com`.
1. Sélectionnez Ensuite **Continuer et vérifiez la propriété du domaine**. 

    La vérification du domaine ne prend généralement que quelques minutes, mais elle peut prendre jusqu’à 48 heures.

1. Accédez au [Centre d’administration Microsoft 365](https://admin.microsoft.com).
1. Dans le Centre d'administration Microsoft 365, dans le volet de navigation de gauche, **sélectionnez Afficher tous les** >  domaines **de** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**paramètres**</a>, puis **Ajoutez un domaine**. 
1. Entrez le sous-domaine que vous avez créé précédemment, puis **sélectionnez Utiliser ce domaine**. 
1. Pour connecter le domaine, sélectionnez **Continuer**. 
1. Faites défiler vers le bas et prenez note des enregistrements MX, des enregistrements CNAME et des enregistrements TXT. 
1. Revenez à la **console d’administration Google**.
1. Sélectionnez **Domaines**, **Gérer les domaines**, **Vérifier les détails** , puis Gérer le **domaine**. 
1. Dans le volet de navigation de gauche, choisissez **DNS** et faites défiler jusqu’aux **enregistrements de ressources personnalisés**. 
1. Ouvrez la liste déroulante du type d’enregistrement, sélectionnez **MX**, entrez ou copiez et collez les informations d’enregistrement MX que vous avez notées précédemment, puis choisissez **Ajouter**. 
1. Répétez le processus pour l’enregistrement CNAME et l’enregistrement TXT. 

    L’application de ces modifications peut prendre un certain temps.  

1. Revenez à l’endroit où vous vous êtes arrêté dans Centre d'administration Microsoft 365, puis **sélectionnez Continuer**. 

Votre domaine est maintenant configuré.  

### <a name="create-email-aliases-in-microsoft-365"></a>Créer des alias de messagerie dans Microsoft 365

Avant de commencer la migration, vous devez créer des alias de messagerie pour vos utilisateurs avec le nouveau sous-domaine. 

1. Pour démarrer l’étape suivante, dans l’Assistant **Ajouter des domaines** dans le Centre d'administration Microsoft 365, sélectionnez **Accéder aux utilisateurs actifs**. 
1. Sélectionnez un utilisateur, puis **gérez le nom d’utilisateur et l’e-mail**. 
1. Dans la liste déroulante **Domaines** , sélectionnez le sous-domaine que vous avez créé précédemment. 
1. Entrez un nom d’utilisateur, **sélectionnez Ajouter**, **Enregistrer les modifications** et fermez la fenêtre. 

    Répétez ce processus pour chaque utilisateur. 

### <a name="start-the-migration-process"></a>Démarrer le processus de migration

Une fois que vous avez terminé, vous êtes prêt à migrer. 

1. Dans la navigation gauche de la <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>, faites défiler jusqu’à **Administration centres**, puis sélectionnez **Exchange**. 
1. Sous **destinataires**, choisissez **migration**, sélectionnez **Nouveau**, **Migrer vers Exchange Online**, choisissez **migration G Suite**, puis **Suivant**. 
1. Créez un fichier CSV avec une liste des boîtes aux lettres que vous souhaitez migrer. Assurez-vous que le fichier suit ce format : 

    ```CSV
    EmailAddress
    will@fabrikaminc.net
    user123@fabrikaminc.net
    ```

      Pour plus d’informations, consultez [aka.ms/GoogleWorkspaceMigration](/exchange/mailbox-migration/perform-g-suite-migration#start-a-g-suite-migration-batch-with-the-exchange-admin-center-eac). 

1. **Sélectionnez Choisir un fichier**, accédez au fichier CSV, choisissez-le, sélectionnez **Ouvrir**, puis **Suivant**. 
1. Vérifiez l’adresse e-mail de l’administrateur que vous souhaitez utiliser pour le test. 
1. **Sélectionnez Choisir un fichier**, accédez au fichier JSON que vous avez créé précédemment (généralement dans le dossier Téléchargements sur votre ordinateur), choisissez-le, sélectionnez **Ouvrir**, puis **Suivant**. 
1. Entrez un nom dans le **champ Nouveau nom du lot de migration**.
1. Entrez le sous-domaine que vous avez créé dans le champ **domaine de remise cible** , sélectionnez **Suivant**, puis **Nouveau**. 
1. Une fois les informations enregistrées, sélectionnez **OK**. 

    Vous pouvez maintenant afficher l’état de votre migration. 

1. Après un certain temps, selon le nombre d’utilisateurs que vous migrez, sélectionnez **Actualiser**. 
1. Une fois l’état **synchronisé**, sélectionnez **Terminer ce lot de migration**, puis **Oui**. 
1. Une fois le processus terminé, votre état passe à **Terminé**. 
1. Si vous le souhaitez, vous pouvez sélectionner **Afficher les détails** pour plus d’informations sur la migration. 
1. Sélectionnez **Fermer**. 
1. Ouvrez Outlook pour vérifier que tous les e-mails de Google Workspace ont été correctement migrés.
Vous pouvez le répéter également pour les éléments de calendrier et les contacts.
