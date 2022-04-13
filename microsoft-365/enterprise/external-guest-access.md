---
title: Vue d’ensemble des options de collaboration externe dans Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- SPO_Content
ms.localizationpriority: medium
description: Découvrez comment les personnes extérieures à votre organisation peuvent accéder à votre abonnement Microsoft 365 pour les réunions, le partage d’invités, la conversation et la collaboration.
ms.openlocfilehash: 988a1ecae8a060cae2334f97ef19bc90ba2be6bc
ms.sourcegitcommit: 5eff41a350a01e18d9cdd572c9d8ff99d6c9563a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64836451"
---
# <a name="overview-of-external-collaboration-options-in-microsoft-365"></a>Vue d’ensemble des options de collaboration externe dans Microsoft 365

Avec Microsoft 365, vos utilisateurs peuvent collaborer avec des personnes extérieures à votre organisation de différentes façons. Les utilisateurs peuvent partager des fichiers, inviter des invités à des équipes, avoir des réunions avec des participants externes et discuter avec des personnes d’autres organisations. Cet article traite des options de collaboration externe disponibles et des liens vers le contenu dont vous avez besoin pour configurer chacune d’elles.

Le tableau suivant présente les principales façons dont les personnes extérieures à votre organisation peuvent accéder à vos ressources Microsoft 365 :

|Activité|Type de compte|Valeur par défaut|
|:-------|:-----------|:--------------|
|Partage de fichiers et de dossiers authentifié|Compte invité|Activé|
|Partage de site|Compte invité|Activé|
|Partage d’équipe|Compte invité|Activé|
|Canal partagé dans Teams|Compte externe Microsoft 365 existant|Désactivé|
|Conversations et réunions externes|Compte externe Microsoft 365 existant|Activé|
|Participation anonyme à une réunion|Aucun|Activé|
|Partage de fichiers et de dossiers non authentifié|Aucun|Activé|

Les personnes extérieures à votre organisation n’ont pas accès, sauf si un utilisateur de votre organisation lance l’une de ces activités. Vous pouvez désactiver l’un de ces paramètres si vous ne souhaitez pas autoriser cette activité dans votre organisation.

## <a name="document-site-and-team-sharing-with-guest-accounts"></a>Partage de documents, de site et d’équipe avec des comptes invités

Le partage de documents, de sites et d’équipes avec des personnes extérieures à votre organisation utilise des *comptes invités*. Les comptes invités sont un type de compte dans Azure Active Directory qui est géré via [Azure AD collaboration B2B](/azure/active-directory/external-identities/what-is-b2b). Ils peuvent être utilisés pour partager des ressources dans votre organisation avec toute personne disposant d’une adresse e-mail. Vous pouvez gérer les comptes invités de la même façon que vous gérez les utilisateurs de votre organisation. Les invités n’ont pas besoin d’une licence pour la plupart des fonctionnalités de collaboration. 

Les invités peuvent uniquement accéder aux ressources que vous partagez spécifiquement avec eux.

Si l’invité dispose d’un compte professionnel ou scolaire dans une autre organisation ou d’un compte Microsoft, il peut se connecter avec son nom d’utilisateur et son mot de passe standard. S’ils ont un autre type de compte, tel qu’un compte Gmail, ils peuvent se connecter à l’aide d’un code secret unique envoyé à leur adresse e-mail.

Avec les invités, vous pouvez :

- Invitez-les à Microsoft 365 groupes, équipes ou sites SharePoint où ils peuvent collaborer avec des personnes de votre organisation.
- Partagez un seul fichier ou un dossier avec eux qu’ils peuvent afficher ou modifier en fonction des autorisations que vous leur accordez.

Pour plus d’informations sur la planification de la collaboration avec les invités dans Microsoft 365, consultez les références suivantes :

- [Planifier la collaboration externe](/microsoft-365/solutions/plan-external-collaboration)
- [Configurer le partage de fichiers sécurisé et la collaboration avec Microsoft Teams](/microsoft-365/solutions/setup-secure-collaboration-with-teams)

Pour plus d’informations sur la configuration de Microsoft 365 pour la collaboration avec les invités, consultez les références suivantes :

- [Collaborer avec des invités sur un document](/microsoft-365/solutions/collaborate-on-documents)
- [Collaborer avec des invités sur un site](/microsoft-365/solutions/collaborate-in-site)
- [Collaborer avec des invités au sein d’une équipe](/microsoft-365/solutions/collaborate-as-team)
 
## <a name="shared-channels"></a>Canaux partagés

Les canaux partagés sont un type de canal Teams qui vous permet de partager avec des personnes extérieures à l’équipe, y compris des personnes d’autres organisations Microsoft 365. Bien que les canaux partagés sont activés par défaut dans Teams, la collaboration externe avec les canaux partagés est désactivée par défaut. La collaboration externe avec les canaux partagés utilise [Azure AD connexion directe B2B](/azure/active-directory/external-identities/b2b-direct-connect-overview) qui vous permet d’ajouter des personnes d’autres organisations Microsoft 365 à Teams canaux sans avoir à créer de compte invité.

Les canaux partagés présentent un avantage particulier par rapport aux comptes invités, en ce qu’ils n’obligent pas les participants externes à changer d’organisation dans le client de bureau Teams ou à se connecter à votre organisation. Ils peuvent rester connectés à leur organisation et accéder directement au canal.

Le partage de canaux avec des personnes extérieures à votre organisation nécessite que votre organisation et l’organisation externe configurent une relation organisationnelle dans [Azure AD B2B Direct Connecter](/azure/active-directory/external-identities/b2b-direct-connect-overview).

Pour plus d’informations sur la configuration de Microsoft 365 pour une collaboration externe avec des canaux partagés, consultez les références suivantes :

