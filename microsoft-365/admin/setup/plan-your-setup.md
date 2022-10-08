---
title: Planifier votre installation de Microsoft 365 pour les entreprises
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- highpri
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
- Adm_TOC
ms.custom:
- VSBFY23
- AdminSurgePortfolio
- okr_smb
- adminvideo
search.appverid:
- MET150
- MOE150
ms.assetid: eb926624-018b-4486-bf11-5fba6ee4d645
description: Découvrez les exigences et les considérations relatives à la migration vers Microsoft 365 pour les entreprises.
ms.openlocfilehash: 1115d16add6373f583144beb569f8ebb197696bc
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68206540"
---
# <a name="plan-your-setup-of-microsoft-365-for-business"></a>Planifier votre installation de Microsoft 365 pour les entreprises

Consultez [l’aide de Microsoft 365 petite entreprise](https://go.microsoft.com/fwlink/?linkid=2197659) sur YouTube.

Cet article est destiné aux personnes qui se sont abonnées à un plan Microsoft 365 pour les entreprises.
  
Avant de déplacer votre organisation vers Microsoft 365, vous devez respecter les exigences, les informations dont vous avez besoin et les décisions que vous devez prendre.

## <a name="overview-of-microsoft-365-for-business-setup"></a>Vue d’ensemble de la configuration de Microsoft 365 pour les entreprises

Regardez cette vidéo et d’autres encore sont disponibles sur notre [chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2197910).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Vjso?autoplay=false]

Félicitations pour votre décision de migrer votre entreprise vers le cloud avec Microsoft 365 ! Que vous ayez une personne dans votre entreprise ou 20, faire un peu de planification vous aidera à tirer le meilleur parti de Microsoft 365 pour les entreprises.

## <a name="info-to-have-on-hand-before-you-run-the-setup-wizard"></a>Informations à avoir sous la main avant d’exécuter l’Assistant Installation

Lorsque vous êtes prêt à exécuter l’Assistant Installation et à déplacer votre domaine vers Microsoft 365, voici les informations dont vous aurez besoin :
  
- Liste des personnes que vous souhaitez ajouter à Microsoft 365. Même si vous les avez déjà ajoutées à Microsoft 365, si vous mettez à jour vos informations de domaine, vous devez entrer leurs noms ici.

- Comment vous allez informer vos employés de leur ID d’utilisateur et de leur mot de passe afin qu’ils puissent se connecter. Comptez-vous les appeler pour leur fournir ces informations ? Comptez-vous envoyer celles-ci à leur adresse de courrier personnelle ? Ils n’auront pas accès à leur courrier électronique. Vous ne pouvez donc pas l’utiliser.

- Si vous disposez d’un nom de domaine pour votre organisation (par exemple, contoso.com) **et** que vous prévoyez d’utiliser la messagerie Microsoft, vous devez savoir où votre domaine est inscrit et disposer d’informations de connexion.

## <a name="what-happens-when-you-run-the-microsoft-365-setup-wizard"></a>Que se passe-t-il quand vous exécutez l’Assistant Installation de Microsoft 365 ?

L’Assistant Installation vous guide tout au long de l’installation des applications Microsoft 365 sur votre ordinateur, de l’ajout et de la vérification de votre domaine, de l’ajout d’utilisateurs et de l’attribution de licences, et de la connexion de votre domaine.

> [!NOTE]
> Si vous devez [attribuer des rôles d’administrateur dans Microsoft 365 pour les entreprises](../add-users/assign-admin-roles.md) aux utilisateurs que vous ajoutez dans l’Assistant, vous pouvez le faire plus tard sur la page **Utilisateurs** . 
  
