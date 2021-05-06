---
title: Gestionnaire de conformité Microsoft et RGPD
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
description: Le Gestionnaire de conformité Microsoft est un outil gratuit d’évaluation des risques des flux de travail disponible dans le Portail d’approbation de services de Microsoft. Le Gestionnaire de conformité vous permet de suivre, d’affecter et de vérifier les activités de mise en conformité réglementaires liées aux services de cloud computing Microsoft.
ms.openlocfilehash: 69e6551620fb654cb09d46554e6e3c98b6a2fc60
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41595801"
---
# <a name="microsoft-compliance-manager-and-the-gdpr"></a>Gestionnaire de conformité Microsoft et RGPD

Le Règlement général sur la protection des données (RGPD) adopté par l’Union européenne peut affecter votre stratégie de conformité et peut rendre obligatoire des actions spécifiques pour gérer les informations client et utilisateur utilisées dans le Gestionnaire de conformité.

## <a name="user-privacy-settings"></a>Paramètres de confidentialité de l’utilisateur

Certaines réglementations exigent qu’une organisation puisse supprimer les données de l’historique d’un utilisateur. Le Gestionnaire de conformité fournit des fonctionnalités, les **Paramètres de confidentialité de l’utilisateur**, qui permettent aux administrateurs d’effectuer ce qui suit :
  
- [Rechercher un utilisateur](#search-for-a-user)
- [Exporter le rapport de l’historique des données d’un compte](#export-a-report-of-account-data-history)
- [Supprimer l’historique des données d’un utilisateur](#delete-user-data-history)
  
## <a name="search-for-a-user"></a>Rechercher un utilisateur

Pour rechercher un compte d’utilisateur :
  
1. Entrez l’alias de l’adresse e-mail de l’utilisateur (informations à gauche du symbole @), puis choisissez le nom de domaine à partir de la liste des suffixes de domaine à droite. Pour les organisations ayant plusieurs domaines inscrits, revérifiez le suffixe du nom de domaine pour éviter toute erreur.

2. Une fois que le nom d’utilisateur est correctement entré, sélectionnez **Rechercher**.

3. Pour les comptes d’utilisateur non renvoyés, la page affiche **Utilisateur introuvable**. Vérifiez l’adresse e-mail de l’utilisateur, puis apportez les corrections nécessaires le cas échéant. Pour réessayer, sélectionnez **Rechercher**.

4. Pour les comptes d’utilisateur renvoyés, le texte du bouton passe de **Rechercher** à **Effacer**. Ceci indique que les comptes d’utilisateur renvoyés est le contexte opérationnel pour les fonctions supplémentaires et que ces dernières s’appliquent à ce compte d’utilisateur.

5. Pour effacer les résultats de la recherche et rechercher un autre utilisateur, sélectionnez **Effacer**.

## <a name="export-a-report-of-account-data-history"></a>Exporter le rapport de l’historique des données d’un compte

Pour chaque compte d’utilisateur identifié, vous pouvez générer un rapport sur les dépendances liées au compte. Ces informations vous permettent de réaffecter des éléments d’action en cours ou de garantir l’accès à des preuves chargées.
  
 Pour générer et exporter un rapport :
  
1. Sélectionnez **Exporter** pour générer et télécharger un rapport sur les éléments d’action de contrôle du Gestionnaire de conformité actuellement attribués au compte d’utilisateur renvoyé, ainsi que la liste des documents chargés par cet utilisateur. En l’absence d’actions attribuées ou de documents chargés, un message d’erreur indique « Aucune données pour cet utilisateur ».

2. Le rapport est téléchargé en arrière-plan de la fenêtre active du navigateur. Si aucune fenêtre contextuelle de téléchargement n’apparaît, vérifiez l’historique de téléchargement de votre navigateur.

3. Ouvrez le document pour consulter les données du rapport.

> [!IMPORTANT]
> Les données du rapport ne sont pas une liste historique qui consigne et affiche les changements d’état de l’historique d’affectation des éléments d’action. Le rapport généré est une capture instantanée des éléments d’action du contrôle affectés pendant l’exécution du rapport (horodateur indiqué dans le rapport). Par exemple, toute réaffectation des éléments d’action génère une autre capture instantanée des données du rapport si ce rapport est généré une nouvelle fois pour le même utilisateur.
  
## <a name="delete-user-data-history"></a>Supprimer l’historique des données d’un utilisateur

Cette action définit tous les éléments affectés d’action de contrôle sur « non affecté » à l’utilisateur renvoyé. Elle définit la valeur **chargé par** sur « utilisateur supprimé » pour tous les documents chargés par l’utilisateur renvoyé.
  
Pour supprimer un élément d’action du compte d’utilisateur et l’historique de chargement des documents :
  
1. Sélectionnez **Supprimer**.

    Une boîte de dialogue de confirmation apparaît, indiquant : *Cette action supprime tous les éléments d’action du contrôle affectés et l’historique de chargement des documents pour l’utilisateur sélectionné. Cette action est définitive. Voulez-vous vraiment continuer ?*  »

2. Pour continuer, sélectionnez **OK**. Sinon, sélectionnez **Annuler**.
