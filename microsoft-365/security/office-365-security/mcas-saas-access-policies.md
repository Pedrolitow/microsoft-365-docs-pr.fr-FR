---
title: Stratégies de Microsoft Defender for Cloud Apps recommandées pour les applications SaaS - Microsoft 365 Entreprise | Microsoft Docs
description: Décrit les stratégies recommandées pour l’intégration à Microsoft Defender for Cloud Apps.
author: BrendaCarter
manager: laurawi
ms.topic: article
audience: Admin
ms.author: bcarter
ms.date: 03/22/2021
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- zerotrust-solution
ms.prod: m365-security
ms.openlocfilehash: 3a0c5b3cbc34bf24c04a476091e3dc08b0655a74
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750251"
---
# <a name="recommended-microsoft-defender-for-cloud-apps-policies-for-saas-apps"></a>Stratégies de Microsoft Defender for Cloud Apps recommandées pour les applications SaaS

Microsoft Defender for Cloud Apps s’appuie sur des stratégies d’accès conditionnel Azure AD pour permettre la surveillance et le contrôle en temps réel des actions granulaires avec les applications SaaS, telles que le blocage des téléchargements, des chargements, du copier-coller et de l’impression. Cette fonctionnalité ajoute la sécurité aux sessions qui comportent des risques inhérents, par exemple lorsque les ressources d’entreprise sont accessibles à partir d’appareils non gérés ou par des utilisateurs invités.

Defender pour Cloud Apps s’intègre également en mode natif à Protection des données Microsoft Purview, en fournissant une inspection du contenu en temps réel pour rechercher des données sensibles basées sur des types d’informations sensibles et des étiquettes de confidentialité et pour prendre les mesures appropriées.

Ces conseils incluent des recommandations pour ces scénarios :

- Intégrer des applications SaaS dans la gestion informatique
- Paramétrer la protection pour des applications SaaS spécifiques
- Configurer la protection contre la perte de données (DLP) Microsoft Purview pour vous aider à respecter les réglementations en matière de protection des données

## <a name="bring-saas-apps-into-it-management"></a>Intégrer des applications SaaS dans la gestion informatique

La première étape de l’utilisation de Defender pour Cloud Apps pour gérer les applications SaaS consiste à les découvrir, puis à les ajouter à votre locataire Azure AD. Si vous avez besoin d’aide pour la découverte, consultez [Découvrir et gérer les applications SaaS dans votre réseau](/cloud-app-security/tutorial-shadow-it). Une fois que vous avez découvert des applications, [ajoutez-les à votre locataire Azure AD](/azure/active-directory/manage-apps/add-application-portal).

Vous pouvez commencer à les gérer en procédant comme suit :

1. Tout d’abord, dans Azure AD, créez une stratégie d’accès conditionnel et configurez-la pour « Utiliser le contrôle d’application d’accès conditionnel ». Cette opération redirige la demande vers Defender pour Cloud Apps. Vous pouvez créer une stratégie et ajouter toutes les applications SaaS à cette stratégie.
1. Ensuite, dans Defender pour Cloud Apps, créez des stratégies de session. Créez une stratégie pour chaque contrôle que vous souhaitez appliquer.

Les autorisations sur les applications SaaS sont généralement basées sur les besoins de l’entreprise en matière d’accès à l’application. Ces autorisations peuvent être très dynamiques. L’utilisation de stratégies Defender pour Cloud Apps garantit la protection des données d’application, que les utilisateurs soient affectés à un groupe Azure AD associé à un point de départ, à une entreprise ou à une protection de sécurité spécialisée.

Pour protéger les données de votre collection d’applications SaaS, le diagramme suivant illustre la stratégie d’accès conditionnel Azure AD nécessaire, ainsi que les stratégies suggérées que vous pouvez créer dans Defender pour Cloud Apps. Dans cet exemple, les stratégies créées dans Defender pour Cloud Apps s’appliquent à toutes les applications SaaS que vous gérez. Elles sont conçues pour appliquer les contrôles appropriés en fonction de la gestion des appareils, ainsi que des étiquettes de confidentialité déjà appliquées aux fichiers.

:::image type="content" source="../../media/microsoft-365-policies-configurations/mcas-manage-saas-apps-2.png" alt-text="Stratégies de gestion des applications SaaS dans Defender pour Cloud Apps" lightbox="../../media/microsoft-365-policies-configurations/mcas-manage-saas-apps-2.png":::

Le tableau suivant répertorie la nouvelle stratégie d’accès conditionnel que vous devez créer dans Azure AD.

