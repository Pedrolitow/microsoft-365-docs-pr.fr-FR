---
title: Installer Microsoft 365 Entreprise à l'aide de l'Assistant Installation
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_M365SetupBanner
- BCS365_M365SetupBanner
ms.service: o365-administration
localization_priority: Normal
ms.collection: Adm_O365
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: 6e7a2dfd-8ec4-4eb7-8390-3ee103e5fece
description: Découvrez comment configurer Microsoft 365 Business en quatre étapes.
ms.openlocfilehash: f57239b884bd2e186c0bc01973130a10fa4cfe84
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26866845"
---
# <a name="set-up-microsoft-365-business-by-using-the-setup-wizard"></a>Installer Microsoft 365 Entreprise à l'aide de l'Assistant Installation

Effectuez les étapes 1 à 4 ci-dessous.
  
### <a name="set-up-microsoft-365-business"></a>Configurer Microsoft 365 Business

Regardez une vidéo sur la façon de configurer Microsoft 365 Business lorsque vous n’avez pas Active Directory local :
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/0705c337-f3e8-4d28-bb6c-530cd28e99f2?autoplay=false]
  
Les étapes de configuration contiennent des informations pour les installations comprenant Active Directory local. Si vous souhaitez continuer à accéder à des périphériques à un domaine, lisez les articles suivants pour deux différemment de l’activation qui et effectuer les étapes avant d’exécuter l’Assistant installation :
  
- [Permettre à un domaine aux périphériques Windows 10 devant être gérés par Microsoft 365 entreprise](manage-windows-devices.md)
    
    -Il s’agit de la méthode recommandée.
    
- [Accès aux ressources à partir d’un périphérique joint à AD Azure dans Microsoft 365 Business sur site](access-resources.md)
    
### <a name="step-1-personalize-sign-in"></a>Étape 1 : Personnaliser connexion

