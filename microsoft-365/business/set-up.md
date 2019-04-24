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
ms.collection:
- Adm_O365
- M365-subscription-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: 6e7a2dfd-8ec4-4eb7-8390-3ee103e5fece
description: Découvrez comment configurer Microsoft 365 entreprise en suivant quatre étapes.
ms.openlocfilehash: a1c8a41c3e291983276280a063248bdd10a7f85a
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32283896"
---
# <a name="set-up-microsoft-365-business-by-using-the-setup-wizard"></a>Installer Microsoft 365 Entreprise à l'aide de l'Assistant Installation

Suivez les étapes décrites ci-dessous 1-4.
  
### <a name="set-up-microsoft-365-business"></a>Configurer Microsoft 365 Business

Regardez une vidéo sur la configuration de Microsoft 365 entreprise lorsque vous n'avez pas d'Active Directory local:
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/0705c337-f3e8-4d28-bb6c-530cd28e99f2?autoplay=false]
  
Les étapes de configuration incluent des informations pour les configurations qui incluent Active Directory local. Si vous souhaitez continuer à accéder aux appareils joints à un domaine, lisez les articles suivants pour obtenir deux méthodes différentes d'activation de ce dernier, puis effectuez les étapes suivantes avant d'exécuter l'Assistant Installation:
  
- [Activer la gestion des appareils Windows 10 associés à un domaine par Microsoft 365 Business](manage-windows-devices.md)
    
    -Il s'agit de la méthode recommandée.
    
