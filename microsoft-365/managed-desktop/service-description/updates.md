---
title: Comment les mises à jour sont gérées dans Bureau géré Microsoft
description: Le Bureau géré Microsoft à jour est un équilibre entre vitesse et stabilité.
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
ms.openlocfilehash: 6d93bf492f7cfea5a1ff863205085d853c4bbadb
ms.sourcegitcommit: be929f79751c0c52dfa6bd98a854432a0c63faf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2021
ms.locfileid: "52925430"
---
# <a name="how-updates-are-handled-in-microsoft-managed-desktop"></a>Comment les mises à jour sont gérées dans Bureau géré Microsoft


<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/update-rings); do not delete.-->

<!--Update management -->

Bureau géré Microsoft connecte tous les appareils à une infrastructure cloud moderne. Maintenir Windows, Office, pilotes, microprogrammes et applications Microsoft Store pour Entreprises à jour constitue un équilibre entre vitesse et stabilité. Les groupes de déploiement seront utilisés pour s’assurer que les mises à jour et les stratégies du système d’exploitation sont déployées en toute sécurité. Pour plus d’informations, voir la vidéo [Bureau géré Microsoft processus de modification et de publication.](https://www.microsoft.com/videoplayer/embed/RE4mWqP)

Les mises à jour publiées par Microsoft sont cumulatives et sont classées en tant que mises à jour de qualité ou de fonctionnalités.
Pour plus d’informations, [voir Windows Update for Business: Update types](/windows/deployment/update/waas-manage-updates-wufb#update-types). 

## <a name="update-groups"></a>Mettre à jour un groupe

Bureau géré Microsoft utilise quatre groupes Azure AD pour gérer les mises à jour :

- **Test**: permet de valider les Bureau géré Microsoft de stratégie, les mises à jour du système d’exploitation, les mises à jour des fonctionnalités et d’autres modifications apportées au client. Aucun utilisateur ne doit être placé dans le groupe de test. Le groupe de test est exempté de tout contrat de niveau de service établi et du support utilisateur. Ce groupe est disponible pour la validation de la compatibilité des applications avec de nouvelles stratégies ou modifications de système d’exploitation.  
- **Tout d’abord**: contient les premiers utilisateurs de logiciels et les appareils qui peuvent être soumis à des mises à jour de pré-publication. Les appareils de ce groupe peuvent être en panne s’il existe des scénarios qui n’ont pas été couverts lors des tests dans l’anneau de test.
- **Rapide**: hiérarchise la vitesse sur la stabilité. Utile pour détecter les problèmes de qualité avant qu’ils ne soient proposés au groupe Large. Ce groupe fait office de couche de validation suivante, mais il est généralement plus stable que les groupes Test et First. 
- **Large**: dernier groupe à avoir des mises à jour de fonctionnalités et de qualité disponibles. Ce groupe contient la plupart des utilisateurs du client et privilégie donc la stabilité par rapport à la vitesse de déploiement. Le test des applications doit être effectué ici, car l’environnement est le plus stable. 

### <a name="moving-devices-between-update-groups"></a>Déplacement d’appareils entre des groupes de mise à jour
Vous souhaiterez peut-être que certains appareils reçoivent les mises à jour en dernier et d’autres que vous souhaitez passer en premier. Pour déplacer ces appareils dans le groupe de mise à jour approprié, envoyez une demande de [support](../working-with-managed-desktop/admin-support.md) administrateur et nous déplacerons les appareils pour vous. 

> [!NOTE]
> Si vous devez déplacer un utilisateur vers un autre groupe de mise à jour, envoyez une demande de support. Ne déplacez pas vous-même les appareils entre les groupes de mise à jour. Les conséquences sont graves si un appareil est déplacé de manière incorrecte. L’appareil peut se mettre à jour de manière inattendue et les stratégies peuvent être en conflit, ce qui modifie la configuration de l’appareil.

Pour plus d’informations sur les rôles et responsabilités au sein de ces groupes de déploiement, [voir Bureau géré Microsoft Rôles et responsabilités](../intro/roles-and-responsibilities.md)

### <a name="using-microsoft-managed-desktop-update-groups"></a>Utilisation de groupes Bureau géré Microsoft de mise à jour 
Certaines parties du service que vous gérez, telles que le déploiement d’applications, peuvent être nécessaires pour cibler tous les appareils gérés. Dans ces cas-là, il est logique d’utiliser des groupes de mise à jour pour atteindre ces utilisateurs en comprenant que vous ne pouvez pas ajouter, supprimer ou modifier l’appartenance à ces groupes. 

## <a name="how-update-deployment-works"></a>Fonctionnement du déploiement de la mise à jour :
1. Bureau géré Microsoft déploie une nouvelle mise à jour de fonctionnalité ou de qualité conformément à la planification spécifiée dans le tableau suivant.
2. Pendant le déploiement, Bureau géré Microsoft surveille les signes d’échec ou de perturbation en fonction des données de diagnostic et du système de support utilisateur. Si des groupes sont détectés, nous interrompons immédiatement le déploiement vers tous les groupes actuels et futurs.
    - Exemple : si un problème est détecté lors du déploiement d’une mise à jour qualité dans le premier groupe, les déploiements de mise à jour vers First, Fast et Broad seront tous suspendus jusqu’à ce que le problème soit résolu.
    - Vous pouvez signaler des problèmes de compatibilité en classant un ticket dans le portail Bureau géré Microsoft’administration.
    - Les mises à jour des fonctionnalités et de la qualité sont suspendues indépendamment. L’interruption est en vigueur pendant 35 jours par défaut, mais peut être réduite ou étendue selon que le problème est corrigé ou non.
3. Une fois les groupes non suspendus, le déploiement reprend en fonction de la planification du tableau.

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
>Ces périodes de report sont conçues intentionnellement pour garantir des normes élevées en matière de sécurité et de performances pour tous les utilisateurs. En outre, en fonction des données recueillies sur tous les appareils Bureau géré Microsoft et de l’étendue et de l’impact variables des mises à jour, Bureau géré Microsoft se réserve la flexibilité nécessaire pour modifier la durée des périodes de report ci-dessus pour tous les groupes de déploiement de manière ponctuelle.
>
>Bureau géré Microsoft effectue une évaluation indépendante de chaque version Windows fonctionnalité pour évaluer sa nécessité et son utilité pour ses locataires gérés. Par conséquent, Bureau géré Microsoft peuvent ou non déployer toutes les mises à jour Windows fonctionnalités. 

## <a name="windows-insider-program"></a>Programme Windows Insider

Bureau géré Microsoft ne prend pas en charge les appareils qui font partie du programme Windows Insider. Le Windows Insider est utilisé pour valider les logiciels Windows pré-version et est destiné aux appareils qui ne sont pas essentiels. Bien qu’il s’agit d’une initiative Microsoft importante, elle n’est pas destinée à un déploiement à grande échelle dans des environnements de production. 

Tous les appareils trouvés avec les builds Insider Windows peuvent être placés dans le groupe test et ne seront pas pris en charge par les utilisateurs et les contrats de niveau de service de mise à jour Bureau géré Microsoft.

## <a name="bandwidth-management"></a>Gestion de la bande passante

Nous utilisons [l’optimisation de la](/windows/deployment/update/waas-delivery-optimization) distribution pour toutes les mises à jour du système d’exploitation et des pilotes. Cela réduit la taille de téléchargement à partir du service Windows mise à jour en recherchant les mises à jour des homologues au sein du réseau d’entreprise.