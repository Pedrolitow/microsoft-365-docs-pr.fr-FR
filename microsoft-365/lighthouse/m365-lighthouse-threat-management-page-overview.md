---
title: Vue d’ensemble de la page Gestion des menaces dans Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: algreer
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez la page gestion des menaces.
ms.openlocfilehash: aeaa240e940e12782c194e0f718031f74b4ba867
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68191648"
---
# <a name="overview-of-the-threat-management-page-in-microsoft-365-lighthouse"></a>Vue d’ensemble de la page Gestion des menaces dans Microsoft 365 Lighthouse 

**S’applique à :**

- Windows

Microsoft Defender Antivirus protège les locataires, les utilisateurs et les appareils contre les menaces logicielles, notamment les virus, les programmes malveillants et les logiciels espions. Il s’agit d’une protection robuste et continue intégrée à Windows.  
  
Pour accéder à la page Gestion des menaces dans Microsoft 365 Lighthouse, sélectionnez **Gestion des menaces** **des appareils** >  dans le volet de navigation gauche pour afficher la posture de sécurité de vos locataires clients contre les menaces. Vous verrez des locataires, des utilisateurs et des appareils qui nécessitent votre attention et des recommandations qui vous aideront à réduire les risques.  
  
## <a name="overview-tab"></a>Onglet Overview  
  
Sous l’onglet Vue d’ensemble de la page Gestion des menaces, vous pouvez surveiller l’état de l’antivirus sur tous vos locataires pour identifier les zones qui nécessitent une attention particulière.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-overview-tab.png" alt-text="Capture d’écran de l’onglet Vue d’ensemble.":::

## <a name="threats-tab"></a>Onglet Menaces

Sous l’onglet Menaces de la page Gestion des menaces, vous pouvez voir les menaces actives, atténuées, résolues et autorisées sur tous vos locataires. Vous pouvez également corriger plusieurs menaces en même temps sur tous vos locataires en filtrant et en explorant chaque menace pour savoir quels appareils, utilisateurs ou locataires sont affectés.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-threats-tab.png" alt-text="Capture d’écran de la page De référence par défaut.":::
  
Vous pouvez filtrer les menaces en :

- État de la menace
- Gravité des menaces
- Type de menace
- Plage de dates

Le tableau suivant répertorie les différents états de menace et leur définition :<br><br>

| État de la menace | Définition |
|---|---|
| Actif | La menace est active sur l’appareil. |
| Aucun état | L’état de la menace n’est pas disponible. Exécutez une analyse complète sur l’appareil pour que Microsoft Defender Antivirus redéecte la menace. |
| Échec de l’action | L’appareil n’est pas à risque. Une action a échoué, mais une menace potentielle a été arrêtée et n’est pas active sur l’appareil. Exécutez une analyse complète sur l’appareil. |
| Étapes manuelles requises | La menace a été arrêtée, mais elle nécessite une étape manuelle, telle qu’une analyse complète ou un redémarrage de l’appareil. |
| Analyse complète requise | Une analyse complète de l’appareil est nécessaire. |
| Redémarrage requis | Un redémarrage de l’appareil est nécessaire. |
| Corrigé avec des échecs non critiques | La menace a été corrigée et aucune autre action n’est nécessaire. |
| Quarantaine | La menace a été mise en quarantaine. Aucune autre action n’est nécessaire. |
| Supprimé | La menace a été supprimée de l’appareil. Aucune autre action n’est nécessaire. |
| Nettoyé | Microsoft Defender Antivirus a récupéré et désinfecté des fichiers. Aucune autre action n’est nécessaire. |
| Autorisé | La menace est autorisée par un administrateur à rester sur l’appareil. | 

## <a name="antivirus-protection-tab"></a>Onglet Protection antivirus

L’onglet Protection antivirus de la page gestion des menaces affiche les appareils de tous vos locataires et leur état de protection antivirus Microsoft Defender. Vous pouvez évaluer l’état et prendre des mesures pour un ou plusieurs appareils susceptibles d’être vulnérables. Vous pouvez également sélectionner un appareil pour afficher plus d’informations, telles que Vue d’ensemble de l’appareil, Menaces actuelles et État de l’action de l’appareil.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-antivirus-tab.png" alt-text="Capture d’écran de l’onglet Antivirus.":::

## <a name="related-content"></a>Contenu associé

[Déployer Microsoft 365 Lighthouse lignes de base](m365-lighthouse-deploy-baselines.md) (article)\
[MICROSOFT 365 LIGHTHOUSE FAQ](m365-lighthouse-faq.yml) (article)
