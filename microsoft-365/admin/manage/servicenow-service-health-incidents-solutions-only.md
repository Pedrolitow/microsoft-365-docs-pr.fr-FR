---
title: Microsoft 365 l’intégration des incidents d’état du service et des solutions recommandées uniquement
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
ms.openlocfilehash: b2676c05a4ee7767b40356852d32398f2d2c04a3
ms.sourcegitcommit: 7e59802f251da96ec639fb09534aa96acf5d6ce7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2021
ms.locfileid: "61071425"
---
# <a name="microsoft-365-support-integration-for-service-health-incidents-and-recommended-solutions-only"></a>Microsoft 365 l’intégration des incidents d’état du service et des solutions recommandées uniquement

Cette configuration ne vous permet pas de créer un cas avec le support Microsoft via votre instance ServiceNow. Cette option vous fournit uniquement les informations sur l’incident d’état du service et les solutions recommandées disponibles via votre instance ServiceNow.

## <a name="prerequisites-service-health-incidents-and-recommended-solutions-only"></a>Conditions préalables (incidents d’état du service et solutions recommandées UNIQUEMENT)

Ces conditions préalables sont nécessaires pour configurer la prise en **charge Microsoft 365'intégration.**

1. \[AAD admin \] Créez AAD application pour le trafic sortant sous votre Microsoft 365 client.

    1. Connectez-vous au portail Azure avec vos informations d’identification Microsoft 365 client et créez une application sur la page Inscriptions [de l’application.](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade)

    2. Sélectionnez les comptes dans cet annuaire d’organisation **uniquement ({Microsoft-365-tenant-name}** uniquement – Client unique), puis sélectionnez **Enregistrer**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Go to **Authentication** and select **Add a platform**. Sélectionnez **l’option Web** et entrez l’URL de redirection : `https://{your-servicenow-instance``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Obtenez l’ID client de l’application, créez une secret client et obtenez cette valeur.

1. \[L’administrateur ServiceNow \] a installé le fournisseur OAuth sortant dans ServiceNow.

    Si l’étendue n’est pas définie sur **Global,** passez à **Paramètres &gt; &gt; Applications** de développeur et passez à **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/Servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/Servicenow-guide-image5.png" alt-text="Interface utilisateur graphique, texte, application, conversation ou message texte Description générés automatiquement":::

1. Go to **System OAuth &gt; Application Registry**.

1. Créez une application en utilisant l’Connecter à une option de fournisseur **OAuth** tierce et en entrant les valeurs ci-après :

    - ID client : il s’agit de l’ID client de l’application créée à l’étape 1 des conditions préalables (Informations \# uniquement).

    - Secret client : il s’agit de la valeur de la secret client de l’application créée à l’étape 1 des conditions préalables (Informations \# uniquement).

    - Type d’octroi par défaut : informations d’identification du client

    - URL du jeton : `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - URL de redirection : `https://{service-now-instance-name``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

## <a name="configure-the-microsoft-365-support-integration-application"></a>Configurer l’application Microsoft 365 prise en charge de l’intégration

L’Microsoft 365'intégration de support technique peut être définie sous Microsoft 365 prise en charge.

Ces étapes sont nécessaires pour configurer l’intégration entre votre instance ServiceNow et Microsoft 365 prise en charge.

1. \[ServiceNow Admin \] Switch the scope to Microsoft 365 support **integration**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image9.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image9.png" alt-text="Interface utilisateur graphique, description de tableau générée automatiquement":::

1. \[ServiceNow Admin \] Go to Microsoft 365 Support **&gt; Setup** to open the integration workflow.

    > [!NOTE]
    > Si l’erreur « Opération de lecture par rapport à l’entité oauth » de l’étendue « \_ x \_ mioms m365 assis » a été refusée en raison de la stratégie d’accès à plusieurs étendues de la table, elle est due à votre stratégie \_ d’accès à la \_ table. Vous devez vous assurer **que toutes les étendues d’application &gt;** lues sont vérifiées pour l’entité oauth \_ de table.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image27.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image27.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[ServiceNow Admin \] Select **Agree** to continue.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image11.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image11.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[L’administrateur ServiceNow \] a installé le fournisseur OAuth sortant.

    Sélectionnez le profil OAuth pour le fournisseur OAuth sortant, puis sélectionnez **Suivant**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image12.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image12.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. \[L’administrateur ServiceNow \] ignore le fournisseur OAuth entrant.

    Vérifiez **ignorer l’étape actuelle,** puis sélectionnez **Suivant.**

1. \[L’administrateur ServiceNow \] ignore l’utilisateur d’intégration des appels entrants.

    Vérifiez **ignorer l’étape actuelle,** puis sélectionnez **Suivant.**

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image34.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image34.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

1. \[ServiceNow Admin \] Set up the Repository ID.

    Spécifiez l’ID de référentiel, puis sélectionnez **Suivant**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image15.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image15.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

1. \[ServiceNow Admin \] Set up Application Paramètres.

    Sélectionnez ces paramètres, puis sélectionnez **Suivant**:

    - SSO avec Microsoft 365 : vérifiez si l’instance ServiceNow est définie en tant qu’OS avec Microsoft 365 clients, sinon décochez-la.

    - Microsoft 365 e-mail de l’administrateur : adresse de messagerie Microsoft 365'administrateur qui est contacté lors de la création Microsoft 365 de support technique.

    - Environnement de test : cochez la case pour indiquer une phase de test afin d’éviter que les agents du support Microsoft ne vous contactent pour résoudre le problème. Si vous êtes prêt à passer officiellement à l’étape Microsoft 365 l’intégration, décochez la case.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image16.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image16.png" alt-text="Interface utilisateur graphique, texte, description de l’application générés automatiquement":::

1. \[Microsoft 365 client \] Terminez l’intégration.

    Vérifiez que les informations ci-dessous sont correctes. NE sélectionnez **PAS Suivant** pour le moment.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image35.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image35.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Go to **Administration Microsoft 365 Portal Paramètres Org &gt; &gt; settings Organization &gt; profiles**.

1. Configurez les paramètres d’intégration de la prise en charge :

    Sélectionnez **l’onglet** Informations de base >'outil de support interne ServiceNow, puis entrez la valeur de l’ID de l’application sortante dans l’ID d’application pour émettre le champ de jeton  >   **OAuth.**  Cet ID d’application sortante se trouve à l’étape 6 : terminez l’intégration, qui a été créée à l’étape [ \# 1](#prerequisites-service-health-incidents-and-recommended-solutions-only)de la prérequise (Informations UNIQUEMENT).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="Interface utilisateur graphique, texte, application, description de courrier électronique généré automatiquement":::

1. Sous **l’onglet Référentiels,** sélectionnez **Nouveau** référentiel et mettez-le à jour avec les paramètres suivants :

    - Référentiel : valeur **de l’ID** de référentiel de l’étape 6 : terminer l’intégration.

    - Point de terminaison : valeur **de point** de terminaison de l’étape 6 : terminer l’intégration.

    - Type d’authentification **: sélectionnez AAD auth**.

    - ID client : valeur aléatoire (exemple : ignoré).

    - Nom d’utilisateur rest : valeur aléatoire (exemple : ignoré).

    - Mot de passe utilisateur rest : valeur aléatoire (exemple : ignoré).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image36.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image36.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

1. Revenir à ServiceNow.

1. Sélectionnez **Suivant** pour terminer l’intégration.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image37.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image37.png" alt-text="Interface utilisateur graphique, description de l’application générée automatiquement":::

1. \[L’administrateur ServiceNow \] active l’intégration du support Microsoft pour un utilisateur existant.

    Microsoft 365 prise en charge de l’intégration est activée pour l’utilisateur avec l’un des rôles ci-après :

    - utilisateur \_ x mioms \_ m365 \_ assis.insights \_

    - x \_ mioms \_ m365 \_ assis.administrator

    > [!NOTE]
    > L’utilisateur ayant le rôle x \_ mioms \_ m365 assis.insights peut voir Incidents d’état du \_ \_ service, Solutions recommandées. L’utilisateur avec le rôle x \_ mioms \_ m365 assis.administrator peut également ouvrir un cas \_ avec Microsoft 365 prise en charge. Avec Informations UNIQUEMENT, personne ne doit se voir attribuer le rôle x \_ mioms \_ m365 \_ assis.administrator.
