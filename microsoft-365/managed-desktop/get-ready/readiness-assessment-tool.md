---
title: Outils d’évaluation de la préparation
description: Explique les deux outils, les vérifications qu’ils exécutent et la signification des résultats
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 8d949b13203aaeab51d2518f16650ba6df832195
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525637"
---
# <a name="readiness-assessment-tools"></a>Outils d’évaluation de la préparation

Pour une expérience la plus fluide possible lorsque vous vous inscrivez à Microsoft Manged Desktop, il existe des paramètres et d’autres paramètres que vous devez définir à l’avance, ainsi que certaines configurations requises pour l’appareil et le réseau.

Un outil, accessible via le portail Microsoft Manged Desktop’administration, vérifie les paramètres liés à la gestion. Un autre outil, téléchargeable, vérifie les configurations réseau et les configurations requises pour chaque appareil. Vous pouvez utiliser ces outils pour vérifier ces paramètres et recevoir des étapes détaillées pour résoudre les problèmes.

## <a name="downloadable-readiness-assessment-checker-for-devices-and-network"></a>Téléchargeable readiness assessment checker for devices and network

Pour plus d’informations sur l’utilisation de l’outil de vérification de l’évaluation de la disponibilité [téléchargeable, voir Téléchargeable readiness assessment checker](readiness-assessment-downloadable.md).

## <a name="online-readiness-assessment-tool-for-management-settings"></a>Outil d’évaluation de la préparation en ligne pour les paramètres de gestion

