---
title: Étape 3. Identité de votre Microsoft 365 pour les locataires d’entreprise
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Déployez le modèle d’identité approprié pour vos locataires Microsoft 365 et appliquez des connexions utilisateur fortes.
ms.openlocfilehash: b31bbc089d6c6824eacc9cce00f71a877052ec72
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67986419"
---
# <a name="step-3-identity-for-your-microsoft-365-for-enterprise-tenants"></a>Étape 3. Identité de votre Microsoft 365 pour les locataires d’entreprise

Votre locataire Microsoft 365 inclut un locataire Azure Active Directory (Azure AD) pour gérer les identités et l’authentification pour les connexions. Il est essentiel de configurer correctement votre infrastructure d’identité pour gérer l’accès et les autorisations des utilisateurs Microsoft 365 pour votre organisation.

## <a name="cloud-only-vs-hybrid"></a>Cloud uniquement et hybride

Voici les deux types de modèles d’identité et leurs meilleurs ajustement et avantages.


| Modèle | Description | Comment Microsoft 365 authentifie les informations d’identification de l’utilisateur | Idéal pour | Plus grand avantage |
|:-------|:-----|:-----|:-----|:-----|
| Cloud uniquement | Le compte d’utilisateur existe uniquement dans le locataire Azure AD pour votre locataire Microsoft 365. | Le locataire Azure AD pour votre locataire Microsoft 365 effectue l’authentification avec le compte d’identité cloud. | Organisations qui n’ont pas ou ont besoin d’un Active Directory local. | Simple à utiliser. Aucun serveur ou outil d’annuaire supplémentaire n’est requis. |
| Hybride |  Le compte d’utilisateur existe dans votre Active Directory local Domain Services (AD DS) et une copie se trouve également dans le locataire Azure AD pour votre locataire Microsoft 365. Azure AD Connect s’exécute sur un serveur local pour synchroniser les modifications AD DS avec votre locataire Azure AD. Le compte d’utilisateur dans Azure AD peut également inclure une version hachée du mot de passe du compte d’utilisateur AD DS déjà haché. | Le locataire Azure AD de votre locataire Microsoft 365 gère le processus d’authentification ou redirige l’utilisateur vers un autre fournisseur d’identité. | Organisations utilisant AD DS ou un autre fournisseur d’identité. | Les utilisateurs peuvent utiliser les mêmes informations d’identification lors de l’accès aux ressources locales ou cloud. |
||||||

Voici les composants de base de l’identité cloud uniquement.

![Composants de base de l’identité cloud uniquement.](../media/about-microsoft-365-identity/cloud-only-identity.png)

Dans cette illustration, les utilisateurs locaux et distants se connectent avec des comptes dans le locataire Azure AD de leur locataire Microsoft 365.

Voici les composants de base de l’identité hybride.

![Composants de base de l’identité hybride.](../media/about-microsoft-365-identity/hybrid-identity.png)

Dans cette illustration, les utilisateurs locaux et distants se connectent à leur locataire Microsoft 365 avec des comptes dans le locataire Azure AD qui ont été copiés à partir de leur service AD DS local.

## <a name="synchronizing-your-on-premises-ad-ds"></a>Synchronisation de votre AD DS local

En fonction des besoins de votre entreprise et des exigences techniques, le modèle d’identité hybride et la synchronisation d’annuaires sont le choix le plus courant pour les clients d’entreprise qui adoptent Microsoft 365. La synchronisation d’annuaires vous permet de gérer les identités dans votre service AD DS et toutes les mises à jour des comptes d’utilisateur, des groupes et des contacts sont synchronisées avec le locataire Azure AD de votre locataire Microsoft 365.

> [!NOTE]
> Lorsque les comptes d’utilisateur AD DS sont synchronisés pour la première fois, ils ne reçoivent pas automatiquement de licence Microsoft 365 et ne peuvent pas accéder aux services Microsoft 365, tels que les e-mails. Vous devez d'abord leur attribuer un emplacement d'utilisation. Ensuite, attribuez une licence à ces comptes d'utilisateurs, soit individuellement, soit dynamiquement via l'appartenance à un groupe.

Voici les deux types d’authentification lors de l’utilisation du modèle d’identité hybride.

| Type d’authentification | Description |
|:-------|:-----|
| Authentification managée | Azure AD gère le processus d'authentification en utilisant une version hachée du mot de passe stockée localement ou envoie les informations d'identification à un agent logiciel local pour qu'elles soient authentifiées par l'AD DS local. <br> <br>  Il existe deux types d’authentification managée : la synchronisation de hachage de mot de passe (PHS) et l’authentification directe (PTA). Avec PHS, Azure AD effectue l’authentification elle-même. Avec PTA, Azure AD dispose d’AD DS pour effectuer l’authentification. |
| Authentification fédérée | Azure AD redirige l'ordinateur client demandant l'authentification vers un autre fournisseur d'identité. |
|  |  |

