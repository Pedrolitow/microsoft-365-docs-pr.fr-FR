---
title: Créer et gérer des rôles pour le contrôle d’accès basé sur un rôle
description: Créer des rôles et définir les autorisations attribuées au rôle dans le cadre de l’implémentation du contrôle d’accès basé sur un rôle dans le Centre de sécurité Microsoft Defender
keywords: rôles utilisateur, rôles, accès rbac
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 932fd6ecd7dca66f4cb587b226474109c788c341
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51065950"
---
# <a name="create-and-manage-roles-for-role-based-access-control"></a>Créer et gérer des rôles pour le contrôle d’accès basé sur un rôle

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-roles-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="create-roles-and-assign-the-role-to-an-azure-active-directory-group"></a>Créer des rôles et attribuer le rôle à un groupe Azure Active Directory

Les étapes suivantes vous guident sur la création de rôles dans le Centre de sécurité Microsoft Defender. Il part du principe que vous avez déjà créé des groupes d’utilisateurs Azure Active Directory.

1. Connectez-vous au Centre de sécurité [Microsoft Defender à](https://securitycenter.windows.com/) l’aide d’un compte attribué par un administrateur de sécurité ou un rôle d’administrateur général.

2. Dans le volet de navigation, sélectionnez **Paramètres > rôles.**

3. Sélectionnez **Ajouter un élément.**

4. Entrez le nom de rôle, la description et les autorisations que vous souhaitez attribuer au rôle.

5. Sélectionnez **Suivant** pour attribuer le rôle à un groupe de sécurité Azure AD.

6. Utilisez le filtre pour sélectionner le groupe Azure AD à ajouter à ce rôle.

7. **Enregistrez et fermez.**

8. Appliquez les paramètres de configuration.

> [!IMPORTANT]
> Après avoir créé des rôles, vous devez créer un groupe d’appareils et fournir l’accès au groupe d’appareils en l’attribuant à un rôle que vous venons de créer.

### <a name="permission-options"></a>Options d’autorisation

- **Afficher les données**
    - **Opérations de sécurité** : afficher toutes les données des opérations de sécurité dans le portail
    - **Gestion des menaces et des vulnérabilités** : afficher les données de gestion des menaces et des vulnérabilités dans le portail

- **Actions de correction actives**
    - **Opérations de sécurité** : prendre des mesures de réponse, approuver ou ignorer les actions de correction en attente, gérer les listes autorisées/bloquées pour l’automatisation et les indicateurs
    - **Gestion des menaces et des vulnérabilités : gestion des exceptions** : créer des exceptions et gérer les exceptions actives
    - **Gestion des menaces et des vulnérabilités : gestion** des corrections : soumettre de nouvelles demandes de correction, créer des tickets et gérer les activités de correction existantes

- **Examen des alertes** : gérer les alertes, lancer des enquêtes automatisées, exécuter des analyses, collecter des packages d’enquête, gérer les balises d’appareil et télécharger uniquement les fichiers exécutables portables (PE) 

- **Gérer les paramètres** système du portail : configurer les paramètres de stockage, les paramètres SIEM et les paramètres de l’API Intel contre les menaces (s’applique globalement), les paramètres avancés, les téléchargements de fichiers automatisés, les rôles et les groupes d’appareils

    > [!NOTE]
    > Ce paramètre est uniquement disponible dans le rôle d’administrateur Microsoft Defender pour point de terminaison (par défaut).

- **Gérer les paramètres** de sécurité dans le Centre de sécurité : configurer les paramètres de suppression des alertes, gérer les exclusions de dossiers pour l’automatisation, les appareils intégrés et hors-carte, et gérer les notifications par courrier électronique, gérer le laboratoire d’évaluation

- **Fonctionnalités de réponse en direct**
    - **Commandes de** base :
        - Démarrer une session de réponse en direct
        - Exécuter des commandes de réponse en direct en lecture seule sur un appareil distant (à l’exception de la copie et de l’exécution de fichiers)
    - **Commandes** avancées :
        - Télécharger un fichier à partir de l’appareil distant via une réponse en direct
        - Télécharger des fichiers PE et non PE à partir de la page de fichiers
        - Télécharger un fichier sur l’appareil distant
        - Afficher un script à partir de la bibliothèque de fichiers
        - Exécuter un script sur l’appareil distant à partir de la bibliothèque de fichiers

Pour plus d’informations sur les commandes disponibles, voir Examiner les appareils à [l’aide de la réponse Live.](live-response.md)
  
## <a name="edit-roles"></a>Modifier des rôles

1. Connectez-vous au [Centre de sécurité Microsoft Defender à](https://securitycenter.windows.com/) l’aide d’un compte attribué par un administrateur de sécurité ou un rôle d’administrateur général.

2. Dans le volet de navigation, sélectionnez **Paramètres > rôles.**

3. Sélectionnez le rôle que vous souhaitez modifier.

4. Cliquez sur **Modifier**.

5. Modifiez les détails ou les groupes affectés au rôle. 

6. Cliquez **sur Enregistrer et fermer.**

## <a name="delete-roles"></a>Supprimer des rôles

1. Connectez-vous au [Centre de sécurité Microsoft Defender à](https://securitycenter.windows.com/) l’aide d’un compte attribué par un administrateur de sécurité ou un rôle d’administrateur général.

2. Dans le volet de navigation, sélectionnez **Paramètres > rôles.**

3. Sélectionnez le rôle que vous souhaitez supprimer.

4. Cliquez sur le bouton de la drop-down et **sélectionnez Supprimer le rôle**.

## <a name="related-topic"></a>Rubrique connexe

- [Autorisations utilisateur de base pour accéder au portail](basic-permissions.md)
- [Créer et gérer des groupes d’appareils](machine-groups.md)
