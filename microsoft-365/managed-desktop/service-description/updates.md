---
title: Comment les mises à jour sont gérées dans Microsoft Manged Desktop
description: Le Microsoft Manged Desktop à jour est un équilibre entre vitesse et stabilité.
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: 5e696f1b89cf03bbd4123252ea967e2aca10ef49
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2022
ms.locfileid: "62879251"
---
# <a name="how-updates-are-handled-in-microsoft-managed-desktop"></a>Comment les mises à jour sont gérées dans Microsoft Manged Desktop

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/update-rings); do not delete.-->

<!--Update management -->

Microsoft Manged Desktop connecte tous les appareils à une infrastructure informatique moderne.

Maintenir Windows, Office, pilotes, microprogrammes et applications Microsoft Store pour Entreprises à jour constitue un équilibre entre vitesse et stabilité. Nous utilisons des groupes de mise à jour pour nous assurer que les mises à jour et les stratégies du système d’exploitation sont déployées en toute sécurité. Pour plus d’informations, voir la vidéo Microsoft Manged Desktop [processus de modification et de publication](https://www.microsoft.com/videoplayer/embed/RE4mWqP).

Les mises à jour publiées par Microsoft sont cumulatives et sont classées en tant que mises à jour qualité ou fonctionnalités. Pour plus d’informations, [voir Windows Update for Business: Update types](/windows/deployment/update/waas-manage-updates-wufb#update-types).

## <a name="update-groups"></a>Mettre à jour un groupe

Microsoft Manged Desktop utilise quatre groupes Azure AD pour gérer les mises à jour :

| Group | Description |
| ------ | ------ |
| Tester | Permet de valider les Microsoft Manged Desktop de stratégie, les mises à jour du système d’exploitation, les mises à jour des fonctionnalités et d’autres modifications Azure AD l’organisation ( « client »). Le groupe Test est : <ul><li>Le meilleur pour les tests ou les utilisateurs qui peuvent fournir des commentaires précoces.</li><li>Exemptez-vous des contrats de niveau de service établis et du support utilisateur.</li><li>Disponible pour valider la compatibilité des applications avec de nouvelles stratégies ou modifications de système d’exploitation.</li></ul> |
| Premier | Contient les premiers utilisateurs de logiciels et les appareils qui peuvent faire l’objet de mises à jour pré-publiées. <br><br> Les appareils de ce groupe peuvent être en panne s’il existe des scénarios qui n’ont pas été couverts lors du test dans l’anneau de test. |
| Rapide | Hiérarchise la vitesse sur la stabilité. Le groupe Rapide est : <ul><li>Utile pour détecter les problèmes de qualité avant qu’ils ne soit proposés au groupe Large.</li> <li>Couche suivante de validation, généralement plus stable que les groupes Test et First.</li></ul> |
| Larges | Ce groupe est le dernier groupe à avoir mis à disposition des mises à jour de fonctionnalités et de qualité. <br><br> Le groupe Large contient la plupart des utilisateurs de l Azure AD organisation, et par conséquent privilégie la stabilité par rapport à la vitesse de déploiement. Le test des applications doit être effectué avec ce groupe, car l’environnement est le plus stable. |

### <a name="moving-devices-between-update-groups"></a>Déplacement d’appareils entre des groupes de mise à jour

Vous souhaiterez peut-être que certains appareils reçoivent les mises à jour en dernier et d’autres que vous souhaitez passer en premier. Pour déplacer ces appareils dans le groupe de mise à jour approprié, voir [Affecter des appareils à un groupe de déploiement](../working-with-managed-desktop/assign-deployment-group.md).

Pour plus d’informations sur les rôles et responsabilités au sein de ces groupes de [déploiement, voir Microsoft Manged Desktop Rôles et responsabilités](../intro/roles-and-responsibilities.md)

### <a name="using-microsoft-managed-desktop-update-groups"></a>Utilisation de groupes Microsoft Manged Desktop de mise à jour

Certaines parties du service que vous gérez, telles que le déploiement d’applications, peuvent être nécessaires pour cibler tous les appareils gérés.

## <a name="update-deployment"></a>Mettre à jour le déploiement

Ci-dessous décrit le fonctionnement du déploiement des mises à jour.

| Étape | Description |
| ------ | ------ |
| Étape 1 | Microsoft Manged Desktop déploie une nouvelle mise à jour de fonctionnalité ou de qualité conformément à la planification spécifiée dans le tableau suivant.|
| Étape 2 | Pendant le déploiement, Microsoft Manged Desktop surveille les signes d’échec ou de perturbation en fonction des données de diagnostic et du système de support utilisateur. Si des groupes sont détectés, nous interrompons immédiatement le déploiement vers tous les groupes actuels et futurs.<br><br> Par exemple, si un problème est détecté lors du déploiement d’une mise à jour qualité pour le premier groupe, les déploiements de mise à jour vers les groupes First, Fast et Broad sont suspendus jusqu’à ce que le problème soit atténué. <br><br> Vous pouvez signaler des problèmes de compatibilité en classant un ticket dans le portail Microsoft Manged Desktop’administration. <br><br> Les mises à jour des fonctionnalités et de la qualité sont suspendues indépendamment. La pause est en vigueur pendant 35 jours par défaut. Toutefois, elle peut être réduite ou étendue selon que le problème est atténué ou non. |
| Étape 3 | Une fois les groupes inutilisés, le déploiement reprend en fonction de la planification du tableau. |
| Étape 4| Les utilisateurs sont habilités à répondre aux notifications de redémarrage pendant une période définie. Cette période est appelée échéance et est mesurée à partir du moment où la mise à jour est proposée à l’appareil. <br><br> Pendant ce temps, l’appareil redémarrera automatiquement en dehors des heures d’activité. Une fois cette période expirée, l’échéance est atteinte et l’appareil redémarre à la prochaine opportunité disponible, quelles que soient les heures d’activité. <br><br> La date d’échéance pour les mises à jour qualité est de trois jours . pour les mises à jour de fonctionnalités, il s’agit de cinq jours. |

> [!NOTE]
> Ce processus de déploiement s’applique aux mises à jour des fonctionnalités et de la qualité, bien que la chronologie varie pour chacune d’elles.

## <a name="deployment-settings"></a>Paramètres de déploiement

Mettre à jour les paramètres de déploiement répertoriés ci-dessous :

| Type de mise à jour | Tester | Premier | Rapide | Larges |
| ------ | ------ | ------ | ------ | ------ |
| Mises à jour qualité pour le système d’exploitation | Zéro jour | Zéro jour | Zéro jour | Sept jours |
| Mises à jour de fonctionnalités pour le système d’exploitation | Zéro jour | 30 jours | 60 jours | 90 jours |
| Pilotes/microprogramme | Suit la planification des mises à jour qualité. | Suit la planification des mises à jour qualité. | Suit la planification des mises à jour qualité. | Suit la planification des mises à jour qualité. |
| Définition de l’antivirus | Mise à jour avec chaque analyse. | Mise à jour avec chaque analyse. | Mise à jour avec chaque analyse. | Mise à jour avec chaque analyse. |
| Applications Microsoft 365 pour Entreprise | [En savoir plus](../get-started/m365-apps.md#updates-to-microsoft-365-apps) | [Si vous souhaitez en savoir plus](../get-started/m365-apps.md#updates-to-microsoft-365-apps) | [En savoir plus](../get-started/m365-apps.md#updates-to-microsoft-365-apps) | [En savoir plus](../get-started/m365-apps.md#updates-to-microsoft-365-apps) |
| Microsoft Edge | [Si vous souhaitez en savoir plus](../get-started/edge-browser-app.md#updates-to-microsoft-edge) | [En savoir plus](../get-started/edge-browser-app.md#updates-to-microsoft-edge) | [Si vous souhaitez en savoir plus](../get-started/edge-browser-app.md#updates-to-microsoft-edge) | [En savoir plus](../get-started/edge-browser-app.md#updates-to-microsoft-edge) |
| Microsoft Teams | [En savoir plus](../get-started/teams.md#updates) | [En savoir plus](../get-started/teams.md#updates) | [Si vous souhaitez en savoir plus](../get-started/teams.md#updates) | [En savoir plus](../get-started/teams.md#updates) |

>[!NOTE]
>Ces périodes de report sont conçues intentionnellement pour garantir des normes élevées en matière de sécurité et de performances pour tous les utilisateurs.<br><br> En fonction des données recueillies sur tous les appareils Microsoft Manged Desktop et de l’étendue et de l’impact variables des mises à jour, Microsoft Manged Desktop se réserve la flexibilité nécessaire pour modifier la durée des périodes de report ci-dessus pour tous les groupes de déploiement de manière ponctuelle.
>
>Microsoft Manged Desktop effectue une évaluation indépendante de chaque version Windows fonctionnalité pour évaluer sa nécessité et son utilité pour ses locataires gérés. Par conséquent, Microsoft Manged Desktop peuvent ou non déployer toutes les mises à jour Windows fonctionnalités.

## <a name="windows-insider-program"></a>Programme Windows Insider

Microsoft Manged Desktop ne prend pas en charge les appareils qui font partie du programme Windows Insider.

Le Windows Insider est utilisé pour valider la version pré-Windows logiciels. Il est destiné aux appareils qui ne sont pas essentiels à la mission. Bien qu’il s’agit d’une initiative Microsoft importante, elle n’est pas destinée à un déploiement à grande échelle dans des environnements de production.

Tous les appareils trouvés avec Windows builds Insider peuvent être placés dans le groupe test. Ces appareils seront exemptés des contrats de niveau de service de mise à jour et de la prise en charge des utilisateurs Microsoft Manged Desktop.

## <a name="bandwidth-management"></a>Gestion de la bande passante

Nous utilisons [l’optimisation de la](/windows/deployment/update/waas-delivery-optimization) distribution pour toutes les mises à jour du système d’exploitation et des pilotes. L’optimisation de la distribution réduit la taille de téléchargement à partir du service Windows mise à jour en recherchant les mises à jour des homologues au sein du réseau d’entreprise.
