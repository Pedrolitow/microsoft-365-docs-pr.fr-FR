---
title: Data Residency pour Microsoft Teams
description: En savoir plus sur la résidence des données pour Microsoft Teams
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.service: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.date: ''
ms.reviewer: dmwmsft
ms.custom:
- it-pro
ms.collection:
- M365-subscription-management
ms.openlocfilehash: 6f7853537a4a263e888fc27b496cd61f83f13024
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805413"
---
# <a name="data-residency-for-microsoft-teams"></a>Data Residency pour Microsoft Teams

## <a name="data-residency-commitments-available"></a>Data Residency engagements disponibles

### <a name="product-terms"></a>Conditions du produit

Conditions requises :

1. _Le locataire_ dispose d’un pays d’inscription inclus dans _la zone géographique de la région_ locale, l’Union européenne ou le États-Unis.

**Engagement:**

_Pour connaître la langue actuelle, reportez-vous aux Conditions relatives au [produit de confidentialité et de sécurité](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all) et consultez la section intitulée « Emplacement des données client au repos pour les principaux services en ligne »._

### <a name="advanced-data-residency-add-on"></a>Module complémentaire Data Residency avancé

Conditions requises :

1. _Le client_ a un pays d’inscription inclus dans _Région locale Geography_ ou _Expanded Local Region Geography_.
1. _Le locataire_ dispose d’un abonnement advanced Data Residency valide pour tous les utilisateurs du _locataire_
1. Les données client de l’abonnement Microsoft Teams sont approvisionnées dans _Région locale Géographie_ ou _Zone géographique de la région locale étendue_.

**Engagement:**

