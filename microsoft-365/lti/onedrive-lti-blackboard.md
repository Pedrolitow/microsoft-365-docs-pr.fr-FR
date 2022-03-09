---
title: Intégrer Microsoft OneDrive LTI au Tableau noir
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Créez et classez des devoirs, créez et organisez du contenu de cours et collaborez sur des fichiers en temps réel avec le nouveau tableau noir Microsoft OneDrive Learning Tools Interoperability.
ms.openlocfilehash: 94e77181244bbf02115bd706e86751a9382b906b
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63406540"
---
# <a name="integrate-microsoft-onedrive-lti-with-blackboard"></a>Intégrer Microsoft OneDrive LTI au Tableau noir

L’intégration Microsoft OneDrive LTI au Tableau noir est un processus en deux étapes. La première étape rend l’Microsoft OneDrive LTI disponible dans les cours de tableau noir, et la deuxième étape Microsoft OneDrive le tableau noir.

> [!IMPORTANT]
> La personne qui effectue cette intégration doit être administrateur du Tableau noir et administrateur du client Microsoft 365 client.

## <a name="recommended-browser-settings"></a>Paramètres de navigateur recommandés

- Les cookies doivent être autorisés pour Microsoft OneDrive.
- Les fenêtres pop-up ne doivent pas être bloquées pour Microsoft OneDrive.

> [!NOTE]
>
> - Les cookies ne sont pas autorisés par défaut dans le navigateur Chrome en modecognito et doivent être autorisés.
> - Microsoft OneDrive LTI fonctionne en mode privé dans Microsoft Edge navigateur. Assurez-vous que vous n’avez pas bloqué les cookies (qui sont autorisés par défaut).

## <a name="register-the-onedrive-lti-13-tool-in-blackboard"></a>Inscrire l OneDrive l’outil LTI 1.3 dans Le Tableau noir

1. Dans le panneau Administrateur du Tableau noir,  **sélectionnez Fournisseurs d’outils selectLTI**.
2.  **SelectRegister LTI 1.3 Tool**.
3. Dans le champ ID client, tapez ou copiez-collez cet ID : ``78cd1b1c-ccbd-4318-9f90-22241f63b1f5``

  > [!NOTE]
  > L’ajout de cet ID client configure deux emplacements différents dans le Tableau noir : un qui permet d’accéder à l’outil à partir du marché du contenu, des livres et des outils, et l’éditeur de texte enrichi, et un autre qui permet d’accéder à l’outil à partir du menu Ajouter du contenu dans le cours en ligne pour les cours Ultra.

4. Sélectionnez **Envoyer**.
5. Examinez tous les paramètres pré-remplis dans l’outil  **Statusview**  Et assurez-vous que le bouton round État de l’outil sélectionné  **estapprové**.
6. Stratégies In  **Contrôle**, sélectionnez **le rôle dans le cours** et **les case à** cocher Nom dans les champs utilisateur à envoyer. Tous les autres champs utilisateur sont facultatifs, mais il est recommandé de les laisser sur la preuve ultérieure de OneDrive’installation.
7. **Autoriser l’accès au service de qualité**   **l’accès au service d’appartenance** est également facultatif pour le moment, mais peut être nécessaire pour les futures mises à jour de l’outil LTI.
8. Copiez **l’ID de déploiement**. Vous en aurez besoin pour configurer l’outil Microsoft LTI.
9. Sélectionnez **le bouton** Envoyer pour terminer.

## <a name="configure-the-microsoft-lti-tool-to-work-with-blackboard"></a>Configurer l’outil Microsoft LTI pour qu’il fonctionne avec le Tableau noir

1. Connectez-vous [Microsoft OneDrive portail d’inscription LTI](https://onedrivelti.microsoft.com/admin).
2. Sélectionnez le **bouton Consentement de l’administrateur** et acceptez les autorisations.

> [!CAUTION]
> Si cette étape n’est pas effectuée, l’étape suivante vous donnera une erreur et vous ne pourrez pas effectuer cette étape pendant une heure une fois que vous aurez obtenu l’erreur.

3. Sélectionnez **le bouton Créer un client LTI** .
4. Dans la page Inscription LTI, sélectionnez **Tableau noir** dans la liste rouge de la plateforme consommateur LTI, puis sélectionnez **le bouton** Suivant.
5. Collez **l’ID de déploiement** que vous avez copié lors de l’inscription de l’outil dans tableau noir, puis sélectionnez **Suivant**.
6. Examinez et enregistrez vos modifications. Un message s’affiche lorsque l’inscription réussit.
7. Vous pouvez également consulter les détails de votre inscription en sélectionnant le bouton Afficher les locataires **LTI** sur la page d’accueil.

Une fois ces étapes terminées, vos instructeurs pourront ouvrir des documents à partir de OneDrive lorsqu’ils utiliseront le menu « plus » dans la page Contenu du cours.

## <a name="recommended-content"></a>Contenu recommandé

[Intégrations Microsoft pour le tableau noir](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft)

[intégration Microsoft Teams classes](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft_Classes)
