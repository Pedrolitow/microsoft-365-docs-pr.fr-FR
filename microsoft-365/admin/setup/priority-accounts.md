---
title: Gérer et surveiller les comptes prioritaires
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
description: Le moniteur a échoué et retardé les messages envoyés vers ou à partir de comptes ayant un impact élevé sur l’activité.
ms.openlocfilehash: bc191873b3bbdcd84122a5430adeffe2b8c29fb1
ms.sourcegitcommit: 5ce64d510b15c6e2df32b78e6086f77156731e3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "49477612"
---
# <a name="manage-and-monitor-priority-accounts"></a>Gérer et surveiller les comptes prioritaires

Dans chaque organisation Microsoft 365, il existe des personnes qui sont essentielles, comme des cadres, des dirigeants, des responsables ou d’autres utilisateurs qui ont accès à des informations sensibles, propriétaires ou à haute priorité.

Pour aider votre organisation à protéger ces comptes, vous pouvez maintenant désigner des utilisateurs spécifiques comme comptes prioritaires et exploiter des fonctionnalités spécifiques aux applications qui leur fournissent une protection supplémentaire. À l’avenir, des applications et des fonctionnalités supplémentaires prendront en charge les comptes prioritaires et nous avons annoncé deux fonctionnalités : la **protection de compte prioritaire** et l' **analyse du flux de messagerie Premium**.

- **Protection des comptes prioritaires** : Microsoft Defender pour Office 365 (anciennement Office 365 Advanced Threat Protection) prend en charge les comptes prioritaires en tant que balises pouvant être utilisées dans les filtres dans les alertes, les rapports et les enquêtes. Pour plus d’informations, consultez les [balises utilisateur dans Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/user-tags?view=o365-worldwide).
- **Surveillance du flux de messagerie Premium** : le flux de messagerie intègre peut être essentiel à la réussite de l’entreprise, et les délais de remise ou les échecs peuvent avoir un impact négatif sur l’entreprise. Vous pouvez choisir un seuil pour les e-mails ayant échoué ou retardé, recevoir des alertes en cas de dépassement de ce seuil et afficher un rapport des problèmes de messagerie pour les comptes prioritaires. Pour plus d’informations, consultez [l’e-mail problèmes liés aux comptes prioritaires dans le centre d'](https://docs.microsoft.com/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report)administration Exchange moderne.

## <a name="before-you-begin"></a>Avant de commencer

La fonctionnalité de **protection des comptes prioritaires** décrite dans cette rubrique est disponible uniquement pour les organisations qui répondent aux exigences suivantes :

- Microsoft Defender pour Office 365 plan 2, y compris ceux avec Office 365 E3, Office 365 E5, Microsoft 365 E5 ou Microsoft 365 E5 sécurité.

La fonctionnalité de **surveillance du flux de messagerie Premium** décrite dans cette rubrique est disponible uniquement pour les organisations qui remplissent les conditions suivantes :

- Votre organisation doit avoir un nombre de licences d’au moins 10 000, soit de l’une ou l’autre des produits suivants : Office 365 E3, Microsoft 365 E3, Office 365 E5, Microsoft 365 E5. Par exemple, votre organisation peut avoir 3000 Office 365 E3 licences et 8500 Microsoft 365 E5, soit un total de 11 500 licences des produits qualifiants.
- Votre organisation doit disposer d’au moins 50 utilisateurs Exchange Online actifs mensuels.

> [!NOTE]
> Vous pouvez surveiller jusqu’à 250 comptes de priorité.

### <a name="add-priority-accounts-from-the-setup-page"></a>Ajouter des comptes de priorité à partir de la page de configuration

Ajoutez des comptes de priorité à partir de la **page de configuration**.

1. Accédez au centre d’administration Microsoft 365 à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> .

2. Accédez à **configurer**  >  les connaissances de l'**organisation**, puis choisissez **affichage** sous **surveiller vos comptes les plus importants**.

3. Sélectionnez **prise en main** ou **gestion**.

4. Dans la page **Ajouter un compte prioritaire** , dans le champ de recherche, tapez le nom ou l’adresse de messagerie de la personne que vous souhaitez ajouter à la liste comptes prioritaires. Vous pouvez également définir le seuil de courrier électronique pour les messages ayant échoué ou différé et obtenir un rapport hebdomadaire des problèmes liés aux comptes prioritaires.

5. Sélectionnez l’utilisateur, puis cliquez sur **Enregistrer**.

Vous pouvez également ajouter des comptes de priorité à partir de la page utilisateurs actifs.

### <a name="add-priority-accounts-from-active-users-page"></a>Ajouter des comptes prioritaires à partir de la page utilisateurs actifs

Ajoutez des comptes de priorité à partir de la page utilisateurs actifs.

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Accédez à **utilisateurs**  >  **actifs** et sélectionnez **...** en haut de la page. Sélectionnez **Manage Priority Accounts**.

3. Sélectionnez **Ajouter des comptes**, puis, dans la page **Ajouter un compte prioritaire** , dans le champ de recherche, tapez le nom de la personne que vous souhaitez ajouter à la liste comptes prioritaires.

4. Sélectionnez l’utilisateur, puis cliquez sur **Enregistrer**.

## <a name="remove-a-user-from-the-priority-accounts-list"></a>Supprimer un utilisateur de la liste des comptes prioritaires

1. Accédez au centre d’administration Microsoft 365 à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> .

2. Accédez à **configurer**  >  les connaissances de l'**organisation**, puis choisissez **affichage** sous **surveiller vos comptes les plus importants**.

3. Sur la page **surveiller votre plus grand nombre de comptes** , choisissez **comptes prioritaires** sous **gérer cette fonctionnalité**.

4. Sur la page **comptes prioritaires** , sélectionnez l’utilisateur ou les utilisateurs que vous souhaitez supprimer de la liste, puis choisissez **supprimer des comptes**.

## <a name="related-topics"></a>Voir aussi

[Utilisation de comptes prioritaires dans Microsoft 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/using-priority-accounts-in-microsoft-365/ba-p/1873314)