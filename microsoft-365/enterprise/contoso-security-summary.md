---
title: Résumé de la sécurité de Microsoft 365 Entreprise pour Contoso Corporation
author: JoeDavies-MSFT
ms.author: josephd
manager: laurawi
ms.date: 09/13/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Utilisation des fonctionnalités de sécurité sur Microsoft 365 Entreprise par Contoso.
ms.openlocfilehash: 3de3b748659d713d4db8375d4bcc51ce89573d79
ms.sourcegitcommit: d9b462e035416bfa4b3d42467902c75859c55381
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "36054966"
---
# <a name="summary-of-microsoft-365-enterprise-security-for-the-contoso-corporation"></a>Résumé de la sécurité de Microsoft 365 Entreprise pour Contoso Corporation

**Résumé :** Utilisation des fonctionnalités de sécurité sur Microsoft 365 Entreprise par Contoso.

Pour obtenir la déconnexion du déploiement de Microsoft 365 Entreprise par le service de sécurité informatique, un examen minutieux de la sécurité a été effectué. Voici les exigences de sécurité de Contoso pour le cloud :

- Utilisation des meilleures méthodes d’authentification pour l’accès des employés aux ressources du cloud
- Garantie que les PC et les appareils mobiles se connectent et accèdent aux applications en toute sécurité
- Protection des PC et de la messagerie contre les programmes malveillants
- Les autorisations sur les biens numériques basés sur le cloud définissent ceux pouvant accéder au contenu, ainsi que le contenu accessible et les actions possibles à prendre, et sont conçues pour ne permettre qu’un accès privilège restreint
- Les biens numériques sensibles et hautement réglementés sont étiquetés, chiffrés et stockés dans des emplacements sécurisés
- Les biens numériques hautement réglementés sont protégés par des autorisations
- La sécurité informatique permet de contrôler la posture de sécurité à partir de tableaux de bord centraux et de recevoir des notifications d’événements de sécurité afin d’intervenir rapidement et de limiter l’impact

## <a name="contosos-path-to-microsoft-365-security-readiness"></a>Procédure de préparation à la sécurité de Microsoft 365 de Contoso

Contoso a suivi la procédure suivante pour préparer la sécurité pour son déploiement de Microsoft 365 Entreprise :

1. Limitation des comptes Administrateur pour le cloud

   Contoso a effectué une révision complète des comptes de services de domaine Active Directory d’administrateur(AD DS)existants et configuré une série de groupes et de comptes d’administrateurs du cloud.

2. Analyse de la classification des données effectuée selon trois niveaux

   Après une étude approfondie, Contoso a défini les trois niveaux qui lui ont permis d’identifier les fonctionnalités de Microsoft 365 Entreprise destinées à protéger ses données les plus importantes.

3. Définition des stratégies d’accès, de rétention et de protection des informations pour les niveaux de données

   En fonction des niveaux de données, Contoso a déterminé des exigences précises, qui seront utilisées pour qualifier les futures charges de travail informatiques déplacées vers le cloud.

Conformément aux meilleures pratiques de sécurité et aux exigences de déploiement de Microsoft 365 Entreprise, le service informatique et les administrateurs de la sécurité de Contoso ont déployé de nombreuses fonctionnalités de sécurité, comme décrites dans les sections suivantes.

## <a name="identity--access-management"></a>Gestion des identités et des accès 

- Comptes d’administrateur général dédiés avec l’authentification multifacteur (MFA) et Azure AD Privileged Identity Management (PIM)

  Au lieu d’attribuer le rôle d’administrateur général aux comptes d’utilisateurs ordinaires, Contoso a créé trois comptes d’administrateur général dédiés avec des mots de passe très forts et les a protégés avec l’authentification multifacteur (MFA) et la gestion des identités Azure AD Privileged Identity Management (PIM).  PIM est disponible uniquement avec Microsoft 365 Entreprise E5.

  La connexion par le biais d’un compte d’administrateur général se fait uniquement pour des tâches d’administration spécifiques ; les mots de passe ne sont connus que par le personnel désigné et ne peuvent être utilisés que dans le temps configuré dans Azure AD PIM. 

  Les administrateurs de la sécurité de Contoso ont attribué des rôles d’administrateur inférieurs aux comptes selon la fonction et les responsabilités du membre du service informatique en question.

  Pour obtenir plus d’informations, consultez l’article [À propos des rôles d’administrateur Office 365](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles).

