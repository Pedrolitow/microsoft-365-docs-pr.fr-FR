---
title: Configurer l’intégration de la prise en charge avec ServiceNow - Authentification de base
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: Guide de configuration et d’installation d’applications certifiées étendues pour ServiceNow.
ms.openlocfilehash: ed3e7340d91ad3ae997bb27400d81c46ace4773b
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68191296"
---
# <a name="configure-support-integration-with-servicenow---basic-authentication"></a>Configurer l’intégration de la prise en charge avec ServiceNow - Authentification de base

## <a name="prerequisites-basic-authentication"></a>Prérequis (Authentification de base)

Ces prérequis sont nécessaires pour configurer **l’intégration du support Microsoft 365**.

1. \[AAD Administration\] créer une application Azure AD sous votre locataire Microsoft 365.

    1. Connectez-vous au portail Azure avec vos informations d’identification de locataire Microsoft 365 et accédez à la [page inscriptions d'applications](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) pour créer une application.

    1. Sélectionnez **Comptes dans cet annuaire organisationnel uniquement ({Microsoft-365-tenant-name} uniquement – Locataire unique)** et **sélectionnez Inscrire**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="Interface utilisateur graphique, texte, application, description de l’e-mail généré automatiquement":::

1. Accédez à **l’authentification** et **sélectionnez Ajouter une plateforme**. Sélectionnez l’option **Web** et entrez l’URL de redirection : `https://{your-servicenow-instance``}.service-now.com/oauth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="Interface utilisateur graphique, texte, application, description de l’e-mail généré automatiquement":::

1. Obtenez l’ID client de l’application, créez une clé secrète client et obtenez cette valeur.

1. \[ServiceNow Administration\] configurer le fournisseur OAuth sortant dans ServiceNow.

    Si l’étendue n’est pas définie sur **Global**, accédez à **Paramètres &gt; applications de développeur &gt;** et basculez vers **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Interface utilisateur graphique, texte, application, conversation ou sms Description générée automatiquement":::

1. Accédez au **registre d’applications OAuth &gt; système**.

1. Créez une application à l’aide de l’option **Se connecter à un fournisseur OAuth tiers** et entrez les valeurs suivantes :

    - ID client : il s’agit de l’ID client de l’application créée à l’étape \#1.

    - Clé secrète client : il s’agit de la valeur de clé secrète client de l’application créée à l’étape \#1.

    - Type d’octroi par défaut : Informations d’identification du client

    - URL du jeton : `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - URL de redirection : `https://{service-now-instance-name``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

1. \[ServiceNow Administration\] configurer le fournisseur OAuth entrant.

    Si l’étendue n’est pas définie sur **Global**, accédez à **Paramètres &gt; applications de développeur &gt;** et basculez vers **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Interface utilisateur graphique, texte, application, conversation ou sms Description générée automatiquement":::

1. Accédez au **registre d’applications OAuth &gt; système**.

1. Créez une application à l’aide de l’option **Créer un point de terminaison d’API OAuth pour les clients externes** . Nommez le fournisseur OAuth entrant et laissez tous les autres champs avec leurs valeurs par défaut.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image7.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image7.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

1. \[ServiceNow Administration\] Créer un utilisateur d’intégration.

    Vous devez spécifier un utilisateur d’intégration. Si vous n’avez pas d’utilisateur d’intégration existant ou si vous souhaitez en créer un spécifiquement pour cette intégration, accédez à **Utilisateurs de l’organisation &gt;** pour en créer un.

    Si vous créez un utilisateur d’intégration, vérifiez l’option **d’accès au service Web uniquement** . Vous devez également accorder à cet utilisateur le rôle **gestionnaire d’incidents\_**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image8.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image8.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

## <a name="optional-allow-the-services-ip-addresses-to-microsoft-365-support-integration"></a>\[FACULTATIF\] Autoriser l’intégration des adresses IP du service à l’intégration du support Microsoft 365

Si votre entreprise limite l’accès à Internet avec vos propres stratégies, activez l’accès réseau pour le service d’intégration de la prise en charge de Microsoft 365 en autorisant les adresses IP ci-dessous pour l’accès à l’API entrante et sortante :

- 52.149.152.32

- 40.83.232.243

- 40.83.114.39

- 13.76.138.31

- 13.79.229.170

- 20.105.151.142

> [!NOTE]
> Cette commande de terminal répertorie toutes les adresses IP actives du service pour l’intégration de la prise en charge de Microsoft 365 : `nslookup`` connector.rave.microsoft.com`

## <a name="configure-the-microsoft-365-support-integration-application"></a>Configurer l’application d’intégration de prise en charge de Microsoft 365

L’application d’intégration de support Microsoft 365 peut être configurée sous le support Microsoft 365.

Ces étapes sont nécessaires pour configurer l’intégration entre votre instance ServiceNow et le support Microsoft 365.

1. \[ServiceNow Administration\] Basculer l’étendue vers **l’intégration du support Microsoft 365**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image9.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image9.png" alt-text="Interface utilisateur graphique, description de table générée automatiquement":::

1. \[ServiceNow Administration\] accédez au **programme d’installation du support &gt; Microsoft 365** pour ouvrir le flux de travail d’intégration.

    > [!NOTE]
    > Si vous voyez que l’erreur « Opération de lecture sur l’entité oauth\_» de l’étendue « x\_mioms\_m365\_assis » a été refusée en raison de la stratégie d’accès inter-étendue de la table », cela est dû à votre stratégie d’accès à la table. Vous devez vérifier que **toutes les étendues d’application &gt; pouvant être lues** sont vérifiées pour l’entité oauth\_de table.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image10.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image10.png" alt-text="Interface utilisateur graphique, texte, application, description de l’e-mail généré automatiquement":::

1. \[ServiceNow Administration\] Sélectionnez **Accepter** de continuer.

    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-1.png" lightbox="../../media/ServiceNow-guide/snowbasic-1.png" alt-text="Interface utilisateur graphique, texte, application, description de l’e-mail généré automatiquement":::

1. \[ServiceNow Administration\] configurer l’environnement et le type d’installation.

    Si cette installation se trouve sur un environnement de test, sélectionnez l’option Il s’agit d’un environnement de test. Vous pourrez désactiver rapidement cette option une fois l’installation terminée et tous vos tests terminés ultérieurement.
    Si votre instance autorise l’authentification de base pour les connexions entrantes, sélectionnez Oui. Sinon, reportez-vous à [l’installation avancée avec AAD](servicenow-aad-oauth-token.md). :::image type="content" source="../../media/ServiceNow-guide/snowbasic-2.png" lightbox="../../media/ServiceNow-guide/snowbasic-2.png" alt-text="Interface utilisateur graphique, texte, application, description de l’e-mail généré automatiquement":::

1. \[ServiceNow Administration\] entrez votre domaine de locataire Microsoft 365.

    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-3.png" lightbox="../../media/ServiceNow-guide/snowbasic-3.png" alt-text="Interface utilisateur graphique, texte, application, description de l’e-mail généré automatiquement":::

1. \[ServiceNow Administration\] configurer les paramètres sortants.
    1. Inscrivez l’application Azure Active Directory (AAD).
    1. Après avoir suivi les instructions de la section Prérequis, cliquez sur **Terminé**. Sinon, suivez les instructions de l’Assistant pour créer l’inscription d’application nécessaire dans AAD.
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-4.png" lightbox="../../media/ServiceNow-guide/snowbasic-4.png" alt-text="Interface utilisateur graphique, texte, application, description de l’e-mail généré automatiquement":::

    1. Inscrivez l’application OAuth ServiceNow.
    1. Après avoir suivi les instructions de la section prérequis, sélectionnez l’inscription d’application OAuth nouvellement créée, puis cliquez sur Suivant. Sinon, suivez les instructions pour créer l’entité dans ServiceNow, puis sélectionnez la nouvelle inscription d’application.
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-5.png" lightbox="../../media/ServiceNow-guide/snowbasic-5.png" alt-text="Interface utilisateur graphique, texte, application, description de l’e-mail généré automatiquement":::

1. \[ServiceNow Administration\] configurer les paramètres entrants.
    1. Configurez le point de terminaison de l’API OAuth entrante.
    1. Après avoir suivi les instructions de la section prérequis, sélectionnez l’inscription d’application OAuth nouvellement créée, puis cliquez sur Terminé. Sinon, suivez les instructions pour créer l’entité, puis sélectionnez la nouvelle inscription de point de terminaison REST.
     
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-6.png" lightbox="../../media/ServiceNow-guide/snowbasic-6.png" alt-text="Interface utilisateur graphique, texte, application, description de l’e-mail généré automatiquement":::

    1. Configurez l’utilisateur d’intégration.
    1. Après avoir suivi les instructions de la section prérequis, sélectionnez l’utilisateur d’intégration nouvellement créé, puis cliquez sur Suivant. Sinon, suivez les instructions pour créer l’entité dans ServiceNow, puis sélectionnez le nouvel utilisateur d’intégration.
    
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-7.png" lightbox="../../media/ServiceNow-guide/snowbasic-7.png" alt-text="Interface utilisateur graphique, texte, application, description de l’e-mail généré automatiquement":::


1. \[Le locataire Microsoft 365 Administration\] terminer l’intégration dans le portail Administration Microsoft 365.

    Vérifiez que les informations ci-dessous sont correctes. NE SÉLECTIONNEZ PAS **Suivant** pour l’instant.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image17.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image17.png" alt-text="Interface utilisateur graphique, texte, description de l’application généré automatiquement":::

1. Accédez à **Administration Microsoft 365 Profils d’organisation des paramètres de l’organisation des &gt; paramètres &gt; du portail&gt;**.

1. Configurez les paramètres d’intégration du support :

    Sélectionnez l’onglet **Informations de base** **>'outil** >  de **support interne** ServiceNow, puis entrez la valeur **d’ID d’application sortante** dans l’ID **d’application pour émettre le champ Jeton d’authentification**. Cet ID d’application sortante se trouve à l’étape 6 : terminer l’intégration, qui a été créée à [l’étape \#1 de prérequis (authentification de base](#prerequisites-basic-authentication)).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="Interface utilisateur graphique, texte, application, description de l’e-mail généré automatiquement":::

1. Sous l’onglet **Dépôts** , sélectionnez **Nouveau référentiel** et mettez-le à jour avec les paramètres suivants :

    - Référentiel : valeur **d’ID de référentiel** de l’étape 6 – Terminer l’intégration.

    - Point de terminaison : valeur de **point de terminaison** de l’étape 6 – Terminer l’intégration.

    - Type d’authentification : sélectionnez **l’authentification de base**.

    - ID client : valeur **d’ID client** de l’étape 6 – Terminer l’intégration.

    - Clé secrète client : secret du fournisseur OAuth entrant qui a été créé à l’étape \#Prérequis (Authentification de base) 3.

    - Expiration du jeton d’actualisation : 864000

    - Nom d’utilisateur rest : valeur **de nom d’utilisateur** de l’étape 6 – Terminer l’intégration.

    - Mot de passe de l’utilisateur rest : mot de passe de l’utilisateur d’intégration qui a été créé à [l’étape \#Prérequis (Authentification de base) 4](#prerequisites-basic-authentication).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image19.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image19.png" alt-text="Interface utilisateur graphique, la description de l’application génère automatiquement":::

1. Retour à ServiceNow.

1. Sélectionnez **Suivant** pour terminer l’intégration.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image20.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image20.png" alt-text="Interface utilisateur graphique, application, description du site web générée automatiquement":::

1. \[ServiceNow Administration\] Tester la connexion Une fois l’étape précédente terminée, cliquez sur **Tester la connexion**.
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-8.png" lightbox="../../media/ServiceNow-guide/snowbasic-8.png" alt-text="Interface utilisateur graphique, texte, application, description de l’e-mail généré automatiquement":::
    L’application d’intégration de support Microsoft 365 exécute des tests pour s’assurer que l’intégration fonctionne. En cas de problème avec la configuration, un message d’erreur explique ce qui doit être résolu. Sinon, l’application est prête.
     :::image type="content" source="../../media/ServiceNow-guide/snowbasic-9.png" lightbox="../../media/ServiceNow-guide/snowbasic-9.png" alt-text="Interface utilisateur graphique, texte, application, description de l’e-mail généré automatiquement":::

1. \[ServiceNow Administration\] Activer l’intégration du support Microsoft pour un utilisateur existant.

    L’intégration de la prise en charge de Microsoft 365 est activée pour l’utilisateur avec l’un des rôles suivants :

    - utilisateur x\_mioms\_m365\_assis.insights\_

    - x\_mioms\_m365\_assis.administrator

1. \[FACULTATIF\] [L’utilisateur ayant un rôle x_mioms_m365_assis.administrator] Lien Administration Microsoft 365 compte.

    Si un utilisateur a le rôle x_mioms_m365_assis.administrator et utilise différents comptes Microsoft 365 pour gérer un cas de support Microsoft 365, il doit accéder au support Technique Microsoft 365 > Compte Link pour configurer son e-mail d’administrateur Microsoft 365.
    
    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image21.png" alt-text="Interface utilisateur graphique, texte, description de l’application généré automatiquement":::
