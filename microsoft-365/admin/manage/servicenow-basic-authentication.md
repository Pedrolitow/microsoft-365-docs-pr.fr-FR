---
title: Configurer l’intégration de la prise en charge avec ServiceNow - Authentification de base
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
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
ms.openlocfilehash: cf9b5149847b51d9d701a49e32624ada3f708a17
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2022
ms.locfileid: "62321482"
---
# <a name="configure-support-integration-with-servicenow---basic-authentication"></a>Configurer l’intégration de la prise en charge avec ServiceNow - Authentification de base

## <a name="prerequisites-basic-authentication"></a>Conditions préalables (Authentification de base)

Ces conditions préalables sont nécessaires pour configurer l’Microsoft 365 **l’intégration**.

1. \[AAD admin\] Créez Azure AD application sous votre Microsoft 365 client.

    1. Connectez-vous au portail Azure à l’Microsoft 365 vos informations d’identification client et allez sur la [page](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) d’inscription de l’application pour créer une application.

    1. Sélectionnez comptes dans cet annuaire d’organisation uniquement **({Microsoft-365-tenant-name} uniquement – Client unique)** et sélectionnez **Enregistrer**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Go to **Authentication** and select **Add a platform**. Sélectionnez **l’option Web** et entrez l’URL de redirection : `https://{your-servicenow-instance``}.service-now.com/oauth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Obtenez l’ID client de l’application, créez une secret client et obtenez cette valeur.

1. \[L’administrateur\] ServiceNow a installé le fournisseur OAuth sortant dans ServiceNow.

    Si l’étendue n’est pas définie sur **Global**, **&gt; &gt; Paramètres Applications** de développeur et passez à **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Interface utilisateur graphique, texte, application, conversation ou message texte Description générés automatiquement":::

1. Go to **System OAuth &gt; Application Registry**.

1. Créez une application en utilisant l’Connecter à une option **de fournisseur OAuth** tierce et en entrant les valeurs ci-après :

    - ID client : il s’agit de l’ID client de l’application créée à l’étape \#1.

    - Secret client : il s’agit de la valeur de la secret client de l’application créée à l’étape \#1.

    - Type d’octroi par défaut : informations d’identification du client

    - URL du jeton : `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - URL de redirection : `https://{service-now-instance-name``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

1. \[L’administrateur\] ServiceNow a installé le fournisseur OAuth entrant.

    Si l’étendue n’est pas définie sur **Global**, faites-le **&gt; &gt;** en Paramètres Applications de développeur et en passant à **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Interface utilisateur graphique, texte, application, conversation ou message texte Description générés automatiquement":::

1. Go to **System OAuth &gt; Application Registry**.

1. Créez une application à l’aide de l’option Créer un point de terminaison **de l’API OAuth pour les clients externes** . Nommez le fournisseur OAuth entrant et laissez tous les autres champs avec leurs valeurs par défaut.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image7.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image7.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

1. \[Administrateur ServiceNow Créez\] un utilisateur d’intégration.

    Vous devez spécifier un utilisateur d’intégration. Si vous n’avez pas d’utilisateur d’intégration existant ou si vous souhaitez en créer un spécifiquement pour cette intégration, **&gt;** rendez-vous sur Utilisateurs de l’organisation pour créer un utilisateur.

    Si vous créez un utilisateur d’intégration, vérifiez l’option d’accès **au service Web uniquement** . Vous devez également accorder à cet utilisateur le rôle **de gestion\_ des** incidents.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image8.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image8.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

## <a name="optional-allow-the-services-ip-addresses-to-microsoft-365-support-integration"></a>\[FACULTATIF\] Autoriser les adresses IP du service à prendre en charge Microsoft 365'intégration

Si votre entreprise limite l’accès à Internet avec vos propres stratégies, activez l’accès réseau pour le service de Microsoft 365 en permettant l’intégration des adresses IP ci-dessous pour l’accès à l’API entrante et sortante :

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

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image10.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image10.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[ServiceNow Admin\] Select **Agree** to continue.

    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-1.png" lightbox="../../media/ServiceNow-guide/snowbasic-1.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[Administration De ServiceNow\] Configurez l’environnement et le type d’installation.

    Si cette installation se trouve dans un environnement de test, sélectionnez l’option Il s’agit d’un environnement de test. Vous pourrez rapidement désactiver cette option après l’installation et tous vos tests seront effectués ultérieurement.
    Si votre instance autorise l’authentification de base pour les connexions entrantes, sélectionnez Oui, sinon, reportez-vous à [l’installation avancée avec AAD](servicenow-aad-oauth-token.md). :::image type="content" source="../../media/ServiceNow-guide/snowbasic-2.png" lightbox="../../media/ServiceNow-guide/snowbasic-2.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[Administrateur ServiceNow Entrez\] votre domaine Microsoft 365 client.

    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-3.png" lightbox="../../media/ServiceNow-guide/snowbasic-3.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[L’administrateur\] ServiceNow configure les paramètres sortants.
    1. Inscrivez l’Azure Active Directory (AAD).
    1. Après avoir suivi les instructions de la section Conditions préalables, cliquez sur **Terminé**. Sinon, suivez les instructions de l’Assistant pour créer l’inscription d’application nécessaire dans AAD.
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-4.png" lightbox="../../media/ServiceNow-guide/snowbasic-4.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

    1. Inscrivez l’application OAuth ServiceNow.
    1. Après avoir suivi les instructions de la section Conditions préalables, sélectionnez l’inscription de l’application OAuth nouvellement créée, puis cliquez sur Suivant. Sinon, suivez les instructions pour créer l’entité dans ServiceNow, puis sélectionnez la nouvelle inscription d’application.
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-5.png" lightbox="../../media/ServiceNow-guide/snowbasic-5.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[L’administrateur\] ServiceNow configure les paramètres entrants.
    1. Configurez le point de terminaison de l’API OAuth entrante.
    1. Après avoir suivi les instructions de la section Conditions préalables, sélectionnez l’inscription de l’application OAuth nouvellement créée, puis cliquez sur Terminé. Sinon, suivez les instructions pour créer l’entité, puis sélectionnez l’inscription du point de terminaison REST.
     
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-6.png" lightbox="../../media/ServiceNow-guide/snowbasic-6.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

    1. Configurez l’utilisateur d’intégration.
    1. Après avoir suivi les instructions de la section Conditions préalables, sélectionnez l’utilisateur d’intégration nouvellement créé, puis cliquez sur Suivant. Sinon, suivez les instructions pour créer l’entité dans ServiceNow, puis sélectionnez le nouvel utilisateur d’intégration.
    
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-7.png" lightbox="../../media/ServiceNow-guide/snowbasic-7.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::


1. \[Microsoft 365 client\] Terminez l’intégration dans le portail Administration Microsoft 365 web.

    Vérifiez que les informations ci-dessous sont correctes. NE sélectionnez **PAS Suivant** pour le moment.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image17.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image17.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

1. Go to **Administration Microsoft 365 Portal &gt; Paramètres &gt; Org settings &gt; Organization profiles**.

1. Configurez les paramètres d’intégration de la prise en charge :

    Sélectionnez **l’onglet** Informations de base >'outil de **support** >  **interneServiceNow**, puis entrez la valeur **de l’ID** de l’application sortante dans **l’ID d’application** pour émettre le champ Jeton auth. Cet ID d’application sortante se trouve à l’étape 6 : terminez l’intégration, qui a été créée à l’étape [1 prérequise (Authentification de \#base](#prerequisites-basic-authentication)).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Sous **l’onglet Référentiels** , sélectionnez **Nouveau** référentiel et mettez-le à jour avec les paramètres suivants :

    - Référentiel : valeur **de l’ID** de référentiel de l’étape 6 : terminer l’intégration.

    - Point de terminaison **: valeur de point** de terminaison de l’étape 6 : terminer l’intégration.

    - Type d’authentification : sélectionner **l’authentification de base**.

    - ID client : valeur **de l’ID client** de l’étape 6 : terminer l’intégration.

    - Secret client : secret du fournisseur OAuth entrant créé à l’étape 3 des conditions préalables (authentification de \#base).

    - Expiration du jeton d’actualisation : 864000

    - Nom d’utilisateur restant : valeur **du nom d’utilisateur** de l’étape 6 : terminer l’intégration.

    - Mot de passe de l’utilisateur restant : mot de passe de l’utilisateur d’intégration qui a été créé à l’étape [4 des conditions préalables (Authentification de base\#](#prerequisites-basic-authentication)).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image19.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image19.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

1. Revenir à ServiceNow.

1. **Sélectionnez Suivant** pour terminer l’intégration.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image20.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image20.png" alt-text="Interface utilisateur graphique, application, description du site web générée automatiquement":::

1. \[ServiceNow Admin\] Test the connection After completing the previous step, click **Test connection**.
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-8.png" lightbox="../../media/ServiceNow-guide/snowbasic-8.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::
    L’Microsoft 365 d’intégration de prise en charge exécutera des tests pour s’assurer que l’intégration fonctionne. En cas de problème avec la configuration, un message d’erreur explique ce qui doit être résolu. Sinon, l’application est prête.
     :::image type="content" source="../../media/ServiceNow-guide/snowbasic-9.png" lightbox="../../media/ServiceNow-guide/snowbasic-9.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[FACULTATIF\] [Utilisateur avec le lien x_mioms_m365_assis.administrator] Lien Administration Microsoft 365 compte.
    Si un utilisateur a le rôle x_mioms_m365_assis.administrator et utilise différents comptes Microsoft 365 pour gérer un cas de support Microsoft 365, il doit se rendre sur Microsoft 365 support > Link Account pour configurer son e-mail d’administrateur Microsoft 365.
    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image21.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::