- Authentification multifacteur pour tous les comptes d’utilisateur

  L’authentification multifacteur ajoute une couche de protection supplémentaire au processus de connexion en demandant aux utilisateurs de confirmer la réception d’un appel téléphonique, d’un SMS ou d’une notification d’application sur leur smartphone après avoir correctement saisi leur mot de passe. Avec l’authentification multifacteur, les comptes d’utilisateur Azure AD sont protégés contre une connexion non autorisée même si un mot de passe du compte a été compromis.

   - Pour se protéger contre les risques de compromission de l’abonnement Microsoft 365, Contoso requiert l’activation de l’authentification multifacteur sur tous les comptes d’administrateur général.
   - Pour se protéger contre les attaques par hameçonnage, pendant lesquelles un utilisateur malveillant compromet les informations d’identification d’une personne approuvée dans l’organisation et envoie des e-mails malveillants, Contoso a activé la MFA sur tous les comptes d’utilisateur, y compris ceux des gestionnaires et du personnel de la direction. 

- Accès plus sûr aux périphériques et aux applications grâce à des stratégies d’accès conditionnel

  Contoso utilise les [stratégies d’accès conditionnel](microsoft-365-policies-configurations.md) pour l’identité, les périphériques, Exchange Online et SharePoint Online. Les stratégies d’accès conditionnel pour l’identité obligent les utilisateurs à haut risque à modifier leurs mots de passe et empêchent les clients d’utiliser des applications qui ne prennent pas en charge l’authentification moderne. Les stratégies d’accès conditionnel pour les périphériques incluent la définition des applications approuvées et nécessitent des PC et des appareils mobiles compatibles. Les stratégies d’accès conditionnel pour Exchange Online permettent de bloquer les clients ActiveSync et de configurer le chiffrement de messages Office 365. Les stratégies d’accès conditionnel pour SharePoint Online incluent une protection supplémentaire pour les sites sensibles et hautement réglementés.

- Windows Hello Entreprise

  Contoso a réalisé le déploiement et nécessite [Windows Hello Entreprise](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification) afin d’éliminer à terme la nécessité de mots de passe grâce à l’authentification forte à deux facteurs sur PC et appareils mobiles exécutant Windows 10 Entreprise.

- Windows Defender Credential Guard

  Pour bloquer les attaques ciblées et les programmes malveillants en cours d’exécution dans le système d’exploitation grâce à des privilèges administratifs, Contoso a activé [Windows Defender Credential Guard](https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard)par le biais de la stratégie de groupe AD DS.

## <a name="threat-protection"></a>Protection contre les menaces

- Protection contre les programmes malveillants avec Antivirus Windows Defender

  Contoso utilise [Antivirus Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10) pour assurer la protection contre les programmes malveillants et la gestion anti-programme malveillant pour les PC et les périphériques exécutant Windows 10 Entreprise.

