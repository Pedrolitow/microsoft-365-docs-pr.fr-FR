---
title: Planifier votre configuration de Microsoft 365 entreprise
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- okr_smb
search.appverid:
- MET150
- MOE150
ms.assetid: eb926624-018b-4486-bf11-5fba6ee4d645
description: Découvrez les exigences et les considérations à prendre en compte pour effectuer le déplacement vers Microsoft 365 entreprise.
ms.openlocfilehash: b4d2b5d500b73b62c67d3f8126b6313484e2bc78
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59178484"
---
# <a name="plan-your-setup-of-microsoft-365-for-business"></a>Planifier votre configuration de Microsoft 365 entreprise

Cet article est réservé aux personnes qui se sont abonnées à une Microsoft 365 pour les entreprises.
  
Avant de déplacer votre organisation vers Microsoft 365, il existe des exigences que vous devez respecter, des informations dont vous avez besoin et des décisions que vous devez prendre.


  
## <a name="info-to-have-on-hand-before-you-run-the-setup-wizard"></a>Informations à prendre en main avant d’exécuter l’Assistant Installation

Lorsque vous êtes prêt à exécuter l’Assistant Installation et à déplacer votre domaine vers Microsoft 365, voici les informations dont vous aurez besoin :
  
- Liste des personnes que vous souhaitez ajouter à Microsoft 365. Même si vous les avez déjà ajoutés à Microsoft 365, si vous actualisez vos informations de domaine, vous devez entrer leurs noms ici.

- Comment vous allez informer vos employés de leur ID d’utilisateur et mot de passe afin qu’ils se connectent. Comptez-vous les appeler pour leur fournir ces informations ? Comptez-vous envoyer celles-ci à leur adresse de courrier personnelle ? Ils n’ont pas accès à leur messagerie, vous ne pouvez donc pas l’utiliser.

- Si vous avez un nom de domaine pour votre organisation (par exemple, **contoso.com)** et que vous envisagez d’utiliser la messagerie Électronique Microsoft, vous devez savoir où votre domaine est enregistré et avoir des informations de connectez-vous.

## <a name="what-happens-when-you-run-the-microsoft-365-setup-wizard"></a>Que se passe-t-il lorsque vous exécutez l’Assistant Microsoft 365 configuration

L’Assistant Installation vous permet d’installer les applications Microsoft 365 sur votre ordinateur, d’ajouter et de vérifier votre domaine, d’ajouter des utilisateurs et de leur attribuer des licences et de connecter votre domaine.

> [!NOTE]
> Si vous devez attribuer des rôles d’administrateur [dans Microsoft 365](../add-users/assign-admin-roles.md) entreprise aux utilisateurs que vous ajoutez dans l’Assistant, vous pouvez le faire ultérieurement sur la page **Utilisateurs.** 
  
