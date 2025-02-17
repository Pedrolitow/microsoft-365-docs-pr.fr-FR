---
title: Gérer la passerelle Microsoft LMS pour n’importe quel LMS
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: microsoft-365-business
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
description: Découvrez comment effectuer des tâches clés de gestion de passerelle Microsoft LMS, notamment l’affichage, la suppression, la modification et la résolution des problèmes.
ms.openlocfilehash: ccf05bb497546bae153f2132e27440713661845b
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68187556"
---
# <a name="manage-microsoft-lms-gateway-for-any-lms"></a>Gérer la passerelle Microsoft LMS pour n’importe quel LMS

La passerelle Microsoft LMS s’intègre à plusieurs LMS, notamment Canvas, Blackboard, Moodle et Brightspace.

Dans cet article, les administrateurs informatiques trouveront des instructions sur les principales tâches de gestion de passerelle Microsoft LMS.

- [Afficher une inscription LTI](#view-an-lti-registration).
- [Supprimez une inscription LTI](#delete-an-lti-registration).
- [Modifiez une inscription LTI](#edit-an-lti-registration).
- [Résoudre les problèmes liés à la passerelle Microsoft LMS](#troubleshoot-issues-with-microsoft-lms-gateway).
- [Signaler des problèmes avec la passerelle Microsoft LMS](#report-problems-with-lti-registration-portal).

## <a name="view-an-lti-registration"></a>Afficher une inscription LTI

Si vous souhaitez afficher les détails d’une inscription LTI, suivez les étapes ci-dessous.

1. Visitez la [passerelle Microsoft LMS](https://lti.microsoft.com/).
2. Connectez-vous avec un compte d’administrateur Microsoft 365.
3. Dans la liste d’inscription, recherchez l’inscription LTI que vous souhaitez afficher.
4. Sélectionnez **l’icône d’œil** en regard de la liste.
5. Le panneau détails de l’inscription s’ouvre.

## <a name="delete-an-lti-registration"></a>Supprimer une inscription LTI

Si vous souhaitez supprimer une inscription LTI, suivez les étapes ci-dessous.

1. Visitez la [passerelle Microsoft LMS](https://lti.microsoft.com/).
2. Connectez-vous avec un compte d’administrateur Microsoft 365.
3. Dans la liste d’inscription, recherchez l’inscription LTI que vous souhaitez supprimer.
4. Sélectionnez **l’icône de corbeille** en regard de la liste.
5. Dans la boîte de dialogue de confirmation, **sélectionnez Supprimer** pour confirmer la suppression.
6. Un message de réussite s’affiche une fois supprimé.

## <a name="edit-an-lti-registration"></a>Modifier une inscription LTI

Actuellement, nous ne prenons pas en charge la modification d’une inscription LTI existante après son ajout.

Pour modifier une inscription LTI, vous devez :

1. [Supprimez l’inscription existante](#delete-an-lti-registration).
2. Ajoutez une nouvelle inscription.

## <a name="troubleshoot-issues-with-microsoft-lms-gateway"></a>Résoudre les problèmes liés à la passerelle Microsoft LMS

Si vous ou vos enseignants rencontrez des problèmes avec la passerelle Microsoft LMS, voici quelques actions que vous pouvez effectuer pour résoudre les problèmes.

### <a name="issues-while-launching-an-lti-app-from-the-lms"></a>Problèmes lors du lancement d’une application LTI à partir du LMS

Les enseignants peuvent rencontrer des problèmes lors du lancement d’une application Microsoft LTI dans leur LMS.

Si c’est le cas, voici quelques problèmes courants et comment les résoudre.

- **Les cookies sont introuvables**
  - Les cookies tiers doivent être autorisés pour **l’URL LMS** dans les paramètres du navigateur.
  - Ces cookies sont nécessaires pour terminer l’établissement de la liaison LTI 1.3 conformément aux spécifications IMS.
  - Pour savoir comment mettre à jour les paramètres de cookie de votre navigateur, consultez [Autoriser les cookies pour les URL LMS dans votre navigateur](browser-cookies.md).

- **Détails de l’inscription introuvables**
  - Ce problème se produit lorsque l’inscription de l’application LTI n’est pas terminée ou si l’inscription a été supprimée dans la passerelle Microsoft LMS.
  - L’administrateur informatique doit terminer l’inscription de l’application LTI.

- **Certains détails de LMS ne sont pas valides**
  - Ce problème se produit lorsque les détails envoyés par le LMS dans la demande de lancement de l’application ne sont pas alignés sur la spécification IMS LTI 1.3.
  - L’administrateur informatique devra contacter [l’équipe du support technique microsoft en cas](https://edusupport.microsoft.com/support?product_id=lti_apps&platform_id=web) de persistance du problème.

### <a name="issues-with-signing-in-to-the-microsoft-lms-gateway"></a>Problèmes de connexion à la passerelle Microsoft LMS

Lors de la connexion à la passerelle Microsoft LMS, vous pouvez rencontrer des problèmes d’accès à la page d’inscription ou de réception d’une erreur de connexion.

Voici quelques problèmes courants de connexion et comment les résoudre.

- **Erreur d’autorisation**
  - Si vous voyez le message d’erreur « Votre compte n’a pas l’autorisation d’accéder à cette page », procédez comme suit :
    - Le compte n’appartient pas à un locataire inscrit, ou
    - Le compte n’appartient pas à un enseignant ou à un administrateur.

  - Dans ces deux cas, vous verrez un bouton Se **déconnecter & changer de compte** .
    - Sélectionnez ce bouton ou sélectionnez le bouton **Se déconnecter** sous le menu profil utilisateur.
    - Connectez-vous avec un compte qui appartient au locataire, à un enseignant ou à un administrateur.

  - Si le locataire n’est pas inscrit, l’administrateur informatique doit l’inscrire avant d’essayer d’inscrire des intégrations LTI.

  - Si, après avoir essayé ces étapes, vous voyez toujours cette erreur, puis déconnectez-vous et reconnectez-vous.
    - Vous pouvez également effacer les cookies et le stockage local pour la passerelle Microsoft LMS et `https://login.microsoftonline.com/`.
    - Essayez de vous reconnecter.
    - Si le problème persiste, signalez le problème en sélectionnant le lien **Signaler un problème** en haut à droite.

- **Erreur d’authentification**
  - Si vous voyez le message d’erreur « Échec de l’authentification. Réessayez », la session de connexion a peut-être expiré.
    - Déconnectez-vous et reconnectez-vous.
    - Vous pouvez également effacer les cookies et le stockage local pour la passerelle Microsoft LMS et `https://login.microsoftonline.com/`.
    - Essayez de vous reconnecter.
    - Si le problème persiste, signalez le problème en sélectionnant le lien **Signaler un problème** en haut à droite.

- **Autres erreurs**
  - Pour toutes les autres erreurs, vous verrez le message d’erreur « Un problème s’est produit. Veuillez réessayer plus tard. »
    - Il peut s’agir d’une erreur de traitement interne.
    - Essayez de vous reconnecter après quelques heures.
      - Sélectionnez le bouton **Accéder à la page d’accueil** . Cette opération permet de revenir à la page d’accueil.
      - Sélectionnez le bouton **Accéder au portail d’inscription** pour revenir à la passerelle Microsoft LMS.

### <a name="report-problems-with-lti-registration-portal"></a>Signaler des problèmes avec le portail d’inscription LTI

Pour signaler des problèmes ou envoyer des commentaires pour le portail d’inscription LTI, suivez les étapes ci-dessous.

1. Dans le portail d’inscription LTI, sélectionnez **l’icône de point d’interrogation** dans l’en-tête de page.
2. Dans la liste déroulante, sélectionnez **Signaler un problème**.
3. La page support Microsoft Éducation s’ouvre. Connectez-vous avec vos informations d’identification Microsoft 365.
4. Remplissez le formulaire et envoyez-le.
