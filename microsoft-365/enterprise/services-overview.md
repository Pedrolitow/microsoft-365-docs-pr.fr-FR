---
title: Vue d’ensemble des services Microsoft 365 Enterprise | Microsoft Docs
description: Ce document fournit une vue d’ensemble de Microsoft 365 Enterprise et des recommandations relatives à son utilisation.
author: jeffgilb
manager: femila
ms.prod: microsoft-365-business
ms.topic: article
ms.date: 08/23/2017
ms.author: jeffgilb
ms.reviewer: jsnow
ms.custom: it-pro
ms.openlocfilehash: 7772421a32abd863f4301a4bc3d8264d8fe44242
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867400"
---
# <a name="microsoft-365-enterprise-services-and-concepts"></a>Concepts et services de Microsoft 365 Enterprise

Conçu pour les grandes entreprises, Microsoft 365 Entreprise intègre Office 365 Entreprise, Windows 10 Entreprise et Enterprise Mobility + Security (EMS) pour permettre à tous d’être créatifs et de travailler ensemble, en toute sécurité. Microsoft 365 Entreprise comprend une édition Entreprise de Windows 10 et des applications Office avec Office 365 ProPlus.

En mars et en septembre, Windows 10 et Office 365 ProPlus fournissent à l’entreprise de nouvelles versions des fonctionnalités par le biais du Canal semi-annuel. La version d’une fonctionnalité sur le Canal semi-annuel est prise en charge pendant 18 mois. Microsoft Intune et System Center Configuration Manager offrent tous deux la possibilité de déployer et de mettre à jour Windows 10 et Office 365 ProPlus.

Voici les dernières versions de Windows 10, Office 365 ProPlus, Microsoft Intune et System Center Configuration Manager :

|     |**Canal semi-annuel (ciblé)**|**Canal semi-annuel**|
|:-----|:-----|:-----|
|**Windows 10**|Windows 10 Fall Creators Update (bientôt disponible)|Version 1703|
|**Office 365 ProPlus**|Version 1803|Version 1708|
|**Intune**|N/A|Version 1708|
|**System Center Configuration Manager**|Technical Preview Version 1708|Version 1706<sup>*</sup>|

<sup>*</sup> La mise à jour 1706 de la version Current Branch de System Center Configuration Manager est une mise à jour dans la console des sites déjà installés avec la version 1606, 1610 ou 1702.

