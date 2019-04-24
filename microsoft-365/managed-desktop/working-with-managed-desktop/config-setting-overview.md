---
title: Paramètres configurables pour le bureau géré Microsoft
description: Informations sur les paramètres configurables avec Microsoft maNaged Desktop
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation, paramètres, paramètres configurables
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 2/14/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: 0d30e92eb9747079a7edc5a8fd198298508f342e
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32278210"
---
# <a name="configurable-settings---microsoft-managed-desktop"></a>Paramètres configurables-bureau géré Microsoft

Microsoft maNaged Desktop déploie les paramètres et les stratégies qui sont appliqués à tous les appareils gérés par Microsoft maNaged Desktop. Pour plus d'informations, consultez la rubrique Configuration de l' [appareil](../service-description/device-policies.md).

Configurable Settings in Microsoft maNaged Desktop offre aux administrateurs informatiques un moyen de personnaliser et de déployer des paramètres propres à leur organisation et leurs besoins professionnels. Ces paramètres s'ajoutent aux stratégies et aux paramètres de configuration des appareils qui sont gérés par le bureau géré Microsoft.  

Les modifications de paramètres configurables sont apportées dans le Cloud et appliquées à vos appareils de bureau gérés par Microsoft dans des groupes de déploiement définis. Ce processus est similaire à la façon dont Microsoft maNaged Desktop gère les modifications apportées aux stratégies et paramètres de l'appareil configuruation qui sont définis et gérés par le service. À l'aide de la même procédure que celle utilisée par Microsoft maNaged Desktop pour le déploiement des modifications, vous continuez à faire avancer votre organisation à l'aide des pratiques modernes de gestion informatique.

## <a name="when-to-use-configurable-settings"></a>Quand utiliser des paramètres configurables?

Il existe plusieurs fois que vous pouvez utiliser des paramètres configurables. 

**Processus d'intégration** : Microsoft Managed Desktop recommande de personnaliser les paramètres configurables lorsque vous intégrez à Microsoft Managed Desktop service, ou lorsque vous configurez un grand nombre d'appareils (20 ou plus). Les catégories de définition sont configurées dans le portail d'administration de bureau géré Microsoft. Une fois que vous avez intégré et que vous avez accès au portail d'administration, vous pouvez choisir les catégories de paramètres que vous souhaitez personnaliser pour votre organisation, effectuer les modifications, mettre en place un déploiement, puis déployer vos modifications.

**Gérer les paramètres** : Vérifiez régulièrement vos paramètres et effectuez les mises à jour nécessaires. Vous devrez peut-être effectuer des modifications pour prendre en charge un changement au sein de votre entreprise.   

## <a name="setting-categories"></a>Définition des catégories