|Niveau de protection|Stratégie|Plus d’informations|
|---|---|---|
|Tous les niveaux de protection|[Utiliser le contrôle d’application d’accès conditionnel dans Defender pour les applications cloud](/cloud-app-security/proxy-deployment-aad#configure-integration-with-azure-ad)|Cela configure votre fournisseur d’identité (Azure AD) pour qu’il fonctionne avec Defender pour Cloud Apps.|
||||

Ce tableau suivant répertorie les exemples de stratégies illustrés ci-dessus que vous pouvez créer pour protéger toutes les applications SaaS. Veillez à évaluer vos propres objectifs d’entreprise, de sécurité et de conformité, puis créez des stratégies qui fournissent la protection la plus appropriée pour votre environnement.

|Niveau de protection|Stratégie|
|---|---|
|Point de départ|Surveiller le trafic à partir d’appareils non gérés <p> Ajouter une protection aux téléchargements de fichiers à partir d’appareils non gérés|
|Entreprise|Bloquer le téléchargement des fichiers étiquetés avec des données sensibles ou classifiées à partir d’appareils non gérés (cela fournit un accès au navigateur uniquement)|
|Sécurité spécialisée|Bloquer le téléchargement des fichiers étiquetés avec une classification à partir de tous les appareils (cela fournit un accès au navigateur uniquement)|
|||

Pour obtenir des instructions de bout en bout sur la configuration du contrôle d’application d’accès conditionnel, consultez [Déployer le contrôle d’application d’accès conditionnel pour les applications proposée](/cloud-app-security/proxy-deployment-aad). Cet article vous guide tout au long du processus de création de la stratégie d’accès conditionnel nécessaire dans Azure AD et de test de vos applications SaaS.

Pour plus d’informations, consultez [Protéger les applications avec Microsoft Defender for Cloud Apps contrôle d’application d’accès conditionnel](/cloud-app-security/proxy-intro-aad).

## <a name="tune-protection-for-specific-saas-apps"></a>Paramétrer la protection pour des applications SaaS spécifiques

Vous souhaiterez peut-être appliquer une surveillance et des contrôles supplémentaires à des applications SaaS spécifiques dans votre environnement. Defender pour Cloud Apps vous permet d’effectuer cette opération. Par exemple, si une application comme Box est largement utilisée dans votre environnement, il est judicieux d’appliquer des contrôles supplémentaires. Ou, si votre service juridique ou financier utilise une application SaaS spécifique pour les données métier sensibles, vous pouvez cibler une protection supplémentaire pour ces applications.

Par exemple, vous pouvez protéger votre environnement Box avec ces types de modèles de stratégie de détection d’anomalie intégrés :

- Activité provenant d’adresses IP anonymes
- Activité provenant d’un pays peu fréquent
- Activité provenant d’adresses IP suspectes
- Temps de trajet impossible
- Activité effectuée par l’utilisateur arrêté (nécessite AAD comme fournisseur d’identité)
- Détection des logiciels malveillants
- Plusieurs tentatives de connexion infructueuses
- Activité de rançongiciel
- Application Oauth risquée
- Activité de partage de fichiers inhabituelle

Il s’agit d’exemples. Des modèles de stratégie supplémentaires sont ajoutés régulièrement. Pour obtenir des exemples d’application d’une protection supplémentaire à des applications spécifiques, consultez [Protection des applications connectées](/cloud-app-security/protect-connected-apps).

[La façon dont Defender pour Cloud Apps contribue à protéger votre environnement Box](/cloud-app-security/protect-box) illustre les types de contrôles qui peuvent vous aider à protéger vos données métier dans Box et d’autres applications avec des données sensibles.

## <a name="configure-data-loss-prevention-dlp-to-help-comply-with-data-protection-regulations"></a>Configurer la protection contre la perte de données (DLP) pour vous aider à se conformer aux réglementations en matière de protection des données

Defender pour Cloud Apps peut être un outil précieux pour configurer la protection des réglementations de conformité. Dans ce cas, vous créez des stratégies spécifiques pour rechercher des données spécifiques auxquelles un règlement s’applique et configurez chaque stratégie pour qu’elle prenne les mesures appropriées.

L’illustration et le tableau suivants fournissent plusieurs exemples de stratégies qui peuvent être configurées pour aider à se conformer au Règlement général sur la protection des données (RGPD). Dans ces exemples, les stratégies recherchent des données spécifiques. En fonction de la sensibilité des données, chaque stratégie est configurée pour prendre les mesures appropriées.

:::image type="content" source="../../media/microsoft-365-policies-configurations/mcas-dlp.png" alt-text="Page Stratégies Defender pour Cloud Apps pour la protection contre la perte de données" lightbox="../../media/microsoft-365-policies-configurations/mcas-dlp.png":::

|Niveau de protection|Exemples de stratégies|
|---|---|
|Point de départ|Alerte lorsque les fichiers contenant ce type d’informations sensibles (« Numéro de carte de crédit ») sont partagés en dehors de l’organisation <p> >Bloquer les téléchargements de fichiers contenant ce type d’informations sensibles (« Numéro de carte de crédit ») sur les appareils non gérés|
|Entreprise|Protéger les téléchargements de fichiers contenant ce type d’informations sensibles (« Numéro de carte de crédit ») sur les appareils gérés <p> Bloquer les téléchargements de fichiers contenant ce type d’informations sensibles (« Numéro de carte de crédit ») sur des appareils non gérés <p> Alerte lorsqu’un fichier contenant ces étiquettes est chargé dans OneDrive Entreprise ou Box (données client, ressources humaines : données de salaire, ressources humaines, données d’employé)|
|Sécurité spécialisée|Alerte quand les fichiers portant cette étiquette (« Hautement classifié ») sont téléchargés sur des appareils gérés <p> Bloquer les téléchargements de fichiers avec cette étiquette (« Hautement classifié ») sur des appareils non gérés|
|||

## <a name="next-steps"></a>Prochaines étapes

Pour plus d’informations sur l’utilisation de Defender pour Cloud Apps, consultez [Microsoft Defender for Cloud Apps documentation](/defender-cloud-apps/).