Si vous n’avez pas terminé l’Assistant Installation, vous pouvez effectuer les tâches d’installation à tout moment à partir du programme d’installation [du Centre d’administration.](https://go.microsoft.com/fwlink/p/?linkid=2024339)  >   À partir de là, vous pouvez migrer le courrier électronique et les contacts à partir d’un autre service de messagerie, modifier le domaine de votre compte d’administrateur, gérer vos informations de facturation, ajouter ou supprimer des utilisateurs, réinitialiser des mots de passe et faire d’autres fonctions professionnelles. Pour plus d’informations sur les différences entre l’Assistant Installation et la **page** d’installation, voir Différences entre l’Assistant Microsoft 365 configuration et la [page d’installation.](o365-setup-wizard-and-setup-page.md)

Si vous êtes bloqué à un moment quelconque, contactez-nous. [Nous sommes là pour vous aider.](../../business-video/get-help-support.md)
  
## <a name="when-not-to-use-the-setup-wizard-active-directory-synchronization-and-hybrid-environments"></a>Cas où l'Assistant Configuration ne doit pas être utilisé : Synchronisation Active Directory et environnements hybrides

Il existe quelques scénarios qui incluent la migration de données ou d’utilisateurs à partir d’environnements locaux ou la configuration d’un système hybride qui inclut la synchronisation d’annuaires. Si vous êtes dans l’une ou l’autre catégorie, suivez les instructions des articles suivants :
  
- Pour configurer la synchronisation d’annuaires avec votre annuaire Active Directory local, consultez Configurer la synchronisation d’annuaires pour [Microsoft 365](../../enterprise/set-up-directory-synchronization.md)et pour comprendre les différents modèles d’identité dans Microsoft 365, lisez Comprendre l’identité Microsoft 365 et les [Azure Active Directory](../../enterprise/about-microsoft-365-identity.md).

- Pour configurer un déploiement Exchange hybride, les instructions relatives aux différentes étapes (dont la configuration des enregistrements DNS) sont disponibles ici : [Assistant de déploiement Exchange Server](/exchange/exchange-deployment-assistant)

- Pour configurer un déploiement SharePoint hybride, en particulier les fonctionnalités hybrides de recherche et de site, voir [Recherche hybride dans SharePoint](/SharePoint/hybrid/hybrid-search-in-sharepoint).

## <a name="move-to-microsoft-365-all-at-once-or-in-stages"></a>Passer à Microsoft 365 en une seule fois ou par étapes

- **Voulez-vous déplacer votre organisation vers Microsoft 365 en même temps ?** Si c’est le cas, prévoyez de déplacer votre domaine vers Microsoft 365 immédiatement. Commencez par l’exécution de l Microsoft 365 de configuration de l’ordinateur . Il vous invite à configurer votre domaine.

- **Voulez-vous passer à Microsoft 365 progressivement ?** Si vous souhaitez passer à Microsoft 365 par étapes, ignorez l’exécution de l’Assistant Installation de Microsoft 365 et envisagez d’adopter Microsoft 365 fonctionnalités dans l’ordre suivant :

    1. [Ajoutez vos employés à Microsoft 365](../add-users/add-users.md) pour qu’ils téléchargent et installent les Office applications.

    2. [Téléchargez et installez les applications Office](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) afin d'utiliser Word, Excel et PowerPoint sur votre ordinateur et vos appareils.

    3. [Configurer les Microsoft Teams](#plan-for-teams) à utiliser pour vos réunions.

    4. [Déplacez votre contenu vers Microsoft 365 stockage cloud](set-up-file-storage-and-sharing.md) (OneDrive ou SharePoint sites d’équipe).

    5. Lorsque vous êtes prêt, dans le  centre d’administration, [](https://go.microsoft.com/fwlink/p/?linkid=2024339)sélectionnez Le programme d’installation dans le volet de navigation de gauche et utilisez la **page** d’installation pour déplacer votre domaine et votre courrier [électronique.](add-domain.md)

## <a name="check-that-your-devices-meet-system-requirements"></a>Vérifiez que vos appareils présentent la configuration requise.

Chaque personne de votre organisation peut installer la suite d’applications Office 2016 (Word, Excel, PowerPoint, etc.) sur cinq PC et Mac. Voir le système d'exploitation et la configuration système requise pour l'installation des [suites Office 2016](https://go.microsoft.com/fwlink/?LinkId=534827) pour les entreprises.
  
Les applications mobiles peuvent être installées sur iOS, Android et Windows appareils mobiles. Pour plus d'informations sur la prise en charge des appareils mobiles et du navigateur, voir [Configuration requise pour Office](https://go.microsoft.com/fwlink/?LinkId=534827).
  
## <a name="plan-for-email"></a>Plan pour le courrier électronique

Si vous envisagez de passer d’un service de messagerie existant à Microsoft 365, le basculement prend généralement deux jours.
  
### <a name="plan-for-email-downtime"></a>Prévoyez un temps d'arrêt du courrier électronique
  
Si vous comptez utiliser Microsoft 365 pour votre courrier électronique :
  
- Pour déplacer votre adresse de messagerie professionnelle (par exemple, *rob \@ contoso.com*) d’un autre service de messagerie vers Microsoft 365, vous devez diriger votre courrier vers votre nouvelle boîte aux lettres Microsoft 365. Pour ce faire,  sélectionnez Migrer les données de vos utilisateurs sur la **page** d’installation, où nous vous guidons pas à pas dans les mises à jour que vous devez effectuer au niveau de votre hôte de domaine.

- Une fois votre hôte de domaine mis à jour, les modifications prennent généralement effet après une heure ou deux. Toutefois, sachez que la mise à jour sur Internet des modifications peut prendre jusqu’à 72 heures.

- Étant donné que vous pouvez avoir un temps d’arrêt du courrier électronique, nous vous recommandons de passer à la messagerie Microsoft le soir ou le week-end lorsque vous recevez moins d’e-mails.

### <a name="plan-to-move-your-existing-email-contacts-and-calendar"></a>Planifier le déplacement de vos courriers, contacts et calendrier existants
  
Si vous comptez utiliser Microsoft 365 pour votre compte de messagerie, vous pouvez apporter votre courrier électronique, vos contacts et votre calendrier existants avec vous. La page **Installation** vous aide à déplacer vos messages électroniques et contacts existants pour la plupart des scénarios. Nous proposons également des guides détaillés pour le déplacement d'une ou plusieurs boîtes aux lettres.
  
|**Nombre de boîtes aux lettres ?**|**Recommandation**|
|:-----|:-----|
|Quelques-unes  <br/> |Si vous ne souhaitez pas utiliser la **page** d’installation pour migrer les boîtes aux lettres, vous pouvez laisser les propriétaires de boîtes aux lettres migrer leurs propres e-mails et contacts. Voir [Migrer le courrier électronique et les contacts vers Microsoft 365 entreprise.](migrate-email-and-contacts-admin.md)  <br/> |
|Plusieurs  <br/> |Si vous migrez à partir de Gmail, voir [Migrer](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrate-g-suite-mailboxes)des boîtes aux lettres G Suite vers Microsoft 365 .  <br/> Si vous migrez à partir d’un autre fournisseur de messagerie, y compris Exchange, voir Méthodes de migration de plusieurs comptes de messagerie vers [Microsoft 365](/Exchange/mailbox-migration/mailbox-migration).  <br/> |

## <a name="plan-for-file-storage-and-migration"></a>Planifier le stockage et la migration de fichiers

Microsoft 365 offre un stockage cloud pour les individus, les petites organisations et les entreprises. Pour obtenir des instructions sur les l’endroit où stocker, voir Où stocker [des documents dans Microsoft 365](../../business-video/store-files.md).
  
- **Vous pouvez déplacer des centaines de fichiers vers** [OneDrive](https://support.microsoft.com/office/45114744-6D42-45CD-8975-F9617819BDEB) ou vers un [site d SharePoint’équipe.](https://support.microsoft.com/office/da549fb1-1fcb-4167-87d0-4693e93cb7a0#__toc384119242) Vous pouvez charger jusqu'à 100 fichiers à la fois. Évitez de charger des fichiers d'une taille supérieure à 2 Go, soit la taille de fichier maximale par défaut.
  
- **Si vous souhaitez déplacer plusieurs milliers** de fichiers vers Microsoft 365 stockage, examinez les [limites SharePoint en ligne.](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits) Nous vous recommandons de recourir à un outil de migration ou de faire appel à un [partenaire](https://go.microsoft.com/fwlink/?linkid=391089) pour vous aider à effectuer la migration. Pour plus d'informations sur la migration d'un grand nombre de fichiers, voir le [Guide de l'utilisateur pour la migration SharePoint Online et OneDrive](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).
  
## <a name="plan-for-teams"></a>Planifier les Teams

Vous pouvez utiliser Microsoft Teams pour appeler d’autres personnes de votre organisation qui font appel à votre abonnement. Par exemple, si votre organisation compte 10 personnes, vous pouvez vous appeler et vous instantanér à l’aide Teams sans configuration spéciale. Pour plus d’informations, [consultez La mise en Microsoft Teams](/MicrosoftTeams/get-started-with-teams-quick-start).

Pour les grandes organisations ou si vous débutez à partir de déploiements Skype Entreprise, locaux ou hybrides, voir comment déployer [Microsoft Teams](/MicrosoftTeams/how-to-roll-out-teams).
  
## <a name="plan-for-integration-with-active-directory-or-other-software"></a>Planifier l'intégration avec Active Directory ou d'autres logiciels

- **Vous voulez opérer une intégration avec votre Active Directory en local ?** Vous pouvez intégrer votre annuaire Active Directory local à Microsoft 365 à l’aide Azure Active Directory Connecter. Pour obtenir des instructions, voir Configurer la synchronisation [d’annuaires pour Microsoft 365](../../enterprise/set-up-directory-synchronization.md).
  
- **Souhaitez-vous intégrer des Microsoft 365 logiciels d’autres entreprises ?** Si vous devez intégrer des Microsoft 365 à d’autres logiciels de votre organisation, nous vous recommandons d’envisager d’engager un partenaire pour vous aider dans votre déploiement. [](https://go.microsoft.com/fwlink/?linkid=391089)
  
## <a name="do-you-want-someone-to-help-you-set-up-microsoft-365"></a>Voulez-vous que quelqu’un vous aide à configurer Microsoft 365 ?

- **Si vous avez moins de 50 employés :**

  - **Demandez de l'aide et nous vous contacterons par téléphone**. Après avoir acheté Microsoft 365, vous pouvez accéder au Centre d’administration (vous n’avez pas besoin d’exécuter le programme d’installation pour y accéder). En bas du Centre d’administration, sélectionnez **Besoin d’aide ?** Décrivez-nous votre problème et nous vous contacterons par téléphone. 
  - **Appelez [Microsoft 365 support technique pour les](../../business-video/get-help-support.md) entreprises avec vos questions.** We're here to help! 
  - **Songez à faire appel à un [partenaire Microsoft](https://go.microsoft.com/fwlink/?linkid=391089)**. Si vous manquez de temps ou si vous avez des exigences avancées (par exemple, le déplacement de milliers de fichiers vers un stockage cloud Microsoft 365 ou l’intégration à d’autres logiciels), un partenaire expérimenté peut vous être très utile. 

- **Si vous avez plus de 50 employés**, le [Centre d'intégration FastTrack](https://go.microsoft.com/fwlink/?LinkId=517115) est disponible pour vous aider à effectuer votre déploiement.