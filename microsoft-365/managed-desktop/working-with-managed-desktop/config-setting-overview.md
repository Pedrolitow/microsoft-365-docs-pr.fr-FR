---
title: Paramètres configurables pour Microsoft Manged Desktop
description: Informations sur les paramètres configurables avec Microsoft Manged Desktop
keywords: Microsoft Manged Desktop, Microsoft 365, service, documentation, paramètres, paramètres configurables
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 910bd8d37853ce70acb6379599b0259446b0752e
ms.sourcegitcommit: 2c3b737e71038f843ef9e9ff4d5b99d6110b8ec5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2022
ms.locfileid: "62265666"
---
# <a name="configurable-settings---microsoft-managed-desktop"></a>Paramètres configurables : Bureau géré Microsoft

Microsoft Manged Desktop déploie des paramètres et des stratégies qui sont appliqués à tous les appareils gérés par Microsoft Manged Desktop. Pour plus d’informations, voir [Configuration de l’appareil.](../service-description/device-policies.md)

Les paramètres configurables dans Microsoft Manged Desktop offrent aux administrateurs informatiques un moyen de personnaliser et de déployer des paramètres propres à leur organisation et aux besoins de leur entreprise. Ces paramètres s’ajoutent aux paramètres de configuration d’appareil et aux stratégies qui sont gérés par Microsoft Manged Desktop.  

Les modifications de paramètre configurables sont apportées dans le cloud. Ils sont appliqués à vos appareils Microsoft Manged Desktop dans des groupes de déploiement définis. Ce processus est similaire à la façon dont Microsoft Manged Desktop les modifications apportées aux paramètres et stratégies de configuration des appareils qui sont définis et gérés par le service. En utilisant le même processus que celui Microsoft Manged Desktop pour le déploiement des modifications, vous continuez à faire avancer votre organisation à l’aide des pratiques de gestion des technologies de l’entreprise modernes.

## <a name="when-to-use-configurable-settings"></a>Quand utiliser les paramètres configurables ?

Utilisez les paramètres configurables dans les scénarios suivants :

| Scénario | Description |
| ------ | ------ |
| Processus d’intégration | Microsoft Manged Desktop vous recommande de personnaliser les paramètres configurables lors de l’intégration au service Microsoft Manged Desktop ou lors de l’intégration d’un grand nombre d’appareils (20 ou plus). <br><br>Les catégories de paramètres sont configurées dans Microsoft Manged Desktop portail d’administration. Une fois que vous avez intégré le portail d’administration et que vous avez accès à celui-ci, vous pouvez choisir les catégories de paramètres que vous souhaitez personnaliser pour votre organisation. Après cela, a effectuer les modifications, effectuer un déploiement, puis déployer vos modifications. |
| Gérer les paramètres | Examinez vos paramètres régulièrement et mettez à jour les mises à jour nécessaires. Vous devrez peut-être apporter des modifications pour prendre en charge une modification dans votre entreprise. |

## <a name="setting-categories"></a>Définition des catégories

Les catégories de paramètres configurables que vous pouvez personnaliser sont les suivantes :

