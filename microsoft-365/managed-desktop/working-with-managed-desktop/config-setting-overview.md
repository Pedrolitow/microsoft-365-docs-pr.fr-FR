---
title: Paramètres configurables pour Microsoft Manged Desktop
description: Informations sur les paramètres configurables avec Microsoft Manged Desktop
keywords: Microsoft Manged Desktop, Microsoft 365, service, documentation, paramètres, paramètres configurables
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: bf8672ee6c3332ea6f8522f5086d72e58d1b9048
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59182032"
---
# <a name="configurable-settings---microsoft-managed-desktop"></a>Paramètres configurables : Bureau géré Microsoft

Microsoft Manged Desktop déploie des paramètres et des stratégies qui sont appliqués à tous les appareils gérés par Microsoft Manged Desktop. Pour plus d’informations, voir [Configuration de l’appareil.](../service-description/device-policies.md)

Les paramètres configurables dans Microsoft Manged Desktop offrent aux administrateurs informatiques un moyen de personnaliser et de déployer des paramètres propres à leur organisation et aux besoins de leur entreprise. Ces paramètres s’ajoutent aux paramètres de configuration des appareils et aux stratégies qui sont gérés par Microsoft Manged Desktop.  

Les modifications de paramètre configurables sont apportées dans le cloud et appliquées à vos Microsoft Manged Desktop dans des groupes de déploiement définis. Ce processus est similaire à la façon dont Microsoft Manged Desktop les modifications apportées aux paramètres et stratégies de configuration des appareils qui sont définis et gérés par le service. En utilisant le même processus que celui Microsoft Manged Desktop pour le déploiement des modifications, vous continuez à faire avancer votre organisation à l’aide des pratiques de gestion des technologies de l’entreprise modernes.

## <a name="when-to-use-configurable-settings"></a>Quand utiliser les paramètres configurables ?

Il existe plusieurs fois des paramètres configurables. 

**Processus** d’intégration : Microsoft Manged Desktop vous recommande de personnaliser les paramètres configurables lors de l’intégration au service Microsoft Manged Desktop ou lors de l’intégration d’un grand nombre d’appareils (20 ou plus). Les catégories de paramètres sont configurées dans Microsoft Manged Desktop portail d’administration. Une fois que vous êtes intégré et que vous avez accès au portail d’administration, vous pouvez choisir les catégories de paramètres que vous souhaitez personnaliser pour votre organisation, apporter les modifications, effectuer un déploiement, puis déployer vos modifications.

**Gérer les paramètres** : examinez vos paramètres régulièrement et mettez à jour les mises à jour nécessaires. Vous devrez peut-être apporter des modifications pour prendre en charge une modification dans votre entreprise.   

## <a name="setting-categories"></a>Définition des catégories

