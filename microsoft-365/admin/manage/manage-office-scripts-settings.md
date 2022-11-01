---
title: Gérer les paramètres de Office Scripts
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid: MET150
description: Découvrez comment gérer les paramètres des scripts Office pour les utilisateurs de votre organisation.
ms.openlocfilehash: 5179c88c90a6a96b1f2d0dfcafe1c06299c5069d
ms.sourcegitcommit: 4bae15909267a70c8842bd0cd3dceb8459b4cc29
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68798318"
---
# <a name="manage-office-scripts-settings"></a>Gérer les paramètres de Office Scripts

[Les scripts Office](/office/dev/scripts) permettent aux utilisateurs d’automatiser des tâches en enregistrant, en modifiant et en exécutant des scripts dans Excel sur le Web. Les scripts Office fonctionnent avec Power Automate et les utilisateurs exécutent des scripts sur des classeurs à l’aide du connecteur Excel Online (Business). Les administrateurs Microsoft 365 peuvent gérer les paramètres de scripts Office à partir de la Centre d'administration Microsoft 365.

## <a name="before-you-begin"></a>Avant de commencer

- Pour gérer les paramètres des scripts Office, vous devez être administrateur général. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../add-users/about-admin-roles.md).

- Vérifiez que les utilisateurs de votre organisation disposent d’une licence valide pour un plan Microsoft 365 ou Office 365 commercial ou EDU qui inclut l’accès aux applications de bureau Office, comme l’un des plans suivants :

- Office 365 Business Premium
- Microsoft 365 Apps for business
- Microsoft 365 Apps for enterprise
- Office 365 E3
- Office 365 E5
- Office 365 A3
- Office 365 A5

## <a name="manage-availability-of-office-scripts-and-sharing-of-scripts"></a>Gérer la disponibilité des scripts Office et le partage des scripts

1. Dans le Centre d'administration Microsoft 365, accédez à l’onglet **Paramètres** \> **Des paramètres De l’organisation** \> **[Services](https://go.microsoft.com/fwlink/p/?linkid=2053743)**.

2. Sélectionnez **Scripts Office**.

3. Les scripts Office sont activés par défaut, et tous les membres de votre organisation peuvent accéder à la fonctionnalité et l’utiliser et partager des scripts. Pour désactiver les scripts Office pour votre organisation, décochez la case **Permettre aux utilisateurs d’automatiser leurs tâches dans Excel sur le Web**.

4. Si vous avez précédemment désactivé les scripts Office pour votre organisation et que vous souhaitez le réactiver, sélectionnez **Permettre aux utilisateurs d’automatiser leurs tâches dans Excel sur le Web**, puis spécifiez qui peut accéder à la fonctionnalité et l’utiliser :

    - Pour autoriser tous les utilisateurs de votre organisation à accéder aux scripts Office et à les utiliser, laissez **l’option Tout le monde** (valeur par défaut) sélectionnée.

    - Pour autoriser uniquement les membres d’un groupe spécifique à accéder et à utiliser les scripts Office, sélectionnez **Groupe spécifique**, puis entrez le nom ou l’alias de messagerie du groupe pour l’ajouter à la liste verte. Vous ne pouvez ajouter qu’un seul groupe à la liste verte, et il doit s’agir de l’un des types suivants :
        - Groupe Microsoft 365
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie

        Pour en savoir plus sur les différents types de groupes, consultez [Comparer des groupes](../create-groups/compare-groups.md).

5. Pour permettre aux utilisateurs ayant accès aux scripts Office de partager leurs scripts avec d’autres membres de votre organisation, sélectionnez **Permettre aux utilisateurs ayant accès aux scripts Office de partager leurs scripts avec d’autres membres de l’organisation**. Le partage de scripts en dehors d’une organisation n’est pas autorisé.

    > [!NOTE]
    > Si vous désactivez ultérieurement le partage de scripts pour votre organisation, les utilisateurs pourront toujours exécuter des scripts précédemment partagés.

