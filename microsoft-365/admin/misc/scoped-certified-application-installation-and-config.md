---
title: Guide de configuration et d’installation d’applications certifiées étendues
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: Guide de configuration et d’installation d’applications certifiées étendues pour ServiceNow.
ms.openlocfilehash: 0bac2a0c12c1997627da77419a7b47d6cd4c74cb
ms.sourcegitcommit: f358e321f7e81eff425fe0f0db1be0f3348d2585
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2021
ms.locfileid: "58508456"
---
# <a name="scoped-certified-application-installation-and-configuration-guide"></a>Guide de configuration et d’installation d’applications certifiées étendues

[Vue d’ensemble](#overview) 

[Dépendances d’application dans les environnements ServiceNow](#application-dependencies-in-servicenow-environments)

[Instructions de configuration](#configuration-instructions)

[Qui pouvez configurer la prise en charge Microsoft 365'intégration ?](#who-can-set-up-microsoft-365-support-integration)

[Quelles fonctionnalités sont disponibles dans Microsoft 365 l’intégration ?](#what-features-are-available-in-microsoft-365-support-integration) 

[Configurer l’Microsoft 365 prise en charge de l’intégration avec l’authentification de base ServiceNow](#set-up-microsoft-365-support-integration-with-servicenow-basic-authentication)

[Configurer l’Microsoft 365 prise en charge de l’intégration avec le jeton OAuth AAD](#set-up-microsoft-365-support-integration-with-aad-oauth-token)

[Configurer l’intégration Microsoft 365 prise en charge pour Informations UNIQUEMENT](#set-up-microsoft-365-support-integration-for-insights-only) 

[Test de la configuration](#testing-the-configuration) 

[Résolution des problèmes](#troubleshooting) 

## <a name="overview"></a>Vue d’ensemble

Microsoft 365'intégration du support technique vous permet d’intégrer Microsoft 365 aide, support et état du service à ServiceNow. Vous pouvez effectuer des recherches sur les problèmes connus et signalés par Microsoft, résoudre les incidents et effectuer des tâches à l’aide des solutions recommandées par Microsoft et, si nécessaire, faire appel au support technique de Microsoft.

## <a name="application-dependencies-in-servicenow-environments"></a>Dépendances d’application dans les environnements ServiceNow

Autorisations requises :

- entité \_ oauth

- Profil \_ d’entité oauth \_

Une fois Microsoft 365'intégration de support technique a été installée, deux accès d’étendues croisées d’applications ont été créés. S’ils ne sont pas créés correctement pour une raison quelconque, créez-les manuellement.

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image1.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

## <a name="configuration-instructions"></a>Instructions de configuration

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image2.png" alt-text="Description du diagramme générée automatiquement":::

Pour configurer l’Microsoft 365 l’intégration :

- Inscrivez des applications dans Microsoft Azure Active Directory (AAD) pour l’authentification des appels d’API entrants et sortants.

- Créez des entités ServiceNow avec des applications Microsoft AAD pour le flux de données sortant et entrant.

- Intégrer l’instance ServiceNow à la prise en charge de Microsoft via Administration Microsoft 365 Portal.

## <a name="who-can-set-up-microsoft-365-support-integration"></a>Qui pouvez configurer l’intégration Microsoft 365 prise en charge ?

- Toute personne autorisée à créer des applications AAD.

- Un administrateur ServiceNow.

- Un administrateur du service d’aide ou un administrateur de demande de service Microsoft 365 clients.

## <a name="what-features-are-available-in-microsoft-365-support-integration"></a>Quelles fonctionnalités sont disponibles dans Microsoft 365 l’intégration ?

Avant de définir une configuration pour Microsoft 365 l’intégration, examinez vos réponses à ces questions :

**Question #1** Votre environnement ServiceNow autorise-t-il l’authentification de base (accès avec les informations d’identification de l’utilisateur ServiceNow) pour les appels de service web entrants ?

**Question #2** Si vous avez plusieurs clients, envisagez-vous d’utiliser un seul client intégré à votre environnement ServiceNow pour l’intégration Microsoft 365 prise en charge ?

Ce tableau identifie les fonctionnalités à votre disposition en fonction des réponses à ces questions et des liens vers les instructions spécifiques sur la façon de configurer Microsoft 365 l’intégration. Pour obtenir une description de chaque fonctionnalité, voir [Microsoft 365'intégration de prise en charge.](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f)

|Question #1 réponse|Question #2 réponse|Quelles fonctionnalités sont disponibles ?|Étapes de configuration|
|--- |--- |--- |--- |
|Oui|Oui|Incidents d’état du service <br/>Solutions recommandées </br>Demande de service Microsoft|[Configurer l’Microsoft 365 prise en charge de l’intégration avec l’authentification de base ServiceNow](#set-up-microsoft-365-support-integration-with-servicenow-basic-authentication)|
|Oui|Non|Incidents d’état du service <br/>Solutions recommandées </br>Demande de service Microsoft||
|Non|Oui|Incidents d’état du service <br/>Solutions recommandées </br>Demande de service Microsoft|[Configurer l’Microsoft 365 prise en charge de l’intégration avec le jeton OAuth AAD](#set-up-microsoft-365-support-integration-with-aad-oauth-token)|
|Non|Non|Incidents d’état du service <br/>Solutions recommandées|[Configurer l’intégration Microsoft 365 prise en charge pour Informations UNIQUEMENT](#set-up-microsoft-365-support-integration-for-insights-only) |

## <a name="set-up-microsoft-365-support-integration-with-servicenow-basic-authentication"></a>Configurer l’Microsoft 365 prise en charge de l’intégration avec l’authentification de base ServiceNow

### <a name="prerequisites-basic-authentication"></a>Conditions préalables (Authentification de base)

Certaines conditions préalables sont nécessaires pour configurer la prise en charge Microsoft 365 l’intégration.

1. \[La personne qui peut créer des applications AAD \] Créez une application AAD sous votre Microsoft 365 client.

    1. Connectez-vous au [portail Azure avec](https://portal.azure.com/) vos informations d Microsoft 365 client.

    1. Go to the App registrations page and create a new application.

        Sélectionnez **les comptes dans cet annuaire d’organisation uniquement ({TenantName} uniquement – Client unique**.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image3.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

    1. Ajouter une URL de redirection `https://&lt;your-servicenow-instance&gt;.service-now.com/oauth\_redirect.do` : .

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image4.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

    1. Obtenez l’ID client de l’application et créez une secret d’application.

2. \[La personne qui est un administrateur ServiceNow a installé le fournisseur \] OAuth sortant dans ServiceNow.

    1. Go to **System OAuth**  >  **Application Registry**.

    1. Si l’étendue n’est pas définie sur **Global,** **ouvrez Paramètres**  >    >  **applications** de développeur pour basculer vers **Global**.

     :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image5.png" alt-text="Interface utilisateur graphique, texte, application, conversation ou message texte Description générés automatiquement":::

    1. Créez une application avec les valeurs suivantes en sélectionnant Connecter à un fournisseur [OAuth tiers.](https://dev77417.service-now.com/wizard_view.do?sys_action=sysverb_wizard_ans&WIZARD:action=follow&wiz_referring_url=oauth_entity_list.do?sys_id=-1@99@sys_target=oauth_entity@99@sysparm_fixed_query=@99@sysparm_group_sort=@99@sysparm_parent=2c7cab53d7232100f20bc8170e61036b@99@sysparm_query=type%3dclient%5eORtype%3doauth_provider@99@sysparm_target=@99@sysparm_view=&wiz_collection_key=&wiz_collectionID=&wiz_collection=&wiz_collection_related_field=&wiz_view=&wiz_action=sysverb_new&sys_id=79ce2f53d7232100f20bc8170e610361&sysparm_query=type=client%5eORtype=oauth_provider&sysparm_target=&sys_target=oauth_entity)

    - ID client : ID client de l’application créée à \# l’étape 1

    - Secret client : secret d’application de l’application créée à \# l’étape 1

    - Type d’octroi par défaut : Informations d’identification client

    - URL du jeton : `https://login.microsoftonline.com/{M365\_Tenant\_Name}/oauth2/token`

    - URL de redirection :

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image6.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

3. \[La personne qui est un administrateur ServiceNow \] a installé le fournisseur OAuth entrant.

    1. Go to **System OAuth**  >  **Application Registry**.

    1. Si l’étendue n’est pas définie sur **Global,** **ouvrez Paramètres**  >    >  **applications** de développeur pour basculer vers **Global**.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image5.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

    1. Créez une application en sélectionnant Créer un point de **terminaison d’API OAuth pour les clients externes.** Nommez le fournisseur OAuth entrant et laissez les autres champs à leurs valeurs par défaut.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image7.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

4. \[La personne qui est un administrateur ServiceNow crée \] des utilisateurs d’intégration.

    Vous devez spécifier un utilisateur d’intégration. Si vous n’avez pas d’utilisateur d’intégration existant ou si vous souhaitez en créer un spécifique, rendez-vous sur Utilisateurs de l’organisation pour créer  >   un utilisateur.

    Si vous créez un utilisateur d’intégration, cochez la case Accès **au service Web uniquement.**

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image8.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

### <a name="optional-whitelist-the-services-ips-of-microsoft-365-support-integration"></a>\[Liste \] blanche facultative des adresses IP du service Microsoft 365 l’intégration

Si votre entreprise limite l’accès à Internet avec vos propres stratégies, activez l’accès réseau pour le service de prise en charge de Microsoft 365 en sélectionnant les adresses IP ci-dessous pour l’accès à l’API entrante et sortante.

- 52.149.152.32

- 40.83.232.243

- 40.83.114.39

- 13.76.138.31

- 13.79.229.170

- 20.105.151.142

> [!NOTE]
> Cette commande terminal répertorie toutes les IP actives du service pour Microsoft 365 l’intégration de la prise en charge :`nslookup connector.rave.microsoft.com`

### <a name="set-up-microsoft-365-support-integration-application"></a>Configurer l’application Microsoft 365 prise en charge de l’intégration

L’Microsoft 365'intégration de support technique peut être définie sous Microsoft 365 prise en charge.

Ces étapes sont nécessaires pour configurer l’intégration entre votre instance ServiceNow et Microsoft 365 prise en charge.

1. \[La personne qui est un administrateur ServiceNow basculez l’étendue vers \] Microsoft 365 l’intégration.

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image9.png" alt-text="Interface utilisateur graphique, description de tableau générée automatiquement":::

2. \[La personne qui est un administrateur ServiceNow est Microsoft 365 prendre en charge > \] **le programme d’installation** pour ouvrir le flux d’intégration.

    > [!NOTE]
    > Si l’erreur « Opération de lecture par rapport à l’entité oauth » de l’étendue « \_ x \_ mioms m365 assis » a été refusée en raison de la stratégie d’accès entre étendues de la table, elle est due à votre stratégie \_ d’accès à la \_ table. Vous devez vous assurer **que toutes les étendues d’application** lues sont vérifiées pour l’entité  >   oauth \_ de table.

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image10.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

3. \[La personne qui est un administrateur ServiceNow \] **sélectionnez Accepter** d’accepter le consentement

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image11.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

4. \[La personne qui est un administrateur ServiceNow \] a installé le fournisseur OAuth sortant.

    Sélectionnez le profil OAuth pour le fournisseur OAuth sortant créé à l’étape 2 Conditions [préalables (Authentification](#prerequisites-basic-authentication) de base) et \# sélectionnez **Suivant**.

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image12.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

5. \[La personne qui est un administrateur ServiceNow \] a installé le fournisseur OAuth entrant.

- Décochez **Ignorer l’étape actuelle.**

- Décochez **le jeton d’OIDC externe.**

- Sélectionnez le client OAuth créé dans les [conditions préalables (Authentification](#prerequisites-basic-authentication) de base) étape \# 3 et sélectionnez **Suivant**.

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image13.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

6. \[La personne qui est un administrateur ServiceNow Configurer \] l’utilisateur d’intégration des appels entrants.

- Décochez **Ignorer l’étape actuelle.**

- Sélectionnez l’utilisateur d’intégration créé à l’étape 4 [conditions préalables (Authentification](#prerequisites-basic-authentication) de base), \# puis sélectionnez **Suivant.**

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image13.png" alt-text="Interface utilisateur graphique, texte, description d’application générés automatiquement":::

7. \[La personne qui est un ID de référentiel de configurer l’administrateur \] ServiceNow.

Spécifiez l’ID de référentiel, puis sélectionnez **Suivant**.

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image14.png" alt-text="Interface utilisateur graphique, texte, description d’application générés automatiquement":::

8. \[La personne qui est un administrateur ServiceNow \] a installé les paramètres de l’application.

Sélectionnez les paramètres suivants, puis sélectionnez **Suivant**.

- SSO avec Microsoft 365 : vérifiez si l’instance ServiceNow est définie en tant qu’OS avec Microsoft 365 clients, sinon décochez-la.

- Microsoft 365 courrier électronique de l’administrateur : adresse électronique de l Microsoft 365'administrateur qui est contacté lors Microsoft 365 cas de support sont créés.

- Environnement de test : cochez la case pour indiquer une phase de test afin d’éviter que les agents du support Microsoft ne vous contactent pour résoudre le problème. Si vous êtes prêt à passer officiellement à l’étape Microsoft 365 l’intégration, décochez la case.

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image16.png" alt-text="Interface utilisateur graphique, texte, description d’application générés automatiquement":::

9. \[La personne qui est administrateur du service d’aide ou administrateur de demande de service dans Microsoft 365 client complète \] l’intégration.

    1. Vérifiez les informations ci-dessous pour vous assurer qu’elles sont correctes.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image17.png" alt-text="Interface utilisateur graphique, texte, description d’application générés automatiquement":::

    1. Go to Microsoft 365 [Admin Portal](https://admin.microsoft.com/)  >  **Paramètres**  >  **Paramètres**  >  **Organization profiles**.

    1. Configurer les paramètres d’intégration de prise en charge :

        1. Dans  l’onglet Informations de base, sélectionnez l’outil de support interne **Service Now** et tapez L’ID de l’application sortante comme valeur de l’ID d’application dans la page Étape - 6 Terminé, qui a été créé à l’étape 1 Des conditions [préalables (Authentification](#prerequisites-basic-authentication) de  \# base).

            :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image18.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

        1. Dans l’onglet **Référentiels,** **sélectionnez** Ajouter un référentiel pour créer un référentiel avec les paramètres suivants :

        - Référentiel : valeur **de l’ID** du référentiel à partir de l’étape de page - 6 Terminer l’intégration.

        - Point de terminaison : valeur **de point** de terminaison de l’étape de page - 6 Terminer l’intégration.

        - Type d’authentification : sélectionner **l’authentification de base.**

        - ID client : valeur **de l’ID client** de l’étape de la page - 6 Terminer l’intégration.

        - Secret client : secret du fournisseur OAuth entrant créé à l’étape 3 des conditions [préalables](#prerequisites-basic-authentication) \# (authentification de base).

        - Expiration du jeton d’actualisation : 864000

        - Nom d’utilisateur restant : valeur **nom d’utilisateur** de l’étape de la page - 6 Terminer l’intégration.

        - Mot de passe de l’utilisateur restant : mot de passe de l’utilisateur d’intégration qui a été créé à l’étape 4 des [conditions préalables](#prerequisites-basic-authentication) \# (Authentification de base).

            :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image19.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

        1. Revenir en arrière et sélectionnez le bouton pour enregistrer l’intégration.

    1. Sélectionnez **Suivant** pour terminer l’intégration.

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image20.png" alt-text="Interface utilisateur graphique, application, description du site web générée automatiquement":::

10. \[La personne qui est un administrateur ServiceNow active \] Microsoft 365 l’intégration d’un utilisateur existant.

Microsoft 365'intégration de la prise en charge est activée uniquement pour l’utilisateur ayant l’un des rôles ci-après :

- [utilisateur \_ x mioms \_ m365 \_ assis.insights \_](https://ven01306.service-now.com/sys_user_role.do?sys_id=802b2adfdb4cac507c80230bd3961911&sysparm_record_target=sys_user_role&sysparm_record_row=2&sysparm_record_rows=2&sysparm_record_list=nameSTARTSWITHx_mioms_m365%5EORDERBYname)

- [x \_ mioms \_ m365 \_ assis.administrator](https://ven01306.service-now.com/sys_user_role.do?sys_id=4b25c9fb1b7784507ddd4227cc4bcb3a&sysparm_record_target=sys_user_role&sysparm_record_row=1&sysparm_record_rows=2&sysparm_record_list=nameSTARTSWITHx_mioms_m365%5EORDERBYname)

> [!NOTE]
> L’utilisateur ayant le rôle x \_ mioms \_ m365 assis.insights peut voir Incidents d’état du \_ \_ service, Solutions recommandées. L’utilisateur avec le rôle x \_ mioms \_ m365 assis.administrator peut également ouvrir un cas \_ avec Microsoft 365 prise en charge.

11. \[Facultatif \] \[ La personne qui est un lien d’administration ServiceNow \] Administration Microsoft 365 compte.

Si un utilisateur a le rôle x \_ mioms \_ m365 assis.administrator et utilise différents comptes Microsoft 365 pour gérer un cas de support Microsoft 365, il doit se rendre sur Microsoft 365 support > Link Account pour configurer son e-mail d’administrateur \_ Microsoft 365.

 :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image21.png" alt-text="Interface utilisateur graphique, texte, description d’application générés automatiquement":::

## <a name="set-up-microsoft-365-support-integration-with-aad-oauth-token"></a>Configurer l’Microsoft 365 prise en charge de l’intégration avec le jeton OAuth AAD

### <a name="prerequisites-aad-oauth-token"></a>Prerequisites (jeton OAuth AAD)

Ces étapes préalables sont nécessaires pour configurer la prise en charge Microsoft 365'intégration :

1. \[La personne qui peut créer des applications AAD crée une application AAD pour le trafic sortant \] sous votre Microsoft 365 client.

    1. Connectez-vous [au portail Azure avec](https://portal.azure.com/) Microsoft 365 d’identification client.

    1. Go to the **App registrations** page and create a new application.

        Sélectionnez **les comptes dans cet annuaire d’organisation uniquement ({TenantName} uniquement – Client unique**.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image3.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

    1. Ajoutez une URL de redirection : `https://&lt;your-servicenow-instance&gt;.service-now.com/auth\_redirect.do`

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image4.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

    1. Obtenez l’ID client de l’application et créez la secret de l’application.

2. \[Personne qui peut créer des applications AAD Créer une application AAD pour \] l’API Rest sous votre Microsoft 365 client.

    1. Connectez-vous au [portail Azure avec](https://portal.azure.com/) vos informations d Microsoft 365 client.

    1. Go to **App registrations** and create a new application.

        Sélectionnez **les comptes dans cet annuaire d’organisation uniquement ({TenantName} uniquement – Client unique**.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image22.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

    1. Obtenez l’ID client de l’application et créez la secret de l’application.

3. \[La personne qui peut créer des applications AAD \] Créez une application AAD pour l’utilisateur Rest sous votre Microsoft 365 client.

    1. Connectez-vous au [portail Azure avec](https://portal.azure.com/) vos informations d Microsoft 365 client.

    1. Go to the **App registrations** page and create a new application.
    1. Sélectionnez **les comptes dans cet annuaire d’organisation uniquement ({TenantName} uniquement – Client unique**.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

    1. Obtenez l’ID client de l’application et créez une secret d’application.

4. \[La personne qui est un administrateur ServiceNow a installé le fournisseur \] OAuth sortant dans ServiceNow.

    1. Go to **System OAuth**  >  **Application Registry**.

    2. Si l’étendue n’est pas définie sur **Global,** **ouvrez Paramètres**  >    >  **applications** de développeur pour basculer vers **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image5.png" alt-text="Interface utilisateur graphique, texte, application, conversation ou message texte Description générés automatiquement":::

    3. Créez une application avec les valeurs ci-dessous en sélectionnant Connecter à un fournisseur [OAuth tiers.](https://dev77417.service-now.com/wizard_view.do?sys_action=sysverb_wizard_ans&WIZARD:action=follow&wiz_referring_url=oauth_entity_list.do?sys_id=-1@99@sys_target=oauth_entity@99@sysparm_fixed_query=@99@sysparm_group_sort=@99@sysparm_parent=2c7cab53d7232100f20bc8170e61036b@99@sysparm_query=type%3dclient%5eORtype%3doauth_provider@99@sysparm_target=@99@sysparm_view=&wiz_collection_key=&wiz_collectionID=&wiz_collection=&wiz_collection_related_field=&wiz_view=&wiz_action=sysverb_new&sys_id=79ce2f53d7232100f20bc8170e610361&sysparm_query=type=client%5eORtype=oauth_provider&sysparm_target=&sys_target=oauth_entity)

        - ID client : ID client de l’application créée à l’étape 1 des conditions [préalables (jeton OAuth AAD).](#prerequisites-aad-oauth-token) \#

        - Secret client : secret d’application de l’application créée à l’étape 1 des conditions [préalables (jeton OAuth AAD).](#prerequisites-aad-oauth-token) \#

        - Type d’octroi par défaut : Informations d’identification du client.

        - URL du jeton : `https://login.microsoftonline.com/{M365\_Tenan\_Name}/oauth2/token`

        - URL de redirection :

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image6.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

5. \[La personne qui est un administrateur ServiceNow \] Configure OIDC provider in ServiceNow, refer to the [online documentation](https://docs.servicenow.com/bundle/quebec-platform-administration/page/administer/security/task/add-OIDC-entity.html), otherwise go to step 7.

    1. Go to **System OAuth**  >  **Application Registry**.

    1. Si l’étendue n’est pas définie sur **Global,** **ouvrez Paramètres**  >    >  **applications** de développeur pour basculer vers **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image5.png" alt-text="Interface utilisateur graphique, texte, application, conversation ou message texte Description générés automatiquement":::

    1. Sélectionnez   >  **Créer un nouveau fournisseur d’Connecter Open ID.**

    1. Dans la configuration du fournisseur **OAuth OIDC,** sélectionnez Rechercher et créez une configuration de fournisseur OIDC sous « oidc provider configuration.list » avec les valeurs  \_ \_ ci-dessous :

    - Fournisseur OIDC : Contoso Azure

    - URL de métadonnées OIDC : `https://login.microsoftonline.com/{tenant\_name}/.well-known/openid-configuration`

    - UserClaim: **appId**

    - Champ Utilisateur : **ID utilisateur**

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image24.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

    1. Créez une application en sélectionnant Configurer un fournisseur OIDC pour vérifier les **jetons d’ID** avec les valeurs ci-après :

    - Name: contoso \_ application \_ inbound \_ api

    - ID client : ID client de l’application créée à l’étape 2 [prerequisites (jeton OAuth AAD).](#prerequisites-aad-oauth-token) \#

    - Secret client : secret d’application de l’application créée à l’étape 2 des conditions [préalables (jeton OAuth AAD).](#prerequisites-aad-oauth-token) \#

    - Configuration du fournisseur OAuth OIDC : fournisseur OIDC créé à la dernière étape.

    - URL de redirection :  
        `https://{service\_now\_instance}.service-now.com/oauth\_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image25.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

6. \[La personne qui est un administrateur ServiceNow crée \] des utilisateurs d’intégration.

    Accédez à  >  **Utilisateurs de l’organisation** pour créer un utilisateur s’il n’y a pas d’utilisateur d’intégration. La valeur de **l’ID** utilisateur est l’ID client de l’application créé à l’étape [Prérequis (jeton OAuth AAD)](#prerequisites-aad-oauth-token) \# 3

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image26.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

### <a name="optional-whitelist-the-services-ips-of-microsoft-365-support-integration"></a>\[Liste \] blanche facultative des adresses IP du service Microsoft 365 l’intégration

Si votre entreprise limite l’accès à Internet avec vos propres stratégies, activez l’accès réseau pour le service de Microsoft 365 prise en charge de l’intégration en sélectionnant ces adresses IP pour l’accès à l’API entrante et sortante :

- 52.149.152.32

- 40.83.232.243

- 40.83.114.39

- 13.76.138.31

- 13.79.229.170

- 20.105.151.142

> [!NOTE]
> Cette commande terminal répertorie toutes les IP actives du service pour l’intégration Microsoft 365 prise en charge : *nslookup connector.rave.microsoft.com*

### <a name="set-up-microsoft-365-support-integration"></a>Configurer l’intégration Microsoft 365 prise en charge

L Microsoft 365'application d’intégration de support technique peut être configurée via le **programme d’installation** sous la Microsoft 365 prise en charge.

Ces étapes sont nécessaires pour configurer l’intégration entre votre instance ServiceNow et Microsoft 365 prise en charge.

1. \[La personne qui est un administrateur ServiceNow basculez l’étendue vers \] Microsoft 365 l’intégration.

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image9.png" alt-text="Interface utilisateur graphique, description de tableau générée automatiquement":::

2. \[La personne qui est un administrateur ServiceNow est Microsoft 365 prendre en charge > \] **le programme d’installation** pour ouvrir le flux d’intégration.

> [!NOTE]
> Si l’erreur « Opération de lecture par rapport à l’entité oauth » de l’étendue « \_ x \_ mioms m365 assis » a été refusée en raison de la stratégie d’accès à plusieurs étendues de la table, elle est due à votre stratégie \_ d’accès à la \_ table. Vous devez vous assurer **que toutes les étendues d’application** lues sont vérifiées pour l’entité  >   oauth \_ de table.

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image27.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

3. \[La personne qui est un administrateur ServiceNow \] **sélectionnez Accepter** d’accepter le consentement.

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image11.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

4. \[La personne qui est un administrateur ServiceNow \] a installé le fournisseur OAuth sortant.

Sélectionnez le profil OAuth pour le fournisseur OAuth sortant créé à l’étape 4 [prerequisites (AAD OAuth Token)](#prerequisites-aad-oauth-token) et \# sélectionnez **Suivant**.

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image12.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

5. \[La personne qui est un administrateur ServiceNow \] a installé le fournisseur OAuth entrant.

    1. Décochez **Ignorer l’étape actuelle.**

    1. Vérifier **le jeton d’OIDC externe auth**.

    1. Sélectionnez le client OAuth créé à l’étape 5 des conditions [préalables (jeton OAuth AAD),](#prerequisites-aad-oauth-token) puis sélectionnez **Suivant.**

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image28.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

6. \[La personne qui est un administrateur ServiceNow a \] installé l’utilisateur d’intégration des appels entrants.

    1. Décochez **Ignorer l’étape actuelle.**

    1. Entrez l’ID client de l’application créée à l’étape 3 [prerequisites (jeton OAuth AAD)](#prerequisites-aad-oauth-token) et \# sélectionnez **Suivant**.

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image29.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

7. \[La personne qui est un administrateur ServiceNow \] a installé l’ID de référentiel.

    Spécifiez l’ID de référentiel et sélectionnez **Suivant.**

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image15.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

8. \[La personne qui est un administrateur ServiceNow \] Configurer l’application Paramètres.

    Sélectionnez les paramètres ci-après :

    1. SSO avec Microsoft 365 : cochez la case si l’instance ServiceNow est en cours d’installation avec Microsoft 365 clients ; Sinon, décochez-le.

    1. Microsoft 365 e-mail de l’administrateur : adresse électronique de l Microsoft 365'administrateur à contacter lors de la création Microsoft 365 de support technique.

    1. Environnement de test : cochez la case pour indiquer une phase de test afin d’éviter que les agents du support Microsoft ne vous contactent pour résoudre le problème. Si vous êtes prêt à passer officiellement à l’étape Microsoft 365 l’intégration, décochez la case.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image16.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

    1. Sélectionnez **Suivant**.

9. \[La personne qui est administrateur du service d’aide ou administrateur de demande de service dans Microsoft 365 client complète \] l’intégration.

    1. Vérifiez les informations suivantes pour vous assurer qu’elles sont correctes.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image30.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

    1. Go to Microsoft 365 [Admin Portal](https://admin.microsoft.com)  >  **Paramètres**  >  **Paramètres**  >  **Organization profiles**.

    1. Configurer les paramètres d’intégration de prise en charge.

        1. Sous  l’onglet Informations de base, sélectionnez **Service Maintenant** en tant qu’outil de support interne, puis tapez ID d’application sortante comme valeur de l’ID d’application dans la page Étape - 6 Terminée, qui a été créée à l’étape 1 des conditions  [préalables (jeton OAuth AAD).](#prerequisites-aad-oauth-token) \#

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image18.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

    1. Sous **l’onglet Référentiels,** **sélectionnez** Ajouter un référentiel pour créer un référentiel avec les informations suivantes :

    - Référentiel : utilisez la valeur **de l’ID** de référentiel de l’étape - 6 Terminer la page d’intégration.

    - Point de terminaison : valeur **de point** de terminaison de l’étape - 6 Terminer la page d’intégration.

    - Type d’authentification : **sélectionnez l’authentification AAD.**

    - ID client : valeur de **l’ID client** à l’étape 6 Terminez la page d’intégration, qui est l’ID client de l’application créée à l’étape 2 des conditions [préalables (jeton OAuth AAD).](#prerequisites-aad-oauth-token) \#

    - Nom d’utilisateur restant : valeur du nom d’utilisateur à l’étape 6 Terminez la page d’intégration, qui est l’ID **client** de l’application créée à l’étape 3 des conditions  [préalables (jeton OAuth AAD).](#prerequisites-aad-oauth-token) \#

    - Mot de passe de l’utilisateur rest : secret d’application de l’application créée à l’étape 3 des conditions [préalables (jeton OAuth AAD).](#prerequisites-aad-oauth-token) \#

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image31.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

    1. Revenir en arrière et sélectionnez le bouton pour enregistrer l’intégration.

    1. Sélectionnez **Suivant** pour terminer l’intégration.

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image32.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

10. \[La personne qui est un administrateur ServiceNow active \] Microsoft 365 l’intégration d’un utilisateur existant.

Microsoft 365'intégration de la prise en charge est activée uniquement pour les utilisateurs ayant les rôles suivants :

- [utilisateur \_ x mioms \_ m365 \_ assis.insights \_](https://ven01306.service-now.com/sys_user_role.do?sys_id=802b2adfdb4cac507c80230bd3961911&sysparm_record_target=sys_user_role&sysparm_record_row=2&sysparm_record_rows=2&sysparm_record_list=nameSTARTSWITHx_mioms_m365%5EORDERBYname)

- [x \_ mioms \_ m365 \_ assis.administrator](https://ven01306.service-now.com/sys_user_role.do?sys_id=4b25c9fb1b7784507ddd4227cc4bcb3a&sysparm_record_target=sys_user_role&sysparm_record_row=1&sysparm_record_rows=2&sysparm_record_list=nameSTARTSWITHx_mioms_m365%5EORDERBYname)

> [!NOTE]
> L’utilisateur avec le rôle x \_ mioms \_ m365 assis.insights peut voir Incidents d’état du \_ \_ service, Solutions recommandées. L’utilisateur avec le rôle x \_ mioms \_ m365 assis.administrator peut également ouvrir un cas \_ avec Microsoft 365 prise en charge.

11. **\[Facultatif La personne qui est un compte de lien \] \[ d’administration ServiceNow \] Administration Microsoft 365 compte**

Si un utilisateur a le rôle « x \_ mioms m365 assis.administrator » et qu’il utilise différents comptes Microsoft 365 pour gérer les cas de support Microsoft, il doit se rendre sur le support Microsoft 365 > Link Account pour configurer son e-mail \_ \_ d’administrateur Microsoft 365.

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image21.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

## <a name="set-up-microsoft-365-support-integration-for-insights-only"></a>Configurer l’intégration Microsoft 365 prise en charge pour Informations UNIQUEMENT

### <a name="prerequisites-insights-only"></a>Conditions préalables (Informations UNIQUEMENT)

Ces étapes préalables sont nécessaires pour configurer la prise en charge Microsoft 365 l’intégration :

1. \[La personne qui peut créer des applications AAD \] Créez une application AAD sous votre Microsoft 365 client.

    1. Connectez-vous au [portail Azure avec](https://portal.azure.com/) vos informations d Microsoft 365 client.

    1. Go to the **App registrations** page and create a new application.

    1. Sélectionnez **les comptes dans cet annuaire d’organisation uniquement ({TenantName} uniquement – Client unique**.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image3.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

    1. Ajoutez une URL de redirection : `https://&lt;your-servicenow-instance&gt;.service-now.com/auth\_redirect.do`

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image4.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

    1. Obtenez l’ID client de l’application et créez une secret d’application.

1. \[La personne qui est un administrateur ServiceNow a installé le fournisseur \] OAuth sortant dans ServiceNow.

    1. Go to **System OAuth**  >  **Application Registry**.

    1. Si l’étendue n’est pas définie sur **Global,** **ouvrez Paramètres**  >    >  **applications** de développeur pour basculer vers **Global**.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image5.png" alt-text="Interface utilisateur graphique, texte, application, conversation ou message texte Description générés automatiquement":::

    1. Créez une application avec les valeurs ci-dessous en sélectionnant Connecter à un fournisseur [OAuth tiers.](https://dev77417.service-now.com/wizard_view.do?sys_action=sysverb_wizard_ans&WIZARD:action=follow&wiz_referring_url=oauth_entity_list.do?sys_id=-1@99@sys_target=oauth_entity@99@sysparm_fixed_query=@99@sysparm_group_sort=@99@sysparm_parent=2c7cab53d7232100f20bc8170e61036b@99@sysparm_query=type%3dclient%5eORtype%3doauth_provider@99@sysparm_target=@99@sysparm_view=&wiz_collection_key=&wiz_collectionID=&wiz_collection=&wiz_collection_related_field=&wiz_view=&wiz_action=sysverb_new&sys_id=79ce2f53d7232100f20bc8170e610361&sysparm_query=type=client%5eORtype=oauth_provider&sysparm_target=&sys_target=oauth_entity)

    - ID client : **ID client de** l’application créée dans les conditions [préalables (Informations UNIQUEMENT)](#prerequisites-insights-only) étape \# 1

    - Secret client : secret d’application de l’application créée dans les conditions [préalables (Informations UNIQUEMENT)](#prerequisites-insights-only) étape \# 1

    - Type d’octroi par défaut : Informations d’identification client

    - URL du jeton : `https://login.microsoftonline.com/{M365\_Tenan\_Name}/oauth2/token`

    - URL de redirection : `https://{ServiceNow\_Istance\_Name}.service-now.com/oauth\_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image6.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

### <a name="set-up-microsoft-365-support-integration"></a>Configurer l’intégration Microsoft 365 prise en charge

L’Microsoft 365'intégration de support technique peut être configurée via **le programme d’installation** Microsoft 365 prise en charge.

Les étapes suivantes sont nécessaires pour configurer l’intégration entre votre instance ServiceNow et le support Microsoft.

1. \[La personne qui est un administrateur ServiceNow basculez l’étendue vers \] Microsoft 365 l’intégration.

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image9.png" alt-text="Interface utilisateur graphique, description de tableau générée automatiquement":::

2. \[La personne qui est un administrateur ServiceNow est Microsoft 365 prendre en charge > \] **le programme d’installation** pour ouvrir le flux d’intégration.

> [!NOTE]
> Si l’erreur « Opération de lecture par rapport à l’entité oauth » de l’étendue « \_ x \_ mioms m365 assis » a été refusée en raison de la stratégie d’accès entre étendues de la table, elle est due à votre stratégie \_ d’accès à la \_ table. Vous devez vous assurer **que toutes les étendues d’application** lues sont vérifiées pour l’entité  >   oauth \_ de table.

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image27.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

3. \[La personne qui est un administrateur ServiceNow \] **sélectionnez Accepter** d’accepter le consentement.

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image11.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

4. \[La personne qui est un administrateur ServiceNow \] a installé le fournisseur OAuth sortant.

Sélectionnez le profil OAuth pour le fournisseur OAuth sortant et sélectionnez **Suivant.**

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image12.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

5. \[La personne qui est un administrateur ServiceNow \] ignore le fournisseur OAuth entrant.

    Vérifiez **ignorer l’étape actuelle,** puis sélectionnez **Suivant.**

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image33.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

6. \[La personne qui est un administrateur ServiceNow ignore \] l’utilisateur d’intégration.

    Vérifiez **ignorer l’étape actuelle** et sélectionnez **Suivant.**

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image34.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

7. \[La personne qui est un ID de référentiel de configurer l’administrateur \] ServiceNow.

Spécifiez l’ID de référentiel et sélectionnez **Suivant.**

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image15.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

8. \[La personne qui est un administrateur ServiceNow \] Configurer l’application Paramètres.

    Sélectionnez les paramètres et sélectionnez **Suivant.**

    - SSO avec Microsoft 365 : vérifiez si l’instance ServiceNow est définie en tant qu’OS avec Microsoft 365 clients ; Sinon, décochez-le.

    - Administration Microsoft 365 Courrier électronique : adresse électronique de l Microsoft 365'administrateur à contacter lors de la création Microsoft 365 de support technique.

    - Environnement de test : cochez la case pour indiquer une phase de test afin d’éviter que les agents du support Microsoft ne vous contactent pour résoudre le problème. Si vous êtes prêt à passer officiellement à l’étape Microsoft 365 l’intégration, décochez la case.

    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image16.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

9. \[La personne qui est administrateur du service d’aide ou administrateur de demande de service dans Microsoft 365 client complète \] l’intégration.

    1. Vérifiez les informations ici pour vous assurer qu’elles sont correctes.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image35.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

    1. Go to Microsoft 365 [Admin Portal](https://admin.microsoft.com)  >  **Paramètres**  >  **Paramètres**  >  **Organization profiles**.

        1. Configurer les paramètres d’intégration de prise en charge avec les informations affichées dans le flux d’installation.

        1. Sous **l’onglet** Informations de base, sélectionnez **Service Now** en tant qu’outil de support interne, puis tapez ID d’application sortante comme **ID** d’application pour émettre un jeton OAuth.

            :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image18.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

        1. Sous **l’onglet Référentiels,** **sélectionnez** Ajouter un référentiel pour créer un référentiel avec les informations suivantes :

        - Référentiel : valeur **de l’ID** de référentiel de l’étape - 6 Terminer la page d’intégration.

        - Point de terminaison : valeur **de point** de terminaison de l’étape - 6 Terminer la page d’intégration.

        - Type d’authentification : **sélectionnez L’authentification AAD.**

        - ID client : valeur aléatoire, telle **qu’ignorée.**

        - Nom d’utilisateur rest : valeur aléatoire, telle **qu’ignorée.**

        - Mot de passe de l’utilisateur rest : valeur aléatoire, telle **qu’ignorée.**

            :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image36.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

        1. Revenir en arrière et sélectionnez le bouton pour enregistrer l’intégration.

    1. Sélectionnez **Suivant** pour terminer l’intégration.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image37.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

10. \[La personne qui est un administrateur ServiceNow active \] Microsoft 365 l’intégration d’un utilisateur existant.

Microsoft 365'intégration de la prise en charge est activée uniquement pour ces rôles d’utilisateur :

- [utilisateur \_ x mioms \_ m365 \_ assis.insights \_](https://ven01306.service-now.com/sys_user_role.do?sys_id=802b2adfdb4cac507c80230bd3961911&sysparm_record_target=sys_user_role&sysparm_record_row=2&sysparm_record_rows=2&sysparm_record_list=nameSTARTSWITHx_mioms_m365%5EORDERBYname)

- [x \_ mioms \_ m365 \_ assis.administrator](https://ven01306.service-now.com/sys_user_role.do?sys_id=4b25c9fb1b7784507ddd4227cc4bcb3a&sysparm_record_target=sys_user_role&sysparm_record_row=1&sysparm_record_rows=2&sysparm_record_list=nameSTARTSWITHx_mioms_m365%5EORDERBYname)

> [!NOTE] 
> L’utilisateur avec le rôle x \_ mioms \_ m365 assis.insights peut voir Incidents d’état du \_ \_ service, Solutions recommandées. L’utilisateur avec le rôle x \_ mioms \_ m365 assis.administrator peut également ouvrir un cas \_ avec Microsoft 365 prise en charge.

11. \[Facultatif \] \[ La personne qui est un lien d’administration ServiceNow \] Administration Microsoft 365 compte.

Si un utilisateur a le rôle « x \_ mioms \_ m365 assis.administrator et utilise différents comptes Microsoft 365 pour gérer un cas de support Microsoft, il doit se rendre sur le support Microsoft 365 > Link Account pour configurer son e-mail d’administrateur \_ Microsoft 365.

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image21.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

## <a name="testing-the-configuration"></a>Test de la configuration

Si votre application nécessite une communication réussie avec des systèmes externes, indiquez comment tester la connexion pour garantir une configuration réussie.

Voici les étapes à suivre pour tester la configuration de la prise en charge Microsoft 365'intégration :

1. Connectez-vous au portail ServiceNow en tant qu’administrateur.

2. Ouvrez n’importe quel incident.

3. Concentrez-vous **Microsoft 365'onglet** de prise en charge, puis **sélectionnez Microsoft 365 Informations** pour déterminer si les solutions recommandées ont été récupérées avec succès.

:::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image38.png" alt-text="Interface utilisateur graphique, application, description du site web générée automatiquement":::

##  <a name="troubleshooting"></a>Résolution des problèmes

|#|Problème|Action diagnostics|
|--- |--- |--- |
|1 |Ne peut pas voir **l’onglet Microsoft 365 prise en charge**|Vérifiez l’affichage actuel et **tous les journaux système** à  >   l’x_mioms_m365_assit|
|2 |Sélectionnez **les solutions recommandées par Microsoft,** mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui d’effectuer les étapes de configuration de l’application ».|Vérifiez le message d’erreur en haut du formulaire et des **journaux système** à  >   l’x_mioms_m365_assit|
|3 |Sélectionnez **les solutions recommandées par Microsoft,** mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui de terminer l’étape finale de mise en place de l’application ».|Vérifiez le message d’erreur en haut du formulaire et des **journaux système** à  >   l’x_mioms_m365_assit|
|4 |Tapez le problème dans la zone de recherche et sélectionnez les **solutions recommandées** par Microsoft, mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui d’effectuer les étapes de configuration de l’application ».|Vérifiez le message d’erreur en haut du formulaire et des **journaux système** à  >   l’x_mioms_m365_assit|
|5 |Tapez le problème dans la zone de recherche et sélectionnez les **solutions recommandées** par Microsoft, mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui de terminer l’étape finale de mise en place de l’application ».|Vérifiez le message d’erreur en haut du formulaire et des **journaux système** à  >   l’x_mioms_m365_assit|
|6 |Sélectionnez **Contacter le support Microsoft,** mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui d’effectuer les étapes de configuration de l’application ».|Vérifiez le message d’erreur en haut du formulaire et **journaux système** à  >   l’x_mioms_m365_assit|
|7 |Sélectionnez **Contacter le support Microsoft,** mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui de terminer l’étape finale de mise en place de l’application ».|Vérifiez le message d’erreur en haut du formulaire et **journaux système** à  >   l’x_mioms_m365_assit|
|8 |Sélectionnez **Contacter le support Microsoft,** mais obtenez l’erreur « {EmailAddress} n’est pas un compte d’administrateur Microsoft 365 valide. Vous devez Microsoft 365'administrateur pour ouvrir une demande de service. Dans l’application, lier le compte d’administrateur. »|Vérifiez le message d’erreur en haut du formulaire et **journaux système** à  >   l’x_mioms_m365_assit|
|9 |Sélectionnez **les solutions recommandées par Microsoft,** mais rien ne s’affiche|Vérifier **les journaux système : journaux HTTP sortants** avec filtres login.microsoftonline.com et connector.rave.microsoft.com|
|10 |Sélectionnez **les solutions recommandées par Microsoft,** mais obtenez l’erreur « Veuillez contacter le support de l’application ».|Vérifiez le message d’erreur en haut du formulaire et **journaux système** à  >   l’x_mioms_m365_assit|
|11 |Tapez le problème dans la zone de recherche et sélectionnez **les solutions recommandées par Microsoft,** mais rien ne s’affiche|Vérifier **les journaux système : journaux HTTP sortants** avec filtres login.microsoftonline.com et connector.rave.microsoft.com|
|12 |Tapez un problème dans la zone de recherche et sélectionnez **les solutions recommandées** par Microsoft, mais obtenez l’erreur « Veuillez contacter le support de l’application ».|Vérifiez le message d’erreur en haut du formulaire et **journaux système** à  >   l’x_mioms_m365_assit|
|13 |L’utilisateur sélectionne **contacter le support Microsoft,** mais rien ne se produit|Vérifier **les journaux système : journaux HTTP sortants** avec filtres login.microsoftonline.com et connector.rave.microsoft.com|
|14 |Can’t see Microsoft recommended solution after reopening the incident|Vérifier **tous les journaux système** à  >   l’x_mioms_m365_assit|
|15 |Can’t see Microsoft cases when reopening the incident that was transferred to Microsoft support|Vérifier **tous les journaux système** à  >   l’x_mioms_m365_assit|
|16 |Impossible d’enregistrer les détails du ticket, obtenez l’erreur « Impossible d’enregistrer les détails du ticket. Veuillez contacter le support technique de l’application. »|Vérifier le message d’erreur en haut du formulaire|