Voici les catégories de paramètres configurables que vous pouvez personnaliser :
- [Image d’arrière-plan du](config-setting-ref.md#desktop-background-picture) bureau : personnaliser l’image d’arrière-plan du bureau Microsoft Manged Desktop appareils. 
- [Pages de démarrage du navigateur](config-setting-ref.md#browser-start-pages) : ajoutez des pages de démarrage à utiliser avec Microsoft Edge. Voir la page de démarrage du navigateur
- [Enterprise de sites en mode d’ajout](config-setting-ref.md#enterprise-mode-site-list-location) : ajoutez des sites et leur mode de compatibilité. Les sites de la liste démarrent dans Internet Explorer. 
- [Sites de confiance](config-setting-ref.md#trusted-sites) : ajoutez des sites de confiance et définissez des zones de sécurité pour chaque site. 
- [Exceptions de site proxy](config-setting-ref.md#proxy) : configurer le numéro d’adresse et le numéro de port de votre serveur proxy, et ajouter des exceptions de site proxy.

Chaque catégorie de paramètres peut être personnalisée et déployée seule. Vous pouvez déployer les modifications apportées à plusieurs catégories de paramètres en même temps, mais vous ne pouvez déployer qu’une seule modification à la fois dans une catégorie de paramètres.

Par exemple :
- Vous pouvez déployer les modifications apportées à l’image d’arrière-plan du bureau et aux sites de confiance, chacun en tant que son propre déploiement, en même temps. 
- Vous ne pouvez pas déployer deux déploiements sur les pages de démarrage du navigateur en même temps. Le déploiement le plus récent arrête les déploiements précédents en cours.

## <a name="configurable-setting-process"></a>Processus de paramètre configurable

Microsoft Manged Desktop vous recommande de suivre un processus semblable au suivant lors de l’utilisation des paramètres configurables pour votre organisation :

**Étape 1 : Planifier** : découvrez les paramètres configurables et déterminez les catégories de paramètres que vous souhaitez configurer pour votre organisation. Créez une chronologie pour le moment où vous prévoyez de déployer les modifications apportées à chaque groupe. Planifiez une communication avec vos utilisateurs qui répond à vos processus de gestion des changements internes. Par exemple, si vous ajoutez des pages de démarrage de navigateur, faites savoir à vos utilisateurs qu’ils auront un nouvel ensemble de pages de démarrage dans leur navigateur après le déploiement.  

**Étape 2 : configurer et configurer** le déploiement : a apporter des modifications aux paramètres configurables dans Microsoft Manged Desktop portail d’administration. Préparez les modifications afin qu’elles sont prêtes à être déployées. N’oubliez pas d’en faire savoir à vos utilisateurs sur les modifications et sur la façon dont elles modifieront l’expérience de leur appareil.   

Vous configurez et configurez les modifications dans Microsoft Manged Desktop portail d’administration. Pour plus d’informations, voir [Personnaliser les paramètres configurables.](config-setting-ref.md) 

**Étape 3 : communiquer les modifications** Communiquez des informations sur les modifications à venir à vos utilisateurs. Pour chaque déploiement, terminez la communication qui fait partie de vos processus de gestion des changements. Vous devez clairement communiquer toute modification qui a une incidence sur le fonctionnement d’un utilisateur ou sur ce qu’il verra sur ses appareils.

**Étape 4 : Déployer les modifications** : déployez vos modifications, en commençant par le groupe test. Le groupe test vous permet de valider et de résoudre les problèmes d’un groupe avec moins d’appareils, avant de déployer les modifications apportées à des groupes plus importants d’appareils. Si vous avez des problèmes, vous pouvez inverser la modification, mettre à jour le paramètre et mettre en place un nouveau déploiement. Microsoft Manged Desktop vous recommande de suivre l’approche structurée et de déployer les groupes dans cet ordre : Test, Premier, Rapide, puis Large.   

Tous les paramètres configurables sont gérés à l’aide Microsoft Manged Desktop portail d’administration. Pour plus d’informations, voir [Déployer les modifications.](config-setting-deploy.md) 

**Étape 5 : suivre les modifications** : suivre l’avancement de vos modifications sur l’état du déploiement. Pour chaque paramètre, vous pouvez :
- **Suivre la progression** : suivre l’état après le déploiement de la modification. L’état est en **cours,** puis terminé **ou** **a échoué.** En cas d’échec d’un déploiement, une demande de support est automatiquement ouverte Microsoft Manged Desktop Opérations pour examiner le problème.  
- **Voir la version déployée** : chaque modification déployée a un numéro de version.
- **Revenir aux modifications** : la reconversion d’une modification arrête le déploiement actuel et retourne tous les groupes aux dernières modifications qui ont été déployées pour tous les groupes. Vous revenir à la dernière valeur de paramètre connue.
- **Valider les modifications** : une fois le déploiement terminé, validez que les modifications ont été appliquées comme prévu.  

Si un déploiement a échoué ou si vous ne pouvez pas revenir à une modification, ouvrez une demande de [support](admin-support.md) avec Microsoft Manged Desktop Operations. 

Pour plus d’informations, [voir Déployer et suivre les paramètres configurables.](config-setting-deploy.md)

## <a name="additional-resources"></a>Ressources supplémentaires
- [Référence des paramètres configurables](config-setting-ref.md) 
- [Déployer des paramètres configurables](config-setting-deploy.md) 
