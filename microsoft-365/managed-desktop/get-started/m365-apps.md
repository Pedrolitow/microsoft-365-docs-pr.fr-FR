---
title: Microsoft 365 Apps for enterprise
description: Comment déployer Microsoft 365 Apps, comment elles sont mises à jour et comment les paramètres sont gérés
keywords: historique des modifications
ms.service: m365-md
ms.sitesec: library
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.topic: article
ms.localizationpriority: normal
ms.openlocfilehash: 26e62d6e59f1f90e35d9e18e6eed917a66876645
ms.sourcegitcommit: 375168ee66be862cf3b00f2733c7be02e63408cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50453920"
---
# <a name="microsoft-365-apps-for-enterprise"></a>Applications Microsoft 365 for entreprise

## <a name="initial-deployment"></a>Déploiement initial

Bureau géré Microsoft garantit que les applications Microsoft 365 pour les entreprises (64 bits) sont installées dans le cadre de l’image sur tous les [appareils du programme.](../service-description/device-list.md) Toutes les applications suivantes doivent être présentes sur l’appareil lorsqu’il est remis :

- Word
- Excel
- PowerPoint
- Outlook
- Éditeur
- Access
- Skype Entreprise
- OneNote

Cette approche réduit l’impact sur le réseau et garantit que les utilisateurs peuvent être productifs dès qu’ils reçoivent leur appareil. Nous déployons ensuite d’autres stratégies sur les appareils gérés pour configurer les applications à utiliser.

> [!NOTE]
> Microsoft Teams est déployé séparément de Microsoft 365 Apps for enterprise et n’est pas inclus dans l’image de base. 

### <a name="available-deployment-to-users"></a>Déploiement disponible pour les utilisateurs

Si un utilisateur n’a pas Microsoft 365 Apps sur son appareil pour une raison quelconque, vous pouvez utiliser un package pour revenir à l’état attendu de l’appareil. Ajoutez l’utilisateur au groupe **Moderne Workplace-Office-Office365_Install** et les applications seront disponibles dans le portail d’entreprise.

### <a name="microsoft-365-apps-for-enterprise-32-bit"></a>Applications Microsoft 365 pour les entreprises (32 bits)

Bureau géré Microsoft ne prend pas en charge le déploiement de la version 32 bits de M365 Apps for enterprise.

## <a name="updates-to-microsoft-365-apps"></a>Mises à jour de Microsoft 365 Apps

