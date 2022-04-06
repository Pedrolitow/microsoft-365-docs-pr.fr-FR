---
title: Gérer des appareils avec Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- enroll devices into Intune
- manage device endpoints
- zero trust deployment stack
- device management with zero trust
manager: dougeby
audience: ITPro
ms.topic: article
description: Inscrivez vos appareils de point de terminaison dans Microsoft Intune dans le cadre de votre architecture de sécurité Zero Trust, en vous protégeant contre les rançongiciels tout en créant une protection pour les travailleurs à distance.
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-overview
ms.custom: ''
keywords: ''
ms.openlocfilehash: a9872e707bbbb6546d6801ac88ebd28f23fb9806
ms.sourcegitcommit: a06bb81fbd727a790a8fe6a3746b8a3cf62a6b24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2022
ms.locfileid: "64651320"
---
# <a name="manage-devices-with-intune-overview"></a>Vue d’ensemble de la gestion des appareils avec Intune

Un composant essentiel de la sécurité au niveau de l’entreprise inclut la gestion et la protection des appareils. Que vous construisiez une architecture de sécurité de confiance zéro, renforciez votre environnement contre les rançongiciels ou que vous génériez des protections pour prendre en charge les travailleurs à distance, la gestion des appareils fait partie de la stratégie.
Bien que Microsoft 365 inclut plusieurs outils et méthodologies pour la gestion et la protection des appareils, ces instructions suivent les recommandations de Microsoft à l’aide de Microsoft Intune. Il s’agit de conseils qui vous conviennent si vous :

- Prévoyez d’inscrire des appareils dans Intune via la jonction Azure AD (y compris la jonction Azure AD Hybride).
- Prévoyez d’inscrire manuellement des appareils dans Intune.
- Autorisez les appareils BYOD avec des plans d’implémentation de la protection pour les applications et les données et/ou inscrivez ces appareils à Intune.

En revanche, si votre environnement inclut des plans de cogestion, notamment Microsoft Endpoint Configuration Manager, consultez la [Documentation sur la cogestion](/mem/configmgr/comanage/) pour développer le meilleur parcours pour votre organisation. Si votre environnement inclut des plans pour Windows 365 PC Cloud, consultez la [Documentation Windows 365 Enterprise](/windows-365/enterprise/) pour développer le meilleur parcours pour votre organisation.

## <a name="why-manage-endpoints"></a>Pourquoi gérer les points de terminaison ?

L’entreprise moderne possède une diversité incroyable de points de terminaison qui accèdent à ses données. Cette configuration crée une surface d’attaque massive, et par conséquent, les points de terminaison peuvent facilement devenir le lien le plus faible dans votre stratégie de sécurité Confiance zéro.

Principalement pilotés par une nécessité telle que le monde s’est déplacé vers un modèle de travail distant ou hybride, les utilisateurs travaillent à partir de n’importe où, de n’importe quel appareil, plus qu’à tout autre moment dans l’histoire. Les attaquants ajustent rapidement leurs tactiques pour profiter de ce changement. De nombreuses organisations font face à des ressources limitées alors qu’elles relèvent ces nouveaux défis d’entreprise. Pratiquement du jour au lendemain, les entreprises ont accéléré la transformation numérique. Autrement dit, la façon dont les individus travaillent a changé : nous ne nous attendons plus à accéder aux ressources d’entreprise uniquement à partir du bureau et des appareils de l’entreprise.

Obtenir une visibilité sur les points de terminaison accédant à vos ressources d’entreprise est la première étape de votre stratégie d’appareils de confiance zéro. En règle générale, les entreprises sont proactives pour protéger les PC contre les vulnérabilités et les attaques, tandis que les appareils mobiles restent souvent sans surveillance et sans protection. Pour vous assurer que vous n’exposez pas vos données à des risques, nous devons surveiller chaque point de terminaison à la recherche de risques et utiliser des contrôles d’accès granulaires pour offrir le niveau d’accès approprié en fonction de la stratégie de l’organisation. Par exemple, si un appareil personnel est jailbreaké, vous pouvez bloquer l’accès pour vous assurer que les applications d’entreprise ne sont pas exposées aux vulnérabilités connues.

