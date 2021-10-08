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
ms.localizationpriority: ''
ROBOTS: NOINDEX, NOFOLLOW
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Le Gestionnaire de conformité Microsoft est un outil gratuit d’évaluation des risques des flux de travail disponible dans le Portail d’approbation de services de Microsoft. Le Gestionnaire de conformité vous permet de suivre, d’affecter et de vérifier les activités de mise en conformité réglementaires liées aux services de cloud computing Microsoft.
ms.openlocfilehash: b4a648c43fb20f557b85e24e9e67de036cc4f2e0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60168661"
---
# <a name="microsoft-compliance-manager-and-the-gdpr"></a>Gestionnaire de conformité Microsoft et RGPD

Le Règlement général sur la protection des données (RGPD) adopté par l’Union européenne peut affecter votre stratégie de conformité et peut rendre obligatoire des actions spécifiques pour gérer les informations client et utilisateur utilisées dans le Gestionnaire de conformité.

## <a name="user-privacy-settings"></a>Paramètres de confidentialité de l’utilisateur

Certaines réglementations exigent que les organisations soient en mesure de supprimer les données de l’historique d’un utilisateur. Le Gestionnaire de conformité propose les fonctions **Paramètres de confidentialité de l’utilisateur**, qui permettent aux administrateurs d’effectuer les actions suivantes :
  
- [Rechercher un utilisateur](#search-for-a-user)
- [Exporter le rapport de l’historique des données d’un compte](#export-a-report-of-account-data-history)
- [Supprimer l’historique des données d’un utilisateur](#delete-user-data-history)
  
## <a name="search-for-a-user"></a>Rechercher un utilisateur

Pour rechercher un compte d’utilisateur :
  
1. Entrez l’alias de l’adresse e-mail de l’utilisateur (informations à gauche du symbole @), puis choisissez le nom de domaine à partir de la liste des suffixes de domaine à droite. Pour les organisations ayant plusieurs domaines inscrits, revérifiez le suffixe du nom de domaine pour éviter toute erreur.

2. Une fois que le nom d’utilisateur est correctement entré, sélectionnez **Rechercher**.

3. Pour les comptes d’utilisateur non renvoyés, la page affiche **Utilisateur introuvable**. Vérifiez l’adresse e-mail de l’utilisateur, puis apportez les corrections nécessaires le cas échéant. Pour réessayer, sélectionnez **Rechercher**.

4. Pour le compte d’utilisateur retourné, le texte du bouton n’affichera plus **Rechercher** mais **Effacer**. Ceci indique que le compte d’utilisateur renvoyé peut utiliser les autres fonctions qui seront affichées ci-dessous, et que l’exécution de ces fonctions sera rattachée à ce compte d’utilisateur.

5. Pour effacer les résultats de la recherche et rechercher un autre utilisateur, sélectionnez **Effacer**.

## <a name="export-a-report-of-account-data-history"></a>Exporter le rapport de l’historique des données d’un compte

Pour chaque compte d’utilisateur identifié, vous pouvez générer un rapport sur les dépendances liées au compte. Ces informations vous permettent de réaffecter des éléments d’action en cours ou de garantir l’accès à des preuves chargées.
  
 Pour générer et exporter un rapport :
  
1. Sélectionnez **Exporter** pour générer et télécharger un rapport des éléments d’action d’un contrôle du Gestionnaire de conformité actuellement affectés au compte d’utilisateur retourné, et la liste des documents chargés par cet utilisateur. S’il n’y a aucune action affectée ni aucun document téléchargé, un message d’erreur indiquera « Aucune donnée liée à cet utilisateur ». Vous pouvez spécifier plusieurs valeurs séparées par des virgules.

2. Le rapport est téléchargé en arrière-plan de la fenêtre active du navigateur. Si aucune fenêtre contextuelle de téléchargement n’apparaît, vérifiez l’historique de téléchargement de votre navigateur.

3. Ouvrez le document pour consulter les données du rapport.

> [!IMPORTANT]
> Les données du rapport ne sont pas une liste historique qui consigne et affiche les changements d’état de l’historique d’affectation des éléments d’action. Le rapport généré est une capture instantanée des éléments d’action du contrôle affectés pendant l’exécution du rapport (horodateur indiqué dans le rapport). Par exemple, toute réaffectation des éléments d’action génère une autre capture instantanée des données du rapport si ce rapport est généré une nouvelle fois pour le même utilisateur.
  
## <a name="delete-user-data-history"></a>Supprimer l’historique des données d’un utilisateur

Cette action définit tous les éléments affectés d’action de contrôle sur « non affecté » à l’utilisateur renvoyé. Elle définit la valeur **chargé par** sur « utilisateur supprimé » pour tous les documents chargés par l’utilisateur renvoyé.
  
Pour supprimer un élément d’action du compte d’utilisateur et l’historique de chargement des documents :
  
1. Sélectionnez **Supprimer**.

    Une boîte de dialogue de confirmation apparaît, indiquant : *Cette action supprime tous les éléments d’action du contrôle affectés et l’historique de chargement des documents pour l’utilisateur sélectionné. Cette action est définitive. Voulez-vous vraiment continuer ?* »

2. Pour continuer, sélectionnez **OK**. Sinon, sélectionnez **Annuler**.
