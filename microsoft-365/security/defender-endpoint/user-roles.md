---
title: Créer et gérer des rôles pour le contrôle d’accès en fonction du rôle
description: Créez des rôles et définissez les autorisations affectées au rôle dans le cadre de l’implémentation du contrôle d’accès en fonction du rôle dans le Microsoft 365 Defender
keywords: rôles d’utilisateur, rôles, accès rbac
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 8d86c55dcab74ea3901b4e1c55882664d9e7dd83
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67586597"
---
# <a name="create-and-manage-roles-for-role-based-access-control"></a>Créer et gérer des rôles pour le contrôle d’accès en fonction du rôle

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-roles-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="create-roles-and-assign-the-role-to-an-azure-active-directory-group"></a>Créer des rôles et attribuer le rôle à un groupe Azure Active Directory

Les étapes suivantes vous guident dans la création de rôles dans Microsoft 365 Defender. Il suppose que vous avez déjà créé des groupes d’utilisateurs Azure Active Directory.

1. Connectez-vous à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> à l’aide d’un compte avec un rôle d’administrateur de sécurité ou de Administrateur général attribué.

2. Dans le volet de navigation, sélectionnez **Paramètres des rôles** \> **de points de terminaison** \> (sous **Autorisations**).

3. Sélectionnez **Ajouter un élément**.

4. Entrez le nom du rôle, la description et les autorisations que vous souhaitez attribuer au rôle.

5. Sélectionnez **Suivant** pour attribuer le rôle à un groupe de sécurité Azure AD.

6. Utilisez le filtre pour sélectionner le groupe Azure AD auquel vous souhaitez ajouter ce rôle.

7. **Enregistrez et fermez**.

8. Appliquez les paramètres de configuration.

> [!IMPORTANT]
> Après avoir créé des rôles, vous devez créer un groupe d’appareils et fournir l’accès au groupe d’appareils en l’affectant à un rôle que vous venez de créer.

### <a name="permission-options"></a>Options d’autorisation

- **Afficher les données**
  - **Opérations de sécurité** - Afficher toutes les données des opérations de sécurité dans le portail
  - **Gestion des menaces et des vulnérabilités** - Afficher les données de gestion des vulnérabilités Defender dans le portail

- **Actions de correction actives**
  - **Opérations de sécurité** : effectuer des actions de réponse, approuver ou ignorer les actions de correction en attente, gérer les listes autorisées/bloquées pour l’automatisation et les indicateurs
  - **Gestion des menaces et des vulnérabilités - Gestion des** exceptions - Créer de nouvelles exceptions et gérer les exceptions actives
  - **Gestion des menaces et des vulnérabilités - Gestion des corrections** - Envoyer de nouvelles demandes de correction, créer des tickets et gérer les activités de correction existantes

- **Investigation des alertes** - Gérer les alertes, lancer des investigations automatisées, exécuter des analyses, collecter des packages d’investigation, gérer les balises d’appareil et télécharger uniquement les fichiers exécutables portables (PE)

- **Gérer les paramètres système du portail** : configurer les paramètres de stockage, les paramètres d’API SIEM et intel de menace (s’applique globalement), les paramètres avancés, les chargements de fichiers automatisés, les rôles et les groupes d’appareils

    > [!NOTE]
    > Ce paramètre est disponible uniquement dans le rôle d’administrateur Microsoft Defender pour point de terminaison (par défaut).

- **Gérer les paramètres de sécurité dans Security Center** - Configurer les paramètres de suppression des alertes, gérer les exclusions de dossiers pour l’automatisation, intégrer et déconnecter des appareils, gérer les notifications par e-mail et gérer le laboratoire d’évaluation

- **Fonctionnalités de réponse dynamique**
  - **Commandes de base** :
    - Démarrer une session de réponse dynamique
    - Exécuter des commandes de réponse dynamique en lecture seule sur un appareil distant (à l’exception de la copie et de l’exécution de fichiers)
    - Télécharger un fichier à partir de l’appareil distant via une réponse en direct
  - **Commandes avancées** :
    - Télécharger des fichiers PE et non-PE à partir de la page de fichiers
    - Charger un fichier sur l’appareil distant
    - Afficher un script à partir de la bibliothèque de fichiers
    - Exécuter un script sur l’appareil distant à partir de la bibliothèque de fichiers

Pour plus d’informations sur les commandes disponibles, consultez [Examiner les appareils à l’aide de la réponse en direct](live-response.md).

## <a name="edit-roles"></a>Modifier les rôles

1. Connectez-vous à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender à l’aide d’un</a> compte avec l’administrateur de sécurité ou le rôle Administrateur général attribué.

2. Dans le volet de navigation, sélectionnez **Paramètres des rôles** \> **de points de terminaison** \> (sous **Autorisations**).

3. Sélectionnez le rôle que vous souhaitez modifier.

4. Cliquez sur **Modifier**.

5. Modifiez les détails ou les groupes affectés au rôle.

6. Cliquez sur **Enregistrer et fermer**.

## <a name="delete-roles"></a>Supprimer des rôles

1. Connectez-vous à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender à l’aide d’un</a> compte avec l’administrateur de sécurité ou le rôle Administrateur général attribué.

2. Dans le volet de navigation, sélectionnez **Paramètres des rôles** \> **de points de terminaison** \> (sous **Autorisations**).

3. Sélectionnez le rôle que vous souhaitez supprimer.

4. Cliquez sur le bouton déroulant et **sélectionnez Supprimer le rôle**.

## <a name="related-topic"></a>Rubrique connexe

- [Autorisations de base de l’utilisateur pour accéder au portail](basic-permissions.md)
- [Créer et gérer des groupes d’appareils](machine-groups.md)
