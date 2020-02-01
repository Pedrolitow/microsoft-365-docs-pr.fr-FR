---
title: Centre d’administration Exchange dans Exchange Online Protection
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 97921f0e-832f-40c7-b56d-414faede5191
ms.collection:
- M365-security-compliance
description: Le Centre d'administration Exchange (CAE) est la console de gestion basée sur le web pour Microsoft Exchange Online Protection (EOP).
ms.openlocfilehash: 3a00b6b259c94e1446b6d6dc49b0f5daa9178cbd
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41599401"
---
# <a name="exchange-admin-center-in-exchange-online-protection"></a>Centre d’administration Exchange dans Exchange Online Protection

Le Centre d'administration Exchange (CAE) est la console de gestion basée sur le web pour Microsoft Exchange Online Protection (EOP).

Vous recherchez la version Exchange Server de cette rubrique ? Consultez la rubrique [Centre d’administration Exchange dans Exchange Server](https://docs.microsoft.com/exchange/architecture/client-access/exchange-admin-center).

Vous recherchez la version Exchange Online de cette rubrique ? Consultez la rubrique [Exchange admin center in Exchange Online](https://docs.microsoft.com/exchange/exchange-admin-center).

## <a name="accessing-the-eac"></a>Accès au CAE

Dans la plupart des cas, les clients EOP accèdent au centre d’administration Exchange par le biais du centre d’administration Microsoft 365. Un lien vers EOP est disponible dans le menu déroulant de la vignette **Administrateur**, située près de la vignette **Moi**. Cliquez sur la vignette **Administrateur** et sélectionnez **Exchange Online Protection** dans le menu déroulant pour accéder au CAE.

Vous pouvez également accéder à la page de connexion du CAE directement via l'URL suivante : `https://admin.protection.outlook.com/ecp/<companydomain>`. Par exemple, `https://admin.protection.outlook.com/ecp/contoso.onmicrosoft.com`. Après avoir indiqué vos informations de connexion d'utilisateur, vous être envoyé directement dans le CAE.

## <a name="common-user-interface-elements-in-the-eac"></a>Éléments d'interface utilisateur courants dans le CAE

Cette section décrit les éléments d'interface utilisateur disponibles dans le CAE.

![EOP-AdminCenter](../media/EOP-AdminCenter.png)

### <a name="feature-pane"></a>Volet des fonctionnalités

Il s'agit du premier niveau de navigation pour la plupart des tâches que vous effectuez au sein du CAE. Le volet des fonctionnalités est organisé par domaines de fonctionnalités.

1. **Destinataires**: c’est ici que vous allez afficher les utilisateurs internes et les contacts externes.

2. **Autorisations**: ce qui vous permet de gérer les rôles d’administrateur.

3. **Gestion de la conformité**: c’est ici que se trouvent les journaux et les rapports d’audit, tels que le rapport de groupe de rôles d’administrateur.

4. **Protection**: c’est ici que vous gérerez la protection contre les programmes malveillants et le courrier indésirable pour votre organisation, ainsi que gérer les messages en quarantaine.

5. **Flux de messagerie**: c’est ici que vous gérerez les règles, les domaines acceptés et les connecteurs, ainsi que les emplacements dans lesquels vous allez effectuer le suivi des messages.

### <a name="tabs"></a>Onglets

Les onglets constituent votre deuxième niveau de navigation. Chaque domaine de fonctionnalités contient différents onglets, chacun représentant une fonctionnalité.

### <a name="toolbar"></a>Barre d'outils

Lorsque vous cliquez sur la plupart des onglets, vous devez voir une barre d'outils. La barre d'outils contient des icônes qui correspondent à une action spécifique. Le tableau suivant décrit les icônes et leurs actions.

|**Icône**|**Nom**|**Action**|
|:-----|:-----|:-----|
|![Icône Ajouter](../media/ITPro-EAC-AddIcon.gif)|Ajouter, Nouveau|Permet de créer un objet. Certaines de ces icônes comportent une flèche vers le bas associée, sur laquelle vous pouvez cliquer pour afficher des objets supplémentaires que vous pouvez créer.|
|![Icône Modifier](../media/ITPro-EAC-EditIcon.gif)|Modifier|Permet de modifier un objet.|
|![Icône Supprimer](../media/ITPro-EAC-DeleteIcon.gif)|Supprimer|Permet de supprimer un objet. Certaines des icônes de suppression comportent une flèche vers le bas, sur laquelle vous pouvez cliquer pour afficher des options supplémentaires.|
|![Icône Recherche](../media/ITPro-EAC-.gif)|Rechercher|Permet d'ouvrir une zone de recherche dans laquelle vous pouvez entrer une expression pour rechercher un objet.|
|![Icône Actualiser](../media/ITPro-EAC-RefreshIcon.gif)|Actualiser|Permet d'actualiser l'affichage Liste.|
|![Icône Options supplémentaires](../media/ITPro-EAC-MoreOptionsIcon.gif)|Plus d'options|Utilisez cette icône pour afficher d'autres actions que vous pouvez effectuer pour les objets figurant sous cet onglet. Par exemple, dans **Destinataires \> Utilisateurs**, le fait de cliquer sur cette icône affiche l'option de **Recherche avancée**.  |
|![Icône flèche vers le haut](../media/ITPro-EAC-UpArrowIcon.gif)![Icône de flèche vers le bas](../media/ITPro-EAC-DownArrowIcon.gif)|Flèche Haut et flèche Bas|Utilisez ces icônes pour relever ou abaisser la priorité d'un objet.|
|![Icône Suppression](../media/ITPro-EAC-RemoveIcon.gif)|Supprimer|Permet de supprimer des objets d'une liste.|

### <a name="list-view"></a>Affichage Liste

Dans la plupart des cas, vous devez voir un affichage Liste lorsque vous sélectionnez un onglet. La limite d'affichage de l'affichage Liste du CAE est d'environ 10 000 objets. En outre, la pagination est incluse pour vous permettre de paginer les résultats.

### <a name="details-pane"></a>Volet d'informations

Quand vous sélectionnez un objet de l'affichage Liste, les informations relatives à cet objet apparaissent dans le volet d'informations. Dans certains cas, le volet d'informations inclut les tâches de gestion.

### <a name="me-tile-and-help"></a>Vignette de l'utilisateur en cours et Aide

La vignette **Moi** vous permet de fermer votre session du Centre d'administration Exchange (CAE) pour ouvrir ensuite une session en tant qu'utilisateur différent. Dans le menu déroulant **Aide**![Icône d'aide](../media/ITPro-EAC-HelpIcon.gif), vous pouvez effectuer les actions suivantes :

1. **Aide**: cliquez ![sur l'](../media/ITPro-EAC-HelpIcon.gif) icône aide pour afficher le contenu de l’aide en ligne.

2. **Désactiver la bulle d'** aide : la bulle d’aide affiche une aide contextuelle pour les champs lorsque vous créez ou modifiez un objet. Vous pouvez activer ou désactiver la bulle d'aide.

3. **Copyright**: cliquez sur ce lien pour lire l’avis de copyright pour Exchange Online Protection.

4. **Confidentialité**: cliquez pour lire la politique de confidentialité pour Exchange Online Protection.

## <a name="supported-browsers"></a>Navigateurs pris en charge

Pour bénéficier d’une meilleure expérience d’utilisation du CAE, nous vous recommandons de toujours utiliser les navigateurs, clients Office et applications les plus récents. Nous vous recommandons également d'installer les mises à jour logicielles lorsqu'elles sont disponibles. Pour plus d’informations sur les navigateurs pris en charge et la configuration système requise pour le service, voir [Configuration requise pour Office](https://products.office.com/office-system-requirements).

## <a name="supported-languages-in-eop"></a>Langues prises en charge dans EOP

Les langues suivantes sont prises en charge et disponibles dans Exchange Online Protection.

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


