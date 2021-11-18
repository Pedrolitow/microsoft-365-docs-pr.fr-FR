---
title: Configurer l’intégration de la prise en charge Microsoft 365 avec le jeton AAD OAuth
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
ms.openlocfilehash: da241452f989ba5f682fd3219e3f3baabf623138
ms.sourcegitcommit: 7e59802f251da96ec639fb09534aa96acf5d6ce7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2021
ms.locfileid: "61071449"
---
# <a name="configure-microsoft-365-support-integration-with-aad-oauth-token"></a>Configurer l’intégration de la prise en charge Microsoft 365 avec le jeton AAD OAuth

## <a name="prerequisites-aad-oauth-token"></a>Conditions préalables (AAD jeton OAuth)

Ces conditions préalables sont nécessaires pour configurer la prise en charge Microsoft 365 l’intégration.

1. \[AAD admin \] Créez AAD application pour le trafic sortant sous votre Microsoft 365 client.

    1. Connectez-vous au portail Azure à l’Microsoft 365 vos informations d’identification client et allez sur la [page](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) d’inscription de l’application pour créer une application.

    2. Sélectionnez les comptes dans cet annuaire d’organisation **uniquement ({Microsoft-365-tenant-name} uniquement – Client unique)** et sélectionnez **Enregistrer**.

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Go to **Authentication** and select **Add a platform**. Sélectionnez **l’option Web** et entrez l’URL de redirection : `https://{your-servicenow-instance``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Obtenez l’ID client de l’application, créez une secret client et obtenez cette valeur.

1. \[AAD admin \] Créez une application AAD l’API Rest sous votre Microsoft 365 client.

    1. Connectez-vous au [portail Azure](https://portal.azure.com/) avec vos informations d’identification Microsoft 365 client et allez sur la page d’inscription de l’application pour créer une application.

    1. Sélectionnez **les comptes dans ce répertoire d’organisation uniquement {(Microsoft-365-tenant-name} uniquement – Client unique).**

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image22.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image22.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Obtenez l’ID client de l’application, créez une secret client et obtenez cette valeur.

1. \[AAD admin \] Créez une application AAD l’utilisateur Rest sous votre Microsoft 365 client.

    1. Connectez-vous au [portail Azure](https://portal.azure.com/) avec vos informations d’identification Microsoft 365 client et allez sur la page d’inscription de l’application pour créer une application.

    1. Sélectionnez **les comptes dans ce répertoire d’organisation uniquement {(Microsoft-365-tenant-name} uniquement – Client unique).**

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" lightbox="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Obtenez l’ID client de l’application, créez une secret client et obtenez cette valeur.

1. \[L’administrateur ServiceNow \] a installé le fournisseur OAuth sortant dans ServiceNow.

    Si l’étendue n’est pas définie sur **Global,** faites-le en naviguant vers **Paramètres &gt; &gt; applications** de développeur et en passant à **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Interface utilisateur graphique, texte, application, conversation ou message texte Description générés automatiquement":::

1. Go to **System OAuth &gt; Application Registry**.

1. Créez une application à **l’aide Connecter’une** option de fournisseur OAuth tierce et en entrant les valeurs ci-après :

    - ID client : il s’agit de l’ID client de l’application créée à l’étape 1 AAD (jeton OAuth). \#

    - Secret client : il s’agit de la valeur de la secret client de l’application créée à l’étape 1 AAD (jeton OAuth). \#

    - Type d’octroi par défaut : informations d’identification du client

    - URL du jeton : `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - URL de redirection : `https://{service-now-instance-name``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

1. \[Administration de ServiceNow \] Pour configurer le fournisseur OIDC dans ServiceNow, consultez la documentation en [ligne.](https://docs.servicenow.com/bundle/quebec-platform-administration/page/administer/security/task/add-OIDC-entity.html)

    Si l’étendue n’est pas définie sur **Global,** passez à **Paramètres &gt; &gt; Applications** de développeur et passez à **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Interface utilisateur graphique, texte, application, conversation ou message texte Description générés automatiquement":::

1. Go to **System OAuth &gt; Application Registry**.

1. Sélectionnez **Nouveau,** puis créez un nouvel **ID d’ouverture Connecter fournisseur.**

1. Dans la configuration du fournisseur **OAuth OIDC,** sélectionnez **Rechercher** et créez une nouvelle configuration de fournisseur OIDC sous **\_ oidc provider \_ configuration.list** avec les valeurs ci-dessous :

    - Fournisseur OIDC : **{Tenant \_ Name} Azure** (exemple : Contoso Azure)

    - URL de métadonnées OIDC : `https://login.microsoftonline.com/{microsoft-365-tenant-name}/.well-known/openid-configuration`

    - UserClaim: **appId**

    - UserField : **ID utilisateur**

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image24.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image24.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

