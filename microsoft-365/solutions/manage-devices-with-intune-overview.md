---
title: Gérer des appareils avec Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: dougeby
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
ms.custom: seo-marvel-jun2020
keywords: ''
description: ''
ms.openlocfilehash: e0bcbfcadd1e604c4d75b3fa400b9028bf6eeee5
ms.sourcegitcommit: 2ea2105d40b60a87fc9aa30f392a73a3a9db6d99
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2021
ms.locfileid: "61129100"
---
# <a name="manage-devices-with-intune-overview"></a>Vue d’ensemble de la gestion des appareils avec Intune

Un composant essentiel de la sécurité au niveau de l’entreprise inclut la gestion et la protection des appareils. Que vous construisiez une architecture de sécurité de confiance zéro, renforciez votre environnement contre les rançongiciels ou que vous génériez des protections pour prendre en charge les travailleurs à distance, la gestion des appareils fait partie de la stratégie. Bien que Microsoft 365 inclut plusieurs outils et méthodologies pour la gestion et la protection des appareils, ces instructions suivent les recommandations de Microsoft à l’aide de Microsoft Intune. Il s’agit de conseils qui vous conviennent si vous :

- Prévoyez d’inscrire des appareils dans Intune via la jonction Azure AD (y compris la jonction Azure AD Hybride).
- Prévoyez d’inscrire manuellement des appareils dans Intune.
- Autorisez des appareils BYOD avec des plans pour implémenter la protection des applications et des données et/ou inscrire ces appareils dans la gestion.

En revanche, si votre environnement inclut des plans de cogestion, notamment Microsoft Endpoint Configuration Manager, consultez la [Documentation sur la cogestion](/mem/configmgr/comanage/) pour développer le meilleur parcours pour votre organisation. Si votre environnement inclut des plans pour Windows 365 PC Cloud, consultez la [Documentation Windows 365 Enterprise](/windows-365/enterprise/) pour développer le meilleur parcours pour votre organisation. 

## <a name="why-manage-endpoints"></a>Pourquoi gérer les points de terminaison ?
L’entreprise moderne possède une diversité incroyable de points de terminaison qui accèdent à ses données. Cela crée une surface d’attaque massive et, par conséquent, les points de terminaison peuvent facilement devenir le lien le plus faible dans votre stratégie de sécurité de confiance zéro. 

Principalement poussés par une nécessité quand le monde est passé à un modèle de travail à distance ou hybride, les utilisateurs travaillent depuis n’importe où, sur n’importe quel appareil, plus qu’à tout autre moment dans l’histoire. Les attaquants ajustent rapidement leurs tactiques pour profiter de ce changement. De nombreuses organisations font face à des ressources limitées alors qu’elles relèvent ces nouveaux défis d’entreprise. Pratiquement du jour au lendemain, les entreprises ont accéléré la transformation numérique. Autrement dit, la façon dont les individus travaillent a changé : nous ne nous attendons plus à accéder aux ressources d’entreprise uniquement à partir du bureau et des appareils de l’entreprise.

Obtenir une visibilité sur les points de terminaison accédant à vos ressources d’entreprise est la première étape de votre stratégie d’appareils de confiance zéro. En règle générale, les entreprises sont proactives pour protéger les PC contre les vulnérabilités et les attaques, tandis que les appareils mobiles restent souvent sans surveillance et sans protection. Pour vous assurer que vous n’exposez pas vos données à des risques, nous devons surveiller chaque point de terminaison à la recherche de risques et utiliser des contrôles d’accès granulaires pour offrir le niveau d’accès approprié en fonction de la stratégie de l’organisation. Par exemple, si un appareil personnel est jailbreaké, vous pouvez bloquer l’accès pour vous assurer que les applications d’entreprise ne sont pas exposées aux vulnérabilités connues.

Cette série d’articles vous permet de parcourir un processus recommandé de gestion des appareils qui accèdent à vos ressources. Si vous suivez les étapes recommandées, votre organisation peut obtenir une protection très sophistiquée pour vos appareils et les ressources auxquelles ils accèdent.


