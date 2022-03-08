---
title: Comprendre les profils d’appareil
description: Les différents profils que les administrateurs peuvent affecter aux appareils
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: d12a197db8dbcb6356882082c212754fef726d4e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320828"
---
# <a name="device-profiles"></a>Profils d’appareil

Vous pouvez penser que les profils d’appareil font partie d’une hiérarchie d’options de configuration d’appareil.

:::image type="content" source="../../media/mmd-profile-options-heirarchy.png" alt-text="Configurations d’appareil affichées sous la forme d’une pyramide. Description suivante.":::

| Options de configuration d’appareil | Description
| ----- | ----- |
| Vos configurations | En haut, vous avez vos propres configurations, telles que les détails du réseau ou les applications. Un appareil peut avoir n’importe quel nombre de ces configurations, qui ne sont pas gérées ou bloquées par Microsoft Manged Desktop. |
| Personnalisations | Le niveau supérieur suivant est les [personnalisations supplémentaires](customizing.md). Chaque appareil peut avoir une ou plusieurs personnalisations (ou aucune). Les personnalisations peuvent modifier une couche de niveau inférieur (profils d’appareil ou configuration de base) ou être une toute nouvelle demande superposée à la configuration standard. |
| Profils d’appareil | Chaque Microsoft Manged Desktop’appareil doit avoir un seul profil affecté. Les administrateurs peuvent sélectionner le profil attribué à un appareil.<br><br>Vous pouvez affecter différents profils pré-définies aux appareils. Chaque profil est optimisé pour les besoins de types spécifiques d’utilisateurs. Trois profils d’appareil sont disponibles :<ul><li>Standard</li><li>Données sensibles</li><li>Utilisateur avec pouvoir</li> |
| Foundation | Fondamentalement, chaque Microsoft Manged Desktop a une base qui inclut :<br><ul><li>Base de référence de sécurité standard</li><li>Stratégies de conformité</li><li>Windows de mise à jour</li><li>Groupes</li></ul><br>Pour fonctionner avec Microsoft Manged Desktop, chaque appareil doit inclure tous ces éléments. Ces éléments ne peuvent pas être modifiés par les administrateurs. Vous devez envoyer une demande à Microsoft Manged Desktop. |

## <a name="device-profile-details"></a>Détails du profil de l’appareil

Le tableau suivant récapitule les paramètres et leurs valeurs par défaut pour chaque paramètre configuré par les profils d’appareil. En arrière-plan, ces paramètres sont configurés avec OMA-URIs à l’aide de profils de configuration personnalisés Microsoft Endpoint Manager.

<br>

****

| Fonctionnalité | Données sensibles | Power User | Standard |
| ----- | :-----: | :-----: | :-----: |
|**Bloquer les Stockage**| Oui | Oui | Non |
|**[Niveau de blocage cloud](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel)**| Élevé | Élevé | Élevé |
|**Désactiver les comptes Microsoft**| Oui | Oui | Non |
|**Désactiver les OneDrive**| Oui | Oui | Non |
|**[Basculer vers un bureau sécurisé pour l’élévation](/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-useraccountcontrol-switchtothesecuredesktopwhenpromptingforelevation)**| Non | Oui | Non |
|**Balise d’appareil Microsoft Defender pour point de terminaison**| M365Managed-SensitiveData | M365Managed-PowerUser | M365Managed-Standard |
|**Administrateur sur l’appareil ?**| Non | Oui | Non |
|**Profil Autopilot**| MMD Standard | Utilisateur d’alimentation MMD | MMD Standard |
|**AppLocker**| Oui | Non | Non |
|**Bloquer le magasin public**| Oui | Oui | Non |
|

Chaque profil d’appareil implique également les éléments ci-après :

- Une appartenance dynamique à Azure Active Directory groupe d’appareils.
- Appartenance statique à Azure Active Directory groupe d’appareils.
- Profil Microsoft Endpoint Manager configuration.

> [!IMPORTANT]
> Ne modifiez pas directement l’appartenance de ces groupes. Utilisez l’interface comme décrit dans [Réaffecter des profils](../working-with-managed-desktop/change-device-profile.md).

## <a name="limitations"></a>Limitations

Vous pouvez demander des exceptions aux profils d’appareil et à leurs détails comme vous le feriez avec n’importe quelle autre stratégie.

N’oubliez pas que vous ne pouvez avoir qu’un seul profil d’appareil dans votre organisation Azure Active Directory ( « client »). Par exemple, vous ne pouvez pas demander que le profil d’appareil de données sensibles désactive AppLocker pour certains de vos utilisateurs uniquement. Tous les appareils avec le profil d’appareil de données sensibles doivent avoir la même configuration.

Chaque appareil ne peut avoir qu’un seul profil. Si un appareil donné est utilisé par plusieurs utilisateurs, tous les utilisateurs de cet appareil auront la même configuration.