1. Créez une application en sélectionnant Configurer un fournisseur OIDC pour vérifier les **jetons d’ID** avec les valeurs ci-après :

    - Name: **{Tenant \_ Name} \_ application \_ inbound \_ api** (example: contoso \_ application \_ inbound \_ api)

    - ID client : ID client de l’application créée dans les conditions préalables (AAD jeton OAuth) étape \# 2.

    - Secret client : secret d’application de l’application créée à l’étape 2 AAD (jeton OAuth). \#

    - Configuration du fournisseur OAuth OIDC : fournisseur OIDC créé à l’étape précédente

    - URL de redirection : `https://{service-now-instance-name}.service-now.com/oauth\_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image25.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image25.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

1. \[L’administrateur ServiceNow \] crée des utilisateurs d’intégration.

    Vous devez spécifier un utilisateur d’intégration. Si vous n’avez pas d’utilisateur d’intégration existant ou si vous **&gt;** souhaitez en créer un spécifiquement pour cette intégration, rendez-vous sur Utilisateurs de l’organisation pour créer un utilisateur. La valeur de **l’ID** d’utilisateur est l’ID client de l’application créé à [l’étape AAD (jeton OAuth) étape \# 3](#prerequisites-aad-oauth-token).

    Si vous créez un utilisateur d’intégration, vérifiez l’option **d’accès au service Web uniquement.** Vous devez également accorder à cet utilisateur le rôle **gestionnaire \_ d’incidents.**

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image26.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image26.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

## <a name="optional-allow-the-services-ip-addresses-to-microsoft-365-support-integration"></a>\[FACULTATIF Autoriser les adresses IP du service à prendre \] en charge Microsoft 365'intégration

Si votre entreprise limite l’accès à Internet avec vos propres stratégies, activez l’accès réseau pour le service de prise en charge de Microsoft 365 en permettant les adresses IP ci-dessous pour l’accès à l’API entrante et sortante.

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

1. \[ServiceNow Admin \] Switch the scope to Microsoft 365 support **integration**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image9.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image9.png" alt-text="Interface utilisateur graphique, description de tableau générée automatiquement":::

1. \[ServiceNow Admin \] Go to Microsoft 365 Support **&gt; Setup** to open the integration workflow.

    > [!NOTE]
    > Si l’erreur « Opération de lecture par rapport à l’entité oauth » de l’étendue « \_ x \_ mioms m365 assis » a été refusée en raison de la stratégie d’accès à plusieurs étendues de la table, elle est due à votre stratégie \_ d’accès à la \_ table. Vous devez vous assurer **que toutes les étendues d’application &gt;** lues sont vérifiées pour l’entité oauth \_ de table.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image27.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image27.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[Sélection de l’administrateur ServiceNow \] **Acceptez** l’invite de consentement pour continuer.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image11.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image11.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[L’administrateur ServiceNow \] a installé le fournisseur OAuth sortant.

    Sélectionnez le profil OAuth pour le fournisseur OAuth sortant créé à l’étape [ \# 4 prérequise (AAD OAuth Token),](#prerequisites-aad-oauth-token)puis sélectionnez **Suivant.**

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image12.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image12.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[L’administrateur ServiceNow \] a installé le fournisseur OAuth entrant.

    1. Décochez **Ignorer l’étape actuelle.**

    1. Vérifier **le jeton d’OIDC externe auth**.

    1. Sélectionnez le client OAuth créé dans les conditions préalables (AAD jeton [OAuth) étape \# 5,](#prerequisites-aad-oauth-token)puis sélectionnez **Suivant**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image28.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image28.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

1. \[L’administrateur ServiceNow \] a installé l’utilisateur d’intégration des appels entrants.

    1. Décochez **Ignorer l’étape actuelle.**

    1. Entrez **l’ID client** de l’application qui a été créée dans les conditions préalables (AAD jeton [OAuth) étape \# 3,](#prerequisites-aad-oauth-token)puis sélectionnez **Suivant**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image39.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image39.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[ServiceNow Admin \] Set up the Repository ID.

    Spécifiez l’ID de référentiel, puis sélectionnez **Suivant**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image15.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image15.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

1. \[ServiceNow Admin \] Set up Application Paramètres.

    Sélectionnez les paramètres suivants, puis sélectionnez **Suivant**.

    - SSO avec Microsoft 365 : vérifiez si l’instance ServiceNow est définie en tant qu’OS avec Microsoft 365 clients, sinon décochez-la.

    - Microsoft 365 e-mail de l’administrateur : adresse de messagerie Microsoft 365'administrateur qui est contacté lors de la création Microsoft 365 de support technique.

    - Environnement de test : cochez la case pour indiquer une phase de test afin d’éviter que les agents du support Microsoft ne vous contactent pour résoudre le problème. Si vous êtes prêt à passer officiellement à l’étape Microsoft 365 l’intégration, décochez la case.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image16.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image16.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

1. \[Microsoft 365 client \] Terminez l’intégration.

    Vérifiez que les informations ci-dessous sont correctes. NE sélectionnez **PAS Suivant** pour le moment.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image40.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image40.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Go to **Administration Microsoft 365 Portal Paramètres Org &gt; &gt; settings Organization &gt; profiles**.

1. Configurez les paramètres d’intégration de la prise en charge :

    Sélectionnez **l’onglet** Informations de base >'outil de support interne ServiceNow, puis entrez la valeur de l’ID de l’application sortante dans l’ID d’application pour émettre le champ de jeton  >   **OAuth.**  Cet ID d’application sortante se trouve à l’étape 6 : terminer l’intégration, qui a été créée à l’étape [ \# 1 AAD (jeton OAuth)](#prerequisites-aad-oauth-token).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Sous **l’onglet Référentiels,** sélectionnez **Nouveau** référentiel et mettez-le à jour avec les paramètres suivants :

    - Référentiel : valeur **de l’ID** de référentiel de « Étape 6 : Terminer l’intégration ».

    - Point de terminaison : valeur **de point** de terminaison de « Étape 6 - Terminer l’intégration ».

    - Type d’authentification **: sélectionnez AAD auth**.

    - ID client : valeur **de l’ID client** de l’étape 6 : terminer l’intégration.

    - Secret client : secret du fournisseur OAuth entrant créé à l’étape 2 des conditions préalables (AAD \# OAuth).

    - Nom d’utilisateur restant : valeur du nom d’utilisateur de l’étape 6 : terminer l’intégration, qui est l’ID **client** de l’application créée à l’étape 3 des conditions préalables (jeton OAuth  \# AAD).

    - Mot de passe de l’utilisateur rest : secret d’application de l’application créée à l’étape 3 AAD (jeton OAuth). \#

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image31.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image31.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

1. Revenir à ServiceNow.

1. Sélectionnez **Suivant** pour terminer l’intégration.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image32.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image32.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

1. \[L’administrateur ServiceNow \] active l’intégration du support Microsoft pour un utilisateur existant.

    Microsoft 365 prise en charge de l’intégration est activée pour l’utilisateur avec l’un des rôles ci-après :

    - utilisateur \_ x mioms \_ m365 \_ assis.insights \_

    - x \_ mioms \_ m365 \_ assis.administrator

1. \[FACULTATIF \] \[ L’utilisateur avec le rôle x \_ mioms \_ m365 \_ assis.administrator lien Microsoft 365 compte \] d’administrateur.

    Si un utilisateur a le rôle x \_ mioms \_ m365 \_ assis.administrator et utilise différents comptes Microsoft 365 pour gérer un cas de support Microsoft 365, il doit se rendre sur le compte de lien de support Microsoft 365 pour configurer son e-mail d’administrateur &gt; Microsoft 365.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image21.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image21.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::
