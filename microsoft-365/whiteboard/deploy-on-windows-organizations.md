---
title: Déployer Microsoft Whiteboard sur des appareils Windows 10
ms.author: chucked
author: chuckedmonson
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.prod: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: Découvrez comment déployer des Microsoft Whiteboard sur des appareils exécutant Windows 10 ou versions ultérieures.
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 07c55ecb881c3c7c8f6803845d8619c368c65270
ms.sourcegitcommit: b0b1be67de8f40b199bb9b51eb3568e59377e93a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2022
ms.locfileid: "66159765"
---
# <a name="deploy-microsoft-whiteboard-on-windows-10-devices"></a>Déployer Microsoft Whiteboard sur des appareils Windows 10

Le tableau blanc peut être déployé sur des appareils qui s’exécutent Windows 10 ou ultérieur à l’aide d’Microsoft Intune ou de Microsoft Configuration Manager (anciennement System Center Configuration Manager). Le tableau blanc n’est pas pris en charge sur Windows Server.

- **Microsoft Intune à l’aide d’un mode de licence en ligne** : ce processus vous permet de spécifier des groupes d’utilisateurs qui recevront l’accès à l’application Tableau blanc.

- **Microsoft Configuration Manager à l’aide d’une installation et de mises à jour manuelles hors connexion** : ce processus vous permet d’installer le Tableau blanc, puis de le mettre à jour manuellement toutes les 2 à 4 semaines.

>[!NOTE]
> Nous vous recommandons d’utiliser Microsoft Intune. L’utilisation de Microsoft Configuration Manager nécessite que le service informatique réemballe et installe en permanence les mises à jour pour s’assurer que les utilisateurs exécutent une version à jour.

## <a name="install-whiteboard-using-microsoft-intune"></a>Installer le Tableau blanc à l’aide de Microsoft Intune

1. Ajoutez le tableau blanc en tant qu’application disponible en suivant les étapes décrites dans cet article : [Ajouter des applications Microsoft Store à Microsoft Intune](/mem/intune/apps/store-apps-windows).

2. Affectez l’application à un groupe en suivant les étapes décrites dans cet article : [Affecter des applications à des groupes avec Microsoft Intune](/mem/intune/apps/apps-deploy).

## <a name="install-whiteboard-using-microsoft-configuration-manager"></a>Installer le Tableau blanc à l’aide de Microsoft Configuration Manager

1. À l’aide d’un compte d’administrateur général, connectez-vous au [Microsoft Store pour Entreprises](https://businessstore.microsoft.com).

2. Dans l’en-tête, sélectionnez **Gérer**.

3. Dans le volet de navigation de droite, sélectionnez **Paramètres**, puis **activez Afficher les applications hors connexion**.

4. Attendez 10 à 15 minutes pour la propagation.

5. Ensuite, accédez à [l’application Tableau blanc](https://businessstore.microsoft.com/store/details/microsoft-whiteboard/9mspc6mp8fm4).

6. Sélectionnez **Obtenir l’application**, puis acceptez les termes du contrat de licence.

7. Retour à la page de l’application.

8. Dans le menu déroulant **Type de licence** , sélectionnez **Hors connexion**.

9. Sélectionnez **Gérer**.

10. Cette action vous permet d’accéder à la page de gestion des stocks, qui offre désormais la possibilité de **télécharger le package pour une utilisation hors connexion**.

11. Choisissez la version de l’architecture, puis téléchargez-la.

12. Dès que vous avez téléchargé l’application, vous pouvez la déployer via Configuration Manager. Pour créer un package de mise à jour, suivez les étapes 7 à 10 pour télécharger une version plus récente et l’empaqueter pour Configuration Manager.

13. Pour plus d’informations, consultez [Installer des applications pour un appareil](/mem/configmgr/apps/deploy-use/install-app-for-device).

## <a name="see-also"></a>Voir aussi

[Activer et gérer l’accès au Tableau blanc](enable-whiteboard-access-organizations.md)

[Gérer les données pour le tableau blanc](manage-data-organizations.md)

[Gérer le partage pour le tableau blanc](manage-sharing-organizations.md)

