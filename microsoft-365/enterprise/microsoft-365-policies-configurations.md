---
title: 'Configurations d’accès aux identités et aux appareils : Microsoft 365 Enterprise'
description: Décrit les recommandations et les concepts fondamentaux de Microsoft pour le déploiement de stratégies et de configurations de messagerie électronique, de documents et d’applications sécurisées.
author: brendacarter
manager: laurawi
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 09/11/2018
f1.keywords:
- NOCSH
ms.author: bcarter
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
ms.openlocfilehash: f336c9ef2957374223a8f0d7b64f892c87e1169d
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43631548"
---
# <a name="identity-and-device-access-configurations"></a>Configurations des identités et de l’accès aux appareils

Cette série d’articles explique comment configurer un accès sécurisé aux services Cloud via les produits Enterprise Mobility + Security (EMS) en implémentant un environnement et une configuration recommandés, y compris un ensemble de stratégies d’accès conditionnel et des fonctionnalités associées. EMS est un composant essentiel de Microsoft 365. Vous pouvez utiliser ces conseils pour protéger l’accès à tous les services intégrés à Azure Active Directory, notamment les services Microsoft 365, d’autres services SaaS et les applications locales publiées avec le proxy d’application Azure AD. 

Ces recommandations sont alignées sur le score de sécurité Microsoft et le [score d’identité dans Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/identity-secure-score), et augmentent ces scores pour votre organisation. Ces recommandations vous aideront également à mettre [en œuvre ces cinq étapes pour sécuriser votre infrastructure d’identité](https://docs.microsoft.com/azure/security/azure-ad-secure-steps). 

Microsoft sait que certaines organisations ont des exigences ou des complexités d’environnement uniques. Si vous êtes l’une de ces organisations, utilisez ces recommandations comme point de départ. Toutefois, la plupart des organisations peuvent mettre en œuvre ces recommandations comme indiqué. 

## <a name="intended-audience"></a>Public cible

Ces recommandations sont destinées aux architectes d’entreprise et aux professionnels de l’informatique qui sont familiarisés avec [Office 365](https://technet.microsoft.com/library/dn127064(v=office.14).aspx) et [Microsoft Enterprise Mobility + Security](https://microsoft.com/ems), qui inclut, entre autres, Azure Active Directory (identité), Microsoft Intune (gestion des appareils) et Azure information protection (protection des données).

### <a name="customer-environment"></a>Environnement du client

Les stratégies recommandées s’appliquent aux organisations d’entreprise opérant entièrement dans le Cloud Microsoft et pour les clients ayant une infrastructure hybride (déployés sur site et dans le Cloud Microsoft).

La plupart des recommandations fournies s’appuient sur les services disponibles uniquement avec les licences Enterprise Mobility + Security (EMS) E5. Les recommandations présentées supposent que les fonctionnalités de licence EMS E5 sont complètes.

Pour les organisations qui ne disposent pas de licences Enterprise Mobility + Security E5, Microsoft vous recommande au moins d’implémenter les fonctionnalités Azure AD Baseline protection incluses dans tous les plans. Vous trouverez plus d’informations dans l’article, [qu’est-ce que la protection de base](/azure/active-directory/active-directory-conditional-access-baseline-protection), dans la bibliothèque Azure ad.

### <a name="caveats"></a>Observer lors

Votre organisation peut être soumise à des exigences réglementaires ou autres en matière de conformité, notamment des recommandations spécifiques pouvant nécessiter l’application de stratégies qui divergent de ces configurations recommandées. Ces configurations recommandent des contrôles de l’utilisation qui n’étaient pas disponibles par le passé. Nous recommandons ces contrôles, car nous pensons qu’ils représentent le bon équilibre entre sécurité et productivité.  

Nous avons réalisé notre meilleure solution pour tenir compte de nombreuses exigences de protection de l’organisation, mais nous ne sommes pas en mesure de tenir compte de toutes les exigences possibles ou de tous les aspects spécifiques de votre organisation.

## <a name="three-tiers-of-protection"></a>Trois niveaux de protection

La plupart des organisations ont des besoins spécifiques en matière de sécurité et de protection des données. Ces besoins varient selon leur secteur d’activité et selon les postes de travail en leur sein. Par exemple, votre service juridique et les administrateurs peuvent exiger des contrôles de sécurité et de protection des informations supplémentaires concernant la correspondance de leur courrier électronique qui ne sont pas requis pour les autres utilisateurs de divisions. 

Chaque secteur d’activité possède aussi sa propre réglementation spécialisée. Au lieu de fournir une liste de toutes les options de sécurité possibles ou une recommandation par segment d’industrie ou fonction, des recommandations ont été fournies pour trois niveaux différents de sécurité et de protection pouvant être appliqués en fonction de la granularité de vos besoins.

- **Baseline protection**: nous vous recommandons de définir une norme minimale pour la protection des données, ainsi que les identités et les appareils qui accèdent à vos données. Vous pouvez suivre ces recommandations de base pour fournir une protection par défaut efficace qui répond aux besoins de nombreuses organisations.
- **Protection sensible**: certains clients disposent d’un sous-ensemble de données qui doivent être protégées à des niveaux supérieurs, ou nécessitent que toutes les données soient protégées à un niveau supérieur. Vous pouvez renforcer la protection de l’ensemble ou des ensembles de données spécifiques dans votre environnement Microsoft 365. Nous vous recommandons de protéger les identités et les appareils qui accèdent à des données sensibles avec des niveaux de sécurité comparables.  
- **Hautement réglementé**: certaines organisations peuvent avoir une petite quantité de données qui est hautement classifiée, des secrets commerciaux consititutes ou des données réglementées. Microsoft fournit des fonctionnalités pour aider les organisations à respecter de telles exigences, notamment de protection renforcée des appareils et des identités.

![Cône de sécurité : tous les clients > certains clients > des clients spécifiques. Application étendue à une application spécifique](../media/M365-idquality-threetiers.png)

Ce guide vous montre comment implémenter la protection des identités et des périphériques pour chacune de ces niveaux de protection. Utilisez ces conseils comme point de départ pour votre organisation et ajustez les stratégies pour répondre aux besoins spécifiques de votre organisation.

Il est important d'utiliser des niveaux de protection cohérents pour l'ensemble de vos données, de vos identités et de vos appareils. Par exemple, si vous implémentez ces instructions, veillez à protéger vos données à des niveaux comparables. Ces modèles d’architecture vous montrent quelles fonctionnalités sont comparables.

**La protection des appareils et de l’identité pour Office 365**<br/>
![Miniature de l’affiche « protection des identités et des appareils pour Office 365 »](../media/O365_Identity_device_protection_thumb.png)<br/>
[PDF](https://go.microsoft.com/fwlink/p/?linkid=841656) | [Visio](https://go.microsoft.com/fwlink/p/?linkid=841657) | [Plus de langues](https://www.microsoft.com/download/details.aspx?id=55032)

**Solutions de protection des fichiers dans Office 365**<br/>
![Miniature de l’affiche « solutions de protection de fichier dans Office 365 »](../media/24be68b5-d852-4fdb-94ad-94491a19edd8.png)<br/>
[PDF](https://download.microsoft.com/download/7/8/9/789645A5-BD10-4541-BC33-F8D1EFF5E911/MSFT_cloud_architecture_O365%20file%20protection.pdf) | [Visio](https://download.microsoft.com/download/7/8/9/789645A5-BD10-4541-BC33-F8D1EFF5E911/MSFT_cloud_architecture_O365%20file%20protection.vsdx)

## <a name="security-and-productivity-trade-offs"></a>Compromis entre sécurité et productivité

L’implémentation d’une stratégie de sécurité nécessite des compromis entre la sécurité et la productivité. Il est utile d’évaluer la façon dont chaque décision influe sur l’équilibre de la sécurité, des fonctionnalités et de la convivialité.

![La sécurité, les fonctionnalités et la facilité d’utilisation de l’équilibrage de la sécurité.](../media/policies-configurations/security-triad.png)

Les recommandations fournies sont basées sur les principes suivants :

- Connaître votre public et s’adapte à ses exigences en matière de sécurité et de fonctionnement.
- Appliquer une stratégie de sécurité juste à temps et s’assurer qu’elle est significative.

## <a name="services-and-concepts-for-identity-and-device-access-protection"></a>Services et concepts relatifs à la protection de l’accès aux identités et aux appareils

Microsoft 365 Enterprise est conçu pour les grandes organisations et intègre Office 365 Enterprise, Windows 10 entreprise et Enterprise Mobility + Security (EMS), afin de permettre à chacun d’être créatif et de collaborer en toute sécurité.

Cette section fournit une vue d’ensemble des services et des fonctionnalités Microsoft 365 qui sont importants pour l’accès aux identités et aux appareils.

### <a name="microsoft-azure-active-directory"></a>Microsoft Azure Active Directory

Azure AD fournit une suite complète de fonctionnalités de gestion des identités. Pour sécuriser l’accès, nous vous recommandons d’utiliser les fonctionnalités suivantes :

- **[Réinitialisation du mot de passe en libre-service](/azure/active-directory/authentication/concept-sspr-howitworks)**: permet à vos utilisateurs de réinitialiser leur mot de passe en toute sécurité et sans intervention de l’assistance technique, en fournissant la vérification de plusieurs méthodes d’authentification que l’administrateur peut contrôler.

- **[Authentification multifacteur (MFA) : l’authentification multifacteur](/azure/active-directory/authentication/concept-mfa-howitworks)** exige que les utilisateurs fournissent deux formes de vérification, telles qu’un mot de passe utilisateur, ainsi qu’une notification de l’application Microsoft Authenticator ou d’un appel téléphonique. MFA réduit considérablement le risque qu’une identité volée puisse être utilisée pour accéder à votre environnement.

- **[Accès conditionnel](/azure/active-directory/conditional-access/overview)**: Azure ad évalue les conditions de connexion de l’utilisateur et utilise des stratégies d’accès conditionnel que vous créez pour autoriser l’accès. Par exemple, dans ce guide, nous vous montrons comment créer une stratégie d’accès conditionnel pour exiger la conformité de l’appareil pour l’accès aux données sensibles. Cela réduit considérablement le risque qu’un pirate disposant d’une identité volée puisse accéder à vos données sensibles. Il protège également les données sensibles sur les appareils, car les appareils répondent à des exigences spécifiques en matière d’intégrité et de sécurité.

- Les **[groupes Azure ad](/azure/active-directory/fundamentals/active-directory-manage-groups)**: les règles d’accès conditionnel, la gestion des périphériques avec Intune et même les autorisations sur les fichiers et les sites de votre organisation, dépendent de l’attribution à des groupes d’utilisateurs et/ou Azure ad. Nous vous recommandons de créer des groupes Azure AD qui correspondent aux niveaux de protection que vous implémentez. Par exemple, votre personnel exécutif est probablement plus à même de cibler des pirates. Par conséquent, il est logique d’affecter ces employés à un groupe Azure AD et d’affecter ce groupe aux stratégies d’accès conditionnelles et à d’autres stratégies qui appliquent un niveau de protection plus élevé pour l’accès.

- **[Inscription](/azure/active-directory/devices/overview)** de l’appareil : vous inscrivez un appareil dans Azure AD pour fournir une identité à l’appareil. Cette identité est utilisée pour authentifier l’appareil lorsqu’un utilisateur se connecte et pour appliquer des règles d’accès conditionnel qui nécessitent des PC joints à un domaine ou des PC conformes. Pour ce guide, nous utilisons l’inscription de l’appareil pour enregistrer automatiquement des ordinateurs Windows associés à un domaine. L’inscription de l’appareil est une condition préalable à la gestion des appareils avec Intune. 

- **[Azure ad Identity Protection](/azure/active-directory/identity-protection/overview)**: Azure ad Identity Protection vous permet de détecter les vulnérabilités potentielles affectant les identités de votre organisation et de configurer une stratégie de correction automatisée sur un risque de connexion faible, moyen et élevé et de risque utilisateur. Ces instructions s’appuient sur cette évaluation des risques pour appliquer des stratégies d’accès conditionnel pour l’authentification multifacteur. Ce guide inclut également une stratégie d’accès conditionnel qui exige que les utilisateurs modifient leur mot de passe si l’activité à haut risque est détectée pour leur compte.

### <a name="microsoft-intune"></a>Microsoft Intune

[Intune](https://docs.microsoft.com/intune/introduction-intune) est le service de gestion des appareils mobiles de Microsoft basé sur le Cloud. Ce guide recommande la gestion des périphériques Windows avec Intune et recommande des configurations de stratégie de conformité des appareils. Intune détermine si les appareils sont conformes et envoie ces données à Azure AD pour les utiliser lors de l’application de stratégies d’accès conditionnel.

#### <a name="intune-app-protection"></a>Protection des applications Intune

Les stratégies [Intune App protection](https://docs.microsoft.com/intune/app-protection-policy) peuvent être utilisées pour protéger les données de votre organisation dans les applications mobiles, avec ou sans l’enregistrement d’appareils dans la gestion. Intune contribue à protéger les informations, en veillant à ce que vos employés puissent toujours être productifs et empêcher la perte de données. En implémentant des stratégies au niveau de l’application, vous pouvez restreindre l’accès aux ressources de l’entreprise et conserver les données dans le contrôle de votre service informatique.

Ce guide vous montre comment créer des stratégies recommandées pour appliquer l’utilisation des applications approuvées et déterminer comment ces applications peuvent être utilisées avec vos données métiers.

### <a name="microsoft-365"></a>Microsoft 365

Ce guide vous montre comment implémenter un ensemble de stratégies pour protéger l’accès à Office 365, notamment Exchange Online, SharePoint Online et OneDrive entreprise. En plus de mettre en œuvre ces stratégies, nous vous recommandons d’augmenter également le niveau de protection de votre client à l’aide de ces ressources :

- [Configurez votre client pour renforcer la sécurité](https://support.office.com/article/Configure-your-Office-365-tenant-for-increased-security-8d274fe3-db51-4107-ba64-865e7155b355): ces recommandations s’appliquent à la sécurité de base pour votre client.
- Feuille [de route de sécurité Microsoft 365 : les principales priorités des 30 premiers jours, 90 jours et au-delà](https://support.office.com/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352): ces recommandations incluent la journalisation, la gouvernance des données, l’accès administrateur et la protection contre les menaces.


### <a name="windows-10-and-microsoft-365-apps-for-enterprise"></a>Applications Windows 10 et Microsoft 365 pour les entreprises

Les applications Windows 10 et Microsoft 365 pour Enterprise sont l’environnement client recommandé pour les PC. Nous vous recommandons Windows 10, car Azure est conçu pour offrir l’expérience la plus facile possible pour les versions locale et Azure AD. Windows 10 inclut également des fonctionnalités de sécurité avancées qui peuvent être gérées via Intune. Microsoft 365 Apps for Enterprise inclut les versions les plus récentes des applications Office. Ces éléments utilisent l’authentification moderne, qui est plus sécurisée et nécessite un accès conditionnel. Ces applications incluent également des outils de sécurité et de conformité améliorés.

## <a name="applying-these-capabilities-across-the-three-tiers-of-protection"></a>Application de ces fonctionnalités aux trois niveaux de protection

Le tableau suivant résume nos recommandations pour l’utilisation de ces fonctionnalités dans les trois niveaux de protection.

|Mécanisme de protection|Baseline|Sensible|Hautement réglementé|
|:-------------------|:-------|:--------|:---------------|
|**Appliquer une authentification multifacteur**|En cas de risque de connexion moyen ou supérieur|En cas de risque de connexion faible ou supérieur|Pour toutes les nouvelles sessions|
|**Appliquer la modification du mot de passe**|Pour les utilisateurs à haut risque|Pour les utilisateurs à haut risque|Pour les utilisateurs à haut risque|
|**Appliquer la protection des applications Intune**|Oui|Oui|Oui|
|**Appliquer l’enregistrement Intune (COD)**|Exiger un PC conforme ou joint à un domaine, mais autoriser les téléphones/tablettes BYOD|Exiger un appareil compatible ou joint à un domaine|Exiger un appareil compatible ou joint à un domaine|

## <a name="device-ownership"></a>Propriété des appareils

Le tableau ci-dessus reflète la tendance pour de nombreuses organisations à prendre en charge un mélange d’appareils appartenant à une entreprise, ainsi que des appareils personnels ou BYODs, pour permettre une productivité mobile au sein du personnel. Les stratégies de protection des applications Intune garantissent que les courriers électroniques sont protégés contre les exfiltrating de l’application mobile Outlook et d’autres applications mobiles Office, qu’il s’agisse d’appareils appartenant à une entreprise ou d’BYODs.  

Nous recommandons que les appareils appartenant à une entreprise soient gérés par Intune ou par un domaine joint pour appliquer des protections et des contrôles supplémentaires. En fonction de la sensibilité des données, votre organisation peut choisir de ne pas autoriser BYODs pour des populations d’utilisateurs spécifiques ou des applications spécifiques.

## <a name="next-steps"></a>Étapes suivantes

[Tâches préalables à l’implémentation de stratégies d’accès aux identités et aux appareils](identity-access-prerequisites.md)
