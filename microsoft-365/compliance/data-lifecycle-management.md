---
title: En savoir plus sur la gestion du cycle de vie des données Microsoft Purview
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
- m365initiative-compliance
description: Apprenez comment la gestion du cycle de vie des données Microsoft Purview vous aide à conserver ce dont vous avez besoin et à supprimer ce dont vous n'avez pas besoin.
ms.openlocfilehash: d783ef7f97b45f21f6c90f2aa0230120634abd93
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624396"
---
# <a name="learn-about-data-lifecycle-management"></a>En savoir plus sur la gestion du cycle de vie des données

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

La gestion du cycle de vie des données Microsoft Purview (anciennement Microsoft Information Governance) vous fournit des outils et des capacités pour conserver le contenu que vous devez conserver et supprimer le contenu que vous ne devez pas conserver. La conservation et la suppression de contenu sont souvent nécessaires pour la conformité et les exigences réglementaires, mais la suppression de contenu qui n’a plus de valeur commerciale vous aide également à gérer les risques et la responsabilité. Par exemple, cela réduit la surface d’attaque.

**Les stratégies de conservation** sont la pierre angulaire de la gestion du cycle de vie des données. Utilisez ces stratégies pour les charges de travail Microsoft 365 qui comprennent Exchange, SharePoint, OneDrive, Teams et Yammer. Configurez si le contenu de ces services doit être conservé indéfiniment ou pendant une période spécifique si les utilisateurs le modifient ou le suppriment. Vous pouvez également configurer la stratégie pour supprimer automatiquement définitivement le contenu après une période spécifiée s’il n’est pas déjà supprimé. Vous pouvez également combiner ces deux actions pour conserver, puis supprimer, ce qui est une configuration très classique. Par exemple, conservez le courrier pendant trois ans, puis supprimez-le.

Lorsque vous configurez une stratégie de rétention, vous pouvez cibler toutes les instances de votre organisation (telles que toutes les boîtes aux lettres et tous les sites SharePoint) ou des instances individuelles (telles que les boîtes aux lettres pour des départements ou régions spécifiques, ou des sites SharePoint sélectionnés).

Si vous avez besoin d’exceptions pour des e-mails ou des documents individuels, par exemple une période de rétention plus longue pour les documents juridiques, vous pouvez le faire avec des **étiquettes de rétention** que vous publiez sur des applications afin que les utilisateurs puissent les appliquer, ou les appliquer automatiquement en inspectant le contenu.

Pour plus d’informations sur les stratégies de rétention et les étiquettes de rétention et sur le fonctionnement de la rétention dans Microsoft 365, consultez [En savoir plus sur les stratégies de rétention et les étiquettes de rétention](retention.md). 

> [!NOTE]
> Si vous devez gérer des éléments de grande valeur pour des raisons commerciales, juridiques ou réglementaires, utilisez des étiquettes de conservation avec [gestion des enregistrements](records-management.md) plutôt que des étiquettes de conservation avec gestion du cycle de vie des données.

D'autres fonctionnalités de gestion du cycle de vie des données pour vous aider à conserver ce dont vous avez besoin et à supprimer ce qui ne l'est pas :

- **Archivage de boîte aux lettres** pour fournir aux utilisateurs un espace de stockage de boîte aux lettres supplémentaire et l’archivage à extension automatique pour les boîtes aux lettres nécessitant plus de 100 Go de stockage. Une stratégie d’archivage par défaut déplace automatiquement le courrier vers la boîte aux lettres d’archivage et, si nécessaire, vous pouvez personnaliser cette stratégie. Pour plus d’informations sur l’archivage des boîtes aux lettres, voir [En savoir plus sur les boîtes aux lettres d’archivage.](archive-mailboxes.md)
    
- **Boîtes aux lettres inactives** qui conservent le contenu de la boîte aux lettres après que les employés ont quitté l’organisation. Pour plus d’informations sur les boîtes aux lettres inactives, voir [En savoir plus sur les boîtes aux lettres inactives.](inactive-mailboxes-in-office-365.md)

- **Service d’importation pour les fichiers PST** à l’aide du chargement réseau ou de l’expédition de disque. Pour plus d’informations, voir [En savoir plus sur l’importation des fichiers PST de votre organisation](importing-pst-files-to-office-365.md).

## <a name="deployment-guidance"></a>Instructions de déploiement

Pour obtenir des conseils sur le déploiement de la gestion du cycle de vie des données, notamment une feuille de route recommandée pour le déploiement, des informations sur les licences, les autorisations, une liste des scénarios pris en charge et la documentation destinée aux utilisateurs finaux, [consultez la rubrique Démarrez avec la gestion du cycle de vie des données](get-started-with-information-governance.md).

Vous recherchez des conseils de déploiement pour protéger vos données ? Voir [Déployer une solution de protection des informations avec Microsoft Purview](information-protection-solution.md).

