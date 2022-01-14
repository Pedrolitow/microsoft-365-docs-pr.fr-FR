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
ms.openlocfilehash: 2a2b4d4b5a4b4aa2344368344168809949a48847
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2022
ms.locfileid: "62035509"
---
# <a name="how-updates-are-handled-in-microsoft-managed-desktop"></a>Comment les mises à jour sont gérées dans Microsoft Manged Desktop


<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/update-rings); do not delete.-->

<!--Update management -->

Microsoft Manged Desktop connecte tous les appareils à une infrastructure informatique moderne. Maintenir Windows, Office, pilotes, microprogrammes et applications Microsoft Store pour Entreprises à jour constitue un équilibre entre vitesse et stabilité. Nous utilisons des groupes de mise à jour pour nous assurer que les mises à jour et les stratégies du système d’exploitation sont déployées en toute sécurité. Pour plus d’informations, voir la vidéo [Microsoft Manged Desktop processus de modification et de publication.](https://www.microsoft.com/videoplayer/embed/RE4mWqP) 

Les mises à jour publiées par Microsoft sont cumulatives et sont classées en tant que mises à jour qualité ou fonctionnalités.
Pour plus d’informations, [voir Windows Update for Business: Update types](/windows/deployment/update/waas-manage-updates-wufb#update-types). 

## <a name="update-groups"></a>Mettre à jour un groupe


Microsoft Manged Desktop utilise quatre groupes Azure AD pour gérer les mises à jour :

- **Test**: permet de valider les Microsoft Manged Desktop de stratégie, les mises à jour du système d’exploitation, les mises à jour des fonctionnalités et d’autres modifications Azure AD l’organisation ( « client »). Le meilleur pour les tests ou les utilisateurs qui peuvent fournir des commentaires précoces. Le groupe de test est exempté de tout contrat de niveau de service établi et du support utilisateur. Ce groupe peut être utilisé pour valider la compatibilité des applications avec de nouvelles stratégies ou modifications de système d’exploitation.  
- **Tout d’abord**: contient les premiers utilisateurs et périphériques logiciels qui peuvent faire l’objet de mises à jour pré-publiées. Les appareils de ce groupe peuvent être en panne s’il existe des scénarios qui n’ont pas été couverts lors des tests dans l’anneau de test.
- **Rapide**: hiérarchise la vitesse sur la stabilité. Utile pour détecter les problèmes de qualité avant qu’ils ne soient proposés au groupe Large. Ce groupe fait office de couche suivante de validation, mais il est généralement plus stable que les groupes Test et First. 
- **Large**: dernier groupe à avoir des mises à jour de fonctionnalités et de qualité disponibles. Ce groupe contient la plupart des utilisateurs de l Azure AD organisation, et privilégie donc la stabilité par rapport à la vitesse de déploiement. Le test des applications doit être effectué ici, car l’environnement est le plus stable.

### <a name="moving-devices-between-update-groups"></a>Déplacement d’appareils entre des groupes de mise à jour
Vous souhaiterez peut-être que certains appareils reçoivent les mises à jour en dernier et d’autres que vous souhaitez passer en premier. Pour déplacer ces appareils dans le groupe de mise à jour approprié, voir Affecter des [appareils à un groupe de déploiement.](../working-with-managed-desktop/assign-deployment-group.md)

Pour plus d’informations sur les rôles et responsabilités au sein de ces groupes de [déploiement, voir Microsoft Manged Desktop Rôles et responsabilités](../intro/roles-and-responsibilities.md)

### <a name="using-microsoft-managed-desktop-update-groups"></a>Utilisation de groupes Microsoft Manged Desktop de mise à jour 
Certaines parties du service que vous gérez, telles que le déploiement d’applications, peuvent être nécessaires pour cibler tous les appareils gérés.

## <a name="how-update-deployment-works"></a>Fonctionnement du déploiement de la mise à jour :
1. Microsoft Manged Desktop déploie une nouvelle mise à jour de fonctionnalité ou de qualité conformément à la planification spécifiée dans le tableau suivant.
2. Pendant le déploiement, Microsoft Manged Desktop surveille les signes d’échec ou de perturbation en fonction des données de diagnostic et du système de support utilisateur. Si des groupes sont détectés, nous interrompons immédiatement le déploiement vers tous les groupes actuels et futurs.
    - Exemple : si un problème est détecté lors du déploiement d’une mise à jour qualité dans le premier groupe, les déploiements de mise à jour vers First, Fast et Broad seront tous suspendus jusqu’à ce que le problème soit atténué.
    - Vous pouvez signaler des problèmes de compatibilité en classant un ticket dans le portail Microsoft Manged Desktop’administration.
    - Les mises à jour des fonctionnalités et de la qualité sont suspendues indépendamment. L’interruption est en vigueur pendant 35 jours par défaut, mais peut être réduite ou étendue selon que le problème est atténué ou non.
3. Une fois les groupes inutilisés, le déploiement reprend en fonction de la planification du tableau.
4. Les utilisateurs sont habilités à répondre aux notifications de redémarrage pendant une période définie (connue sous le nom d’échéance et mesurée à partir du moment où la mise à jour est proposée à l’appareil), pendant laquelle l’appareil redémarre automatiquement uniquement en dehors des heures d’activité. Une fois cette période expirée, l’échéance est atteinte et l’appareil redémarre à la prochaine opportunité disponible, quelles que soient les heures d’activité. La date d’échéance pour les mises à jour qualité est de trois jours . pour les mises à jour de fonctionnalités, il s’agit de cinq jours.

Ce processus de déploiement s’applique aux mises à jour des fonctionnalités et de la qualité, bien que la chronologie varie pour chacune d’elles.


<table>
    <tr><th colspan="5">Mettre à jour les paramètres de déploiement</th></tr>
    <tr><th>Type de mise à jour</th><th>Tester</th><th>Premier</th><th>Rapide</th><th>Larges</th></tr>
    <tr><td>Mises à jour qualité pour le système d’exploitation</td><td>0 jour</td><td>0 jour</td><td>0 jour</td><td>7 jours</td></tr>
    <tr><td>Mises à jour de fonctionnalités pour le système d’exploitation</td><td>0 jour</td><td>30 jours</td><td>60 jours</td><td>90 jours</td></tr>
    <tr><td>Pilotes/microprogramme</td><td colspan="4">Suit la planification des mises à jour qualité</td></tr>
    <tr><td>Définition de l’antivirus</td><td colspan="4">Mise à jour avec chaque analyse</td></tr>
    <tr><td>Applications Microsoft 365 for entreprise</td><td colspan="4"><a href="/microsoft-365/managed-desktop/get-started/m365-apps#updates-to-microsoft-365-apps">En savoir plus</a></td></tr>
    <tr><td>Microsoft Edge</td><td colspan="4"><a href="/microsoft-365/managed-desktop/get-started/edge-browser-app#updates-to-microsoft-edge">En savoir plus</a></td></tr>
    <tr><td>Microsoft Teams</td><td colspan="4"><a href="/microsoft-365/managed-desktop/get-started/teams#updates">En savoir plus</a></td></tr>
</table>

>[!NOTE]
>Ces périodes de report sont conçues intentionnellement pour garantir des normes élevées en matière de sécurité et de performances pour tous les utilisateurs. En outre, en fonction des données recueillies sur tous les appareils Microsoft Manged Desktop et de l’étendue et de l’impact variables des mises à jour, Microsoft Manged Desktop se réserve la flexibilité nécessaire pour modifier la durée des périodes de report ci-dessus pour tous les groupes de déploiement de manière ponctuelle.
>
>Microsoft Manged Desktop effectue une évaluation indépendante de chaque version Windows fonctionnalité pour évaluer sa nécessité et son utilité pour ses locataires gérés. Par conséquent, Microsoft Manged Desktop peuvent ou non déployer toutes les mises à jour Windows fonctionnalités. 

## <a name="windows-insider-program"></a>Programme Windows Insider

Microsoft Manged Desktop ne prend pas en charge les appareils qui font partie du programme Windows Insider. Le Windows Insider est utilisé pour valider les logiciels Windows pré-version et est destiné aux appareils qui ne sont pas essentiels. Bien qu’il s’agit d’une initiative Microsoft importante, elle n’est pas destinée à un déploiement à grande échelle dans des environnements de production. 

Tous les appareils trouvés avec des builds Insider Windows peuvent être placés dans le groupe test et seront exemptés des contrats de niveau de service de mise à jour et de la prise en charge des utilisateurs Microsoft Manged Desktop.

## <a name="bandwidth-management"></a>Gestion de la bande passante

Nous utilisons [l’optimisation de la](/windows/deployment/update/waas-delivery-optimization) distribution pour toutes les mises à jour du système d’exploitation et des pilotes. L’optimisation de la distribution réduit la taille de téléchargement à partir du service Windows mise à jour en recherchant les mises à jour des homologues au sein du réseau d’entreprise.