Consultez [le choix de la méthode d’authentification appropriée](/azure/active-directory/hybrid/choose-ad-authn) pour en savoir plus.

## <a name="enforcing-strong-sign-ins"></a>Application de connexions fortes

Pour renforcer la sécurité des connexions utilisateur, utilisez les fonctionnalités et fonctionnalités du tableau suivant.

| Fonctionnalité | Description | Plus d’informations | Conditions d'octroi de licence |
|:-------|:-----|:-----|:-----|:-----|
| Windows Hello Entreprise | Remplace les mots de passe par une authentification forte à deux facteurs lors de la connexion sur un appareil Windows. Les deux facteurs sont un nouveau type d’informations d’identification d’utilisateur qui est lié à un appareil et à un code biométrique ou PIN. | [Vue d’ensemble de Windows Hello Entreprise](/windows/security/identity-protection/hello-for-business/hello-overview) | Microsoft 365 E3 ou E5 |
| Protection par mot de passe Azure AD. | Détecte et bloque les mots de passe faibles connus et leurs variantes, et peut également bloquer d’autres termes faibles spécifiques à votre organisation. | [Configurer la protection par mot de passe Azure AD](/azure/active-directory/authentication/concept-password-ban-bad) | Microsoft 365 E3 ou E5 |
| Utilisez l’authentification multifacteur (MFA) | L’authentification multifacteur nécessite que les connexions utilisateur soient soumises à une autre vérification au-delà du mot de passe du compte d’utilisateur, comme la vérification avec une application smartphone ou un SMS envoyé à un smartphone. Consultez [cette vidéo](https://support.microsoft.com/office/set-up-multi-factor-authentication-in-microsoft-365-business-a32541df-079c-420d-9395-9d59354f7225) pour obtenir des instructions sur la façon dont les utilisateurs configurent l’authentification multifacteur. | [MFA pour Microsoft 365 pour entreprise](../enterprise/microsoft-365-secure-sign-in.md#mfa) | Microsoft 365 E3 ou E5 |
| Configurations des identités et de l’accès aux appareils | Paramètres et stratégies qui se composent de fonctionnalités prérequises recommandées et de leurs paramètres combinés à des stratégies d’accès conditionnel, Intune et Azure AD Identity Protection qui déterminent si une demande d’accès donnée doit être accordée et dans quelles conditions.  | [Configurations des identités et de l’accès aux appareils](../security/office-365-security/microsoft-365-policies-configurations.md) | Microsoft 365 E3 ou E5 |
| Azure AD Identity Protection | Protégez-vous contre la compromission des informations d’identification, où un attaquant détermine le nom de compte et le mot de passe d’un utilisateur pour accéder aux données et services cloud d’une organisation. | [Azure AD Identity Protection](/azure/active-directory/active-directory-identityprotection) | Microsoft 365 E5 ou Microsoft 365 E3 avec le module complémentaire Identity & Threat Protection |
|  |  |  |



## <a name="results-of-step-3"></a>Résultats de l’étape 3

Pour l’identité de votre locataire Microsoft 365, vous avez déterminé :

- Modèle d’identité à utiliser.
- Comment appliquer un accès utilisateur et appareil fort.

Voici un exemple de locataire avec les nouveaux éléments d’identité hybride mis en évidence.

![Exemple d’identité hybride pour un locataire.](../media/tenant-management-overview/tenant-management-tenant-build-step3.png)

Dans cette illustration, le locataire a :

- Forêt AD DS synchronisée avec le locataire Azure AD à l’aide d’un serveur de synchronisation d’annuaires et d’Azure AD Connect.
- Copie des comptes d’utilisateur AD DS et d’autres objets de la forêt AD DS.
- Ensemble de stratégies d’accès conditionnel pour appliquer des connexions et un accès utilisateur sécurisés en fonction du compte d’utilisateur.

## <a name="ongoing-maintenance-for-identity"></a>Maintenance en cours pour l’identité

De façon continue, vous devrez peut-être :

- Ajoutez ou modifiez des comptes et des groupes d’utilisateurs. Pour l’identité cloud uniquement, vous gérez vos utilisateurs et groupes basés sur le cloud avec des outils Azure AD tels que le Centre d'administration Microsoft 365 ou PowerShell. Pour l’identité hybride, vous gérez vos utilisateurs et groupes locaux avec les outils AD DS.
- Ajoutez ou modifiez votre configuration d’accès à l’identité et à l’appareil pour appliquer les exigences de sécurité de connexion.

## <a name="next-step"></a>Étape suivante

[![Étape 4. Migrez vos serveurs et données Office locaux.](../media/tenant-management-overview/tenant-management-step-grid-migration.png)](tenant-management-migration.md)

Poursuivez la [migration](tenant-management-migration.md) pour migrer vos serveurs Office locaux et leurs données vers Microsoft 365.