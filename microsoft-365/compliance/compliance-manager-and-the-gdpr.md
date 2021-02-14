---
title: Gestionnaire de conformité Microsoft et R GDPR
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Le Gestionnaire de conformité Microsoft est un outil gratuit d’évaluation des risques basé sur les flux de travail dans le portail d’approbation de services Microsoft. Le Gestionnaire de conformité vous permet de suivre, d’affecter et de vérifier les activités de conformité réglementaire liées aux services cloud de Microsoft.
ms.openlocfilehash: 69e6551620fb654cb09d46554e6e3c98b6a2fc60
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41595801"
---
# <a name="microsoft-compliance-manager-and-the-gdpr"></a>Gestionnaire de conformité Microsoft et R GDPR

Le règlement général sur la protection des données (R GDPR) adopté par l’Union européenne peut avoir un impact sur votre stratégie de conformité et rendre obligatoires des actions spécifiques pour gérer les informations utilisateur et client utilisées dans le Gestionnaire de conformité.

## <a name="user-privacy-settings"></a>Paramètres de confidentialité de l’utilisateur

Certaines réglementations exigent qu’une organisation puisse supprimer les données de l’historique des utilisateurs. Le Gestionnaire de conformité fournit **des fonctions de paramètres** de confidentialité utilisateur qui permettent aux administrateurs de :
  
- [Rechercher un utilisateur](#search-for-a-user)
- [Exporter le rapport de l’historique des données d’un compte](#export-a-report-of-account-data-history)
- [Supprimer l’historique des données d’un utilisateur](#delete-user-data-history)
  
## <a name="search-for-a-user"></a>Rechercher un utilisateur

Pour rechercher un compte d’utilisateur :
  
1. Entrez l’alias de messagerie de l’utilisateur (les informations à gauche du symbole @ ) et choisissez le nom de domaine dans la liste des suffixes de domaine à droite. Pour les organisations avec plusieurs domaines inscrits, vérifiez le suffixe du nom de domaine pour vous assurer qu’il est correct.

2. Lorsque vous avez entré correctement le nom d’utilisateur, sélectionnez **Rechercher.**

3. Pour les comptes d’utilisateurs qui ne sont pas renvoyés, la page affiche **User in found**. Vérifiez les informations de l’adresse e-mail de l’utilisateur et a corrections si nécessaire. Pour réessayer, sélectionnez **Rechercher.**

4. Pour les comptes d’utilisateur renvoyés, le texte du bouton passe de **La** recherche à **Effacer.** Cela indique que le compte d’utilisateur renvoyé est le contexte d’exploitation pour les fonctions supplémentaires et que ces fonctions s’appliquent à ce compte d’utilisateur.

5. Pour effacer les résultats de recherche et rechercher un autre utilisateur, sélectionnez **Effacer.**

## <a name="export-a-report-of-account-data-history"></a>Exporter le rapport de l’historique des données d’un compte

Pour chaque compte d’utilisateur identifié, vous pouvez générer un rapport des dépendances liées au compte. Ces informations vous permettent de réaffecter les éléments d’action ouverts ou de garantir l’accès aux preuves précédemment téléchargées.
  
 Pour générer et exporter un rapport :
  
1. Sélectionnez **Exporter** pour générer et télécharger un rapport des éléments d’action de contrôle du Gestionnaire de conformité actuellement affectés au compte d’utilisateur renvoyé, ainsi que la liste des documents téléchargés par cet utilisateur. S’il n’y a pas d’actions affectées ou de documents téléchargés, un message d’erreur indique « Aucune donnée pour cet utilisateur ».

2. Le rapport est téléchargé en arrière-plan de la fenêtre active du navigateur. Si vous ne voyez pas de fenêtre de téléchargement, vous souhaitez vérifier l’historique de téléchargement de votre navigateur.

3. Ouvrez le document pour consulter les données du rapport.

> [!IMPORTANT]
> Les données du rapport ne sont pas une liste historique qui conserve et affiche les modifications d’état apportées à l’historique d’affectation de l’élément d’action. Le rapport généré est un instantané des éléments d’action de contrôle affectés au moment de l’utilisation du rapport (date et horodaté écrits dans le rapport). Par exemple, toute réaffectation ultérieure des éléments d’action entraîne des données de rapport de capture instantanée différentes si le rapport est généré à nouveau pour le même utilisateur.
  
## <a name="delete-user-data-history"></a>Supprimer l’historique des données d’un utilisateur

Définit tous les éléments d’action de contrôle affectés à l’utilisateur renvoyé sur « non affecté ». Définit la **valeur téléchargée par valeur** pour tous les documents téléchargés par l’utilisateur renvoyé sur « utilisateur supprimé ».
  
Pour supprimer l’élément d’action du compte d’utilisateur et l’historique de chargement du document :
  
1. Sélectionnez **Supprimer**.

    Une boîte de dialogue de confirmation s’affiche : « Cette action supprime toutes les affectations d’élément d’action de contrôle et l’historique de téléchargement de *document pour l’utilisateur sélectionné. Cette action est permanente. Voulez-vous vraiment continuer ?*»

2. Pour continuer, **sélectionnez OK,** sinon **sélectionnez Annuler.**