- [Accéder aux ressources locales à partir d'un appareil joint à Azure AD dans Microsoft 365 Business](access-resources.md)
    
### <a name="step-1-personalize-sign-in"></a>Étape 1: personnalisation de la connexion

1. Connectez-vous à [Microsoft 365 Business](https://portal.microsoft.com) avec vos informations d'identification d'administrateur général. Sélectionnez la vignette **Administrateur** pour accéder au Centre d'administration. 
    
2. Sélectionnez **Commencer la configuration** (selon votre situation, il est possible que ce soit **Poursuivre la configuration** qui soit affiché) dans le Centre d'administration pour démarrer l'Assistant. 
    
3. Entrez le nom de domaine que vous voulez utiliser (par exemple, contoso.com).
    
    Entrez votre domaine même si vous l'avez déjà confirmé, par exemple lors de l'utilisation d'Azure AD Connect. Les deux étapes suivantes ne s'appliquent pas si vous avez utilisé Azure AD Connect pour vérifier votre domaine.
    
4. Suivez les étapes de l'Assistant pour [créer des enregistrements DNS auprès d'un fournisseur d'hébergement DNS pour Office 365](https://support.office.com/article/7b7b075d-79f9-4e37-8a9e-fb60c1d95166) qui vérifie que vous êtes propriétaire du domaine. 
    
    Vous pouvez voir un exemple de vidéo de [vidéo: Setup Office 365 dans le nouveau centre d'administration](https://support.office.com/article/a8c2002a-34bc-4ab3-93d8-9b5156c48bf8). Veuillez noter que cette vidéo n'inclut pas les étapes de protection des données de Microsoft 365 Entreprise.
    
    ![Screenshot of the Business Cloud Suite setup wizard.](media/3c4fd40c-2de1-4a87-8ee0-78d3928c7bb7.png)
  
### <a name="step-2-add-users-and-assign-licenses"></a>Étape 2: ajouter des utilisateurs et attribuer des licences

1. Vous pouvez ajouter des utilisateurs à ce stade ou [ajouter des utilisateurs plus tard](add-users-m365b.md) dans le centre d'administration. 
    
    Une licence Microsoft 365 Entreprise est automatiquement attribuée aux utilisateurs que vous ajoutez.
    
2. Si votre abonnement Microsoft 365 Entreprise est associé à des utilisateurs existants (par exemple, si vous utilisiez Azure AD Connect), vous avez la possibilité de leur attribuer des licences à ce stade. Poursuivez et ajoutez des licences pour eux aussi.
    
3. Vous avez également la possibilité de partager des informations d'identification avec les nouveaux utilisateurs que vous ajoutez. Vous pouvez choisir de les imprimer, de les envoyer par e-mail ou de les télécharger.
    
4. Ignorez la migration des messages e-mail et sélectionnez **Suivant** dans la page **Migrer les messages e-mail**. 
    
    Si vous effectuez une migration à partir d'un autre fournisseur de courrier et que vous souhaitez copier vos données ultérieurement, vous pouvez migrer le [courrier électronique et les contacts vers Office 365](https://support.office.com/article/a3e3bddb-582e-4133-8670-e61b9f58627e).
    
    ![Screenshot of two new users added in the setup wizard](media/8f729967-5c65-4ceb-b737-18119db40564.png)
  
### <a name="step-3-connect-your-domain"></a>Étape 3: Connectez votre domaine

> [!NOTE]
> Si vous avez choisi d'utiliser le domaine. onmicrosoft ou Azure AD Connect, vous ne verrez pas cette étape. 
  
Pour configurer des services, vous devez mettre à jour des enregistrements au niveau de votre hôte DNS ou de votre bureau d'enregistrement de domaines.
  
1. L'Assistant Configuration détecte généralement votre bureau d'enregistrement et vous fournit un lien vers des instructions détaillées vous permettant de mettre à jour vos enregistrements NS sur le site web du bureau d'enregistrement. Si ce n'est pas le cas, [Modifiez les serveurs de noms pour configurer Office 365 avec n'importe quel](https://support.office.com/article/a8b487a9-2a45-4581-9dc4-5d28a47010a2)Bureau d'enregistrement de domaine.
    
2. La messagerie électronique et d'autres services sont configurés pour vous.
    
### <a name="step-4-manage-devices-and-work-files"></a>Étape 4: gérer les appareils et les fichiers de travail

1. Dans la page **Protéger les fichiers professionnels sur vos appareils mobiles**, définissez les paramètres **Protéger les fichiers professionnels en cas de perte ou de vol des appareils** et **Gérer la manière dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles** sur **Activé**. Vous pouvez également accéder à chaque sous-paramètre en cliquant sur les chevrons en regard de chaque paramètre.
  
  Tous les fichiers de travail de vos utilisateurs sous licence sont maintenant protégés sur les appareils iOS et Android, dès qu'ils installent les [applications Office](set-up-mobile-devices.md) (et s'authentifient avec leurs informations d'identification Microsoft 365 entreprise). 
  
  ![Screenshot of protect work files on your mobile devices page](media/3139a9aa-6228-4e74-8166-c6a886d7319f.PNG)
  
2. Sur la page **définir la configuration des appareils Windows 10** , définissez le paramètre sécurisEr les **appareils Windows 10** sur **activé**.
  
   Vous pouvez également accéder à chaque sous-paramètre en cliquant sur le chevron en regard de celui-ci.
  
3. Définissez le paramètre **Installer Office sur les appareils Windows 10** sur **Oui** si tous vos utilisateurs ont des ordinateurs Windows 10 et aucune installation Office existante ou des installations Office « Démarrer en un clic ». Si ce n'est pas le cas, définissez cette option sur **Non**. Vous pouvez [automatiquement installer Office](auto-install-or-uninstall-office.md) plus tard à partir du centre d'administration, une fois que vous aurez préparé les ordinateurs des utilisateurs. Pour obtenir des instructions, consultez la rubrique [Prepare for Office client installation](prepare-for-office-client-deployment.md).
  
    Les fichiers de travail des utilisateurs sous licence sur les appareils Windows 10 seront projetés dès qu'ils rejoignent [leur appareil Windows 10](set-up-windows-devices.md) à un domaine Microsoft 365 Business Azure ad ou [installer Windows 10 sur un nouvel ordinateur](https://support.office.com/article/c654bd23-d256-4ac7-8fba-0c993bf5a771.aspx) tout en rejoignant simultanément Microsoft 365 Domaine Business Azure AD. 
  
4. Cliquez sur **Suivant** pour terminer la configuration. 
  
    Merci de nous faire part de vos commentaires à cette étape pour nous aider à améliorer l'expérience.
  
    ![Screenshot of Prepare Windows 10 devices page](media/bff701c1-48a3-44f4-aa95-9d959d57c85b.PNG)
  
## <a name="additional-security-settings"></a>Paramètres de sécurité supplémentaires

Outre le paramètre de sécurité et de conformité dans l'Assistant Installation, vous pouvez également configurer les paramètres supplémentaires suivants:
  
- ConFigurez la protection contre les pièces jointes potentiellement dangereuses. **Protection avancée contre les menaces** (ATP) identifie le contenu malveillant, puis bloque la remise de pièces jointes potentiellement dangereuses, ce qui vous permet de vous protéger contre les schémas de hameçonnage et les infections par ransomware. Pour activer la protection des pièces jointes, consultez la rubrique [set up Office 365 ATP Safe Attachments Policies](https://support.office.com/article/078eb946-819a-4e13-8673-fe0c0ad3a775#setpolicy).
    
- Protégez votre environnement lorsque les utilisateurs cliquent sur des liens malveillants. La fonctionnalité ATP examine les liens dans les courriers électroniques lorsqu'un utilisateur clique dessus. Si un lien n'est pas sécurisé, l'utilisateur est averti de ne pas visiter le site ou d'être informé que le site a été bloqué. Cela permet de vous protéger contre les schémas de phishing. [Configurez les stratégies de liens approuvés office 365 ATP](https://support.office.com/article/bdd5372d-775e-4442-9c1b-609627b94b5d#reveddefaultscc) ou configurez [les stratégies de liens fiables Office 365 ATP](https://support.office.com/article/bdd5372d-775e-4442-9c1b-609627b94b5d#addemailpolscc).
    
- Vous pouvez conserver tout le contenu des boîtes aux lettres, y compris les éléments supprimés, en mettant la boîte aux lettres entière d'un utilisateur en **conservation pour litige**. Pour obtenir des instructions, voir 
- ConFigurez la rétention du [courrier électronique avec archivAge Exchange Online](security-features.md#set-up-email-retention-with-exchange-online-archiving).
    
- ConFigurez des **stratégies**de rétention personnalisées, par exemple, pour les conserver pendant une période de temps spécifique ou supprimer définitivement le contenu à la fin de la période de rétention. Vous pouvez activer des stratégies de rétention personnalisées dans le centre de sécurité et de conformité, accédez à rétention de **gouvernance** \> **** des données, puis suivez les étapes de l'Assistant. Pour en savoir plus, consultez la rubrique [vue d'ensemble des stratégies de](https://support.office.com/article/5e377752-700d-4870-9b6d-12bfc12d2423)rétention.
    
## <a name="next-steps"></a>Étapes suivantes

Pour les utilisateurs qui disposent d'une licence, l'étape suivante consiste à configurer des appareils.<br/> Pour plus d'informations, voir [Configurer des appareils Windows pour les utilisateurs de Microsoft 365 Business](set-up-windows-devices.md) et [Configurer des appareils mobiles pour les utilisateurs de Microsoft 365 Business](set-up-mobile-devices.md). <br/>Pour obtenir des liens vers des rubriques relatives à la définition de stratégies de protection des applications et des appareils, et à la suppression de données sur les appareils des utilisateurs, consultez l'article [Gérer Microsoft 365 Business](manage.md). 
  


