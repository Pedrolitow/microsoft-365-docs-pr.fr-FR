---
title: Configuration Analyzer pour les stratégies de sécurité
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à utiliser l’analyseur de configuration pour rechercher et corriger des stratégies de sécurité qui contiennent des paramètres inférieurs aux stratégies de sécurité standard protection prédéfinie protection et protection stricte.
ms.openlocfilehash: 4515efcd73d40eae93523c6ef139553420e48677
ms.sourcegitcommit: e12fa502bc216f6083ef5666f693a04bb727d4df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "46825772"
---
# <a name="configuration-analyzer-for-protection-policies-in-eop-and-office-365-atp"></a>Configuration Analyzer pour les stratégies de protection dans EOP et Office 365 ATP

> [!NOTE]
> Les fonctionnalités décrites dans cette rubrique sont en aperçu, ne sont pas disponibles dans toutes les organisations et peuvent faire l’objet de modifications.

Configuration Analyzer dans le centre de sécurité & conformité fournit un emplacement central pour rechercher et corriger toutes vos stratégies de sécurité qui contiennent des paramètres inférieurs aux paramètres de profil de protection standard et de profil de protection stricte dans les [stratégies de sécurité prédéfinies](preset-security-policies.md).

Les types de stratégies suivants sont analysés par l’analyseur de configuration :

