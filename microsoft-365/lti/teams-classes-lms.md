---
title: Utiliser Microsoft Teams classes avec tableau noir
ms.author: v-cichur
author: cichur
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
description: Intégrer Microsoft Teams classes dans votre système de gestion de l’apprentissage
ms.openlocfilehash: 287b9f1cadfdcf3adafdca91f4a351865bbcf3bc
ms.sourcegitcommit: 50908a93554290ff1157b58d0a868a33e012513c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52821270"
---
# <a name="use-microsoft-teams-classes-with-blackboard"></a>Utiliser Microsoft Teams classes avec tableau noir

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Microsoft Teams classes est une application d’interopérabilité des outils d’apprentissage (LTI) qui permet aux enseignants et aux étudiants de naviguer facilement entre leur système de gestion de l’apprentissage (LMS) et Teams. Les utilisateurs peuvent accéder à leurs équipes de cours associées à leur cours directement à partir de leur LMS.

## <a name="approve-the-app-in-the-microsoft-azure-tenant"></a>Approuver l’application dans le Microsoft Azure client

Les tâches suivantes sont effectuées par l’administrateur Microsoft Office 365 et l’administrateur Blackboard Learn Ultra.

Avant de gérer l’intégration dans Blackboard Learn Ultra, l’administrateur Microsoft Office 365 doit approuver le **Teams MSFT** pour l’application Learn Ultra Azure pour le client Microsoft Azure de l’établissement.

1. Recherchez votre ID de locataire Microsoft. Découvrez [comment trouver le client.](/azure/active-directory/fundamentals/active-directory-how-to-find-tenant)

2. Redirigez le point de terminaison de consentement de l’administrateur de la plateforme d’identités Microsoft en fonction de l’exemple suivant :

   `https://login.microsoftonline.com/{tenant}/adminconsent?client\_id=2d94989f-457a-47c1-a637-e75acdb11568`

   > [!NOTE]
   > Remplacez {tenant} par l’ID de client Microsoft de votre organisation.

## <a name="register-the-integration-apps"></a>Inscrire les applications d’intégration

En tant qu’administrateur Blackboard Learn Ultra, vous devez inscrire 2 applications d’intégration LTI 1.3 dans votre environnement de test :

- Intégration de la classe Blackboard Learn Teams prise en charge de la synchronisation des listes de classes

- Application LTI Microsoft Teams l’équipe de la classe

1. Notez les ID de client LTI suivants pour les deux applications :

    - Tableau noir - f1561daa-1b21-4693-ba90-6c55f1a0eb41

    - Microsoft - 027328b7-c2e3-4c9e-aaa1-07802dae6c89

2. Accédez au Panneau d’administration et, sous **Intégrations,** recherchez les fournisseurs d’outils LTI.

   ![Il s’agit de la boîte de dialogue Fournisseur d’outils LTI qui affiche la liste des fournisseurs](../media/lti-media/lti-tool-providers.png)

3. Sélectionnez **Inscrire LTI1.3/Outil Advantage.**

4. Entrez le premier des ID clients fournis (tableau noir ou Microsoft), puis sélectionnez **Envoyer.**

   ![l’outil d’inscription LTI avec un champ pour entrer l’ID client](../media/lti-media/register-tool.png)

5. Examinez les paramètres pré-remplis et assurez-vous que l’état de l’outil est marqué comme approuvé.

6. Faites défiler vers le bas, puis sélectionnez **Envoyer.**

7. Répétez les étapes précédentes pour inscrire la deuxième application LTI dans votre environnement.

## <a name="set-up-the-rest-application-and-cross-origin-resource-sharing"></a>Configurer l’application REST et le partage de ressources d’origine croisée

L’administrateur Blackboard Learn Ultra devra également configurer l’application REST et la configuration du partage de ressources d’origine croisée.

Complétez les procédures suivantes pour configurer l’application REST

1. Accédez aux outils d’administration Learn, puis sélectionnez **Intégrations d’API REST dans** la section **Intégrations.**

2. Sélectionnez **Créer des intégrations** et entrez le même ID d’application/client que celui que vous avez entré pour l’outil Blackboard Learn Class Teams Integration LTI.

3. Entrez l’utilisateur Learn (il peut s’y trouver à votre propre nom d’utilisateur d’administrateur Learn) ou **sélectionnez Parcourir** pour le localiser.

4. Sélectionnez **Oui** pour **l’accès des utilisateurs finux.**

5. Sélectionnez **Oui** **pour être autorisé à agir en tant qu’utilisateur**

6. Sélectionnez **Envoyer** une fois terminé.

## <a name="set-up-cross-origin-resource-sharing"></a>Configurer le partage de ressources d’origine croisée

1. Accédez aux outils d’administration Learn et sélectionnez **Partage** de ressources d’origine croisée dans la section **Intégrations.**

2. Sélectionnez **Créer une configuration.**

3. Entrez `https://bb-ms-teams-ultra-ext.api.blackboard.com` l’origine.

4. Ajoutez le mot **Autorisation** dans les **en-têtes autorisés.**

5. Définir **Disponible** sur **Oui**.

6. Sélectionnez **Envoyer** une fois terminé.

## <a name="enable-class-teams-in-blackboard-learn"></a>Activer l’Teams classe dans Blackboard Learn

Une fois que vous avez activé les outils LTI, l’étape suivante consiste à configurer l’intégration de microsoft Class Teams à partir de votre propre client Microsoft Office 365 client. Pour ce faire, vous pouvez suivre ces étapes en tant qu’administrateur Blackboard Learn Ultra.

1. In **Learn Admin** Tools and  >  **Utilities,** select Microsoft Teams Integration **Admin**.

   ![boîte de dialogue outils et utilitaires avec une liste des outils disponibles](../media/lti-media/tools-utilities.png)

2. Activez la case à cocher **Microsoft Teams**.

3. Entrez votre ID de client comme indiqué dans la section sous Microsoft O365 Admin

 > [!NOTE]
 > Vous ne pourrez pas enregistrer les paramètres tant que l’application n’aura pas été approuvée par l’administrateur O365. Voir [Approuver l’application dans Microsoft Azure client.](#approve-the-app-in-the-microsoft-azure-tenant)

4. Lorsque l’administrateur général O365 a approuvé le tableau noir Teams application dans votre client Microsoft, sélectionnez **Envoyer.**
