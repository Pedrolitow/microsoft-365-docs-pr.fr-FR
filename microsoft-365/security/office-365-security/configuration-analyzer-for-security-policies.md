---
title: Analyseur de configuration pour les stratégies de sécurité
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- m365-security
ms.custom: ''
description: Les administrateurs peuvent apprendre à utiliser l’analyseur de configuration pour rechercher et corriger les stratégies de sécurité qui se trouvent sous les paramètres de protection standard et de protection stricte dans les stratégies de sécurité prédéfinies.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 1d53ee6b0eb163be2552eee42ed4851520b62f98
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68069092"
---
# <a name="configuration-analyzer-for-protection-policies-in-eop-and-microsoft-defender-for-office-365"></a>Analyseur de configuration pour les stratégies de protection dans EOP et Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

L’analyseur de configuration dans le portail Microsoft 365 Defender fournit un emplacement central pour rechercher et corriger les stratégies de sécurité où les paramètres sont inférieurs aux paramètres de protection standard et de profil de protection stricte dans les [stratégies de sécurité prédéfinies](preset-security-policies.md).

Les types de stratégies suivants sont analysés par l’analyseur de configuration :

- **stratégies Exchange Online Protection (EOP)** : cela inclut les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online et des organisations EOP autonomes sans boîtes aux lettres Exchange Online :
  - [Stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).
  - [Stratégies anti-programme malveillant](configure-anti-malware-policies.md).
  - [Stratégies anti-hameçonnage EOP](set-up-anti-phishing-policies.md#spoof-settings).

- **Microsoft Defender pour Office 365 stratégies** : cela inclut les organisations avec des abonnements Microsoft 365 E5 ou Defender pour Office 365 module complémentaire :
  - Stratégies anti-hameçonnage dans Microsoft Defender pour Office 365, notamment :
    - Paramètres [d’usurpation d’identité disponibles](set-up-anti-phishing-policies.md#spoof-settings) dans les stratégies anti-hameçonnage EOP.
    - [Paramètres d’emprunt d’identité](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Seuils d’hameçonnage avancés](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Stratégies de liens fiables](set-up-safe-links-policies.md).
  - [Stratégies de pièces jointes fiables](set-up-safe-attachments-policies.md).

Les valeurs des paramètres de stratégie Standard et Strict utilisées comme lignes de base sont [décrites dans les paramètres recommandés pour EOP et Microsoft Defender pour Office 365 sécurité](recommended-settings-for-eop-and-office365.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Analyseur de configuration** , utilisez <https://security.microsoft.com/configurationAnalyzer>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Vous devez disposer d’autorisations dans le portail Microsoft 365 Defender avant de pouvoir effectuer les procédures décrites dans cet article :
  - Pour utiliser l’analyseur de configuration **et** mettre à jour les stratégies de sécurité, vous devez être membre des groupes de **rôles Gestion de l’organisation** ou **Administrateur de la sécurité** .
  - Pour l’accès en lecture seule à l’analyseur de configuration, vous devez être membre des groupes de rôles **Lecteur global** ou **Lecteur de sécurité**.

  Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

  > [!NOTE]
  >
  > - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant donne aux utilisateurs les autorisations requises dans le portail Microsoft 365 Defender _et_ les autorisations pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  > - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

## <a name="use-the-configuration-analyzer-in-the-microsoft-365-defender-portal"></a>Utiliser l’analyseur de configuration dans le portail Microsoft 365 Defender

Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & **Analyseur** de configuration des stratégies de **collaboration** \> **& des stratégies** de **menace** \> de règles \> dans la section **Stratégies modèles**. Pour accéder directement à la page **Analyseur de configuration** , utilisez <https://security.microsoft.com/configurationAnalyzer>.

La page **Analyseur de configuration** comporte trois onglets principaux :

- **Recommandations standard** : comparez vos stratégies de sécurité existantes aux recommandations standard. Vous pouvez ajuster vos valeurs de paramètres pour les élever au même niveau que Standard.
- **Recommandations strictes** : comparez vos stratégies de sécurité existantes aux recommandations strictes. Vous pouvez ajuster vos valeurs de paramètres pour les élever au même niveau que Strict.
- **Analyse et historique des dérives de configuration** : auditez et suivez les modifications de stratégie au fil du temps.

### <a name="standard-recommendations-and-strict-recommendations-tabs-in-the-configuration-analyzer"></a>Recommandations standard et onglets Recommandations strictes dans l’analyseur de configuration

Par défaut, l’analyseur de configuration s’ouvre sous l’onglet **Recommandations standard** . Vous pouvez passer à l’onglet **Recommandations strictes** . Les paramètres, la disposition et les actions sont les mêmes sur les deux onglets.

:::image type="content" source="../../media/configuration-analyzer-settings-and-recommendations-view.png" alt-text="Vue Paramètres et recommandations dans l’analyseur de configuration" lightbox="../../media/configuration-analyzer-settings-and-recommendations-view.png":::

La première section de l’onglet affiche le nombre de paramètres dans chaque type de stratégie qui doivent être améliorés par rapport à la protection Standard ou Strict. Les types de stratégies sont les suivants :

- **Anti-spam**
- **Anti-hameçonnage**
- **Anti-programme malveillant**
- **Pièces jointes sécurisées** (si votre abonnement inclut Microsoft Defender pour Office 365)
- **Liens sécurisés** (si votre abonnement inclut Microsoft Defender pour Office 365)

Si aucun type et numéro de stratégie ne s’affichent, toutes vos stratégies de ce type respectent les paramètres recommandés de protection Standard ou Strict.

Le reste de l’onglet est la table des paramètres qui doivent être élevés au niveau de protection Standard ou Strict. Le tableau contient les colonnes suivantes :

- **Recommendations**: la valeur du paramètre dans le profil de protection Standard ou Strict.
- **Stratégie**: le nom de la stratégie affectée qui contient le paramètre.
- **Nom du groupe/paramètre de stratégie**: le nomdu paramètre qui nécessite votre attention.
- **Type de stratégie** : anti-courrier indésirable, anti-hameçonnage, anti-programme malveillant, liens sécurisés ou pièces jointes sécurisées.
- **Configuration actuelle** : valeur actuelle du paramètre.
- **Dernière modification**: la date de la dernière modification de la stratégie.
- **État** : en règle générale, cette valeur **n’est pas démarrée**.

### <a name="change-a-policy-setting-to-the-recommended-value"></a>Remplacer un paramètre de stratégie par la valeur recommandée

Sous l’onglet **Protection standard** ou **Protection stricte** de l’analyseur de configuration, sélectionnez la ligne dans le tableau. Les boutons suivants s’affichent :

- **Appliquer une recommandation**
- **Afficher la stratégie**
- **Actualiser** :

Si vous sélectionnez une ligne et cliquez sur **Appliquer la recommandation**, une boîte de dialogue de confirmation (avec l’option de ne plus afficher la boîte de dialogue) s’affiche. Si vous cliquez sur **OK**, les choses suivantes se produisent :

- Le paramètre est mis à jour avec la valeur recommandée.
- La **stratégie Appliquer la recommandation** et **l’affichage** disparaissent (seul le bouton **Actualiser** reste).
- La valeur **d’état** de la ligne devient **Complete**.

Si vous sélectionnez une ligne et cliquez sur **Afficher la stratégie**, vous accédez au menu volant des détails de la stratégie affectée dans le portail Microsoft 365 Defender où vous pouvez mettre à jour manuellement le paramètre.

Après avoir mis à jour automatiquement ou manuellement le paramètre, cliquez sur **Actualiser** pour afficher le nombre réduit de recommandations et la suppression de la ligne mise à jour des résultats.

### <a name="configuration-drift-analysis-and-history-tab-in-the-configuration-analyzer"></a>Onglet Analyse de dérive de configuration et historique dans l’analyseur de configuration

Cet onglet vous permet de suivre les modifications apportées à vos stratégies de sécurité et de comparer ces modifications aux paramètres Standard ou Strict. Par défaut, les informations suivantes sont affichées:

- **Dernière modification**
- **Modifié par**
- **Nom du paramètre**
- **Stratégie** : nom de la stratégie affectée.
- **Type** : Anti-spam, anti-hameçonnage, anti-programme malveillant, liens sécurisés ou pièces jointes sécurisées.
- **Modification de la configuration** : ancienne valeur et nouvelle valeur du paramètre
- **Dérive de configuration** : valeur **Augmentation** ou **diminution** qui indique que le paramètre a augmenté ou diminué la sécurité par rapport au paramètre Standard ou Strict recommandé.

Pour filtrer les résultats, cliquez sur **Filtrer**. Dans le menu volant **Filtres** qui s’affiche, vous pouvez sélectionner parmi les filtres suivants:

- **Heure de début** et **heure de fin** (date) : vous pouvez remonter jusqu’à 90 jours à partir d’aujourd’hui.
- **Protection standard** ou **protection stricte**

Lorsque vous avez terminé, cliquez sur **Appliquer**.

Pour exporter les résultats dans un fichier .csv, cliquez sur **Exporter**.

Pour filtrer les résultats en fonction d’une **valeur** **de** type, **de nom de paramètre** ou de modification spécifique, utilisez la zone **de recherche**.

:::image type="content" source="../../media/configuration-analyzer-configuration-drift-analysis-view.png" alt-text="Vue Analyse de dérive de configuration et historique dans l’analyseur de configuration" lightbox="../../media/configuration-analyzer-configuration-drift-analysis-view.png":::
