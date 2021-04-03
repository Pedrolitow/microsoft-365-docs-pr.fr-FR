---
title: Outils d’évaluation de la préparation
description: Explique les deux outils, les vérifications qu’ils exécutent et la signification des résultats
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: caf9274284548a179e088131930ae832c098b521
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51579397"
---
# <a name="readiness-assessment-tools"></a>Outils d’évaluation de la préparation

Pour une expérience la plus fluide possible lorsque vous vous inscrivez au Bureau géré Microsoft, il existe des paramètres et d’autres paramètres que vous devez définir à l’avance, ainsi que certaines configurations requises pour l’appareil et le réseau. Un outil, accessible via le portail d’administration du bureau géré Microsoft, vérifie les paramètres liés à la gestion. Un autre outil, téléchargeable, vérifie les configurations réseau et les configurations requises pour chaque appareil. Vous pouvez utiliser ces outils pour vérifier ces paramètres et recevoir des étapes détaillées pour résoudre les problèmes.

## <a name="downloadable-readiness-assessment-checker-for-devices-and-network"></a>Téléchargeable readiness assessment checker for devices and network

Pour plus d’informations sur l’utilisation de l’outil de vérification de l’évaluation de la disponibilité [téléchargeable, voir Téléchargeable readiness assessment checker](readiness-assessment-downloadable.md).

## <a name="online-readiness-assessment-tool-for-management-settings"></a>Outil d’évaluation de la préparation en ligne pour les paramètres de gestion

