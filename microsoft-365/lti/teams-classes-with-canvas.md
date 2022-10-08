---
title: Utiliser des classes Microsoft Teams avec Canvas
ms.author: danismith
author: cichur
manager: serdars
ms.reviewer: sovaish
audience: admin
ms.topic: article
ms.service: microsoft-365-business
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Intégrer des classes Microsoft Teams à Canvas
ms.openlocfilehash: abff070c5981570f6afb8f712e5a4e8026050248
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68194420"
---
# <a name="use-microsoft-teams-classes-with-canvas"></a>Utiliser des classes Microsoft Teams avec Canvas

Les classes Microsoft Teams sont une application d’interopérabilité des outils d’apprentissage (LTI) qui permet aux enseignants et aux étudiants de naviguer facilement entre leur système de gestion de l’apprentissage (LMS) et Teams. Les utilisateurs peuvent accéder à leurs équipes de classe associées à leur cours directement à partir de leur LMS.

## <a name="prerequisites-before-deployment"></a>Prérequis avant le déploiement

> [!NOTE]
> Les classes Teams actuelles prennent uniquement en charge la synchronisation des utilisateurs canvas avec Microsoft Azure Active Directory (AAD) dans une étendue limitée.
>
> - Votre locataire doit disposer d’une licence Microsoft Education (A1 ou ultérieure).
> - Un seul locataire Microsoft peut être utilisé pour le mappage des utilisateurs entre Canvas et Microsoft.
> - Votre locataire doit avoir une correspondance exacte entre un champ Canvas (e-mail, ID d’utilisateur unique, ID SIS ou ID d’intégration) et un champ dans AAD (nom d’utilisateur principal (UPN), adresse de Email principale (courrier) ou alias Email (mailNickname)).
> - Si vous utilisez SDS pour créer des classes et des groupes, nous vous recommandons de désactiver l’option de création d’équipe dans SDS et d’effectuer un [nettoyage de groupe](/schooldatasync/group-cleanup) pour éviter la duplication des classes. SDS peut toujours être utilisé pour synchroniser l’organisation et les données utilisateur.

## <a name="enable-the-microsoft-teams-app-in-canvas"></a>Activer l’application Microsoft Teams dans Canvas

Pour commencer l’intégration, vous devez activer l’application dans Canvas en activant les clés de développeur, en activant Microsoft Teams Sync et en approuvant l’application Microsoft-Teams-Sync-for-Canvas. Notez que l’approbation de l’application ne peut être effectuée que par un administrateur client Microsoft qui peut approuver des applications.

**Pour activer Microsoft Teams Sync et approuver l’accès à l’application** :

1. Connectez-vous à Canvas en tant qu’administrateur.

2. Sélectionnez le lien **Administration** dans la navigation globale, puis sélectionnez votre compte.
3. Dans le volet de navigation de l’administrateur, sélectionnez le lien **Clés** du développeur, puis sélectionnez l’onglet **Hérité** .
4. Activez les applications LTI que vous allez déployer en sélectionnant l’état **ON** pour chacune des applications appropriées.

5. Dans la navigation de l’administrateur, sélectionnez le lien **Paramètres** , puis l’onglet **Intégrations** .

