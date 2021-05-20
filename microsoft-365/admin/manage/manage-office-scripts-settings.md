---
title: Gérer les paramètres de Office Scripts
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid: MET150
description: Découvrez comment gérer les paramètres Office scripts pour les utilisateurs de votre organisation.
ms.openlocfilehash: e0cb52c4a8f48ff2310c83ffce61e08a0236ed59
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572308"
---
# <a name="manage-office-scripts-settings"></a>Gérer les paramètres de Office Scripts

[Office scripts permet aux utilisateurs](/office/dev/scripts)d’automatiser les tâches en enregistrant, éditant et exécutant des scripts Excel sur le Web. Office Scripts fonctionne avec Power Automate, et les utilisateurs exécutent des scripts sur les cahiers de travail en utilisant le connecteur Excel en ligne (Business). Microsoft 365 administrateurs peuvent gérer les paramètres Office scripts à partir du centre d Microsoft 365'administration.

## <a name="before-you-begin"></a>Avant de commencer

- Pour gérer Office paramètres scripts, vous devez être un administrateur global. Pour plus d’informations, voir [Sur les rôles admin](../add-users/about-admin-roles.md).

- Assurez-vous que les utilisateurs de votre organisation ont une licence valide pour un plan commercial ou UDI Microsoft 365 ou Office 365 qui inclut l’accès à des applications de bureau Office, telles que l’un des plans suivants :

    - Microsoft 365 Business Standard
    - Applications Microsoft 365 pour les entreprises
    - Microsoft 365 Apps for enterprise
    - Office 365 E3
    - Office 365 E5
    - Office 365 A3
    - Office 365 A5

## <a name="manage-availability-of-office-scripts-and-sharing-of-scripts"></a>Gérer la disponibilité Office scripts et le partage de scripts

1. Dans le Microsoft 365 d’administration, rendez-vous sur **l’onglet Paramètres** \> **paramètres Org** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">Services.</a>

2. Sélectionnez **Office scripts**.

3. Office Les scripts sont activés par défaut, et tous les membres de votre organisation peuvent accéder et utiliser la fonctionnalité et partager des scripts. Pour désactiver les Office pour votre organisation, effacer les utilisateurs **Let automatiser leurs tâches dans la case Excel sur le Web** cochée.

4. Si vous avez déjà désactivé les scripts Office pour votre organisation et que vous souhaitez l’activer, **sélectionnez Laissez les utilisateurs automatiser leurs tâches en Excel sur le Web,** puis spécifiez qui peut accéder et utiliser la fonctionnalité :

    - Pour permettre à tous les utilisateurs de votre organisation d’accéder et d’utiliser Office scripts, **laissez Tout le** monde (par défaut) sélectionné.

    - Pour permettre aux membres d’un groupe spécifique d’accéder et d’utiliser Office Scripts, **sélectionnez Groupe spécifique,** puis entrez le nom ou l’alias e-mail du groupe pour l’ajouter à la liste de permis. Vous pouvez ajouter un seul groupe à la liste d’autoriser, et il doit être l’un des types suivants:
        - Microsoft 365 groupe
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie
    
        Pour en savoir plus sur les différents types de groupes, consultez [Comparez les groupes](../create-groups/compare-groups.md).

5. Pour permettre aux utilisateurs ayant accès à Office Scripts de partager leurs scripts avec d’autres membres de votre organisation, **sélectionnez Laissez les utilisateurs ayant accès à Office Scripts partager leurs scripts avec d’autres membres de l’organisation.** Le partage de scripts en dehors d’une organisation n’est pas autorisé.
 
    > [!NOTE]
    > Si vous éteignez plus tard le partage de script pour votre organisation, les utilisateurs pourront toujours exécuter des scripts précédemment partagés.
 
6. Spécifiez quels utilisateurs ayant accès Office scripts peuvent partager leurs scripts :
    
    - Pour permettre à tous les utilisateurs ayant accès Office scripts de partager leurs scripts, laissez **Tout le monde** (par défaut) sélectionné.

    - Pour permettre aux membres d’un groupe spécifique ayant accès à Office Scripts de partager leurs scripts, sélectionnez **Groupe spécifique,** puis entrez le nom ou l’alias e-mail du groupe pour l’ajouter à la liste d’autoriser. Vous pouvez ajouter un seul groupe à la liste d’autoriser, et il doit être l’un des types suivants:
        - Microsoft 365 groupe
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie
    
        Pour en savoir plus sur les différents types de groupes, consultez [Comparez les groupes](../create-groups/compare-groups.md).

7. Pour permettre aux utilisateurs d’exécuter leurs scripts Office à l’intérieur des flux Power Automate, **sélectionnez Laissez les utilisateurs ayant accès à Office Scripts** exécuter leurs scripts avec Power Automate . Cela permet aux utilisateurs d’ajouter des étapes de [flux avec l’option Excel](/connectors/excelonlinebusiness) de **script** Run de Connector en ligne (Business).

    - Pour permettre à tous les utilisateurs ayant accès Office scripts d’utiliser leurs scripts dans les flux, **laissez Tout le** monde (par défaut) sélectionné.

    - Pour permettre aux membres d’un groupe spécifique ayant accès à Office Scripts d’utiliser leurs scripts dans les flux, sélectionnez **Groupe spécifique,** puis entrez le nom ou l’alias e-mail du groupe pour l’ajouter à la liste d’autoriser. Vous pouvez ajouter un seul groupe à la liste d’autoriser, et il doit être l’un des types suivants:
        - Microsoft 365 groupe
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie

        Pour en savoir plus sur les différents types de groupes, consultez [Comparez les groupes](../create-groups/compare-groups.md).

    - Pour en savoir plus sur l’utilisation Office scripts avec Power Automate, [consultez Exécuter Office scripts avec Power Automate](/office/dev/scripts/develop/power-automate-integration).

8. Sélectionnez **Enregistrer**.

    L’entrée en vigueur des modifications apportées aux paramètres des scripts Office jusqu’à 48 heures peut prendre effet.

## <a name="next-steps"></a>Étapes suivantes

Étant donné Office Scripts fonctionne avec Power Automate, nous vous recommandons d’examiner vos politiques existantes de prévention des pertes de données (DLP) pour vous assurer que les données de votre organisation restent protégées pendant que les utilisateurs utilisent Office Scripts. Pour plus d’informations, [consultez les politiques de prévention des pertes de données (DLP).](/power-automate/prevent-data-loss)

## <a name="related-content"></a>Contenu connexe

[Office Documentation technique scripts (page](/office/dev/scripts/) de lien)\
[Introduction aux Office scripts dans Excel](https://support.microsoft.com/office/9fbe283d-adb8-4f13-a75b-a81c6baf163a) (article)\
[Partage Office scripts en Excel pour le Web](https://support.microsoft.com/office/226eddbc-3a44-4540-acfe-fccda3d1122b) (article)\
[Enregistrer, modifier et créer des scripts Office dans Excel sur le Web](/office/dev/scripts/tutorials/excel-tutorial) (article)
