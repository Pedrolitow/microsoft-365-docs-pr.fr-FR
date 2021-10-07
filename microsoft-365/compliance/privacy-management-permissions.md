---
title: Définir des autorisations utilisateur et attribuer des rôles dans la gestion de la confidentialité (aperçu)
f1.keywords:
- CSH
ms.author: v-jgriffee
author: jmgriffee
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- M365-privacy-management
search.appverid:
- MOE150
- MET150
description: Découvrez comment configurer des autorisations de gestion de la confidentialité et attribuer des utilisateurs à des groupes de rôles.
ms.openlocfilehash: b1db7a9fd0bef1429172fe9afef262be4808c164
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60206012"
---
# <a name="set-user-permissions-and-assign-roles-in-privacy-management-preview"></a>Définir des autorisations utilisateur et attribuer des rôles dans la gestion de la confidentialité (aperçu)

Pour accorder aux membres de votre organisation les autorisations d’utiliser la gestion de la confidentialité, affectez-les aux groupes de rôles appropriés dans le Centre de conformité Microsoft 365. Notez que les rôles spécifiques à la gestion de la confidentialité n’apparaissent pas dans Azure Active Directory.

## <a name="sign-in-and-set-permissions"></a>Se connectez et définissez des autorisations

1. Go to the [Centre de conformité Microsoft 365](https://compliance.microsoft.com/) and select **Permissions** in the left navigation.  
2. Sous la dropdown **du Centre de** conformité, sélectionnez **Rôles.** La liste complète des groupes de rôles s’affiche.
3. Recherchez le groupe de rôles auquel vous souhaitez ajouter un ou plusieurs utilisateurs, puis cochez la case à gauche du nom du groupe. Voir ci-dessous pour obtenir la liste des rôles de gestion de la confidentialité.  
4. Dans le volet volant de ce groupe, sélectionnez **Modifier** sous **l’en-tête Membres.**  
5. Sélectionnez **Choisir les membres.** Une autre fenêtre volante s’affiche.
6. Sélectionnez **+ Ajouter** pour choisir un ou plusieurs utilisateurs à ajouter au groupe.  
7. Cochez la case en regard des noms que vous souhaitez ajouter, puis sélectionnez le bouton **Ajouter** en bas.  
8. Lorsque vous avez terminé d’affecter des utilisateurs, sélectionnez **Terminé,** puis **Enregistrer,** puis **Fermer**.

## <a name="role-groups-and-roles"></a>Groupes de rôles et rôles

Les membres doivent être affectés à des groupes de rôles en fonction des tâches qu’ils doivent accomplir et du niveau d’accès approprié aux fichiers. Chaque groupe de rôles comprend un ou plusieurs rôles. Ces rôles peuvent concerner des tâches de gestion de la confidentialité spécifiques ou des fonctions clés qui sont activées ou restreintes pour les membres de ce groupe.  

Les groupes de rôles peuvent être personnalisés si nécessaire. Pour éviter toute perte accidentelle d’accès, nous vous recommandons de créer une copie du groupe de rôles existant que vous souhaitez personnaliser, d’attribuer un nom identifiable à la copie, d’apporter et de vérifier vos modifications au nouveau groupe et d’y affecter des personnes selon le cas.

## <a name="privacy-management-role-group"></a>Groupe de rôles Gestion de la confidentialité

Ce groupe contient tous les rôles d’autorisation de gestion de la confidentialité dans un seul groupe. Ce groupe de rôles peut être adapté aux organisations où la même personne peut effectuer toutes les tâches au sein de la solution de gestion de la confidentialité. L’appartenance à ce groupe de rôles octroie à ce compte un accès total à toutes les fonctionnalités de la solution de gestion de la confidentialité.

Les rôles sont les suivants :

- Gestion des cas  
- Visionneuse de contenu de classification des données  
- Visionneuse de listes de classification des données  
- Administrateur de la gestion de la confidentialité  
- Analyse de la gestion de la confidentialité  
- Examen de la gestion de la confidentialité  
- Contribution permanente à la gestion de la confidentialité  
- Contribution temporaire à la gestion de la confidentialité  
- Visionneuse de la gestion de la confidentialité  
- Administrateur des demandes de droits de l’objet  
- View-Only Case

## <a name="privacy-management-administrators-role-group"></a>Groupe de rôles Administrateurs de la gestion de la confidentialité

Les membres de ce groupe de rôles ont un large accès aux fonctions de gestion de la confidentialité, notamment la création, la lecture, la mise à jour et la suppression de stratégies de gestion de la confidentialité, les demandes des droits de l’objet, les autorisations de gestion de la confidentialité et les paramètres de gestion de la confidentialité.

Les rôles sont les suivants :

- Gestion des cas  
- Administrateur de la gestion de la confidentialité  
- View-Only Case

## <a name="privacy-management-analysts-role-group"></a>Groupe de rôles Analystes de la gestion de la confidentialité

Les membres de ce groupe de rôles agissent en tant qu’analystes de cas de gestion de la confidentialité. Ils peuvent examiner les correspondances de stratégie, afficher les métadonnées des fichiers et prendre des mesures correctives. Ce groupe ne peut pas accéder aux fichiers complets via l’Explorateur de contenu.

Les rôles sont les suivants :

- Gestion des cas  
- Visionneuse de listes de classification des données  
- Analyse de la gestion de la confidentialité  
- View-Only Case

### <a name="privacy-management-investigators-role-group"></a>Groupe de rôles Enquêteurs de la gestion de la confidentialité

Les membres de ce groupe agissent en tant qu’enquêteurs de données de gestion de la confidentialité. Ils peuvent examiner les correspondances de stratégie, afficher le contenu du fichier associé et prendre des mesures correctives. Ce groupe peut accéder aux fichiers via l’Explorateur de contenu.

Les rôles sont les suivants :

- Gestion des cas  
- Visionneuse de contenu de classification des données  
- Visionneuse de listes de classification des données  
- Examen de la gestion de la confidentialité  
- View-Only Case

## <a name="privacy-management-viewer-role-group"></a>Groupe de rôles Visionneuse de gestion de la confidentialité

Les membres de ce groupe peuvent afficher des informations analytiques dans la gestion de la confidentialité, telles que la vue d’ensemble, le profil de données et les rapports de demande d’objet.

Les rôles sont les suivants :

- Visionneuse de la gestion de la confidentialité

## <a name="subject-rights-request-administrators-role-group"></a>Groupe de rôles Administrateurs des demandes de droits de l’objet

Les membres de ce groupe ont un accès total pour administrer et créer des demandes de droits d’objet.

Les rôles sont les suivants :

- Administrateur des demandes de droits de l’objet

## <a name="privacy-management-contributors-role-group"></a>Groupe de rôles Contributeurs à la gestion de la confidentialité

Les membres de ce groupe ont un accès collaborateur aux demandes de droits de l’objet.  

Les rôles sont les suivants :

- Contribution temporaire à la gestion de la confidentialité  
- Contribution permanente à la gestion de la confidentialité