Reportez-vous à la [page Engagement ADR](m365-dr-commitments.md#microsoft-teams) pour comprendre les engagements spécifiques fournis par le biais des Conditions du produit.  Voici quelques exemples de données validées :

- Messages de conversation/canal et structure d’équipe : chaque équipe de Microsoft Teams est soutenue par un groupe moderne Microsoft 365, son site SharePoint et sa boîte aux lettres Exchange. Les conversations privées (y compris les conversations de groupe), les messages envoyés dans le cadre d’une conversation dans un canal et la structure des équipes et des canaux sont stockés dans un service de conversation azure. Les données sont également stockées dans un dossier masqué dans les boîtes aux lettres d’utilisateur et de groupe pour activer les fonctionnalités de protection des informations.  
- Images et médias : les médias utilisés dans les conversations (à l’exception des gif Giphy qui ne sont pas stockés, mais qui constituent un lien de référence vers l’URL Giphy d’origine) sont stockés dans un service media basé sur Azure déployé aux mêmes emplacements que le service de conversation.
- Enregistrements de réunion : Pour les utilisateurs de Microsoft Stream (sur SharePoint), les enregistrements de réunion sont stockés dans le stockage OneDrive Entreprise de l’utilisateur qui lance l’enregistrement.

### <a name="multi-geo-add-on"></a>Module complémentaire multigéographique

Conditions requises :

1. _Les locataires_ disposent d’un abonnement multigéographique valide qui couvre tous les utilisateurs affectés à une _zone géographique satellite_
1. Le client doit avoir un Accord Entreprise actif.
1. Le nombre total d’unités multigéographiques achetées doit être supérieur à 5 % du nombre total de sièges éligibles dans le _locataire_.

**Engagement:** Les clients peuvent affecter des utilisateurs de Microsoft Teams à n’importe quelle _zone géographique satellite_ prise en charge par multigéographique. Les données client suivantes seront stockées dans la _zone géographique satellite_ appropriée : données de conversation Teams qui se composent de messages de conversation, y compris les messages privés, les messages de canal et les images utilisées dans les conversations.

## <a name="multi-geo-capabilities-in-microsoft-teams"></a>Fonctionnalités multigéographiques dans Microsoft Teams

Dans Teams, les fonctionnalités multigéographiques permettent de stocker les données de conversation Teams au repos dans un emplacement _Géographique de macro Région_ ou _Région locale_ spécifié. Les données de conversation se composent de messages de conversation, y compris les messages privés, les messages de canal et les images utilisées dans les conversations.

Teams utilise l’emplacement de données préféré (PDL) pour les utilisateurs et les groupes afin de déterminer où stocker les données. Si la pdL n’est pas définie ou n’est pas valide, les données sont stockées dans l’emplacement _géographique approvisionné principal_ du locataire.

>[!NOTE]
>Les fonctionnalités multigéographiques dans Teams ont été déployées en juillet 2021. Au cours des prochains trimestres, vos messages de conversation et de canal seront automatiquement migrés vers la zone géographique de la macro _ou la_ _zone géographique de la région locale_ . Toutes les nouvelles modifications pdL seront traitées une fois que le _locataire_ aura terminé la synchronisation initiale, et les nouvelles modifications pdL au-delà seront mises en file d’attente et traitées dans l’ordre dans lequel elles sont reçues.

### <a name="user-chat"></a>Conversation utilisateur

La conversation utilisateur comprend des messages de réunion un-à-un, un-à-plusieurs et privés.

Lorsqu’un nouvel utilisateur est créé, Teams lit le PDL de l’utilisateur et stocke toutes ses données de conversation dans cet emplacement _géographique de la région macro_ ou de la _région locale_ .
Pour les utilisateurs existants, si un administrateur ajoute ou modifie le PDL d’un utilisateur, les données de conversation de cet utilisateur sont ajoutées à une file d’attente de migration pour être déplacées vers l’emplacement _géographique de la région_ macro ou _de la région locale_ spécifié.

L’emplacement de stockage d’une conversation un-à-un ou un-à-plusieurs est basé sur le PDL de la personne qui a créé la conversation. Si le PDL de cet utilisateur est modifié, la conversation est migrée vers le nouvel emplacement _Géographique de la région_ macro ou _De la région locale_ . L’emplacement de stockage d’une conversation de réunion est basé sur la PDL de l’organisateur de la réunion.

Pour rechercher l’emplacement actuel des données Teams d’un utilisateur, connectez-vous à Teams PowerShell et exécutez la commande suivante :

```PowerShell
Get-MultiGeoRegion -EntityType User -EntityId <UPN>
```

### <a name="channel-messages"></a>Messages de canal

Chaque groupe Microsoft 365 a un emplacement de données préféré (PDL) qui indique l’emplacement _Geography_ où les données associées doivent être stockées. Teams utilise le PDL pour le groupe associé à chaque équipe afin de déterminer où stocker les données de messagerie de canal pour cette équipe. Cela inclut les canaux privés et les conversations qui se produisent dans une réunion de canal.

Lorsqu’un utilisateur crée une équipe, le PDL de cet utilisateur détermine le PDL affecté au groupe Microsoft 365. Le PDL du groupe détermine où les données de cette équipe sont stockées. Si la pdL de cet utilisateur change ultérieurement, la pdl du groupe n’est pas modifiée.

Pour les équipes existantes, si un administrateur ajoute ou modifie le PDL pour le groupe Microsoft 365 qui sauvegarde une équipe, les données de messagerie du canal de cette équipe sont ajoutées à une file d’attente de migration pour être déplacées vers l’emplacement _géographique de la région_ macro ou _de la région locale_ spécifié.

La modification de la PDL du groupe Microsoft 365 met en file d’attente les données Teams à migrer vers l’emplacement _géographique de la macro ou_ _de la région locale_ choisi. Toutefois, cela ne migre pas automatiquement le site SharePoint ou les fichiers associés au groupe. Vous devez déplacer le site séparément en suivant les procédures décrites dans Déplacer un site SharePoint vers un autre emplacement _Geography_ . Veillez à effectuer les deux étapes pour éviter les données Teams et les données SharePoint pour un groupe dans des emplacements différents.

Pour trouver l’emplacement actuel des données d’une équipe, connectez-vous à Teams PowerShell et exécutez la commande suivante :

```PowerShell
Get-MultiGeoRegion -EntityType Group -EntityId <GroupObjectId>
```

### <a name="user-experience"></a>Expérience de l’utilisateur

Teams Multi-Geo est transparent pour l’utilisateur final. Une fois que vous avez modifié la PDL d’un utilisateur ou d’un groupe, les données respectives sont mises en file d’attente pour la migration et la migration se produit automatiquement sans impact sur l’utilisateur ou son client Teams, même s’ils sont actifs pendant la migration.

### <a name="migration"></a>Migration

**Onglet Fichiers** Une fois la migration terminée, le chargement complet de l’onglet Fichiers peut prendre plus de temps (jusqu’à 7 secondes) lorsque l’utilisateur tente de l’utiliser pour la première fois.

**Période de lecture seule** Les services de conversation Teams déplacent chaque thread individuellement. Le thread est verrouillé dans un état en lecture seule pendant le déplacement, qui dure quelques secondes par thread. Les threads restent accessibles pendant la migration.

**Dans l’étendue de la migration** Outre les Exchange Online, SharePoint Online et OneDrive Entreprise ; Microsoft migrera les données Teams vers le centre de données local.

- Messages de conversation Teams, y compris les messages privés et les messages de canal.
- Images Teams utilisées dans les conversations.

Les fichiers Teams sont stockés dans SharePoint Online et les fichiers de conversation Teams sont stockés dans OneDrive Entreprise. La messagerie vocale, le calendrier et les contacts sont stockés dans Exchange Online. Dans de nombreux cas, Exchange Online, SharePoint Online et OneDrive Entreprise sont déjà utilisés par le client dans le centre de données local _Geography_ et font également partie du programme de migration Microsoft 365 pour les pays clients éligibles.

### <a name="how-can-i-determine-customer-data-location"></a>Comment puis-je déterminer l’emplacement des données client ?
Vous trouverez l’emplacement réel des données dans _le Centre de Administration du locataire_. En tant qu’administrateur _de locataire_, vous pouvez trouver l’emplacement réel des données validées en accédant à Administration| Paramètres | Paramètres de l’organisation| Profil d’organisation| Emplacement des données.
