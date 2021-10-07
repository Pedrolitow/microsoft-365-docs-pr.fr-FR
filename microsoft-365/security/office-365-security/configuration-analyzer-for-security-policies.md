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
- M365-security-compliance
description: Les administrateurs peuvent apprendre à utiliser l’analyseur de configuration pour rechercher et corriger les stratégies de sécurité qui se trouvent sous les paramètres dans protection standard et protection stricte dans les stratégies de sécurité prédéfines.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b537da88199f9b565833c74fb94c233459970557
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60197916"
---
# <a name="configuration-analyzer-for-protection-policies-in-eop-and-microsoft-defender-for-office-365"></a>Analyseur de configuration des stratégies de protection dans EOP et Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

L’analyseur de configuration dans le portail Microsoft 365 Defender fournit un emplacement central pour rechercher et corriger les stratégies de sécurité où les paramètres sont inférieurs aux paramètres de profil de protection standard et strict dans les stratégies de sécurité prédéfines. [](preset-security-policies.md)

Les types de stratégies suivants sont analysés par l’analyseur de configuration :

- **Exchange Online Protection (EOP)**: cela inclut les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online et les organisations EOP autonomes Exchange Online boîtes aux lettres :
  - [Stratégies anti-courrier indésirable.](configure-your-spam-filter-policies.md)
  - [Stratégies anti-programme malveillant.](configure-anti-malware-policies.md)
  - [Stratégies anti-hameçonnage EOP](set-up-anti-phishing-policies.md#spoof-settings).

- **Stratégies de Microsoft Defender pour Office 365**: cela inclut les organisations avec des abonnements Microsoft 365 E5 ou Defender pour Office 365 de modules:
  - Stratégies anti-hameçonnage dans Microsoft Defender pour Office 365, qui incluent :
    - Paramètres [d’usurpation disponibles](set-up-anti-phishing-policies.md#spoof-settings) dans les stratégies anti-hameçonnage EOP.
    - [Paramètres d’emprunt d’identité](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Seuils d’hameçonnage avancés](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Stratégies de liens fiables](set-up-safe-links-policies.md).
  - [Stratégies de pièces jointes fiables](set-up-safe-attachments-policies.md).

Les valeurs de paramètre de stratégie Standard et Strict utilisées comme lignes de base sont décrites dans les [paramètres recommandés](recommended-settings-for-eop-and-office365.md)pour EOP et Microsoft Defender pour Office 365 sécurité.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour aller directement à la page de **l’analyseur de configuration,** utilisez <https://security.microsoft.com/configurationAnalyzer> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous être attribuées dans le portail Microsoft 365 Defender avant de pouvoir suivre les procédures de cet article :
  - Pour utiliser l’analyseur de configuration et mettre à jour les  stratégies de sécurité, vous devez être membre des groupes de rôles Gestion de l’organisation ou **Administrateur** de la sécurité. 
  - Pour l’accès en lecture seule à l’analyseur de configuration, vous devez être membre des groupes de rôles **Lecteur global** ou **Lecteur de sécurité**.

  Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

  > [!NOTE]
  >
  > - L’ajout d’utilisateurs au rôle Azure Active Directory leur donne les autorisations  requises dans le portail Microsoft 365 Defender et les autorisations pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  > - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

## <a name="use-the-configuration-analyzer-in-the-microsoft-365-defender-portal"></a>Utiliser l’analyseur de configuration dans le portail Microsoft 365 Defender client

Dans le portail Microsoft 365 Defender, go to **Email & Collaboration** Policies & \> **Rules** Threat \> **policies** \> **Configuration analyzer** in the **Templated policies** section.

La page **De l’analyseur de** configuration possède trois onglets principaux :

- **Recommandations standard**: comparez vos stratégies de sécurité existantes aux recommandations standard. Vous pouvez ajuster les valeurs de vos paramètres pour les faire monter au même niveau que Standard.
- **Recommandations strictes**: comparez vos stratégies de sécurité existantes aux recommandations strictes. Vous pouvez ajuster les valeurs de vos paramètres pour les faire monter au même niveau que Strict.
- **Analyse et historique de dérive de configuration**: auditer et suivre les modifications de stratégie au fil du temps.

### <a name="standard-recommendations-and-strict-recommendations-tabs-in-the-configuration-analyzer"></a>Recommandations standard et onglets Recommandations strictes dans l’analyseur de configuration

Par défaut, l’analyseur de configuration s’ouvre sous **l’onglet Recommandations standard.** Vous pouvez basculer vers **l’onglet Recommandations strictes.** Les paramètres, la disposition et les actions sont les mêmes sur les deux onglets.

![Paramètres et recommandations dans l’analyseur de configuration.](../../media/configuration-analyzer-settings-and-recommendations-view.png)

La première section de l’onglet affiche le nombre de paramètres de chaque type de stratégie qui ont besoin d’être améliorés par rapport à protection standard ou stricte. Les types de stratégies sont :

- **Anti-courrier indésirable**
- **Anti-hameçonnage**
- **Anti-programme malveillant**
- **Coffre pièces jointes** (si votre abonnement inclut Microsoft Defender pour Office 365)
- **Coffre liens** (si votre abonnement inclut Microsoft Defender pour Office 365)

Si un type et un numéro de stratégie ne sont pas affichés, toutes vos stratégies de ce type répondent aux paramètres recommandés de protection standard ou stricte.

Le reste de l’onglet est le tableau des paramètres qui doivent être élevés au niveau Standard ou Strict Protection. Le tableau contient les colonnes suivantes :

- **Recommendations**: la valeur du paramètre dans le profil de protection Standard ou Strict.
- **Stratégie**: le nom de la stratégie affectée qui contient le paramètre.
- **Nom du groupe/paramètre de stratégie**: le nomdu paramètre qui nécessite votre attention.
- **Type de stratégie**: Anti-spam, Anti-phishing, Anti-malware, Coffre Links ou Coffre Attachments.
- **Configuration actuelle**: valeur actuelle du paramètre.
- **Dernière modification**: la date de la dernière modification de la stratégie.
- **État**: en règle générale, cette valeur **n’est pas démarrée.**

### <a name="change-a-policy-setting-to-the-recommended-value"></a>Définir un paramètre de stratégie sur la valeur recommandée

Sous **l’onglet Protection standard** ou **Protection stricte** de l’analyseur de configuration, sélectionnez la ligne dans le tableau. Les boutons suivants s’affichent :

- **Appliquer une recommandation**
- **Afficher la stratégie**
- **Actualiser**:

Si vous sélectionnez une ligne et cliquez sur Appliquer **la recommandation,** une boîte de dialogue de confirmation (avec la possibilité de ne plus afficher la boîte de dialogue) s’affiche. Si vous cliquez sur **OK,** les choses suivantes se produisent :

- Le paramètre est mis à jour à la valeur recommandée.
- La **stratégie Appliquer la recommandation** et **Afficher** disparaît (seul le bouton **Actualiser** reste).
- La **valeur d’état** de la ligne est **terminée.**

Si vous sélectionnez  une ligne et cliquez sur Afficher la stratégie, vous êtes conduit au volant des détails de la stratégie concernée dans le portail Microsoft 365 Defender où vous pouvez mettre à jour manuellement le paramètre.

Après avoir automatiquement ou manuellement mis  à jour le paramètre, cliquez sur Actualiser pour voir le nombre réduit de recommandations et la suppression de la ligne mise à jour des résultats.

### <a name="configuration-drift-analysis-and-history-tab-in-the-configuration-analyzer"></a>Onglet Analyse de dérive de configuration et historique dans l’analyseur de configuration

Cet onglet vous permet d’assurer le suivi des modifications apportées à vos stratégies de sécurité et de comparer ces modifications aux paramètres Standard ou Strict. Par défaut, les informations suivantes sont affichées:

- **Dernière modification**
- **Modifié par**
- **Nom du paramètre**
- **Stratégie**: nom de la stratégie concernée.
- **Type**: Anti-spam, Anti-phishing, Anti-malware, Coffre Links, or Coffre Attachments.
- **Modification de configuration**: l’ancienne valeur et la nouvelle valeur du paramètre
- **Dérive de configuration**:  valeur **d’augmentation** ou de diminution qui indique que le paramètre a augmenté ou diminué la sécurité par rapport au paramètre Standard ou Strict recommandé.

Pour filtrer les résultats, cliquez sur **Filtrer**. Dans le menu volant **Filtres** qui s’affiche, vous pouvez sélectionner parmi les filtres suivants:

- **Heure de** début et **heure de fin** (date) : vous pouvez revenir à 90 jours à partir d’aujourd’hui.
- **Protection standard** ou **protection stricte**

Lorsque vous avez terminé, cliquez sur **Appliquer**.

Pour exporter les résultats vers un fichier .csv, cliquez sur **Exporter.**

Pour filtrer les résultats en fonction d’une modification spécifique par **,** **nom de paramètre** ou valeur de **type,** utilisez la **zone de** recherche.

![Analyse de dérive de configuration et affichage historique dans l’analyseur de configuration.](../../media/configuration-analyzer-configuration-drift-analysis-view.png)
