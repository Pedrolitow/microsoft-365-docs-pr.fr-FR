---
title: Délai d’inactivité pour les sessions Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Adm_TOC
description: Définissez la durée de la session de l’utilisateur Microsoft 365 avant son délai d’Microsoft 365 terme.
ms.openlocfilehash: 215b900315b2d98b01a8cf87b14a6fa65289e121
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504876"
---
# <a name="idle-session-timeout-for-microsoft-365-public-preview"></a>Délai d’Microsoft 365 session inactif (prévisualisation publique)

<!-- Add metadata: localization, AdminSurgePortfolio, admindeeplinkMAC. remove robots nofollow -->

Utilisez le délai d’attente des sessions inactives pour configurer une stratégie sur la durée pendant combien de temps les utilisateurs sont inactifs dans votre organisation avant d’être Microsoft 365 applications web. Cela permet de protéger les données sensibles de l’entreprise et d’ajouter une couche de sécurité supplémentaire pour les utilisateurs finaux qui travaillent sur des appareils non professionnels ou partagés.

Lorsqu’un utilisateur atteint la session de délai d’inactivité que vous avez définie, il reçoit une notification lui avertissant qu’il est sur le point d’être signé. Ils doivent choisir de rester en ligne ou ils seront automatiquement Microsoft 365 applications web.

> [!IMPORTANT]
> Le délai d’inactivité de session n’affecte pas Microsoft 365 bureau et les applications mobiles.

## <a name="turn-on-idle-session-timeout"></a>Activer le délai d’attente de session inactive

Si vous n’êtes pas administrateur Microsoft 365 ou Office 365 administrateur global, l’onglet Sécurité & **confidentialité ne s'&** pas.

1. Dans la Centre d'administration Microsoft 365, sélectionnez **l’onglet** **->** Sécurité Paramètres organisation [&](https://go.microsoft.com/fwlink/p/?linkid=2072756) et sélectionnez Délai d’inactivité **de la session**.  

2. Dans le **délai d’inactivité de session** , sélectionnez le basculement pour l’activer. Vous pouvez choisir un paramètre par défaut ou choisir votre propre heure personnalisée. Il faudra quelques minutes avant que la session inactive soit allumée dans votre organisation.

