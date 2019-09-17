---
title: 'Phase 2 : Identité'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/06/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Les étapes de déploiement de l’infrastructure d’identités pour Microsoft 365 Entreprise.
ms.openlocfilehash: 07f95a249912826b80e0654cac4063b3d5763267
ms.sourcegitcommit: 91ff1d4339f0f043c2b43997d87d84677c79e279
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "36981948"
---
# <a name="phase-2-identity"></a>Phase 2 : Identité

![](./media/deploy-foundation-infrastructure/identity_icon.png)

Dans Microsoft 365 Entreprise, une infrastructure d’identités bien planifiée et exécutée ouvre la voie à une sécurité plus forte et à un accès à vos charges de travail de productivité et à leurs données uniquement par des utilisateurs et appareils authentifiés.

Regardez cette vidéo pour obtenir une vue d’ensemble des modèles d’identité et de l’authentification pour Microsoft 365 Entreprise.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

>[!Note]
>Si vous avez déjà déployé une infrastructure d’identités, consultez les [critères de sortie d’identité](identity-exit-criteria.md) pour vous assurer que vous répondez aux conditions requises et facultatives pour Microsoft 365 Entreprise.
>

Pour plus d’informations sur les fonctionnalités d’identité de chaque offre Microsoft 365 Entreprise, le rôle Azure Active Directory (Azure AD), les composants locaux et cloud, ainsi que les configurations d’authentification les plus courantes, consultez l’[affiche Infrastructure d’identités](media/identity-infrastructure/M365E-ID-Infra.pdf).

[![Affiche Infrastructure d’identités](./media/identity-infrastructure/m365e-identity-arch-poster.png)](media/identity-infrastructure/M365E-ID-Infra.pdf)

Cette affiche en double page permet de bien comprendre les concepts et configurations d’identités pour Microsoft 365 Entreprise.

Vous pouvez également [télécharger cette affiche](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/enterprise/media/identity-infrastructure/M365E-ID-Infra.pdf) et l’imprimer au format lettre, légal ou tabloïd (11 x 17).

## <a name="plan-and-deploy-your-microsoft-365-enterprise-identity-infrastructure"></a>Planifier et déployer votre infrastructure d’identités de Microsoft 365 Entreprise 

Procédez comme suit pour planifier et déployer votre nouvelle infrastructure d’identités dans le cloud. Vous pouvez également utiliser ces étapes pour adapter votre infrastructure d’identités locale ou hybride et l’utiliser avec Microsoft 365 Entreprise. 

|||
|:-------|:-----|
|![](./media/stepnumbers/Step1.png)| [Planifier les utilisateurs et les groupes](identity-plan-users-groups.md) |
|![](./media/stepnumbers/Step2.png)| [Sécuriser vos identités privilégiées](identity-designate-protect-admin-accounts.md) |
|![](./media/stepnumbers/Step3.png)| [Configurer une identité hybride](identity-azure-ad-connect.md) |
|![](./media/stepnumbers/Step4.png)| [Configurer l’authentification utilisateur sécurisée](identity-multi-factor-authentication.md) |
|![](./media/stepnumbers/Step5.png)| [Simplifier l’accès pour les utilisateurs](identity-password-reset.md) |
|![](./media/stepnumbers/Step6.png)| [Utiliser des groupes pour faciliter la gestion](identity-self-service-group-management.md) |
|![](./media/stepnumbers/Step7.png)| [Configurer la gouvernance des identités](identity-governance.md) |

Lorsque vous avez terminé ces étapes, accédez aux [critères de sortie](identity-exit-criteria.md) de cette phase pour vous assurer que vous répondez aux conditions requises et facultatives pour l’identité Microsoft 365 Entreprise.

## <a name="identity-and-device-access-recommendations"></a>Recommandations en matière d’identité et d’accès aux appareils

Microsoft fournit un ensemble de recommandations en matière d’[identité et d’accès aux appareils](microsoft-365-policies-configurations.md) afin de garantir un personnel sécurisé et productif. Pour l’identité, utilisez les recommandations et les paramètres des articles suivants, ainsi que les étapes décrites dans cette phase :

- [Conditions préalables](identity-access-prerequisites.md)
- [Stratégies communes pour les identités et l’accès aux appareils](identity-access-policies.md)

## <a name="how-microsoft-does-microsoft-365-enterprise"></a>Comment Microsoft gère-t-il Microsoft 365 Entreprise

Découvrez comment les experts informatiques de [Microsoft gèrent les identités et la sécurisation des accès](https://www.microsoft.com/fr-FR/itshowcase/deploying-and-managing-microsoft-365#primaryR5).

## <a name="how-contoso-did-microsoft-365-enterprise"></a>Comment Contoso est-elle passée à Microsoft 365 Entreprise ?

Découvrez comment Contoso Corporation, une entreprise multinationale fictive mais représentative, [a déployé une infrastructure d’identité hybride](contoso-identity.md) pour les services cloud Microsoft 365.

![](./media/contoso-overview/contoso-icon.png)


## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step1.png)| [Planifiez les utilisateurs et les groupes](identity-plan-users-groups.md) |
