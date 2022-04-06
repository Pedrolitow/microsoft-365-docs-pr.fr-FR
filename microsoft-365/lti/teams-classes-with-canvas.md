---
title: Utiliser Microsoft Teams classes avec Canvas
ms.author: v-cichur
author: cichur
manager: serdars
ms.reviewer: sovaish
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Intégrer Microsoft Teams classes à Canvas
ms.openlocfilehash: 08edb2065cd91ccb0e0d52290dfe83f8a3e60392
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569001"
---
# <a name="use-microsoft-teams-classes-with-canvas"></a>Utiliser Microsoft Teams classes avec Canvas

Microsoft Teams classes est une application Learning Tools Interoperability (LTI) qui permet aux enseignants et aux étudiants de naviguer facilement entre leur système de gestion Learning (LMS) et leur Teams. Les utilisateurs peuvent accéder à leurs équipes de cours associées à leur cours directement à partir de leur LMS.

## <a name="prerequisites-before-deployment"></a>Conditions préalables avant le déploiement

> [!NOTE]
> L’Teams classes LTI prend uniquement en charge la synchronisation des utilisateurs canvas avec Microsoft Azure Active Directory (AAD) dans une étendue limitée.
>
> - Votre client doit avoir une licence Microsoft Éducation (A1 ou supérieure).
> - Un seul client Microsoft peut être utilisé pour le mappage d’utilisateurs entre Canvas et Microsoft.
> - Votre client doit avoir une correspondance exacte entre un champ Canvas (e-mail, ID utilisateur unique, ID SIS ou ID d’intégration) et un champ dans AAD (nom d’utilisateur principal (UPN), adresse de messagerie principale (messagerie) ou alias de messagerie (mailNickname)).
> - Si vous utilisez SDS pour créer des classes et des groupes, nous vous recommandons de désactiver l’option de création d’équipe dans [](/schooldatasync/group-cleanup) SDS et d’effectuer un nettoyage de groupe pour éviter la duplication des classes. SDS peut toujours être utilisé pour synchroniser les données de l’organisation et des utilisateurs.

## <a name="enable-the-microsoft-teams-app-in-canvas"></a>Activer l’application Microsoft Teams dans Canvas

Pour commencer l’intégration, vous devez activer l’application dans Canvas en activant les clés de développeur, en activant la synchronisation Microsoft Teams et en approuvant l’application Microsoft-Teams-Sync-for-Canvas. Notez que l’approbation de l’application peut uniquement être effectuée par un administrateur client Microsoft qui peut approuver les applications.

**Pour activer Microsoft Teams synchroniser et approuver l’accès pour l’application** :

1. Connectez-vous à Canvas en tant qu’administrateur.

2. Sélectionnez **le lien** Administrateur dans la navigation globale, puis sélectionnez votre compte.
3. Dans la navigation d’administration, sélectionnez le lien **Clés** de développement, puis sélectionnez **l’onglet** Hérité.
4. Activez les applications LTI que vous allez déployer en sélectionnant l’état **ON** pour chacune des applications appropriées.

5. Dans la navigation de l’administrateur, **sélectionnez Paramètres** lien, puis l’onglet **Intégrations**.

6. Activez Microsoft Teams synchronisation en  activer le basculement. Cette synchronisation permet de créer des classes dans Teams en fonction de l’inscription d’un cours.

   ![Canvas Teams Sync Updated png.](https://user-images.githubusercontent.com/87142492/128225881-abdfc52d-dc9e-48ad-aec5-f6617c6436f3.png)

7. Remplissez les champs suivants avec les informations appropriées. Ces champs seront utilisés pour faire correspondre les utilisateurs de Canvas aux utilisateurs AAD.
   - Le **nom du client** est le nom de votre client Microsoft.
   - **L’attribut de connexion** est l’un des attributs utilisateur canvas suivants utilisés pour le mappage :
      - **Le courrier** électronique est l’adresse de messagerie par défaut de l’utilisateur de Canvas. Si les utilisateurs modifient leur adresse de messagerie par défaut dans Canvas, leur inscription à un cours peut être bloquée lors de la synchronisation avec Teams.
      - **L’ID utilisateur unique** est l’ID de connexion canvas de l’utilisateur.
      - **L’ID utilisateur SIS** est la valeur d’ID qui est remplie à partir du système d’information sur les étudiants (SIS) et qui est consultable sur la page de profil de l’utilisateur.
      - **L’ID d’intégration** est uniquement rempli via les importations SIS et est consultable sur la page de profil de l’utilisateur. En règle générale, cet identificateur unique est fourni par l’établissement et utilisé dans les trusts de comptes ou dans les situations d’identification des utilisateurs sur plusieurs comptes.

   - Le **champ Suffix** est facultatif et vous permet de spécifier un domaine lorsqu’il n’existe pas de mappage exact entre les attributs canvas et les champs Microsoft AAD. Par exemple, si votre e-mail Canvas est « name@example.edu » alors que l’UPN dans Microsoft AAD est « name » (nom), vous pouvez faire correspondre les utilisateurs en entrant « @example.edu » dans le champ suffixe. Le domaine doit être entré dans ce champ avec le @précédent.
   - L’attribut de recherche Active Directory est le champ AAD les attributs Canvas sont en correspondance. Sélectionnez l’UPN, l’adresse de messagerie principale ou l’alias de messagerie.

8. **Sélectionnez Mettre à jour Paramètres**.

9. Pour approuver l’accès à l’application **Azure Microsoft-Teams-Sync-for-Canvas de Canvas**, sélectionnez le lien Accorder l’accès **client**. Vous serez redirigé vers le point de terminaison de consentement de l’administrateur de la plateforme d’identités Microsoft.

   ![autorisations.](media/permissions.png)

   > [!NOTE]
   > Cette étape doit être effectuée par un administrateur client Microsoft qui peut approuver des applications.

10. Sélectionnez **Accepter**.

## <a name="integrate-teams-classes-lti-in-canvas"></a>Intégrer Teams classes LTI dans Canvas

Après l’activation de la synchronisation et l’approbation de l’application Azure, l’administrateur canvas peut désormais ajouter l’application LTI des classes Teams à l’environnement canvas afin qu’elle apparaisse dans la navigation de l’interface utilisateur de Canvas.

**Pour ajouter l’application Teams classes LTI à l’environnement Canvas** :

1. Sous **l’onglet** Applications des **paramètres d’administration**, sélectionnez **+ Application** pour ajouter Teams applications LTI.

   ![external-apps.](media/external-apps.png)

2. Pour **le type de configuration**, **sélectionnez Par ID client**.

   ![ajouter une application.](media/add-app.png)

3. Pour **l’ID client**, entrez **170000000000570** pour les classes Microsoft Teams LTI, puis sélectionnez **Envoyer**.

4. Dans la confirmation qui s’affiche, vérifiez le nom de l’application (Microsoft Teams classes), puis sélectionnez **Installer**.

   L Microsoft Teams’application LTI des classes est désormais ajoutée à la liste des applications externes.

## <a name="enabling-the-lti-app-for-canvas-courses"></a>Activation de l’application LTI pour les cours Canvas

Pour utiliser l’application LTI dans un cours, un instructeur du cours Canvas doit activer la synchronisation des intégrations. Chaque cours doit être activé par un instructeur pour qu’une équipe correspondante soit créée . Il n’existe pas de mécanisme global pour la création d’équipes. Il s’agit d’une mesure de précaution pour empêcher la création d’équipes indésirables.

Consultez la [documentation](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) des instructeurs pour activer l’application LTI pour chaque cours et terminer la configuration de l’intégration.
