---
title: Gérer les commentaires de Microsoft pour votre organisation
f1.keywords:
- NOCSH
ms.author: Kwekua
author: Kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
description: Gérez les commentaires que vos utilisateurs peuvent envoyer à Microsoft concernant les produits Microsoft.
ms.openlocfilehash: 9f6923f4f20ec445980a40aeb2d731f8b1a2085a
ms.sourcegitcommit: aebcdbef52e42f37492a7f780b8b9b2bc0998d5c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2021
ms.locfileid: "59775779"
---
# <a name="manage-microsoft-feedback-for-your-organization"></a>Gérer les commentaires de Microsoft pour votre organisation

En tant qu’administrateur d’une organisation Microsoft 365, il existe désormais plusieurs stratégies pour vous aider à gérer la collecte de commentaires et l’expérience d’engagement client de vos utilisateurs lors de l’utilisation d Microsoft 365 applications. Vous pouvez créer et utiliser des groupes Azure Active Directory existants dans votre organisation pour chacune de ces stratégies. Grâce à ces politiques, vous pouvez contrôler la façon dont les différents services de votre organisation peuvent envoyer des commentaires à Microsoft. Microsoft examine tous les commentaires envoyés par les clients et utilise ces commentaires pour améliorer le produit. La conservation des expériences **de** commentaires vous permet de voir ce que vos utilisateurs pensent des produits Microsoft qu’ils utilisent. Les commentaires que nous collectons auprès de vos utilisateurs seront bientôt disponibles dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>.

Pour en savoir plus sur les types de commentaires et sur la façon dont Microsoft utilise les commentaires des utilisateurs, voir En savoir plus sur les commentaires [de Microsoft pour votre organisation.](../misc/feedback-user-control.md)

Le tableau ci-dessous représente les applications et services actuellement connectés aux stratégies de commentaires indiquées dans le tableau des stratégies de commentaires ci-dessous. Voir ci-dessous le tableau pour obtenir des exemples de capture d’écran.

|**Applications & Services**|**Commentaires sur le produit** <br> |**Enquêtes sur le produit** <br> |**Collection de métadonnées** <br> |**Implication des clients** <br> |
|:-----|:-----|:-----|:-----|:-----|
|**Access**|Oui|Oui|Oui|Oui|
|**Excel**|Oui|Oui|Oui|Oui|
|**Office.com**|Bientôt disponible|Bientôt disponible|Bientôt disponible|Bientôt disponible|
|**OneNote**|Oui|Oui|Oui|Oui|
|**OneDrive**|[Certains paramètres sont actuellement gérés par d’autres contrôles.](/onedrive/disable-contact-support-send-feedback)||||
|**Outlook**|Bientôt disponible|Bientôt disponible|Bientôt disponible|Bientôt disponible|
|**PowerPoint**|Oui|Oui|Oui|Oui|
|**Project**|Bientôt disponible|Bientôt disponible|Bientôt disponible|Bientôt disponible|
|**Éditeur**|Oui|Oui|Oui|Oui|
|**SharePoint**|[Certains paramètres sont actuellement gérés par d’autres contrôles.](/powershell/module/sharepoint-online/set-spotenant)||||
|**Teams**|[Certains paramètres sont actuellement gérés par d’autres contrôles.](/microsoftteams/manage-feedback-policies-in-teams)||||
|**Word**|Oui|Oui|Oui|Oui|
|**Visio**|Oui|Oui|Oui|Oui|
|**Yammer**|Oui|Oui|Oui|Oui|

[Pour obtenir des exemples d’enquêtes et de commentaires sur les produits, voir ici.](/microsoft-365/admin/misc/feedback-user-control#in-product-surveys)

**Collection de métadonnées**

:::image type="content" source="../../media/feedback-metadata2.png" alt-text="Capture d’écran : page de commentaires montrant l’exemple de métadonnées":::

**Implication des clients**

:::image type="content" source="../../media/feedback-in-product-customer-engagement.png" alt-text="Screenshot: In-product customer research question example":::

## <a name="before-you-begin"></a>Avant de commencer

Vos appareils doivent avoir un numéro de build minimal pour utiliser ces stratégies. Pour plus d’informations, voir le tableau ci-dessous.

|**Build #**|**Win32**|**iOS**|**Android**|**Mac**|**Web**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Commentaires sur le produit|Au moins 16.0.13328|Au moins 2,42|Au moins 16.0.13328|Au moins 16,42|Disponible publiquement|
|Enquêtes sur le produit|Au moins 16.0.13328|Au moins 2,42|Au moins 16.0.13426|Au moins 16,42|Déploiement en attente|
|Collection de métadonnées|Au moins 16.0.13328|Au moins 2,42|Au moins 16.0.13328|Au moins 16,42|Disponible publiquement|
|Implication des clients|Au moins 16.0.13328|Au moins 2,42|Au moins 16.0.13426|Au moins 16,42|Déploiement en attente|

## <a name="specific-policies-you-can-configure"></a>Stratégies spécifiques que vous pouvez configurer

### <a name="feedback-policies"></a>Stratégies de commentaires

|**Nom de la stratégie**|**État par défaut**|**Résumé des contrôles**|
|:-----|:-----|:-----|
|Autoriser les utilisateurs à envoyer des commentaires à Microsoft|Activé|Contrôle les points d’entrée de commentaires entre les applications|
|Autoriser les utilisateurs à recevoir et à répondre aux enquêtes in-product de Microsoft|Activé|Contrôle les invites d’enquête au sein du produit|
|Autoriser les utilisateurs à inclure des captures d’écran et des pièces jointes lorsqu’ils envoient des commentaires à Microsoft|Désactivé|Détermine les métadonnées que l’utilisateur peut décider d’envoyer avec des commentaires/enquêtes|
|Autoriser Microsoft à suivre les commentaires envoyés par les utilisateurs|Désactivé|Détermine si l’utilisateur peut partager des informations de contact avec des commentaires/enquêtes|
|Autoriser les utilisateurs à inclure des fichiers journaux et des exemples de contenu lorsque les commentaires sont envoyés à Microsoft|Désactivé|Détermine les métadonnées que l’utilisateur peut décider d’envoyer avec des commentaires/enquêtes|

## <a name="configure-policies"></a>Configurer des stratégies

1. Allez à [https://config.office.com](https://config.office.com) et connectez-vous.
1. Sélectionnez **Personnalisation,** puis **Gestion des stratégies.**
1. Sélectionnez **Créer**.
1. Entrez **le nom** et la **description.**
1. Choisissez les groupes Azure Active Directory que vous souhaitez configurer.
1. Recherchez les **commentaires et** les **enquêtes.**
1. Pour chaque stratégie répertoriée, définissez la valeur que vous souhaitez.

Pour plus d’informations, voir [Vue d’ensemble Office service de stratégie cloud.](/deployoffice/overview-office-cloud-policy-service)

Ces paramètres de stratégie sont également disponibles si vous utilisez la stratégie de groupe. Pour utiliser ces paramètres de stratégie, téléchargez au moins la version 5146.1000 des fichiers de modèle d’administration [(ADMX/ADML),](https://www.microsoft.com/download/details.aspx?id=49030)publiée le 22 mars 2021.

Vous trouverez ces paramètres de stratégie sous Configuration utilisateur -> Stratégies -> Modèles d’administration -> Microsoft Office 2016 -> Confidentialité -> Centre de gestion de la confidentialité.

> [!NOTE]
> La mise à jour des applications clientes prend quelques heures.
