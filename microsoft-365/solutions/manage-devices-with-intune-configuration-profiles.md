---
title: Étape 5. Déployer des profils d’appareil dans Microsoft Intune
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
ms.openlocfilehash: cf97cda1d5d439877c7628611d35e6843e40fb7d
ms.sourcegitcommit: 2ea2105d40b60a87fc9aa30f392a73a3a9db6d99
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2021
ms.locfileid: "61129128"
---
# <a name="step-5-deploy-device-profiles-in-microsoft-intune"></a>Étape 5. Déployer des profils d’appareil dans Microsoft Intune

Microsoft Intune inclut des paramètres et fonctionnalités que vous pouvez activer ou désactiver sur différents appareils au sein de votre organisation. Ces paramètres et fonctionnalités sont ajoutés aux « profils de configuration ». Vous pouvez créer des profils pour différents appareils et différentes plateformes, notamment iOS/iPadOS, l’administrateur d’appareil Android, Android Enterprise et Windows. Utilisez ensuite Intune pour appliquer ou « attribuer » le profil aux appareils.

Cet article offre des conseils sur la prise en main des profils de configuration. 


![Étapes de gestion des appareils](../media/devices/intune-mdm-step-4.png#lightbox)

Les profils de configuration vous permettent de configurer une protection importante et de mettre les appareils en conformité afin qu’ils puissent accéder à vos ressources. Ces types de modifications de configuration étaient précédemment configurés à l’aide des paramètres de stratégie de groupe dans Active Directory Domain Services. Une stratégie de sécurité moderne inclut le déplacement des contrôles de sécurité vers le cloud où leur application ne dépend pas de l’accès et des ressources locales. Les profils de configuration Intune sont le moyen de faire passer ces contrôles de sécurité vers le cloud. 

Pour vous donner une idée du type de profils de configuration que vous pouvez créer, voir [Appliquer des fonctionnalités et des paramètres sur vos appareils à l’aide des profils d’appareil dans Microsoft Intune](/mem/intune/configuration/device-profiles).

## <a name="deploy-windows-security-baselines-for-intune"></a>Déployer les bases de référence de sécurité Windows pour Intune

Comme point de départ, si vous souhaitez aligner vos configurations d’appareils sur les bases de référence de sécurité Microsoft, nous vous recommandons les bases de référence de sécurité dans Microsoft Endpoint Manager. L’avantage de cette approche est que vous pouvez compter sur Microsoft pour maintenir les lignes de base à jour à mesure que les fonctionnalités Windows 10 et 11 sont disponibles. 

Pour déployer les bases de référence de sécurité Windows pour Intune, disponibles pour Windows 10 et Windows 11. Voir [Utiliser les lignes de base de sécurité pour configurer des appareils Windows dans Intune](/mem/intune/protect/security-baselines) pour en savoir plus sur les bases de référence disponibles.

Pour l’instant, déployez simplement la base de référence de sécurité MDM la plus appropriée. Voir [Gérer des profils de bases de référence de sécurité dans Microsoft Intune](/mem/intune/protect/security-baselines-configure) pour créer le profil et choisir la version de base de référence.

Plus tard, lorsque Microsoft Defender pour point de terminaison est installé et que vous avez connecté Intune, déployez les bases de référence de Defender pour point de terminaison. Cela est abordé dans l’article suivant de cette série : [Étape 6. Surveillez les risques et la conformité des appareils aux bases de référence de sécurité](manage-devices-with-intune-monitor-risk.md).

Il est important de comprendre que ces bases de référence de sécurité ne sont pas conformes au CIS ou NIST, mais reflètent étroitement leurs recommandations. Pour plus d’informations, voir [Les bases de référence de sécurité Intune sont-elles conformes au CIS ou NIST](/mem/intune/protect/security-baselines) ?

## <a name="customize-configuration-profiles-for-your-organization"></a>Personnaliser les profils de configuration pour votre organisation

Outre le déploiement des bases de référence pré-configurées, de nombreuses organisations à l’échelle de l’entreprise implémentent des profils de configuration pour un contrôle plus granulaire. Cela permet de réduire la dépendance aux objets de stratégie de groupe dans l’environnement Active Directory local et de déplacer les contrôles de sécurité vers le cloud. 

Les nombreux paramètres que vous pouvez configurer à l’aide de profils de configuration peuvent être regroupés en quatre catégories, comme illustré ci-dessous.

![Catégories de profil d’appareil Intune](../media/devices/intune-device-profile-categories.png#lightbox)

Le tableau suivant décrit l’illustration.


|Catégorie |Description |Exemples  |
|---------|---------|---------|
|Fonctionnalités des appareils     | Contrôle les fonctionnalités de l’appareil. Cette catégorie s’applique uniquement aux appareils iOS/iPadOS et macOS.        | Airprint, notifications, messages d’écran de verrouillage        |
|Restrictions d’appareil     | Contrôle la sécurité, le matériel, le partage de données et d’autres paramètres sur les appareils        | Exiger un code PIN, chiffrement de données        |
|Configuration de l’accès     |  Configure un appareil pour accéder aux ressources de votre organisation        | Profils de messagerie, profils VPN, paramètres Wi-Fi, certificats        |
|Personnalisé     | Définir une configuration personnalisée ou exécuter des actions de configuration personnalisées       | Définir les paramètres du fabricant d'ordinateurs (OEM), exécuter des scripts PowerShell        |
|    |         |         |

Lors de la personnalisation des profils de configuration pour votre organisation, utilisez les instructions suivantes :
- Simplifiez votre stratégie de gouvernance de la sécurité en faisant en sorte que le nombre global de stratégies soit réduit.
- Regroupez les paramètres dans les catégories répertoriées ci-dessus ou dans des catégories utiles pour votre organisation.
- Lors du déplacement des contrôles de sécurité des objets de stratégie de groupe vers des profils de configuration Intune (GPO), vous pouvez déterminer si les paramètres configurés par chaque objet de stratégie de groupe sont toujours pertinents et nécessaires pour contribuer à votre stratégie de sécurité cloud globale. L’accès conditionnel et les nombreuses stratégies qui peuvent être configurées dans les services cloud, y compris Intune, fournissent une protection plus sophistiquée que celle qui peut être configurée dans un environnement local où les objets de stratégies de groupe (GPO) personnalisés ont été conçus à l’origine.
- Utilisez l’analyse des stratégies de groupe pour comparer et mapper vos paramètres des objets de stratégie de groupe actuels sur les fonctionnalités au sein de Microsoft Endpoint Manager. Voir [Analyser vos objets de stratégie de groupe (GPO) locaux à l’aide de l’analyse de stratégie de groupe](/mem/intune/configuration/group-policy-analytics) dans Microsoft Endpoint Manager.
- Lorsque vous utilisez des profils de configuration personnalisés, veillez à utiliser les instructions ci-après : [Créer un profil avec des paramètres personnalisés dans Intune](/mem/intune/configuration/custom-settings-configure).

## <a name="additional-resources"></a>Ressources supplémentaires

Si vous ne savez pas par où commencer avec les profils d’appareil, les conseils ci-après peuvent vous aider :

- [Scénarios guidés](/mem/intune/fundamentals/guided-scenarios-overview) 
- [Bases de référence de sécurité](/mem/intune/protect/security-baselines)

Si votre environnement inclut des objets de stratégie de groupe sur site, les fonctionnalités suivantes sont une bonne transition vers le cloud :

- [Analyses de stratégie de groupe](/mem/intune/configuration/group-policy-analytics)
- [Modèles d’administration (ADMX)](/mem/intune/configuration/administrative-templates-windows)
- [Catalogue des paramètres](/mem/intune/configuration/settings-catalog)


## <a name="next-steps"></a>Prochaines étapes
Accédez à [l’Étape 6. Surveillez les risques et la conformité des appareils aux bases de référence de sécurité](manage-devices-with-intune-monitor-risk.md).