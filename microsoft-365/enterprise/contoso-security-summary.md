---
title: Résumé de Microsoft 365 pour la sécurité d’entreprise pour Contoso Corporation
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
ms.date: 10/02/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Comment Contoso utilise les fonctionnalités de sécurité de Microsoft 365 pour les entreprises.
ms.openlocfilehash: d84b1423497a6a4358142902c4e159cc54b3500b
ms.sourcegitcommit: 66b8fc1d8ba4f17487cd2004ac19cf2fff472f3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "48754231"
---
# <a name="summary-of-microsoft-365-for-enterprise-security-for-the-contoso-corporation"></a>Résumé de Microsoft 365 pour la sécurité d’entreprise pour Contoso Corporation

Pour obtenir l’approbation de déploiement de Microsoft 365 pour Enterprise, le service de sécurité informatique de Contoso a effectué un examen de sécurité approfondi. Ils ont identifié les exigences de sécurité suivantes pour le Cloud :

- Utilisez les méthodes d’authentification les plus puissantes pour l’accès des employés aux ressources Cloud.
- Assurez-vous que les PC et les appareils mobiles se connectent et accèdent aux applications de manière sécurisée.
- Protégez les PC et les messages électroniques contre les programmes malveillants.
- Les autorisations sur les biens numériques basés sur le Cloud définissent qui peut accéder à quels éléments et ce qu’ils peuvent faire, et qui sont conçus pour un accès au moins privilégié
- Les biens numériques sensibles et hautement réglementés sont étiquetés, chiffrés et stockés dans des emplacements sécurisés.
- Les biens numériques hautement réglementés sont protégés par un chiffrement et des autorisations supplémentaires.
- Le personnel de sécurité informatique peut surveiller la position actuelle de la sécurité à partir des tableaux de bord centraux et recevoir des notifications d’événements de sécurité pour une réponse et une atténuation rapides.

## <a name="the-contoso-path-to-microsoft-365-security-readiness"></a>Le chemin d’accès contoso à la préparation de sécurité Microsoft 365

Contoso a suivi ces étapes pour préparer sa sécurité pour le déploiement de Microsoft 365 pour les entreprises :

1. Limiter les comptes d’administrateur pour le Cloud

   Contoso a fait un examen approfondi de ses comptes d’administrateur des services de domaine Active Directory (AD DS) existants et a configuré la série de comptes et de groupes d’administrateurs de Cloud dédiés.

2. Classer les données en trois niveaux de sécurité

   Contoso a fait un examen attentif et a déterminé les trois niveaux, qui ont été utilisés pour identifier les fonctionnalités Microsoft 365 pour les entreprises afin de protéger les données les plus précieuses.

3. Déterminer les stratégies d’accès, de rétention et de protection des informations pour les niveaux de données

   En fonction des niveaux de données, Contoso a déterminé les besoins détaillés pour qualifier les charges de travail informatiques futures qui sont déplacées vers le Cloud.

Pour suivre les meilleures pratiques en matière de sécurité et les exigences de déploiement d’entreprise de Microsoft 365, les administrateurs de la sécurité de contoso et son service informatique ont déployé de nombreuses fonctionnalités et fonctionnalités de sécurité, comme décrit dans les sections suivantes.

## <a name="identity-and-access-management"></a>Gestion des identités et des accès 

- Comptes d’administrateur général dédiés avec l’authentification multifacteur (MFA) et Azure AD Privileged Identity Management (PIM)

  Au lieu d’attribuer le rôle d’administrateur global aux comptes d’utilisateur quotidiens, Contoso a créé trois comptes d’administrateur général dédiés avec des mots de passe forts. Les comptes sont protégés par Azure Multi-Factor Authentication (MFA) et Azure Active Directory (Azure AD) Privileged Identity Management (PIM). *PIM est uniquement disponible avec Microsoft 365 E5.*

  La connexion avec un compte d’administrateur général est uniquement réalisée pour des tâches d’administration spécifiques. Les mots de passe sont uniquement connus du personnel désigné et ne peuvent être utilisés que dans une période configurée dans Azure AD PIM.

  Les administrateurs de la sécurité de contoso ont attribué des rôles d’administrateur moins important aux comptes appropriés à la fonction de travail de ce dernier.

  Si vous souhaitez en savoir plus, consultez l’article [À propos des rôles d’administrateur Microsoft 365](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles).

- Authentification multifacteur pour tous les comptes d’utilisateur

  MFA ajoute une couche de protection supplémentaire pour le processus de connexion. Les utilisateurs doivent accuser réception d’un appel téléphonique, d’un message texte ou d’une notification d’application sur leur téléphone intelligent après avoir entré correctement leur mot de passe. Avec MFA, les comptes d’utilisateur Azure AD sont protégés contre la connexion non autorisée, même si un mot de passe de compte est compromis.

   - Pour vous protéger contre la compromission de l’abonnement Microsoft 365, contoso requiert l’authentification multifacteur sur tous les comptes d’administrateur général.
   - Pour se protéger contre les attaques par hameçonnage, pendant lesquelles un utilisateur malveillant compromet les informations d’identification d’une personne approuvée dans l’organisation et envoie des e-mails malveillants, Contoso a activé la MFA sur tous les comptes d’utilisateur, y compris ceux des gestionnaires et de la direction.

