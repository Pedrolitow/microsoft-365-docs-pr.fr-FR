---
title: Exiger l’accès conditionnel pour les personnes extérieures à votre organisation
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Découvrez comment demander à des personnes extérieures à votre organisation de passer des contrôles d’accès conditionnel tels que l’authentification multifacteur et les appareils conformes.
ms.openlocfilehash: 1beada2bb844804e380ed549c3d826169a21aa59
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67584979"
---
# <a name="require-conditional-access-for-people-outside-your-organization"></a>Exiger l’accès conditionnel pour les personnes extérieures à votre organisation

Vous pouvez exiger l’une des options d’accès conditionnel suivantes pour les personnes extérieures à votre organisation :

- Authentification multifacteur
- Appareils conformes
- Appareils joints à Azure AD hybride

Lorsque vous utilisez Azure AD B2B Direct Connect , par exemple avec des canaux partagés dans Teams, vous pouvez choisir d’approuver les paramètres d’accès conditionnel d’autres organisations pour ces options. Notez que les stratégies d’accès conditionnel sont utilisées uniquement pour l’accès à l’onglet Fichiers dans le canal partagé et le site SharePoint associé.

## <a name="planning-considerations-for-conditional-access"></a>Considérations relatives à la planification de l’accès conditionnel

L’authentification multifacteur peut être utilisée avec n’importe quel compte externe. Si votre organisation n’approuve pas l’authentification multifacteur d’autres organisations Azure AD, les utilisateurs de ces organisations devront effectuer une authentification multifacteur lors de l’accès aux ressources de votre organisation. Personnes avec des adresses e-mail tierces (non hébergées par Microsoft) sont toujours invités à effectuer une authentification multifacteur.

Les options **Exiger que l’appareil soit marqué conforme** et **exiger un appareil joint à Azure AD hybride** nécessitent des appareils gérés dans Azure AD. Si vous choisissez d’activer ces options, les personnes extérieures à votre organisation doivent utiliser des appareils gérés par votre organisation ou par une organisation de confiance. Personnes sans appareils gérés seront bloqués, notamment :

- Personnes avec des adresses e-mail tierces ou de consommateur
- Personnes d’organisations Microsoft 365 ou Azure AD qui ne gèrent pas d’appareils
- Personnes d’organisations Microsoft 365 ou Azure AD qui nécessitent des appareils gérés où votre organisation ne fait pas confiance à ses paramètres d’accès conditionnel.

Nous vous recommandons d’utiliser la prudence lorsque vous avez besoin d’appareils joints à Azure AD conformes ou hybrides, car cela bloquera de nombreux scénarios de collaboration externe. Assurez-vous que toutes vos organisations partenaires gèrent leurs appareils et que votre organisation approuve leurs paramètres.

## <a name="set-up-conditional-access-requirements-for-people-outside-your-organization"></a>Configurer les exigences d’accès conditionnel pour les personnes extérieures à votre organisation

Pour exiger un accès conditionnel pour les personnes extérieures à votre organisation, procédez comme suit :