| Catégorie | Description |
| ------ | ------ |
| [Image d’arrière-plan du bureau](config-setting-ref.md#desktop-background-picture) | Personnalisez l’image d’arrière-plan du bureau Microsoft Manged Desktop appareils mobiles. |
| [Pages de démarrage du navigateur](config-setting-ref.md#browser-start-pages) | Ajoutez des pages de démarrage à utiliser avec Microsoft Edge. |
| [liste Enterprise sites en mode d’Enterprise](config-setting-ref.md#enterprise-mode-site-list-location) | Ajouter des sites et leur mode de compatibilité. Les sites de la liste démarrent dans Internet Explorer. |
| [Sites de confiance](config-setting-ref.md#trusted-sites) | Ajouter des sites de confiance et définir des zones de sécurité pour chaque site. |
| [Exceptions de site proxy](config-setting-ref.md#proxy) | Configurer le numéro d’adresse et le numéro de port de votre serveur proxy, et ajouter des exceptions de site proxy. |

Chaque catégorie de paramètres peut être personnalisée et déployée seule. Vous pouvez déployer les modifications apportées à plusieurs catégories de paramètres en même temps. Toutefois, vous ne pouvez déployer qu’une seule modification à la fois dans une catégorie de paramètres.

Par exemple :

- Vous pouvez déployer les modifications apportées à l’image d’arrière-plan du bureau et aux sites de confiance, chacun en tant que son propre déploiement, en même temps.
- Vous ne pouvez pas déployer deux déploiements sur les pages de démarrage du navigateur en même temps. Le déploiement le plus récent arrête les déploiements précédents qui sont toujours en cours.

## <a name="configurable-setting-process"></a>Processus de paramètre configurable

Microsoft Manged Desktop vous recommande de suivre un processus comme celui ci-dessous lors de l’utilisation des paramètres configurables pour votre organisation :

| Étape  | Processus |
| ------ | ------ |
| **Étape 1 : planifier** | <ol type="1"><li>Découvrez les paramètres configurables et déterminez les catégories de paramètres que vous souhaitez configurer pour votre organisation.</li> <li>Créez une chronologie lorsque vous prévoyez de déployer les modifications apportées à chaque groupe.</li> <li>Planifiez une communication avec vos utilisateurs qui répond à vos processus de gestion des changements internes. Par exemple, si vous ajoutez des pages de démarrage de navigateur, informez vos utilisateurs qu’ils auront un nouvel ensemble de pages de démarrage dans leur navigateur après le déploiement.</li></ol> |
| **Étape 2 : Configurer et configurer le déploiement par étapes** | <ol type="1"><li>A apporté des modifications aux paramètres configurables dans Microsoft Manged Desktop portail d’administration.</li><li>Préparez les modifications afin qu’elles sont prêtes à être déployées.</li> <li>N’oubliez pas d’informer vos utilisateurs des modifications et de la façon dont elles modifieront l’expérience de leur appareil.</li><li>Configurez et configurez les modifications dans Microsoft Manged Desktop portail d’administration. Pour plus d’informations, voir [Personnaliser les paramètres configurables.](config-setting-ref.md)</li></ol>|
| **Étape 3 : Communiquer les modifications** | <ol type="1"><li>Communiquez des informations sur les modifications à venir à vos utilisateurs.</li> <li>Pour chaque déploiement, terminez la communication qui fait partie de vos processus de gestion des changements. Vous devez clairement communiquer toute modification qui a une incidence sur le fonctionnement d’un utilisateur ou sur ce qu’il verra sur ses appareils.</li></ol> |
| **Étape 4 : Déployer les modifications** | Déployez vos modifications, en commençant par le groupe Test. Le groupe test vous permet de valider et de résoudre les problèmes dans un groupe avec moins d’appareils, avant de déployer les modifications apportées à des groupes plus importants d’appareils. <br><br>Si vous avez des problèmes, vous pouvez inverser la modification, mettre à jour le paramètre et mettre en place un nouveau déploiement. Microsoft Manged Desktop vous recommande de suivre l’approche structurée et de déployer les groupes dans cet ordre : Test, Premier, Rapide, puis Large. <br><br>Tous les paramètres configurables sont gérés à l’aide Microsoft Manged Desktop portail d’administration. Pour plus d’informations, voir [Déployer les modifications.](config-setting-deploy.md) |
| **Étape 5 : Suivre les modifications** | Suivez l’avancement de vos modifications dans la section État du déploiement. Pour chaque paramètre, vous pouvez : <ul><li>**Suivre la progression :**  Suivez l’état après avoir déployé la modification. L’état est en **cours,** puis terminé **ou** **a échoué.** En cas d’échec d’un déploiement, une demande de support est automatiquement ouverte Microsoft Manged Desktop Opérations pour examiner le problème.</li> <li>**Voir la version déployée :** Chaque modification déployée a un numéro de version.</li><li>**Inversez les modifications :** Le retour à une modification arrête le déploiement actuel. Il retourne tous les groupes aux dernières modifications qui ont été déployées sur tous les groupes. Vous revenir à la dernière valeur de paramètre connue.</li><li>**Validez les modifications :** Une fois le déploiement terminé, validez que les modifications ont été appliquées comme prévu.</li></ul> |

Si un déploiement a échoué ou si vous ne pouvez pas revenir à une modification, ouvrez une demande de [support](admin-support.md) avec Microsoft Manged Desktop Operations.

Pour plus d’informations, voir [Déployer et suivre les paramètres configurables.](config-setting-deploy.md)

## <a name="additional-resources"></a>Ressources supplémentaires

- [Référence des paramètres configurables](config-setting-ref.md)
- [Déployer des paramètres configurables](config-setting-deploy.md)
