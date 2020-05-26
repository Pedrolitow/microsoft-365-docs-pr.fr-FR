---
title: Infrastructure de base de Microsoft 365 pour entreprise pour les non-entreprises
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
ms.date: 05/15/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Suivez les phases simplifiées de l’infrastructure de base pour Microsoft 365 pour entreprise pour les organisations tierces.
ms.openlocfilehash: caca093463e4a180f50c880a77fa18399103f069
ms.sourcegitcommit: 47c45bd81afdc4867ff2980ced3df31dbad92b84
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "44268384"
---
# <a name="microsoft-365-for-enterprise-foundation-infrastructure-for-non-enterprises"></a>Infrastructure de base de Microsoft 365 pour entreprise pour les non-entreprises

Les organisations tierces peuvent également déployer Microsoft 365 pour entreprise et tirer parti de la valeur commerciale d’une infrastructure intégrée et sécurisée qui permet de créer des équipes et de libérer leur créativité. Une entreprise tierce possède généralement :

- Une petite quantité d’infrastructure informatique locale, par exemple, des serveurs de messagerie et de fichiers et un domaine AD DS (Active Directory Domain Services), ou aucune.
- Une petite équipe informatique, principalement composée d’informaticiens généralistes, plutôt que de spécialistes d’une technologie ou d’une charge de travail particulière, comme la mise en réseau ou le courrier électronique.

