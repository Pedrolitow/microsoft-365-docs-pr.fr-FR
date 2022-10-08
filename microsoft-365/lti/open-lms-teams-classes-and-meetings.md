---
title: Intégrer des classes et des réunions Microsoft Teams à Open LMS
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
description: Créez et gérez des classes et des réunions Teams avec l’interopérabilité des outils d’apprentissage Microsoft pour Open LMS.
ms.openlocfilehash: 034aa9924798b7e284665713e6d8fe2809c1e70f
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68203813"
---
# <a name="integrate-microsoft-teams-classes-and-meetings-within-open-lms"></a>Intégrer des classes et des réunions Microsoft Teams dans Open LMS

Ce guide fournit les étapes de l’administrateur informatique pour l’inscription des classes Teams et des applications LTI réunions Teams sur Open LMS.

Pour plus d’informations sur la gestion de toutes les applications LTI pour n’importe quel LMS, consultez [Gérer la passerelle Microsoft LMS pour n’importe quel LMS](manage-microsoft-one-lti.md).

## <a name="prerequisites-before-set-up"></a>Prérequis avant la configuration

Pour que l’intégration entre Open LMS et Teams fonctionne correctement, Open LMS et Teams doivent être configurés pour communiquer entre eux.

Suivez les [instructions d’installation et de configuration des plug-ins Moodle LMS](open-lms-plugin-configuration.md).

## <a name="register-microsoft-teams-lti-for-use-in-open-lms"></a>Inscrire Microsoft Teams LTI pour une utilisation dans Open LMS

> [!IMPORTANT]
> La personne qui effectue cette intégration doit être un administrateur Open LMS et un administrateur client Microsoft 365.

1. Visitez [la passerelle Microsoft LMS](https://lti.microsoft.com/) et **sélectionnez le bouton Accéder au portail d’inscription** .

2. Connectez-vous avec un compte d’administrateur Microsoft 365.

3. Une fois connecté, **sélectionnez Ajouter une nouvelle inscription**.

4. Sélectionnez **LTI réunions Teams** ou **LTI des classes Teams** à inscrire, puis sélectionnez **Suivant**.

5. Entrez un nom **d’inscription** facilement identifiable et sélectionnez **Ouvrir LMS** comme plateforme LMS. Sélectionnez **Suivant**.

6. Vous recevrez une liste de clés qui doivent être ajoutées à votre site Open LMS.

7. Ouvrez Ouvrir LMS dans un autre onglet. Ne fermez pas l’onglet Passerelle Microsoft LMS.

8. Dans Open LMS, accédez aux **modules Activité des plug-ins** >  **d’administration** >  de site Outils **externes** >  > **Gérer les outils**.

9. Dans la page **Gérer les outils** , sélectionnez **configurer un outil manuellement**.

10. Sous **Paramètres de** l’outil, entrez un **nom d’outil** comme **Classes Microsoft Teams**. Pour **la version LTI**, sélectionnez **LTI 1.3**. Pour **le type de clé publique**, sélectionnez **l’URL du jeu de clés**.

11. Ensuite, copiez les clés des **clés Microsoft LTI** vers les entrées d’outil correspondantes.
    1. La clé **URL du lien cible** de Microsoft entre dans le champ URL de l’outil d’Open LMS.
    1. La clé **d’URL de connexion Open ID** de Microsoft entre dans le champ **Lancer l’URL de connexion** d’Open LMS.
    1. La clé **URL de redirection** de Microsoft entre dans le champ **URI de redirection** d’Open LMS.

12. Sélectionnez **Enregistrer les modifications**.

13. Le nouvel outil doit maintenant apparaître dans la section **Outils** de la page **Gérer les outils** d’Open LMS. Sélectionnez l’icône de liste pour afficher **les détails de la configuration de l’outil**.

14. Retour à l’onglet Passerelle Microsoft LMS. Sélectionnez **Suivant** pour accéder à l’étape **des clés d’inscription fournies par LMS**.

15. Copiez et collez les valeurs des **détails de configuration de l’outil** Open LMS à l’étape des **clés d’inscription fournies par LMS** de Microsoft.

    Collez les valeurs comme suit :

    | Sur Open LMS | Sur le portail d’inscription Microsoft LTI |
    | --------- | ------------------------------------ |
    | ID de plateforme | URL de l’ID de l’émetteur |
    | ID du client | ID du client |
    | ID de déploiement | ID de déploiement |
    | URL du jeu de clés public | URL du jeu de clés |
    | URL du jeton d’accès | URL du jeton d’accès |
    | URL de la demande d’authentification | URL d’authentification de la plateforme |

    Sélectionnez **Suivant**.

16. Passez en revue la page **Révision et ajoutez** . En l’absence d’erreurs, **sélectionnez Enregistrer et quitter**. Vous devriez voir un message indiquant que l’inscription a réussi.

Vous avez terminé l’inscription des classes Teams ou de l’application LTI Réunions Teams.

Si vous souhaitez ajouter l’autre application également, répétez les étapes ci-dessus, en sélectionnant l’autre application LTI Teams à l’étape 4.

### <a name="add-teams-lti-apps-to-educators-open-lms-courses"></a>Ajouter des applications LTI Teams aux cours Open LMS des enseignants

Après avoir inscrit des applications LTI Teams, les enseignants peuvent ajouter l’application Classes Teams et l’application Réunions Teams à leurs cours Open LMS.

- [Instructions pour les enseignants sur l’ajout de l’application Teams Classes](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-ac6a1e34-32f7-45e6-b83e-094185a1e78a).
- [Instructions pour les enseignants sur l’ajout de l’application Réunions Teams](https://support.microsoft.com/topic/use-microsoft-teams-meetings-in-your-lms-11b6095d-f90b-42b9-ab77-4dcff2bb3b76).

## <a name="technical-requirements-to-launch-teams-lti-apps"></a>Conditions techniques requises pour lancer des applications LTI Teams

Pour lancer les applications LTI Teams dans Open LMS, il existe quelques exigences techniques qui doivent être satisfaites.

> [!NOTE]
> Les administrateurs informatiques et les enseignants peuvent inscrire des applications LTI sur le portail d’inscription des applications LTI.

### <a name="it-admin-technical-requirements"></a>Exigences techniques de l’administrateur informatique

- Utilisez Moodle version 3.10 ou ultérieure.
- Téléchargez le dernier plug-in Microsoft O365 pour Moodle version 3.10 ou ultérieure.
- Accédez au portail d’inscription des applications LTI pour inscrire les applications LTI.
  - L’inscription doit être effectuée sur un appareil de bureau.
- Téléchargez la dernière version de Microsoft Edge, Google Chrome, Safari ou Mozilla Firefox.

### <a name="educator-technical-requirements"></a>Exigences techniques des enseignants

- Accédez au portail d’inscription des applications LTI pour inscrire les applications LTI, si l’administrateur informatique n’a pas inscrit les applications.
  - L’inscription doit être effectuée sur un appareil de bureau.
- Téléchargez la dernière version de Microsoft Edge, Google Chrome, Safari ou Mozilla Firefox.
- [Applications LTI Teams pour les classes et les réunions dans Open LMS](#add-teams-lti-apps-to-educators-open-lms-courses).

### <a name="student-technical-requirements"></a>Exigences techniques des étudiants

- Applications LTI Teams pour les classes et les réunions dans Open LMS.
  - Les étudiants n’ont pas besoin d’effectuer d’actions pour ajouter les applications LTI Teams Classes ou Meetings.