Cette série d’articles vous permet de parcourir un processus recommandé de gestion des appareils qui accèdent à vos ressources. Si vous suivez les étapes recommandées, votre organisation peut obtenir une protection très sophistiquée pour vos appareils et les ressources auxquelles ils accèdent.

## <a name="implementing-the-layers-of-protection-on-and-for-devices"></a>Mise en œuvre de couches de protection sur et pour les appareils

La protection des données et des applications sur les appareils et les appareils eux-mêmes est un processus à plusieurs couches. Il existe certaines protections que vous pouvez acquérir sur des appareils non gérés. Après avoir inscrit des appareils à Intune, vous pouvez implémenter des contrôles plus sophistiqués. Lorsque la protection contre les menaces est déployée sur vos points de terminaison, vous obtenez davantage d’informations et la possibilité de corriger automatiquement certaines attaques. Enfin, si votre organisation a travaillé pour identifier les données sensibles, appliquer une classification et des étiquettes et configurer des stratégies de protection contre la perte de données, vous pouvez obtenir une protection encore plus granulaire des données sur vos points de terminaison.

Le diagramme suivant illustre les blocs de construction pour obtenir une posture de sécurité de confiance zéro pour Microsoft 365 et d’autres applications SaaS que vous introduisez dans cet environnement. Les éléments liés aux appareils sont numérotés de 1 à 7. Il s’agit des couches des administrateurs de périphérique de protection qui se coordonnent avec d’autres administrateurs à accomplir.

