---
title: Utiliser Microsoft OneDrive LTI avec Blackboard
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: microsoft-365-business
ms.collection: m365initiative-edu
ms.localizationpriority: medium
description: Créez et classez des affectations, créez et organisez du contenu de cours, et collaborez sur des fichiers en temps réel avec la nouvelle interopérabilité des outils d’apprentissage Microsoft OneDrive pour Blackboard.
ms.openlocfilehash: d5a1b4f08b3507af176c7dd145520767ecdb752f
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68177633"
---
# <a name="use-microsoft-onedrive-lti-with-blackboard"></a>Utiliser Microsoft OneDrive LTI avec Blackboard

L’intégration de Microsoft OneDrive LTI à Blackboard est un processus en deux étapes. La première étape rend Microsoft OneDrive LTI disponible dans les cours Blackboard, et la deuxième étape active Microsoft OneDrive pour Blackboard.

> [!IMPORTANT]
> La personne qui effectue cette intégration doit être un administrateur de Blackboard et un administrateur du locataire Microsoft 365.

## <a name="recommended-browser-settings"></a>Paramètres de navigateur recommandés

- Les cookies doivent être autorisés pour Microsoft OneDrive.
- Les fenêtres contextuelles ne doivent pas être bloquées pour Microsoft OneDrive.

> [!NOTE]
>
> - Les cookies ne sont pas autorisés par défaut dans le mode incognito du navigateur Chrome et doivent être autorisés.
> - Microsoft OneDrive LTI fonctionne en mode privé dans le navigateur Microsoft Edge. Vérifiez que vous n’avez pas bloqué les cookies (qui sont autorisés par défaut).

## <a name="register-the-onedrive-lti-13-tool-in-blackboard"></a>Inscrire l’outil OneDrive LTI 1.3 dans Blackboard

1. Dans le panneau Administrateur de Blackboard, sélectionnez **Fournisseurs d’outils LTI**.
2. Sélectionnez **Inscrire l’outil LTI 1.3**.
3. Dans le champ ID client, tapez ou copiez-collez cet ID : ``78cd1b1c-ccbd-4318-9f90-22241f63b1f5``

   > [!NOTE]
   > L’ajout de cet ID client configure deux emplacements différents dans Blackboard : un qui permet d’accéder à l’outil à partir du marché du contenu, des livres et des outils, et l’éditeur de texte enrichi, et un autre qui permet d’accéder à l’outil à partir du menu Ajouter du contenu dans le cours en ligne pour les cours Ultra.

4. Sélectionnez **Envoyer**.
5. Passez en revue tous les paramètres préremplis dans la vue **État** de l’outil et assurez-vous que le bouton **Ronde État** de l’outil sélectionné est **Approuvé**.
6. Dans **Stratégies d’établissement**, sélectionnez le **rôle en cours** et cochez les cases **Nom** dans les champs utilisateur à envoyer. Tous les autres champs utilisateur sont facultatifs, mais il est recommandé de les laisser à la prochaine preuve de votre installation de OneDrive.
7. **Autoriser l’accès au service de niveau** et **Autoriser l’accès au service d’appartenance** sont également facultatifs pour l’instant, mais peuvent être nécessaires pour les futures mises à jour de l’outil LTI.
8. Copiez **l’ID de déploiement**. Vous en aurez besoin pour configurer l’outil Microsoft LTI.
9. Sélectionnez le bouton **Envoyer** pour terminer.

## <a name="configure-the-microsoft-lti-tool-to-work-with-blackboard"></a>Configurer l’outil Microsoft LTI pour qu’il fonctionne avec Blackboard

1. Connectez-vous au [portail d’inscription LTI Microsoft OneDrive](https://onedrivelti.microsoft.com/admin).
2. Sélectionnez le bouton **Administration Consentement** et acceptez les autorisations.

    > [!CAUTION]
    > Si cette étape n’est pas effectuée, l’étape suivante vous donnera une erreur, et vous ne pourrez pas effectuer cette étape pendant une heure une fois que vous aurez obtenu l’erreur.

3. Sélectionnez le bouton **Créer un locataire LTI** .
4. Dans la page Inscription LTI, choisissez **Tableau noir** dans la liste déroulante plateforme grand public LTI, puis sélectionnez le bouton **Suivant** .
5. Collez **l’ID de déploiement** que vous avez copié lors de l’inscription de l’outil dans Blackboard, puis sélectionnez **Suivant**.
6. Passez en revue et enregistrez vos modifications. Un message s’affiche lors de l’inscription réussie.
7. Vous pouvez également consulter les détails de votre inscription en sélectionnant le bouton **Afficher les locataires LTI** sur la page d’accueil.

Une fois ces étapes effectuées, vos instructeurs pourront ouvrir des documents à partir de OneDrive lorsqu’ils utiliseront le menu « plus » dans la page Contenu du cours.

## <a name="recommended-content"></a>Contenu recommandé

[Microsoft Integrations pour Blackboard](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft)

[Intégration des classes Microsoft Teams](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft_Classes)