## <a name="implementing-the-layers-of-protection-on-and-for-devices"></a>Mise en œuvre de couches de protection sur et pour les appareils

La protection des données et des applications sur les appareils et les appareils eux-mêmes est un processus à plusieurs couches. Il existe certaines protections que vous pouvez acquérir sur des appareils non gérés. Après avoir inscrit des appareils dans la gestion, vous pouvez implémenter des contrôles plus sophistiqués. Lorsque la protection contre les menaces est déployée sur vos points de terminaison, vous obtenez davantage d’informations et la possibilité de corriger automatiquement certaines attaques. Enfin, si votre organisation a travaillé pour identifier les données sensibles, appliquer une classification et des étiquettes et configurer des stratégies de protection contre la perte de données, vous pouvez obtenir une protection encore plus granulaire des données sur vos points de terminaison.

Le diagramme suivant illustre les blocs de construction pour obtenir une posture de sécurité de confiance zéro pour Microsoft 365 et d’autres applications SaaS que vous introduisez dans cet environnement. Les éléments liés aux appareils sont numérotés de 1 à 7. Ce sont les couches de protection que les administrateurs de l’appareil coordonneront avec d’autres administrateurs pour effectuer l’opération. 

![Pile de déploiement Microsoft 365 de confiance zéro](../media/devices/m365-zero-trust-deployment-stack-devices.png#lightbox)

Dans cette illustration : 


|  |Étape |Description  |Conditions d'octroi de licence  |
|---------|---------|---------|---------|
|1     | Configurer le point de départ des stratégies d’accès aux appareils et aux identités de confiance zéro       | Travaillez en équipe avec l’administrateur des identités pour [Implémenter la protection des données des stratégies (APP) de niveau 2](manage-devices-with-intune-app-protection.md). Ces stratégies ne nécessitent pas une gestion des appareils. Vous configurez les stratégies de stratégie de protection des applications (SPA) dans Intune. L’administrateur des identités configure une stratégie d’accès conditionnel pour exiger des applications approuvées.          |E3, E5, F1, F3, F5    |
|2     | Inscrire des appareils dans la gestion       | Cette tâche nécessite davantage de planification et de temps pour son implémentation. Bien que vous ayez le choix entre les outils et les méthodes pour y parvenir, l’[Étape 3 : inscrire des appareils dans la gestion](manage-devices-with-intune-enroll.md) vous guide tout au long du processus à l’aide d’Intune avec Autopilot et de l’inscription automatisée.      | E3, E5, F1, F3, F5        |
|3     | Configurer des stratégies de conformité        |  Vous souhaitez vérifier que les appareils qui accèdent à vos applications et données répondent à une configuration minimale, par exemple, qu’ils sont protégés par mot de passe ou par code confidentiel et que le système d’exploitation est à jour. Les stratégies de conformité sont le moyen de définir les exigences que les appareils doivent respecter. [Étape 3. La configuration des stratégies de conformité](manage-devices-with-intune-compliance-policies.md) vous permet de configurer ces stratégies.        |   E3, E5, F3, F5      |
|4     | Configurer les stratégies d’entreprise d’accès aux appareils et aux identités de confiance zéro (recommandé)        |Maintenant que vos appareils sont inscrits, vous pouvez travailler avec l’administrateur des identités pour [régler les stratégies d’accès conditionnel afin d’exiger des appareils sains et conformes](manage-devices-with-intune-require-compliance.md).          | E3, E5, F3, F5        |
|5     |Déployer des profils de configuration      | Par opposition aux stratégies de conformité des appareils qui marquent simplement un appareil comme conforme ou non en fonction des critères que vous configurez, les profils de configuration modifient réellement la configuration des paramètres sur un appareil. Vous pouvez utiliser des stratégies de configuration pour protéger les appareils contre les cybermenaces. Voir l’[Étape 5. Déployer des profils de configuration.](manage-devices-with-intune-configuration-profiles.md)        | E3, E5, F3, F5        |
|6      |Surveiller les risques et la conformité des appareils aux bases de référence de sécurité         | Dans cette étape, vous connectez Intune à Microsoft Defender pour point de terminaison. Grâce à cette intégration, vous pouvez ensuite surveiller les risques des appareils comme condition d’accès. Les appareils dont l’état est à risque sont bloqués. Vous pouvez également surveiller la conformité aux bases de référence de sécurité. Voir l’[Étape 6. Surveiller les risques et la conformité des appareils aux bases de référence de sécurité](manage-devices-with-intune-monitor-risk.md).       | E5, F5        |
|7      |Implémenter la protection contre la perte de données (DLP) avec les fonctionnalités de protection des informations   | Si votre organisation a travaillé pour identifier les données sensibles et étiqueter les documents, vous pouvez travailler avec l’administrateur de protection des informations pour [protéger les informations sensibles et les documents sur vos appareils](manage-devices-with-intune-dlp-mip.md).         | Module complémentaire de conformité E5, F5        |
| | | | |

## <a name="coordinating-endpoint-management-with-zero-trust-identity-and-device-access-policies"></a>Coordination de la gestion du point de terminaison avec des stratégies d’accès aux appareils et aux identités de confiance zéro

Ces instructions sont étroitement coordonnées avec les [Stratégies d’accès aux appareils et aux identités de confiance zéro](../security/office-365-security/microsoft-365-policies-configurations.md) recommandées. Vous collaborez avec l’équipe chargée des identités pour assurer la protection que vous configurez avec Intune dans les stratégies d’accès conditionnel Azure AD. 

Voici une illustration de la stratégie recommandée définie avec des légendes d’étape pour le travail que vous allez faire dans Intune/MEM et les stratégies d’accès conditionnel associées que vous allez coordonner dans Azure AD. 

[![Stratégies d’accès aux appareils et aux identités de confiance zéro](../media/devices/identity-device-overview-steps.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-overview-steps.png)


Dans cette illustration :
- À l’étape 1, [Implémente des stratégies de protection des applications (APP) de niveau 2](manage-devices-with-intune-app-protection.md), vous configurez le niveau recommandé de protection des données avec les stratégies APP. Vous travaillez ensuite avec l’équipe chargée des identités pour configurer la règle d’accès conditionnel associée afin d’exiger l’utilisation de cette protection.
- Aux étapes 2, 3 et 4, vous inscrivez les appareils à la gestion avec Intune/Microsoft Endpoint Manager, définissez des stratégies de conformité des appareils, puis vous coordonnez avec votre équipe d’identité pour configurer la règle d’accès conditionnel associée afin d’autoriser uniquement l’accès aux appareils conformes. 

<!---
## Managing change with users
--->

## <a name="learning-for-administrators"></a>Apprentissage pour les administrateurs
Les ressources suivantes permettent aux administrateurs de découvrir des concepts sur l’utilisation de Microsoft Endpoint Manager et Intune.

[Simplifiez la gestion des appareils avec la description de Microsoft Endpoint Manager](/learn/modules/simplify-device-management-with-microsoft-endpoint-manager/) : découvrez la gestion moderne et Microsoft Endpoint Manager et comment les outils de gestion d’entreprise dans Microsoft 365 peuvent simplifier la gestion de tous vos appareils.

[Configurer la description de Microsoft Endpoint Manager](/learn/modules/set-up-microsoft-intune/) : Microsoft Intune, qui fait partie de Microsoft Endpoint Manager, vous aide à protéger les appareils, les applications et les données que les membres de votre organisation utilisent pour être productifs. Une fois ce module terminé, vous aurez installé Microsoft Intune. La configuration inclut l’examen des configurations prises en charge, l’inscription à Intune, l’ajout d’utilisateurs et de groupes, l’attribution de licences aux utilisateurs, l’octroi d’autorisations d’administrateur et la définition de l’autorité de Gestion des données de référence.