6. Spécifiez les utilisateurs ayant accès aux scripts Office qui peuvent partager leurs scripts :

    - Pour permettre à tous les utilisateurs ayant accès aux scripts Office de partager leurs scripts, laissez **Tout le monde** (par défaut) sélectionné.

    - Pour autoriser uniquement les membres d’un groupe spécifique ayant accès aux scripts Office à partager leurs scripts, sélectionnez **Groupe spécifique**, puis entrez le nom ou l’alias de messagerie du groupe pour l’ajouter à la liste verte. Vous ne pouvez ajouter qu’un seul groupe à la liste verte, et il doit s’agir de l’un des types suivants :
        - Groupe Microsoft 365
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie

        Pour en savoir plus sur les différents types de groupes, consultez [Comparer des groupes](../create-groups/compare-groups.md).

7. Pour permettre aux utilisateurs d’exécuter leurs scripts Office dans des flux Power Automate, sélectionnez **Permettre aux utilisateurs ayant accès aux scripts Office d’exécuter leurs scripts avec Power Automate**. Cela permet aux utilisateurs d’ajouter des étapes de flux avec l’option **Exécuter le script** [du connecteur Excel Online (Business).](/connectors/excelonlinebusiness)

    - Pour permettre à tous les utilisateurs ayant accès aux scripts Office d’utiliser leurs scripts dans les flux, laissez **Tout le monde** (par défaut) sélectionné.

    - Pour autoriser uniquement les membres d’un groupe spécifique ayant accès aux scripts Office à utiliser leurs scripts dans des flux, sélectionnez **Groupe spécifique**, puis entrez le nom ou l’alias de messagerie du groupe pour l’ajouter à la liste verte. Vous ne pouvez ajouter qu’un seul groupe à la liste verte, et il doit s’agir de l’un des types suivants :
        - Groupe Microsoft 365
        - Groupe de distribution
        - Groupe de sécurité
        - Groupe de sécurité à extension messagerie

        Pour en savoir plus sur les différents types de groupes, consultez [Comparer des groupes](../create-groups/compare-groups.md).

    - Pour en savoir plus sur l’utilisation des scripts Office avec Power Automate, consultez [Exécuter des scripts Office avec Power Automate](/office/dev/scripts/develop/power-automate-integration).

8. Sélectionnez **Enregistrer**.

    Jusqu'à 48 heures peuvent être nécessaires pour que les modifications apportées aux paramètres d'Office Scripts prennent effet.

## <a name="manage-visibility-of-the-automate-tab-by-using-group-policy"></a>Gérer la visibilité de l’onglet Automatiser à l’aide de stratégie de groupe

stratégie de groupe dispose d’un paramètre pour afficher ou masquer l’onglet **Automatiser** ou tous les utilisateurs d’Excel sur le bureau de votre organisation. Vous trouverez les paramètres scripts Office sous Configuration ordinateur\Modèles d’administration\Microsoft Excel 2016\Divers dans la console de gestion stratégie de groupe.

Pour plus d’informations, consultez [Utiliser stratégie de groupe pour configurer les paramètres de mise à jour pour Microsoft 365 Apps](/deployoffice/configure-update-settings-microsoft-365-apps#use-group-policy-to-configure-update-settings-for-microsoft-365-apps).

## <a name="next-steps"></a>Prochaines étapes

Étant donné que les scripts Office fonctionnent avec Power Automate, nous vous recommandons de passer en revue vos stratégies de Protection contre la perte de données Microsoft Purview (DLP) existantes pour vous assurer que les données de votre organisation restent protégées pendant que les utilisateurs utilisent des scripts Office. Pour plus d’informations, consultez [stratégies de protection contre la perte de données (DLP)](/power-automate/prevent-data-loss).

## <a name="related-content"></a>Contenu associé

[Documentation technique sur les scripts Office](/office/dev/scripts/) (page de liens)\
[Présentation des scripts Office dans Excel](https://support.microsoft.com/office/9fbe283d-adb8-4f13-a75b-a81c6baf163a) (article)\
[Partage de scripts Office dans Excel pour le web](https://support.microsoft.com/office/226eddbc-3a44-4540-acfe-fccda3d1122b) (article)\
[Enregistrer, modifier et créer des scripts Office dans Excel sur le Web](/office/dev/scripts/tutorials/excel-tutorial) (article)
