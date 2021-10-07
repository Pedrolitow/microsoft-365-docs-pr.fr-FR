---
title: Résumé des Microsoft 365 pour la sécurité de l’entreprise pour Contoso Corporation
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
ms.date: 10/02/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Comment Contoso utilise les fonctionnalités de sécurité de Microsoft 365 entreprise.
ms.openlocfilehash: f4d35ef3c5b862b42bf0a995f25b29c26eedd408
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60152741"
---
# <a name="summary-of-microsoft-365-for-enterprise-security-for-the-contoso-corporation"></a>Résumé des Microsoft 365 pour la sécurité de l’entreprise pour Contoso Corporation

Pour obtenir l’approbation du déploiement de Microsoft 365 entreprise, le service de sécurité informatique de Contoso a effectué un examen approfondi de la sécurité. Ils ont identifié les exigences de sécurité suivantes pour le cloud :

- Utilisez les méthodes d’authentification les plus fortes pour l’accès des employés aux ressources cloud.
- Assurez-vous que les PC et les appareils mobiles se connectent aux applications et y accèdent de manière sécurisée.
- Protéger les PC et les e-mails contre les programmes malveillants.
- Les autorisations sur les biens numériques basés sur le cloud définissent qui peut accéder à quoi et ce qu’ils peuvent faire, et sont conçues pour l’accès selon le moindre privilège
- Les biens numériques sensibles et hautement réglementés sont étiquetés, chiffrés et stockés dans des emplacements sécurisés.
- Les biens numériques hautement réglementés sont protégés par un chiffrement et des autorisations supplémentaires.
- Le personnel de sécurité informatique peut surveiller la posture de sécurité actuelle à partir des tableaux de bord centraux et être averti des événements de sécurité pour une réponse et une atténuation rapides.

## <a name="the-contoso-path-to-microsoft-365-security-readiness"></a>Chemin d’accès De Contoso à la préparation Microsoft 365 sécurité

Contoso a suivi ces étapes pour préparer sa sécurité pour son déploiement de Microsoft 365 entreprise :

1. Limiter les comptes d’administrateur pour le cloud

   Contoso a réalisé un examen approfondi de ses comptes d’administrateur des services de domaine Active Directory (AD DS) existants et a mis en place une série de groupes et comptes d’administrateur cloud dédiés.

2. Classer les données en trois niveaux de sécurité

   Contoso a fait un examen approfondi et a déterminé les trois niveaux, qui ont été utilisés pour identifier les Microsoft 365 pour les fonctionnalités d’entreprise afin de protéger les données les plus précieuses.

3. Déterminer les stratégies d’accès, de rétention et de protection des informations pour les niveaux de données

   En fonction des niveaux de données, Contoso a déterminé des exigences détaillées pour qualifier les futures charges de travail informatiques déplacées vers le cloud.

Pour respecter les meilleures pratiques et les Microsoft 365 de sécurité pour les besoins de déploiement d’entreprise, les administrateurs de la sécurité Contoso et son service informatique ont déployé de nombreuses fonctionnalités et fonctionnalités de sécurité, comme décrit dans les sections suivantes.

## <a name="identity-and-access-management"></a>Gestion des identités et des accès 

- Comptes d’administrateur général dédiés avec l’authentification multifacteur (MFA) et Azure AD Privileged Identity Management (PIM)

  Au lieu d’attribuer le rôle d’administrateur général à des comptes d’utilisateurs quotidiens, Contoso a créé trois comptes d’administrateur général dédiés avec des mots de passe forts. Les comptes sont protégés par Azure AD Multi-Factor Authentication (MFA) et Azure Active Directory (Azure AD) Privileged Identity Management (PIM). *PIM est uniquement disponible avec Microsoft 365 E5.*

  La signature avec **un administrateur Azure AD DC** ou un compte d’administrateur **global** est effectuée uniquement pour des tâches administratives spécifiques. Les mots de passe sont connus uniquement du personnel désigné et ne peuvent être utilisés que pendant une période configurée dans Azure AD PIM.

  Les administrateurs de sécurité Contoso ont attribué des rôles d’administrateur inférieurs aux comptes qui sont appropriés à la fonction de travail de ce travailleur de l’informatique.

  Si vous souhaitez en savoir plus, consultez l’article [À propos des rôles d’administrateur Microsoft 365](/office365/admin/add-users/about-admin-roles).

- Authentification multifacteur pour tous les comptes d’utilisateur

  L' multi-fa ajoute une couche de protection supplémentaire au processus de signature. Il exige que les utilisateurs reconnaissent un appel téléphonique, un SMS ou une notification d’application sur leur smartphone après avoir entré correctement leur mot de passe. Avec l’mf, les comptes d’utilisateur Azure AD sont protégés contre la connectez-vous non autorisée, même si un mot de passe de compte est compromis.

   - Pour se protéger contre la compromission de l’abonnement Microsoft 365, Contoso requiert l’mfmf sur tous les comptes d’administrateur **Azure AD DC** ou d’administrateur global. 
   - Pour se protéger contre les attaques par hameçonnage, pendant lesquelles un utilisateur malveillant compromet les informations d’identification d’une personne approuvée dans l’organisation et envoie des e-mails malveillants, Contoso a activé la MFA sur tous les comptes d’utilisateur, y compris ceux des gestionnaires et de la direction.

