---
title: Délai d’expiration de session inactif pour Microsoft 365
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
description: Définissez la durée de la session de l’utilisateur dans Microsoft 365 avant son expiration.
ms.openlocfilehash: 527862e77f8fdfba3c418ba13607bc1389875cab
ms.sourcegitcommit: 6e570b79944862c86735db455349b685d5b903b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2022
ms.locfileid: "67019920"
---
# <a name="idle-session-timeout-for-microsoft-365"></a>Délai d’expiration de session inactif pour Microsoft 365

<!-- Add metadata: localization, AdminSurgePortfolio, admindeeplinkMAC. remove robots nofollow -->

> [!IMPORTANT]
> Le délai d’expiration de la session inactive n’est pas disponible pour Microsoft 365 géré par 21Vianet ou Microsoft 365 Germany.

Utilisez le délai d’inactivité de session pour configurer une stratégie sur la durée pendant laquelle les utilisateurs sont inactifs dans votre organisation avant de se déconnecter des applications web Microsoft 365. Cela permet de protéger les données d’entreprise sensibles et ajoute une autre couche de sécurité pour les utilisateurs finaux qui travaillent sur des appareils non professionnels ou partagés.

Lorsqu’un utilisateur atteint la session de délai d’inactivité que vous avez définie, il reçoit une notification indiquant qu’il est sur le point d’être déconnecté. Ils doivent choisir de rester connectés, sinon ils seront automatiquement déconnectés de toutes les applications web Microsoft 365.

> [!IMPORTANT]
> Le délai d’inactivité de la session n’affecte pas vos applications mobiles et de bureau Microsoft 365.

## <a name="turn-on-idle-session-timeout"></a>Activer le délai d’expiration de la session inactive

Vous devez être membre des rôles d’administrateur général, d’administrateur de sécurité, d’administrateur d’application ou d’administrateur d’application cloud pour voir le paramètre de délai d’expiration de session inactif.

1. Dans le Centre d'administration Microsoft 365, sélectionnez Sécurité **des paramètres** **->** de [l’organisation & onglet Confidentialité](https://go.microsoft.com/fwlink/p/?linkid=2072756), puis **sélectionnez Délai d’expiration de session inactif**.  

2. Dans le **délai d’expiration de la session inactive** , sélectionnez le bouton bascule pour l’activer. Vous pouvez choisir un paramètre par défaut ou choisir votre propre heure personnalisée. Quelques minutes sont nécessaires avant que la session inactive ne soit activée dans votre organisation.