Voici les catégories de paramètres configurables que vous pouvez personnaliser:
- [Image d'arrière-plan du Bureau](config-setting-ref.md#desktop-background-picture) : personnaliser l'image d'arrière-plan du Bureau pour les appareils de bureau gérés Microsoft. 
- [Pages de démarrage du navigateur](config-setting-ref.md#browser-start-pages) : ajouter des pages de démarrage à utiliser avec Microsoft Edge. Voir page de démarrage du navigateur
- [Liste des sites en mode entreprise](config-setting-ref.md#enterprise-mode-site-list-location) : ajouter des sites et leur mode de compatibilité. Les sites de la liste démarreront dans Internet Explorer. 
- [Sites de confiance](config-setting-ref.md#trusted-sites) : ajoutez des sites de confiance et définissez des zones de sécurité pour chaque site. 
- [Exceptions de site proxy](config-setting-ref.md#proxy) : configurez le numéro de votre adresse et le numéro de port de votre serveur proxy, et ajoutez des exceptions de site proxy.

Chaque catégorie de paramètres peut être personnalisée et déployée de lui-même. Vous pouvez déployer des modifications à plusieurs catégories de paramètres en même temps, mais vous ne pouvez déployer qu'une seule modification à la fois à une catégorie de paramètres.

Par exemple :
- Vous pouvez déployer en même temps des modifications apportées à l'image d'arrière-plan du bureau et aux sites approuvés, chacun comme leur propre déploiement. 
- Vous ne pouvez pas déployer deux déploiements sur les pages de démarrage du navigateur en même temps. Le déploiement le plus récent arrêtera les déploiements antérieurs qui sont toujours en cours.

## <a name="configurable-setting-process"></a>Processus de définition configurable

Microsoft maNaged Desktop recommande de suivre un processus similaire à celui-ci lors de l'utilisation de paramètres configurables pour votre organisation:

**Étape 1-plan** : Découvrez les paramètres configurables et déterminez les catégories de paramètres que vous souhaitez configurer pour votre organisation. Créez une chronologie pour le moment où vous prévoyez de déployer les modifications apportées à chaque groupe. Planifiez la communication avec vos utilisateurs qui répond à vos processus de gestion des modifications internes. Par exemple, si vous ajoutez des pages de démarrage de navigateur, indiquez à vos utilisateurs qu'ils disposeront d'un nouveau jeu de pages de démarrage dans leur navigateur après le déploiement.  

**Étape 2: configurer et déployer le déploiement** : modifiez les paramètres configurables dans le portail d'administration de bureau géré Microsoft. Préparez les modifications de sorte qu'elles soient prêtes à être déployées. N'oubliez pas de donner aux utilisateurs des informations sur les modifications, ainsi que la façon dont les modifications modifieront leur expérience de l'appareil.   

Vous configurez et modifiez les étapes dans le portail d'administration de bureau géré Microsoft. Pour plus d'informations, [](config-setting-ref.md)consultez la rubrique Customize configurable Settings. 

**Étape 3-communiquer les modifications** Communiquer des informations sur les modifications à venir à vos utilisateurs. Pour chaque déploiement, effectuez la communication qui fait partie de vos processus de gestion des modifications. Vous devez communiquer clairement toute modification qui influe sur le fonctionnement d'un utilisateur ou sur ses appareils.

**Étape 4-déployer les modifications** – déployez vos modifications, en commençant par le groupe de test. Le groupe de test vous permet de valider et de résoudre les problèmes rencontrés dans un groupe avec moins d'appareils, avant de déployer des modifications sur des groupes plus importants d'appareils. Si vous rencontrez des problèmes, vous pouvez annuler la modification, mettre à jour le paramètre et déployer un nouveau déploiement. Microsoft maNaged Desktop recommande de suivre l'approche structurée et de déployer des groupes dans cet ordre: test, First, Fast, puis large.   

Tous les paramètres configurables sont gérés à l'aide du portail d'administration de bureau géré Microsoft. Pour plus d'informations, consultez la rubrique [Deploy changes](config-setting-deploy.md). 

**Étape 5-suivi des modifications** – suivez la progression de vos modifications sur l'état du déploiement. Pour chaque paramètre, vous pouvez:
- **Suivre l'avancement** : suivre l'état après le déploiement de la modification. L'État prend la valeur **en cours**, puis **terminé**ou **échec**. En cas d'échec d'un déploiement, une demande de support est automatiquement ouverte pour les opérations de bureau géré Microsoft pour examiner le problème.  
- **Voir version déployée** : chaque modification déployée possède un numéro de version.
- **Rétablir les modifications** : la restauration d'une modification arrête le déploiement actuel et rétablit tous les groupes avec les dernières modifications qui ont été déployées sur tous les groupes. Vous revenez à la dernière valeur de paramètre correcte.
- **Valider les modifications** -une fois le déploiement terminé, vérifiez que les modifications ont été appliquées comme prévu.  

Si un déploiement a échoué ou si vous ne pouvez pas annuler une modification, [ouvrez une demande de support](admin-support.md) avec Microsoft maNaged Desktop Operations. 

Pour plus d'informations, consultez la rubrique [Deploy and Track configurable Settings](config-setting-deploy.md).

## <a name="additional-resources"></a>Ressources supplémentaires
- [Référence des paramètres configurables](config-setting-ref.md) 
- [Déployer des paramètres configurables](config-setting-deploy.md) 