- **Stratégies Exchange Online Protection (EoP)**: cela inclut les organisations Microsoft 365 avec les boîtes aux lettres Exchange Online et les organisations EOP autonomes sans boîtes aux lettres Exchange Online :
  
  - [Stratégies de blocage du courrier indésirable](configure-your-spam-filter-policies.md).
  - [Stratégies de protection contre les programmes malveillants](configure-anti-malware-policies.md).
  - [Stratégies de hameçonnage d’EOP](set-up-anti-phishing-policies.md#spoof-settings).

- **Stratégies Office 365 Advanced Threat Protection (ATP)**: cela inclut les organisations avec les abonnements complémentaires Microsoft 365 E5 ou Office 365 ATP :

  - Stratégies anti-hameçonnage ATP, qui incluent :

    - Les mêmes [paramètres d’usurpation](set-up-anti-phishing-policies.md#spoof-settings) qui sont disponibles dans les stratégies anti-hameçonnage EOP.
    - [Paramètres d’emprunt d’identité](set-up-anti-phishing-policies.md#impersonation-settings-in-atp-anti-phishing-policies)
    - [Seuils de hameçonnage avancés](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-atp-anti-phishing-policies)

  - [Stratégies de liens fiables](recommended-settings-for-eop-and-office365-atp.md#safe-links-policy-settings-in-custom-policies-for-specific-users).

  - [Stratégies de pièces jointes approuvées](recommended-settings-for-eop-and-office365-atp.md#safe-attachments-policy-settings-in-custom-policies-for-specific-users).

Les valeurs de paramètres de stratégie **standard** et **strictes** utilisées comme configurations de référence sont décrites dans [paramètres recommandés pour la sécurité de l’ATP et d’Office 365](recommended-settings-for-eop-and-office365-atp.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page de l' **Analyseur de configuration** , utilisez <https://protection.office.com/configurationAnalyzer> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces procédures. décrites dans cette rubrique :

  - Pour utiliser l’analyseur de configuration **et** mettre à jour les stratégies de sécurité, vous devez être membre de l’un des groupes de rôles suivants :

    - **Gestion de l’organisation** ou **Administrateur de sécurité** dans le [Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).
    - **Gestion de l’organisation** ou **Gestion de l’hygiène** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups).

  - Pour un accès en lecture seule à Configuration Analyzer, vous devez être membre de l’un des groupes de rôles suivants :

    - **Lecteur de sécurité** dans le [Centre de conformité et sécurité](permissions-in-the-security-and-compliance-center.md).
    - **Gestion de l’organisation en affichage seul** dans[Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups).

## <a name="use-the-configuration-analyzer-in-the-security--compliance-center"></a>Utiliser l’analyseur de configuration dans le centre de sécurité & conformité

Dans le centre de sécurité & conformité, accédez à **Threat Management** \> **Policy** \> **Analyzer**.

![Widget Configuration Analyzer sur la page de stratégie de gestion des menaces \>](../../media/configuration-analyzer-widget.png)

L’analyseur de configuration comporte deux onglets principaux :

- **Paramètres et recommandations**: sélectionnez standard ou strict et Comparez ces paramètres à vos stratégies de sécurité existantes. Dans les résultats, vous pouvez ajuster les valeurs de vos paramètres pour les ramener au même niveau que standard ou strict.

- **Analyse et historique de dérive de configuration**: cette vue permet de suivre les modifications que vous avez apportées à vos stratégies en fonction des résultats de l’analyseur de configuration au fil du temps.

### <a name="setting-and-recommendations-tab-in-the-configuration-analyzer"></a>Onglet définition et recommandations de l’analyseur de configuration

Par défaut, l’onglet s’ouvre sur la comparaison avec le profil de protection standard. Vous pouvez passer à la comparaison du profil de protection strict en cliquant sur **Afficher rigoureuse Recommendations**. Pour revenir en arrière, sélectionnez **afficher les recommandations standard**.

![Vue paramètres et recommandations dans l’analyseur de configuration](../../media/configuration-analyzer-settings-and-recommendations-view.png)

Par défaut, la colonne **groupe de stratégies/nom du paramètre** contient une vue réduite des différents types de stratégies de sécurité et le nombre de paramètres dans ces stratégies qui doivent être améliorés (le cas échéant). Les types de stratégies sont les suivants :

- **Anti-spam**
- **Anti-hameçonnage**
- **Anti-programme malveillant**
- **Pièces jointes sûres ATP** (si votre abonnement inclut ATP)
- **Liens fiables ATP** (si votre abonnement inclut ATP)

Dans l’affichage par défaut, tout est réduit. En regard de chaque stratégie, un résumé des résultats de la comparaison de vos stratégies (que vous pouvez modifier) et les paramètres des stratégies correspondantes pour les profils de protection standard ou stricte (que vous ne pouvez pas modifier) s’affichent. Les informations suivantes s’affichent :

- **Vert**: tous les paramètres de toutes les stratégies existantes sont au moins aussi sécurisés que le profil de protection auquel vous effectuez une comparaison.
- **Orange**: un petit nombre de paramètres dans les stratégies existantes n’est pas aussi sécurisé que le profil de protection auquel vous effectuez une comparaison.
- **Rouge**: un nombre significatif de paramètres dans les stratégies existantes n’est pas aussi sécurisé que le profil de protection auquel vous effectuez une comparaison. Il peut s’agir de quelques paramètres dans de nombreuses stratégies ou de nombreux paramètres dans une stratégie.

Pour les comparaisons favorables, vous verrez le texte : **tous les paramètres suivent** les \<**Standard** or **Strict**\> **recommandations**. Dans le cas contraire, vous verrez le nombre de paramètres recommandés à modifier.

Si vous développez le **nom du groupe de stratégies/du paramètre**, toutes les stratégies et les paramètres associés dans chaque stratégie spécifique nécessitant une attention sont révélés. Vous pouvez également développer un type spécifique de stratégie (par exemple, le **blocage du courrier indésirable**) pour afficher uniquement ces paramètres dans ces types de stratégies qui nécessitent votre attention.

Si la comparaison n’a pas de recommandations d’amélioration (en vert), le développement de la stratégie n’indique rien. S’il existe un nombre de recommandations pour l’amélioration (jaune ou rouge), les paramètres nécessitant une attention sont révélés, et les informations correspondantes sont révélées dans les colonnes suivantes :

- Nom du paramètre qui requiert votre attention. Par exemple, dans la capture d’écran précédente, il s’agit du **seuil de courrier électronique en bloc** dans une stratégie de blocage du courrier indésirable.

- **Stratégie**: nom de la stratégie concernée qui contient le paramètre.

- **Appliqué à**: le nombre d’utilisateurs auxquels les stratégies affectées sont appliquées.

- **Configuration actuelle**: valeur actuelle du paramètre.

- **Dernière modification**: date de la dernière modification de la stratégie.

- **Recommandations**: valeur du paramètre dans le profil de protection standard ou strict. Pour modifier la valeur du paramètre dans votre stratégie pour qu’elle corresponde à la valeur recommandée dans le profil de protection, cliquez sur **adopter**. Si la modification réussit, vous verrez le message suivant : **recommandations correctement adoptées**. Cliquez sur **Actualiser** pour afficher le nombre réduit de recommandations, ainsi que la suppression de la ligne de paramètre/stratégie spécifique des résultats.

### <a name="configuration-drift-analysis-and-history-tab-in-the-configuration-analyzer"></a>Onglet analyse de dérive et historique de configuration de l’analyseur de configuration

Cet onglet vous permet d’effectuer le suivi des modifications que vous avez apportées à vos stratégies de sécurité personnalisées en fonction des informations de l’analyseur de sécurité. Par défaut, les informations suivantes s’affichent :

- **Dernière modification**
- **Modifié par**
- **Nom du paramètre**
- **Stratégie**
- **Type**

Pour filtrer les résultats, cliquez sur **Filtrer**. Dans le menu volant **filtres** qui s’affiche, vous pouvez sélectionner l’un des filtres suivants :

- Heure de **début** et **heure de fin** (date)
- **Protection standard** ou **protection stricte**

Pour exporter les résultats dans un fichier. csv, cliquez sur **Exporter**.

![Analyse de dérive de configuration et vue historique dans l’analyseur de configuration](../../media/configuration-analyzer-configuration-drift-analysis-view.png)
