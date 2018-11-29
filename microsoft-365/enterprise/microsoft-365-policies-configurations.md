---
title: Identité et appareil configurations access - Microsoft 365 pour entreprises
description: Décrit les concepts fondamentaux pour le déploiement de messagerie sécurisée, documents, les stratégies d’applications et des configurations et les recommandations de Microsoft.
author: brendacarter
manager: laurawi
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 09/11/2018
ms.author: bcarter
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.openlocfilehash: 74378da4206c3735cd949358c6cb34b314c82b97
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26866860"
---
# <a name="identity-and-device-access-configurations"></a>Configurations des identités et de l’accès aux appareils

Cette série d’articles explique comment configurer un accès sécurisé aux services de cloud computing et la mobilité d’entreprise + produits de sécurité en implémentant un environnement recommandé et la configuration, y compris un ensemble de stratégies d’accès conditionnel prescrit et fonctionnalités connexes. Vous pouvez utiliser ce guide pour protéger l’accès à tous les services qui sont intégrés à Azure Active Directory, notamment les services Office 365, autres SaaS services et des applications sur site publié par le Proxy d’Application Azure AD. 

Ces recommandations sont alignées avec Microsoft Secure Score ainsi que [l’identité score dans Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/identity-secure-score) et augmenteront ces scores pour votre organisation. Ces recommandations vous aideront également à implémenter ces [cinq étapes pour sécuriser votre infrastructure d’identité](https://docs.microsoft.com/en-us/azure/security/azure-ad-secure-steps). 

Microsoft est conscient que certaines organisations ont des besoins de l’environnement unique ou de complexité. Si vous êtes une de ces organisations, utilisez ces recommandations comme point de départ. Toutefois, la plupart des organisations peuvent implémenter ces recommandations comme prévu. 

## <a name="intended-audience"></a>Public cible

Ces recommandations sont destinées aux architectes de l’entreprise et les professionnels de l’informatique qui sont familiarisés avec [Office 365](https://technet.microsoft.com/library/dn127064(v=office.14).aspx) et [mobilité d’entreprise Microsoft + sécurité](http://microsoft.com/ems) qui inclut, entre autres, Azure Active Directory (identité), Microsoft Intune (gestion des périphériques) et la Protection des informations Azure (protection des données).

### <a name="customer-environment"></a>Environnement du client

Les stratégies recommandées sont applicables aux entreprises d’exploitation à la fois entièrement dans le nuage Microsoft et pour l’environnement hybride clients avec une infrastructure déploiement sur site et le nuage Microsoft.

Bon nombre des recommandations fournies s’appuient sur les services disponibles uniquement avec la mobilité d’entreprise + licences E5 de sécurité (EMS). Recommandations présentées supposent que les fonctions de licence EMS E5 complètes.

Pour les organisations qui n’ont pas de mobilité d’entreprise + licences E5 de sécurité, Microsoft recommande qu'au moins de mettre en œuvre de fonctionnalités de protection planifié Azure AD qui sont incluses dans tous les plans. Plus d’informations, voir l’article [What ' s protection planifié](/azure/active-directory/active-directory-conditional-access-baseline-protection) dans la bibliothèque Azure AD.

### <a name="caveats"></a>Avertissements

Votre organisation peut être soumis à des exigences de conformité réglementaire ou autres, y compris des recommandations spécifiques qui peuvent vous obliger à appliquer des stratégies de différer de ces configurations recommandées. Ces configurations est recommandé de contrôles de l’utilisation ne faisaient pas disponibles. Nous vous recommandons de ces contrôles, car qu'ils représentent un équilibre entre la sécurité et la productivité.  

Nous avons pour prendre en compte pour un large éventail de protection d’organisation, nous ne sommes pas en mesure de compte pour toutes les conditions possibles ou pour tous les aspects uniques de votre organisation.

## <a name="three-tiers-of-protection"></a>Trois couches de protection

La plupart des organisations ont des besoins spécifiques en matière de sécurité et de protection des données. Ces besoins varient selon leur secteur d’activité et selon les postes de travail en leur sein. Par exemple, votre service juridique et ses administrateurs Office 365 peuvent avoir des besoins plus importants en matière de contrôle de la sécurité et de la protection des informations contenues dans leur correspondance par e-mail que d’autres services.

Chaque secteur a également leur propre ensemble de la réglementation spécialisées. Au lieu de fournissant une liste de toutes les options de sécurité ou d’une recommandation par la fonction de segment ou le travail du secteur, les recommandations ont été fournies pour trois différents niveaux de sécurité et protection qui peut être appliquée en fonction de la granularité de vos besoins .

- **Protection de base** , nous vous recommandons d’établir une norme minimale de protection des données, ainsi que les identités et les périphériques qui accèdent à vos données. Vous pouvez suivre ces recommandations de planification pour assurer la protection par défaut fort qui répond aux besoins de bon nombre d’organisations.
- **Protection sensible** , certains clients ont un sous-ensemble de données qui doivent être protégées à des niveaux supérieurs ou qui nécessitent toutes les données d’être protégé à un niveau supérieur. Vous pouvez appliquer une meilleure protection à l’ensemble ou définit des données spécifiques dans votre environnement Office 365. Nous vous recommandons de protéger les identités et les périphériques qui accèdent aux données sensibles avec des niveaux de sécurité comparables.  
- **Hautement régulé** — certaines organisations peuvent avoir une petite quantité de données qui sont hautement classées, secret commercial ou régulé. Microsoft fournit des fonctionnalités pour permettre aux organisations de répondre à ces exigences, y compris la protection ajoutée des identités et des périphériques.

![Cône de sécurité - tous les clients > certains clients > clients spécifiques. Étendue d’applications à une application spécifique](../images/M365-idquality-threetiers.png)

Ce guide vous montre comment implémenter la protection des identités et des périphériques pour chacun de ces niveaux de protection. Utilisez ce guide comme point de départ pour votre organisation et ajuster les stratégies pour les besoins de votre organisation.

Il est important d’utiliser des niveaux de protection cohérentes entre vos données, les identités et les périphériques. Par exemple, si vous implémentez ce guide, veillez à protéger vos données à des niveaux comparables. Ces modèles d’architecture vous montrent les fonctionnalités sont comparables.

**Protection d’identité et de périphérique pour Office 365**<br/>
![Miniature pour affiche « Identity et appareil protection pour Office 365 »](../images/O365_Identity_device_protection_thumb.png)<br/>
[PDF](https://go.microsoft.com/fwlink/p/?linkid=841656) | [Visio](https://go.microsoft.com/fwlink/p/?linkid=841657) | [Plus de langues](https://www.microsoft.com/download/details.aspx?id=55032)

**Solutions de protection des fichiers dans Office 365**<br/>
![Miniature d’affiche « Solutions de protection de fichiers dans Office 365 »](../images/24be68b5-d852-4fdb-94ad-94491a19edd8.png)<br/>
[PDF](http://download.microsoft.com/download/7/8/9/789645A5-BD10-4541-BC33-F8D1EFF5E911/MSFT_cloud_architecture_O365%20file%20protection.pdf) | [Visio](http://download.microsoft.com/download/7/8/9/789645A5-BD10-4541-BC33-F8D1EFF5E911/MSFT_cloud_architecture_O365%20file%20protection.vsdx)

## <a name="security-and-productivity-trade-offs"></a>Compromis entre sécurité et productivité

L’implémentation de toute stratégie de sécurité nécessite des compromis entre la sécurité et la productivité. Il est utile évaluer l’impact de chaque décision l’équilibre de la sécurité, la fonctionnalité et facilité d’utilisation.

![Triangle sécurité l’équilibrage de la sécurité, la fonctionnalité et facilité d’utilisation.](media/policies-configurations/security-triad.png)

Les recommandations fournies sont basées sur les principes suivants :

- Connaître votre public souplesse à leurs exigences fonctionnelles et de sécurité.
- Appliquer la stratégie de sécurité dans le temps et vérifiez qu’il est explicite.

## <a name="services-and-concepts-for-identity-and-device-access-protection"></a>Services et les concepts d’identité et de périphérique pour protection d’accès

Microsoft 365 Enterprise est conçu pour les grandes organisations et intègre des fonctionnalités Office 365 pour entreprises, Windows 10 entreprise et mobilité d’entreprise + sécurité (EMS) pour permettre à tout le monde creative et fonctionnent ensemble, en toute sécurité.

Cette section fournit une vue d’ensemble des services Microsoft 365 et les fonctionnalités qui sont importantes pour l’accès des identités et des périphériques.

### <a name="microsoft-azure-active-directory"></a>Microsoft Azure Active Directory

Azure AD fournit une suite complète de l’identité des fonctionnalités de gestion. Nos recommandations pour sécuriser l’accès utilisent les fonctionnalités suivantes :

- **[Mot de passe libre-service réinitialiser (SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks.md)** : autoriser les utilisateurs à réinitialiser leur mot de passe sans l’intervention de l’assistance en toute sécurité en fournissant la vérification de l’administrateur peut contrôler plusieurs méthodes d’authentification.
- **[L’authentification multifacteur (MFA)](/azure/active-directory/authentication/concept-mfa-howitworks.md)** — MFA requiert que les utilisateurs fournissent deux formes de vérification, comme un mot de passe utilisateur plus une notification à partir de l’application Microsoft Authenticator ou un appel téléphonique. MFA réduit considérablement le risque qu’une identité peut être utilisé pour accéder à votre environnement Office 365.
- **[Accès conditionnel](/azure/active-directory/conditional-access/overview.md)** — Azure AD évalue les conditions de la connexion de l’utilisateur et utilise les stratégies d’accès conditionnel que vous créez pour autoriser l’accès. Par exemple, dans ce guide nous vous montrer comment créer une stratégie d’accès conditionnel pour exiger que la conformité de périphérique pour l’accès aux données sensibles. Cela réduit le risque qu’un pirate avec une identité peut accéder à vos données sensibles. Il protège également les données sensibles sur les appareils, car les périphériques répondant à des besoins spécifiques pour l’intégrité et la sécurité.
- **[Groupes d’Azure AD](/azure/active-directory/fundamentals/active-directory-manage-groups.md)** — règles d’accès conditionnel, gestion des périphériques avec Intune, et même des autorisations sur les sites de votre organisation et les fichiers reposent sur l’affectation à des utilisateurs ou groupes Azure AD. Nous vous recommandons de que créer des groupes Azure AD qui correspondent aux niveaux de protection que vous implémentez. Par exemple, votre équipe de production est susceptibles de cibles de valeur supérieures pour les pirates. Par conséquent, il est judicieux affecter ces employés à un groupe d’Azure AD et affectez ce groupe aux stratégies d’accès conditionnel et les autres stratégies qui appliquent un niveau plus élevé de protection de l’accès.
- **[Inscription de l’appareil](/azure/active-directory/devices/overview.md)** — vous inscrivez un périphérique dans Azure AD pour fournir une identité au périphérique. Ce paramètre identity est utilisé pour authentifier le périphérique lorsqu’un utilisateur se connecte et appliquer des règles d’accès conditionnel qui nécessitent des PC compatible ou à un domaine. Pour ce guide, nous utilisons l’inscription de périphérique enregistrer automatiquement à un domaine des ordinateurs Windows. Inscription de l’appareil est requis pour la gestion des appareils avec Intune. 
- **[Protection d’Azure AD identité](/azure/active-directory/identity-protection/overview)** — Protection Azure AD identité vous permet de détecter les vulnérabilités potentielles affectant les identités de votre organisation et de configurer la stratégie de mise à jour automatique à risque faible, moyen et élevé connexion et les risques de l’utilisateur. Ce guide s’appuie sur cette évaluation des risques pour appliquer des stratégies d’accès conditionnel pour l’authentification multifacteur. Ce guide inclut également une stratégie d’accès conditionnel qui requiert que les utilisateurs à modifier leur mot de passe en cas de détection d’activité risque élevé pour leur compte.

### <a name="microsoft-intune"></a>Microsoft Intune

[Intune](https://docs.microsoft.com/intune/introduction-intune) est un service de gestion d’appareil mobile en nuage de Microsoft. Ce guide recommande de gestion de PC Windows Intune avec des périphériques et recommande des configurations de stratégie de conformité de l’appareil. Intune détermine si les périphériques sont conformes et envoie ces données Azure AD à utiliser lors de l’application des stratégies d’accès conditionnel.

#### <a name="intune-app-protection"></a>Protection d’application Intune

Stratégies de [protection d’application Intune](https://docs.microsoft.com/intune/app-protection-policy) permet de protéger les données de votre société dans les applications mobiles avec ou sans périphériques inscription dans gestion. Intune vous permet de protéger les informations d’Office 365, vous assurer que vos employés peuvent être toujours une perte de données productive et prévention. En mettant en œuvre des stratégies au niveau de l’application, vous pouvez restreindre l’accès à des ressources d’entreprise et conserver des données dans le contrôle de votre service informatique.

Ce guide vous montre comment créer des stratégies recommandées pour imposer l’utilisation d’applications approuvées et déterminer comment ces applications peuvent être utilisées avec les données de votre entreprise.

### <a name="office-365"></a>Office 365

Ce guide vous montre comment implémenter un ensemble de stratégies pour protéger l’accès à Office 365, notamment Exchange Online, SharePoint Online et OneDrive for Business. Outre l’implémentation de ces stratégies, nous vous recommandons de que vous également augmentez le niveau de protection de votre client Office 365 à l’aide de ces ressources :

- [Configurer votre client Office 365 pour accroître la sécurité](https://support.office.com/article/Configure-your-Office-365-tenant-for-increased-security-8d274fe3-db51-4107-ba64-865e7155b355) , les recommandations suivantes s’appliquent à la sécurité de base pour votre client Office 365.
- [Feuille de route de sécurité office 365 : principaux des priorités pour les 30 premiers jours, 90 jours et au-delà](https://support.office.com/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) — ces recommandations incluent la journalisation, la gouvernance des données, l’accès d’administration et protection contre les menaces.
- [Fichiers et des sites d’informations sécurisé SharePoint Online](https://docs.microsoft.com/office365/enterprise/secure-sharepoint-online-sites-and-files) , cet ensemble d’articles explique comment protéger les fichiers et aux niveaux appropriés pour la protection sensibles et hautement confidentielles de planification, les sites.

### <a name="windows-10-and-office-365-proplus"></a>Windows 10 et Office 365 ProPlus

10 Windows et Office 365 ProPlus sont l’environnement du client recommandé pour les ordinateurs. Nous vous recommandons de 10 Windows Azure est conçu pour fournir l’expérience un possible pour locale et Azure AD. 10 Windows inclut également des fonctionnalités avancées de sécurité qui peuvent être gérées par le biais de Intune. Office 365 ProPlus inclut les dernières versions des applications Office. Ces utilisent l’authentification moderne, ce qui est plus sécurisée et une spécification pour un accès conditionnel. Ces applications comprennent également des outils de sécurité et conformité améliorées.

## <a name="applying-these-capabilities-across-the-three-tiers-of-protection"></a>Appliquer ces fonctionnalités sur les trois couches de protection

Le tableau suivant résume nos recommandations pour l’utilisation de ces fonctionnalités sur les trois couches de protection.

|Mécanisme de protection|Baseline|Sensible|Hautement réglementé|
|:-------------------|:-------|:--------|:---------------|
|**Appliquer une authentification multifacteur**|En cas de risque de connexion moyen ou supérieur|En cas de risque de connexion faible ou supérieur|Pour toutes les nouvelles sessions|
|**Appliquer une modification de mot de passe**|Pour les utilisateurs à haut risque|Pour les utilisateurs à haut risque|Pour les utilisateurs à haut risque|
|**Appliquer la protection des applications Intune**|Oui|Oui|Oui|
|**Appliquer l’inscription à Intune (COD)**|Exiger un conforme ou domaine joint PC, mais autoriser BYOD téléphones/tablettes|Exiger un appareil conforme ou joint à un domaine|Exiger un appareil conforme ou joint à un domaine|

## <a name="device-ownership"></a>Propriété des appareils

Le tableau ci-dessus reflète la tendance pour de nombreuses organisations prendre en charge un mélange de périphériques appartenant à l’entreprise, ainsi que des périphériques personnels ou mettre vos propres (BYOD) pour activer la productivité mobile sur les ressources. Stratégies de Protection des applications Intune Assurez-vous que le courrier électronique est protégé contre exfiltrating en dehors de l’application mobile Outlook et autres applications mobiles Office, sur les périphériques appartenant à l’entreprise et BYOD.  

Nous vous recommandons de périphériques appartenant à l’entreprise être gérés par Intune ou à un domaine pour appliquer les protections supplémentaires et le contrôle.  Selon la sensibilité des données, votre organisation peut choisir pour n’autoriser BYOD de nombreux utilisateurs spécifiques ou des applications spécifiques.

## <a name="next-steps"></a>Étapes suivantes

[Travail requis pour l’implémentation des stratégies d’accès identité et de périphérique](identity-access-prerequisites.md)