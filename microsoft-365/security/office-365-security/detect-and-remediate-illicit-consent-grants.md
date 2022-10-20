---
title: Détecter et corriger les octrois de consentement illicites
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection:
- o365_security_incident_response
- m365-security
ms.date: 07/28/2022
ms.localizationpriority: medium
search.appverid:
- MET150
description: Découvrez comment reconnaître et corriger l’attaque par octroi de consentement illicite dans Microsoft 365.
ms.custom:
- seo-marvel-apr2020
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 7a6e5b02593247cc3ee5ab0111fb496d58e60f9b
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68642324"
---
# <a name="detect-and-remediate-illicit-consent-grants"></a>Détecter et corriger les octrois de consentement illicites

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Résumé**  Découvrez comment reconnaître et corriger l’attaque par octroi de consentement illicite dans Microsoft 365.

## <a name="what-is-the-illicit-consent-grant-attack-in-microsoft-365"></a>Quelle est l’attaque par octroi de consentement illicite dans Microsoft 365 ?

Dans une attaque d’octroi de consentement illicite, l’attaquant crée une application inscrite sur Azure qui demande l’accès à des données telles que des informations de contact, des e-mails ou des documents. L’attaquant trompe ensuite un utilisateur final en lui accordant le consentement de cette application pour accéder à ses données par le biais d’une attaque par hameçonnage ou en injectant du code illicite dans un site web approuvé. Une fois que l’application illicite a obtenu le consentement, elle dispose d’un accès au niveau du compte aux données sans avoir besoin d’un compte professionnel. Les étapes de correction normales, telles que la réinitialisation des mots de passe pour les comptes violés ou l’exigence de l’authentification multifacteur (MFA) sur les comptes, ne sont pas efficaces contre ce type d’attaque, car il s’agit d’applications tierces et externes à l’organisation.

Ces attaques tirent parti d’un modèle d’interaction qui suppose que l’entité qui appelle les informations est l’automatisation et non un humain.

> [!IMPORTANT]
> Pensez-vous que vous rencontrez des problèmes avec les octrois de consentement illicites d’une application, en ce moment ? Microsoft Defender for Cloud Apps dispose d’outils pour détecter, examiner et corriger vos applications OAuth. Cet article de Defender pour Cloud Apps propose un didacticiel qui explique comment [examiner les applications OAuth à risque](/cloud-app-security/investigate-risky-oauth). Vous pouvez également définir des [stratégies d’application OAuth](/cloud-app-security/app-permission-policy) pour examiner les autorisations demandées par l’application, que les utilisateurs autorisent ces applications, et approuver ou interdire largement ces demandes d’autorisations.

## <a name="what-does-an-illicit-consent-grant-attack-look-like-in-microsoft-365"></a>À quoi ressemble une attaque par octroi de consentement illicite dans Microsoft 365 ?

Vous devez effectuer une recherche dans le **journal d’audit** pour rechercher des signes, également appelés Indicateurs de compromission (IOC) de cette attaque. Pour les organisations avec de nombreuses applications inscrites sur Azure et une grande base d’utilisateurs, la meilleure pratique consiste à examiner les octrois de consentement de vos organisations sur une base hebdomadaire.

### <a name="steps-for-finding-signs-of-this-attack"></a>Étapes de recherche des signes de cette attaque

1. Ouvrez le portail Microsoft 365 Defender, <https://security.microsoft.com> puis sélectionnez **Audit**. Ou, pour accéder directement à la page **Audit**, utilisez <https://security.microsoft.com/auditlogsearch>.

2. Dans la page **Audit** , vérifiez que l’onglet **Recherche** est sélectionné, puis configurez les paramètres suivants :
   - **Plage de dates et d’heures**
   - **Activités** : vérifiez que **l’option Afficher les résultats de toutes les activités** est sélectionnée.

   Lorsque vous avez terminé, cliquez sur **Rechercher**.

3. Cliquez sur la colonne **Activité** pour trier les résultats et rechercher **le consentement à l’application**.

4. Sélectionnez une entrée dans la liste pour afficher les détails de l’activité. Vérifiez si IsAdminConsent a la valeur True.

