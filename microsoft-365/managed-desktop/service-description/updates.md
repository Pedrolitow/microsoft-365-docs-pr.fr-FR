---
title: Gestion des mises à jour dans le bureau géré Microsoft
description: La mise à jour de Microsoft maNaged Desktop est un équilibre entre vitesse et stabilité.
keywords: Microsoft maNaged Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 01/09/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: 0dad909ce9e17f993de64ba39b08f388c71abb89
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32278643"
---
# <a name="how-updates-are-handled-in-microsoft-managed-desktop"></a>Gestion des mises à jour dans le bureau géré Microsoft


<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/update-rings); do not delete.-->

<!--Update management -->

Microsoft maNaged Desktop connecte tous les périphériques à une infrastructure moderne basée sur le Cloud. La mise à jour des mises à jour des applications Windows, Office, des pilotes, des microprogrammes et Microsoft Store pour les applications métiers est un équilibre entre vitesse et stabilité. Les groupes de déploiement seront utilisés pour s'assurer que le système d'exploitation et les stratégies sont déployés de manière sécurisée. 

Les mises à jour publiées par Microsoft sont cumulatives et peuvent être classées en tant que mises à jour de qualité ou de fonctionnalité.
Pour plus d'informations, reportez-vous à la rubrique [Windows Update for Business: Update types](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb#update-types). 

## <a name="update-groups"></a>Mettre à jour un groupe

Microsoft maNaged Desktop utilise quatre groupes Azure AD pour gérer les mises à jour:

- **Test**: permet de valider les modifications apportées à la stratégie de bureau géré Microsoft, les mises à jour du système d'exploitation, les mises à jour des fonctionnalités et d'autres modifications envoyées au client. Aucun utilisateur final ne doit être placé dans le groupe de test. Le groupe test est exempté de tout SLA établi et de la prise en charge de l'utilisateur final. Ce groupe peut être utilisé pour valider la compatibilité des applications avec la nouvelle stratégie ou les modifications apPortées au système d'exploitation.  
- **Tout d'abord**: contient les dispositifs et les exposants logiciels susceptibles d'être soumis aux mises à jour de pré-publication. Les périphériques de ce groupe peuvent subir des pannes s'il existe des scénarios qui n'ont pas été pris en compte pendant le test de l'anneau de test.
- **Fast**: hiérarchise la vitesse sur la stabilité. Utile pour détecter les problèmes de qualité avant de les proposer à l'ensemble du groupe. Ce groupe sert de couche de validation suivante, mais est généralement plus stable que le test et les premiers groupes. 
- **Large**: dernier groupe avec des mises à jour de la qualité et des fonctionnalités disponibles. Ce groupe contient la majorité des utilisateurs dans le client, et favorise ainsi la stabilité de la vitesse pendant le déploiement. Le test des applications doit être réalisé ici, car l'environnement est le plus stable. 

Pour plus d'informations sur les rôles et les responsabilités liés à ces groupes de déploiement, consultez la rubrique [rôles et responsabilités de Microsoft Managed Desktop](../intro/roles-and-responsibilities.md)

Fonctionnement du déploiement des mises à jour:
- Le bureau géré Microsoft déploie une nouvelle fonctionnalité ou mise à jour de qualité en fonction de la planification spécifiée ci-dessous.
- Lors du déploiement, le bureau géré par Microsoft analyse les signes d'échec ou de perturbation (en fonction des signaux de données de diagnostic et du système de prise en charge de l'utilisateur final). Si elles sont détectées, le déploiement sur tous les groupes actuels et futurs est immédiatement suspendu.
    - Exemple: si un problème est découvert pendant le déploiement d'une mise à jour de la qualité pour le premier groupe, les déploiements de mise à jour vers le premier, le plus rapide et le plus large seront suspendus jusqu'à ce que le problème soit résolu.
    - Des problèmes de compatibilité peuvent être signalés en désignant un ticket dans le portail de l'administrateur informatique géré par Microsoft.
- Les mises à jour de la fonctionnalité et de la qualité sont suspendues indépendamment. La suspension est appliquée pendant 35 jours par défaut, mais elle peut être réduite ou étendue selon que le problème est résolu ou non.
- Une fois les groupes annulés, le déploiement reprend en fonction de la planification ci-dessous.
- Ce processus de déploiement s'applique aux mises à jour des fonctionnalités et de la qualité, bien que la chronologie varie en fonction de chacune d'elles.

<table>
<tr><th colspan="5">Mettre à jour les paramètres de déploiement</th></tr>
<tr><th>Type de mise à jour</th><th>Tester</th><th>Premier</th><th>Rapide</th><th>Larges</th></tr>
<tr><td>Mises à jour de la qualité pour le système d'exploitation</td><td>0 jour</td><td>0 jour</td><td>0 jour</td><td>3 jours</td></tr>
<tr><td>Mises à jour de fonctionnalité pour le système d'exploitation</td><td>0 jour</td><td>30 jours</td><td>60 jours</td><td>90 jours</td></tr>
<tr><td>Pilotes/microprogramme</td><td colspan="4">Suit la planification des mises à jour de la qualité</td></tr>
<tr><td>Définition de la protection antivirus</td><td colspan="4">Mise à jour avec chaque analyse</td></tr>
</table>

Ces périodes de report sont intentionnellement conçues pour garantir des normes de performances et de sécurité élevées pour tous les utilisateurs. Par ailleurs, en fonction des données collectées sur tous les appareils de bureau gérés par Microsoft et de l'étendue et de l'impact des mises à jour, Microsoft maNaged Desktop réserve de souplesse pour modifier la longueur des périodes de report ci-dessus pour tous les groupes de déploiement d'une annonce. base hoc.

## <a name="windows-insider-program"></a>Programme Windows inSider

Microsoft maNaged Desktop ne prend pas en charge les appareils qui font partie du programme Windows inSider. Le programme Windows inSider est utilisé pour valider le logiciel précommercial Windows et destiné aux appareils non stratégiques. Bien qu'il s'agit d'une initiative Microsoft importante, il n'est pas destiné à un déploiement étendu dans les environnements de production. 

Tous les appareils trouvés avec des builds Windows inSider sont placés dans le groupe de test et ne sont pas inclus dans les contrats de niveau de service (SLA) de mise à jour.

## <a name="bandwidth-management"></a>Gestion de la bande passante

L'optimisation de la remise est utilisée pour toutes les mises à jour du système d'exploitation et des pilotes. Elle réduit la taille de téléchargement à partir du service Windows Update (WU) en recherchant des mises à jour à partir des pairs au sein du réseau d'entreprise.