- Accès plus sûr aux périphériques et aux applications grâce à des stratégies d’accès conditionnel

  Contoso utilise les [stratégies d’accès conditionnel](../security/office-365-security/microsoft-365-policies-configurations.md) pour l’identité, les périphériques, Exchange Online et SharePoint. Les stratégies d’accès conditionnel pour l’identité obligent les utilisateurs à haut risque à modifier leurs mots de passe et empêchent les clients d’utiliser des applications qui ne prennent pas en charge l’authentification moderne. Les stratégies pour les périphériques incluent la définition des applications approuvées et nécessitent des PC et des appareils mobiles compatibles. Les stratégies d’accès conditionnel pour Exchange Online permettent de bloquer les clients ActiveSync et de configurer le chiffrement de messages Office 365. Les stratégies d’accès conditionnel pour SharePoint incluent une protection supplémentaire pour les sites sensibles et hautement réglementés.

- Windows Hello Entreprise

  Contoso a déployé [Windows Hello](/windows/security/identity-protection/hello-for-business/hello-identity-verification) entreprise pour éliminer le besoin de mots de passe par le biais d’une authentification forte à deux facteurs sur les PC et les appareils mobiles exécutant Windows 10 Entreprise.

- Windows Defender Credential Guard

  Pour bloquer les attaques ciblées et les programmes malveillants en cours d’exécution dans le système d’exploitation avec des privilèges d’administration, Contoso a activé Windows Defender [Credential Guard](/windows/security/identity-protection/credential-guard/credential-guard) via la stratégie de groupe AD DS.

## <a name="threat-protection"></a>Protection contre les menaces

- Protection contre les programmes malveillants avec Antivirus Windows Defender

  Contoso utilise [Antivirus Windows Defender](/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10) pour assurer la protection contre les programmes malveillants et la gestion anti-programme malveillant pour les PC et les périphériques exécutant Windows 10 Entreprise.

- Sécuriser le flux de messagerie et l’enregistrement d’audit des boîtes aux lettres avec Microsoft Defender pour Office 365 

  Contoso utilise Exchange Online Protection et Defender pour [Office 365](/office365/securitycompliance/office-365-atp) protection contre les programmes malveillants inconnus, les virus et les URL malveillantes transmises par courrier électronique.

  Contoso a également activé l’enregistrement d’audit de boîte aux lettres pour identifier les personnes qui se connectent aux boîtes aux lettres des utilisateurs, envoient des messages et effectuent d’autres activités effectuées par le propriétaire de la boîte aux lettres, un utilisateur délégué ou un administrateur.

- Surveillance et prévention des attaques avec l’examen et réponse contre les menaces Office 365

  Contoso [](/office365/securitycompliance/office-365-ti) utilise l Office 365 et la réponse aux menaces pour protéger les utilisateurs en leur permettant d’identifier et de traiter facilement les attaques, et d’empêcher les attaques futures.

- Protection contre les attaques sophistiquées avec Advanced Threat Analytics

  Contoso utilise [Advanced Threat Analytics (ATA)](/advanced-threat-analytics/what-is-ata) pour se protéger contre des attaques ciblées avancées. ATA analyse, apprend et identifie automatiquement le comportement normal et inhabituel des entités (utilisateur, périphériques et ressources).

## <a name="information-protection"></a>Protection des informations

- Protection des biens numériques sensibles et hautement réglementés avec des étiquettes Azure Information Protection

  Contoso a déterminé trois niveaux [](../compliance/sensitivity-labels.md) de protection des données et Microsoft 365 étiquettes de sensibilité que les utilisateurs appliquent aux biens numériques. Pour ses secrets commerciaux et ses autres propriétés intellectuelles, Contoso utilise des sous-bels de sensibilité pour les données hautement réglementées. Ce processus chiffre le contenu et limite l’accès à des comptes et groupes d’utilisateurs spécifiques.

- Empêcher les fuites de données intranet avec la protection contre la perte de données

  Contoso a [](../compliance/dlp-learn-about-dlp.md) configuré des stratégies de protection contre la perte de données pour Exchange Online, SharePoint et OneDrive Entreprise pour empêcher les utilisateurs de partager accidentellement ou intentionnellement des données sensibles.

- Prévention des fuites de données de périphériques grâce au service Protection des informations Windows

  Contoso utilise la Protection des informations [Windows (WIP)](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) pour se protéger contre les fuites de données par le biais d’applications et de services internet, ainsi que d’applications et de données d’entreprise sur des appareils et des appareils personnels d’entreprise que les employés apportent au travail.

- Surveillance du cloud avec Microsoft Cloud App Security

  Contoso utilise [Microsoft Cloud App Security](/cloud-app-security/what-is-cloud-app-security) pour mapper son environnement cloud, surveiller son utilisation et détecter les événements de sécurité et les incidents. *Microsoft Cloud App Security est disponible uniquement avec Microsoft 365 E5.*

- Gestion des périphériques avec Microsoft Intune

  Contoso utilise [Microsoft Intune](/intune/introduction-intune) pour inscrire, gérer et configurer l’accès aux appareils mobiles et aux applications qui s’exécutent sur ces derniers. Les stratégies d’accès conditionnel basé sur l’appareil nécessitent également des applications approuvées et des PC et des appareils mobiles compatibles.

## <a name="security-management"></a>Gestion de la sécurité

- Tableau de bord central de sécurité pour les services informatiques avec Azure Defender

  Contoso utilise [Azure Defender](https://azure.microsoft.com/services/security-center/) pour présenter une vue unifiée de la sécurité et de la protection contre les menaces, pour gérer les stratégies de sécurité sur toutes ses charges de travail et pour répondre aux cyberattaques.

- Tableau de bord central de sécurité pour les utilisateurs utilisant le Centre de sécurité Windows Defender

  Contoso a déployé [l’application Sécurité Windows](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) sur ses PC et appareils exécutant des Windows 10 Entreprise afin que les utilisateurs voient leur posture de sécurité d’un seul coup d’œil et prennent des mesures.
