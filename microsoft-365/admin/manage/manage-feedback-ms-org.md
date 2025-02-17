---
title: Gérer les commentaires de Microsoft pour votre organisation
f1.keywords:
- NOCSH
ms.author: Kwekua
author: Kwekua
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
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
description: Gérer les commentaires que vos utilisateurs peuvent envoyer à Microsoft sur les produits Microsoft.
ms.openlocfilehash: a10c16bea183520594d47d7f3010bfcc71883325
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68729146"
---
# <a name="manage-microsoft-feedback-for-your-organization"></a>Gérer les commentaires de Microsoft pour votre organisation

En tant qu’administrateur d’une organisation Microsoft 365, il existe désormais plusieurs stratégies pour vous aider à gérer la collecte de commentaires et l’expérience d’engagement client de vos utilisateurs lors de l’utilisation d’applications Microsoft 365. Vous pouvez créer et utiliser des groupes Azure Active Directory existants dans votre organisation pour chacune de ces stratégies. Avec ces stratégies, vous pouvez contrôler la façon dont les différents services de votre organisation peuvent envoyer des commentaires à Microsoft. Microsoft passe en revue tous les commentaires envoyés par les clients et utilise ces commentaires pour améliorer le produit. Le fait de garder les expériences de **commentaires activées** vous permet de voir ce que vos utilisateurs disent des produits Microsoft qu’ils utilisent. Les commentaires que nous recueillons auprès de vos utilisateurs sont disponibles dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>.

Pour en savoir plus sur les types de commentaires et la façon dont Microsoft utilise les commentaires des utilisateurs, consultez [En savoir plus sur les commentaires Microsoft pour votre organisation](../misc/feedback-user-control.md).

Le tableau ci-dessous indique les applications et services qui sont actuellement connectés aux stratégies de commentaires indiquées dans le tableau des stratégies de commentaires ci-dessous. Consultez le tableau ci-dessous pour obtenir des exemples de capture d’écran.

|**Applications & Services**|**Commentaires sur le produit** <br> |**Enquêtes sur les produits** <br> |**Collection de métadonnées** <br> |**Engagement client** <br> |
|:-----|:-----|:-----|:-----|:-----|
|**Access**|Oui|Oui|Oui|Oui|
|**Excel**|Oui|Oui|Oui|Oui|
|**Forms**|Oui|Oui|Oui|Oui|
|**Portail d'entreprise Intune (Android)**|Oui|Oui|Oui|Oui|
|**Microsoft Stream (Android, iOS)**|Oui|Oui|Oui|Oui|
|**Microsoft Whiteboard**|Oui|Oui|Oui|Oui|
|**Office.com**|Oui|Oui|Oui|Oui|
|**OneNote**|Oui|Oui|Oui|Oui|
|**OneDrive**|[Certains paramètres actuellement gérés par d’autres contrôles.](/onedrive/disable-contact-support-send-feedback)||||
|**Outlook (Web, iOS)**|Bientôt disponible|Bientôt disponible|Bientôt disponible|Bientôt disponible|
|**Outlook (Bureau, Android, Mac)**|Oui|Oui|Oui|Oui|
|**PowerPoint**|Oui|Oui|Oui|Oui|
|**Project**|Oui|Oui|Oui|Oui|
|**Éditeur**|Oui|Oui|Oui|Oui|
|**SharePoint**|[Certains paramètres actuellement gérés par d’autres contrôles.](/powershell/module/sharepoint-online/set-spotenant)||||
|**Teams**|[Certains paramètres actuellement gérés par d’autres contrôles.](/microsoftteams/manage-feedback-policies-in-teams)||||
|**To Do**|Oui|Oui|Oui|Oui|
|**Word**|Oui|Oui|Oui|Oui|
|**Visio**|Oui|Oui|Oui|Oui|
|**Viva Goals**|Oui|Oui|Oui|Oui|
|**Viva Insights**|Oui|Oui|Oui|Oui|
|**Tableau blanc collaboratif**|Oui|Oui|Oui|Oui|
|**Yammer**|Oui|Oui|Oui|Oui|

