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
ms.openlocfilehash: bd19e5fd72e2b21c7ec08e00497444475701817c
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2021
ms.locfileid: "60754252"
---
# <a name="configure-support-integration-with-servicenow---basic-authentication"></a>Configurer l’intégration de la prise en charge avec ServiceNow - Authentification de base

## <a name="prerequisites-basic-authentication"></a>Conditions préalables (Authentification de base)

Ces conditions préalables sont nécessaires pour configurer la prise en **charge Microsoft 365'intégration.**

1. \[AAD Admin \] Create AAD Application under your Microsoft 365 tenant.

    1. Connectez-vous au portail Azure à l’Microsoft 365 vos informations d’identification client et allez sur la [page](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) d’inscription de l’application pour créer une application.

    1. Sélectionnez les comptes dans cet annuaire d’organisation **uniquement ({Microsoft-365-tenant-name} uniquement – Client unique)** et sélectionnez **Enregistrer**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Go to **Authentication** and select **Add a platform**. Sélectionnez **l’option Web** et entrez l’URL de redirection : `https://{your-servicenow-instance``}.service-now.com/oauth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Obtenez l’ID client de l’application, créez une secret client et obtenez cette valeur.

1. \[L’administrateur ServiceNow \] a installé le fournisseur OAuth sortant dans ServiceNow.

    Si l’étendue n’est pas définie sur **Global,** passez à **Paramètres &gt; &gt; Applications** de développeur et passez à **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Interface utilisateur graphique, texte, application, conversation ou message texte Description générés automatiquement":::

1. Go to **System OAuth &gt; Application Registry**.

1. Créez une application en utilisant l’Connecter à une option de fournisseur **OAuth** tierce et en entrant les valeurs ci-après :

    - ID client : il s’agit de l’ID client de l’application créée à \# l’étape 1.

    - Secret client : il s’agit de la valeur de la secret client de l’application créée à \# l’étape 1.

    - Type d’octroi par défaut : informations d’identification du client

    - URL du jeton : `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - URL de redirection : `https://{service-now-instance-name``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

1. \[L’administrateur ServiceNow \] a installé le fournisseur OAuth entrant.

    Si l’étendue n’est pas définie sur **Global,** faites-le en passant à Paramètres **&gt; &gt; Applications** de développeur et en passant à **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Interface utilisateur graphique, texte, application, conversation ou message texte Description générés automatiquement":::

1. Go to **System OAuth &gt; Application Registry**.

1. Créez une application à l’aide de l’option Créer un point de terminaison **de l’API OAuth pour les clients externes.** Nommez le fournisseur OAuth entrant et laissez tous les autres champs avec leurs valeurs par défaut.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image7.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image7.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

1. \[Administrateur ServiceNow \] Créez un utilisateur d’intégration.

    Vous devez spécifier un utilisateur d’intégration. Si vous n’avez pas d’utilisateur d’intégration existant ou si vous **&gt;** souhaitez en créer un spécifiquement pour cette intégration, rendez-vous sur Utilisateurs de l’organisation pour créer un utilisateur.

    Si vous créez un utilisateur d’intégration, vérifiez l’option d’accès **au service Web uniquement.** Vous devez également accorder à cet utilisateur le rôle **gestionnaire \_ d’incidents.**

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image8.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image8.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

## <a name="optional-allow-the-services-ip-addresses-to-microsoft-365-support-integration"></a>\[FACULTATIF Autoriser les adresses IP du service à prendre \] en charge Microsoft 365'intégration

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

1. \[L’administrateur ServiceNow \] bascule l’étendue **vers Microsoft 365'intégration de support technique.**

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image9.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image9.png" alt-text="Interface utilisateur graphique, description de tableau générée automatiquement":::

1. \[ServiceNow Admin \] Go to Microsoft 365 Support **&gt; Setup** to open the integration workflow.

    > [!NOTE]
    > Si l’erreur « Opération de lecture par rapport à l’entité oauth » de l’étendue « \_ x \_ mioms m365 assis » a été refusée en raison de la stratégie d’accès à plusieurs étendues de la table, elle est due à votre stratégie \_ d’accès à la \_ table. Vous devez vous assurer **que toutes les étendues d’application &gt;** lues sont vérifiées pour l’entité oauth \_ de table.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image10.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image10.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[ServiceNow Admin \] Select **Agree** to continue.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image11.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image11.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[L’administrateur ServiceNow \] a installé le fournisseur OAuth sortant.

    Sélectionnez le profil OAuth pour le fournisseur OAuth sortant créé à l’étape 2 Conditions [préalables \# (Authentification](#prerequisites-basic-authentication) de base) et sélectionnez **Suivant**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image12.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image12.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[L’administrateur ServiceNow \] a installé le fournisseur OAuth entrant.

    1. Décochez **Ignorer l’étape actuelle.**

    1. Décochez **le jeton d’OIDC externe.**

    1. Sélectionnez le client OAuth créé à l’étape [3 prérequise \# (Authentification](#prerequisites-basic-authentication)de base), puis sélectionnez **Suivant.**

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image13.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image13.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[L’administrateur ServiceNow \] a installé l’utilisateur d’intégration des appels entrants.

    1. Décochez **Ignorer l’étape actuelle.**

    1. Sélectionnez l’utilisateur d’intégration créé à l’étape 4 des conditions [préalables \# (Authentification](#prerequisites-basic-authentication)de base), puis sélectionnez **Suivant**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image14.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image14.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

1. \[ServiceNow Admin \] Set up the Repository ID.

    Spécifiez l’ID de référentiel, puis sélectionnez **Suivant**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image15.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image15.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

1. \[ServiceNow Admin \] Set up Application settings.

    Sélectionnez les paramètres suivants, puis sélectionnez **Suivant**.

    - SSO avec Microsoft 365 : vérifiez si l’instance ServiceNow est définie en tant qu’OS avec Microsoft 365 clients, sinon décochez-la.

    - Microsoft 365 e-mail de l’administrateur : adresse de messagerie Microsoft 365'administrateur qui est contacté lors de la création Microsoft 365 de support technique.

    - Environnement de test : cochez la case pour indiquer une phase de test afin d’éviter que les agents du support Microsoft ne vous contactent pour résoudre le problème. Si vous êtes prêt à passer officiellement à l’étape Microsoft 365 l’intégration, décochez la case.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image16.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image16.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

1. \[Microsoft 365 L’administrateur client \] termine l’intégration.

    Vérifiez que les informations ci-dessous sont correctes. NE sélectionnez **PAS Suivant** pour le moment.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image17.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image17.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

1. Go to **Administration Microsoft 365 Portal Paramètres Org &gt; &gt; settings Organization &gt; profiles**.

1. Configurez les paramètres d’intégration de la prise en charge :

    Sélectionnez **l’onglet** Informations de base >'outil de support interne ServiceNow, puis entrez la valeur de l’ID de l’application sortante dans l’ID d’application pour émettre le champ de jeton  >   **OAuth.**  Cet ID d’application sortante se trouve à l’étape 6 : terminer l’intégration, qui a été créée à l’étape 1 prérequise [ \# (Authentification](#prerequisites-basic-authentication)de base).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Sous **l’onglet Référentiels,** **sélectionnez** Ajouter un référentiel pour créer un référentiel avec les paramètres suivants :

    - Référentiel : valeur **de l’ID** de référentiel de l’étape 6 : terminer l’intégration.

    - Point de terminaison : valeur **de point** de terminaison de l’étape 6 : terminer l’intégration.

    - Type d’authentification : sélectionner **l’authentification de base.**

    - ID client : valeur **de l’ID client** de l’étape 6 : terminer l’intégration.

    - Secret client : secret du fournisseur OAuth entrant créé à l’étape 3 des conditions préalables \# (authentification de base).

    - Expiration du jeton d’actualisation : 864000

    - Nom d’utilisateur restant : valeur **du nom d’utilisateur** de l’étape 6 : terminer l’intégration.

    - Mot de passe de l’utilisateur rest : mot de passe de l’utilisateur d’intégration qui a été créé à l’étape 4 des [conditions préalables \# (Authentification de base).](#prerequisites-basic-authentication)

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image19.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image19.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

1. Revenir à ServiceNow.

1. Sélectionnez **Suivant** pour terminer l’intégration.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image20.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image20.png" alt-text="Interface utilisateur graphique, application, description du site web générée automatiquement":::

1. \[L’administrateur ServiceNow \] active l’intégration du support Microsoft pour un utilisateur existant.

    Microsoft 365 prise en charge de l’intégration est activée pour l’utilisateur avec l’un des rôles ci-après :

    - utilisateur \_ x mioms \_ m365 \_ assis.insights \_

    - x \_ mioms \_ m365 \_ assis.administrator

    > [!NOTE]
    > L’utilisateur ayant le rôle x \_ mioms \_ m365 assis.insights peut voir Incidents d’état du \_ \_ service, Solutions recommandées. L’utilisateur avec le rôle x \_ mioms \_ m365 assis.administrator peut également ouvrir un cas \_ avec Microsoft 365 prise en charge.

1. \[FACULTATIF \] \[ L’utilisateur avec le rôle x \_ mioms \_ m365 \_ assis.administrator \] lien Administration Microsoft 365 compte.

    Si un utilisateur a le rôle x \_ mioms \_ m365 \_ assis.administrator et utilise différents comptes Microsoft 365 pour gérer un cas de support Microsoft 365, il doit se rendre sur le compte de lien de support Microsoft 365 pour configurer son e-mail d’administrateur &gt; Microsoft 365.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image21.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image21.png" alt-text="Interface utilisateur graphique, texte, description d’application générés automatiquement":::
