---
title: vue d Microsoft 365 Lighthouse de la page gestion des menaces
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez la page Gestion des menaces.
ms.openlocfilehash: e57163ba462e241c74a96db78fe701c024a037ff
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329876"
---
# <a name="microsoft-365-lighthouse-threat-management-page-overview"></a>vue d Microsoft 365 Lighthouse de la page gestion des menaces 

**S’applique à :**

- Windows 10

Antivirus Microsoft Defender les clients, les utilisateurs et les appareils contre les menaces logicielles, notamment les virus, les programmes malveillants et les logiciels espions. Il s’agit d’une protection robuste et continue intégrée à Windows 10 et incluse avec Microsoft 365 Business Premium et Microsoft365E3&nbsp;&nbsp;.  
  
Pour accéder à la page Gestion des menaces dans Microsoft 365 Lighthouse, sélectionnez Gestion des menaces dans le volet de navigation de gauche pour afficher la posture de sécurité de vos clients contre les menaces. Vous verrez des clients, des utilisateurs et des appareils qui nécessitent votre attention et des recommandations qui vous aideront à réduire les risques.  
  
## <a name="overview-tab"></a>Onglet Overview  
  
Sous l’onglet Vue d’ensemble de la page Gestion des menaces, vous pouvez surveiller l’état antivirus de tous vos locataires pour identifier les domaines qui doivent être surveillés.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-overview-tab.png" alt-text="Capture d’écran de l’onglet Vue d’ensemble.":::

## <a name="threats-tab"></a>Onglet Menaces

Sous l’onglet Menaces de la page Gestion des menaces, vous pouvez voir les menaces actives, atténuées, résolues et autorisées sur tous vos locataires. Vous pouvez également résoudre plusieurs menaces en même temps sur tous vos clients en filtrant et en explorant chaque menace pour savoir quels appareils, utilisateurs ou clients sont affectés.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-threats-tab.png" alt-text="Capture d’écran de la page de référence par défaut.":::
  
Vous pouvez filtrer les menaces en :

- État de la menace
- Gravité des menaces
- Type de menace
- Plage de dates

Le tableau suivant répertorie les différents états des menaces et leur définition :<br><br>

| État de la menace | Définition |
|--|--|
| Actif | La menace est active sur l’appareil. |
| Aucun état | L’état de la menace n’est pas disponible. Exécutez une analyse complète sur l’appareil pour Antivirus Microsoft Defender la menace. |
| Échec de l’action | L’appareil n’est pas en danger. Une action a échoué, mais une menace potentielle a été arrêtée et n’est pas active sur l’appareil. Exécutez une analyse complète sur l’appareil. |
| Étapes manuelles requises | La menace a été arrêtée, mais elle nécessite une étape manuelle, telle qu’une analyse complète ou un redémarrage de l’appareil. |
| Analyse complète requise | Une analyse complète de l’appareil est requise. |
| Redémarrage requis | Un redémarrage de l’appareil est requis. |
| Correction avec défaillances non critiques | La menace a été corrigé et aucune autre action n’est nécessaire. |
| Mis en quarantaine | La menace a été mise en quarantaine. Aucune autre action n’est nécessaire. |
| Supprimé | La menace a été correctement supprimée de l’appareil. Aucune autre action n’est nécessaire. |
| Nettoyé | Antivirus Microsoft Defender des fichiers récupérés et inextérés. Aucune autre action n’est nécessaire. |
| Autorisé | La menace est autorisée par un administrateur à rester sur l’appareil. | 

## <a name="antivirus-protection-tab"></a>Onglet Protection antivirus

L’onglet Protection antivirus de la page Gestion des menaces affiche les appareils sur tous vos locataires et leur état Antivirus Microsoft Defender protection. Vous pouvez évaluer l’état et prendre des mesures pour un ou plusieurs appareils qui peuvent être vulnérables. Vous pouvez également sélectionner un appareil pour afficher plus d’informations, telles que la vue d’ensemble de l’appareil, les menaces actuelles et les états d’action de l’appareil.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-antivirus-tab.png" alt-text="Capture d’écran de l’onglet Antivirus.":::

## <a name="related-content"></a>Contenu associé

[Déployer Microsoft 365 Lighthouse lignes de base](m365-lighthouse-deploy-baselines.md) (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)
