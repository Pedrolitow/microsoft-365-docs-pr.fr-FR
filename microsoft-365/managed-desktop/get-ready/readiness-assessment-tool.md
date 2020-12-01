---
title: Outil d’évaluation de la préparation
description: Explique les vérifications que l’outil exécute et la signification des résultats
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: e2d1c68c3fe963c957e4c3e18fce441b92c96bf1
ms.sourcegitcommit: d3ca8021f7da00a474ac14aac5f1358204a848f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "49519820"
---
# <a name="readiness-assessment-tool"></a>Outil d’évaluation de la préparation

Pour une plus bonne expérience possible lors de l’inscription au bureau géré Microsoft, il existe un certain nombre de paramètres et d’autres paramètres que vous devez définir à l’avance. Vous pouvez utiliser cet outil pour vérifier ces paramètres et recevoir des instructions détaillées pour les corriger.

L’outil vérifie les paramètres dans le gestionnaire de points de terminaison Microsoft (en particulier Microsoft Intune), Azure Active Directory (Azure AD) et Microsoft 365 pour s’assurer qu’ils fonctionneront avec Microsoft Managed Desktop. Le bureau géré Microsoft conserve les données associées à ces vérifications pendant 12 mois après la dernière exécution d’une vérification dans votre organisation Azure AD. Au bout de 12 mois, nous les conservent dans un formulaire déidentifié.  Vous pouvez choisir de supprimer les données collectées.

Tout utilisateur disposant au moins du rôle d’administrateur Intune pourra exécuter cet outil, mais deux des vérifications ([stratégies d’accès conditionnel](readiness-assessment-fix.md#conditional-access-policies) et [authentification multifacteur](readiness-assessment-fix.md#multi-factor-authentication) nécessitent des autorisations supplémentaires.
 
L’outil d’évaluation vérifie ces éléments :

## <a name="microsoft-intune-settings"></a>Paramètres Microsoft Intune

|Vérifier  |Description  |
|---------|---------|
|Profil de déploiement de AutoPilot     | Vérifie que l’attribution du profil de déploiement AutoPilot ne s’applique pas à tous les appareils (le profil ne doit *pas* être attribué à des appareils de bureau gérés par Microsoft).       |
|Connecteurs de certificats     | Vérifie l’état des connecteurs de certificat pour s’assurer qu’ils sont actifs   |
|Accès conditionnel     | Vérifie que les stratégies d’accès conditionnel ne sont pas affectées à tous les utilisateurs (les stratégies d’accès conditionnel ne doivent *pas* être affectées à des comptes de service de bureau géré Microsoft.)    |
|Stratégies de conformité des appareils     | Vérifie que les stratégies de conformité Intune ne sont pas affectées à tous les utilisateurs (les stratégies ne doivent *pas* être affectées à des appareils de bureau gérés par Microsoft).    |
|Profils de configuration d’appareil     | Confirme que les profils de configuration ne sont pas affectés à tous les utilisateurs ou tous les appareils (les profils de configuration ne doivent *pas* être attribués à des appareils de bureau gérés par Microsoft).     |
|Restrictions de type de périphérique     | Vérifie que les appareils Windows 10 de votre organisation sont autorisés à s’inscrire dans Intune        |
|Page d’état d’enregistrement     | Confirme que la page d’état d’enregistrement n’est pas activée.      |
|Enregistrement Intune     | Vérifie que les appareils Windows 10 de votre organisation Azure AD sont automatiquement apportés dans Intune         |
|Microsoft Store pour Entreprises     | Confirme que Microsoft Store pour les entreprises est activé et synchronisé avec Intune        |
|Authentification multifacteur | Vérifie que l’authentification multifacteur n’est pas appliquée aux comptes de service de bureau géré Microsoft.
|Scripts PowerShell     | Vérifie que les scripts Windows PowerShell *ne sont pas* affectés de manière à cibler les périphériques de bureau géré Microsoft.    |
|Région     | Vérifie que votre région est prise en charge par le bureau géré Microsoft        |
|Lignes de base de sécurité     | Vérifie que le profil de la base de sécurité ne cible pas tous les utilisateurs ou tous les appareils (les stratégies de base de sécurité ne doivent *pas* viser les appareils de bureau gérés par Microsoft).       |
|Applications Windows     | Examiner les applications que vous souhaitez affecter aux appareils de bureau gérés Microsoft      |
|Windows Hello Entreprise     | Vérifie que Windows Hello entreprise est activé        |
|Sonnerie de mise à jour Windows 10     | Vérifie que la stratégie « Windows 10 Update Ring » de Intune ne cible pas tous les utilisateurs ou tous les appareils (la stratégie ne doit *pas* cibler les appareils de bureau gérés par Microsoft).     |


## <a name="azure-active-directory-settings"></a>Paramètres Azure Active Directory

|Vérifier  |Description  |
|---------|---------|
|Abonnements ad hoc pour l’itinérance de l’état de l’entreprise     | Indique comment vérifier un paramètre qui, s’il est défini sur « false », peut empêcher le fonctionnement correct de l’état d’entreprise.  |
|Itinérance du statut Entreprise     | Indique comment vérifier que l’itinérance de l’état de l’entreprise est activée       |
|Licences     | Vérifie que vous avez obtenu les [licences](prerequisites.md#more-about-licenses) nécessaires         |
|Authentification multifacteur     | Vérifie que l’authentification multifacteur n’est pas appliquée à tous les utilisateurs (l’authentification multifacteur ne doit pas être appliquée accidentellement aux comptes de service de bureau géré Microsoft.)|
|Noms des comptes de sécurité   | Vérifie qu’aucun nom d’utilisateur n’est en conflit avec ceux que Microsoft Managed Desktop réserve pour sa propre utilisation.        |
|Rôles d’administrateur de sécurité     | Confirme que les utilisateurs ayant des rôles de lecteur de sécurité, d’opérateur de sécurité ou de lecteur global ont reçu ces rôles dans Microsoft Defender pour le point de terminaison.         |
|Paramètres de sécurité par défaut | Vérifie si les paramètres de sécurité par défaut de votre organisation Azure AD sont activés dans Azure Active Directory |
|Réinitialisation du mot de passe en libre-service     | Confirme que la réinitialisation du mot de passe en libre-service est activée        |
|Rôle d’utilisateur standard     | Vérifie que les utilisateurs sont des utilisateurs standard et qu’ils ne disposent pas de droits d’administrateur local         |


## <a name="microsoft-365-apps-for-enterprise-settings"></a>Paramètres des applications Microsoft 365 pour l’entreprise

|Vérifier  |Description  |
|---------|---------|
|OneDrive Entreprise     | Vérifie si OneDrive entreprise utilise des paramètres non pris en charge.        |


Pour chaque vérification, l’outil signale l’un des quatre résultats possibles :


|Résultat  |Signification  |
|---------|---------|
|Prêt     | Aucune action n’est requise avant la fin de l’enregistrement.        |
|OpenSSL    | Suivez les étapes de l’outil pour une expérience optimale avec l’enregistrement et pour les utilisateurs. Vous *pouvez* effectuer l’opération d’enregistrement, mais vous devez résoudre ces problèmes avant de déployer votre premier périphérique.        |
|Non prêt | L' *enregistrement échoue* si vous ne résolvez pas ces problèmes. Suivez les étapes de l’outil pour les résoudre.        |
|Erreur | Le rôle Azure active Director (AD) que vous utilisez ne dispose pas des autorisations suffisantes pour effectuer cette vérification. |
