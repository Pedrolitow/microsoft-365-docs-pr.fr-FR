---
title: Exiger un accès conditionnel pour les personnes extérieures à votre organisation
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Découvrez comment exiger des personnes extérieures à votre organisation qu’elles passent des vérifications d’accès conditionnel telles que l’mf et les appareils conformes.
ms.openlocfilehash: 181ee77e6b8a8d491294c9a5d3f8ec9202c9f9c1
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63715997"
---
# <a name="require-conditional-access-for-people-outside-your-organization"></a>Exiger un accès conditionnel pour les personnes extérieures à votre organisation

Vous pouvez exiger l’une des options d’accès conditionnel suivantes pour les personnes extérieures à votre organisation :

- Authentification multifacteur
- Appareils conformes
- Appareils joints Azure AD hybrides

Lorsque vous utilisez Azure AD connexion directe B2B (par exemple, avec des canaux partagés dans Teams), vous pouvez choisir d’utiliser les paramètres d’accès conditionnel d’autres organisations pour ces options.

## <a name="planning-considerations-for-conditional-access"></a>Considérations sur la planification de l’accès conditionnel

L’authentification multifacteur peut être utilisée avec n’importe quel compte externe. Si votre organisation ne fait pas confiance à l’authentification multifacteur d’autres organisations Azure AD, les utilisateurs de ces organisations devront effectuer une authentification multifacteur lors de l’accès aux ressources de votre organisation. Les personnes ayant des adresses de messagerie tierces (non hébergées par Microsoft) seront toujours invités à authentification multifacteur.

Les options nécessitent **que l’appareil soit** marqué  comme conforme et Azure AD appareil joint nécessite des appareils gérés dans Azure AD. Si vous choisissez d’activer ces options, les personnes extérieures à votre organisation doivent utiliser des appareils gérés par votre organisation ou par une organisation de confiance. Les personnes sans appareils gérés seront bloquées, notamment :

- Personnes avec des adresses de messagerie tierces ou grand public
- Personnes de Microsoft 365 ou Azure AD organisations qui ne gèrent pas les appareils
- Les personnes Microsoft 365 ou Azure AD organisations qui nécessitent des appareils gérés où votre organisation n’a pas confiance dans leurs paramètres d’accès conditionnel.

Nous vous recommandons d’être prudent lorsque vous exigez des appareils Azure AD compatibles ou hybrides, car cela bloquera de nombreux scénarios de collaboration externe. Assurez-vous que toutes vos organisations partenaires gèrent leurs appareils et que votre organisation fait confiance à leurs paramètres.

## <a name="set-up-conditional-access-requirements-for-people-outside-your-organization"></a>Configurer les exigences d’accès conditionnel pour les personnes extérieures à votre organisation

Pour exiger un accès conditionnel pour les personnes extérieures à votre organisation, vous pouvez :

