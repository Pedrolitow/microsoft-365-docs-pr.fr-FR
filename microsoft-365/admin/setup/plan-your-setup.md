---
title: Planifier la configuration de Microsoft 365 pour les entreprises
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
ms.assetid: eb926624-018b-4486-bf11-5fba6ee4d645
description: Découvrez ce que vous devez faire pour configurer votre Microsoft 365 pour les entreprises.
ms.openlocfilehash: 7509e2c4801adbca492e5f5446c5b97eae31dccf
ms.sourcegitcommit: 659adf65d88ee44f643c471e6202396f1ffb6576
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44778948"
---
# <a name="plan-your-setup-of-microsoft-365-for-business"></a>Planifier la configuration de Microsoft 365 pour les entreprises

Cet article est destiné aux personnes qui ont souscrit à un plan Microsoft 365 pour les entreprises.
  
Il existe quelques éléments à prendre en compte et vous devez disposer des informations dont vous avez besoin, avant de transférer votre organisation à Microsoft 365.
  
## <a name="info-to-have-on-hand-before-you-run-the-setup-wizard"></a>Informations devant être disponibles avant l’exécution de l’Assistant Installation

Lorsque vous êtes prêt à exécuter l’Assistant Installation et à déplacer votre domaine vers Microsoft 365, Voici les informations dont vous devez disposer :
  
- Liste des personnes que vous souhaitez ajouter à Microsoft 365. Même si vous les avez déjà ajoutés à Microsoft 365, si vous mettez à jour les informations de votre domaine, vous devez entrer leur nom ici.

- Comment vous allez informer vos employés de leur ID utilisateur et de leur mot de passe afin qu’ils puissent se connecter. Comptez-vous les appeler pour leur fournir ces informations ? Comptez-vous envoyer celles-ci à leur adresse de courrier personnelle ? Ils n’auront pas accès à leur courrier électronique, c’est pourquoi vous ne pouvez pas l’utiliser.

- Si vous disposez d’un nom de domaine pour votre organisation (par exemple, contoso.com) **et** que vous envisagez d’utiliser la messagerie Microsoft, vous devez savoir où votre domaine est enregistré et disposer d’informations de connexion.

## <a name="what-happens-when-you-run-the-microsoft-365-setup-wizard"></a>Que se passe-t-il lorsque vous exécutez l’Assistant Installation de Microsoft 365

L’Assistant installation vous guide tout au long de l’installation des applications Microsoft 365 sur votre ordinateur, en ajoutant et en vérifiant votre domaine, en ajoutant des utilisateurs et en leur affectant des licences, et en connectant votre domaine.

> [!NOTE]
> Si vous devez [attribuer des rôles d’administrateur dans Microsoft 365 pour les entreprises](../add-users/assign-admin-roles.md) aux utilisateurs que vous ajoutez dans l’Assistant, vous pouvez le faire plus tard dans la page **utilisateurs** . 
  
Si vous n’exécutez pas l’Assistant Installation, vous pouvez effectuer les tâches de configuration à [admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339)tout moment à partir du  >  **programme d’installation**du centre d’administration. À partir de là, vous pouvez migrer le courrier électronique et les contacts à partir d’un autre service de messagerie, modifier le domaine de votre compte d’administrateur, gérer vos informations de facturation, ajouter ou supprimer des utilisateurs, réinitialiser des mots de passe et effectuer d’autres fonctions professionnelles. Pour plus d’informations sur les différences entre l’Assistant Installation et la page **installation** , consultez la rubrique [différences entre l’Assistant installation de Microsoft 365 et la page installation](o365-setup-wizard-and-setup-page.md).

Si vous êtes bloqué à un moment quelconque, contactez-nous. [Nous sommes là pour vous aider.](../contact-support-for-business-products.md)
  
## <a name="when-not-to-use-the-setup-wizard-active-directory-synchronization-and-hybrid-environments"></a>Cas où l'Assistant Configuration ne doit pas être utilisé : Synchronisation Active Directory et environnements hybrides

Il existe deux scénarios qui incluent la migration de données ou d’utilisateurs à partir d’environnements locaux ou la configuration d’un système hybride qui inclut la synchronisation d’annuaires. Si vous êtes dans l’une de ces catégories, suivez les instructions fournies dans les articles suivants :
  
