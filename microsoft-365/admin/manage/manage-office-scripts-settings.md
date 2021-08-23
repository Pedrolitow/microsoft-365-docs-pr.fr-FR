---
title: Gérer les paramètres de Office Scripts
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
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid: MET150
description: Découvrez comment gérer les paramètres Office scripts pour les utilisateurs de votre organisation.
ms.openlocfilehash: 4af5d318552b371e9b7eef5be6750fde2c0b2ace
ms.sourcegitcommit: a7b289b8cc3a2eb79d5e46f20f2968adc0237da1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2021
ms.locfileid: "58394203"
---
# <a name="manage-office-scripts-settings"></a>Gérer les paramètres de Office Scripts

[Office scripts permet](/office/dev/scripts) aux utilisateurs d’automatiser les tâches en enregistrant, en éditant et en exécutant des scripts dans Excel sur le Web. Office Les scripts fonctionnent avec Power Automate, et les utilisateurs exécutent des scripts sur des workbooks à l’aide du connecteur Excel Online (Entreprise). Microsoft 365 administrateurs peuvent gérer les paramètres Office scripts à partir du Centre d’administration Microsoft 365.

## <a name="before-you-begin"></a>Avant de commencer

- Pour gérer Office de scripts, vous devez être administrateur global. Pour plus d’informations, voir [à propos des rôles d’administrateur.](../add-users/about-admin-roles.md)

- Assurez-vous que les utilisateurs de votre organisation ont une licence valide pour un plan Microsoft 365 ou Office 365 commercial ou EDU qui inclut l’accès aux applications de bureau Office, telles que l’un des plans suivants :

- Office 365 Business Premium
- Microsoft 365 Apps for business
- Microsoft 365 Apps for enterprise
- Office 365 E3
- Office 365 E5
- Office 365 A3
- Office 365 A5

## <a name="manage-availability-of-office-scripts-and-sharing-of-scripts"></a>Gérer la disponibilité des Office scripts et le partage des scripts

1. Dans la Centre d’administration Microsoft 365, go to the **Paramètres** \> **Org settings** \> **[Services](https://go.microsoft.com/fwlink/p/?linkid=2053743)** tab.

2. Sélectionnez **Office scripts**.

3. Office Les scripts sont allumés par défaut, et tous les membres de votre organisation peuvent accéder à la fonctionnalité et les utiliser et partager des scripts. Pour désactiver la Office scripts pour votre organisation, désactiver la case à cocher Laisser les utilisateurs **automatiser leurs tâches Excel sur le Web** cocher.

4. Si vous avez précédemment désactivé Office Scripts pour votre organisation et que vous souhaitez le désactiver à nouveau, sélectionnez Laisser les utilisateurs automatiser leurs tâches dans **Excel sur le Web,** puis spécifiez qui peut accéder à la fonctionnalité et l’utiliser :

    - Pour autoriser tous les utilisateurs de votre organisation à accéder et à utiliser Office scripts, laissez Tout le monde **(par** défaut) sélectionné.

    - Pour autoriser uniquement les membres d’un groupe spécifique à accéder aux scripts Office et à les utiliser, sélectionnez **Groupe** spécifique, puis entrez le nom ou l’alias de messagerie du groupe pour l’ajouter à la liste d’adresses. Vous ne pouvez ajouter qu’un seul groupe à la liste d’utilisateurs et il doit s’agit de l’un des types suivants :
        - Microsoft 365 groupe
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie

        Pour en savoir plus sur les différents types de groupes, voir [Comparer les groupes.](../create-groups/compare-groups.md)

5. Pour permettre aux utilisateurs ayant accès à Office Scripts de partager leurs scripts avec d’autres membres de votre organisation, sélectionnez Autoriser les utilisateurs à accéder à **Office Les scripts** partagent leurs scripts avec d’autres membres de l’organisation. Le partage de scripts en dehors d’une organisation n’est pas autorisé.

    > [!NOTE]
    > Si vous désactiverez ultérieurement le partage de scripts pour votre organisation, les utilisateurs pourront toujours exécuter des scripts précédemment partagés.

6. Spécifiez les utilisateurs ayant accès Office scripts peuvent partager leurs scripts :

    - Pour autoriser tous les utilisateurs à accéder Office scripts pour partager leurs scripts, laissez **Tout** le monde (par défaut) sélectionné.

    - Pour autoriser uniquement les membres d’un groupe spécifique ayant accès à Office Scripts à partager leurs scripts, sélectionnez **Groupe** spécifique, puis entrez le nom ou l’alias de messagerie du groupe pour l’ajouter à la liste d’adresses. Vous ne pouvez ajouter qu’un seul groupe à la liste d’utilisateurs et il doit s’agit de l’un des types suivants :
        - Microsoft 365 groupe
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie

        Pour en savoir plus sur les différents types de groupes, voir [Comparer les groupes.](../create-groups/compare-groups.md)

7. Pour permettre aux utilisateurs d’exécuter leurs scripts Office à l’intérieur de flux Power Automate, sélectionnez Autoriser les utilisateurs à accéder à **Office Scripts** exécutent leurs scripts avec Power Automate . Cela permet aux utilisateurs d’ajouter des étapes de flux [à l’Excel script](/connectors/excelonlinebusiness) Run du connecteur d’entreprise en ligne. 

    - Pour permettre à tous les utilisateurs ayant accès Office scripts d’utiliser leurs scripts dans les flux, laissez Tout le monde **(par** défaut) sélectionné.

    - Pour autoriser uniquement les membres d’un groupe spécifique ayant accès à Office Scripts à utiliser leurs scripts dans les flux, sélectionnez Groupe **spécifique,** puis entrez le nom ou l’alias de messagerie du groupe pour l’ajouter à la liste d’adresses. Vous ne pouvez ajouter qu’un seul groupe à la liste d’utilisateurs et il doit s’agit de l’un des types suivants :
        - Microsoft 365 groupe
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie

        Pour en savoir plus sur les différents types de groupes, voir [Comparer les groupes.](../create-groups/compare-groups.md)

    - Pour en savoir plus sur l’utilisation Office scripts avec Power Automate, voir [Exécuter Office scripts avec Power Automate](/office/dev/scripts/develop/power-automate-integration).

8. Sélectionnez **Enregistrer**.

    Jusqu'à 48 heures peuvent être nécessaires pour que les modifications apportées aux paramètres d'Office Scripts prennent effet.

## <a name="next-steps"></a>Étapes suivantes

Étant donné que Office Scripts fonctionne avec Power Automate, nous vous recommandons de passer en revue vos stratégies de protection contre la perte de données (DLP) existantes pour vous assurer que les données de votre organisation restent protégées pendant que les utilisateurs utilisent Office Scripts. Pour plus d’informations, consultez [stratégies de protection contre la perte de données (DLP)](/power-automate/prevent-data-loss).

## <a name="related-content"></a>Contenu connexe

[Office documentation technique sur les scripts](/office/dev/scripts/) (page de liens)\
[Introduction à Office scripts dans Excel](https://support.microsoft.com/office/9fbe283d-adb8-4f13-a75b-a81c6baf163a) (article)\
[Partage Office scripts dans Excel web](https://support.microsoft.com/office/226eddbc-3a44-4540-acfe-fccda3d1122b) (article)\
[Enregistrer, modifier et créer Office scripts dans Excel sur le Web](/office/dev/scripts/tutorials/excel-tutorial) (article)
