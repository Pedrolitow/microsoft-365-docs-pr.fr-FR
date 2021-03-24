---
title: Gérer et surveiller les comptes de priorité
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
ms.custom: AdminSurgePortfolio
description: Surveiller les messages électroniques ayant échoué et retardés envoyés vers ou depuis des comptes ayant un impact important sur l’entreprise.
ms.openlocfilehash: 0bba1f87f80de9fea249ce2604e83ceeadfb79ee
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51050641"
---
# <a name="manage-and-monitor-priority-accounts"></a>Gérer et surveiller les comptes de priorité

Dans chaque organisation Microsoft 365, il existe des personnes essentielles, telles que des cadres, des responsables, des responsables ou d’autres utilisateurs qui ont accès à des informations sensibles, propriétaires ou prioritaires.

Pour aider votre organisation à protéger ces comptes, vous pouvez désormais désigner des utilisateurs spécifiques en tant que comptes prioritaires et tirer parti des fonctionnalités propres à l’application qui leur offrent une protection supplémentaire. À l’avenir, d’autres applications et fonctionnalités ront en charge les comptes prioritaires et, pour commencer, nous avons annoncé deux fonctionnalités : la **protection** de compte prioritaire et la surveillance du flux de messagerie **premium.**

- Protection des comptes prioritaires **:** Microsoft Defender pour Office 365 (anciennement Office 365 - Protection avancée contre les menaces) prend en charge les comptes prioritaires en tant que balises qui peuvent être utilisées dans les filtres dans les alertes, les rapports et les enquêtes. Pour plus d’informations, consultez [balises utilisateur dans Microsoft Defender pour Office 365.](../../security/defender-365-security/user-tags.md)
- **Surveillance du flux de messagerie premium** : un flux de messagerie sain peut être essentiel au succès de l’entreprise, et les retards ou défaillances de remise peuvent avoir un impact négatif sur l’entreprise. Vous pouvez choisir un seuil pour les e-mails en échec ou différés, recevoir des alertes lorsque ce seuil est dépassé et afficher un rapport des problèmes de messagerie pour les comptes prioritaires. Pour plus d’informations, consultez le rapport Problèmes de messagerie pour les comptes de priorité dans [le CE moderne](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report)

Pour obtenir les meilleures pratiques en matière de sécurité pour les comptes prioritaires, voir Recommandations en matière de [sécurité pour les comptes prioritaires.](../../security/defender-365-security/security-recommendations-for-priority-accounts.md)

## <a name="before-you-begin"></a>Avant de commencer

La **fonctionnalité de protection des** comptes prioritaires décrite dans cette rubrique est disponible uniquement pour les organisations qui répondent aux exigences suivantes :

- Microsoft Defender pour Office 365 Plan 2, y compris ceux avec Office 365 E3, Office 365 E5, Microsoft 365 E5 ou Microsoft 365 E5 Security.

La **fonctionnalité De surveillance du flux** de messagerie Premium décrite dans cette rubrique est disponible uniquement pour les organisations qui répondent aux exigences suivantes :

- Votre organisation doit avoir un nombre de licences d’au moins 10 000, de l’un des produits suivants ou d’une combinaison des produits suivants : Office 365 E3, Microsoft 365 E3, Office 365 E5, Microsoft 365 E5. Par exemple, votre organisation peut avoir 3 000 licences Office 365 E3 et 8 500 Licences Microsoft 365 E5, pour un total de 11 500 licences provenant des produits éligibles.
- Votre organisation doit avoir au moins 50 utilisateurs Exchange Online actifs par mois.

> [!NOTE]
> Vous pouvez surveiller jusqu’à 250 comptes prioritaires.

### <a name="add-priority-accounts-from-the-setup-page"></a>Ajouter des comptes de priorité à partir de la page d’installation

Ajoutez des comptes de priorité à partir de la **page d’installation.**

1. Go to the Microsoft 365 admin center at <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> .

2. Go to **Setup**  >  **Organizational knowledge**, and choose **View** under Monitor your most **important accounts**.

3. Sélectionnez **Commencer ou** **Gérer.**

4. Dans la page Ajouter **des** comptes de priorité, dans le champ de recherche, tapez le nom ou l’adresse e-mail de la personne que vous souhaitez ajouter à la liste des comptes prioritaires. Vous pouvez également définir votre seuil de courrier électronique pour les courriers électroniques en échec ou différés et obtenir un rapport hebdomadaire des problèmes pour les comptes prioritaires.

5. Sélectionnez l’utilisateur et choisissez **Enregistrer.**

Vous pouvez également ajouter des comptes de priorité à partir de la page Utilisateurs actifs.

### <a name="add-priority-accounts-from-active-users-page"></a>Ajouter des comptes de priorité à partir de la page Utilisateurs actifs

Ajoutez des comptes de priorité à partir de la page Utilisateurs actifs.

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Go to **Users**  >  **Active users** and choose **...** at the top of the page. Sélectionnez **Gérer les comptes prioritaires.**

3. Sélectionnez **Ajouter des** comptes et, dans la **page** Ajouter des comptes de priorité, dans le champ de recherche, tapez le nom de la personne que vous souhaitez ajouter à la liste des comptes prioritaires.

4. Sélectionnez l’utilisateur et choisissez **Enregistrer.**

## <a name="remove-a-user-from-the-priority-accounts-list"></a>Supprimer un utilisateur de la liste des comptes prioritaires

1. Go to the Microsoft 365 admin center at <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> .

2. Go to **Setup**  >  **Organizational knowledge**, and choose **View** under Monitor your most **important accounts**.

3. On the **Monitor your most accounts** page, choose **Priority accounts** under **Manage this feature**.

4. Dans la page **Comptes prioritaires,** sélectionnez l’utilisateur ou les utilisateurs que vous souhaitez supprimer de la liste, puis choisissez Supprimer **des comptes.**

## <a name="related-topics"></a>Voir aussi

[Utilisation des comptes prioritaires dans Microsoft 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/using-priority-accounts-in-microsoft-365/ba-p/1873314)