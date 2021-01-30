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
description: Découvrez comment gérer les paramètres Des scripts Office pour les utilisateurs de votre organisation.
ms.openlocfilehash: 75d0a9d9e98652fc11eab7e8a7d6c826be031f6e
ms.sourcegitcommit: 50f10d83fa21db8572adab90784146e5231e3321
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "50058422"
---
# <a name="manage-office-scripts-settings"></a>Gérer les paramètres de Office Scripts

Les scripts Office permettent aux utilisateurs d’automatiser les tâches en enregistrant, en éditant et en exécutant des scripts dans Excel sur le web. Office Scripts fonctionne avec Power Automate et les utilisateurs exécutent des scripts sur des workbooks à l’aide du connecteur Excel Online (Entreprise). Les administrateurs Microsoft 365 peuvent gérer les paramètres des scripts Office à partir du Centre d’administration Microsoft 365.

## <a name="before-you-begin"></a>Avant de commencer

- Pour gérer les paramètres d’Office Scripts, vous devez être administrateur général. Pour plus d’informations, voir [à propos des rôles d’administrateur.](../add-users/about-admin-roles.md)

- Assurez-vous que les utilisateurs de votre organisation ont une licence valide pour un plan Microsoft 365 ou Office 365 commercial ou EDU qui inclut l’accès aux applications de bureau Office, telles que l’un des plans suivants :

    - Microsoft 365 Business Standard
    - Applications Microsoft 365 pour les entreprises
    - Applications Microsoft 365 for entreprise
    - Office 365 E3
    - Office 365 E5
    - Office 365 A3
    - Office 365 A5

## <a name="manage-availability-of-office-scripts-and-sharing-of-scripts"></a>Gérer la disponibilité des scripts Office et le partage des scripts

1. Dans le Centre d’administration Microsoft 365, go to the **Settings** \> **Org settings** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">Services</a> tab.

2. Sélectionnez **Scripts Office**.

3. Les scripts Office sont allumés par défaut, et tous les membres de votre organisation peuvent accéder à la fonctionnalité et les utiliser et partager des scripts. Pour désactiver les scripts Office pour votre organisation, désactiver la case à cocher Laisser les utilisateurs automatiser leurs tâches **dans Excel sur le web.**

4. Si vous avez précédemment désactivé Les scripts Office pour votre organisation et que vous souhaitez le désactiver à nouveau, sélectionnez Laisser les utilisateurs automatiser leurs tâches dans **Excel sur le web,** puis spécifiez qui peut accéder à la fonctionnalité et l’utiliser :

    - Pour autoriser tous les utilisateurs de votre organisation à accéder aux scripts Office et à les utiliser, laissez Tout le monde **(par** défaut) sélectionné.

    - Pour autoriser uniquement les membres d’un groupe spécifique à accéder aux scripts Office et à les utiliser, sélectionnez Groupe **spécifique,** puis entrez le nom ou l’alias de messagerie du groupe pour l’ajouter à la liste d’adresses. Vous ne pouvez ajouter qu’un seul groupe à la liste d’utilisateurs et il doit s’agit de l’un des types suivants :
        - Groupe Microsoft 365
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie
    
        Pour en savoir plus sur les différents types de groupes, voir [Comparer les groupes.](../create-groups/compare-groups.md)

5. Pour permettre aux utilisateurs ayant accès aux scripts Office de partager leurs scripts avec d’autres membres de votre organisation, sélectionnez Autoriser les utilisateurs ayant accès à Office Scripts à partager leurs scripts avec d’autres membres de **l’organisation.** Le partage de scripts en dehors d’une organisation n’est pas autorisé.
 
    > [!NOTE]
    > Si vous désactiverez ultérieurement le partage de scripts pour votre organisation, les utilisateurs pourront toujours exécuter des scripts précédemment partagés.
 
6. Spécifiez les utilisateurs ayant accès aux scripts Office qui peuvent partager leurs scripts :
    
    - Pour autoriser tous les utilisateurs ayant accès aux scripts Office à partager leurs scripts, laissez Tout le monde **(par** défaut) sélectionné.

    - Pour autoriser uniquement les membres d’un groupe spécifique ayant accès aux scripts Office à partager leurs scripts, sélectionnez **Un** groupe spécifique, puis entrez le nom ou l’alias de messagerie du groupe pour l’ajouter à la liste d’adresses. Vous ne pouvez ajouter qu’un seul groupe à la liste d’utilisateurs et il doit s’agit de l’un des types suivants :
        - Groupe Microsoft 365
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie
    
        Pour en savoir plus sur les différents types de groupes, voir [Comparer les groupes.](../create-groups/compare-groups.md)

7. Pour permettre aux utilisateurs d’exécuter leurs scripts Office à l’intérieur de flux Power Automate, sélectionnez Autoriser les utilisateurs ayant accès à Des scripts Office à exécuter leurs scripts avec **Power Automate.** Cela permet aux utilisateurs d’ajouter des étapes de flux avec l’option de **script** Exécuter [d’Excel Online (Business) Connector.](/connectors/excelonlinebusiness)

    - Pour autoriser tous les utilisateurs ayant accès aux scripts Office à utiliser leurs scripts dans les flux, laissez Tout le monde **(par** défaut) sélectionné.

    - Pour autoriser uniquement les membres d’un groupe spécifique ayant accès aux scripts Office à utiliser leurs scripts dans les flux, sélectionnez Groupe **spécifique,** puis entrez le nom ou l’alias de messagerie du groupe pour l’ajouter à la liste d’adresses. Vous ne pouvez ajouter qu’un seul groupe à la liste d’utilisateurs et il doit s’agit de l’un des types suivants :
        - Groupe Microsoft 365
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie

        Pour en savoir plus sur les différents types de groupes, voir [Comparer les groupes.](../create-groups/compare-groups.md)

    - Pour en savoir plus sur l’utilisation des scripts Office avec Power Automate, notamment sur l’impact de vos stratégies de protection contre la perte de données, voir Exécuter des scripts Office avec [Power Automate.](/office/dev/scripts/develop/power-automate-integration)

8. Sélectionnez **Enregistrer**.

    L’application des modifications apportées aux paramètres Office Scripts peut prendre jusqu’à 48 heures.

## <a name="next-steps"></a>Étapes suivantes

Comme Office Scripts fonctionne avec Power Automate, nous vous recommandons de passer en revue vos stratégies de protection contre la perte de données (DLP) existantes pour vous assurer que les données de votre organisation restent protégées pendant que les utilisateurs utilisent des scripts Office. Pour plus d’informations, voir Stratégies de protection contre la perte de [données (DLP).](/power-automate/prevent-data-loss)

## <a name="related-content"></a>Contenu connexe

Documentation technique relative aux [scripts Office](/office/dev/scripts/) (page de liens)\
[Introduction aux scripts Office dans Excel](https://support.microsoft.com/office/9fbe283d-adb8-4f13-a75b-a81c6baf163a) (article)\
[Partage de scripts Office dans Excel pour le Web](https://support.microsoft.com/office/226eddbc-3a44-4540-acfe-fccda3d1122b) (article)\
[Enregistrer, modifier et créer des scripts Office dans Excel sur le web](/office/dev/scripts/tutorials/excel-tutorial) (article)
