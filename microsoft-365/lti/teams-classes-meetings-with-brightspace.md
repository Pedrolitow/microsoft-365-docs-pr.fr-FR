---
title: Intégrer des applications LTI de classes et de réunions Microsoft Teams à Desire2Learn Brightspace LMS
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
ms.collection:
- M365-modern-desktop
- m365initiative-edu
ms.localizationpriority: medium
description: Créez et gérez des classes et des réunions Teams avec Microsoft Learning Tools Interoperability (LTI) pour desire2Learn (D2L) Brightspace LMS.
ms.openlocfilehash: c3d551fcdc866c08437564addb1cd3cb9b144a75
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66950814"
---
# <a name="integrate-microsoft-teams-classes-and-meetings-lti-apps-within-desire2learn-brightspace-lms"></a>Intégrer des applications LTI de classes et de réunions Microsoft Teams dans Desire2Learn Brightspace LMS

Ce guide fournit les étapes de l’administrateur informatique pour l’inscription à la fois des classes Teams et des applications LTI réunions Teams pour le LMS Brightspace Desire2Learn (D2L).

Pour plus d’informations sur la gestion de toutes les applications LTI pour n’importe quel LMS, consultez [Gérer la passerelle Microsoft LMS pour n’importe quel LMS](manage-microsoft-one-lti.md).

Les étapes de base pour intégrer les applications LTI Teams et Brightspace sont les suivantes :