Pour les organisations non commerciales de plus petite taille, Microsoft propose [Microsoft 365 Entreprise](https://www.microsoft.com/microsoft-365/business). Cependant, vous pouvez parfois avoir besoin de Microsoft 365 pour entreprise, par exemple dans les cas suivants :

- Votre organisation a ou aura besoin de plus de 300 licences Microsoft 365, ce qui correspond au nombre maximum pour Microsoft 365 Entreprise.
- Votre organisation a besoin de fonctionnalités avancées de productivité, de voix, de sécurité et d’analyse qui ne sont pas disponibles avec Microsoft 365 Entreprise.

Cet article vous explique comment procéder à un déploiement simplifié de l’infrastructure de base de Microsoft 365 pour entreprise conformément à vos besoins.

## <a name="first-set-up-your-subscription"></a>Tout d’abord, configurez votre abonnement

Vous devez configurer les domaines DNS (Domain Name System) pour votre abonnement. Si vous disposez déjà d’un abonnement Microsoft 365, cela devrait être fait. Si ce n’est pas le cas , suivez les instructions de la section [Ajouter un domaine à Office 365](https://docs.microsoft.com/office365/admin/setup/add-domain?view=o365-worldwide).

Vous devez ensuite configurer une sécurité supplémentaire pour Microsoft 365. Suivez les instructions de la section[ configurer l’augmentation de la sécurité](https://docs.microsoft.com/office365/securitycompliance/tenant-wide-setup-for-increased-security).

## <a name="phase-1-networking"></a>Phase 1 : Mise en réseau

Les organisations qui ne sont pas des entreprises ont généralement une connexion Internet locale dans chacun de leurs bureaux et n’utilisent pas de serveur proxy, de pare-feu ou d’autres appareils d’inspection des paquets. Le fournisseur de services Internet (ISP) qui dessert chaque bureau dispose d’un serveur DNS local. Ainsi, le trafic est dirigé vers l’emplacement réseau Microsoft 365 le plus proche de vos bureaux et de leurs utilisateurs locaux. Pour plus d’informations, consultez [Configurer les connexions Internet locales pour chaque bureau](networking-dns-resolution-same-location.md).

Par conséquent, il vous suffit de vérifier auprès de votre fournisseur de services Internet que la connexion à chacun de vos bureaux :

- Utilise un serveur DNS local.
- Convient aux besoins actuels et à venir, sachant que vos utilisateurs commencent à utiliser d’autres services cloud Microsoft 365.

Si vous utilisez des serveurs proxy, des pare-feu ou des dispositifs d’inspection des paquets, consultez [Configurer le contournement du trafic](networking-configure-proxies-firewalls.md) pour en savoir plus sur l’optimisation des performances des services Microsoft 365.

### <a name="your-configuration-so-far"></a>Votre configuration jusqu’à présent

Voici un résumé visuel avec l’élément phase 1 mis en surbrillance. **Votre organisation** peut se répartir entre plusieurs bureaux, chacun d’eux disposant d’une connexion Internet locale avec un fournisseur d’accès Internet qui utilise un serveur DNS local. Grâce au fournisseur de services Internet, les utilisateurs de chaque bureau ont accès à l’emplacement réseau Microsoft 365 le plus proche et aux ressources de votre abonnement Microsoft 365.

![Votre organisation après la phase Mise en réseau](../media/deploy-foundation-infrastructure-non-enterprises/networking-config.png)

## <a name="phase-2-identity"></a>Phase 2 : Identité

Chacun des employés de votre organisation doit être en mesure de se connecter, ce qui nécessite un compte d’utilisateur dans le client Azure Active Directory (Azure AD) de votre abonnement Microsoft 365 pour entreprise. Des groupes sont ensuite utilisés pour contenir les comptes d’utilisateurs et d’autres groupes afin de communiquer ou d’accéder aux ressources autorisées, telles qu’un site SharePoint Online ou une équipe. 

### <a name="administrator-accounts"></a>Comptes d’administrateur

Protégez les comptes d’utilisateur de votre administrateur général en demandant des mots de passe forts et une authentification multifacteurs (MFA). Voir [Protéger des comptes Administrateur général](identity-create-protect-global-admins.md#protect-global-administrator-accounts) pour plus d’informations.

Si votre organisation requiert un niveau de sécurité élevé et que vous avez Microsoft 365 E5, utilisez Azure AD Privileged Identity Management pour activer l’accès administrateur en temps réel. Voir [Configurer des administrateurs généraux à la demande](identity-create-protect-global-admins.md#identity-pim) pour plus d’informations.

### <a name="recommendations-for-groups"></a>Recommandations pour les groupes

Si vous avez un domaine AD DS local, continuez à utiliser ces groupes dans Microsoft 365 pour entreprise comme groupes dans Azure AD.

Si vous n’avez pas de domaine AD DS local, créez des groupes de sécurité dans Azure AD à l’aide de ces niveaux de sécurité.

| Niveau de sécurité | Description | Exemples |
|:-------|:-----|:-----|
| Base de référence | Il s’agit d’une norme minimale pour la protection des données, ainsi que les identités et les appareils qui accèdent à vos données. <BR><BR> Il s’agit généralement de la plupart des données de votre organisation gérées par la plupart de vos utilisateurs. | Groupes pour les travailleurs de premier rang, tels ventes, marketing, service clientèle, administration et fabrication. |
| Sensible | Il s’agit d’une protection supplémentaire pour un sous-ensemble de vos données qui doivent être protégées au-delà du niveau de base. Ces groupes contiennent des utilisateurs qui utilisent et créent des données sensibles propres aux services et projets qui ne sont pas destinés à être mis à la disposition de tout le monde. | Équipes produit ou marketing qui développent de futurs produits |
| Hautement réglementé | Il s’agit du niveau de protection le plus élevé pour un petit nombre de données très classifiées, considérées comme des secrets de propriété intellectuelle ou des secrets commerciaux ou des données qui doivent respecter les réglementations en matière de sécurité. |  Les équipes de recherche, juridiques et financières, tout comme celles qui stockent ou utilisent les données des clients ou des partenaires. |
||||

### <a name="hybrid-identity"></a>Identité hybride

Si vous avez un domaine AD DS local, vous devez synchroniser l’ensemble des comptes d’utilisateurs, des groupes et des contacts de votre domaine avec le locataire Azure AD de votre abonnement Microsoft 365 pour entreprise. Pour votre entité non-entreprise, configurez Azure AD Connect sur un serveur avec la synchronisation de hachage de mot de passe. Pour plus d’informations, consultez [Synchroniser les identités](identity-add-user-accounts.md#synchronize-identities-for-hybrid-identity).

### <a name="more-secure-user-access-with-conditional-access-policies"></a>Accès utilisateur plus sécurisé grâce aux stratégies d’accès conditionnel

Azure AD évalue les conditions liées aux connexions utilisateur et peut utiliser des stratégies d’accès conditionnel pour accorder ou refuser l’accès, et imposer d’autres actions afin de faire aboutir la connexion. Par exemple, si Azure AD détermine que le risque lié à la connexion est moyen ou élevé, une authentification multifacteur peut être exigée pour faire aboutir cette connexion.

Les stratégies d’accès conditionnel s’appliquent aux comptes ou groupes d’utilisateurs. Pour faciliter l’attribution des stratégies d’accès conditionnel, créez les groupes de sécurité Azure AD suivants au sein de votre organisation :

- RÉFÉRENCE

  Contient les groupes ou comptes d’utilisateur pour les utilisateurs ayant accès aux données de base.

- SENSIBLE

  Contient les groupes ou comptes d’utilisateur pour les utilisateurs ayant accès aux données de sensibles.

- HAUTEMENT RÉGLEMENTÉ

  Contient les groupes ou comptes d’utilisateur pour les utilisateurs ayant accès aux données hautement réglementées.

- ACCÈS-COND-EXCLURE

  Groupe vide que vous pouvez utiliser pour exclure temporairement un utilisateur des stratégies d’accès conditionnel.

Voici la liste des stratégies d’accès conditionnel Azure AD à activer ou à créer.

| Stratégie d’accès conditionnel Azure AD | Groupes auxquels elle s’applique |
|:------|:-----|
| Stratégie de référence: exiger l’authentification multifacteur pour les administrateurs | Cette stratégie s’applique aux rôles d’administrateur, de sorte qu’aucun groupe ne doit être spécifié. Cette stratégie doit juste être activée. Toutes les stratégies suivantes doivent être créées et activées. |
| Bloquer les clients ne prenant pas en charge l’authentification moderne | Dans les paramètres de stratégie, sélectionnez « Tous les utilisateurs ». |
| Exiger l’authentification multifacteur lorsque les risques de connexion sont moyens ou élevés (requiert Microsoft 365 E5) | RÉFÉRENCE |
| Exiger l’authentification multifacteur lorsque les risques de connexion sont faibles, moyens ou élevés (requiert Microsoft 365 E5) | SENSIBLE |
| Toujours exiger l’authentification multifacteur  | HAUTEMENT RÉGLEMENTÉ |
| Exiger des applications approuvées sur les appareils iOS et Android | BASE DE RÉFÉRENCE, SENSIBLE, HAUTEMENT RÉGLEMENTÉ |
| Exiger des PC conformes | BASE DE RÉFÉRENCE |
| Nécessitez des PC conformes et des appareils iOS et Android | SENSIBLE, HAUTEMENT RÉGLEMENTÉ |
|||

Voici la Azure Active Directory Identity Protection (requiert Microsoft 365 E5) stratégie de risque pour les utilisateurs à créer et à activer.

| Stratégie d’utilisateur à risque Azure AD Identity Protection | Groupes auxquels elle s’applique |
|:------|:-----|
| Les utilisateurs à risque élevé doivent modifier leur mot de passe | Dans les paramètres de stratégie, sélectionnez « Tous les utilisateurs ». |
|||

Voir [Stratégies d’accès aux identités et aux appareils communes](identity-access-policies.md) pour les instructions.

### <a name="groups-for-easier-management"></a>Utiliser des groupes pour faciliter la gestion

Voici quelques fonctionnalités qui vous permettent de simplifier la gestion des groupes et des licences.

| Fonctionnalité | Utilisation |
|:------|:-----|
| Gestion des groupes en libre-service | Autoriser la gestion des groupes Azure AD par les propriétaires de groupes au lieu du personnel informatique. Pour plus d’informations, voir [Gestion des groupes en libre-service](identity-use-group-management.md#allow-users-to-create-and-manage-their-own-groups). |
| Appartenance à un groupe dynamique | Configurer l’ajout ou la suppression automatique de comptes d’utilisateurs à partir d’Azure AD Groupes sur la base des attributs de compte d’utilisateur, tels que service ou pays. Pour plus d’informations, voir[appartenance aux groupes dynamiques](identity-use-group-management.md#set-up-dynamic-group-membership). |
| Gestion des licences en fonction des groupes  | Utilisez l’appartenance au groupe pour attribuer ou retirer automatiquement des licences aux comptes d’utilisateurs. Pour plus d’informations, voir [gestion des licences basée sur les groupes](identity-use-group-management.md#set-up-automatic-licensing). |
|  |  |

Si vous utilisez une licence basée sur les groupes, créez un groupe nommé « sous licence » pour qu’il contienne les noms des comptes d’utilisateurs auxquels une licence Microsoft 365 pour entreprise est attribuée.

### <a name="monitor-user-access"></a>Surveiller l’accès utilisateur

Si vous avez Microsoft 365 E5, vous pouvez utiliser Azure Active Directory Identity Protection pour contrôler et analyser les connexions de l’utilisateur pour la compromission des informations d’identification. Pour plus d’informations, voir [protéger contre la compromission des informations d’identification](identity-secure-user-sign-ins.md#protect-against-credential-compromise).

### <a name="your-configuration-so-far"></a>Votre configuration jusqu’à présent

Voici une synthèse graphique de la phase Identité pour une identité hybride. Les éléments nouveaux et existants sont mis en surbrillance.

![Votre organisation après la phase Identité pour une identité hybride](../media/deploy-foundation-infrastructure-non-enterprises/identity-config.png)
 
Les éléments nouveaux et mis en surbrillance de l’identité hybride incluent :
 
|||
|:------:|:-----|
| ![Un domaine AD DS local avec des comptes et des groupes d’utilisateurs](../media/deploy-foundation-infrastructure-non-enterprises/identity-adds.png) | Un domaine AD DS local avec des comptes et des groupes d’utilisateurs. |
| ![Un serveur basé sur Windows exécutant Azure AD Connect](../media/deploy-foundation-infrastructure-non-enterprises/identity-aadconnect.png) | Un serveur basé sur Windows exécutant Azure AD Connect. |
| ![L’ensemble synchronisé des comptes et groupes d’utilisateurs AD DS dans Azure AD](../media/deploy-foundation-infrastructure-non-enterprises/identity-aad-accounts.png) | L’ensemble synchronisé des comptes et groupes d’utilisateurs AD DS dans Azure AD. |
| ![Les paramètres Azure AD pour l’authentification, la sécurisation des comptes globaux et la simplification de la gestion des groupes et des licences](../media/deploy-foundation-infrastructure-non-enterprises/identity-aad-settings.png) | Les paramètres Azure AD pour l’authentification, la sécurisation des comptes globaux et la simplification de la gestion des groupes et des licences. |
| ![Stratégies d’accès conditionnel Azure AD](../media/deploy-foundation-infrastructure-non-enterprises/identity-aad-caps.png) | Stratégies d’accès conditionnel Azure AD. |
|||

Voici une synthèse graphique de la phase Identité pour une identité réservée au cloud. Les éléments nouveaux sont mis en surbrillance.

![Votre organisation après la phase Identité pour une identité réservée au cloud](../media/deploy-foundation-infrastructure-non-enterprises/identity-config-cloud-only.png)
 
Les éléments nouveaux et mis en surbrillance de l’identité hybride réservée au cloud incluent :
 
|||
|:------:|:-----|
| ![Les comptes et groupes d’utilisateurs situés dans Azure AD](../media/deploy-foundation-infrastructure-non-enterprises/identity-aad-accounts-cloud-only.png) | Les comptes et groupes d’utilisateurs situés dans Azure AD. |
| ![Les paramètres Azure AD pour l’authentification, la sécurisation des comptes globaux et la simplification de la gestion des groupes et des licences](../media/deploy-foundation-infrastructure-non-enterprises/identity-aad-settings.png) | Les paramètres Azure AD pour l’authentification, la sécurisation des comptes globaux et la simplification de la gestion des groupes et des licences. |
| ![Stratégies d’accès conditionnel Azure AD](../media/deploy-foundation-infrastructure-non-enterprises/identity-aad-caps.png) | Stratégies d’accès conditionnel Azure AD. |
|||

## <a name="phase-3-windows-10-enterprise"></a>Phase 3 : Windows 10 Entreprise

Voici les options disponibles pour vous assurer que vos appareils Windows 10 Entreprise sont intégrés à l’infrastructure d’identité et de sécurité de Microsoft 365 pour entreprise :

- Hybride (vous avez un domaine AD DS local)

  Veuillez joindre au client Azure AD chaque appareil Windows 10 Entreprise déjà joint à votre domaine AD DS. Pour plus d’informations, consultez [Comment configurer des appareils hybrides joints à Azure Active Directory](https://go.microsoft.com/fwlink/p/?linkid=872870).

  Pour chaque nouvel appareil Windows 10 Entreprise, joignez-le à votre domaine AD DS, puis joignez-le au client Azure AD.

  Pour chaque appareil Windows 10 Entreprise, inscrivez-les pour la gestion des appareils mobiles. Si vous souhaitez en savoir plus, veuillez consulter la page [Inscrire un appareil Windows 10 avec Intune à l'aide d’une stratégie de groupe](https://go.microsoft.com/fwlink/p/?linkid=872871).

- Réservé(e) au cloud (vous n’avez pas de domaine AD DS local)

  Joignez chaque appareil Windows 10 Entreprise au client Azure AD de votre abonnement.

  Si vous souhaitez en savoir plus, veuillez consulter la page [Joindre votre appareil professionnel au réseau de votre organisation](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network).


Une fois installé et joint, chaque appareil Windows 10 Entreprise installe automatiquement les mises à jour à partir du service cloud Windows Update pour les entreprises. Il n’est généralement pas nécessaire dans une organisation qui n’est pas une entreprise de configurer une infrastructure pour distribuer et installer les mises à jour de Windows 10.

### <a name="your-configuration-so-far"></a>Votre configuration jusqu’à présent

Voici une synthèse graphique de la phase Windows 10 Entreprise. Les éléments nouveaux sont mis en surbrillance.

![Votre organisation après la phase Windows 10 Entreprise](../media/deploy-foundation-infrastructure-non-enterprises/win10-config.png)
 
Les éléments Windows 10 Entreprise nouveaux et mis en surbrillance incluent :

|||
|:------:|:-----|
| ![Windows 10 Entreprise est installé sur les appareils Windows](../media/deploy-foundation-infrastructure-non-enterprises/win10-device.png) | Windows 10 Entreprise est installé sur les appareils Windows, avec un ordinateur portable local comme exemple. |
| ![Le Centre de gestion des licences en volume](../media/deploy-foundation-infrastructure-non-enterprises/win10-cloud.png) | Le Centre de gestion des licences en volume, qui fournit des images pour les nouvelles installations de Windows 10 Entreprise, et le service Windows Update pour Entreprise, qui fournit les dernières mises à jour. |
|||

## <a name="phase-4-microsoft-365-apps-for-enterprise"></a>Phase 4 : Microsoft 365 Apps pour entreprise

Microsoft 365 pour entreprise inclut Microsoft 365 Apps pour entreprise, la version d’abonnement de Microsoft Office. Comme Office 2016 ou Office 2019, Microsoft 365 Apps pour entreprise est installé directement sur vos appareils clients. Toutefois, Microsoft 365 Apps pour entreprise reçoit de nouvelles mises à jour qui incluent régulièrement de nouvelles fonctionnalités. Si vous souhaitez en savoir plus, consultez la rubrique [À propos des Applications Microsoft 365 pour les grandes entreprises](https://docs.microsoft.com/deployoffice/about-microsoft-365-apps).

Dans la mesure où votre organisation est non commerciale, vous devez installer manuellement Microsoft 365 Apps pour entreprise sur vos appareils Windows, iOS et Android. Cette opération peut être effectuée dans le cadre de la préparation d’un nouvel appareil, ou par l’utilisateur dans le cadre de son processus d’intégration.

Dans les deux cas, l’administrateur ou l’utilisateur se connecte au portail Office 365 sur https://portal.office.com. Sous l'onglet **Accueil de Microsoft Office**, cliquez sur **installer Office** et exécutez le processus d’installation.

Les mises à jour de fonctionnalités de Microsoft 365 Apps pour entreprise sont téléchargées chaque mois par chaque ordinateur sur lequel il est installé. Il n’est généralement pas nécessaire dans une organisation non commerciale de configurer une infrastructure pour distribuer et installer les mises à jour de Microsoft 365 Apps pour entreprise. 

### <a name="your-configuration-so-far"></a>Votre configuration jusqu’à présent

Voici une synthèse visuelle de la phase de Microsoft 365 Apps pour entreprise, avec les nouveaux éléments mis en surbrillance.

![Votre organisation après la phase de Microsoft 365 Apps pour entreprise](../media/deploy-foundation-infrastructure-non-enterprises/o365-proplus-config.png)
 
Les nouveaux éléments mis en surbrillance de Microsoft 365 Apps pour entreprise incluent :
 
|||
|:------:|:-----|
| ![Microsoft 365 Apps pour entreprise installé sur les appareils](../media/deploy-foundation-infrastructure-non-enterprises/o365-proplus-device.png) | Microsoft 365 Apps pour entreprise est installé sur les appareils, avec un ordinateur portable local comme exemple. |
| ![Le réseau de distribution de contenu (CDN) de Microsoft 365 Apps pour entreprise](../media/deploy-foundation-infrastructure-non-enterprises/o365-proplus-cdn.png) | Le réseau de distribution de contenu (CDN) de Microsoft 365 Apps pour entreprise dont les appareils accèdent aux mises à jour de Microsoft 365 Apps pour entreprise. |
|||

## <a name="phase-5-mobile-device-management"></a>Phase 5 : Gestion des appareils mobiles

Microsoft 365 pour entreprise inclut Microsoft Intune pour la gestion des appareils mobiles. Avec Intune, vous pouvez gérer les appareils Windows, iOS, Android, macOS pour protéger l’accès aux ressources de votre organisation, y compris vos données. Intune utilise les comptes d’utilisateurs, de groupes et d’ordinateurs d’Azure AD.

Intune fournit deux types de gestion des appareils mobiles :

- La gestion des périphériques mobiles (MDM) s’avère lorsque les appareils sont inscrits dans Intune. Une fois inscrits, il s’agit de périphériques gérés qui peuvent recevoir les stratégies, règles et paramètres utilisés par votre organisation. Ces types d’appareils sont généralement détenus par votre organisation et émis pour vos employés.

- Les utilisateurs possédant leur propre appareil personnel peuvent ne pas vouloir inscrire leurs appareils ou être gérés par Intune avec vos stratégies et paramètres. Toutefois, vous devez encore protéger les ressources et les données de votre organisation. Pour ce scénario, vous pouvez protéger vos applications à l’aide de la gestion des applications mobiles (GAM).  

Les stratégies Intune peuvent renforcer la conformité des appareils et la protection des applications. Voici la liste des stratégies Intune à créer.

| Stratégies Intune | Groupes auxquels elle s’applique |
|:------|:-----|
| Stratégie de conformité des appareils pour Windows | BASE DE RÉFÉRENCE, SENSIBLE, HAUTEMENT RÉGLEMENTÉ |
| Stratégie de conformité des appareils pour iOS | SENSIBLE, HAUTEMENT RÉGLEMENTÉ |
| Stratégie de conformité des appareils pour macOS | SENSIBLE, HAUTEMENT RÉGLEMENTÉ |
| Stratégie de conformité des appareils pour Android et Android Entreprise | SENSIBLE, HAUTEMENT RÉGLEMENTÉ |
| Stratégie de protection des applications pour iOS | BASE DE RÉFÉRENCE, SENSIBLE, HAUTEMENT RÉGLEMENTÉ |
| Stratégie de protection des applications pour macOS | BASE DE RÉFÉRENCE, SENSIBLE, HAUTEMENT RÉGLEMENTÉ |
| Stratégie de conformité des applications pour Android et Android Entreprise | BASE DE RÉFÉRENCE, SENSIBLE, HAUTEMENT RÉGLEMENTÉ |
|||
    
Voir [Stratégies d’accès aux identités et aux appareils communes](identity-access-policies.md) pour les instructions.

### <a name="your-configuration-so-far"></a>Votre configuration jusqu’à présent

Voici une synthèse graphique de la phase Gestion des appareils mobiles. Les éléments nouveaux sont mis en surbrillance.

![Votre organisation après la phase Gestion des appareils mobiles](../media/deploy-foundation-infrastructure-non-enterprises/mdm-config.png)
 
Les éléments nouveaux et mis en surbrillance pour la gestion des appareils mobiles incluent :

|||
|:------:|:-----|
| ![Les appareils inscrits dans Intune](../media/deploy-foundation-infrastructure-non-enterprises/mdm-device.png) | Les appareils inscrits dans Intune, avec un ordinateur portable local exécutant Windows 10 Entreprise comme exemple. |
| ![Les stratégies Intune pour la conformité des appareils et la protection des applications](../media/deploy-foundation-infrastructure-non-enterprises/mdm-policies.png) | Les stratégies Intune pour la conformité des appareils et la protection des applications. |
|||

## <a name="phase-6-information-protection"></a>Phase 6 : Protection des informations

Microsoft 365 pour entreprise offre une foule de fonctionnalités de protection des informations qui vous permettent de traiter les données de manière différente en appliquant différents niveaux de gouvernance, de sécurité et de protection. 

Par exemple, une correspondance normale entre la plupart des employés et les documents sur lesquels ils travaillent a besoin d’un niveau de protection de base. Les dossiers financiers, les données client et votre propriété intellectuelle nécessitent un niveau de protection plus élevé.

La première étape d’une stratégie de protection des informations consiste à déterminer les niveaux de protection. De nombreuses organisations utilisent les niveaux suivants, qui sont déjà utilisés pour les stratégies d’accès conditionnel :

- Référence

  Les exemples incluent les communications d’entreprise normales (courrier électronique) et les fichiers des collaborateurs de l’administration, des ventes et du support technique.

- Sensible

  Les exemples incluent des informations financières et juridiques ainsi que les données de recherche et de développement de nouveaux produits.

- Hautement réglementé

  Les exemples incluent les informations d’identification personnelle des clients et partenaires, ainsi que les plans stratégiques ou la propriété intellectuelle de votre organisation.

Sur la base de ces niveaux de sécurité des données, l’étape suivante consiste à identifier et à implémenter :

- Types d’informations sensibles personnalisés

  Microsoft 365 fournit une large sélection de types d’informations sensibles, tels que les numéros de sécurité sociale et de carte bancaire. Si vous ne trouvez le type d’informations dont vous avez besoin dans la liste fournie, vous pouvez en créer un.

- Étiquettes de rétention

  Pour se conformer aux stratégies d’organisation et aux réglementations régionales, il se peut que vous deviez spécifier la durée de rétention de certains types de documents ou documents comportant des contenus spécifiques. Vous pouvez implémenter ceci pour le courrier électronique et les documents à l’aide d’étiquettes de rétention. Des étiquettes de rétention peuvent également être utilisées avec des stratégies de protection contre la perte de données qui peuvent limiter le partage de fichiers ou d’e-mails en dehors de votre organisation.

- Étiquettes de confidentialité

  Vous pouvez étiqueter les messages électroniques ou les documents avec une étiquette de confidentialité nommée de sorte que les niveaux de sécurité supplémentaires puissent être appliqués. Il s’agit par exemple de filigranes, de chiffrements et d’autorisations qui spécifient les personnes autorisées à accéder au courrier électronique ou au document et ce qu’ils sont autorisés à faire.

Pour plus d’informations, consultez [Types de classification de Microsoft 365](infoprotect-configure-classification.md#microsoft-365-classification-types).

Si vous utilisez des étiquettes de confidentialité avec des autorisations, vous serez peut-être amené à créer des groupes de sécurité supplémentaires pour définir qui est autorisé à faire quoi avec les e-mails et les documents auxquels l’étiquette de sensibilité est appliquée. 

Par exemple, vous devez créer une étiquette de confidentialité RECHERCHE pour protéger les e-mails et les documents de votre équipe de recherche. À vous de déterminer les éléments suivants :

- Les chercheurs doivent avoir la possibilité pour modifier les documents signalés par l’étiquette de confidentialité de la recherche.
- Les employés qui ne sont pas chercheurs doivent uniquement avoir la possibilité de voir les documents signalés par l’étiquette de confidentialité de la recherche. 

Cela signifie que vous devez créer et gérer deux groupes Microsoft 365 supplémentaires :

- RECHERCHE-TOUT
- RECHERCHE-LECTURE

Ces groupes et leurs autorisations font partie de la configuration de l’étiquette de confidentialité de la RECHERCHE.

Pour les étiquettes de confidentialité configurées avec les autorisations basées sur les groupes, vous devez gérer l’appartenance à ces groupes.

### <a name="your-configuration-so-far"></a>Votre configuration jusqu’à présent

Voici une synthèse graphique de la phase Protection des informations. Les éléments nouveaux sont mis en surbrillance.

![Votre organisation après la phase Protection des informations](../media/deploy-foundation-infrastructure-non-enterprises/info-protect-config.png)
 
Les éléments nouveaux et mis en surbrillance pour la protection des informations incluent :
 
|||
|:------:|:-----|
| ![Les étiquettes de confidentialité pour les trois niveaux de sécurité](../media/deploy-foundation-infrastructure-non-enterprises/info-protect-labels.png) | Les étiquettes de confidentialité pour les trois niveaux de sécurité que les utilisateurs peuvent appliquer aux documents. |
|||

Les étiquettes de rétention et les types d’informations personnalisées ne sont pas affichés.

## <a name="onboarding"></a>Intégration

Avec l’infrastructure Microsoft 365 pour entreprise en place, vous pouvez facilement intégrer vos employés.

### <a name="a-new-windows-10-enterprise-device"></a>Un nouvel appareil Windows 10 Entreprise

Avant d’attribuer à un employé un nouvel appareil Windows 10 Entreprise, procédez comme suit :

- Pour l’identité hybride

  Joignez l’appareil à votre AD DS, joignez l’appareil à votre client Azure AD, puis inscrivez l’appareil dans Intune.

- Pour une identité réservée au cloud

  Joignez l’appareil à votre locataire Azure AD.

### <a name="existing-employee-with-an-ad-ds-user-account"></a>Employé existant avec un compte d’utilisateur AD DS

Dans le cadre de l’intégration initiale de votre organisation lors de l’utilisation de l’identité hybride, ajoutez le compte d’utilisateur AD DS à ces groupes Azure AD :

- SOUS LICENCE
- Les groupes de sécurité AD DS ou Azure AD appropriés qui sont membres des groupes Azure AD de référence, sensibles et hautement réglementés
- Groupes d’étiquettes de confidentialité (selon vos besoins)

L’employé existant doit déjà être ajouté aux groupes de travail appropriés, département et AD DS régional.

Vous pouvez ajouter un compte d’utilisateur à plusieurs groupes Azure AD dans le centre d’administration Microsoft 365. Dans les propriétés du compte d’utilisateur, cliquez sur **Gérer les groupes > Ajouter des groupes**.

Si vous voulez utiliser PowerShell, consultez ce [classeur Excel téléchargeable](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/deploy-foundation-infrastructure-non-enterprises/Group-License-Mgmt-PowerShell.xlsx)qui génère les commandes PowerShell sur la base d’un compte d’utilisateur spécifié et des noms de groupes sélectionnés.

### <a name="new-employee-with-a-cloud-only-user-account"></a>Nouvel employé avec un compte réservé au cloud.

Dans le cadre de l’intégration initiale de votre organisation lors de l’utilisation de l’identité cloud uniquement, ajoutez le compte d’utilisateur à ces groupes :

- SOUS LICENCE
- Les groupes de sécurité Azure AD appropriés qui sont membres des groupes Azure AD de référence, sensibles et hautement réglementés
- Groupes de travail, départementaux et régionaux
- Groupes d’étiquettes de confidentialité (selon vos besoins)

### <a name="initial-sign-in-to-microsoft-365"></a>Première connexion à Microsoft 365

Lorsque les employés se connectent à Microsoft 365, donnez-leur l’instruction suivante :

1. Connectez-vous à leurs appareils à l’aide de leurs informations d’identification de compte d’utilisateur.
2. À l’aide d’un navigateur, connectez-vous au portail Office 365 surhttps://portal.office.com.
3. À partir de l’onglet**Accueil Office 365**, cliquez sur **installer Office** pour installer Microsoft 365 Apps pour entreprise sur leur appareil.

## <a name="end-results"></a>Résultats de fin

Voici les résultats de la configuration de l’infrastructure de base Microsoft 365 pour entreprise pour votre organisation non-entreprise.

### <a name="infrastructure-results"></a>Résultats de l’infrastructure

Une fois que vous avez créé et configuré votre infrastructure Microsoft 365 pour entreprise, vous devez disposer des éléments suivants :

- Une connexion Internet locale pour chacun de vos bureaux avec une bande passante suffisante fournie par un fournisseur d’accès Internet qui utilise un serveur DNS local.
- Pour l’identité hybride, Azure AD Connect se connecte sur un serveur qui synchronise votre domaine AD DS local avec votre client Azure AD.
- Ces groupes :
  - SOUS LICENCE
  - COND-ACCÈS-EXCLURE
  - Les groupes de sécurité AD DS ou Azure AD appropriés qui sont membres des groupes Azure AD de référence, sensibles et hautement réglementés 
  - Groupes de travail, départementaux et régionaux
  - Groupes d’étiquettes de confidentialité Microsoft 365 (selon vos besoins)
- Stratégies d’accès conditionnel de la connexion Azure AD qui utilisent les groupes Azure AD RÉFÉRENCE, SENSIBLE, HAUTEMENT RÉGLEMENTÉ et ACCÈS-COND-EXCLURE.
- Stratégies de conformité des applications Intune et des appareils.
- Types d’informations sensibles personnalisés pour la protection contre la perte de données (selon vos besoins).
- Étiquettes de rétention (selon vos besoins).
- Étiquettes de niveau de confidentialité (selon vos besoins).

Voici une synthèse graphique de l’infrastructure si votre organisation utilise une identité hybride, qui inclut votre domaine AD DS, un serveur Azure AD Connect et les utilisateurs et groupes AD DS synchronisés.

![Synthèse de l’infrastructure si votre organisation utilise une identité hybride](../media/deploy-foundation-infrastructure-non-enterprises/final-hybrid-config.png)
 
Voici une synthèse graphique de l’infrastructure si votre organisation utilise une identité réservée au cloud.
 
![Synthèse de l’infrastructure si votre organisation utilise une identité réservée au cloud](../media/deploy-foundation-infrastructure-non-enterprises/final-cloud-only-config.png)

### <a name="employee-results"></a>Résultats des employés

Après leur intégration, chaque employé doit avoir :

- Un chemin réseau performant et local à partir de leur appareil vers les services Cloud de Microsoft 365 dans leur région.
- Un compte utilisateur avec ces appartenances :
   - SOUS LICENCE
   - Les groupes de sécurité AD DS ou Azure AD appropriés qui sont aussi membres des groupes Azure AD RÉFÉRENCE, SENSIBLE et HAUTEMENT RÉGLEMENTÉ pour les stratégies d’accès conditionnel 
   - Les groupes de travail, départementaux et régionaux appropriés
   - Groupes d’étiquettes de confidentialité Microsoft 365 (selon vos besoins)
- Un appareil Windows 10 Entreprise qui :
   - Est joint au client Azure AD (Cloud uniquement) ou au client Azure AD et à votre domaine AD DS (hybride).
   - Se met automatiquement à jour avec les dernières améliorations apportées à la sécurité et aux améliorations apportées aux produits Windows 10 Entreprise.
   - Microsoft 365 Apps pour entreprise est installé, et se met automatiquement à jour avec les dernières améliorations des produits Office et les derniers renforcements de la sécurité.
   - Est inscrit dans Intune et soumis aux stratégies de conformité avec les appareils Intune et les stratégies de protection des applications.

## <a name="next-step"></a>Étape suivante

Déployez vos [charges de travail](deploy-workloads.md) pour tirer parti des fonctionnalités et de la configuration de votre infrastructure Microsoft 365 pour entreprise.