- [Planifier la collaboration externe](/microsoft-365/solutions/plan-external-collaboration)
- [Canaux partagés dans Microsoft Teams](/MicrosoftTeams/shared-channels)
- [Collaborer avec des participants externes dans un canal](/microsoft-365/solutions/collaborate-teams-direct-connect)

## <a name="external-chat-and-meetings"></a>Conversations et réunions externes

Les utilisateurs de votre organisation peuvent discuter, ajouter des utilisateurs à des réunions et utiliser l’audioconférence ou la vidéoconférence dans Teams avec des utilisateurs d’organisations Microsoft 365 externes. Par défaut, les utilisateurs de votre organisation peuvent communiquer de ces manières avec tous les autres domaines Microsoft 365. Les membres d’autres organisations peuvent communiquer de cette façon avec vos utilisateurs s’ils connaissent l’adresse e-mail de l’utilisateur. Vous pouvez autoriser ou bloquer des domaines spécifiques ou bloquer tous les domaines si vous souhaitez désactiver la fonctionnalité.

Vous pouvez également autoriser les utilisateurs de votre organisation à communiquer avec des personnes extérieures à votre organisation qui utilisent des comptes Teams qui ne sont pas gérés par une organisation, ainsi qu’avec des Skype Entreprise (en ligne et en local) et des utilisateurs Skype.

Les comptes invités ne sont pas utilisés dans le cadre de conversations et de réunions externes. Les participants externes restent connectés à leur organisation ou à Skype et peuvent communiquer directement avec des personnes de votre organisation. Ils n’ont pas accès à vos équipes ou canaux.

Pour plus d’informations sur la configuration de Microsoft 365 pour les conversations et réunions externes, consultez les références suivantes :

- [Utiliser l’accès invité et l’accès externe pour collaborer avec des personnes extérieures à votre organisation](/microsoftteams/communicate-with-users-from-other-organizations)
- [Gérer l’accès externe dans Microsoft Teams](/microsoftteams/manage-external-access).

## <a name="anonymous-meeting-join"></a>Participation anonyme à une réunion 

Les personnes extérieures à votre organisation peuvent participer aux réunions des manières suivantes :

- S’ils sont connectés à votre organisation avec un compte invité, ils participent à des réunions en tant qu’invité.
- S’ils sont connectés à une autre organisation avec un compte professionnel ou scolaire et que votre organisation a activé l’accès externe, ils rejoignent des réunions en tant que participant externe.
- S’ils ne sont pas invités ou participants externes, ils doivent participer aux réunions de manière anonyme.

Si le paramètre de participation anonyme est activé pour votre organisation, les utilisateurs anonymes ne peuvent participer à une réunion qu’à l’aide d’un lien de réunion partagé avec eux (par exemple, un lien dans l’invitation à la réunion). Ils sont invités à entrer un nom complet de leur choix lors de la participation anonyme à la réunion. Selon les paramètres de la salle d’attente, l’utilisateur anonyme peut être automatiquement admis à la réunion ou être ajouté à une salle d’attente où l’organisateur de la réunion (ou les participants à la réunion avec le rôle de présentateur) peut autoriser ou refuser l’accès à la réunion. 

Il n’est pas possible de vérifier l’identité des utilisateurs anonymes avant, pendant ou après la réunion. 

Vous pouvez contrôler la capacité des utilisateurs anonymes à participer à des réunions au niveau de l’organisation. S’il est activé pour l’organisation, les organisateurs de réunion peuvent contrôler la participation anonyme via les paramètres de stratégie de réunion.

Pour plus d’informations sur la configuration de la participation anonyme pour les réunions, consultez [Gérer les paramètres de réunion dans Microsoft Teams](/microsoftteams/meeting-settings-in-teams).

## <a name="unauthenticated-file-and-folder-access"></a>Accès aux fichiers et dossiers non authentifiés

Dans Microsoft 365, les fichiers et dossiers dans Teams, SharePoint et OneDrive peuvent être partagés à l’aide de liens non authentifiés ( ou *n’importe qui* ). Tous les liens donnent accès à l’élément partagé à toute personne disposant du lien. Tous les liens peuvent être partagés avec d’autres personnes, ce qui permet à ces personnes d’accéder au fichier ou au dossier.

Les personnes qui utilisent un lien Tout le monde n’ont pas besoin de s’authentifier et leur accès ne peut pas être contrôlé. Les propriétaires de fichiers et de dossiers peuvent révoquer l’accès à tout moment en supprimant le lien.

Les liens Tout le monde ne peuvent pas être utilisés avec des fichiers dans un site Teams de canal partagé.

Pour plus d’informations sur l’utilisation du partage anonyme de fichiers et de dossiers, consultez les références suivantes :

- [Gérer les paramètres de partage](/sharepoint/turn-external-sharing-on-or-off)
- [Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés](/microsoft-365/solutions/best-practices-anonymous-sharing)

## <a name="related-topics"></a>Voir aussi

[Introduction à la collaboration de fichiers dans Microsoft 365, optimisée par SharePoint](/sharepoint/intro-to-file-collaboration)

[Collaboration sur des fichiers dans SharePoint avec Microsoft 365](/sharepoint/deploy-file-collaboration)

[Utiliser l’accès invité et l’accès externe pour collaborer avec des personnes extérieures à votre organisation](/microsoftteams/communicate-with-users-from-other-organizations)

[Limiter le partage d’invités à des organisations spécifiques](/microsoft-365/solutions/limit-guest-sharing-to-specific-organization)

[Limiter les organisations où les utilisateurs peuvent avoir des comptes invités](/microsoft-365/solutions/limit-organizations-where-users-have-guest-accounts)