> [!NOTE]
>
> L’affichage de l’entrée de journal d’audit correspondante dans les résultats de recherche après un événement peut prendre de 30 minutes à 24 heures.
>
> La durée pendant laquelle un enregistrement d’audit est conservé et pouvant faire l’objet d’une recherche dans le journal d’audit dépend de votre abonnement Microsoft 365, et plus précisément du type de la licence affectée à un utilisateur spécifique. Pour plus d’informations, consultez le [journal d’audit](../../compliance/search-the-audit-log-in-security-and-compliance.md).
>
> Si cette valeur est vraie, elle indique qu’une personne disposant d’un accès Administrateur général a peut-être accordé un accès étendu aux données. Si cela est inattendu, prenez des mesures pour [confirmer une attaque](#how-to-confirm-an-attack).

## <a name="how-to-confirm-an-attack"></a>Comment confirmer une attaque

Si vous avez une ou plusieurs instances des E/S répertoriées ci-dessus, vous devez effectuer une investigation plus approfondie pour confirmer positivement que l’attaque s’est produite. Vous pouvez utiliser l’une de ces trois méthodes pour confirmer l’attaque :

- Stockez les applications et leurs autorisations à l’aide du portail Azure Active Directory. Cette méthode est complète, mais vous ne pouvez vérifier qu’un seul utilisateur à la fois, ce qui peut prendre beaucoup de temps si vous avez de nombreux utilisateurs à vérifier.
- Stockez les applications et leurs autorisations à l’aide de PowerShell. Il s’agit de la méthode la plus rapide et la plus complète, avec le moins de surcharge.
- Demander à vos utilisateurs de vérifier individuellement leurs applications et autorisations et de signaler les résultats aux administrateurs pour les corriger.

## <a name="inventory-apps-with-access-in-your-organization"></a>Inventorier les applications avec accès dans votre organisation

Vous pouvez le faire pour vos utilisateurs avec le portail Azure Active Directory ou PowerShell ou demander à vos utilisateurs d’énumérer individuellement leur accès à l’application.

### <a name="steps-for-using-the-azure-active-directory-portal"></a>Étapes d’utilisation du portail Azure Active Directory

Vous pouvez rechercher les applications auxquelles un utilisateur individuel a accordé des autorisations à l’aide du portail Azure Active Directory à l’adresse <https://portal.azure.com>.

1. Connectez-vous au Portail Azure avec des droits d’administration.
2. Sélectionnez le panneau Azure Active Directory.
3. Sélectionner **Utilisateurs**.
4. Sélectionnez l’utilisateur que vous souhaitez examiner.
5. Sélectionnez **Applications**.

Cela vous montre les applications qui sont affectées à l’utilisateur et les autorisations dont disposent les applications.

### <a name="steps-for-having-your-users-enumerate-their-application-access"></a>Étapes permettant à vos utilisateurs d’énumérer leur accès à l’application

Que vos utilisateurs y accèdent <https://myapps.microsoft.com> et examinent leur propre accès à l’application. Ils doivent être en mesure de voir toutes les applications avec accès, d’afficher des détails à leur sujet (y compris l’étendue de l’accès) et de révoquer des privilèges pour des applications suspectes ou illicites.

### <a name="steps-for-doing-this-with-powershell"></a>Étapes à suivre pour effectuer cette opération avec PowerShell

Le moyen le plus simple de vérifier l’attaque par octroi de consentement illicite consiste à exécuter [Get-AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09), qui vide toutes les octrois de consentement OAuth et les applications OAuth pour tous les utilisateurs de votre location dans un seul fichier .csv.

#### <a name="pre-requisites"></a>Conditions préalables

- Bibliothèque PowerShell Azure AD installée.
- Administrateur général droits sur le locataire sur lequel le script sera exécuté.
- Administrateur local sur l’ordinateur à partir duquel les scripts seront exécutés.

> [!IMPORTANT]
> Nous vous ***recommandons vivement*** d’exiger une authentification multifacteur sur votre compte d’administration. Ce script prend en charge l’authentification MFA.

1. Connectez-vous à l’ordinateur à partir de lequel vous allez exécuter le script avec des droits d’administrateur local.

2. Téléchargez ou copiez le script [Get-AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09) à partir de GitHub dans un dossier à partir duquel vous allez exécuter le script. Il s’agit du même dossier que celui dans lequel le fichier « permissions.csv » de sortie sera écrit.

3. Ouvrez une session PowerShell en tant qu’administrateur et ouvrez le dossier dans lequel vous avez enregistré le script.

4. Connectez-vous à votre répertoire à l’aide de l’applet [de commande Connect-AzureAD](/powershell/module/azuread/connect-azuread) .

5. Exécutez cette commande PowerShell :

   ```powershell
   .\Get-AzureADPSPermissions.ps1 | Export-csv -Path "Permissions.csv" -NoTypeInformation
   ```

Le script produit un fichier nommé Permissions.csv. Suivez ces étapes pour rechercher les octrois d’autorisations d’application illicites :

1. Dans la colonne ConsentType (colonne G), recherchez la valeur « AllPrinciples ». L’autorisation AllPrincipals permet à l’application cliente d’accéder au contenu de tout le monde dans la location. Les applications Microsoft 365 natives ont besoin de cette autorisation pour fonctionner correctement. Toutes les applications non-Microsoft disposant de cette autorisation doivent être examinées attentivement.

2. Dans la colonne Autorisation (colonne F), passez en revue les autorisations dont dispose chaque application déléguée pour le contenu. Recherchez l’autorisation « Lecture » et « Écriture » ou « Tout », puis examinez-les attentivement, car elles peuvent ne pas être appropriées.

3. Passez en revue les utilisateurs spécifiques auxquels des consentements ont été accordés. Si des utilisateurs à haut profil ou à fort impact ont des consentements inappropriés accordés, vous devez examiner plus en détail.

4. Dans la colonne ClientDisplayName (colonne C), recherchez les applications qui semblent suspectes. Les applications avec des noms mal orthographiés, des noms super fades ou des noms de pirates doivent être examinées avec soin.

## <a name="determine-the-scope-of-the-attack"></a>Déterminer l’étendue de l’attaque

Une fois que vous avez terminé l’inventaire de l’accès aux applications, passez en revue le **journal d’audit** pour déterminer l’étendue complète de la violation. Recherchez les utilisateurs concernés, les délais d’accès de l’application illicite à votre organisation et les autorisations de l’application. Vous pouvez effectuer une recherche dans le **journal d’audit** dans le [portail Microsoft 365 Defender](../../compliance/search-the-audit-log-in-security-and-compliance.md).

> [!IMPORTANT]
> [L’audit des boîtes aux lettres](../../compliance/enable-mailbox-auditing.md) et [l’audit des activités pour les administrateurs et les utilisateurs](../../compliance/turn-audit-log-search-on-or-off.md) doivent avoir été activés avant l’attaque pour que vous obteniez ces informations.

## <a name="how-to-stop-and-remediate-an-illicit-consent-grant-attack"></a>Comment arrêter et corriger une attaque d’octroi de consentement illicite

Une fois que vous avez identifié une application avec des autorisations illicites, vous avez plusieurs façons de supprimer cet accès.

- Vous pouvez révoquer l’autorisation de l’application dans le portail Azure Active Directory en :
  1. Accédez à l’utilisateur affecté dans le panneau **Utilisateur Azure Active Directory** .
  2. Sélectionnez **Applications**.
  3. Sélectionnez l’application illicite.
  4. Cliquez sur **Supprimer** dans l’exploration.

- Vous pouvez révoquer l’octroi de consentement OAuth avec PowerShell en suivant les étapes décrites dans [Remove-AzureADOAuth2PermissionGrant](/powershell/module/azuread/Remove-AzureADOAuth2PermissionGrant).

- Vous pouvez révoquer l’attribution de rôle d’application de service avec PowerShell en suivant les [étapes décrites dans Remove-AzureADServiceAppRoleAssignment](/powershell/module/azuread/Remove-AzureADServiceAppRoleAssignment).

- Vous pouvez également désactiver complètement la connexion pour le compte affecté, ce qui désactivera à son tour l’accès des applications aux données de ce compte. Ce n’est pas idéal pour la productivité de l’utilisateur final, bien sûr, mais si vous travaillez à limiter rapidement l’impact, il peut s’agir d’une correction viable à court terme.

- Vous pouvez désactiver les applications intégrées pour votre location. Il s’agit d’une étape radicale qui désactive la possibilité pour les utilisateurs finaux d’accorder leur consentement à l’échelle du locataire. Cela empêche vos utilisateurs d’accorder par inadvertance l’accès à une application malveillante. Cela n’est pas fortement recommandé, car cela nuit gravement à la capacité de vos utilisateurs à être productifs avec des applications tierces. Pour ce faire, suivez les étapes de [l’activation ou de la désactivation des applications intégrées](../../admin/misc/user-consent.md).

## <a name="see-also"></a>Voir aussi

- [L’application inattendue dans ma liste d’applications](/azure/active-directory/application-access-unexpected-application) guide les administrateurs dans différentes actions qu’ils peuvent souhaiter entreprendre après avoir réalisé qu’il existe des applications inattendues ayant accès aux données.
- [L’intégration d’applications à Azure Active Directory](/azure/active-directory/active-directory-apps-permissions-consent) est une vue d’ensemble générale du consentement et des autorisations.
- [Les problèmes de développement de mon application](/azure/active-directory/active-directory-application-dev-development-content-map) fournissent des liens vers différents articles relatifs au consentement.
- [Les objets d’application et de principal de service dans Azure Active Directory (Azure AD)](/azure/active-directory/develop/active-directory-application-objects) fournissent une vue d’ensemble des objets de principal d’application et de service qui sont au cœur du modèle d’application.
- [Gérer l’accès aux applications](/azure/active-directory/active-directory-managing-access-to-apps) est une vue d’ensemble des fonctionnalités dont les administrateurs ont besoin pour gérer l’accès utilisateur aux applications.
