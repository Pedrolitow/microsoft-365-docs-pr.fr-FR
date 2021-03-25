---
title: Centre d’administration Exchange dans EOP autonome
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 97921f0e-832f-40c7-b56d-414faede5191
ms.collection:
- M365-security-compliance
description: Découvrez l’interface de gestion web dans Exchange Online Protection (EOP) autonome.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ab834d14673370a39e148aefa568591ff4c50b8f
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51204824"
---
# <a name="exchange-admin-center-in-standalone-eop"></a>Centre d’administration Exchange dans EOP autonome

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
-  [Exchange Online Protection autonome](exchange-online-protection-overview.md)

Le Centre d’administration Exchange (CAE) est une console de gestion web pour Exchange Online Protection (EOP) autonome.

Vous recherchez la version Exchange Online de cette rubrique ? Consultez la rubrique [Exchange admin center in Exchange Online](/exchange/exchange-admin-center).

## <a name="open-the-eac-in-eop"></a>Ouvrir le CAE dans EOP

Les clients EOP autonomes peuvent accéder au CAE en utilisant les méthodes suivantes :

- **À partir du Centre d’administration Microsoft 365**:

  1. Go to <https://admin.microsoft.com> and click Show **all**.

     ![Cliquez sur Afficher tout dans le Centre d’administration Microsoft 365](../../media/m365-center-show-all.png)

  2. Dans la section **Centres d’administration** qui s’affiche, cliquez **sur Tous les centres d’administration.**

     ![Cliquez sur Tous les centres d’administration dans le Centre d’administration Microsoft 365](../../media/m365-center-select-all-admin-centers.png)

  3. Dans la page **Tous les centres d’administration** qui s’affiche, cliquez **sur Exchange Online Protection**.

- Go directly to `https://admin.protection.outlook.com/ecp/` .

## <a name="common-user-interface-elements-in-the-eac-in-eop"></a>Éléments d’interface utilisateur courants dans le CAE dans EOP

Cette section décrit les éléments d'interface utilisateur disponibles dans le CAE.

![Centre d’administration Exchange dans Exchange Online Protection](../../media/EOP-AdminCenter.png)

### <a name="feature-pane"></a>Volet des fonctionnalités

Il s'agit du premier niveau de navigation pour la plupart des tâches que vous effectuez au sein du CAE. Le volet des fonctionnalités est organisé par domaines de fonctionnalités.

- **Destinataires**: il s’agit de l’endroit où vous allez afficher les groupes et les contacts externes.

- **Autorisations :** c’est ici que vous allez gérer les rôles d’administrateur.

- **Gestion de la** conformité : il s’agit de l’endroit où se trouvent le rapport du groupe de rôles d’administrateur et le rapport du journal d’audit de l’administrateur.

- **Protection**: il s’agit de l’endroit où vous pouvez gérer les stratégies anti-programme malveillant, la stratégie de filtrage des connexions par défaut et DKIM.

  > [!NOTE]
  > Vous devez gérer les stratégies anti-programme malveillant et la stratégie de filtrage des connexions par défaut dans le Centre de sécurité & conformité. Pour plus d’informations, voir [Configure anti-malware policies in EOP](configure-anti-malware-policies.md) and [Configure connection filtering in EOP](configure-the-connection-filter-policy.md).

- **Flux de** messagerie : il s’agit de l’endroit où vous allez gérer les règles de flux de messagerie (également appelées règles de transport), les domaines acceptés et les connecteurs, ainsi que l’endroit où vous pouvez exécuter le suivi des messages.

- **Hybride**: il s’agit de l’endroit où vous pouvez exécuter l’Assistant [Configuration](/Exchange/hybrid-configuration-wizard)hybride et où vous pouvez installer le [module Exchange Online PowerShell](/powershell/exchange/mfa-connect-to-exchange-online-powershell).

### <a name="tabs"></a>Tabulation

Les onglets constituent votre deuxième niveau de navigation. Chaque domaine de fonctionnalités contient différents onglets, chacun représentant une fonctionnalité.

### <a name="toolbar"></a>Barre d'outils

Lorsque vous cliquez sur la plupart des onglets, vous devez voir une barre d'outils. La barre d'outils contient des icônes qui correspondent à une action spécifique. Le tableau suivant décrit les icônes et leurs actions.

****

