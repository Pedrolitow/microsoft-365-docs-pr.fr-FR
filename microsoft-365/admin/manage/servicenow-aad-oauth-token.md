---
title: Configurer l’intégration Microsoft 365 prise en charge avec Azure AD auth
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: Guide de configuration et d’installation d’applications certifiées étendues pour ServiceNow.
ms.openlocfilehash: 9f9985e07989f168f9b27dde1c1d574813c3f349
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320898"
---
# <a name="configure-microsoft-365-support-integration-with-azure-ad-auth-token"></a>Configurer l’intégration Microsoft 365 prise en charge avec Azure AD auth

## <a name="prerequisites-azure-ad-auth-token"></a>Prerequisites (Azure AD Auth Token)

Ces conditions préalables sont nécessaires pour configurer la prise en charge Microsoft 365'intégration.

1. \[AAD admin\] Créez Azure AD application pour le trafic sortant sous votre Microsoft 365 client.

    1. Connectez-vous au portail Azure à l’Microsoft 365 vos informations d’identification client et allez sur la [page](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) d’inscription de l’application pour créer une application.

    2. Sélectionnez comptes dans cet annuaire d’organisation uniquement **({Microsoft-365-tenant-name} uniquement – Client unique)** et sélectionnez **Enregistrer**.

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Go to **Authentication** and select **Add a platform**. Sélectionnez **l’option Web** et entrez l’URL de redirection : `https://{your-servicenow-instance``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Obtenez l’ID client de l’application, créez une secret client et obtenez cette valeur.

1. \[AAD admin\] Créez une API application Azure AD Rest sous votre client Microsoft 365 client.

    1. Connectez-vous au [portail Azure](https://portal.azure.com/) à l’Microsoft 365 vos informations d’identification client et allez sur la page d’inscription de l’application pour créer une application.

    1. **Sélectionnez les comptes dans cet annuaire d’organisation uniquement {(Microsoft-365-tenant-name} uniquement – Client unique).**

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image22.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image22.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Obtenez l’ID client de l’application, créez une secret client et obtenez cette valeur.

1. \[AAD admin\] Créez une Azure AD application pour l’utilisateur Rest sous votre Microsoft 365 client.

    1. Connectez-vous au [portail Azure](https://portal.azure.com/) à l’Microsoft 365 vos informations d’identification client et allez sur la page d’inscription de l’application pour créer une application.

    1. **Sélectionnez les comptes dans cet annuaire d’organisation uniquement {(Microsoft-365-tenant-name} uniquement – Client unique).**

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" lightbox="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Obtenez l’ID client de l’application, créez une secret client et obtenez cette valeur.

1. \[L’administrateur\] ServiceNow a installé le fournisseur OAuth sortant dans ServiceNow.

    Si l’étendue n’est pas définie sur **Global**, pour ce faire, **&gt; &gt;** naviguez jusqu’Paramètres Applications de développeur et basculez vers **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Interface utilisateur graphique, texte, application, conversation ou message texte Description générés automatiquement":::

1. Go to **System OAuth &gt; Application Registry**.

1. Créez une application à **l’aide Connecter’une option de fournisseur OAuth** tierce et en entrant les valeurs ci-après :

    - ID client : il s’agit de l’ID client de l’application créée à l’étape 1 des conditions préalables (Azure AD auth Token).\#

    - Secret client : il s’agit de la valeur de la secret client de l’application créée à l’étape 1 des conditions préalables (Azure AD auth Token).\#

    - Type d’octroi par défaut : informations d’identification du client

    - URL du jeton : `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - URL de redirection : `https://{service-now-instance-name``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

1. \[Administration de ServiceNow\] Pour configurer le fournisseur OIDC dans ServiceNow, consultez la [documentation en ligne](https://docs.servicenow.com/bundle/quebec-platform-administration/page/administer/security/task/add-OIDC-entity.html).

    Si l’étendue n’est pas définie sur **Global**, Paramètres **&gt; &gt; Applications** de développeur et passez à **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Interface utilisateur graphique, texte, application, conversation ou message texte Description générés automatiquement":::

1. Go to **System OAuth &gt; Application Registry**.

1. **Sélectionnez Nouveau**, puis **créez un nouvel ID d’ouverture Connecter fournisseur**.

1. Dans **la configuration du fournisseur OAuth OIDC**, sélectionnez **Rechercher** et créez une configuration de fournisseur OIDC sous **oidcproviderconfiguration.list\_\_** avec les valeurs ci-dessous :

    - Fournisseur OIDC : **{TenantName\_} Azure** (exemple : Contoso Azure)

    - URL de métadonnées OIDC : `https://login.microsoftonline.com/{microsoft-365-tenant-name}/.well-known/openid-configuration`

    - UserClaim: **appid**

    - UserField : **ID utilisateur**

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image24.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image24.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