Si vous ne terminez pas l’Assistant Installation, vous pouvez effectuer des tâches d’installation à tout moment à partir du **programme d’installation** du [centre](https://go.microsoft.com/fwlink/p/?linkid=2024339) >  d’administration. À partir de là, vous pouvez migrer des e-mails et des contacts à partir d’un autre service de messagerie, modifier le domaine de votre compte d’administrateur, gérer vos informations de facturation, ajouter ou supprimer des utilisateurs, réinitialiser les mots de passe et effectuer d’autres fonctions métier. Pour plus d’informations sur les différences entre l’Assistant Installation et la page **Installation** , consultez [Différences entre l’Assistant Installation de Microsoft 365 et la page Installation](o365-setup-wizard-and-setup-page.md).

Si vous êtes bloqué à un moment quelconque, contactez-nous. [Nous sommes là pour vous aider!](../../business-video/get-help-support.md).
  
## <a name="when-not-to-use-the-setup-wizard-active-directory-synchronization-and-hybrid-environments"></a>Cas où l'Assistant Configuration ne doit pas être utilisé : Synchronisation Active Directory et environnements hybrides

Il existe quelques scénarios qui incluent la migration de données ou d’utilisateurs à partir d’environnements locaux ou la configuration d’un système hybride qui inclut la synchronisation d’annuaires. Si vous êtes dans l’une des catégories, suivez les instructions fournies dans les articles suivants :
  
- Pour configurer la synchronisation d’annuaires avec votre Active Directory local, consultez Configurer la [synchronisation d’annuaires pour Microsoft 365](../../enterprise/set-up-directory-synchronization.md) et pour comprendre les différents modèles d’identité dans Microsoft 365, consultez [Déployer votre infrastructure d’identité pour Microsoft 365](../../enterprise/deploy-identity-solution-overview.md).

- Pour configurer un environnement hybride Exchange, vous trouverez ici l’ensemble complet des instructions qui vous guident dans toutes les différentes façons de configurer un échange hybride (y compris la configuration d’enregistrements DNS) : [Exchange Server Assistant Déploiement](/exchange/exchange-deployment-assistant)

- Pour configurer un déploiement SharePoint hybride, en particulier les fonctionnalités hybrides de recherche et de site, voir [Recherche hybride dans SharePoint](/SharePoint/hybrid/hybrid-search-in-sharepoint).

## <a name="move-to-microsoft-365-all-at-once-or-in-stages"></a>Passer à Microsoft 365 en même temps ou par étapes

- **Voulez-vous déplacer votre organisation vers Microsoft 365 en même temps ?** Si c’est le cas, envisagez de déplacer immédiatement votre domaine vers Microsoft 365. Commencez par exécuter l’Assistant Installation de Microsoft 365 ; il vous invite à configurer votre domaine.

- **Voulez-vous passer progressivement à Microsoft 365 ?** Si vous souhaitez passer à Microsoft 365 par étapes, ignorez l’exécution de l’Assistant Installation de Microsoft 365 et envisagez d’adopter les fonctionnalités de Microsoft 365 dans l’ordre suivant :

    1. [Ajoutez vos employés à Microsoft 365](../add-users/add-users.md) pour qu’ils puissent télécharger et installer les applications Office.

    2. [Téléchargez et installez les applications Office](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) afin d'utiliser Word, Excel et PowerPoint sur votre ordinateur et vos appareils.

    3. [Configurez Microsoft Teams](#plan-for-teams) à utiliser pour vos réunions.

    4. [Déplacez votre contenu vers le stockage cloud Microsoft 365](set-up-file-storage-and-sharing.md) (sites d’équipe OneDrive ou SharePoint).

    5. Lorsque vous êtes prêt, dans le [centre d’administration](https://go.microsoft.com/fwlink/p/?linkid=2024339), sélectionnez **Configurer** dans le volet de navigation gauche et utilisez la page **d’installation** pour [déplacer votre domaine et votre courrier électronique](add-domain.md).

## <a name="check-that-your-devices-meet-system-requirements"></a>Vérifiez que vos appareils présentent la configuration requise.

Chaque personne de votre organisation peut installer la suite d’applications Office 2016 (Word, Excel, PowerPoint, et ainsi de suite) sur jusqu’à cinq PC et Mac. Voir le système d'exploitation et la configuration système requise pour l'installation des [suites Office 2016](https://go.microsoft.com/fwlink/?LinkId=534827) pour les entreprises.
  
Les applications mobiles peuvent être installées sur des appareils iOS, Android et Windows. Pour plus d'informations sur la prise en charge des appareils mobiles et du navigateur, voir [Configuration requise pour Office](https://go.microsoft.com/fwlink/?LinkId=534827).
  
## <a name="plan-for-email"></a>Plan pour le courrier électronique

Si vous envisagez de passer d’un service de messagerie existant à Microsoft 365, le basculement prend généralement deux jours.
  
### <a name="plan-for-email-downtime"></a>Prévoyez un temps d'arrêt du courrier électronique
  
Si vous souhaitez utiliser Microsoft 365 pour votre courrier électronique :
  
- Pour déplacer votre adresse e-mail professionnelle (par exemple *, rob\@contoso.com*) d’un autre service de messagerie vers Microsoft 365, vous devez diriger votre courrier vers votre nouvelle boîte aux lettres Microsoft 365. Pour ce faire, **sélectionnez Migrer les données de vos utilisateurs** dans la page **d’installation** , où nous vous guidons pas à pas dans les mises à jour que vous devez effectuer sur votre hôte de domaine.

- Une fois votre hôte de domaine mis à jour, les modifications prennent généralement effet après une heure ou deux. Mais sachez que la mise à jour des modifications sur Internet peut parfois prendre jusqu’à 72 heures.

- Étant donné que vous risquez d’avoir un temps d’arrêt des e-mails, nous vous recommandons de passer à la messagerie Microsoft pendant une soirée ou un week-end lorsque vous recevez moins d’e-mails.

### <a name="plan-to-move-your-existing-email-contacts-and-calendar"></a>Planifier le déplacement de vos courriers, contacts et calendrier existants
  
Si vous envisagez d’utiliser Microsoft 365 pour votre compte de messagerie, vous pouvez apporter votre courrier, vos contacts et votre calendrier existants avec vous. La page **d’installation** vous aide à déplacer votre adresse e-mail et vos contacts existants dans la plupart des scénarios. Nous proposons également des guides détaillés pour le déplacement d'une ou plusieurs boîtes aux lettres.
  
|**Nombre de boîtes aux lettres ?**|**Recommandation**|
|:-----|:-----|
|Quelques-unes  <br/> |Si vous ne souhaitez pas utiliser la page **d’installation** pour migrer les boîtes aux lettres, vous pouvez autoriser les propriétaires de boîtes aux lettres à migrer leurs propres e-mails et contacts. Consultez [Migrer les e-mails et les contacts vers Microsoft 365 pour les entreprises](migrate-email-and-contacts-admin.md).  <br/> |
|Plusieurs  <br/> |Si vous effectuez une migration à partir de Gmail, consultez [Migrer des boîtes aux lettres G Suite vers Microsoft 365](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrate-g-suite-mailboxes).  <br/> Si vous effectuez une migration à partir d’un autre fournisseur de messagerie, y compris Exchange, consultez [Méthodes de migration de plusieurs comptes de messagerie vers Microsoft 365](/Exchange/mailbox-migration/mailbox-migration).  <br/> |

## <a name="plan-for-file-storage-and-migration"></a>Planifier le stockage et la migration de fichiers

Microsoft 365 fournit un stockage cloud pour les particuliers, les petites organisations et les entreprises. Pour obtenir des conseils sur ce qu’il faut stocker, voir [Où stocker des documents dans Microsoft 365](https://support.microsoft.com/office/d18d21a0-1f9f-4f6c-ac45-d52afa0a4a2e).
  
- **Vous pouvez déplacer des centaines de fichiers** vers [OneDrive](https://support.microsoft.com/office/45114744-6D42-45CD-8975-F9617819BDEB) ou un [site d’équipe SharePoint](https://support.microsoft.com/office/da549fb1-1fcb-4167-87d0-4693e93cb7a0#__toc384119242). Vous pouvez charger jusqu'à 100 fichiers à la fois. Évitez de charger des fichiers d'une taille supérieure à 2 Go, soit la taille de fichier maximale par défaut.
  
- **Si vous souhaitez déplacer plusieurs milliers de fichiers** vers le stockage Microsoft 365, passez en revue les [limites de SharePoint Online](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits). Nous vous recommandons de recourir à un outil de migration ou de faire appel à un [partenaire](https://go.microsoft.com/fwlink/?linkid=391089) pour vous aider à effectuer la migration. Pour plus d'informations sur la migration d'un grand nombre de fichiers, voir le [Guide de l'utilisateur pour la migration SharePoint Online et OneDrive](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).
  
## <a name="plan-for-teams"></a>Planifier Teams

Vous pouvez utiliser Microsoft Teams pour passer des appels à d’autres personnes de votre organisation qui se trouvent sur votre abonnement. Par exemple, si votre organisation compte 10 personnes, vous pouvez vous appeler et envoyer des messages instantanés à l’aide de Teams sans aucune configuration spéciale. Pour plus d’informations, consultez [Prise en main de Microsoft Teams](/MicrosoftTeams/get-started-with-teams-quick-start).

Pour les grandes organisations ou si vous commencez à partir de Skype Entreprise, de déploiements locaux ou hybrides, consultez [Comment déployer Microsoft Teams](/MicrosoftTeams/how-to-roll-out-teams).
  
## <a name="plan-for-integration-with-active-directory-or-other-software"></a>Planifier l'intégration avec Active Directory ou d'autres logiciels

- **Vous voulez opérer une intégration avec votre Active Directory en local ?** Vous pouvez intégrer votre Active Directory local à Microsoft 365 à l’aide d’Azure Active Directory Connect. Pour obtenir des instructions, consultez [Configurer la synchronisation d’annuaires pour Microsoft 365](../../enterprise/set-up-directory-synchronization.md).
  
- **Voulez-vous intégrer Microsoft 365 à des logiciels créés par d’autres entreprises ?** Si vous devez intégrer Microsoft 365 à d’autres logiciels de votre organisation, nous vous recommandons [d’engager un partenaire](https://go.microsoft.com/fwlink/?linkid=391089) pour vous aider dans votre déploiement.
  
## <a name="do-you-want-someone-to-help-you-set-up-microsoft-365"></a>Voulez-vous que quelqu’un vous aide à configurer Microsoft 365 ?

- **Si vous avez moins de 50 employés :**

  - **Demandez de l'aide et nous vous contacterons par téléphone**. Après avoir acheté Microsoft 365, vous pouvez accéder au centre d’administration (vous n’avez pas besoin d’exécuter le programme d’installation pour y accéder). En bas du centre d’administration, sélectionnez **Besoin d’aide ?** Décrivez-nous votre problème et nous vous contacterons par téléphone. 
  - **Appelez [le support Technique Microsoft 365 pour Entreprises](../../business-video/get-help-support.md) avec vos questions**. We're here to help! 
  - **Songez à faire appel à un [partenaire Microsoft](https://go.microsoft.com/fwlink/?linkid=391089)**. Si vous manquez de temps ou si vous avez des exigences avancées (comme le déplacement de milliers de fichiers vers le stockage cloud Microsoft 365 ou l’intégration à d’autres logiciels), un partenaire expérimenté peut être une grande aide. 

- **Si vous avez plus de 50 employés**, le [Centre d'intégration FastTrack](https://go.microsoft.com/fwlink/?LinkId=517115) est disponible pour vous aider à effectuer votre déploiement.

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../security-and-compliance/secure-your-business-data.md)
