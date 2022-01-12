---
title: Détecter et corriger les octrois de consentement illicites
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MET150
description: Découvrez comment reconnaître et corriger les attaques par consentement illicite dans Microsoft 365.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: db401231a2db0bddf1115cbdf14ae14cc9897f57
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61935449"
---
# <a name="detect-and-remediate-illicit-consent-grants"></a>Détecter et corriger les octrois de consentement illicites

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Résumé**  Découvrez comment reconnaître et corriger les attaques par consentement illicite dans Microsoft 365.

## <a name="what-is-the-illicit-consent-grant-attack-in-microsoft-365"></a>Qu’est-ce que l’attaque par consentement illicite Microsoft 365 ?

Dans le cas d’une attaque par consentement illicite, l’attaquant crée une application enregistrée par Azure qui demande l’accès à des données telles que des informations de contact, des e-mails ou des documents. L’attaquant astuce ensuite un utilisateur final pour accorder à cette application son consentement pour accéder à ses données via une attaque par hameçonnage ou en injectant du code illicite dans un site web approuvé. Une fois que l’application illicite a obtenu son consentement, elle dispose d’un accès au niveau du compte aux données sans avoir besoin d’un compte d’organisation. Les étapes de correction normales, telles que la réinitialisation des mots de passe pour les comptes en violation ou la nécessité d’une authentification multifacteur (MFA) sur les comptes, ne sont pas efficaces contre ce type d’attaque, car il s’agit d’applications tierces externes à l’organisation.

Ces attaques tirent parti d’un modèle d’interaction qui suppose que l’entité qui appelle les informations est une automatisation et non une personne.

> [!IMPORTANT]
> Pensez-vous que vous rencontrez des problèmes avec l’octroi illégal de consentement à partir d’une application, pour le moment ? Microsoft Defender pour les applications cloud dispose d’outils pour détecter, examiner et corriger vos applications OAuth. Cet article Defender pour les applications cloud dispose d’un didacticiel qui explique comment examiner les applications [OAuth à risque.](/cloud-app-security/investigate-risky-oauth) Vous pouvez également définir des stratégies d’application [OAuth](/cloud-app-security/app-permission-policy) pour examiner les autorisations demandées par l’application, les utilisateurs qui autorisent ces applications, et largement approuver ou interdire ces demandes d’autorisations.

## <a name="what-does-an-illicit-consent-grant-attack-look-like-in-microsoft-365"></a>À quoi ressemble une attaque d’octroi de consentement illicite dans Microsoft 365 ?

Vous devez effectuer une recherche dans le journal **d’audit** pour trouver des signes, également appelés indicateurs de compromission (IOC) de cette attaque. Pour les organisations avec de nombreuses applications inscrites dans Azure et une base d’utilisateurs importante, la meilleure pratique consiste à examiner les octrois de consentement de votre organisation sur une base hebdomadaire.

### <a name="steps-for-finding-signs-of-this-attack"></a>Étapes de recherche des signes de cette attaque

1. Ouvrez le Microsoft 365 Defender <https://security.microsoft.com> portail, puis sélectionnez **Audit.** Ou, pour accéder directement à la page **Audit**, utilisez <https://security.microsoft.com/auditlogsearch>.

2. Dans la page **Audit,** vérifiez que **l’onglet** Recherche est sélectionné, puis configurez les paramètres suivants :
   - **Plage de dates et d’heure**
   - **Activités :** vérifiez que l’affiche **des résultats pour toutes les** activités est sélectionnée.

   Lorsque vous avez terminé, cliquez sur **Rechercher**.

3. Cliquez sur **la colonne** Activité pour trier les résultats et rechercher consentement **à l’application.**

4. Sélectionnez une entrée dans la liste pour voir les détails de l’activité. Vérifiez si IsAdminContent est définie sur True.