1. Créez une application en sélectionnant **Configurer un fournisseur OIDC pour vérifier les jetons d’ID avec les valeurs** ci-après :

    - Nom : **{TenantName\_}\_applicationinboundapi\_\_** (exemple : contosoapplicationinboundapi\_\_\_)

    - ID client : ID client de l’application créée à l’étape Azure AD \#2.

    - Secret client : secret d’application de l’application créée à l’étape Azure AD \#2.

    - Configuration du fournisseur OAuth OIDC : fournisseur OIDC créé à l’étape précédente

    - URL de redirection : `https://{service-now-instance-name}.service-now.com/oauth\_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image25.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image25.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

1. \[L’administrateur ServiceNow crée\] des utilisateurs d’intégration.

    Vous devez spécifier un utilisateur d’intégration. Si vous n’avez pas d’utilisateur d’intégration existant ou si vous souhaitez en créer un spécifiquement pour cette intégration, **&gt;** rendez-vous sur Utilisateurs de l’organisation pour créer un utilisateur. La valeur de **l’ID** d’utilisateur est l’ID client de l’application créé dans [les conditions préalables (Azure AD auth Token).](#prerequisites-azure-ad-auth-token)

    Si vous créez un utilisateur d’intégration, vérifiez l’option **d’accès au service Web uniquement** . Vous devez également accorder à cet utilisateur le rôle **de gestion\_ des** incidents.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image26.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image26.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

## <a name="optional-allow-the-services-ip-addresses-to-microsoft-365-support-integration"></a>\[FACULTATIF\] Autoriser les adresses IP du service à prendre en charge Microsoft 365'intégration

Si votre entreprise limite l’accès à Internet avec vos propres stratégies, activez l’accès réseau pour le service de prise en charge Microsoft 365 en permettant les adresses IP ci-dessous pour l’accès à l’API entrante et sortante.

- 52.149.152.32

- 40.83.232.243

- 40.83.114.39

- 13.76.138.31

- 13.79.229.170

- 20.105.151.142

> [!NOTE]
> Cette commande terminal répertorie toutes les IP actives du service pour Microsoft 365 l’intégration de la prise en charge :`nslookup`` connector.rave.microsoft.com`

## <a name="configure-the-microsoft-365-support-integration-application"></a>Configurer l’application Microsoft 365 prise en charge de l’intégration

L’Microsoft 365'intégration de support technique peut être définie sous Microsoft 365 prise en charge.

Ces étapes sont nécessaires pour configurer l’intégration entre votre instance ServiceNow et Microsoft 365 prise en charge.

1. \[L’administrateur ServiceNow bascule\] l’étendue **Microsoft 365 l’intégration de la prise en charge**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image9.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image9.png" alt-text="Interface utilisateur graphique, description de tableau générée automatiquement":::

1. \[ServiceNow Admin\] Go to **Microsoft 365 Support &gt; Setup** to open the integration workflow.

    > [!NOTE]
    > Si l’erreur « Opération de lecture sur ' oauthentity\_ ' de l’étendue 'xmiomsm365assis\_\_\_' a été refusée en raison de la stratégie d’accès à plusieurs étendues de la table », elle est due à votre stratégie d’accès de table. Vous devez vous assurer **que toutes les étendues d’application lues sont vérifiées &gt;** pour la table oauthentity\_.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image27.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image27.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[Sélection de l’administrateur\] ServiceNow **Acceptez** l’invite de consentement pour continuer.

    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-1.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-1.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[Administration De ServiceNow\] Configurez l’environnement et le type d’installation.
    Si cette installation se trouve dans un environnement de test, sélectionnez l’option Il s’agit d’un environnement de test. Vous pourrez rapidement désactiver cette option après l’installation et tous vos tests seront effectués ultérieurement.
    Si votre instance autorise l’authentification de base pour les connexions entrantes, sélectionnez Oui et reportez-vous au processus de configuration [de l’authentification de base](servicenow-basic-authentication.md). Dans le cas contraire, **sélectionnez Non** , puis cliquez **sur Démarrer l’installation**. 
      :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-2.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-2.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[Administrateur ServiceNow Entrez\] votre domaine Microsoft 365 client.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-3.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-3.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[L’administrateur\] ServiceNow configure le fournisseur OAuth sortant.
    1. Configurez le fournisseur OAuth sortant.
    1. Après avoir suivi les instructions de la section Conditions préalables, cliquez sur Terminé. Sinon, suivez les instructions de l’Assistant pour créer l’inscription d’application nécessaire dans AAD.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-4.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-4.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::
    1. Inscrivez l’application OAuth ServiceNow.
    1. Après avoir suivi les instructions de la section Conditions préalables, sélectionnez l’inscription de l’application OAuth nouvellement créée, puis cliquez sur Suivant. Sinon, suivez les instructions pour créer l’entité dans ServiceNow, puis sélectionnez la nouvelle inscription d’application.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-5.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-5.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[L’administrateur\] ServiceNow configure les paramètres entrants.
    1. Configurez l’application AAD entrante.
    1. Après avoir suivi les instructions de la section Conditions préalables, cliquez sur Terminé pour passer à l’étape suivante. Sinon, suivez les instructions pour créer l’AAD’application pour la connectivité entrante.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-6.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-6.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::
    1. Configurez le fournisseur openid externe ServiceNow Connecter (fournisseur OIDC).
    1. Après avoir suivi les instructions de la section Conditions préalables, sélectionnez l’entité nouvellement créée, puis cliquez sur Terminé. Sinon, suivez les instructions pour créer l’entité dans ServiceNow, puis sélectionnez l’inscription de l’application fournisseur OIDC externe.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-7.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-7.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::
    1. Configurez l’AAD’inscription de l’application pour l’utilisateur d’intégration entrante.
    1. Après avoir suivi les instructions de la section Conditions préalables, cliquez sur Terminé pour passer à l’étape suivante. Dans le cas contraire, suivez les instructions pour créer l’AAD’inscription de l’application pour l’utilisateur REST entrant (utilisateur d’intégration).
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-8.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-8.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::
    1. Configurez l’utilisateur d’intégration.
    1. Après avoir suivi les instructions de la section Conditions préalables, sélectionnez l’entité nouvellement créée, puis cliquez sur Suivant. Sinon, suivez les instructions pour créer l’utilisateur d’intégration dans ServiceNow, puis sélectionnez l’entité.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-9.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-9.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[Microsoft 365 client\] Terminez l’intégration.

    Vérifiez que les informations ci-dessous sont correctes. NE sélectionnez **PAS Suivant** pour le moment.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image40.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image40.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

    1. Go to **Administration Microsoft 365 Portal &gt; Paramètres &gt; Org settings &gt; Organization profiles**.

    1. Configurez les paramètres d’intégration de la prise en charge :

    Sélectionnez **l’onglet** Informations de base >'outil  >  de support **interneServiceNow**, puis entrez la valeur **de l’ID** de l’application sortante dans **l’ID d’application** pour émettre le champ Jeton auth. Cet ID d’application sortante se trouve à l’étape 6 : terminer l’intégration, qui a été créée dans [prerequisites (Azure AD Auth Token).](#prerequisites-azure-ad-auth-token)

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

    1. Sous **l’onglet Référentiels** , sélectionnez **Nouveau** référentiel et mettez-le à jour avec les paramètres suivants :

    - Référentiel : valeur **de l’ID** de référentiel de « Étape 6 : Terminer l’intégration ».

    - Point de terminaison **: valeur de point** de terminaison de « Étape 6 - Terminer l’intégration ».

    - Type d’authentification **: sélectionnez AAD authentification**.

    - ID client : valeur **de l’ID client** de l’étape 6 : terminer l’intégration.

    - Secret client : secret du fournisseur OAuth entrant créé à l’étape 2 des conditions préalables (Azure AD auth).\#

    - Nom d’utilisateur  restant : valeur du nom d’utilisateur de l’étape 6 : terminer l’intégration, qui est **l’ID client** de l’application créée à l’étape 3 des conditions préalables (jeton d’th Azure AD).\#

    - Mot de passe de l’utilisateur rest : secret d’application de l’application créée à l’étape 3 des conditions préalables (Azure AD auth).\#

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image31.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image31.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

    1. Revenir à ServiceNow.

    1. **Sélectionnez Suivant** pour terminer l’intégration.

   :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-10.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-10.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::
    L’Microsoft 365 prise en charge de l’intégration exécutera des tests pour s’assurer que l’intégration fonctionne. En cas de problème avec la configuration, un message d’erreur explique ce qui doit être résolu. Sinon, l’application est prête.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-11.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-11.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[L’administrateur\] ServiceNow active l’intégration du support Microsoft pour un utilisateur existant.

    Microsoft 365'intégration de la prise en charge est activée pour l’utilisateur avec l’un des rôles ci-après :

    - xmiomsm365assis.insightsuser\_\_\_\_

    - xmiomsm365assis.administrator\_\_\_

1. \[FACULTATIF\] \[Lien utilisateur avec le rôle xmiomsm365assis.administrator\]\_\_\_ Microsoft 365 compte d’administrateur.

    Si un utilisateur a le rôle xmiomsm365assis.administrator\_\_\_ et utilise différents comptes Microsoft 365 pour gérer un cas de support Microsoft 365, il doit se rendre sur le compte de lien de support Microsoft 365 &gt; pour configurer son e-mail d’administrateur Microsoft 365.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image21.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image21.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::
