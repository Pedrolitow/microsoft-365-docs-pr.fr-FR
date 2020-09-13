---
title: Microsoft 365 Apps for enterprise
description: Procédure de déploiement des applications Microsoft 365, de leur mise à jour et de la gestion des paramètres
keywords: historique des modifications
ms.service: m365-md
ms.sitesec: library
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.topic: article
ms.localizationpriority: normal
ms.openlocfilehash: 767489ba9f9ac63bc1a2d8b4999b6634335b1aef
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "47547745"
---
# <a name="microsoft-365-apps-for-enterprise"></a>Applications Microsoft 365 for entreprise

## <a name="initial-deployment"></a>Déploiement initial

Microsoft Managed Desktop garantit que les applications Microsoft 365 pour entreprise (64 bits) sont installées en tant que partie de l’image sur tous les [appareils de programme](../service-description/device-list.md). Toutes les applications suivantes doivent être présentes sur l’appareil lors de sa remise :

- Word
- Excel
- PowerPoint
- Outlook
- Publisher
- Access
- Skype Entreprise
- OneNote

Cette approche minimise l’impact sur le réseau et garantit que les utilisateurs peuvent être productifs dès qu’ils reçoivent leur appareil. Nous déployons ensuite des stratégies supplémentaires sur les appareils gérés afin de configurer les applications pour qu’elles soient utilisées.

> [!NOTE]
> Microsoft teams est déployé séparément des applications Microsoft 365 pour Enterprise et n’est pas inclus dans l’image de base. 

### <a name="available-deployment-to-users"></a>Déploiement disponible pour les utilisateurs

Si un utilisateur ne dispose pas d’applications Microsoft 365 sur son appareil pour une raison quelconque, vous pouvez utiliser un package pour rétablir l’État attendu de l’appareil. Ajoutez l’utilisateur au groupe **espace de travail moderne-bureau Office365_Install** et les applications seront disponibles dans le portail de l’entreprise.

### <a name="microsoft-365-apps-for-enterprise-32-bit"></a>Applications Microsoft 365 pour les entreprises (32 bits)

Microsoft Managed Desktop ne prend pas en charge le déploiement de la version 32 bits des applications M365 pour Enterprise.

## <a name="updates-to-microsoft-365-apps"></a>Mises à jour des applications Microsoft 365