> [!NOTE]
>
> L’affichage de l’entrée du journal d’audit correspondant dans les résultats de la recherche après un événement peut prendre entre 30 minutes et 24 heures.
>
> La durée de rétention et de recherche d’un enregistrement d’audit dans le journal d’audit dépend de votre abonnement Microsoft 365 et plus précisément du type de licence attribuée à un utilisateur spécifique. Pour plus d’informations, consultez [le journal d’audit.](../../compliance/search-the-audit-log-in-security-and-compliance.md)
>
> Si cette valeur est vraie, elle indique qu’une personne ayant un accès Administrateur général a peut-être accordé un large accès aux données. S’il s’agit d’une attaque inattendue, prenez les mesures [nécessaires pour confirmer une attaque.](#how-to-confirm-an-attack)

## <a name="how-to-confirm-an-attack"></a>Comment confirmer une attaque

Si vous avez une ou plusieurs instances des CCI répertoriées ci-dessus, vous devez poursuivre l’examen pour confirmer que l’attaque s’est produite. Vous pouvez utiliser l’une de ces trois méthodes pour confirmer l’attaque :

- Inventoriez les applications et leurs autorisations à l’aide Azure Active Directory portail. Cette méthode est minutieuse, mais vous ne pouvez vérifier qu’un seul utilisateur à la fois, ce qui peut prendre beaucoup de temps si vous avez de nombreux utilisateurs à vérifier.
- Inventorier les applications et leurs autorisations à l’aide de PowerShell. Il s’agit de la méthode la plus rapide et la plus minutieuse, avec la charge de traitement la moins importante.
- Demander à vos utilisateurs de vérifier individuellement leurs applications et autorisations et de signaler les résultats aux administrateurs pour correction.

## <a name="inventory-apps-with-access-in-your-organization"></a>Inventaire des applications avec accès dans votre organisation

Vous pouvez le faire pour vos utilisateurs avec le portail Azure Active Directory ou PowerShell ou faire en sorte que vos utilisateurs édent individuellement leur accès aux applications.

### <a name="steps-for-using-the-azure-active-directory-portal"></a>Étapes d’utilisation du portail Azure Active Directory web

Vous pouvez rechercher les applications pour lesquelles un utilisateur individuel a accordé des autorisations à l’aide du portail Azure Active Directory sur <https://portal.azure.com> .

1. Connectez-vous au portail Azure avec des droits d’administration.
2. Sélectionnez le Azure Active Directory de l’équipe.
3. Sélectionnez **Utilisateurs**.
4. Sélectionnez l’utilisateur à réviser.
5. Sélectionnez **Applications**.

Cela vous indique les applications qui sont affectées à l’utilisateur et les autorisations dont elles ont.

### <a name="steps-for-having-your-users-enumerate-their-application-access"></a>Étapes à suivre pour que vos utilisateurs éummentent l’accès à leur application

Demande à vos utilisateurs <https://myapps.microsoft.com> d’y accéder et de consulter leur propre accès à l’application. Ils doivent être en mesure d’afficher toutes les applications ayant accès, d’afficher les détails les concernant (y compris l’étendue de l’accès) et de révoquer des privilèges pour des applications suspectes ou illicites.

### <a name="steps-for-doing-this-with-powershell"></a>Étapes à suivre pour ce faire avec PowerShell

Le moyen le plus simple de vérifier l’attaque par consentement illicite consiste à exécuter [Get-AzureADPSPermissions.ps1, ](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09)qui vide toutes les autorisations OAuth et toutes les applications OAuth pour tous les utilisateurs de votre location dans un seul fichier .csv.

#### <a name="pre-requisites"></a>Conditions préalables

- La Azure AD PowerShell installée.
- Droits d’administrateur général sur le client sur qui le script sera exécuté.
- Administrateur local sur l’ordinateur à partir duquel exécuter les scripts.

> [!IMPORTANT]
> Nous ***vous recommandons vivement*** d’exiger une authentification multifacteur sur votre compte d’administration. Ce script prend en charge l’authentification multifacteur.

1. Connectez-vous à l’ordinateur à partir de qui vous exécuterez le script avec des droits d’administrateur local.

2. Téléchargez ou copiez [Get-AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09) script de GitHub vers un dossier à partir duquel vous exécuterez le script. Ce sera le même dossier dans lequel le fichier « permissions.csv » de sortie sera écrit.

3. Ouvrez une session PowerShell en tant qu’administrateur et ouvrez le dossier dans lequel vous avez enregistré le script.

4. Connecter votre répertoire à l’aide de [l’Connecter-AzureAD.](/powershell/module/azuread/connect-azuread)

5. Exécutez cette commande PowerShell :

   ```powershell
   .\Get-AzureADPSPermissions.ps1 | Export-csv -Path "Permissions.csv" -NoTypeInformation
   ```

Le script produit un fichier nommé Permissions.csv. Pour rechercher des autorisations d’application illicites, suivez les étapes suivantes :

1. Dans la colonne ConsentType (colonne G), recherchez la valeur « AllPrinciples ». L’autorisation AllPrincipals permet à l’application cliente d’accéder au contenu de tout le monde dans la location. Les applications Microsoft 365 natives ont besoin de cette autorisation pour fonctionner correctement. Toutes les applications non-Microsoft qui ont cette autorisation doivent être examinées attentivement.

2. Dans la colonne Autorisation (colonne F), examinez les autorisations dont dispose chaque application déléguée pour le contenu. Recherchez les autorisations « Lecture » et « Écriture » ou « * ». Toutes les autorisations et examinez-les attentivement, car elles peuvent ne pas être appropriées.

3. Examinez les utilisateurs spécifiques qui ont des consentements accordés. Si des utilisateurs à profil élevé ou à fort impact ont des consentements inappropriés accordés, vous devez examiner plus en détail.

4. Dans la colonne ClientDisplayName (colonne C), recherchez les applications qui semblent suspectes. Les applications avec des noms mal orthographiés, des noms de super-sites ou des noms de pirates informatiques doivent être examinées attentivement.

## <a name="determine-the-scope-of-the-attack"></a>Déterminer l’étendue de l’attaque

Une fois que vous avez terminé l’inventaire de l’accès aux applications, examinez le journal **d’audit** pour déterminer l’étendue complète de la violation. Recherchez les utilisateurs concernés, les délais d’accès de l’application illicite à votre organisation et les autorisations de l’application. Vous pouvez effectuer une recherche **dans le journal d’audit** [dans Microsoft 365 Defender portail.](../../compliance/search-the-audit-log-in-security-and-compliance.md)

> [!IMPORTANT]
> [L’audit de boîte](../../compliance/enable-mailbox-auditing.md) aux lettres et l’audit d’activité pour les administrateurs et les utilisateurs doivent avoir été [activés](../../compliance/turn-audit-log-search-on-or-off.md) avant l’attaque pour que vous receviez ces informations.

## <a name="how-to-stop-and-remediate-an-illicit-consent-grant-attack"></a>Comment arrêter et corriger une attaque d’octroi de consentement illicite

Une fois que vous avez identifié une application avec des autorisations illicites, vous avez plusieurs façons de supprimer cet accès.

- Vous pouvez révoquer l’autorisation de l’application dans le portail Azure Active Directory en :
  1. Accédez à l’utilisateur affecté dans le **Azure Active Directory’utilisateur.**
  2. Sélectionnez **Applications**.
  3. Sélectionnez l’application illicite.
  4. Cliquez **sur Supprimer** dans l’exercice vers le bas.

- Vous pouvez révoquer l’octroi de consentement OAuth avec PowerShell en suivant les étapes de [Remove-AzureADOAuth2PermissionGrant](/powershell/module/azuread/Remove-AzureADOAuth2PermissionGrant).

- Vous pouvez révoquer l’attribution de rôle d’application de service avec PowerShell en suivant les étapes de [Remove-AzureADServiceAppRoleAssignment](/powershell/module/azuread/Remove-AzureADServiceAppRoleAssignment).

- Vous pouvez également désactiver la connectez-vous pour le compte affecté, ce qui désactivera à son tour l’accès de l’application aux données de ce compte. Ce n’est pas idéal pour la productivité de l’utilisateur final, bien entendu, mais si vous travaillez pour limiter rapidement l’impact, il peut s’agir d’une correction viable à court terme.

- Vous pouvez désactiver les applications intégrées pour votre location. Il s’agit d’une étape radicale qui désactive la possibilité pour les utilisateurs finaux d’accorder leur consentement à l’échelle du client. Cela empêche vos utilisateurs d’accorder par inadvertance l’accès à une application malveillante. Cette recommandation n’est pas vivement recommandée, car elle nuit gravement à la capacité de productivité de vos utilisateurs avec des applications tierces. Pour ce faire, vous pouvez suivre les étapes de [l’étape d'](../../admin/misc/user-consent.md)allumer ou de éteindre les applications intégrées.

## <a name="secure-microsoft-365-like-a-cybersecurity-pro"></a>Sécuriser Microsoft 365 comme un pro de la cyber-sécurité

Votre abonnement Microsoft 365 inclut un ensemble puissant de fonctionnalités de sécurité que vous pouvez utiliser pour protéger vos données et vos utilisateurs. Utilisez la [Feuille de route du Centre de sécurité Microsoft 365 : principales priorités pour les 30 premiers jours, 90 premiers jours et au-delà](security-roadmap.md), pour implémenter les meilleures pratiques recommandées par Microsoft pour sécuriser votre client Microsoft 365.

- Tâches à effectuer lors des 30 premiers jours. Elle ont un effet immédiat et n’ont qu’un faible impact négatif sur vos utilisateurs.
- Tâches à accomplir en 90 jours. Celles-ci prennent un peu plus de temps à planifier et à implémenter, mais améliorent considérablement votre posture de sécurité.
- Au-delà de 90 jours. Ces améliorations s’appuient sur vos 90 premiers jours de travail.

## <a name="see-also"></a>Voir aussi

- Une application inattendue dans ma liste [d’applications](/azure/active-directory/application-access-unexpected-application) permet aux administrateurs d’accéder aux différentes actions qu’ils souhaitent peut-être réaliser après avoir réalisé qu’il existe des applications inattendues ayant accès aux données.
- [L’intégration d’applications Azure Active Directory](/azure/active-directory/active-directory-apps-permissions-consent) est une vue d’ensemble générale du consentement et des autorisations.
- [Les problèmes liés au développement de mon application](/azure/active-directory/active-directory-application-dev-development-content-map) fournissent des liens vers différents articles relatifs au consentement.
- Les objets principaux d’application et de service dans [Azure Active Directory (Azure AD)](/azure/active-directory/develop/active-directory-application-objects) offrent une vue d’ensemble des objets principaux d’application et de service qui sont essentiels au modèle d’application.
- [La gestion de l’accès aux applications](/azure/active-directory/active-directory-managing-access-to-apps) est une vue d’ensemble des fonctionnalités dont les administrateurs ont besoin pour gérer l’accès des utilisateurs aux applications.