- Pour configurer la synchronisation d’annuaires avec votre annuaire Active Directory local, voir [configurer la synchronisation d’annuaires pour microsoft 365](https://docs.microsoft.com/office365/enterprise/set-up-directory-synchronization)et comprendre les différents modèles d’identité dans Microsoft 365, lisez la rubrique [understanding Microsoft 365 Identity and Azure Active Directory](https://docs.microsoft.com/office365/enterprise/about-office-365-identity).

- Pour configurer un déploiement Exchange hybride, les instructions relatives aux différentes étapes (dont la configuration des enregistrements DNS) sont disponibles ici : [Assistant de déploiement Exchange Server](https://aka.ms/exdeploy)

- Pour configurer un déploiement SharePoint hybride, en particulier les fonctionnalités hybrides de recherche et de site, voir [Recherche hybride dans SharePoint](https://docs.microsoft.com/SharePoint/hybrid/hybrid-search-in-sharepoint).

## <a name="move-to-microsoft-365-all-at-once-or-in-stages"></a>Accéder à Microsoft 365 en une seule fois ou en plusieurs étapes

- **Voulez-vous déplacer votre organisation vers Microsoft 365 en une seule fois ?** Si c’est le cas, prévoyez de déplacer votre domaine immédiatement vers Microsoft 365. Commencez par exécuter l’Assistant Installation de Microsoft 365 ; il vous invite à configurer votre domaine.

- **Voulez-vous passer à Microsoft 365 graduellement ?** Si vous souhaitez passer à Microsoft 365 par étapes, ignorez l’Assistant Installation de Microsoft 365 et envisagez d’adopter les fonctionnalités Microsoft 365 dans l’ordre suivant :

    1. [Ajoutez vos employés à Microsoft 365](../add-users/add-users.md) afin qu’ils puissent télécharger et installer les applications Office.

    2. [Téléchargez et installez les applications Office](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) afin d'utiliser Word, Excel et PowerPoint sur votre ordinateur et vos appareils.

    3. [Configurez Microsoft teams](#plan-for-teams) à utiliser pour vos réunions.

    4. [Déplacez votre contenu sur le stockage Cloud Microsoft 365](set-up-file-storage-and-sharing.md) (OneDrive ou sites d’équipe SharePoint).

    5. Lorsque vous êtes prêt, dans le [Centre d’administration](https://go.microsoft.com/fwlink/p/?linkid=2024339), sélectionnez **configuration** dans le volet de navigation de gauche et utilisez la page de **configuration** pour [déplacer votre domaine et votre messagerie](add-domain.md).

## <a name="check-that-your-devices-meet-system-requirements"></a>Vérifiez que vos appareils présentent la configuration requise.

Chaque membre de votre organisation peut installer la suite d’applications Office 2016 (Word, Excel, PowerPoint, etc.) sur cinq PC et Mac. Voir le système d'exploitation et la configuration système requise pour l'installation des [suites Office 2016](https://go.microsoft.com/fwlink/?LinkId=534827) pour les entreprises.
  
Les applications mobiles peuvent être installées sur des appareils iOS, Android et Windows. Pour plus d'informations sur la prise en charge des appareils mobiles et du navigateur, voir [Configuration requise pour Office](https://go.microsoft.com/fwlink/?LinkId=534827).
  
## <a name="plan-for-email"></a>Plan pour le courrier électronique

Si vous envisagez de passer d’un service de messagerie existant à Microsoft 365, il faut généralement deux jours pour effectuer le changement.
  
### <a name="plan-for-email-downtime"></a>Prévoyez un temps d'arrêt du courrier électronique
  
Si vous envisagez d’utiliser Microsoft 365 pour votre courrier électronique :
  
- Pour déplacer votre adresse de messagerie professionnelle (par exemple, *rob \@ contoso.com*) à partir d’un autre service de messagerie vers Microsoft 365, vous devez diriger votre courrier vers votre nouvelle boîte aux lettres Microsoft 365. Pour ce faire, sélectionnez **migrer les données de vos utilisateurs** sur la page de **configuration** , dans laquelle nous vous guiderons tout au long des mises à jour que vous devez effectuer au niveau de votre hôte de domaine, étape par étape.

- Une fois votre hôte de domaine mis à jour, les modifications prennent généralement effet après une heure ou deux. Cependant, sachez que la mise à jour des modifications sur Internet peut parfois prendre jusqu’à 72 heures.

- Étant donné que vous pouvez avoir un temps d’arrêt du courrier électronique, nous vous recommandons de passer à la messagerie Microsoft pendant un soir ou un week-end lorsque vous recevez moins d’e-mails.

### <a name="plan-to-move-your-existing-email-contacts-and-calendar"></a>Planifier le déplacement de vos courriers, contacts et calendrier existants
  
Si vous envisagez d’utiliser Microsoft 365 pour votre compte de courrier, vous pouvez y insérer vos courriers, contacts et calendrier existants. La page de **configuration** vous permet de déplacer vos courriers et contacts existants dans la plupart des scénarios. Nous proposons également des guides détaillés pour le déplacement d'une ou plusieurs boîtes aux lettres.
  
|**Nombre de boîtes aux lettres ?**|**Recommandation**|
|:-----|:-----|
|Quelques-unes  <br/> |Si vous ne souhaitez pas utiliser la page de **configuration** pour migrer les boîtes aux lettres, vous pouvez permettre aux propriétaires de boîtes aux lettres de migrer leurs propres courriers et contacts. Voir [migrer le courrier électronique et les contacts vers Microsoft 365 pour les entreprises](migrate-email-and-contacts-admin.md).  <br/> |
|Plusieurs  <br/> |Si vous effectuez une migration à partir de Gmail, voir [migrer les boîtes aux lettres G suite vers Microsoft 365](https://docs.microsoft.com/Exchange/mailbox-migration/migrating-imap-mailboxes/migrate-g-suite-mailboxes).  <br/> Si vous effectuez une migration à partir d’un autre fournisseur de messagerie, y compris Exchange, consultez la rubrique [méthodes de migration de plusieurs comptes de messagerie vers Microsoft 365](https://docs.microsoft.com/Exchange/mailbox-migration/mailbox-migration).  <br/> |

## <a name="plan-for-file-storage-and-migration"></a>Planifier le stockage et la migration de fichiers

Microsoft 365 fournit un stockage cloud pour les particuliers, les petites organisations et les entreprises. Pour plus d’informations sur les éléments à stocker [dans, voir où stocker des documents dans Microsoft 365](https://support.microsoft.com/office/c7c20284-bc94-47f4-9728-d28e9daf0790).
  
- **Vous pouvez déplacer des centaines de fichiers** vers [OneDrive](https://support.microsoft.com/office/45114744-6D42-45CD-8975-F9617819BDEB) ou vers un [site d’équipe SharePoint](https://support.microsoft.com/office/da549fb1-1fcb-4167-87d0-4693e93cb7a0#__toc384119242). Vous pouvez charger jusqu'à 100 fichiers à la fois. Évitez de charger des fichiers d'une taille supérieure à 2 Go, soit la taille de fichier maximale par défaut.
  
- **Si vous souhaitez déplacer plusieurs milliers de fichiers** vers le stockage Microsoft 365, consultez les [limites de SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkID=856113). Nous vous recommandons de recourir à un outil de migration ou de faire appel à un [partenaire](https://go.microsoft.com/fwlink/?linkid=391089) pour vous aider à effectuer la migration. Pour plus d'informations sur la migration d'un grand nombre de fichiers, voir le [Guide de l'utilisateur pour la migration SharePoint Online et OneDrive](https://go.microsoft.com/fwlink/?LinkId=723574).
  
## <a name="plan-for-teams"></a>Planifier teams

Vous pouvez utiliser Microsoft teams pour passer des appels à d’autres personnes de votre organisation qui sont sur votre abonnement. Par exemple, si votre organisation compte 10 personnes, vous pouvez appeler et communiquer par messagerie instantanée les uns aux autres à l’aide de teams sans configuration spéciale. Pour plus d’informations, consultez la rubrique [prise en main de Microsoft teams](https://docs.microsoft.com/MicrosoftTeams/get-started-with-teams-quick-start).

Pour les grandes organisations ou si vous commencez à partir de Skype entreprise, déploiements locaux ou hybrides, consultez [la rubrique How to disout Microsoft teams](https://docs.microsoft.com/MicrosoftTeams/how-to-roll-out-teams).
  
## <a name="plan-for-integration-with-active-directory-or-other-software"></a>Planifier l'intégration avec Active Directory ou d'autres logiciels

- **Vous voulez opérer une intégration avec votre Active Directory en local ?** Vous pouvez intégrer votre annuaire Active Directory local à Microsoft 365 à l’aide d’Azure Active Directory Connect. Pour obtenir des instructions, consultez la rubrique [configurer la synchronisation d’annuaires pour Microsoft 365](https://docs.microsoft.com/office365/enterprise/set-up-directory-synchronization).
  
- **Souhaitez-vous intégrer Microsoft 365 avec des logiciels créés par d’autres entreprises ?** Si vous avez besoin d’intégrer Microsoft 365 à d’autres logiciels de votre organisation, nous vous recommandons d’envisager d' [embaucher un partenaire](https://go.microsoft.com/fwlink/?linkid=391089) pour vous aider dans votre déploiement.
  
## <a name="do-you-want-someone-to-help-you-set-up-microsoft-365"></a>Voulez-vous que quelqu’un vous aide à configurer Microsoft 365 ?

- **Si vous avez moins de 50 employés :**

  - **Demandez de l'aide et nous vous contacterons par téléphone**. Une fois que vous avez acheté Microsoft 365, vous pouvez accéder au centre d’administration (vous n’avez pas besoin d’exécuter le programme d’installation pour y accéder). En bas du centre d’administration, sélectionnez **besoin d’aide ?** . Décrivez-nous votre problème et nous vous contacterons par téléphone. 
  - **Appelez le [support technique Microsoft 365 pour les entreprises](../contact-support-for-business-products.md) avec vos questions**. We're here to help! 
  - **Songez à faire appel à un [partenaire Microsoft](https://go.microsoft.com/fwlink/?linkid=391089)**. Si vous manquez de temps ou si vous avez des exigences avancées (telles que le transfert de milliers de fichiers vers le stockage Cloud Microsoft 365 ou l’intégration à d’autres logiciels), un partenaire expérimenté peut être une aide considérable. 

- **Si vous avez plus de 50 employés**, le [Centre d'intégration FastTrack](https://go.microsoft.com/fwlink/?LinkId=517115) est disponible pour vous aider à effectuer votre déploiement. 