Les applications Microsoft 365 sont définies pour être mises à jour sur le [canal d’entreprise mensuel.](https://docs.microsoft.com/deployoffice/overview-update-channels#monthly-enterprise-channel-overview) Cette pratique fournit à vos utilisateurs de nouvelles fonctionnalités Office chaque mois, mais ils ne reçoivent qu’une seule mise à jour par mois selon un calendrier de publication prévisible. Les mises à jour sont publiées le deuxième mardi du mois . Ces mises à jour peuvent inclure des mises à jour de fonctionnalité, de sécurité et de qualité. Ces mises à jour se produisent automatiquement et sont directement tirées du CDN Office pour ce canal spécifique.

Bureau géré Microsoft échelons chaque version pour identifier les problèmes potentiels dans votre environnement. Le déploiement est terminé 28 jours après la publication du groupe de produits Microsoft 365 App. Bureau géré Microsoft planifiera les mises à jour publiées pour différents groupes afin de laisser le temps à la validation et aux tests comme suit : 

- Test : zéro jour
- First: zero days
- Rapide : 3 jours
- Étendue : 7 jours

Bureau géré Microsoft définit une échéance de mise à jour de sept jours [pour](https://docs.microsoft.com/deployoffice/configure-update-settings-microsoft-365-apps) les appareils. Une fois la mise à jour disponible, elle doit être installée dans un délai de sept jours. Les [](https://docs.microsoft.com/deployoffice/end-user-update-notifications-microsoft-365-apps#notifications-your-users-see-when-you-set-an-update-deadline-for-microsoft-365-apps) utilisateurs sont avertis que des mises à jour sont requises à plusieurs emplacements : l’application, dans la bac système 12 heures avant l’échéance, et ils reçoivent un avertissement de 15 minutes avant l’échéance. Toutes les applications Microsoft 365 doivent être fermées pour que la mise à jour soit terminée.

### <a name="pausing-or-rolling-back-an-update"></a>Interruption ou interruption d’une mise à jour

Si vous devez suspendre ou revenir à la mise à jour de l’application Microsoft 365 pour une raison quelconque, déposez une demande de [support](../working-with-managed-desktop/admin-support.md) administrateur via le portail Bureau géré Microsoft.

Lors d’une publication, Bureau géré Microsoft surveille les taux d’erreur de toutes les applications Microsoft 365. Si nous notons une différence significative de qualité entre la nouvelle version et son prédécesseur, nous pouvons vous contacter via le portail d’administration du bureau géré Microsoft. En fonction de la gravité, nous vous demandons si vous souhaitez suspendre la publication ou nous vous informons que nous avons pris des mesures pour atténuer un problème. 

### <a name="delivery-optimization"></a>Optimisation de la distribution

L’optimisation de la distribution est une technologie de distribution pair à pair disponible dans Windows 10. Il permet aux appareils de partager du contenu, tel que des mises à jour, que les appareils ont téléchargés à partir de Microsoft sur Internet. Son utilisation peut aider à réduire la bande passante réseau, car un appareil peut obtenir des parties de la mise à jour à partir d’un autre appareil sur son réseau local au lieu de devoir télécharger entièrement la mise à jour à partir de Microsoft.

[L’optimisation de](https://docs.microsoft.com/deployoffice/delivery-optimization) la distribution est activée par défaut sur les appareils exécutant les éditions Windows 10 Entreprise ou Windows 10 Éducation. 

## <a name="settings-managed-by-microsoft-managed-desktop"></a>Paramètres gérés par Bureau géré Microsoft

Microsoft gère certains paramètres dans le cadre du service. Bureau géré Microsoft ne gère pas une ligne de base de sécurité Office, mais vous pouvez en définir une vous-même en suivant les instructions de la section [Paramètres que vous gérez.](#settings-you-manage)

### <a name="update-settings"></a>Définir les paramètres de mise à jour

Bureau géré Microsoft gère tous les [paramètres de](https://docs.microsoft.com/deployoffice/configure-update-settings-microsoft-365-apps) mise à jour pour les appareils gérés et vous devez modifier ces paramètres.

### <a name="set-updates-to-occur-automatically"></a>Définir des mises à jour automatiques

**Valeur par défaut**: Activé

Cette stratégie est configurée pour garantir que tous les appareils Office peuvent être tenus à jour à partir du cloud. 

### <a name="set-a-deadline-when-updates-have-to-be-applied"></a>Définir une échéance lorsque des mises à jour doivent être appliquées

**Valeur par défaut**: 7 jours

La **stratégie UpdateDeadline** permet de configurer la période de grâce dont les utilisateurs ont besoin avant l’application d’une mise à jour sur l’appareil. Cette stratégie d’échéance déclenche également des [notifications à](https://docs.microsoft.com/deployoffice/end-user-update-notifications-microsoft-365-apps#notifications-your-users-see-when-you-set-an-update-deadline-for-microsoft-365-apps) l’utilisateur pour l’informer des modifications requises sur son appareil.  

### <a name="defer-updates-on-a-device-for-a-period"></a>Différer les mises à jour d’un appareil pendant un certain temps

Cette stratégie est configurée différemment pour chaque groupe d’appareils de gestion des mises à jour et est requise pour que Le Bureau géré Microsoft réponde à ses objectifs de mise à jour :  

- Test : zéro jour
- First: zero days
- 7 jours rapides
- Étendue : 21 jours

### <a name="update-notifications-settings"></a>Mettre à jour les paramètres des notifications

**Valeur par défaut**: False

Le paramètre « Masquer les notifications de mise à jour » est définie [](https://docs.microsoft.com/deployoffice/end-user-update-notifications-microsoft-365-apps#notifications-your-users-see-when-you-set-an-update-deadline-for-microsoft-365-apps) sur **False** sur les appareils de bureau géré Microsoft pour offrir la meilleure expérience de mise à jour aux utilisateurs en les avertissant lorsque des mises à jour sont requises.

### <a name="specify-a-location-to-look-for-updates"></a>Indiquer un emplacement dans lequel rechercher des mises à jour

**Valeur par défaut**: Canal Entreprise mensuel

Une combinaison des **stratégies UpdatePath** et **UpdateChannel** est utilisée selon les besoins pour réaliser la planification des mises à jour. Ces stratégies sont définies pour s’assurer que tous les appareils Office reçoivent les mises à jour directement à partir du CDN pour le canal d’entreprise mensuel.

### <a name="specify-the-target-version-of-microsoft-365-apps"></a>Spécifier la version cible de Microsoft 365 Apps

La stratégie de version cible est parfois utilisée par Le Bureau géré Microsoft afin de revenir en arrière ou d’épingler une version spécifique d’Office. 


### <a name="hide-the-option-to-enable-or-disable-office-automatic-updates"></a>Masquer l’option permettant d’activer ou de désactiver les mises à jour automatiques d’Office

**Valeur par défaut**: Activé

Ce paramètre est requis pour que Le Bureau géré Microsoft réponde à ses objectifs de mise à jour pour les applications Microsoft 365. 

### <a name="first-run-settings"></a>Paramètres de première run 

Plusieurs paramètres affectent le comportement la première fois qu’Office est exécuté.

### <a name="accept-the-license-terms-on-behalf-of-the-end-user"></a>Accepter les termes du contrat de licence pour le compte de l’utilisateur final

**Valeur par défaut**: Disabled

La première fois qu’un utilisateur ouvre une application Microsoft 365, il est invité à accepter les termes du contrat de licence. Si vous souhaitez accepter les termes du contrat de licence pour le compte de vos utilisateurs, déposez une demande de service auprès de l’équipe Microsoft Managed Desktop Operations pour demander l’autorisation de ce paramètre. 

### <a name="suppress-outlook-mobile-check-box"></a>Supprimer la case à cocher Outlook Mobile

**Valeur par défaut**: Disabled

La première fois qu’un utilisateur ouvre Outlook, il est invité à installer Outlook Mobile. Si vous ne souhaitez pas que vos utilisateurs voient cette case à cocher, déposez une demande de service auprès de l’équipe Microsoft Managed Desktop Operations pour demander que ce paramètre soit activé pour vos appareils. 

## <a name="other-settings"></a>Autres paramètres

Il existe d’autres paramètres de l’application Microsoft 365 que Bureau géré Microsoft peut éventuellement configurer en votre nom. 

### <a name="disable-personal-onedrive"></a>Désactiver OneDrive personnel

**Valeur par défaut**: Disabled

Certaines organisations sont préoccupés par le fait que les utilisateurs ont accès aux fichiers d’entreprise et personnels sur leurs appareils. Vous pouvez déposer une demande de service auprès de l’équipe Microsoft Managed Desktop Operations pour demander l’activer. 

## <a name="settings-you-manage"></a>Paramètres que vous gérez

Il existe de nombreuses autres stratégies que Bureau géré Microsoft n’a pas encore définies dans le cadre de notre service. Vous pouvez configurer ces stratégies à l’aide de Microsoft Intune, qui utilise le service de stratégie [cloud Office.](https://docs.microsoft.com/DeployOffice/overview-office-cloud-policy-service#how-the-policy-configuration-is-applied) Pour définir ces stratégies, suivez les étapes suivantes :

1.  Connectez-vous au Centre d’administration Microsoft Endpoint Manager.
2.  Sélectionner **des stratégies > applications pour les applications Office > créer**
3.  Dans la page **Créer une** configuration de stratégie, faites les choses suivantes :
    - Entrez un nom.
    - Fournissez une description (facultative).
    - Dans **les affectations,** choisissez si cette stratégie s’applique à tous les utilisateurs de Microsoft 365 Apps pour entreprise, ou uniquement aux utilisateurs qui accèdent anonymement aux documents à l’aide d’Office pour le web.
    - Sélectionnez le groupe de sécurité basé sur AAD affecté à la configuration de la stratégie. Chaque configuration de stratégie ne peut être affectée qu’à un seul groupe, et chaque groupe ne peut être affecté qu’à une seule configuration de stratégie.
    - Configurez les paramètres de stratégie à inclure dans la configuration de stratégie. Vous pouvez effectuer une recherche sur le nom du paramètre de stratégie pour trouver le paramètre de stratégie que vous souhaitez configurer. Vous pouvez également filtrer l’application, si la stratégie est une ligne de base de sécurité recommandée et si la stratégie a été configurée. La colonne de plateforme indique si la stratégie est appliquée aux applications Microsoft 365 pour les appareils Windows, Office pour le web ou tous.
4.  Une fois que vous avez effectué vos sélections, choisissez **Créer.**

> [!NOTE]
> Les stratégies de configuration Office ne supportent que le déploiement basé sur l’utilisateur
