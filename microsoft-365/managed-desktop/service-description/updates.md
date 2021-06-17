---
title: Gestion des mises à jour dans le Bureau géré Microsoft
description: Le maintien à jour du Bureau géré Microsoft est un équilibre entre vitesse et stabilité.
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 5d78f695785cd81b51e20b90cdefbb3790cf6197
ms.sourcegitcommit: 34c06715e036255faa75c66ebf95c12a85f8ef42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "52984735"
---
# <a name="how-updates-are-handled-in-microsoft-managed-desktop"></a>Gestion des mises à jour dans le Bureau géré Microsoft


<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/update-rings); do not delete.-->

<!--Update management -->

Bureau géré Microsoft connecte tous les appareils à une infrastructure cloud moderne. Maintenir à jour Windows, Office, les pilotes, les microprogrammes et les applications du Microsoft Store pour Entreprises constitue un équilibre entre vitesse et stabilité. Nous utilisons des groupes de mise à jour pour nous assurer que les mises à jour et les stratégies du système d’exploitation sont déployées en toute sécurité. Pour plus d’informations, voir la vidéo [Microsoft Managed Desktop Change and Release Process](https://www.microsoft.com/videoplayer/embed/RE4mWqP). 

Les mises à jour publiées par Microsoft sont cumulatives et sont classées en tant que mises à jour de qualité ou de fonctionnalités.
Pour plus d’informations, voir [Windows Update for Business: Update types](/windows/deployment/update/waas-manage-updates-wufb#update-types). 

## <a name="update-groups"></a>Mettre à jour un groupe


Bureau géré Microsoft utilise quatre groupes Azure AD pour gérer les mises à jour :

- **Test**: permet de valider les modifications de stratégie du Bureau géré Microsoft, les mises à jour du système d’exploitation, les mises à jour des fonctionnalités et autres modifications apportées à l’organisation Azure AD ( « client »). Le meilleur pour les tests ou les utilisateurs qui peuvent fournir des commentaires précoces. Le groupe de test est exempté de tout contrat de niveau de service établi et du support utilisateur. Ce groupe est disponible pour la validation de la compatibilité des applications avec de nouvelles stratégies ou modifications de système d’exploitation.  
- **Tout d’abord**: contient les premiers utilisateurs de logiciels et les appareils qui peuvent être soumis à des mises à jour de pré-publication. Les appareils de ce groupe peuvent être en panne s’il existe des scénarios qui n’ont pas été couverts lors des tests dans l’anneau de test.
- **Rapide**: hiérarchise la vitesse sur la stabilité. Utile pour détecter les problèmes de qualité avant qu’ils ne soient proposés au groupe Large. Ce groupe fait office de couche de validation suivante, mais il est généralement plus stable que les groupes Test et First. 
- **Large**: dernier groupe à avoir des mises à jour de fonctionnalités et de qualité disponibles. Ce groupe contient la plupart des utilisateurs de l’organisation Azure AD. Par conséquent, il privilégie la stabilité par rapport à la vitesse de déploiement. Le test des applications doit être effectué ici, car l’environnement est le plus stable.

### <a name="moving-devices-between-update-groups"></a>Déplacement d’appareils entre des groupes de mise à jour
Vous souhaiterez peut-être que certains appareils reçoivent les mises à jour en dernier et d’autres que vous souhaitez passer en premier. Pour déplacer ces appareils dans le groupe de mise à jour approprié, voir Affecter des [appareils à un groupe de déploiement.](../working-with-managed-desktop/assign-deployment-group.md)

Pour plus d’informations sur les rôles et responsabilités au sein de ces groupes de déploiement, voir Rôles et [responsabilités](../intro/roles-and-responsibilities.md) de Bureau géré Microsoft

### <a name="using-microsoft-managed-desktop-update-groups"></a>Utilisation des groupes de mise à jour du Bureau géré Microsoft 
Certaines parties du service que vous gérez, telles que le déploiement d’applications, peuvent être nécessaires pour cibler tous les appareils gérés.

## <a name="how-update-deployment-works"></a>Fonctionnement du déploiement de la mise à jour :
1. Bureau géré Microsoft déploie une nouvelle mise à jour de fonctionnalité ou de qualité conformément à la planification spécifiée dans le tableau suivant.
2. Pendant le déploiement, Bureau géré Microsoft surveille les signes d’échec ou de perturbation en fonction des données de diagnostic et du système de support utilisateur. Si des groupes sont détectés, nous interrompons immédiatement le déploiement vers tous les groupes actuels et futurs.
    - Exemple : si un problème est détecté lors du déploiement d’une mise à jour qualité dans le premier groupe, les déploiements de mise à jour vers First, Fast et Broad seront tous suspendus jusqu’à ce que le problème soit résolu.
    - Vous pouvez signaler des problèmes de compatibilité en classant un ticket dans le portail d’administration du bureau géré Microsoft.
    - Les mises à jour des fonctionnalités et de la qualité sont suspendues indépendamment. L’interruption est en vigueur pendant 35 jours par défaut, mais peut être réduite ou étendue selon que le problème est corrigé ou non.
3. Une fois les groupes inutilisés, le déploiement reprend en fonction de la planification du tableau.

Ce processus de déploiement s’applique aux mises à jour des fonctionnalités et de la qualité, bien que la chronologie varie pour chacune d’elles.


<table>
    <tr><th colspan="5">Mettre à jour les paramètres de déploiement</th></tr>
    <tr><th>Type de mise à jour</th><th>Tester</th><th>Premier</th><th>Rapide</th><th>Larges</th></tr>
    <tr><td>Mises à jour qualité pour le système d’exploitation</td><td>0 jour</td><td>0 jour</td><td>0 jour</td><td>3 jours</td></tr>
    <tr><td>Mises à jour de fonctionnalités pour le système d’exploitation</td><td>0 jour</td><td>30 jours</td><td>60 jours</td><td>90 jours</td></tr>
    <tr><td>Pilotes/microprogramme</td><td colspan="4">Suit la planification des mises à jour qualité</td></tr>
    <tr><td>Définition de l’antivirus</td><td colspan="4">Mise à jour avec chaque analyse</td></tr>
    <tr><td>Applications Microsoft 365 for entreprise</td><td colspan="4"><a href="/microsoft-365/managed-desktop/get-started/m365-apps#updates-to-microsoft-365-apps">En savoir plus</a></td></tr>
    <tr><td>Microsoft Edge</td><td colspan="4"><a href="/microsoft-365/managed-desktop/get-started/edge-browser-app#updates-to-microsoft-edge">En savoir plus</a></td></tr>
    <tr><td>Microsoft Teams</td><td colspan="4"><a href="/microsoft-365/managed-desktop/get-started/teams#updates">En savoir plus</a></td></tr>
</table>

>[!NOTE]
>Ces périodes de report sont conçues intentionnellement pour garantir des normes de sécurité et de performances élevées pour tous les utilisateurs. En outre, en fonction des données recueillies sur tous les appareils de bureau géré Microsoft et de l’étendue et de l’impact variables des mises à jour, Bureau géré Microsoft se réserve la flexibilité nécessaire pour modifier la durée des périodes de report ci-dessus pour tous les groupes de déploiement sur une base ad hoc.
>
>Bureau géré Microsoft effectue une évaluation indépendante de chaque version de fonctionnalité Windows afin d’évaluer sa nécessité et son utilité pour ses clients gérés. Par conséquent, bureau géré Microsoft peut déployer ou non toutes les mises à jour de fonctionnalités Windows. 

## <a name="windows-insider-program"></a>Programme Windows Insider

Bureau géré Microsoft ne prend pas en charge les appareils qui font partie du programme Windows Insider. Le programme Windows Insider est utilisé pour valider les logiciels Windows pré-publiés et est destiné aux appareils qui ne sont pas essentiels à la mission. Bien qu’il s’agit d’une initiative Microsoft importante, elle n’est pas destinée à un déploiement à grande échelle dans des environnements de production. 

Tous les appareils trouvés avec les builds Windows Insider peuvent être placés dans le groupe test et seront exemptés des contrats de niveau de service de mise à jour et de la prise en charge des utilisateurs du Bureau géré Microsoft.

## <a name="bandwidth-management"></a>Gestion de la bande passante

Nous utilisons [l’optimisation de la](/windows/deployment/update/waas-delivery-optimization) distribution pour toutes les mises à jour du système d’exploitation et des pilotes. L’optimisation de la distribution réduit la taille de téléchargement à partir du service Windows Update en recherchant les mises à jour des homologues au sein du réseau d’entreprise.