1. Connectez-vous à [Microsoft 365 Business](https://portal.microsoft.com) avec vos informations d'identification d'administrateur général. Sélectionnez la vignette **Administrateur** pour accéder au Centre d'administration. 
    
2. Sélectionnez **Commencer la configuration** (selon votre situation, il est possible que ce soit **Poursuivre la configuration** qui soit affiché) dans le Centre d'administration pour démarrer l'Assistant. 
    
3. Entrez le nom de domaine que vous voulez utiliser (par exemple, contoso.com).
    
    Continuez et entrez votre domaine, même si vous l’avez vérifié à l’aide d’Azure AD Connect, par exemple. Les deux étapes suivantes ne s’appliquent pas à vous si vous avez utilisé Azure AD se connecter pour vérifier votre domaine.
    
4. Suivez les étapes de l’Assistant pour [créer des enregistrements DNS à n’importe quel fournisseur d’hébergement DNS pour Office 365](https://support.office.com/article/7b7b075d-79f9-4e37-8a9e-fb60c1d95166) vérifie que vous êtes propriétaire du domaine. 
    
    Vous pouvez afficher une vidéo de l’exemple de [vidéo : le programme d’installation Office 365 dans le nouveau centre d’administration](https://support.office.com/article/a8c2002a-34bc-4ab3-93d8-9b5156c48bf8). Notez que cette vidéo n’inclut pas les étapes de protection de données de Microsoft 365 Business.
    
    ![Screenshot of the Business Cloud Suite setup wizard.](media/3c4fd40c-2de1-4a87-8ee0-78d3928c7bb7.png)
  
### <a name="step-2-add-users-and-assign-licenses"></a>Étape 2 : Ajouter des utilisateurs et attribution de licences

1. Vous pouvez ajouter des utilisateurs à ce stade ou [ajouter des utilisateurs plus tard](add-users-m365b.md) dans le centre d'administration. 
    
    Une licence Microsoft 365 Entreprise est automatiquement attribuée aux utilisateurs que vous ajoutez.
    
2. Si votre abonnement Microsoft 365 Entreprise est associé à des utilisateurs existants (par exemple, si vous utilisiez Azure AD Connect), vous avez la possibilité de leur attribuer des licences à ce stade. Poursuivez et ajoutez des licences pour eux aussi.
    
3. Vous avez également la possibilité de partager des informations d'identification avec les nouveaux utilisateurs que vous ajoutez. Vous pouvez choisir de les imprimer, de les envoyer par e-mail ou de les télécharger.
    
4. Ignorez la migration des messages e-mail et sélectionnez **Suivant** dans la page **Migrer les messages e-mail**. 
    
    Si vous déplacez à partir d’un autre fournisseur de messagerie électronique et que vous souhaitez copier vos données ultérieurement, vous pouvez [migrer e-mail et les contacts vers Office 365](https://support.office.com/article/a3e3bddb-582e-4133-8670-e61b9f58627e).
    
    ![Screenshot of two new users added in the setup wizard](media/8f729967-5c65-4ceb-b737-18119db40564.png)
  
### <a name="step-3-connect-your-domain"></a>Étape 3 : Connectez-vous à votre domaine

> [!NOTE]
> Si vous avez choisi d’utiliser le domaine .onmicrosoft ou utilisé Azure AD se connecter, vous ne verrez pas cette étape. 
  
Pour configurer des services, vous devez mettre à jour des enregistrements au niveau de votre hôte DNS ou de votre bureau d'enregistrement de domaines.
  
1. Généralement, l’Assistant installation détecte votre serveur d’inscriptions et vous donne un lien vers des instructions pas à pas pour mettre à jour vos enregistrements NS sur le site Web du serveur d’inscriptions. Le cas contraire, [modifier des serveurs de noms pour configurer Office 365 avec les domaines](https://support.office.com/article/a8b487a9-2a45-4581-9dc4-5d28a47010a2).
    
2. La messagerie électronique et d'autres services sont configurés pour vous.
    
### <a name="step-4-manage-devices-and-work-files"></a>Étape 4 : Gestion des périphériques et des fichiers de travail

1. **Protéger les fichiers de travail sur des appareils mobiles** page attribuer **sur** **protéger les fichiers de travail lorsque les périphériques sont perdus ou volés** et paramètres **gérer comment les utilisateurs d’accès aux fichiers Office sur des appareils mobiles** . Vous pouvez également accéder à chaque paramètre sous-fonctionnalités en cliquant sur les chevrons en regard de chaque paramètre.
  
  Tous les fichiers de travail de vos utilisateurs sous licence sont maintenant protégées sur les périphériques iOS ou Android, dès qu’ils [installer des applications Office](set-up-mobile-devices.md) (et s’authentifier auprès de leurs informations d’identification Microsoft 365 Business). 
  
  ![Screenshot of protect work files on your mobile devices page](media/3139a9aa-6228-4e74-8166-c6a886d7319f.PNG)
  
2. Dans la page **configuration du périphérique définir Windows 10** , affectez au paramètre **Sécuriser Windows 10 périphériques** **activé**.
  
   Vous pouvez également accéder à chaque paramètre sous-fonctionnalités en cliquant sur le chevron située en regard.
  
3. Définir le paramètre **Installer Office sur les périphériques Windows 10** **Oui** si tous les utilisateurs ont des ordinateurs Windows 10, et n’installe soit aucun Office existante, ou installe Office de click-to-run. Si ce n’est pas le cas, définissez cette option sur **No**. Vous pouvez [installer automatiquement Office](auto-install-or-uninstall-office.md) à partir du centre d’administration une fois que vous avez préparé les ordinateurs des utilisateurs. Pour plus d’informations, voir [Préparation de l’installation du client Office](prepare-for-office-client-deployment.md).
  
    Fichiers de travail des utilisateurs sous licence sur les appareils Windows 10 seront projetées dès qu’ils [participer à leur appareil Windows 10](set-up-windows-devices.md) à un domaine d’entreprise Microsoft 365 Azure AD ou [installer Windows 10 sur un nouvel ordinateur](https://support.office.com/article/c654bd23-d256-4ac7-8fba-0c993bf5a771.aspx) tout en joignant simultanément le 365 Microsoft Domaine d’entreprise Azure AD. 
  
4. Cliquez sur **Suivant** pour terminer la configuration. 
  
    Merci de nous faire part de vos commentaires à cette étape pour nous aider à améliorer l'expérience.
  
    ![Screenshot of Prepare Windows 10 devices page](media/bff701c1-48a3-44f4-aa95-9d959d57c85b.PNG)
  
## <a name="additional-security-settings"></a>Paramètres de sécurité supplémentaires

En plus de la sécurité et la définition de la conformité dans l’Assistant installation, vous pouvez également configurer les paramètres supplémentaires suivants :
  
- Configurer la protection contre les pièces jointes non sécurisés. **Protection contre les menaces de avancée** (DAV) identifie un contenu malveillant et bloque la remise des pièces jointes non sécurisés, vous protéger contre les schémas de phishing et infection de logiciels. Pour activer la protection de la pièce jointe, voir [définir des stratégies Office 365 DAV approuvés en pièce jointe](https://support.office.com/article/078eb946-819a-4e13-8673-fe0c0ad3a775#setpolicy).
    
- Lorsque les utilisateurs cliquent sur les liens malveillants de protéger votre environnement. DAV examine les liens dans le message électronique à la fois qu'un utilisateur clique dessus. Si un lien est non sécurisé, l’utilisateur est averti ne pas sur le site ou informé que le site a été bloqué. Cela permet de protéger contre le phishing. [Définir des stratégies Office 365 DAV fiables liens](https://support.office.com/article/bdd5372d-775e-4442-9c1b-609627b94b5d#reveddefaultscc) ou [définir des stratégies Office 365 DAV fiables liens](https://support.office.com/article/bdd5372d-775e-4442-9c1b-609627b94b5d#addemailpolscc).
    
- Vous pouvez conserver tous les contenus de boîte aux lettres, y compris les éléments supprimés en plaçant les boîtes aux lettres entière d’un utilisateur pour litige **hold**. Pour plus d’informations, voir 
- [Configurer la conservation des e-mails avec l’archivage Exchange Online](security-features.md#set-up-email-retention-with-exchange-online-archiving).
    
- Configurer des **stratégies de rétention**personnalisées, par exemple, à conserver pour une durée spécifique ou supprimer définitivement du contenu à la fin de la période de rétention. Vous pouvez activer les stratégies de rétention personnalisée dans le centre de conformité, accédez à **la gouvernance des données** et les titres \> **rétention**, puis suivez les étapes décrites dans l’Assistant. Pour plus d’informations, voir [vue d’ensemble des stratégies de rétention](https://support.office.com/article/5e377752-700d-4870-9b6d-12bfc12d2423).
    
## <a name="next-steps"></a>Étapes suivantes

Pour les utilisateurs qui disposent d'une licence, l'étape suivante consiste à configurer des appareils.<br/> Pour plus d'informations, voir [Configurer des appareils Windows pour les utilisateurs de Microsoft 365 Business](set-up-windows-devices.md) et [Configurer des appareils mobiles pour les utilisateurs de Microsoft 365 Business](set-up-mobile-devices.md). <br/>Pour obtenir des liens vers des rubriques relatives à la définition de stratégies de protection des applications et des appareils, et à la suppression de données sur les appareils des utilisateurs, consultez l'article [Gérer Microsoft 365 Business](manage.md). 
  