[Consultez cette page pour obtenir des exemples d’enquêtes et de commentaires sur le produit.](/microsoft-365/admin/misc/feedback-user-control#in-product-surveys)

**Collection de métadonnées**

:::image type="content" source="../../media/feedback-metadata2.png" alt-text="Capture d’écran : page de commentaires montrant l’exemple de métadonnées":::

**Engagement client**

:::image type="content" source="../../media/feedback-in-product-customer-engagement.png" alt-text="Capture d’écran : Exemple de question de recherche client dans le produit":::

## <a name="before-you-begin"></a>Avant de commencer

Vos appareils doivent être sur un numéro de build minimal pour utiliser ces stratégies. Pour plus d’informations, consultez le tableau ci-dessous.

|**Construire #**|**Win32**|**iOS**|**Android**|**Mac**|**Web**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Commentaires sur le produit|Au moins la version 2010|Au moins 2,42|Au moins 16.0.13328|Au moins 16,42|Accessibles|
|Enquêtes sur les produits|Au moins la version 2010|Au moins 2,42|Au moins 16.0.13426|Au moins 16,42|Déploiement en attente|
|Collection de métadonnées|Au moins la version 2010|Au moins 2,42|Au moins 16.0.13328|Au moins 16,42|Accessibles|
|Engagement client|Au moins la version 2010|Au moins 2,42|Au moins 16.0.13426|Au moins 16,42|Déploiement en attente|

## <a name="specific-policies-you-can-configure"></a>Stratégies spécifiques que vous pouvez configurer

### <a name="feedback-policies"></a>Stratégies de commentaires

|**Nom de la stratégie**|**État par défaut**|**Résumé du contrôle**|
|:-----|:-----|:-----|
|Autoriser les utilisateurs à accéder au portail de commentaires|Activé|Gérer l’accès utilisateur au portail de commentaires|
|Autoriser les utilisateurs à envoyer des commentaires à Microsoft|Activé|Contrôle les points d’entrée de commentaires entre les applications|
|Autoriser les utilisateurs à recevoir et à répondre à des enquêtes sur des produits à partir de Microsoft|Activé|Contrôles des invites d’enquête dans le produit|
|Autoriser les utilisateurs à inclure des captures d’écran et des pièces jointes lors de l’envoi de commentaires à Microsoft|Désactivé|Détermine les métadonnées que l’utilisateur peut décider d’envoyer avec des commentaires/sondages|
|Autoriser Microsoft à effectuer un suivi sur les commentaires envoyés par les utilisateurs|Désactivé|Détermine si l’utilisateur peut partager des informations de contact avec des commentaires/sondages|
|Autoriser les utilisateurs à inclure des fichiers journaux et des exemples de contenu lorsque les commentaires sont envoyés à Microsoft|Désactivé|Détermine les métadonnées que l’utilisateur peut décider d’envoyer avec des commentaires/sondages|

> [!NOTE]
> La stratégie **Autoriser les utilisateurs à accéder au portail de commentaires** est une stratégie cloud. Cette stratégie n’est pas définie dans ADMX et n’a pas de clé de Registre correspondante disponible pour définir la stratégie. Vous devez créer une stratégie cloud pour l’appliquer. Il s’agit d’une stratégie cloud, car le portail de commentaires est une application web qui effectue un appel au service de stratégie cloud, qui est également une application web, demandant les stratégies pour la personne qui se connecte. Si cette stratégie est configurée, le portail de commentaires reçoit la valeur de stratégie configurée dans la réponse du service de stratégie cloud.

## <a name="configure-policies"></a>Configurer des stratégies

Pour configurer ces paramètres de stratégie, vous pouvez utiliser le service de stratégie cloud Office. Pour plus d’informations, voir [Vue d’ensemble du service de stratégie cloud Office](/deployoffice/overview-office-cloud-policy-service). Vous pouvez rechercher « commentaires » ou « enquête » dans l’interface utilisateur du service de stratégie cloud Office pour trouver les paramètres de stratégie pour les configurer. 

Ces paramètres de stratégie sont également disponibles si vous utilisez stratégie de groupe. Pour utiliser ces paramètres de stratégie, téléchargez au moins la version 5146.1000 des [fichiers de modèle d’administration (ADMX/ADML),](https://www.microsoft.com/download/details.aspx?id=49030) publiée le 22 mars 2021.

Vous trouverez ces paramètres de stratégie sous Configuration utilisateur\Stratégies\Modèles d’administration\Microsoft Office 2016\Confidentialité\Centre de gestion de la confidentialité.

> [!NOTE]
> La mise à jour des applications clientes prend quelques heures.
