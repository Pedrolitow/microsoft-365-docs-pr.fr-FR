---
title: Comprendre les profils d'appareil
description: Les différents profils que les administrateurs peuvent affecter aux appareils
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: e6b0c96d4e145a2e5df7c7555e262aefe891e483
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690615"
---
# <a name="device-profiles"></a>Profils d'appareil

Vous pouvez affecter différentes configurations pré-définies (« profils d'appareil ») aux appareils, chacune optimisée pour les besoins de types spécifiques d'utilisateurs. Trois profils d'appareil sont disponibles :

- Standard
- Données sensibles
- Utilisateur avec pouvoir

Vous pouvez penser que les profils d'appareil font partie d'une hiérarchie d'options de configuration d'appareil.

:::image type="content" source="../../media/mmd-profile-options-heirarchy.png" alt-text="Configurations d'appareil affichées sous la forme d'une pyramide. Description :":::

Fondamentalement, chaque appareil bureau géré Microsoft possède une base qui inclut une ligne de base de sécurité standard, des stratégies de conformité, des paramètres Windows Update et des groupes. Pour fonctionner avec bureau géré Microsoft, chaque appareil doit inclure tous ces éléments, qui ne peuvent pas être modifiés par les administrateurs sans une demande de Bureau géré Microsoft.

Les profils d'appareil apparaissent au niveau supérieur suivant. Un seul profil doit être affecté à chaque appareil de bureau géré Microsoft. Les administrateurs peuvent choisir le profil attribué à un appareil.

À un niveau encore plus élevé, il existe des [personnalisations supplémentaires.](customizing.md) Chaque appareil peut avoir une ou plusieurs personnalisations (ou aucune). Ils peuvent modifier une couche de niveau inférieur (profils d'appareil ou configuration de base) ou être une toute nouvelle demande superposée à la configuration standard.

En haut, vous avez vos propres modifications, telles que les détails du réseau ou les applications. Un appareil peut avoir n'importe quel nombre de ces modifications, qui ne sont pas gérées ou bloquées par Bureau géré Microsoft.


## <a name="device-profile-details"></a>Détails du profil de l'appareil

Le tableau suivant récapitule les paramètres et leurs valeurs par défaut pour chaque paramètre configuré par les profils d'appareil. (En arrière-plan, ces paramètres sont configurés avec OMA-URIs à l'aide de profils de configuration personnalisés dans Microsoft Endpoint Manager.)

| Fonctionnalité | Données sensibles | Power User | Standard |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------|------------------------|-----------------------|
| **Bloquer le stockage externe**                                                                                                                               | Oui                       | Oui                   | Non                   |
| **[Niveau de blocage cloud](https://docs.microsoft.com/graph/api/resources/intune-deviceconfig-defendercloudblockleveltype)** | Élevé                      | Élevé                  | Élevé                 |
| **Désactiver les comptes Microsoft**                                                                                                                           | Oui                       | Oui                   | Non                   |
| **Désactiver OneDrive personnel**                                                                                                                            | Oui                       | Oui                   | Non                   |
| **Basculer vers un bureau sécurisé pour l'élévation**                                                                                                               | Non                        | Oui                   | Non                   |
| **Balise d'appareil Microsoft Defender pour point de terminaison**                                                                                                           | M365Managed-SensitiveData | M365Managed-PowerUser | M365Managed-Standard |
| **Administrateur sur l'appareil ?**                                                                                                                                 | Non                        | Oui                   | Non                   |
| **Profil Autopilot**                                                                                                                                     | MMD Standard               | Utilisateur d'alimentation MMD         | MMD Standard          |
| **AppLocker**                                                                                                                                            | Oui                       | Non                    | Non                   |
| **Bloquer le magasin public**                                                                                                                                   | Oui                       | Oui                   | Non                   |

Chaque profil d'appareil implique également les éléments ci-après :

- Un groupe d'appareils Azure Active Directory (AAD) d'appartenance dynamique
- Un groupe d'appareils AAD d'appartenance statique
- Profil de configuration microsoft Endpoint Manager

> [!IMPORTANT]
> Ne modifiez pas directement l'appartenance de ces groupes. Utilisez l'interface comme décrit dans [Réaffecter des profils.](../working-with-managed-desktop/change-device-profile.md)

## <a name="limitations"></a>Limites

Vous pouvez demander des exceptions aux profils d'appareil et à leurs détails comme vous le feriez avec n'importe quelle autre stratégie. N'oubliez pas que vous ne pouvez avoir qu'un seul profil d'appareil dans votre organisation Azure Active Directory ( « client »). Par exemple, vous ne pouvez pas demander que le profil d'appareil de données sensibles désactive AppLocker pour certains de vos utilisateurs uniquement. Tous les appareils avec le profil de données sensibles doivent avoir la même configuration.

Chaque appareil ne peut avoir qu'un seul profil. Si un appareil donné est utilisé par plusieurs utilisateurs, tous les utilisateurs de cet appareil auront la même configuration.