1. [Prérequis avant l’intégration](#prerequisites-before-integration).
1. [Inscrivez Microsoft LTI pour une utilisation dans Brightspace](#register-microsoft-teams-lti-for-use-in-brightspace).
1. [Déployez les applications Microsoft LTI sur Brightspace](#deploy-the-microsoft-lti-apps-to-brightspace).
1. [Ajoutez des liens d’application LTI Teams à l’espace Brightspace des enseignants](#add-teams-lti-app-links-to-educators-brightspace).

## <a name="prerequisites-before-integration"></a>Prérequis avant l’intégration

Pour que l’intégration entre D2L Brightspace et Teams fonctionne correctement, Brightspace et Teams doivent être configurés pour communiquer entre eux.

1. Pour que les classes Teams fonctionnent, **brightspace Course Connector** doit être installé et configuré correctement. Suivez [ces étapes pour installer le connecteur sur votre compte Brightspace](https://community.brightspace.com/s/article/Getting-started-with-Brightspace-Course-Connector-for-Microsoft-Teams).

   > [!NOTE]
   > Sélectionnez **l’équipe de classes** pour le **type d’intégration** lors de la configuration du connecteur pour garantir la compatibilité avec les outils LTI Teams.

2. Les réunions Teams fonctionnent sans le connecteur de cours. Toutefois, certaines fonctionnalités telles que **Ajouter une classe entière** ne seront pas disponibles. Nous vous recommandons d’installer **Brightspace Course Connector** pour l’application Teams Meetings LTI.

## <a name="register-microsoft-teams-lti-for-use-in-brightspace"></a>Inscrire Microsoft Teams LTI pour une utilisation dans Brightspace

1. Visitez la [passerelle Microsoft LMS](https://lti.microsoft.com/) et **sélectionnez le bouton Accéder au portail d’inscription** .

2. Connectez-vous avec un *compte d’administrateur Microsoft 365*.

3. Une fois connecté, **sélectionnez Ajouter une nouvelle inscription**.

4. Sélectionnez **LTI réunions Teams** ou **LTI des classes Teams** à inscrire, puis sélectionnez **Suivant**.

5. Entrez un nom **d’inscription** facilement identifiable et sélectionnez **D2L Brightspace** comme plateforme LMS. Sélectionnez **Suivant**.

6. Vous recevrez la liste des clés qui doivent être ajoutées à votre site Brightspace LMS.

7. Ouvrez le site Brightspace dans un autre onglet. Ne fermez pas l’onglet Passerelle Microsoft LMS.

8. Sur le site Brightspace, accédez à **Administration** >  **Manage Extensibility**, puis sélectionnez **LTI Advantage**, puis **Register Tool**.

9. Sélectionnez **Inscription Standard** et copiez les clés des **clés Microsoft LTI** vers les entrées d’outil correspondantes.
    1. La clé **d’URL du lien cible** de Microsoft entre dans le champ **URI de liaison cible** de Brightspace.
    1. La clé **d’URL de connexion Open ID** de Microsoft entre dans le champ URL de connexion **OpenID Connect** de Brightspace.
    1. La clé **URL de redirection** de Microsoft entre dans le champ **URL de redirection** de Brightspace.

10. Dans le champ **Domaine** , entrez `https://teams.microsoft.com`.

11. Sélectionnez le bouton **Inscrire**.

12. Un modal affiche les détails de l’inscription Brightspace. Ces valeurs doivent être ajoutées sur la passerelle Microsoft LMS.

13. Sous l’onglet **passerelle Microsoft LMS** , sélectionnez **les clés d’inscription fournies par LMS**.

14. Copiez et collez les valeurs des détails de configuration de Brightspace dans l’étape des **clés d’inscription fournies par LMS de** Microsoft.

    Collez les valeurs comme suit :

    | Sur Brightspace                         | Sur le portail d’inscription Microsoft LTI |
    | -------------------------------------- | ------------------------------------ |
    | Émetteur                                 | URL de l’ID de l’émetteur                        |
    | ID du client                              | ID du client                            |
    | URL du jeu de clés Brightspace                 | URL du jeu de clés                           |
    | Point de terminaison d’authentification OpenID Connect | URL d’authentification de la plateforme          |

    Sélectionnez **Suivant**.

15. Passez en revue la page **Révision et ajoutez** . En l’absence d’erreurs, **sélectionnez Enregistrer et quitter**. Vous devriez voir un message indiquant que l’inscription a réussi.

Vous avez terminé l’inscription des classes Teams ou de l’application LTI Réunions Teams.

Si vous souhaitez ajouter l’autre application également, répétez les étapes ci-dessus, en sélectionnant l’autre application LTI Teams à l’étape 4.

## <a name="deploy-the-microsoft-lti-apps-to-brightspace"></a>Déployer les applications Microsoft LTI sur Brightspace

Après avoir inscrit vos applications Microsoft LTI, vous devez déployer les applications sur votre site Brightspace.

Voici la procédure pour créer un déploiement :

1. Sur le site Brightspace, sélectionnez l’outil que vous avez créé.
2. Entrez un nom de déploiement.
3. Sélectionnez tous les paramètres de sécurité à l’exception **de Classlist** et **Anonymous**.
4. Ne définissez pas les paramètres de configuration.
5. Sélectionnez **Créer un déploiement**.

Choisissez les **unités d’organisation** que vous souhaitez utiliser la nouvelle application LTI. Sélectionnez **l’organisation racine** ou sélectionnez des enfants d’unité d’organisation individuels.

## <a name="add-teams-lti-app-links-to-educators-brightspace"></a>Ajouter des liens d’application LTI Teams à Brightspace des enseignants

Après avoir créé un déploiement, vous allez créer un lien. Ce lien ajoute l’application Microsoft LTI à l’expérience Brightspace des enseignants.

1. Sur le site Brightspace, sélectionnez le déploiement que vous avez créé.
2. Faites défiler vers le bas et sélectionnez **Afficher les liens**.
3. Sélectionnez **Nouveau lien**.
4. Renseignez les informations requises :
    1. Collez **l’URL de redirection** de la *passerelle Microsoft LMS* dans le champ **URL** . Cette URL est accessible en affichant l’inscription sur la passerelle.
    1. Définissez le type sur **Lancement de base**.
5. Sélectionnez **Enregistrer et fermer**.

L’enseignant peut maintenant ajouter l’application Microsoft LTI en la sélectionnant dans la liste déroulante **Contenu existant** brightspace.