L’outil en ligne vérifie les paramètres dans Microsoft Endpoint Manager (en particulier, Microsoft Intune), Azure Active Directory (Azure AD) et Microsoft 365 pour s’assurer qu’ils fonctionneront avec bureau géré Microsoft. [](https://aka.ms/mmdart) Bureau géré Microsoft conserve les données associées à ces vérifications pendant 12 mois après la dernière vérification dans votre organisation Azure AD (client). Après 12 mois, nous le conservons sous forme d’identification. Vous pouvez choisir de supprimer les données que nous collectons.

Toute personne ayant au moins le rôle Lecteur global ou Administrateur Intune pourra exécuter cet outil, mais deux des vérifications[(](readiness-assessment-fix.md#conditional-access-policies) les stratégies d’accès conditionnel et l’authentification [multifacteur](readiness-assessment-fix.md#multifactor-authentication) nécessitent des autorisations supplémentaires.
 
L’outil d’évaluation vérifie les éléments ci-après :

## <a name="microsoft-intune-settings"></a>Paramètres Microsoft Intune

|Chèque  |Description  |
|---------|---------|
|Profil autopilot deployment     | Vérifie que l’affectation du profil Autopilot Deployment ne s’applique pas à tous les appareils (le profil ne doit être affecté à aucun appareil bureau géré Microsoft.)        |
|Connecteurs de certificat     | Vérifie l’état des connecteurs de certificat pour s’assurer qu’ils sont actifs   |
|Accès conditionnel     | Vérifie que les stratégies d’accès conditionnel ne  sont pas affectées à tous les utilisateurs (les stratégies d’accès conditionnel ne doivent pas être affectées aux comptes de service Bureau géré Microsoft.)    |
|Stratégies de conformité des appareils     | Vérifie que les stratégies de conformité Intune  ne sont pas affectées à tous les utilisateurs (les stratégies ne doivent pas être affectées à des appareils bureau géré Microsoft.)    |
|Profils de configuration d’appareil     | Confirme que les profils de configuration ne sont pas  affectés à tous les utilisateurs ou à tous les appareils (les profils de configuration ne doivent pas être affectés à des appareils bureau géré Microsoft.)     |
|Restrictions de type d’appareil     | Vérifie que les appareils Windows 10 de votre organisation sont autorisés à s’inscrire dans Intune        |
|Page État de l’inscription     | Confirme que la page État de l’inscription n’est pas activée      |
|Inscription à Intune     | Vérifie que les appareils Windows 10 de votre organisation Azure AD sont automatiquement inscrits dans Intune         |
|Microsoft Store pour Entreprises     | Confirme que Microsoft Store pour Entreprises est activé et synchronisé avec Intune        |
|Authentification multifacteur | Vérifie que l’authentification multifacteur n’est pas appliquée aux comptes de service Bureau géré Microsoft.
|Scripts PowerShell     | Vérifie que les scripts Windows PowerShell ne *sont* pas affectés d’une manière qui ciblerait les appareils bureau géré Microsoft    |
|Région     | Vérifie que votre région est prise en charge par bureau géré Microsoft        |
|Bases de référence de sécurité     | Vérifie que le profil de base de sécurité ne cible  pas tous les utilisateurs ou tous les appareils (les stratégies de base de sécurité ne doivent pas cibler les appareils bureau géré Microsoft.)       |
|Applications Windows     | Passer en revue les applications que vous souhaitez affecter aux appareils de bureau géré Microsoft      |
|Windows Hello Entreprise     | Vérifie que Windows Hello Entreprise est activé        |
|Anneau de mise à jour Windows 10     | Vérifie que la stratégie « Anneau de mise à jour Windows 10 » d’Intune ne cible pas tous les utilisateurs ou tous les appareils (la stratégie ne doit cibler aucun appareil de bureau géré Microsoft.)      |


## <a name="azure-active-directory-settings"></a>Paramètres Azure Active Directory

|Chèque  |Description  |
|---------|---------|
|Abonnements « Ad hoc » pour Enterprise State Roaming     | Indique comment vérifier un paramètre qui (s’il a la valeur « false ») risque d’empêcher Enterprise State Roaming de fonctionner correctement  |
|Itinérance du statut Entreprise     | Indique comment vérifier que l’itinérance de l’état d’entreprise est activée       |
|Licences     | Vérifie que vous avez obtenu les [licences nécessaires](prerequisites.md#more-about-licenses)         |
|Authentification multifacteur     | Vérifie que l’authentification multifacteur n’est pas appliquée à tous les utilisateurs (l’authentification multifacteur ne doit pas être appliquée accidentellement aux comptes de service Bureau géré Microsoft.)|
|Noms de compte de sécurité   | Vérifie qu’aucun nom d’utilisateur n’entre en conflit avec ceux que Microsoft Managed Desktop réserve pour son propre usage        |
|Rôles d’administrateur de sécurité     | Confirme que les utilisateurs ayant des rôles lecteur sécurité, Opérateur de sécurité ou Lecteur global ont été affectés à ces rôles dans Microsoft Defender for Endpoint         |
|Paramètres de sécurité par défaut | Vérifie si les paramètres de sécurité par défaut de votre organisation Azure AD sont activés dans Azure Active Directory |
|Réinitialisation du mot de passe en libre-service     | Confirme que la réinitialisation du mot de passe en libre-service est activée        |
|Rôle d’utilisateur standard     | Vérifie que les utilisateurs sont des utilisateurs standard et n’ont pas de droits d’administrateur local         |


## <a name="microsoft-365-apps-for-enterprise-settings"></a>Paramètres des applications Microsoft 365 pour les entreprises

|Chèque  |Description  |
|---------|---------|
|OneDrive Entreprise     | Vérifie si OneDrive Entreprise utilise des paramètres non pris en aide.        |


Pour chaque vérification, l’outil signalera l’un des quatre résultats possibles :


|Résultat  |Signification  |
|---------|---------|
|Prêt     | Aucune action n’est requise avant de terminer l’inscription.        |
|Avertissement    | Suivez les étapes de l’outil pour une expérience de l’inscription et pour les utilisateurs. Vous *pouvez terminer* l’inscription, mais vous devez résoudre ces problèmes avant de déployer votre premier appareil.        |
|Non prêt | *L’inscription échoue* si vous ne corrigez pas ces problèmes. Suivez les étapes de l’outil pour les résoudre.        |
|Erreur | Le rôle Azure Active Director (AD) que vous utilisez ne peut pas exécuter cette vérification. |

## <a name="after-enrollment"></a>Après l’inscription

Une fois que vous avez terminé l’inscription au Bureau géré Microsoft, n’oubliez pas de revenir en arrière et d’ajuster certains paramètres Intune et Azure AD. Pour plus d’informations, voir [Ajuster les paramètres après l’inscription.](../get-started/conditional-access.md)

## <a name="steps-to-get-ready"></a>Étapes pour vous préparer

1. Passer en [revue les conditions préalables pour le Bureau géré Microsoft.](prerequisites.md)
2. Utiliser les [outils d’évaluation de la préparation.](readiness-assessment-tool.md) (Cet article)
3. [Conditions préalables pour les comptes invité](guest-accounts.md)
4. [Configuration du réseau pour Bureau géré Microsoft](network.md)
5. [Préparer les certificats et les profils réseau pour le Bureau géré Microsoft](certs-wifi-lan.md)
6. [Préparer l’accès aux ressources locales pour le Bureau géré Microsoft](authentication.md)
7. [Applications dans le Bureau géré Microsoft](apps.md)
8. [Préparer les lecteurs mappés pour le Bureau géré Microsoft](mapped-drives.md)
9. [Préparer des ressources d’impression pour le Bureau géré Microsoft](printing.md)