- Accès plus sûr aux périphériques et aux applications grâce à des stratégies d’accès conditionnel

  Contoso utilise les [stratégies d’accès conditionnel](../security/office-365-security/microsoft-365-policies-configurations.md) pour l’identité, les périphériques, Exchange Online et SharePoint. Les stratégies d’accès conditionnel pour l’identité obligent les utilisateurs à haut risque à modifier leurs mots de passe et empêchent les clients d’utiliser des applications qui ne prennent pas en charge l’authentification moderne. Les stratégies pour les périphériques incluent la définition des applications approuvées et nécessitent des PC et des appareils mobiles compatibles. Les stratégies d’accès conditionnel pour Exchange Online permettent de bloquer les clients ActiveSync et de configurer le chiffrement de messages Office 365. Les stratégies d’accès conditionnel pour SharePoint incluent une protection supplémentaire pour les sites sensibles et hautement réglementés.

- Windows Hello Entreprise

  Contoso a déployé [Windows Hello entreprise](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification) pour finalement éliminer la nécessité d’utiliser des mots de passe via une authentification forte à deux facteurs sur les PC et les appareils mobiles exécutant Windows 10 entreprise.

- Windows Defender Credential Guard

  Pour bloquer les attaques ciblées et les programmes malveillants s’exécutant dans le système d’exploitation avec des privilèges d’administrateur, Contoso a activé la [protection des informations d’identification Windows Defender](https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard) via la stratégie de groupe AD DS.

## <a name="threat-protection"></a>Protection contre les menaces

- Protection contre les programmes malveillants avec Antivirus Windows Defender

  Contoso utilise [Antivirus Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10) pour assurer la protection contre les programmes malveillants et la gestion anti-programme malveillant pour les PC et les périphériques exécutant Windows 10 Entreprise.

- Flux de messagerie et enregistrement d’audit des boîtes aux lettres sécurisés avec Office 365 - Protection avancée contre les menaces 

  Contoso utilise Exchange Online Protection et [Office 365 - Protection avancée contre les menaces (ATP)](https://docs.microsoft.com/office365/securitycompliance/office-365-atp) pour se protéger contre les programmes malveillants inconnus, les virus et les URL malveillantes transmises par les e-mails.

  Contoso a également activé l’enregistrement d’audit de boîte aux lettres pour identifier les utilisateurs qui se connectent aux boîtes aux lettres des utilisateurs, envoie des messages et effectue d’autres activités par le propriétaire de la boîte aux lettres, un utilisateur délégué ou un administrateur.

- Surveillance et prévention des attaques avec l’examen et réponse contre les menaces Office 365

  Contoso utilise une enquête sur les [menaces Office 365 et une réponse](https://docs.microsoft.com/office365/securitycompliance/office-365-ti) pour protéger les utilisateurs en facilitant l’identification et la lutte contre les attaques, ainsi que contre les attaques futures.

- Protection contre les attaques sophistiquées avec Advanced Threat Analytics

  Contoso utilise [Advanced Threat Analytics (ATA)](https://docs.microsoft.com/advanced-threat-analytics/what-is-ata) pour se protéger contre des attaques ciblées avancées. ATA analyse, apprend et identifie automatiquement le comportement normal et inhabituel des entités (utilisateur, périphériques et ressources).

## <a name="information-protection"></a>Protection des informations

- Protection des biens numériques sensibles et hautement réglementés avec des étiquettes Azure Information Protection

  Contoso a déterminé trois niveaux de protection des données et a déployé des [étiquettes de confidentialité Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) que les utilisateurs appliquent aux biens numériques. Pour ses secrets commerciaux et autres droits de propriété intellectuelle, Contoso utilise des sous-étiquettes de sensibilité pour les données hautement réglementées. Ce processus chiffre le contenu et limite l’accès à des comptes d’utilisateurs et à des groupes spécifiques.

- Empêcher les fuites de données intranet avec la protection contre la perte de données

  Contoso a configuré des stratégies de [protection contre la perte de données](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies) pour Exchange Online, SharePoint et OneDrive entreprise afin d’empêcher les utilisateurs de partager accidentellement ou intentionnellement des données sensibles.

- Prévention des fuites de données de périphériques grâce au service Protection des informations Windows

  Contoso utilise la [protection des informations Windows (WIP)](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) pour protéger contre les fuites de données via des applications et des services Internet, ainsi que des applications et des données d’entreprise sur des appareils appartenant à une entreprise et des appareils personnels que les employés mettent en œuvre.

- Surveillance du cloud avec Microsoft Cloud App Security

  Contoso utilise [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security) pour mapper son environnement cloud, surveiller son utilisation et détecter les événements de sécurité et les incidents. *Microsoft Cloud App Security est disponible uniquement avec Microsoft 365 E5.*

- Gestion des périphériques avec Microsoft Intune

  Contoso utilise [Microsoft Intune](https://docs.microsoft.com/intune/introduction-intune) pour inscrire, gérer et configurer l’accès aux appareils mobiles et aux applications qui s’exécutent sur ces derniers. Les stratégies d’accès conditionnel basé sur l’appareil nécessitent également des applications approuvées et des PC et des appareils mobiles compatibles.

## <a name="security-management"></a>Gestion de la sécurité

- Tableau de bord central de sécurité pour les services informatiques avec Azure Security Center

  Contoso utilise le [Centre de sécurité Azure](https://azure.microsoft.com/services/security-center/) pour présenter une vue unifiée de la sécurité et de la protection contre les menaces, pour gérer les stratégies de sécurité sur l’ensemble de ses charges de travail et pour répondre aux cyberattaques.

- Tableau de bord central de sécurité pour les utilisateurs utilisant le Centre de sécurité Windows Defender

  Contoso a déployé l' [application de sécurité Windows](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) sur ses PC et appareils exécutant Windows 10 entreprise afin que les utilisateurs puissent visualiser en un clin d’œil le niveau de sécurité et prendre des mesures.
