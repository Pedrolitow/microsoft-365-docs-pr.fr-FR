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
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
description: Surveillez les messages électroniques ayant échoué et retardés envoyés vers ou depuis des comptes ayant un impact commercial élevé.
ms.openlocfilehash: edf2c2b1994e1647c4df9b639386cc43dc312c80
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65465863"
---
# <a name="manage-and-monitor-priority-accounts-in-microsoft-365"></a>Gérer et surveiller les comptes prioritaires dans Microsoft 365

Dans chaque Microsoft 365 organisation, il existe des personnes essentielles, telles que des cadres supérieurs, des dirigeants, des gestionnaires ou d’autres utilisateurs, qui ont accès à des informations sensibles, propriétaires ou hautement prioritaires.

Pour aider votre organisation à protéger ces comptes, vous pouvez désormais désigner des utilisateurs spécifiques comme comptes prioritaires et tirer parti des fonctionnalités spécifiques à l’application qui leur offrent une protection supplémentaire. À l’avenir, davantage d’applications et de fonctionnalités prendront en charge les comptes prioritaires et, pour commencer, nous avons annoncé deux fonctionnalités : **la protection des comptes prioritaires** et la **surveillance des flux de messagerie Premium**.

- **Protection des comptes prioritaires** : Microsoft Defender pour Office 365 (anciennement Office 365 Advanced Threat Protection) prend en charge les comptes prioritaires en tant que balises qui peuvent être utilisées dans les filtres dans les alertes, les rapports et les enquêtes. Pour plus d’informations, consultez [les balises utilisateur dans Microsoft Defender pour Office 365](../../security/office-365-security/user-tags.md).

  Une question naturelle est la suivante : « Tous les utilisateurs ne sont-ils pas prioritaires ? Pourquoi ne pas désigner tous les utilisateurs comme comptes prioritaires ? » Oui, tous les utilisateurs sont une priorité, mais la protection de compte prioritaire offre les avantages supplémentaires suivants :

  - **Heuristiques supplémentaires** : notre analyse du flux de messagerie dans les centres de données Microsoft indique que les modèles de flux de messagerie pour les cadres de l’entreprise sont différents de ceux de l’employé moyen. La protection prioritaire des comptes offre des heuristiques supplémentaires qui sont spécifiquement adaptées aux cadres de l’entreprise qui ne bénéficieraient pas à un employé régulier.
  - **Visibilité supplémentaire des rapports** : En effet, les informations pour tous les utilisateurs (ou tous les utilisateurs concernés) sont déjà disponibles dans les alertes, les rapports et les enquêtes. La balise de comptes de priorité en tant que filtre vous permet de cibler spécifiquement vos investigations.

- **Premium surveillance des Flow** de courrier : un flux de courrier sain peut être essentiel à la réussite de l’entreprise, et les retards ou les échecs de remise peuvent avoir un impact négatif sur l’entreprise. Vous pouvez choisir un seuil pour les e-mails ayant échoué ou retardé, recevoir des alertes lorsque ce seuil est dépassé et afficher un rapport des problèmes de courrier pour les comptes prioritaires. Pour plus d’informations, consultez le [rapport Des problèmes de courrier électronique pour les comptes prioritaires dans le centre d’administration des comptes modernes](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report)

Pour connaître les meilleures pratiques de sécurité pour les comptes prioritaires, consultez [recommandations de sécurité pour les comptes prioritaires](../../security/office-365-security/security-recommendations-for-priority-accounts.md).

## <a name="before-you-begin"></a>Avant de commencer

La fonctionnalité de **protection des comptes Prioritaire** décrite dans cette rubrique est disponible uniquement pour les organisations qui répondent aux exigences suivantes :

- Microsoft Defender pour Office 365 plan 2, y compris ceux avec Office 365 E3, Office 365 E5, Microsoft 365 E5 ou Microsoft 365 E5 Sécurité.

La fonctionnalité **Premium Mail Flow Monitoring** décrite dans cette rubrique est disponible uniquement pour les organisations qui répondent aux exigences suivantes :

- Votre organisation doit avoir un nombre de licences d’au moins 5 000, provenant de l’un des produits ou d’une combinaison des produits suivants : Office 365 E3, Microsoft 365 E3, Office 365 E5, Microsoft 365 E5. Par exemple, votre organisation peut avoir 3 000 licences Office 365 E3 et 2 500 Microsoft 365 E5, pour un total de 5 500 licences provenant des produits éligibles.
- Votre organisation doit avoir au moins 50 utilisateurs actifs mensuels pour une ou plusieurs charges de travail principales : Teams, One Drive for Business, SharePoint Online, Exchange Online et Office applications.

> [!NOTE]
> Vous pouvez surveiller jusqu’à 250 comptes prioritaires.

Lorsque vous appliquez la protection de compte prioritaire à une boîte aux lettres, vous devez également appliquer la protection de compte prioritaire aux utilisateurs qui ont accès à la boîte aux lettres (par exemple, le PDG et l’assistant exécutif du PDG qui gère le calendrier du PDG).

### <a name="add-priority-accounts-from-the-setup-page"></a>Ajouter des comptes prioritaires à partir de la page d’installation

Ajoutez des comptes prioritaires à partir de la **page d’installation**.

1. Accédez au Centre d'administration Microsoft 365 sur <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Accédez à **SetupOrganizational** >  Knowledge, puis choisissez **Afficher** sous **Surveiller vos comptes les plus importants**.

3. Sélectionnez **Prise en main** ou **Gérer**.

4. Dans la page **Ajouter des comptes prioritaires** , dans le champ de recherche, tapez le nom ou l’adresse e-mail de la personne que vous souhaitez ajouter à la liste des comptes prioritaires. Vous pouvez également définir votre seuil d’e-mail pour les e-mails ayant échoué ou retardés et obtenir un rapport hebdomadaire des problèmes liés aux comptes prioritaires.

5. Sélectionnez l’utilisateur et **choisissez Enregistrer**.

Vous pouvez également ajouter des comptes de priorité à partir de la page Utilisateurs actifs.

### <a name="add-priority-accounts-from-active-users-page"></a>Ajouter des comptes prioritaires à partir de la page Utilisateurs actifs

Ajoutez des comptes prioritaires à partir de la page Utilisateurs actifs.

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Accédez aux **utilisateurs UsersActive** >  et sélectionnez les trois points (autres actions) en haut de la page. Sélectionnez **Gérer les comptes prioritaires**.

3. Sélectionnez **Ajouter des comptes** et, dans la page **Ajouter des comptes prioritaires** , dans le champ de recherche, tapez le nom de la personne que vous souhaitez ajouter à la liste des comptes prioritaires.

4. Sélectionnez l’utilisateur et **choisissez Enregistrer**.

## <a name="remove-a-user-from-the-priority-accounts-list"></a>Supprimer un utilisateur de la liste des comptes prioritaires

1. Accédez au Centre d'administration Microsoft 365 sur <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Accédez à **SetupOrganizational** >  Knowledge, puis choisissez **Afficher** sous **Surveiller vos comptes les plus importants**.

3. Dans la page **Surveiller la plupart de vos comptes** , choisissez **Comptes prioritaires** sous **Gérer cette fonctionnalité**.

4. Dans la page **Comptes prioritaires** , sélectionnez l’utilisateur ou les utilisateurs que vous souhaitez supprimer de la liste, puis **choisissez Supprimer les comptes**.

## <a name="related-topics"></a>Voir aussi

[Utilisation de comptes prioritaires dans Microsoft 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/using-priority-accounts-in-microsoft-365/ba-p/1873314)