> [!NOTE]
> Si vous avez configuré des stratégies de délai d’expiration de session inactive pour [l’application web Outlook](https://support.microsoft.com/topic/description-of-the-activity-based-authentication-timeout-for-owa-in-office-365-0c101e1b-020e-69c1-a0b0-26532d60c0a4) et [SharePoint Online](/sharepoint/sign-out-inactive-users), l’activation du délai d’expiration de session inactive dans le Centre d'administration Microsoft 365 remplace les paramètres de l’application web Outlook et sharePoint.

Le délai d’expiration de la session inactive est l’une des nombreuses mesures de sécurité dans Microsoft 365. Pour en savoir plus sur les autres tâches de sécurité dans Microsoft 365, consultez [Tâches de sécurité principales dans Microsoft 365](../../security/top-security-tasks-for-remote-work.md).  

## <a name="what-users-will-see"></a>Ce que les utilisateurs verront

Lorsqu’un utilisateur a été inactif dans les applications web Microsoft 365 pendant la période que vous avez choisie, l’invite suivante s’affiche. Ils doivent sélectionner **Rester connectés** ou ils seront déconnectés.

:::image type="content" source="../../media/idle-session-timeout.png" alt-text="Capture d’écran : Invite vous informant que votre session est sur le point d’expirer. Sélectionnez Rester connecté pour ne pas vous déconnecter des applications web Microsoft 365":::

## <a name="details-about-idle-session-timeout"></a>Détails sur le délai d’expiration de session inactive

- Les applications web Microsoft 365 suivantes sont prises en charge. D’autres applications web seront bientôt ajoutées.

    - Outlook Web App

    - OneDrive Entreprise

    - SharePoint Online (SPO)

    - Office.com et d’autres pages de démarrage

    - Office (Word, Excel, PowerPoint) sur le web

    - Centre d’administration Microsoft 365

- L’activité fait référence à toute interaction utilisateur côté client qui se produit dans le contexte de l’application web. Par exemple, les clics de souris et les appuis clavier.  

- Le délai d’expiration de la session inactive fonctionne sur une base de session par navigateur. L’activité d’un utilisateur sur Microsoft Edge est traitée différemment de son activité dans d’autres navigateurs tels que Google Chrome. Les utilisateurs seront déconnectés de tous les onglets correspondant à leur compte au sein de cette session de navigateur.

- Une fois que vous avez activé le délai d’expiration de session inactive, il s’applique à l’ensemble de votre organisation et ne peut pas être étendu à des utilisateurs, des unités d’organisation ou des groupes spécifiques. Utilisez des stratégies [d’accès conditionnel Azure AD](/azure/active-directory/conditional-access/) pour différents utilisateurs et groupes afin d’accéder à SharePoint et Exchange Online.

- Les utilisateurs doivent être inactifs sur tous les onglets d’application web Microsoft 365 pendant la durée configurée. Si l’utilisateur est actif sur un onglet (par exemple, OWA) alors qu’il est inactif sur un autre onglet (par exemple, SPO), il est considéré comme actif et ne sera pas déconnecté.  

- Dans ce cas, les utilisateurs ne seront pas déconnectés.
    - S’ils obtiennent l’authentification unique (SSO) dans l’application web à partir du compte joint à l’appareil ou s’ils ont sélectionné **Rester connecté** au moment de la connexion. Pour plus d’informations sur le masquage de cette option pour votre organisation, consultez [Ajouter une personnalisation à la page de connexion de votre organisation](/azure/active-directory/fundamentals/customize-branding).
    - S’ils se trouve sur un appareil géré (un appareil conforme ou joint à un domaine) et utilisent un navigateur pris en charge comme Microsoft Edge ou Google Chrome (avec [l’extension Comptes Windows](https://chrome.google.com/webstore/detail/windows-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji)). Pour que cette fonctionnalité se déclenche sur un appareil non managé, un abonnement Azure AD Premium P1 ou P2 éligible et une stratégie d’accès conditionnel spécifique sont requis. Pour plus d’informations, voir ci-dessous.

## <a name="idle-session-timeout-on-unmanaged-devices"></a>Délai d’expiration de session inactif sur les appareils non gérés  

Pour que le délai d’inactivité de la session soit déclenché sur les appareils non gérés, vous devez ajouter une stratégie d’accès conditionnel dans le Centre d’administration Azure AD.

1. Sur le **| d’accès conditionnel Page Stratégies** du Centre d’administration Azure AD, sélectionnez **Nouvelle stratégie** et entrez un nom pour la stratégie.

2. Sélectionnez **Utilisateurs ou identités de charge de travail**, puis **tous les utilisateurs**.

3. Sélectionnez **applications ou actions cloud**, **sélectionnez des applications** et recherchez **Office 365**. Sélectionnez **Office 365**, puis **sélectionnez**.  

4. Sélectionnez **Conditions**, **Applications clientes**, **Configurer sur Oui**, **Navigateur**, puis Sélectionnez **Terminé**.

5. Sélectionnez **Session**, **Utilisez les restrictions appliquées par l’application**, puis **sélectionnez**.

6. Activez la stratégie, puis **sélectionnez Créer**.

## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="are-there-any-browsers-or-browser-scenarios-in-which-idle-session-timeout-feature-doesnt-work"></a>Existe-t-il des navigateurs ou des scénarios de navigateur dans lesquels la fonctionnalité de délai d’expiration de session inactive ne fonctionne pas ?  

Le délai d’expiration de la session inactive n’est pas pris en charge lorsque des cookies tiers sont désactivés dans le navigateur. Les utilisateurs ne voient aucune invite de déconnexion. Nous vous recommandons de conserver le paramètre de prévention de suivi [sur Balanced (Default)](/microsoft-edge/web-platform/tracking-prevention) pour Microsoft Edge et les cookies tiers activés dans vos autres navigateurs. Les applications et services Microsoft 365 n’ont plus pris en charge Internet Explorer 11 depuis le 17 août 2021.

### <a name="how-should-i-prepare-if-my-organization-is-already-using-existing-outlook-web-app-and-sharepoint-online-idle-timeout-policies"></a>Comment dois-je me préparer si mon organisation utilise déjà une application web Outlook existante et des stratégies de délai d’inactivité SharePoint Online ?  

Si vous utilisez déjà une application web Outlook existante et des stratégies de délai d’inactivité SharePoint Online, vous pouvez toujours activer la fonctionnalité de délai d’expiration de session inactive. Lorsque vous activez la stratégie de délai d’inactivité, elle est prioritaire sur les stratégies d’application web Outlook et SharePoint Online existantes. Nous prévoyons de déprécier prochainement les stratégies d’application web Outlook et SharePoint Online existantes. Pour mieux préparer votre organisation, nous vous recommandons d’activer le délai d’expiration de session inactive.

### <a name="what-happens-if-i-am-inactive-on-an-included-microsoft-365-web-app-but-active-on-a-microsoft-web-app-or-saas-web-app-that-doesnt-have-idle-session-timeout-turned-on"></a>Que se passe-t-il si je suis inactif sur une application web Microsoft 365 incluse, mais actif sur une application web Microsoft ou une application web SaaS pour laquelle le délai d’inactivité de session n’est pas activé ?  

Les applications web Microsoft 365 suivantes sont prises en charge.

- Outlook Web App

- OneDrive Entreprise

- SharePoint Online (SPO)

- Office.com et d’autres pages de démarrage

- Office (Word, Excel, PowerPoint) sur le web

- Centre d’administration Microsoft 365

Si vous travaillez sur une autre application web avec le même compte, l’activité dans cette application web ne sera pas appliquée au délai d’expiration de session inactive.

### <a name="i-want-to-make-changes-to-the-idle-session-timeout-policy-or-delete-it-how-can-i-do-that"></a>Je souhaite apporter des modifications à la stratégie de délai d’expiration de session inactive ou la supprimer. Comment puis-je faire cela ?

Mettez à jour la stratégie :

1. Dans le Centre d'administration Microsoft 365, sélectionnez **Paramètres de l’organisation**, accédez à l’onglet **Sécurité & Confidentialité**, puis **sélectionnez Délai d’expiration de session inactif**.

2. Dans le menu déroulant, sélectionnez une autre valeur de délai d’expiration, puis **Enregistrez**.  

Supprimez la stratégie :

1. Dans le Centre d'administration Microsoft 365, sélectionnez **Paramètres de l’organisation**, accédez à l’onglet **Sécurité & Confidentialité**, puis **sélectionnez Délai d’expiration de session inactif**.

2. Désactivez **l’option Activer pour définir la période d’inactivité pour que les utilisateurs soient déconnectés des applications web Office** , puis **sélectionnez Enregistrer**.
