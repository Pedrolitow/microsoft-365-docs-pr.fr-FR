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
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à utiliser l’analyseur de configuration pour rechercher et corriger les stratégies de sécurité qui se trouvent en dessous des stratégies de sécurité prédéfines Protection standard et Protection stricte.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0d2ad1449730f392adc27c8ed2a8fc8e9ecc7a04
ms.sourcegitcommit: b09aee96a1e2266b33ba81dfe497f24c5300bb56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2021
ms.locfileid: "52789301"
---
# <a name="configuration-analyzer-for-protection-policies-in-eop-and-microsoft-defender-for-office-365"></a>Analyseur de configuration des stratégies de protection dans EOP et Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

L’analyseur de configuration dans le centre de sécurité Microsoft 365 fournit un emplacement central pour rechercher et corriger [](preset-security-policies.md)les stratégies de sécurité où les paramètres se trouvent en dessous des paramètres de profil de protection standard et strict dans les stratégies de sécurité prédéfines.

Les types de stratégies suivants sont analysés par l’analyseur de configuration :

- **Exchange Online Protection (EOP)**: cela inclut les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online et les organisations EOP autonomes Exchange Online boîtes aux lettres :

  - [Stratégies anti-courrier indésirable.](configure-your-spam-filter-policies.md)
  - [Stratégies anti-programme malveillant.](configure-anti-malware-policies.md)
  - [Stratégies anti-hameçonnage EOP](set-up-anti-phishing-policies.md#spoof-settings).

- **Stratégies de Microsoft Defender pour Office 365**: cela inclut les organisations avec des abonnements Microsoft 365 E5 ou Defender pour Office 365 de modules:

  - Stratégies anti-hameçonnage dans Microsoft Defender pour Office 365, qui incluent :
    - Paramètres [d’usurpation disponibles](set-up-anti-phishing-policies.md#spoof-settings) dans les stratégies anti-hameçonnage EOP.
    - [Paramètres d’emprunt d’identité](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Seuils de hameçonnage avancés](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Stratégies de liens sécurisés](set-up-safe-links-policies.md).
  - [Stratégies de pièces jointes sécurisées](set-up-safe-attachments-policies.md).

Les **valeurs de** paramètre de stratégie Standard et **Strict** utilisées comme lignes de base sont décrites dans les [paramètres recommandés](recommended-settings-for-eop-and-office365.md)pour EOP et Microsoft Defender pour Office 365 sécurité.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le centre de sécurité à <https://security.microsoft.com>. Pour aller directement à la page de **l’analyseur de configuration,** utilisez <https://security.microsoft.com/configurationAnalyzer> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous être attribuées dans le centre de sécurité avant de pouvoir suivre les procédures de cet article :
  - Pour utiliser l’analyseur de configuration et mettre à jour les  stratégies de sécurité, vous devez être membre des groupes de rôles Gestion de l’organisation ou **Administrateur** de la sécurité. 
  - Pour un accès en lecture seule à l’analyseur  de configuration, vous devez être membre des groupes de rôles Lecteur global ou Lecteur de sécurité. 

  Pour plus d’informations, [voir Autorisations dans le centre Microsoft 365 de sécurité.](permissions-microsoft-365-security-center.md)

  > [!NOTE]
  >  
  > - L’ajout d’utilisateurs au rôle de Azure Active Directory donne aux  utilisateurs les autorisations requises dans le centre de sécurité et les autorisations pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  >
  > - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

## <a name="use-the-configuration-analyzer-in-the-security-center"></a>Utiliser l’analyseur de configuration dans le centre de sécurité

Dans le centre de sécurité, go to **Email & collaboration** Policies & \> **rules** Threat \> **policies** \> **Templated policies** section Configuration \> **analyzer**.

L’analyseur de configuration possède deux onglets principaux :

- **Paramètres recommandations**: vous choisissez **Standard** ou **Strict** et comparez ces paramètres à vos stratégies de sécurité existantes. Dans les résultats, vous pouvez ajuster les valeurs de vos paramètres pour les faire monter au même niveau que Standard ou Strict.
- **Analyse et historique de dérive de configuration**: cet affichage vous permet de suivre les modifications de stratégie au fil du temps.

### <a name="setting-and-recommendations-tab-in-the-configuration-analyzer"></a>Onglet Paramètres et recommandations dans l’analyseur de configuration

Par défaut, l’onglet s’ouvre dans la comparaison au profil de protection standard. Vous pouvez basculer vers la comparaison du profil De protection stricte en sélectionnant **Afficher les recommandations strictes.** Pour revenir en arrière, **sélectionnez Afficher les recommandations standard.**

![Paramètres et recommandations dans l’analyseur de configuration](../../media/configuration-analyzer-settings-and-recommendations-view.png)

Par défaut, la colonne Nom de **groupe/paramètre** de stratégie contient une vue d’ensemble des différents types de stratégies de sécurité et du nombre de paramètres qui doivent être améliorés (le cas nécessaire). Les types de stratégies sont :

- **Anti-courrier indésirable**
- **Anti-hameçonnage**
- **Anti-programme malveillant**
- **Pièces jointes sécurisées** (si votre abonnement inclut Microsoft Defender pour Office 365)
- **Liens sécurisés** (si votre abonnement inclut Microsoft Defender pour Office 365)

Dans l’affichage par défaut, tout est réduire. En regard de chaque stratégie, il existe un résumé des résultats de comparaison de vos stratégies (que vous pouvez modifier) et des paramètres dans les stratégies correspondantes pour les profils de protection standard ou strict (que vous ne pouvez pas modifier). Vous verrez les informations suivantes pour le profil de protection que vous comparez :

- **Vert**: tous les paramètres de toutes les stratégies existantes sont au moins aussi sécurisés que le profil de protection.
- **Orange**: un petit nombre de paramètres dans les stratégies existantes ne sont pas aussi sécurisés que le profil de protection.
- **Rouge**: un nombre important de paramètres dans les stratégies existantes ne sont pas aussi sécurisés que le profil de protection. Il peut s’agit de quelques paramètres dans de nombreuses stratégies ou de nombreux paramètres dans une stratégie.

Pour des comparaisons favorables, vous verrez le texte : Tous les **paramètres suivent** \<**Standard** or **Strict**\> **les recommandations.** Dans le cas contraire, vous verrez le nombre de paramètres recommandés à modifier.

Si vous développez **le nom du groupe/paramètre** de stratégie, toutes les stratégies et les paramètres associés dans chaque stratégie spécifique nécessitant une attention particulière sont révélés. Vous pouvez également développer un type spécifique de stratégie (par exemple, **anti-courrier** indésirable) pour voir uniquement ces paramètres dans les types de stratégies qui nécessitent votre attention.

Si la comparaison n’a aucune recommandation d’amélioration (vert), l’extension de la stratégie ne révèle rien. S’il existe un certain nombre de recommandations d’amélioration (orange ou rouge), les paramètres qui nécessitent une attention particulière sont révélés et les informations correspondantes sont révélées dans les colonnes suivantes :

- **Nom du groupe/paramètre de stratégie**: nom du paramètre qui nécessite votre attention. Par exemple, dans la capture d’écran précédente, il s’agit des paramètres de la stratégie anti-courrier indésirable par défaut.
- **Stratégie**: nom de la stratégie concernée qui contient le paramètre.
- **Appliqué à**: nombre d’utilisateurs à qui les stratégies affectées sont appliquées.
- **Configuration actuelle**: valeur actuelle du paramètre. Pour la stratégie par défaut de ce type qui s’applique à tous les destinataires, cette valeur est vide.
- **Dernière modification**: date de la dernière modification de la stratégie.
- **Recommandations**: valeur du paramètre dans le profil de protection Standard ou Strict. Pour modifier la valeur du paramètre dans votre stratégie afin qu’elle corresponde à la valeur recommandée dans le profil de protection, cliquez sur **Adopter**. Si la modification réussit, le message suivant s’Recommandations **correctement adopté.** Cliquez **sur** Actualiser pour voir le nombre réduit de recommandations et la suppression de la ligne de paramètre/stratégie spécifique des résultats.

### <a name="configuration-drift-analysis-and-history-tab-in-the-configuration-analyzer"></a>Analyse de dérive de configuration et onglet Historique dans l’analyseur de configuration

Cet onglet vous permet de suivre les modifications que vous avez apportées à vos stratégies de sécurité personnalisées. Par défaut, les informations suivantes s’affichent :

- **Dernière modification**
- **Modifié par**
- **Nom du paramètre**
- **Policy**
- **Type**
- **Modification de configuration**
- **Dérive de configuration**: la valeur **Augmente ou** **Diminue**.

Pour filtrer les résultats, cliquez sur **Filtrer**. Dans le volant **Filtres** qui s’affiche, vous pouvez choisir parmi les filtres suivants :

- **Heure de début** **et heure de fin** (date)
- **Protection standard** ou **protection stricte**

Pour exporter les résultats vers un fichier .csv, cliquez sur **Exporter.**

![Analyse de dérive de configuration et affichage historique dans l’analyseur de configuration](../../media/configuration-analyzer-configuration-drift-analysis-view.png)