![Pile de déploiement Microsoft 365 de confiance zéro](../media/devices/m365-zero-trust-deployment-stack-devices.png#lightbox)

Dans cette illustration :

|&nbsp;|Étape|Description|Conditions d'octroi de licence|
|---|---|---|---|
|1|Configurer le point de départ des stratégies d’accès aux appareils et aux identités de confiance zéro|Travaillez en équipe avec l’administrateur des identités pour [Implémenter la protection des données des stratégies (APP) de niveau 2](manage-devices-with-intune-app-protection.md). Ces stratégies ne nécessitent pas une gestion des appareils. Vous configurez les stratégies de stratégie de protection des applications (SPA) dans Intune. L’administrateur des identités configure une stratégie d’accès conditionnel pour exiger des applications approuvées.|E3, E5, F1, F3, F5|
|2|Inscrire des appareils à Intune|Cette tâche nécessite davantage de planification et de temps pour son implémentation. Microsoft recommande d’utiliser Intune pour inscrire des appareils, car cet outil offre une intégration optimale. Il existe plusieurs options d’inscription d’appareils, en fonction de la plateforme. Par exemple, les appareils Windows peuvent être inscrits à l’aide de Azure AD Join ou d’Autopilot. Vous devez passer en revue les options de chaque plateforme et choisir l’option d’inscription la mieux adaptée à votre environnement. Consultez [l’étape 3 : Inscrire des appareils à Intune](manage-devices-with-intune-enroll.md) pour plus d’informations.|E3, E5, F1, F3, F5|
|3|Configurer des stratégies de conformité|Vous souhaitez vous assurer que les appareils qui accèdent à vos applications et données répondent aux exigences minimales, par exemple les appareils sont protégés par mot de passe ou par code confidentiel et le système d’exploitation est à jour. Les stratégies de conformité sont le moyen de définir les exigences que les appareils doivent respecter. [Étape 3. La configuration des stratégies de conformité](manage-devices-with-intune-compliance-policies.md) vous permet de configurer ces stratégies.|E3, E5, F3, F5|
|4|Configurer les stratégies d’entreprise d’accès aux appareils et aux identités de confiance zéro (recommandé)|Maintenant que vos appareils sont inscrits, vous pouvez travailler avec l’administrateur des identités pour [régler les stratégies d’accès conditionnel afin d’exiger des appareils sains et conformes](manage-devices-with-intune-require-compliance.md).|E3, E5, F3, F5|
|5|Déployer des profils de configuration|Par opposition aux stratégies de conformité des appareils qui marquent simplement un appareil comme conforme ou non en fonction des critères que vous configurez, les profils de configuration modifient réellement la configuration des paramètres sur un appareil. Vous pouvez utiliser des stratégies de configuration pour renforcer les appareils contre les cybermenaces. Voir l’[Étape 5. Déployer des profils de configuration.](manage-devices-with-intune-configuration-profiles.md)|E3, E5, F3, F5|
|6 |Surveiller les risques et la conformité des appareils avec les bases de référence de sécurité|Dans cette étape, vous connectez Intune à Microsoft Defender pour point de terminaison. Grâce à cette intégration, vous pouvez ensuite surveiller les risques des appareils comme condition d’accès. Les appareils dont l’état est à risque sont bloqués. Vous pouvez également surveiller la conformité avec les bases de référence de sécurité. Voir l’[Étape 6. Surveiller les risques et la conformité des appareils aux bases de référence de sécurité](manage-devices-with-intune-monitor-risk.md).|E5, F5|
|7 |Implémenter la protection contre la perte de données (DLP) avec les fonctionnalités de protection des informations|Si votre organisation a travaillé pour identifier les données sensibles et étiqueter les documents, vous pouvez travailler avec l’administrateur de protection des informations pour [protéger les informations sensibles et les documents sur vos appareils](manage-devices-with-intune-dlp-mip.md).|Module complémentaire de conformité E5, F5|

## <a name="coordinating-endpoint-management-with-zero-trust-identity-and-device-access-policies"></a>Coordination de la gestion du point de terminaison avec des stratégies d’accès aux appareils et aux identités de confiance zéro

Ces instructions sont étroitement coordonnées avec les [Stratégies d’accès aux appareils et aux identités de confiance zéro](../security/office-365-security/microsoft-365-policies-configurations.md) recommandées. Vous collaborez avec l’équipe chargée des identités pour assurer la protection que vous configurez avec Intune dans les stratégies d’accès conditionnel Azure AD.

Voici une illustration de la stratégie recommandée définie avec des légendes d’étape pour le travail que vous allez faire dans Intune/MEM et les stratégies d’accès conditionnel associées que vous allez coordonner dans Azure AD.

[![Stratégies d’accès aux appareils et aux identités de confiance zéro](../media/devices/identity-device-overview-steps.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-overview-steps.png)

Dans cette illustration :

- À l’étape 1, [Implémente des stratégies de protection des applications (APP) de niveau 2](manage-devices-with-intune-app-protection.md), vous configurez le niveau recommandé de protection des données avec les stratégies APP. Vous travaillez ensuite avec l’équipe chargée des identités pour configurer la règle d’accès conditionnel associée afin d’exiger l’utilisation de cette protection.
- Dans les étapes 2, 3 et 4, vous inscrivez des appareils à la gestion avec Intune, définissez des stratégies de conformité des appareils, puis vous coordonnez avec votre équipe d’identité pour configurer la règle d’accès conditionnel associée pour autoriser uniquement l’accès aux appareils conformes.

<!---
## Managing change with users
--->

## <a name="enrolling-devices-vs-onboarding-devices"></a>Inscription d’appareils et intégration d’appareils

Si vous suivez ces instructions, vous inscrirez des appareils à la gestion à l’aide de Intune et vous intégrerez des appareils pour les fonctionnalités Microsoft 365 suivantes :

- Microsoft Defender pour point de terminaison
- Microsoft 365 Conformité (pour la protection contre la perte de données de point de terminaison (DLP)) 

L’illustration suivante explique comment cela fonctionne à l’aide d’Intune.

![Processus d’inscription et d’intégration d’appareils](../media/devices/devices-enroll-onboard-process.png#lightbox)

Dans cette illustration :

1. Inscrire des appareils dans la gestion avec Intune.
2. Utilisez Intune pour intégrer des appareils à Microsoft Defender pour point de terminaison.
3. Les appareils qui sont intégrés à Defender pour point de terminaison sont également intégrés pour Microsoft 365 fonctionnalités de conformité, y compris DLP de point de terminaison.

Notez que seul Intune gère les appareils. L’intégration fait référence à la possibilité pour un appareil de partager des informations avec une fonctionnalité de service spécifique. Le tableau suivant récapitule les différences entre l’inscription d’appareils dans la gestion et l’intégration d’appareils pour une fonctionnalité spécifique.

|&nbsp;|Inscription|Intégrer|
|---|---|---|
|Description|L’inscription s’applique à la gestion des appareils. Les appareils sont inscrits pour la gestion avec Intune ou Gestionnaire de configuration.|L’intégration configure un appareil pour qu’il fonctionne avec un ensemble spécifique de fonctionnalités dans Microsoft 365. Actuellement, l’intégration s’applique à Microsoft Defender pour point de terminaison et aux fonctionnalités de conformité Microsoft. <br/><br/> Sur les appareils Windows, l’intégration implique de basculer un paramètre dans Windows Defender qui permet à Defender de se connecter au service en ligne et d’accepter les stratégies qui s’appliquent à l’appareil.|
|Portée|Ces outils de gestion des appareils gèrent l’ensemble de l’appareil, notamment la configuration de l’appareil pour atteindre des objectifs spécifiques, tels que la sécurité.|L’intégration affecte uniquement les fonctionnalités qui s’appliquent.|
|Méthodes recommandées|Azure Active Directory jointure inscrit automatiquement les appareils dans Intune.|Intune est la méthode préférée pour intégrer des appareils à Windows Defender pour point de terminaison, et par conséquent Microsoft 365 fonctionnalités de conformité. <br/><br/> Notez que les appareils intégrés à Microsoft 365 fonctionnalités de conformité à l’aide d’autres méthodes ne sont pas inscrits automatiquement pour Defender pour point de terminaison.|
|Autres méthodes|Les autres méthodes d’inscription dépendent de la plateforme de l’appareil et s’il est BYOD ou géré par votre organisation.|Les autres méthodes d’intégration des appareils sont les suivantes, dans l’ordre recommandé : <ul><li>Gestionnaire de configuration</li><li>Autre outil de gestion des périphériques mobiles (si l’appareil est géré par un seul)</li><li>Script local</li><li>Package de configuration VDI pour l’intégration d’appareils d’infrastructure de bureau virtuel (VDI) non persistants</li><li>Stratégie de groupe</li></ul>|

## <a name="learning-for-administrators"></a>Apprentissage pour les administrateurs

Les ressources suivantes permettent aux administrateurs de découvrir des concepts sur l’utilisation de Microsoft Endpoint Manager et Intune.

[Simplifiez la gestion des appareils avec la description de Microsoft Endpoint Manager](/learn/modules/simplify-device-management-with-microsoft-endpoint-manager/) : découvrez la gestion moderne et Microsoft Endpoint Manager et comment les outils de gestion d’entreprise dans Microsoft 365 peuvent simplifier la gestion de tous vos appareils.

[Configurer la description de Microsoft Endpoint Manager](/learn/modules/set-up-microsoft-intune/) : Microsoft Intune, qui fait partie de Microsoft Endpoint Manager, vous aide à protéger les appareils, les applications et les données que les membres de votre organisation utilisent pour être productifs. Une fois ce module terminé, vous aurez installé Microsoft Intune. La configuration inclut l’examen des configurations prises en charge, l’inscription à Intune, l’ajout d’utilisateurs et de groupes, l’attribution de licences aux utilisateurs, l’octroi d’autorisations d’administrateur et la définition de l’autorité de Gestion des données de référence.