> [!NOTE]
> Si vous avez installé des stratégies de délai d’attente de session inactive pour [Outlook web app](https://support.microsoft.com/topic/description-of-the-activity-based-authentication-timeout-for-owa-in-office-365-0c101e1b-020e-69c1-a0b0-26532d60c0a4) et [SharePoint Online](/sharepoint/sign-out-inactive-users), l’ouverture du délai d’attente des sessions inactives dans le Centre d'administration Microsoft 365 remplacera les paramètres d’application web Outlook et SharePoint.

Le délai d’inactivité de session est l’une des nombreuses mesures de sécurité Microsoft 365. Pour en savoir plus sur les autres tâches de sécurité dans Microsoft 365, consultez [Les principales tâches de sécurité dans Microsoft 365](../../security/top-security-tasks-for-remote-work.md).  

## <a name="what-users-will-see"></a>Ce que les utilisateurs voient

Lorsqu’un utilisateur est inactif dans Microsoft 365 web pendant la période que vous avez choisie, l’invite suivante s’invite. Ils doivent sélectionner **Rester en cours de signature** , sinon ils seront signés.

:::image type="content" source="../../media/idle-session-timeout.png" alt-text="Screenshot: Prompt letting you know that your session is about to expire. Sélectionnez Rester en ligne pour ne pas vous être Microsoft 365 applications web":::

## <a name="details-about-idle-session-timeout"></a>Détails sur le délai d’inactivité de session

- Les applications web Microsoft 365 suivantes sont pris en charge. D’autres applications web seront bientôt ajoutées.

    - Outlook Web App

    - OneDrive Entreprise

    - SharePoint Online (SPO)

    - Office.com et autres pages de démarrage

    - Office (Word, Excel, PowerPoint) sur le web

    - Centre d’administration Microsoft 365

- L’activité fait référence à toute interaction utilisateur côté client qui se produit dans le contexte de l’application web. Par exemple, les clics de souris et les pressions du clavier.  

- Le délai d’inactivité de session fonctionne par session par navigateur. L’activité d’un utilisateur sur Microsoft Edge est traitée différemment de son activité dans d’autres navigateurs tels que Google Chrome. Les utilisateurs seront signés à partir de tous les onglets correspondant à leur compte au sein de cette session de navigateur.

- Une fois que vous avez activer le délai d’attente des sessions inactives, il s’applique à l’ensemble de votre organisation et ne peut pas s’appliquer à des utilisateurs, des unités d’organisation ou des groupes spécifiques. Utilisez l [Azure AD conditionnel pour](/azure/active-directory/conditional-access/) les stratégies pour différents utilisateurs et groupes.

- Les utilisateurs doivent être inactifs sur tous Microsoft 365 onglets de l’application web pendant la durée configurée. Si l’utilisateur est actif sur un onglet (par exemple, OWA) alors qu’il est inactif sur un autre onglet (par exemple SPO), il sera considéré comme actif et ne sera pas signé.  

- Dans ce cas, les utilisateurs ne sont pas signés.
    - S’ils obtiennent l’sign-on unique (SSO) dans l’application web à partir du  compte joint à l’appareil ou sélectionné Restez connecté au moment de la signature. Pour plus d’informations sur le masquage de cette option pour votre organisation, voir Ajouter une marque à la page de signature [de votre organisation](/azure/active-directory/fundamentals/customize-branding).
    - S’ils sont sur un appareil géré (conforme ou joint à un domaine) et qu’ils utilisent un navigateur pris en charge comme Microsoft Edge ou Google Chrome (avec [l’extension Windows Accounts](https://chrome.google.com/webstore/detail/windows-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji)). Pour que cette fonctionnalité ne se déclenche pas sur un appareil géré, un abonnement Azure AD Premium P1 ou P2 éligible et une stratégie d’accès conditionnel spécifique sont requis. Pour plus d’informations, voir ci-dessous.

> [!IMPORTANT]
> Le délai d’inactivité de session n’est pas disponible pour Microsoft 365 géré par 21Vianet ou Microsoft 365 Germany.

## <a name="idle-session-timeout-on-unmanaged-devices"></a>Délai d’inactivité de session sur les appareils non utilisés  

Pour que le délai d’inactivité de session soit déclenché sur les appareils non utilisés, vous devez ajouter une stratégie d’accès conditionnel dans le Centre d’administration Azure AD.

1. Sur la **| Page Stratégies** du centre Azure AD’administration, sélectionnez **Nouvelle** stratégie et entrez un nom pour la stratégie.

2. Sélectionnez **Utilisateurs ou identités de charge de** travail, puis tous **les utilisateurs**.

3. **Sélectionnez des applications ou des actions cloud**, **sélectionnez des applications** et recherchez **des Office 365**. **Sélectionnez Office 365**, puis **Sélectionnez**.  

4. **Sélectionnez Conditions**, **Applications clientes**, **Configurer sur Oui**, **Navigateur**, puis sélectionnez **Terminé**.

5. **Sélectionnez Session**, **utilisez les restrictions appliquées par l’application**, puis **sélectionnez**.

6. Activer la stratégie et sélectionner **Créer**.

## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="are-there-any-browsers-or-browser-scenarios-in-which-idle-session-timeout-feature-doesnt-work"></a>Existe-t-il des navigateurs ou des scénarios de navigateur dans lesquels la fonctionnalité de délai d’attente de session inactive ne fonctionne pas ?  

Le délai d’inactivité de session n’est pas pris en charge lorsque les cookies tiers sont désactivés dans le navigateur. Les utilisateurs ne voient aucune invite de sortie. Nous vous recommandons de conserver le paramètre de prévention du suivi sur [Équilibré (](/microsoft-edge/web-platform/tracking-prevention)par défaut) pour les Microsoft Edge et les cookies tiers activés dans vos autres navigateurs. Microsoft 365 applications et services ont cessé de prise en charge d’Internet Explorer 11 depuis le 17 août 2021.

### <a name="how-should-i-prepare-if-my-organization-is-already-using-existing-outlook-web-app-and-sharepoint-online-idle-timeout-policies"></a>Comment dois-je me préparer si mon organisation utilise déjà une application web Outlook et des stratégies de délai d’inactivité SharePoint Online ?  

Si vous utilisez déjà une application web Outlook existante et des stratégies de délai d’inactivité SharePoint Online, vous pouvez toujours activer la fonctionnalité délai d’attente de session inactive. Lorsque vous allumez la stratégie de délai d’inactivité, elle est prioritaire sur l’application web Outlook et les stratégies SharePoint Online existantes. Nous prévoyons d’Outlook l’application web et SharePoint Online dans un futur proche. Pour mieux préparer votre organisation, nous vous recommandons d’activer le délai d’inactivité des sessions.

### <a name="what-happens-if-i-am-inactive-on-an-included-microsoft-365-web-app-but-active-on-a-microsoft-web-app-or-saas-web-app-that-doesnt-have-idle-session-timeout-turned-on"></a>Que se passe-t-il si je suis inactif sur une application web Microsoft 365 incluse, mais actif sur une application web Microsoft ou Une application web SaaS pour qui le délai d’inactivité de session n’est pas allumé ?  

Les applications web Microsoft 365 suivantes sont pris en charge.

- Outlook Web App

- OneDrive Entreprise

- SharePoint Online (SPO)

- Office.com et autres pages de démarrage

- Office (Word, Excel, PowerPoint) sur le web

- Centre d’administration Microsoft 365

Si vous travaillez sur une autre application web avec le même compte, l’activité dans cette application web ne sera pas appliquée au délai d’inactivité de session.

### <a name="i-want-to-make-changes-to-the-idle-session-timeout-policy-or-delete-it-how-can-i-do-that"></a>Je souhaite apporter des modifications à la stratégie de délai d’attente de session inactive ou la supprimer. Comment puis-je faire ?

Mettez à jour la stratégie :

1. Dans la Centre d'administration Microsoft 365, sélectionnez **Paramètres** de l’organisation, sélectionnez l’onglet Sécurité **& confidentialité** et sélectionnez Délai d’inactivité de **la session**.

2. Dans le menu déroulant, sélectionnez une autre valeur de délai d’arrêt, puis **enregistrez**.  

Supprimez la stratégie :

1. Dans la Centre d'administration Microsoft 365, sélectionnez **Paramètres** de l’organisation, sélectionnez l’onglet Sécurité **& confidentialité** et sélectionnez Délai d’inactivité de **la session**.

2. **Désélectionnez Activer pour définir** la période d’inactivité pour que les utilisateurs soient Office applications web et sélectionnez **Enregistrer**.