6. Activez Microsoft Teams Sync en activant le bouton bascule. Cette synchronisation permet de créer des classes dans Teams en fonction de l’inscription d’un cours.

   ![Canvas Teams Sync Mise à jour png.](https://user-images.githubusercontent.com/87142492/128225881-abdfc52d-dc9e-48ad-aec5-f6617c6436f3.png)

7. Renseignez les champs suivants avec les informations appropriées. Ces champs seront utilisés pour mettre en correspondance les utilisateurs dans Canvas avec les utilisateurs dans AAD.
   - Le **nom du locataire** est votre nom de locataire Microsoft.
   - **L’attribut login** est l’un des attributs utilisateur Canvas suivants utilisés pour le mappage :
      - **Email** est l’adresse e-mail par défaut de l’utilisateur Canvas. Si les utilisateurs modifient leur adresse e-mail par défaut dans Canvas, leur inscription à un cours peut être bloquée pour la synchronisation avec Teams.
      - **L’ID d’utilisateur unique** est l’ID de connexion Canvas de l’utilisateur.
      - **L’ID d’utilisateur SIS** est la valeur d’ID qui est renseignée à partir du système SIS (Student Information System) et qui est visible sur la page de profil de l’utilisateur.
      - **L’ID d’intégration** est rempli uniquement via des importations SIS et est visible sur la page de profil de l’utilisateur. En règle générale, cet identificateur unique est fourni par l’institution et utilisé dans les approbations de compte ou les situations de consortium pour identifier les utilisateurs sur plusieurs comptes.

   - Le champ **Suffixe** est facultatif et vous permet de spécifier un domaine lorsqu’il n’existe pas de mappage exact entre les attributs Canvas et les champs Microsoft AAD. Par exemple, si votre e-mail Canvas est « name@example.edu » alors que l’UPN dans Microsoft AAD est « name », vous pouvez faire correspondre les utilisateurs en entrant « @example.edu » dans le champ de suffixe. Le domaine doit être entré dans ce champ avec le @précédent.
   - L’attribut recherche Active Directory est le champ dans AAD auquel les attributs canvas sont mis en correspondance. Sélectionnez entre l’UPN, l’adresse e-mail principale ou l’alias de messagerie.

8. Sélectionnez **Mettre à jour les paramètres**.

9. Pour approuver l’accès à l’application **Azure Microsoft-Teams-Sync-for-Canvas** de Canvas, sélectionnez le lien **Accorder l’accès au locataire** . Vous êtes redirigé vers le point de terminaison de consentement de la plateforme d’identités Microsoft Administration.

   ![Autorisations.](media/permissions.png)

   > [!NOTE]
   > Cette étape doit être effectuée par un administrateur client Microsoft qui peut approuver des applications.

10. Sélectionnez **Accepter**.

## <a name="integrate-teams-classes-lti-in-canvas"></a>Intégrer des classes Teams LTI dans Canvas

Après avoir activé la synchronisation et approuvé l’application Azure, l’administrateur canvas peut maintenant ajouter l’application LTI des classes Teams à l’environnement Canvas afin qu’elle apparaisse dans la navigation de l’interface utilisateur canvas.

**Pour ajouter l’application LTI des classes Teams à l’environnement Canvas** :

1. Sous l’onglet **Applications** dans **Administration paramètres**, sélectionnez **+ Application** pour ajouter les applications LTI Teams.

   ![external-apps.](media/external-apps.png)

2. Pour **type de configuration**, sélectionnez **Par ID client**.

   ![ajouter une application.](media/add-app.png)

3. Pour **l’ID client**, entrez **170000000000570** pour les classes Microsoft Teams LTI, puis **sélectionnez Envoyer**.

4. Dans la confirmation qui s’affiche, vérifiez le nom de l’application (classes Microsoft Teams), puis sélectionnez **Installer**.

   L’application LTI des classes Microsoft Teams est maintenant ajoutée à la liste des applications externes.

## <a name="enabling-the-lti-app-for-canvas-courses"></a>Activation de l’application LTI pour les cours Canvas

Pour utiliser l’application LTI dans un cours, un instructeur du cours Canvas doit activer la synchronisation des intégrations. Chaque cours doit être activé par un instructeur pour qu’une équipe correspondante soit créée; il n’existe aucun mécanisme global pour la création d’équipes. Il s’agit d’une mesure de précaution destinée à empêcher la création d’équipes indésirables.

Reportez-vous à la [documentation](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) de vos formateurs pour activer l’application LTI pour chaque cours et terminer la configuration de l’intégration.
