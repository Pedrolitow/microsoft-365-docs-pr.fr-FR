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
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid: MET150
description: Découvrez comment gérer Office paramètres de scripts pour les utilisateurs de votre organisation.
ms.openlocfilehash: fdc9c947ee7f12e284fd215f05f8b5c3dcb127eb
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941146"
---
# <a name="manage-office-scripts-settings"></a>Gérer les paramètres de Office Scripts

[Office Scripts permet aux utilisateurs](/office/dev/scripts) d’automatiser les tâches en enregistrant, en modifiant et en exécutant des scripts dans Excel sur le Web. Office Scripts fonctionne avec Power Automate et les utilisateurs exécutent des scripts sur des classeurs à l’aide du connecteur Excel Online (Entreprise). Microsoft 365 administrateurs peuvent gérer les paramètres de scripts Office à partir du Centre d'administration Microsoft 365.

## <a name="before-you-begin"></a>Avant de commencer

- Pour gérer Office paramètres de scripts, vous devez être administrateur général. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../add-users/about-admin-roles.md).

- Vérifiez que les utilisateurs de votre organisation disposent d’une licence valide pour une Microsoft 365 ou Office 365 plan commercial ou EDU qui inclut l’accès à Office applications de bureau, comme l’un des plans suivants :

- Office 365 Business Premium
- Microsoft 365 Apps for business
- Microsoft 365 Apps for enterprise
- Office 365 E3
- Office 365 E5
- Office 365 A3
- Office 365 A5

## <a name="manage-availability-of-office-scripts-and-sharing-of-scripts"></a>Gérer la disponibilité des scripts Office et le partage des scripts

1. Dans le Centre d'administration Microsoft 365, accédez à l’onglet **[Services](https://go.microsoft.com/fwlink/p/?linkid=2053743)** des **paramètres** \> de **l’organisation Paramètres**\>.

2. Sélectionnez **Office Scripts**.

3. Office scripts est activé par défaut, et tous les membres de votre organisation peuvent accéder à la fonctionnalité et l’utiliser et partager des scripts. Pour désactiver Office scripts pour votre organisation, désactivez la case à cocher **Autoriser les utilisateurs à automatiser leurs tâches dans Excel sur le Web** case à cocher.

4. Si vous avez précédemment désactivé Office scripts pour votre organisation et que vous souhaitez le réactiver, sélectionnez **Autoriser les utilisateurs à automatiser leurs tâches dans Excel sur le Web**, puis spécifiez qui peut accéder à la fonctionnalité et l’utiliser :

    - Pour permettre à tous les utilisateurs de votre organisation d’accéder et d’utiliser Office Scripts, laissez **Tout le monde** (valeur par défaut) sélectionné.

    - Pour autoriser uniquement les membres d’un groupe spécifique à accéder et à utiliser Office Scripts, sélectionnez **Groupe spécifique**, puis entrez le nom ou l’alias de messagerie du groupe pour l’ajouter à la liste verte. Vous ne pouvez ajouter qu’un seul groupe à la liste verte, et il doit s’agir de l’un des types suivants :
        - groupe Microsoft 365
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie

        Pour en savoir plus sur les différents types de groupes, consultez [Comparer les groupes](../create-groups/compare-groups.md).

5. Pour permettre aux utilisateurs ayant accès à Office Scripts de partager leurs scripts avec d’autres membres de votre organisation, sélectionnez **Autoriser les utilisateurs ayant accès à Office Scripts partager leurs scripts avec d’autres membres de l’organisation**. Le partage de scripts en dehors d’une organisation n’est pas autorisé.

    > [!NOTE]
    > Si vous désactivez ultérieurement le partage de scripts pour votre organisation, les utilisateurs pourront toujours exécuter des scripts précédemment partagés.

6. Spécifiez les utilisateurs ayant accès à Office Scripts peuvent partager leurs scripts :

    - Pour permettre à tous les utilisateurs ayant accès à Office Scripts de partager leurs scripts, laissez **Tout le monde** (valeur par défaut) sélectionné.

    - Pour autoriser uniquement les membres d’un groupe spécifique ayant accès à Office Scripts à partager leurs scripts, sélectionnez **Groupe spécifique**, puis entrez le nom ou l’alias de messagerie du groupe pour l’ajouter à la liste verte. Vous ne pouvez ajouter qu’un seul groupe à la liste verte, et il doit s’agir de l’un des types suivants :
        - groupe Microsoft 365
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie

        Pour en savoir plus sur les différents types de groupes, consultez [Comparer les groupes](../create-groups/compare-groups.md).

7. Pour permettre aux utilisateurs d’exécuter leurs scripts Office dans Power Automate flux, sélectionnez **Autoriser les utilisateurs ayant accès à Office Scripts exécuter leurs scripts avec Power Automate**. Cela permet aux utilisateurs d’ajouter des étapes de flux avec [l’option de script d’exécution du connecteur Excel Online (Entreprise](/connectors/excelonlinebusiness)).

    - Pour permettre à tous les utilisateurs ayant accès à Office Scripts d’utiliser leurs scripts dans les flux, laissez **Tout le monde** (valeur par défaut) sélectionné.

    - Pour autoriser uniquement les membres d’un groupe spécifique ayant accès à Office Scripts à utiliser leurs scripts dans des flux, sélectionnez **Groupe spécifique**, puis entrez le nom ou l’alias de messagerie du groupe pour l’ajouter à la liste verte. Vous ne pouvez ajouter qu’un seul groupe à la liste verte, et il doit s’agir de l’un des types suivants :
        - groupe Microsoft 365
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie

        Pour en savoir plus sur les différents types de groupes, consultez [Comparer les groupes](../create-groups/compare-groups.md).

    - Pour en savoir plus sur l’utilisation de scripts Office avec Power Automate, consultez [Exécuter des scripts Office avec Power Automate](/office/dev/scripts/develop/power-automate-integration).

8. Sélectionnez **Enregistrer**.

    Jusqu'à 48 heures peuvent être nécessaires pour que les modifications apportées aux paramètres d'Office Scripts prennent effet.

## <a name="next-steps"></a>Étapes suivantes

Étant donné que Office Scripts fonctionne avec Power Automate, nous vous recommandons de passer en revue vos stratégies de protection contre la perte de données (DLP) Microsoft Purview existantes pour vous assurer que les données de votre organisation restent protégées pendant que les utilisateurs utilisent Office Scripts. Pour plus d’informations, consultez [stratégies de protection contre la perte de données (DLP)](/power-automate/prevent-data-loss).

## <a name="related-content"></a>Contenu associé

[documentation technique Office Scripts](/office/dev/scripts/) (page de liens)\
[Présentation des scripts Office dans Excel](https://support.microsoft.com/office/9fbe283d-adb8-4f13-a75b-a81c6baf163a) (article)\
[Partage de scripts Office dans Excel pour le web](https://support.microsoft.com/office/226eddbc-3a44-4540-acfe-fccda3d1122b) (article)\
[Enregistrer, modifier et créer des scripts Office dans Excel sur le Web](/office/dev/scripts/tutorials/excel-tutorial) (article)
