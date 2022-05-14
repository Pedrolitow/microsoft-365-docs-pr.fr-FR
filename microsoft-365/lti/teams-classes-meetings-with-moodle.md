---
title: Intégrer Microsoft Teams classes et réunions à Moodle
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
description: Créez et gérez Teams classes et réunions avec Microsoft OneDrive Learning Tools Interoperability for Moodle.
ms.openlocfilehash: a59c4fcb6f6a39f3a75acbaa241d50d25b9d444a
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415500"
---
# <a name="integrate-microsoft-teams-classes-and-meetings-within-moodle"></a>Intégrer Microsoft Teams classes et réunions dans Moodle

> [!NOTE]
> Actuellement, les intégrations Moodle et Microsoft Teams LTI sont disponibles uniquement en préversion privée.
>
>Si vous souhaitez participer au programme de préversion privée, [inscrivez-vous ici](https://m365crmedu.powerappsportals.com/LMSSignup/).

Ce guide fournit les étapes de l’administrateur informatique pour l’inscription des applications LTI Teams Classes et Teams Meetings sur Moodle.

Pour plus d’informations sur la gestion de toutes les applications LTI pour n’importe quel LMS, consultez [Gérer la passerelle Microsoft LMS pour n’importe quel LMS](manage-microsoft-one-lti.md).

## <a name="prerequisites-before-set-up"></a>Prérequis avant la configuration

Pour que l’intégration entre Moodle et Teams fonctionne correctement, Moodle et Teams doivent être configurés pour communiquer entre eux.

Suivez les [instructions d’installation et de configuration du plug-in Moodle](moodle-plugin-configuration.md).

## <a name="register-microsoft-teams-lti-for-use-in-moodle"></a>Inscrire Microsoft Teams LTI à utiliser dans Moodle

> [!IMPORTANT]
> La personne qui effectue cette intégration doit être un administrateur Moodle et un administrateur de locataire Microsoft 365.

1. Visitez [la passerelle Microsoft LMS](https://lti.microsoft.com/) et **sélectionnez le bouton Accéder au portail d’inscription** .

2. Connectez-vous avec un compte d’administrateur Microsoft 365.

3. Une fois connecté, **sélectionnez Ajouter une nouvelle inscription**.

4. Sélectionnez **Teams Réunions LTI** ou **Teams Classes LTI** à inscrire, puis sélectionnez **Suivant**.

5. Entrez un nom **d’inscription** facilement identifiable et sélectionnez **Moodle** comme plateforme LMS. Sélectionnez **Suivant**.

6. Vous recevrez une liste de clés qui doivent être ajoutées à votre site Moodle.

7. Ouvrez Moodle dans un autre onglet. Ne fermez pas l’onglet Passerelle Microsoft LMS.

8. Dans Moodle, accédez à **Site** **administrationPluginsActivity** >  >  **modulesExternal** >  **toolsManage** >  **toolsManage**.

9. Dans la page **Gérer les outils** , sélectionnez **configurer un outil manuellement**.

10. Sous **Paramètres de** l’outil, entrez un **nom d’outil** comme **Microsoft Teams Classes**. Pour **la version LTI**, sélectionnez **LTI 1.3**. Pour **le type de clé publique**, sélectionnez **l’URL du jeu de clés**.

11. Ensuite, copiez les clés des **clés Microsoft LTI** vers les entrées des outils correspondants.
    1. La clé **d’URL du lien cible** de Microsoft entre dans le champ URL de l’outil Moodle.
    1. La clé **d’URL de connexion Open ID** de Microsoft entre dans le champ **d’URL de connexion Initiate** de Moodle.
    1. La clé **URL de redirection** de Microsoft entre dans le champ **URI de redirection de** Moodle.

12. Sélectionnez **Enregistrer les modifications**.

13. Le nouvel outil doit maintenant apparaître dans la section **Outils** de la page **Gérer les outils** de Moodle. Sélectionnez l’icône de liste pour afficher **les détails de la configuration de l’outil**.

14. Retour à l’onglet Passerelle Microsoft LMS. Sélectionnez **Suivant** pour accéder à l’étape **des clés d’inscription fournies par LMS**.

15. Copiez et collez les valeurs des **détails de configuration** de Moodle’s Tool dans l’étape des **clés d’inscription fournies par LMS de** Microsoft.

  Collez les valeurs comme suit :

  | Sur Moodle | Sur le portail d’inscription Microsoft LTI |
  | --------- | ------------------------------------ |
  | ID de plateforme | URL de l’ID de l’émetteur |
  | ID du client | ID du client |
  | ID de déploiement | ID de déploiement |
  | URL du jeu de clés public | URL du jeu de clés |
  | URL du jeton d’accès | URL du jeton d’accès |
  | URL de la demande d’authentification | URL d’authentification de la plateforme |

  Sélectionnez **Suivant**.

16. Passez en revue la page **Révision et ajoutez** . En l’absence d’erreurs, **sélectionnez Enregistrer et quitter**. Vous devriez voir un message indiquant que l’inscription a réussi.

Vous avez terminé l’inscription de l’application Teams Classes ou Teams Meetings LTI.

Si vous souhaitez ajouter l’autre application également, répétez les étapes ci-dessus, en sélectionnant l’autre application LTI Teams à l’étape 4.

### <a name="add-teams-lti-apps-to-educators-moodle-courses"></a>Ajouter Teams applications LTI aux cours Moodle des enseignants

Après avoir inscrit Teams applications LTI, les enseignants peuvent ajouter l’application Teams Classes et l’application Teams Meetings à leurs cours Moodle.

- [Instructions pour les enseignants sur l’ajout de l’application Teams Classes](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-ac6a1e34-32f7-45e6-b83e-094185a1e78a).
- [Instructions de l’enseignant sur l’ajout de l’application réunions Teams](https://support.microsoft.com/topic/use-microsoft-teams-meetings-in-your-lms-11b6095d-f90b-42b9-ab77-4dcff2bb3b76).

## <a name="technical-requirements-to-launch-teams-lti-apps"></a>Conditions techniques requises pour lancer Teams applications LTI

Pour lancer les applications Teams LTI dans Moodle, il existe quelques exigences techniques qui doivent être satisfaites.

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
- [Teams applications LTI pour les classes et les réunions dans Moodle](#add-teams-lti-apps-to-educators-moodle-courses).

### <a name="student-technical-requirements"></a>Exigences techniques des étudiants

- Teams applications LTI pour les classes et les réunions dans Moodle.
  - Les étudiants n’ont pas besoin d’effectuer d’actions pour ajouter les applications LTI Teams Classes ou Réunions.