> [!NOTE]
> Les services Microsoft Azure sont également mis à jour régulièrement, mais ne sont pas référencés par un numéro de version. Pour connaître les dernières mises à jour et les nouveautés à venir des services Azure, consultez la [feuille de route de la plateforme cloud](https://www.microsoft.com/cloud-platform/roadmap).

Pour plus d’informations sur les fonctionnalités disponibles dans ces versions, consultez les articles suivants :
- [Nouveautés de Windows 10](https://docs.microsoft.com/windows/whats-new/)
- [Informations sur les versions de Windows 10](https://technet.microsoft.com/windows/release-info)
- [Historique des mises à jour de Windows 10](https://support.microsoft.com/help/4018124/windows-10-update-history)
- [Versions du canal de mise à jour du client Office 365](https://technet.microsoft.com/office/mt465751)
- [Nouveautés de Microsoft Intune](https://docs.microsoft.com/intune/whats-new)
- [Nouveautés de System Center Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/changes/whats-new-incremental-versions)
- [Fonctionnalités de la version Technical Preview 1708 de System Center Configuration Manager](https://docs.microsoft.com/sccm/core/get-started/capabilities-in-technical-preview-1708)

## <a name="services-overview"></a>Vue d’ensemble des services

Cette section fournit une vue d’ensemble des services EMS et Office 365 inclus avec Microsoft 365 Enterprise, et présente également les concepts de base nécessaires pour comprendre comment l’utiliser au mieux en fonction des besoins de votre organisation. Ces services fournissent des fonctionnalités qui permettent aux administrateurs d’entreprise Microsoft Cloud non seulement de protéger les identités et les appareils des employés de la société, mais également de contrôler l’accès aux données d’entreprise proprement dites, à la fois en transit et au repos.

|Service|Description|
|-------|-----------|
|[Microsoft Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis)|Azure AD fournit une suite complète de fonctionnalités de gestion d’identités, notamment l’authentification multifacteur, l’inscription d’appareils, la gestion des mots de passe libre-service, la gestion des groupes libre-service, le contrôle d’accès en fonction du rôle, l’analyse de l’utilisation des applications, un audit enrichi, ainsi qu’une surveillance et des alertes de sécurité.|
|[Azure AD Identity Protection](https://docs.microsoft.com/azure/active-directory/active-directory-identityprotection)|Ce service vous permet de détecter les vulnérabilités potentielles qui affectent les identités de votre organisation, et de configurer des réponses automatiques par l’intermédiaire de stratégies d’accès conditionnel en cas de risques de connexion et risques utilisateur de niveau faible, moyen et élevé.|
|[Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)|Ce service permet aux organisations de réduire le nombre de personnes qui ont un accès permanent aux opérations privilégiées. Azure AD Privileged Identity Management introduit le concept d’administrateur éligible. Les administrateurs éligibles doivent être des utilisateurs qui ont besoin d’un accès privilégié de temps en temps, mais pas tous les jours. Le rôle est inactif jusqu’à ce que l’utilisateur ait besoin de l’accès. Il effectue alors un processus d’activation et devient un administrateur actif pendant un laps de temps prédéterminé.|
|[Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection)| Azure Information Protection est une solution basée sur le cloud, délivrée dans le cadre de l’offre SMS E5, qui permet à une organisation de classifier, d’étiqueter et de protéger ses documents et ses e-mails. Ces opérations peuvent être effectuées automatiquement par les administrateurs qui définissent des règles et des conditions ou manuellement par les utilisateurs, qui peuvent éventuellement se voir proposer des recommandations. Les étiquettes Azure Information Protection vous permettent d’appliquer une classification aux documents et e-mails. Ainsi, la classification est identifiable à tout moment, quel que soit l’endroit où les données sont stockées ou avec qui elles sont partagées.<br><br>Les paramètres de stratégie Azure Information Protection sont protégés par [Azure Rights Management](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms). À l’image des étiquettes appliquées, la protection avec Rights Management reste associée aux documents et aux e-mails, indépendamment de leur emplacement (à l’intérieur ou en dehors de votre organisation, de vos réseaux, de vos serveurs de fichiers et de vos applications).|
|[Microsoft Intune](https://docs.microsoft.com/intune/understand-explore/introduction-to-microsoft-intune)|Intune est un service de gestion de la mobilité en entreprise basé sur le cloud qui permet à votre personnel de rester productif tout en protégeant vos données d’entreprise. Intune s’intègre étroitement avec Azure AD pour le contrôle d’accès et d’identité, et s’utilise dans le cadre de la gestion des appareils et des applications. Les fonctionnalités de [gestion d’appareils d’Intune](https://docs.microsoft.com/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) servent à configurer et à protéger les appareils de vos utilisateurs, notamment les PC Windows.<br><br>Les fonctionnalités de gestion d’appareils d’Intune prennent en charge à la fois l’inscription [BYOD (Bring Your Own Device)](https://docs.microsoft.com/enterprise-mobility-security/solutions/enable-byod), qui permet aux utilisateurs d’inscrire leurs téléphones, tablettes ou PC personnels, et l’inscription [COD (Corporate-owned Device)](https://docs.microsoft.com/enterprise-mobility-security/solutions/issue-corp-devices), qui autorise des scénarios de gestion tels que l’inscription automatique, le partage d’appareils ou les configurations d’exigences d’inscription préautorisée. Pour renforcer la sécurité, vous pouvez même exiger l’authentification multifacteur (MFA) pour inscrire un appareil. Une fois les appareils inscrits pour la gestion, Intune peut configurer leurs fonctionnalités et paramètres pour activer l’accès sécurisé aux ressources d’entreprise.|

## <a name="important-concepts-to-understand"></a>Concepts importants
Les principaux concepts et fonctionnalités EMS avec lesquels vous devez vous familiariser sont décrits dans le tableau ci-dessous.

|Concept de base|Description|
|------------|-----------|
|[Azure Multi-Factor Authentication (MFA)](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud)|Solution de vérification Microsoft en deux étapes, Azure MFA contribue à protéger l’accès aux données et aux applications tout en répondant aux demandes des utilisateurs en matière de simplicité du processus de connexion. Elle fournit une authentification forte par le biais de diverses méthodes de vérification, notamment les appels téléphoniques, les messages texte ou la vérification des applications mobiles.|
|[Accès conditionnel Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)|Cette fonctionnalité d’Azure AD vous permet d’appliquer des contrôles sur l’accès aux applications cloud dans votre environnement en fonction de conditions spécifiques. Grâce aux contrôles, vous pouvez soit lier des exigences supplémentaires à l’accès, soit le bloquer. L’implémentation de l’accès conditionnel est basée sur des stratégies.|
|[Protection contre la perte de données (DLP) Exchange Online](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)|Les stratégies de Protection contre la perte de données (DLP) Exchange Online, disponibles en tant que fonctionnalité premium avec les abonnements Exchange Online Plan 2 et Office 365, permettent aux organisations d’identifier, de surveiller et de protéger automatiquement les informations sensibles dans Office 365.<br><br>Grâce aux stratégies DLP Exchange Online, vous pouvez identifier les informations sensibles à de nombreux emplacements, comme Exchange Online, SharePoint Online et OneDrive Entreprise. Ces stratégies peuvent par exemple vous aider à identifier les documents contenant des informations sensibles ou à empêcher le partage accidentel d’informations sensibles avec des personnes extérieures à votre organisation.|
|[Règles de transport/flux de messagerie Exchange](https://support.office.com/article/Define-mail-flow-rules-to-encrypt-or-decrypt-email-messages-9B7DAF19-D5F2-415B-BC43-A0F5F4A585E8)|Les règles de flux de messagerie, également appelées règles de transport, recherchent des conditions spécifiques dans les messages qui passent par votre organisation et effectuent des actions sur ces messages. Elles s’apparentent aux règles de boîte de réception disponibles dans de nombreux clients de messagerie. La principale différence entre les règles de flux de messagerie et les règles définies dans une application cliente telle qu’Outlook est que les règles de flux de messagerie agissent sur les messages pendant qu’ils sont en transit, plutôt qu’une fois le message remis. Elles contiennent également un ensemble enrichi de conditions, d’exceptions et d’actions, ce qui offre la flexibilité nécessaire pour mettre en œuvre de nombreux types de stratégies de messagerie.|
|[Gestion des appareils mobiles Intune](https://docs.microsoft.com/intune/understand-explore/introduction-to-microsoft-intune)|Intune fournit la gestion des appareils mobiles en utilisant les protocoles ou les API disponibles dans les systèmes d’exploitation mobiles. Il inclut des tâches telles que l’inscription d’appareils pour la gestion (qui permet au service Informatique de disposer d’un inventaire des appareils qui accèdent aux services d’entreprise), la configuration des appareils pour garantir leur conformité aux normes de sécurité et d’intégrité de la société, la fourniture de certificats et de profils Wi-Fi/VPN pour l’accès aux services d’entreprise, la création de rapports et la mesure de la conformité des appareils aux normes d’entreprise, ainsi que la suppression des données d’entreprise des appareils gérés.|
|[Stratégies de protection des applications Intune](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)|Vous pouvez utiliser des stratégies de protection des applications Intune pour protéger les données de votre société dans les applications mobiles avec ou sans inscrire les appareils pour la gestion. En fait, les appareils mobiles de vos utilisateurs peuvent même être gérés par une autre solution de gestion des appareils mobiles non-Microsoft pendant qu’[Intune aide à protéger les informations Office 365](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-company-data-without-managing-devices). Tout en veillant à ce que vos employés continuent à être productifs, vous pouvez également éviter toute perte de données, qu’elle soit intentionnelle ou non. En implémentant des stratégies au niveau de l’application, vous pouvez restreindre l’accès aux ressources d’entreprise et veiller à ce que votre service Informatique conserve le contrôle des données.|
|[Durée de vie des jetons Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-configurable-token-lifetimes)|Vous pouvez spécifier la durée de vie d’un jeton émis par Azure Active Directory (Azure AD). Vous pouvez définir les durées de vie des jetons pour toutes les applications de votre organisation, pour une application mutualisée (multi-organisation) ou pour un principal de service spécifique dans votre organisation.|
|Brokers d’identités Microsoft|Microsoft fournit des applications pour chaque plateforme mobile qui autorisent le pontage d’informations d’identification entre les applications de différents fournisseurs et offrent des fonctionnalités améliorées spéciales qui requièrent un emplacement sécurisé unique à partir duquel valider les informations d’identification. Nous appelons ces applications des « brokers ». Sur iOS et Android, ces brokers sont fournis par l’intermédiaire des applications Microsoft Authenticator et Portail d’entreprise Intune. Dans Windows 10, cette fonctionnalité est fournie par un sélecteur de compte intégré au système d’exploitation, appelé « Broker d’authentification web ».|

## <a name="security-best-practices-and-recommendations"></a>Recommandations et bonnes pratiques en matière de sécurité
Si une même recommandation unique ne peut être faite pour l’ensemble des environnements des clients, l’article sur les [stratégies et configurations de sécurité recommandées](microsoft-365-policies-configurations.md) présente les concepts des bonnes pratiques de sécurité qu’il est important de comprendre. Cet article décrit également des recommandations générales de Microsoft sur la façon d’appliquer une stratégie et une configuration dans le cloud Microsoft, pour garantir que vos employés travaillent de façon sécurisée et productive.

### <a name="baseline-recommended-security-policies-and-configurations"></a>Configurations et stratégies de sécurité de base recommandées
[Recommandations générales sur la stratégie pour les identités et l’accès aux appareils](identity-access-policies.md) décrit des stratégies courantes recommandées qui vous aident à sécuriser Microsoft 365 Enterprise. L’article présente également les configurations clientes de plateforme par défaut que nous vous recommandons pour fournir la meilleure expérience d’authentification unique à vos utilisateurs, ainsi que les prérequis techniques pour l’accès conditionnel.

### <a name="exchange-online-access-policies"></a>Stratégies d’accès à Exchange Online
[Recommandations sur les stratégies de sécurisation de la messagerie](secure-email-recommended-policies.md) contient des recommandations de Microsoft pour vous aider à sécuriser la messagerie d’une organisation, ainsi que les clients de messagerie qui prennent en charge l’authentification moderne et l’accès conditionnel. Ces recommandations s’ajoutent aux [recommandations communes sur les stratégies d’accès et d’identité](identity-access-policies.md).

### <a name="sharepoint-online-access-policies"></a>Stratégies d’accès à SharePoint Online
Des recommandations sont fournies pour [protéger l’accès aux fichiers SharePoint Online](sharepoint-file-access-policies.md), en plus des [recommandations communes sur les stratégies d’accès et d’identité](identity-access-policies.md) et des [recommandations sur les stratégies de sécurisation de la messagerie](secure-email-recommended-policies.md). Cet article décrit les nouvelles stratégies qui doivent être créées et comment les stratégies existantes doivent être modifiées pour protéger l’accès à la messagerie Exchange Online et aux fichiers SharePoint Online.

## <a name="deploy-windows-10-and-office-365-proplus"></a>Déployer Windows 10 et Office 365 ProPlus
Découvrez comment déployer Windows 10 et Office 365 ProPlus, et les intégrer à Microsoft Azure Active Directory (Azure AD) ou à Active Directory Domain Services (AD DS) en local. Déployez Windows 10, Office 365 ProPlus et vos autres applications métier sur de nouveaux appareils, ou mettez à niveau des appareils existants vers Windows 10 avec Intune, System Center Configuration Manager et la stratégie de groupe pour gérer les appareils.

Pour plus d'informations, consultez les articles suivants :
- [Considérations relatives au déploiement Windows 10](https://docs.microsoft.com/windows/deployment/planning/windows-10-deployment-considerations)
- [Guide de déploiement d’Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [Guide des meilleures pratiques pour le déploiement d’Office 365 ProPlus dans l’entreprise](https://docs.microsoft.com/DeployOffice/best-practices/best-practices)
- [Déployer des applications Office 365 ProPlus sur des appareils Windows 10 à l’aide d’Intune](https://docs.microsoft.com/intune/apps-add-office365)

Pour obtenir une assistance sur le déploiement de Microsoft 365, [contactez FastTrack](https://fasttrack.microsoft.com/microsoft365).

## <a name="manage-updates-to-windows-10-and-office-365-proplus"></a>Gérer les mises à jour Windows 10 et Office 365 ProPlus
Les liens suivants vous montrent comment obtenir un contrôle maximal des mises à jour qualité et des mises à jour des fonctionnalités de Windows 10 et d’Office 365 ProPlus. Découvrez comment contrôler efficacement l’utilisation de la bande passante et maintenir Windows et Office à jour avec les dernières fonctionnalités, capacités et mises à jour de sécurité.

Pour plus d'informations, consultez les articles suivants :
- [Vue d’ensemble de Windows en tant que service](https://docs.microsoft.com/windows/deployment/update/waas-overview)
- [Présentation des canaux de mise à jour d’Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)
- [Gérer les mises à jour logicielles avec Intune](https://docs.microsoft.com/intune/windows-update-for-business-configure)
- [Déployer les mises à jour de Windows 10 avec System Center Configuration Manager](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-configuration-manager)<sup>*</sup>
- [Gérer Office 365 ProPlus avec Configuration Manager](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates)

<sup>*</sup>Microsoft encourage les organisations qui utilisent actuellement Configuration Manager pour la gestion des mises à jour Windows à faire de même pour les ordinateurs clients Windows 10.

## <a name="next-steps"></a>Étapes suivantes
[Page du produit Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise)<br/>
[Feuille de route de la plateforme cloud](https://www.microsoft.com/cloud-platform/roadmap)