- Flux de messagerie et enregistrement d’audit des boîtes aux lettres sécurisés avec Office 365 - Protection avancée contre les menaces 

  Contoso utilise Exchange Online Protection et [Office 365 - Protection avancée contre les menaces (ATP)](https://docs.microsoft.com/office365/securitycompliance/office-365-atp) pour se protéger contre les programmes malveillants inconnus, les virus et les URL malveillantes transmises par les e-mails. 

  Contoso a également activé l’enregistrement d’audit des boîtes aux lettres pour déterminer qui s’est connecté à des boîtes aux lettres utilisateur, a envoyé des messages, et les autres activités effectuées par le propriétaire de la boîte aux lettres, un utilisateur délégué ou un administrateur.

- Surveillance et prévention des attaques avec l’examen et réponse contre les menaces Office 365

  Contoso utilise [examen et réponse contre les menaces Office 365](https://docs.microsoft.com/office365/securitycompliance/office-365-ti) pour protéger ses utilisateurs Office 365 en simplifiant l’identification et le traitement des attaques, et pour empêcher des attaques futures.

- Protection contre les attaques sophistiquées avec Advanced Threat Analytics

  Contoso utilise [Advanced Threat Analytics (ATA)](https://docs.microsoft.com/advanced-threat-analytics/what-is-ata) pour se protéger contre des attaques ciblées avancées. ATA analyse, apprend et identifie automatiquement le comportement normal et inhabituel des entités (utilisateur, périphériques et ressources). 

## <a name="information-protection"></a>Protection des informations

- Protection des biens numériques sensibles et hautement réglementés avec des étiquettes Azure Information Protection

  Contoso a défini trois niveaux de protection des données et déployé les étiquettes [Azure Information Protection](https://docs.microsoft.com/azure/information-protection/what-is-information-protection) que les utilisateurs appliquent aux biens numériques. Pour ses secrets commerciaux et autres propriétés intellectuelles, Contoso utilise les sous-étiquettes Azure Information Protection dans une stratégie limitée pour les données hautement réglementées qui chiffre du contenu et limite l’accès à des groupes de sécurité spécifiques.

- Prévention des fuites de données intranet avec la protection contre la perte de données Office 365

  Contoso a configuré des stratégies de [protection contre la perte de données](https://docs.microsoft.com/office365/securitycompliance/data-loss-prevention-policies) pour Exchange Online, SharePoint Online et OneDrive Entreprise afin d’empêcher les utilisateurs de partager accidentellement ou intentionnellement des données sensibles.

- Prévention des fuites de données de périphériques grâce au service Protection des informations Windows

  Contoso utilise le service [Protection des informations Windows (WIP)](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) pour se protéger contre les fuites de données via des applications et des services Internet, des applications d’entreprise et des données contenues sur les périphériques appartenant à l’entreprise et les périphériques personnels que les employés apportent au travail.

- Surveillance du cloud avec Microsoft Cloud App Security

  Contoso utilise [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security) pour mapper son environnement cloud, surveiller son utilisation et détecter les événements de sécurité et les incidents. Microsoft Cloud App Security est disponible uniquement avec Microsoft 365 Entreprise E5.

- Gestion des périphériques avec Microsoft Intune

  Contoso utilise [Microsoft Intune](https://docs.microsoft.com/intune/introduction-intune) pour inscrire, gérer et configurer l’accès aux appareils mobiles et aux applications qui s’exécutent sur ces derniers. Les stratégies d’accès conditionnel basé sur l’appareil nécessitent également des applications approuvées et des PC et des appareils mobiles compatibles.

## <a name="security-management"></a>Gestion de la sécurité

- Tableau de bord central de sécurité pour les services informatiques avec Azure Security Center

  Contoso utilise le centre [Azure Security Center](https://docs.microsoft.com/intune/introduction-intune) pour afficher une vue unifiée de la sécurité et de la protection contre les menaces, pour gérer des stratégies de sécurité sur l’ensemble de ses charges de travail et pour répondre aux cyberattaques.

- Tableau de bord central de sécurité pour les utilisateurs utilisant le Centre de sécurité Windows Defender

  Contoso a déployé l’[application Centre de sécurité Windows Defender ](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) vers ses PC et périphériques exécutant Windows 10 Entreprise afin que les utilisateurs puissent voir leur posture de sécurité en un clin d’œil et prendre des mesures.


## <a name="next-step"></a>Étape suivante

[Découvrez](contoso-sharepoint-online-site-for-highly-confidential-assets.md) comment Contoso a créé un site SharePoint Online pour les données hautement réglementées afin de favoriser la collaboration entre ses équipes de recherche.