|Icône|Nom|Action|
|---|---|---|
|![Icône Ajouter](../../media/ITPro-EAC-AddIcon.gif)|Ajouter, Nouveau|Permet de créer un objet. Certaines de ces icônes comportent une flèche vers le bas associée, sur laquelle vous pouvez cliquer pour afficher des objets supplémentaires que vous pouvez créer.|
|![Icône Modifier](../../media/ITPro-EAC-EditIcon.gif)|Modifier|Permet de modifier un objet.|
|![Icône Supprimer](../../media/ITPro-EAC-DeleteIcon.gif)|Supprimer|Permet de supprimer un objet. Certaines des icônes de suppression comportent une flèche vers le bas, sur laquelle vous pouvez cliquer pour afficher des options supplémentaires.|
|![Icône Recherche](../../media/ITPro-EAC-.gif)|Rechercher|Permet d'ouvrir une zone de recherche dans laquelle vous pouvez entrer une expression pour rechercher un objet.|
|![Icône Actualiser](../../media/ITPro-EAC-RefreshIcon.gif)|Actualiser|Permet d'actualiser l'affichage Liste.|
|![Icône Options supplémentaires](../../media/ITPro-EAC-MoreOptionsIcon.gif)|Plus d'options|Utilisez cette icône pour afficher d'autres actions que vous pouvez effectuer pour les objets figurant sous cet onglet. Par exemple, dans **Destinataires \> Utilisateurs**, le fait de cliquer sur cette icône affiche l'option de **Recherche avancée**.  |
|![Icône flèche vers le haut](../../media/ITPro-EAC-UpArrowIcon.gif)![Icône de flèche vers le bas](../../media/ITPro-EAC-DownArrowIcon.gif)|Flèche Haut et flèche Bas|Utilisez ces icônes pour relever ou abaisser la priorité d'un objet.|
|![Icône Suppression](../../media/ITPro-EAC-RemoveIcon.gif)|Supprimer|Permet de supprimer des objets d'une liste.|
|

### <a name="list-view"></a>Affichage Liste

Dans la plupart des cas, vous devez voir un affichage Liste lorsque vous sélectionnez un onglet. La limite d'affichage de l'affichage Liste du CAE est d'environ 10 000 objets. En outre, la pagination est incluse pour vous permettre de paginer les résultats.

### <a name="details-pane"></a>Volet d'informations

Quand vous sélectionnez un objet de l'affichage Liste, les informations relatives à cet objet apparaissent dans le volet d'informations. Dans certains cas, le volet d'informations inclut les tâches de gestion.

### <a name="me-tile-and-help"></a>Vignette de l'utilisateur en cours et Aide

La vignette **Moi** vous permet de fermer votre session du Centre d'administration Exchange (CAE) pour ouvrir ensuite une session en tant qu'utilisateur différent. Dans le menu **déroulant** Icône Aide, vous pouvez ![ faire les actions ](../../media/ITPro-EAC-HelpIcon.gif) suivantes :

- **Aide :** cliquez sur ![ Icône Aide pour afficher le contenu de ](../../media/ITPro-EAC-HelpIcon.gif) l’aide en ligne.
- **Commentaires :** laisser des commentaires.
- **Communauté**: publiez une question pour trouver des réponses dans les forums de la communauté.
- **Désactiver la bulle d’aide**: la bulle d’aide affiche une aide contextuelle pour les champs lorsque vous créez ou modifiez un objet. Vous pouvez activer ou désactiver la bulle d'aide.
- **Afficher la journalisation** des commandes : une nouvelle fenêtre s’ouvre et affiche les commandes PowerShell équivalentes en fonction de ce que vous avez configuré dans le CENTRE D’EAC.

## <a name="supported-browsers"></a>Navigateurs pris en charge

Pour bénéficier d’une meilleure expérience d’utilisation du CAE, nous vous recommandons de toujours utiliser les navigateurs, clients Office et applications les plus récents. Nous vous recommandons également d'installer les mises à jour logicielles lorsqu'elles sont disponibles. Pour plus d’informations sur les navigateurs pris en charge et la système requise pour le service, voir [System requirements for Office](https://products.office.com/office-system-requirements).

## <a name="supported-languages"></a>Langues prises en charge

Les langues suivantes sont pris en charge et disponibles pour le CAE dans EOP autonome.

- Amharique
- Arabe
- basque (Basque)
- Bengla (Inde)
- Bulgare
- Catalan
- Chinois (simplifié)
- Chinois (traditionnel)
- Croate
- Tchèque
- Danois
- Néerlandais
- Anglais
- Estonien
- Filipino (Philippines)
- Finnois
- Français
- Galicien
- Allemand
- Grec
- Goudjrati
- Hébreu
- Hindi
- Hongrois
- Islandais
- Indonésien
- Italien
- Japonais
- Kannada
- Kazakh
- Kiswahili
- Coréen
- Letton
- Lituanien
- Malais (Brunei Darussalam)
- Malais (Malaisie)
- Malayalam
- Marathe
- Norvégien (Bokmål)
- Norvégien (nynorsk)
- Odia
- Perse
- Polonais
- Portugais (Brésil)
- Portugais (Portugal)
- Roumain
- Russe
- Serbe (cyrillique, Serbie)
- Serbe (latin)
- Slovaque
- Slovène
- Espagnol
- Suédois
- Tamoul
- Télougou
- Thaï
- Turc
- Ukrainien
- Ourdou
- Vietnamien
- Gallois