1. [Choisissez les paramètres d’accès conditionnel à faire confiance à d’autres organisations](#choose-conditional-access-settings-to-trust-from-other-organizations).
1. [Configurer l’accès conditionnel pour les personnes extérieures à votre organisation](#set-up-conditional-access-for-people-outside-your-organization).

## <a name="choose-conditional-access-settings-to-trust-from-other-organizations"></a>Choisir les paramètres d’accès conditionnel à faire confiance à d’autres organisations

Vous pouvez choisir d’approbation des paramètres d’accès conditionnel de toutes les autres organisations Microsoft 365 et Azure AD ou uniquement de ceux que vous spécifiez.

> [!NOTE]
> L’application des modifications apportées aux paramètres d’accès entre locataires peut prendre deux heures.

### <a name="trust-conditional-access-settings-from-all-azure-active-directory-organizations"></a>Approbation des paramètres d’accès conditionnel de toutes Azure Active Directory organisations

Si vous souhaitez faire confiance aux paramètres d’accès conditionnel de toutes les organisations, suivez cette procédure.

Pour faire confiance aux paramètres d’accès conditionnel de toutes Azure Active Directory organisations
1. Connectez-vous [à Azure Active Directory](https://aad.portal.azure.com) à l’aide d’un compte d’administrateur général ou d’administrateur de sécurité.
1. **Sélectionnez Identités externes**, puis sélectionnez **Paramètres d’accès entre locataires (prévisualisation).**
1. Sélectionnez **l’onglet Paramètres par** défaut.
1. Sous **Paramètres d’accès entrant**, **sélectionnez Modifier les valeurs par défaut du trafic entrant**.
1. Sélectionnez **l’onglet Paramètres d’confiance** .
1. Choisissez les paramètres que vos stratégies d’accès conditionnel doivent accepter d’autres organisations.
1. **Sélectionnez Enregistrer** et fermez **le lame Paramètres par** défaut.

### <a name="trust-conditional-access-settings-from-a-specific-organization"></a>Approbation des paramètres d’accès conditionnel d’une organisation spécifique

Si vous souhaitez faire confiance aux paramètres d’accès conditionnel d’une organisation spécifique, suivez cette procédure.

Pour faire confiance aux paramètres d’accès conditionnel d’une organisation spécifique
1. Connectez-vous [à Azure Active Directory](https://aad.portal.azure.com) à l’aide d’un compte d’administrateur général ou d’administrateur de sécurité.
1. **Sélectionnez Identités externes**, puis sélectionnez **Paramètres d’accès entre locataires (prévisualisation).**
1. Sélectionnez **les paramètres d’accès** entrant pour l’organisation dans laquelle vous souhaitez faire confiance aux paramètres d’accès conditionnel.
1. Sélectionnez **l’onglet Paramètres d’confiance** .
1. Sélectionnez **l’option Personnaliser les paramètres** .
1. Choisissez les paramètres que vos stratégies d’accès conditionnel doivent accepter d’autres organisations.
1. **Sélectionnez Enregistrer** et fermez **le lame Paramètres par** défaut.

## <a name="set-up-conditional-access-for-people-outside-your-organization"></a>Configurer l’accès conditionnel pour les personnes extérieures à votre organisation

La configuration d’une stratégie d’accès conditionnel pour les personnes extérieures à votre organisation a une incidence sur les suivantes :

- Personnes utilisant des comptes invités (Azure AD utilisateurs de collaboration B2B)
- Participants externes à Teams canaux partagés (Azure AD utilisateurs de connexion directe B2B)

> [!IMPORTANT]
> Sélectionnez uniquement  l’appareil Exiger la conformité ou Exiger l’appareil joint à un **Azure AD** hybride si toutes les personnes extérieures à votre organisation utilisent un appareil géré par votre organisation ou par une organisation Microsoft 365 ou Azure AD approuvé.

Pour configurer l’accès conditionnel pour les personnes extérieures à votre organisation
1. Accédez à [Stratégies d’accès conditionnel Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
1. Dans le panneau **Accès conditionnel | Stratégies**, cliquez sur **Nouvelle stratégie**.
1. Dans le champ **Nom** , tapez un nom.
1. Sous **Affectations**, cliquez sur **Utilisateurs et groupes**.
1. Dans le panneau **Utilisateurs et groupes**, sélectionnez **Sélectionner Utilisateurs et groupes**, activez la case à cocher **Tous les invités et utilisateurs externes**.
1. Sous **Affectations**, cliquez sur **Actions ou applications Cloud**.
1. Dans le panneau **Actions ou applications Cloud**, sélectionnez **Toutes les applications Cloud** sous l’onglet **Inclure**.
1. Sous **Contrôles d’accès**, cliquez sur **Accorder**.
1. Dans le **bouton Accorder** , sélectionnez les options dont vous souhaitez avoir besoin pour les personnes extérieures à votre organisation, puis cliquez sur **Sélectionner**.
1. Dans le panneau **Nouveau**, sous **Activer la stratégie**, cliquez sur **Activer**, puis sur **Créer**.

## <a name="related-topics"></a>Sujets associés

[Didacticiel : Appliquer l’authentification multifacteur pour les invités B2B](/azure/active-directory/external-identities/b2b-tutorial-require-mfa)