L’outil [en](https://aka.ms/mmdart) ligne vérifie les paramètres dans Microsoft Endpoint Manager (en particulier, Microsoft Intune), Azure Active Directory (Azure AD) et Microsoft 365 pour s’assurer qu’ils fonctionneront avec Microsoft Manged Desktop.

Microsoft Manged Desktop conserve les données associées à ces vérifications pendant 12 mois après la dernière vérification dans votre organisation Azure AD (client). Au bout de 12 mois, nous le conservons sous forme d’identification. Vous pouvez choisir de supprimer les données que nous collectons.

Toute personne ayant au moins le rôle Lecteur global ou Administrateur Intune peut exécuter cet outil, mais deux des vérifications [(](readiness-assessment-fix.md#conditional-access-policies) stratégies d’accès conditionnel et authentification [multifacteur](readiness-assessment-fix.md#multi-factor-authentication)) nécessitent des autorisations supplémentaires.

> [!IMPORTANT]  
> L’outil d’évaluation de la préparation en ligne vous permet de vérifier votre préparation à l’inscription Microsoft Manged Desktop pour la première fois. Si votre organisation est déjà inscrite dans Microsoft Manged Desktop, n’utilisez pas cet outil.

L’outil d’évaluation vérifie les éléments ci-après :

## <a name="microsoft-intune-settings"></a>Microsoft Intune paramètres

Les paramètres de Microsoft Intune suivants sont les suivants :

| Chèque | Description |
| ------ | ------ |
| Profil Autopilot Deployment | Vérifie que l’affectation du profil Autopilot Deployment ne s’applique pas à tous les appareils. <br><br> Le profil ne **doit être** affecté à aucun Microsoft Manged Desktop périphériques. |
| Connecteurs de certificat | Vérifie l’état des connecteurs de certificat pour s’assurer qu’ils sont actifs. |
| Accès conditionnel | Vérifie que les stratégies d’accès conditionnel ne sont pas affectées à tous les utilisateurs. <br><br> Les stratégies d’accès **conditionnel** ne doivent pas être affectées Microsoft Manged Desktop comptes de service. |
| Stratégies de conformité des appareils | Vérifie que les stratégies de conformité Intune ne sont pas affectées à tous les utilisateurs. <br><br> Les stratégies ne **doivent être** affectées à aucun Microsoft Manged Desktop périphériques. |
| Profils de configuration d’appareil | Confirme que les profils de configuration ne sont pas affectés à tous les utilisateurs ou à tous les appareils. <br><br> Les profils de **configuration ne doivent** pas être affectés à Microsoft Manged Desktop appareils mobiles. |
| Restrictions de type d’appareil | Vérifie que Windows 10 appareils de votre organisation sont autorisés à s’inscrire dans Intune. |
| Page État de l’inscription | Confirme que la page État de l’inscription n’est pas activée. |
| Inscription Intune | Vérifie que les Windows 10 de votre organisation Azure AD sont automatiquement inscrits dans Intune. |
| Microsoft Store pour Entreprises | Confirme que Microsoft Store pour Entreprises est activé et synchronisé avec Intune. |
| Authentification multifacteur | Vérifie que l’authentification multifacteur n’est pas appliquée Microsoft Manged Desktop comptes de service. |
| Scripts PowerShell | Vérifie que Windows PowerShell scripts ne **sont** pas affectés d’une manière qui ciblerait Microsoft Manged Desktop périphériques. |
| Région | Vérifie que votre région est prise en charge par Microsoft Manged Desktop. |
| Bases de référence de sécurité | Vérifie que le profil de base de sécurité ne cible pas tous les utilisateurs ou tous les appareils. <br><br> Les stratégies de base de sécurité **ne doivent** cibler Microsoft Manged Desktop appareils mobiles. |
| Windows applications | Examinez les applications que vous souhaitez affecter à Microsoft Manged Desktop appareils. |
| Windows Hello Entreprise | Vérifie que Windows Hello entreprise est activé. |
| Windows 10 sonnerie de mise à jour | Vérifie que la stratégie « sonnerie Windows 10 mise à jour » d’Intune ne cible pas tous les utilisateurs ou tous les appareils. <br><br> La stratégie ne **doit cibler** aucun Microsoft Manged Desktop appareils. |

## <a name="azure-active-directory-settings"></a>Azure Active Directory paramètres

Les paramètres de Azure Active Directory suivants sont les suivants :

| Chèque | Description |
| ----- | ----- |
| Abonnements « ad hoc » pour l’itinérance Enterprise’état | Indique comment vérifier un paramètre qui, s’il est « false », risque d’empêcher Enterprise’itinérance d’état fonctionne correctement. |
| Itinérance du statut Entreprise | Indique comment vérifier que l’itinérance Enterprise’état est activée. |
| Licences | Vérifie que vous avez obtenu les [licences nécessaires](prerequisites.md#more-about-licenses). |
| Authentification multifacteur | Vérifie que l’authentification multifacteur n’est pas appliquée à tous les utilisateurs. <br><br> L’authentification multifacteur **ne doit pas** être appliquée accidentellement Microsoft Manged Desktop comptes de service. |
| Noms de compte de sécurité | Vérifie qu’aucun nom d’utilisateur n’entre en conflit avec ceux Microsoft Manged Desktop réserve pour son propre usage. |
| Rôles d’administrateur de sécurité | Confirme que les utilisateurs  ayant des rôles lecteur sécurité, Opérateur de sécurité ou Lecteur global ont été affectés à ces rôles dans Microsoft Defender for Endpoint. |
| Paramètres de sécurité par défaut | Vérifie si les paramètres Azure AD sécurité de votre organisation sont activés dans Azure Active Directory. |
| Réinitialisation du mot de passe en libre-service | Confirme que la réinitialisation du mot de passe en libre-service est activée. |
| Rôle d’utilisateur standard | Vérifie que les utilisateurs sont des utilisateurs standard et n’ont pas de droits d’administrateur local. |

## <a name="microsoft-365-apps-for-enterprise-settings"></a>Microsoft 365 Apps pour Enterprise paramètres

Voici les paramètres de Microsoft 365 Apps’Enterprise suivants :

| Chèque | Description |
| ----- | ----- |
| OneDrive Entreprise | Vérifie si OneDrive Entreprise utilise des paramètres non pris en aide. |

Pour chaque vérification, l’outil signalera l’un des quatre résultats possibles :

| Résultat | Signification |
| ----- | ----- |
| Prêt | Aucune action n’est requise avant de terminer l’inscription. |
| Avertissement | Suivez les étapes de l’outil pour une expérience de l’inscription et pour les utilisateurs. <br><br> Vous *pouvez terminer* l’inscription, mais vous devez résoudre ces problèmes avant de déployer votre premier appareil. |
| Non prêt | **L’inscription échoue** si vous ne corrigez pas ces problèmes. <br><br> Suivez les étapes de l’outil pour les résoudre. |
| Erreur | Le rôle Azure Active Director (AD) que vous utilisez ne peut pas exécuter cette vérification. |

## <a name="after-enrollment"></a>Après l’inscription

Une fois que vous avez terminé l’inscription Microsoft Manged Desktop, n’oubliez pas de revenir en arrière et d’ajuster certains paramètres Intune et Azure AD paramètres. Pour plus d’informations, voir [Ajuster les paramètres après l’inscription](../get-started/conditional-access.md).

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Étapes pour vous préparer à la Microsoft Manged Desktop

1. Examinez [Configuration requise pour le Bureau géré Microsoft](prerequisites.md).
2. Exécuter les outils d’évaluation de la préparation (cet article).
3. Achetez [Portail d’entreprise](../get-started/company-portal.md).
4. Passez en revue les [prérequis pour les comptes invités](guest-accounts.md).
5. Vérifiez la[configuration réseau](network.md).
6. [Préparer les certificats et les profils réseau](certs-wifi-lan.md).
7. [Préparer l’accès utilisateur aux données](authentication.md).
8. [Préparer les applications](apps.md).
9. [Préparer les lecteurs mappés](mapped-drives.md).
10. [Préparer les ressources d’impression](printing.md).
11. [noms d’appareil](address-device-names.md) d’une adresse.