Les applications Microsoft 365 sont configurées pour être mises à jour sur le [canal d’entreprise mensuel](https://docs.microsoft.com/deployoffice/overview-update-channels#monthly-enterprise-channel-overview). Cette pratique fournit aux utilisateurs les nouvelles fonctionnalités d’Office chaque mois, mais elles ne reçoivent qu’une seule mise à jour par mois sur un planning de publication prévisible. Les mises à jour sont publiées le deuxième mardi du mois ; ces mises à jour peuvent inclure des mises à jour de la fonctionnalité, de la sécurité et de la qualité. Ces mises à jour se produisent automatiquement et sont directement extraites du CDN Office pour ce canal spécifique.

Microsoft Managed Desktop effectue un échelonnement de chaque version pour identifier les problèmes éventuels dans votre environnement. Nous terminons le déploiement 28 jours après la publication du groupe de produits d’application Microsoft 365. Microsoft Managed Desktop planifie les versions de mise à jour de différents groupes pour permettre une validation et des tests, comme suit : 

- Test : 0 jour
- Première : 0 jour
- Rapide : 7 jours
- Large : 21 jours

Microsoft Managed Desktop définit une [Date d’échéance de mise à jour](https://docs.microsoft.com/deployoffice/configure-update-settings-microsoft-365-apps) de sept jours pour les appareils. Une fois que la mise à jour est disponible, elle doit être installée dans les sept jours. Les utilisateurs sont [avertis](https://docs.microsoft.com/deployoffice/end-user-update-notifications-microsoft-365-apps#notifications-your-users-see-when-you-set-an-update-deadline-for-microsoft-365-apps) que les mises à jour sont requises à plusieurs endroits : l’application, dans la barre d’état système 12 heures avant la date d’échéance, et ils reçoivent un avertissement 15 minutes avant la date d’échéance. Toutes les applications Microsoft 365 doivent être fermées pour que la mise à jour soit terminée.

### <a name="pausing-or-rolling-back-an-update"></a>Suspension ou annulation d’une mise à jour

Si vous devez suspendre ou restaurer la mise à jour de l’application Microsoft 365 pour une raison quelconque, mettez en file d’attente une [demande d’assistance administrative](../working-with-managed-desktop/admin-support.md) via le portail de bureau géré Microsoft.

Au cours d’une publication, Microsoft Managed Desktop surveille les taux d’erreur de toutes les applications Microsoft 365. Si nous prévoyons une différence significative en matière de qualité entre la nouvelle version et son prédécesseur, nous pouvons vous contacter via le portail d’administration de bureau géré Microsoft. En fonction de la gravité, nous vous demanderons si vous souhaitez suspendre la publication ou vous informer que nous avons pris des mesures pour limiter un problème. 

### <a name="delivery-optimization"></a>Optimisation de la remise

L’optimisation de la remise est une technologie de distribution P2P disponible dans Windows 10. Elle permet aux appareils de partager du contenu, tel que des mises à jour, que les appareils ont téléchargés à partir de Microsoft via Internet. Cela permet de réduire la bande passante du réseau, car un périphérique peut obtenir des portions de la mise à jour à partir d’un autre appareil sur son réseau local au lieu de devoir télécharger complètement la mise à jour à partir de Microsoft.

L’optimisation de la [remise](https://docs.microsoft.com/deployoffice/delivery-optimization) est activée par défaut sur les appareils exécutant Windows 10 entreprise ou Windows 10 éducation. 

## <a name="settings-managed-by-microsoft-managed-desktop"></a>Paramètres gérés par le bureau géré Microsoft

Microsoft gère certains paramètres dans le cadre du service. Microsoft Managed Desktop ne gère pas la référence de sécurité Office, mais vous pouvez en définir un vous-même en suivant les instructions indiquées dans la section [paramètres que vous gérez](#settings-you-manage) .

### <a name="update-settings"></a>Définir les paramètres de mise à jour

Microsoft Managed Desktop gère tous les [paramètres de mise à jour](https://docs.microsoft.com/deployoffice/configure-update-settings-microsoft-365-apps) pour les appareils gérés et vous devez modifier ces paramètres.

### <a name="set-updates-to-occur-automatically"></a>Définir des mises à jour automatiques

**Valeur par défaut**: activé

Cette stratégie est configurée afin de s’assurer que tous les appareils Office peuvent être maintenus à jour à partir du Cloud. 

### <a name="set-a-deadline-when-updates-have-to-be-applied"></a>Définir une date d’échéance à laquelle les mises à jour doivent être appliquées

**Valeur par défaut**: 7 jours

La stratégie **UpdateDeadline** est utilisée pour configurer la période de grâce dont disposent les utilisateurs avant qu’une mise à jour ne soit appliquée sur l’appareil. Cette stratégie d’échéance déclenche également des [notifications](https://docs.microsoft.com/deployoffice/end-user-update-notifications-microsoft-365-apps#notifications-your-users-see-when-you-set-an-update-deadline-for-microsoft-365-apps) à l’utilisateur pour les informer des modifications requises sur leur appareil.  

### <a name="defer-updates-on-a-device-for-a-period"></a>Différer les mises à jour sur un appareil pendant une période

Cette stratégie est configurée différemment pour chaque groupe d’appareils de gestion des mises à jour et est requise pour que Microsoft Managed Desktop réponde aux objectifs de mise à jour suivants :  

- Test : 0 jour
- Première : 0 jour
- Express 7 jours
- Large : 21 jours

### <a name="update-notifications-settings"></a>Mettre à jour les paramètres de notification

**Valeur par défaut**: false

Le paramètre « masquer les notifications de mise à jour » est défini sur **faux** sur les appareils de bureau gérés par Microsoft pour fournir la meilleure expérience de mise à jour pour les utilisateurs en les [avertissant](https://docs.microsoft.com/deployoffice/end-user-update-notifications-microsoft-365-apps#notifications-your-users-see-when-you-set-an-update-deadline-for-microsoft-365-apps) de la nécessité de mises à jour.

### <a name="specify-a-location-to-look-for-updates"></a>Indiquer un emplacement dans lequel rechercher des mises à jour

**Valeur par défaut**: canal d’entreprise mensuel

Une combinaison des stratégies **UpdatePath** et **UpdateChannel** est utilisée selon les besoins pour effectuer la planification des mises à jour. Ces stratégies sont définies pour s’assurer que tous les appareils Office reçoivent les mises à jour directement du CDN pour le canal d’entreprise mensuel.

### <a name="specify-the-target-version-of-microsoft-365-apps"></a>Spécifier la version cible des applications Microsoft 365

La stratégie de version cible est parfois utilisée par le bureau géré Microsoft pour restaurer ou épingler une version spécifique d’Office. 


### <a name="hide-the-option-to-enable-or-disable-office-automatic-updates"></a>Masquer l’option permettant d’activer ou de désactiver les mises à jour automatiques d’Office

**Valeur par défaut**: activé

Ce paramètre est requis pour que Microsoft Managed Desktop répond à ses objectifs de mise à jour pour les applications Microsoft 365. 

### <a name="first-run-settings"></a>Paramètres de la première exécution 

Plusieurs paramètres influent sur le comportement lors de la première exécution d’Office.

### <a name="accept-the-license-terms-on-behalf-of-the-end-user"></a>Accepter les termes du contrat de licence au nom de l’utilisateur final

**Valeur par défaut**: désactivé

La première fois qu’un utilisateur ouvre une application Microsoft 365, il est invité à accepter les termes du contrat de licence. Si vous souhaitez accepter les termes du contrat de licence au nom de vos utilisateurs, demandez une demande de service à l’équipe des opérations de bureau géré Microsoft qui demande l’activation de ce paramètre. 

### <a name="suppress-outlook-mobile-check-box"></a>Supprimer la case à cocher Outlook Mobile

**Valeur par défaut**: désactivé

La première fois qu’un utilisateur ouvre Outlook, il est invité à installer Outlook Mobile. Si vous ne souhaitez pas que vos utilisateurs voient cette case à cocher, déposez une demande de service auprès de l’équipe des opérations de bureau géré Microsoft qui demande l’activation de ce paramètre pour vos appareils. 

## <a name="other-settings"></a>Autres paramètres

Il existe d’autres paramètres d’application Microsoft 365 que le bureau géré Microsoft peut configurer en votre nom. 

### <a name="disable-personal-onedrive"></a>Désactiver OneDrive personnel

**Valeur par défaut**: désactivé

Certaines organisations concernent les utilisateurs ayant accès aux fichiers d’entreprise et personnels sur leurs appareils. Vous pouvez classer une demande de service auprès de l’équipe des opérations de bureau géré Microsoft pour demander l’activation de ce paramètre. 

## <a name="settings-you-manage"></a>Paramètres que vous gérez

Il existe de nombreuses autres stratégies que Microsoft Managed Desktop n’a pas encore définies dans le cadre de notre service. Vous pouvez configurer ces éléments à l’aide de Microsoft Intune, qui utilise le service de [stratégie de Cloud Office](https://docs.microsoft.com/DeployOffice/overview-office-cloud-policy-service#how-the-policy-configuration-is-applied) . Pour cela, procédez comme suit :

1.  Connectez-vous au centre d’administration du gestionnaire de points de terminaison Microsoft.
2.  Sélectionnez **applications > stratégies pour les applications Office > créer**
3.  Sur la page créer une configuration de **stratégie** , procédez comme suit :
    - Entrez un nom.
    - Fournissez une description (facultatif).
    - Dans **affectations**, indiquez si cette stratégie s’applique à tous les utilisateurs des applications Microsoft 365 pour Enterprise ou uniquement aux utilisateurs qui accèdent anonymement aux documents à l’aide d’Office pour le Web.
    - Sélectionnez le groupe de sécurité basé sur AAD qui est affecté à la configuration de la stratégie. Chaque configuration de stratégie ne peut être affectée qu’à un seul groupe et chaque groupe ne peut être associé qu’à une configuration de stratégie.
    - Configurez les paramètres de stratégie à inclure dans la configuration de la stratégie. Vous pouvez rechercher le nom du paramètre de stratégie pour trouver le paramètre de stratégie que vous souhaitez configurer. Vous pouvez également filtrer sur l’application, selon que la stratégie est une base de sécurité recommandée et selon que la stratégie a été configurée ou non. La colonne plateforme indique si la stratégie est appliquée aux applications Microsoft 365 pour les appareils Windows, Office pour le Web ou tous.
4.  Une fois vos sélections effectuées, sélectionnez **créer**.

> [!NOTE]
> Les stratégies de configuration Office ne prennent en charge que le déploiement basé sur un utilisateur
