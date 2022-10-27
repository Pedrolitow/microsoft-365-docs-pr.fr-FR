---
title: Gérer et surveiller les comptes de priorité
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
description: Surveillez les messages électroniques ayant échoué et retardé envoyés vers ou à partir de comptes ayant un impact important sur l’activité.
ms.openlocfilehash: 5c19164d8460c1722fe5ebec7355c2283d007a54
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68732314"
---
# <a name="manage-and-monitor-priority-accounts"></a>Gérer et surveiller les comptes de priorité

Dans chaque organisation Microsoft 365, il existe des personnes essentielles, telles que des cadres, des dirigeants, des responsables ou d’autres utilisateurs, qui ont accès à des informations sensibles, propriétaires ou hautement prioritaires.

Pour aider votre organisation à protéger ces comptes, vous pouvez désormais désigner des utilisateurs spécifiques en tant que comptes prioritaires et tirer parti des fonctionnalités spécifiques à l’application qui leur fournissent une protection supplémentaire. À l’avenir, d’autres applications et fonctionnalités prendront en charge les comptes prioritaires. Pour commencer, nous avons annoncé deux fonctionnalités : la **protection des comptes prioritaires** et la **surveillance des flux de messagerie Premium**.

- **Protection des comptes prioritaires** : Microsoft Defender pour Office 365 (anciennement Office 365 Advanced Threat Protection) prend en charge les comptes prioritaires en tant que balises qui peuvent être utilisées dans les filtres dans les alertes, les rapports et les enquêtes. Pour plus d’informations, consultez [Balises utilisateur dans Microsoft Defender pour Office 365](../../security/office-365-security/user-tags.md).

  Une question naturelle est la suivante : « Tous les utilisateurs ne sont-ils pas une priorité ? Pourquoi ne pas désigner tous les utilisateurs comme comptes prioritaires ? » Oui, tous les utilisateurs sont prioritaires, mais la protection des comptes prioritaires offre les avantages supplémentaires suivants :

  - **Heuristique supplémentaire** : notre analyse du flux de courrier dans les centres de données Microsoft indique que les modèles de flux de courrier pour les cadres de l’entreprise sont différents de ceux de l’employé moyen. La protection des comptes prioritaires offre des heuristiques supplémentaires qui sont spécifiquement adaptées aux cadres de l’entreprise qui ne bénéficieraient pas à un employé régulier.
  - **Visibilité supplémentaire dans les rapports** : en effet, les informations pour tous les utilisateurs (ou tous les utilisateurs affectés) sont déjà disponibles dans les alertes, les rapports et les enquêtes. La balise comptes prioritaires en tant que filtre vous permet de cibler spécifiquement vos investigations.

- **Surveillance du flux de courrier Premium** : un flux de courrier sain peut être essentiel à la réussite de l’entreprise, et les retards ou échecs de livraison peuvent avoir un impact négatif sur l’entreprise. Vous pouvez choisir un seuil pour les e-mails ayant échoué ou retardé, recevoir des alertes lorsque ce seuil est dépassé et afficher un rapport des problèmes de messagerie pour les comptes prioritaires. Pour plus d’informations, consultez [Email rapport sur les problèmes liés aux comptes prioritaires dans le centre d’administration Exchange moderne](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report)

Pour connaître les meilleures pratiques de sécurité pour les comptes prioritaires, consultez [Recommandations de sécurité pour les comptes prioritaires](../../security/office-365-security/security-recommendations-for-priority-accounts.md).

## <a name="before-you-begin"></a>Avant de commencer

La fonctionnalité **de protection de compte prioritaire** décrite dans cette rubrique est disponible uniquement pour les organisations qui répondent aux exigences suivantes :

- Microsoft Defender pour Office 365 Plan 2, y compris ceux avec Office 365 E3, Office 365 E5, Microsoft 365 E5 ou Microsoft 365 E5 Sécurité.

La fonctionnalité **Premium Mail Flow Monitoring** décrite dans cette rubrique est disponible uniquement pour les organisations qui répondent aux exigences suivantes :

- Votre organisation doit avoir un nombre de licences d’au moins 5 000, provenant de l’un des produits suivants ou d’une combinaison des produits suivants : Office 365 E3, Microsoft 365 E3, Office 365 E5 Microsoft 365 E5. Par exemple, votre organisation peut avoir 3 000 licences Office 365 E3 et 2 500 Microsoft 365 E5, pour un total de 5 500 licences provenant des produits éligibles.
- Votre organisation doit avoir au moins 50 utilisateurs actifs par mois pour une ou plusieurs charges de travail principales : Teams, OneDrive Entreprise, SharePoint Online, Exchange Online et applications Office.

> [!NOTE]
> Vous pouvez surveiller jusqu’à 250 comptes prioritaires.

Lorsque vous appliquez une protection de compte prioritaire à une boîte aux lettres, vous devez également appliquer la protection des comptes prioritaires aux utilisateurs qui ont accès à la boîte aux lettres (par exemple, le PDG et l’assistant exécutif du PDG qui gère le calendrier du PDG).

### <a name="add-priority-accounts-from-the-setup-page"></a>Ajouter des comptes prioritaires à partir de la page d’installation

Ajoutez des comptes prioritaires à partir de la **page Configuration**.

1. Accédez au Centre d'administration Microsoft 365 sur <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Accédez à **Configurer Connaissances** > **organisationnelles**, puis choisissez **Afficher** sous **Surveiller vos comptes les plus importants**.

3. Sélectionnez **Prise en main** ou **Gérer**.

4. Dans la page **Ajouter des comptes prioritaires** , dans le champ de recherche, tapez le nom ou l’adresse e-mail de la personne que vous souhaitez ajouter à la liste des comptes prioritaires. Vous pouvez également définir votre seuil d’e-mail pour les e-mails ayant échoué ou retardé et obtenir un rapport hebdomadaire des problèmes pour les comptes prioritaires.

5. Sélectionnez l’utilisateur et choisissez **Enregistrer**.

Vous pouvez également ajouter des comptes prioritaires à partir de la page Utilisateurs actifs.

### <a name="add-priority-accounts-from-active-users-page"></a>Ajouter des comptes prioritaires à partir de la page Utilisateurs actifs

Ajoutez des comptes prioritaires à partir de la page Utilisateurs actifs.

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Accédez à **Utilisateurs** > **Utilisateurs actifs** et sélectionnez les trois points (autres actions) en haut de la page. Sélectionnez **Gérer les comptes prioritaires**.

3. Sélectionnez **Ajouter des comptes**, puis dans la page **Ajouter des comptes prioritaires** , dans le champ de recherche, tapez le nom de la personne que vous souhaitez ajouter à la liste des comptes prioritaires.

4. Sélectionnez l’utilisateur et choisissez **Enregistrer**.

## <a name="remove-a-user-from-the-priority-accounts-list"></a>Supprimer un utilisateur de la liste des comptes prioritaires

1. Accédez au Centre d'administration Microsoft 365 sur <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Accédez à **Configurer Connaissances** > **organisationnelles**, puis choisissez **Afficher** sous **Surveiller vos comptes les plus importants**.

3. Dans la page **Surveiller la plupart de vos comptes** , choisissez **Comptes prioritaires** sous **Gérer cette fonctionnalité**.

4. Dans la page **Comptes prioritaires** , sélectionnez le ou les utilisateurs que vous souhaitez supprimer de la liste et choisissez **Supprimer les comptes**.

## <a name="related-topics"></a>Voir aussi

[Utilisation de comptes prioritaires dans Microsoft 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/using-priority-accounts-in-microsoft-365/ba-p/1873314)
