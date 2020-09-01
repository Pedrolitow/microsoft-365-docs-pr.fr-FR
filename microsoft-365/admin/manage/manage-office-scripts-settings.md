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
description: Découvrez comment gérer les paramètres des scripts Office pour les utilisateurs de votre organisation.
ms.openlocfilehash: 44e2a5c0e0577db344fdbb00a110674df3e71bdc
ms.sourcegitcommit: 04f196528a7a91b404478553433af3fa94d7eee7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2020
ms.locfileid: "47317492"
---
# <a name="manage-office-scripts-settings"></a>Gérer les paramètres de Office Scripts

Les scripts Office permettent aux utilisateurs d’automatiser des tâches en enregistrant, modifiant et exécutant des scripts dans Excel sur le Web. Les scripts Office fonctionnent avec Power automate, et les utilisateurs exécutent des scripts sur des classeurs à l’aide du connecteur Excel Online (Business). Les administrateurs 365 de Microsoft peuvent gérer les paramètres des scripts Office à partir du centre d’administration Microsoft 365.

## <a name="before-you-begin"></a>Avant de commencer

- Pour gérer les paramètres des scripts Office, vous devez être un administrateur général. Pour plus d’informations, consultez la rubrique [à propos des rôles d’administrateur](../add-users/about-admin-roles.md).

- Assurez-vous que les utilisateurs de votre organisation disposent d’une licence valide pour un plan commercial ou EDU Microsoft 365 ou Office 365 qui inclut l’accès aux applications de bureau Office, telles que l’un des plans suivants :

    - Microsoft 365 Business Standard
    - Applications Microsoft 365 pour les entreprises
    - Applications Microsoft 365 pour les entreprises
    - Office 365 E3
    - Office 365 E5
    - Office 365 A3
    - Office 365 A5

## <a name="manage-availability-of-office-scripts-and-sharing-of-scripts"></a>Gestion de la disponibilité des scripts et du partage de scripts Office

1. Dans le centre d’administration Microsoft 365, accédez à **l'** \> **Org settings** \> onglet <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">services</a> de paramètres d’organisation.

2. Sélectionnez **scripts Office**.

3. Les scripts Office sont activés par défaut et tous les membres de votre organisation peuvent accéder et utiliser les scripts de fonctionnalité et de partage. Pour désactiver les scripts Office pour votre organisation, désactivez la case à cocher **autoriser les utilisateurs à automatiser leurs tâches dans Excel sur le Web** .

4. Si vous avez précédemment désactivé les scripts Office pour votre organisation et que vous souhaitez le réactiver, sélectionnez **autoriser les utilisateurs à automatiser leurs tâches dans Excel sur le Web**, puis indiquez qui peut accéder à la fonctionnalité et comment l’utiliser :

    - Pour autoriser tous les utilisateurs de votre organisation à accéder et à utiliser des scripts Office, laissez **tout le monde** (valeur par défaut) sélectionnée. 

    - Pour autoriser uniquement les membres d’un groupe spécifique à accéder à des scripts Office et à les utiliser, sélectionnez **groupe spécifique**, puis entrez le nom ou l’alias de messagerie du groupe pour l’ajouter à la liste verte. Vous pouvez ajouter un seul groupe à la liste verte, et il doit s’agir de l’un des types suivants :
        - Groupe Microsoft 365
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie
    
        Pour en savoir plus sur les différents types de groupes, consultez la rubrique [compare Groups](../create-groups/compare-groups.md).

5. Pour permettre aux utilisateurs disposant d’un accès à des scripts Office de partager leurs scripts avec d’autres membres de votre organisation, sélectionnez **permettre aux utilisateurs ayant accès à des scripts Office de partager leurs scripts avec d’autres membres de l’organisation**. Les scripts de partage en dehors d’une organisation ne sont pas autorisés.
 
    > [!NOTE]
    > Si, par la suite, vous désactivez le partage de script pour votre organisation, les utilisateurs pourront toujours exécuter des scripts déjà partagés.
 
6. Spécifier les utilisateurs ayant accès aux scripts Office peuvent partager leurs scripts :
    
    - Pour permettre à tous les utilisateurs ayant accès aux scripts Office de partager leurs scripts, laissez **tout le monde** (valeur par défaut) sélectionnée.

    - Pour autoriser uniquement les membres d’un groupe spécifique à accéder aux scripts Office afin de partager leurs scripts, sélectionnez **groupe spécifique**, puis entrez le nom ou l’alias de messagerie du groupe pour l’ajouter à la liste verte. Vous pouvez ajouter un seul groupe à la liste verte, et il doit s’agir de l’un des types suivants :
        - Groupe Microsoft 365
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie
    
        Pour en savoir plus sur les différents types de groupes, consultez la rubrique [compare Groups](../create-groups/compare-groups.md).

7. Sélectionnez **Enregistrer**.

    L’application des modifications apportées aux paramètres des scripts Office peut prendre jusqu’à 48 heures.

## <a name="next-steps"></a>Étapes suivantes

Étant donné que les scripts Office fonctionnent avec Power Automated, nous vous recommandons de consulter vos stratégies de protection contre la perte de données (DLP) existantes pour vous assurer que les données de votre organisation restent protégées pendant que les utilisateurs utilisent des scripts Office. Pour plus d’informations, consultez la rubrique [stratégies de protection contre la perte de données (DLP)](/power-automate/prevent-data-loss).

## <a name="related-content"></a>Contenu connexe

[Documentation technique relative aux scripts Office](/office/dev/scripts/) (page lien) \
[Introduction aux scripts Office dans Excel](https://support.microsoft.com/office/9fbe283d-adb8-4f13-a75b-a81c6baf163a) (article) \
[Partage de scripts Office dans Excel pour le Web](https://support.microsoft.com/office/226eddbc-3a44-4540-acfe-fccda3d1122b) (article) \
[Enregistrer, modifier et créer des scripts Office dans Excel sur le Web](/office/dev/scripts/tutorials/excel-tutorial) (article)