1. [Choisissez les paramètres d’accès conditionnel à approuver auprès d’autres organisations](#choose-conditional-access-settings-to-trust-from-other-organizations).
1. [Configurez l’accès conditionnel pour les personnes extérieures à votre organisation](#set-up-conditional-access-for-people-outside-your-organization).

## <a name="choose-conditional-access-settings-to-trust-from-other-organizations"></a>Choisir les paramètres d’accès conditionnel à approuver auprès d’autres organisations

Vous pouvez choisir d’approuver les paramètres d’accès conditionnel de toutes les autres organisations Microsoft 365 et Azure AD ou uniquement de celles que vous spécifiez.

> [!NOTE]
> La prise en compte des modifications apportées aux paramètres d’accès entre locataires peut prendre deux heures.

### <a name="trust-conditional-access-settings-from-all-azure-active-directory-organizations"></a>Approuver les paramètres d’accès conditionnel de toutes les organisations Azure Active Directory

Si vous souhaitez approuver les paramètres d’accès conditionnel de toutes les organisations, suivez cette procédure.

Pour approuver les paramètres d’accès conditionnel de toutes les organisations Azure Active Directory
1. Connectez-vous à [Azure Active Directory](https://aad.portal.azure.com) à l’aide d’un compte Administrateur général ou Administrateur de la sécurité.
1. Sélectionnez **Identités externes**, puis sélectionnez **Paramètres d’accès entre locataires (prévisualisation).**
1. Sélectionnez l’onglet **Paramètres par défaut** .
1. Sous **Paramètres d’accès entrant**, **sélectionnez Modifier les valeurs par défaut entrantes**.
1. Sélectionnez l’onglet **Paramètres d’approbation** .
1. Choisissez les paramètres que vous souhaitez que vos stratégies d’accès conditionnel acceptent d’autres organisations.
1. Sélectionnez **Enregistrer** et fermez le panneau **Paramètres par défaut** .

### <a name="trust-conditional-access-settings-from-a-specific-organization"></a>Approuver les paramètres d’accès conditionnel d’une organisation spécifique

Si vous souhaitez approuver les paramètres d’accès conditionnel d’une organisation spécifique, suivez cette procédure.

Pour approuver les paramètres d’accès conditionnel d’une organisation spécifique
1. Connectez-vous à [Azure Active Directory](https://aad.portal.azure.com) à l’aide d’un compte Administrateur général ou Administrateur de la sécurité.
1. Sélectionnez **Identités externes**, puis sélectionnez **Paramètres d’accès entre locataires (prévisualisation).**
1. Sélectionnez les paramètres **d’accès entrant** pour l’organisation dans laquelle vous souhaitez approuver les paramètres d’accès conditionnel.
1. Sélectionnez l’onglet **Paramètres d’approbation** .
1. Sélectionnez l’option **Personnaliser les paramètres** .
1. Choisissez les paramètres que vous souhaitez que vos stratégies d’accès conditionnel acceptent d’autres organisations.
1. Sélectionnez **Enregistrer** et fermez le panneau **Paramètres par défaut** .

## <a name="set-up-conditional-access-for-people-outside-your-organization"></a>Configurer l’accès conditionnel pour les personnes extérieures à votre organisation

La configuration d’une stratégie d’accès conditionnel pour les personnes extérieures à votre organisation affecte les éléments suivants :

- Personnes à l’aide de comptes invités (utilisateurs Azure AD B2B Collaboration)
- Participants externes dans les canaux partagés Teams (utilisateurs de connexion directe Azure AD B2B)

> [!IMPORTANT]
> Sélectionnez uniquement **l’appareil Exiger d’être marqué conforme** ou **Exiger un appareil joint à Azure AD hybride** si tout le monde en dehors de votre organisation utilise un appareil géré par votre organisation ou par une organisation Microsoft 365 ou Azure AD approuvée.

Pour configurer l’accès conditionnel pour les personnes extérieures à votre organisation
1. Accédez à [Stratégies d’accès conditionnel Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
1. Dans le panneau **Accès conditionnel | Stratégies**, cliquez sur **Nouvelle stratégie**.
1. Dans le champ **Nom** , tapez un nom.
1. Sous **Affectations**, cliquez sur **Utilisateurs et groupes**.
1. Dans le panneau **Utilisateurs et groupes**, sélectionnez **Sélectionner Utilisateurs et groupes**, activez la case à cocher **Tous les invités et utilisateurs externes**.
1. Sous **Affectations**, cliquez sur **Actions ou applications Cloud**.
1. Dans le panneau **Actions ou applications Cloud**, sélectionnez **Toutes les applications Cloud** sous l’onglet **Inclure**.
1. Sous **Contrôles d’accès**, cliquez sur **Accorder**.
1. Dans le panneau **Accorder** , sélectionnez les options que vous souhaitez exiger pour les personnes extérieures à votre organisation, puis cliquez sur **Sélectionner**.
1. Dans le panneau **Nouveau**, sous **Activer la stratégie**, cliquez sur **Activer**, puis sur **Créer**.

## <a name="related-topics"></a>Voir aussi

[Tutoriel : Appliquer l’authentification multifacteur pour les invités B2B](/azure/active-directory/external-identities/b2b-tutorial-require-mfa)
