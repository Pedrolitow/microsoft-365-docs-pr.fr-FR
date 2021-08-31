---
title: Configurer Microsoft Defender pour Endpoint Plan 1 (prévisualisation)
description: Découvrez comment configurer Defender pour Endpoint Plan 1. Examinez les conditions requises, planifiez votre déploiement et définissez votre environnement.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 08/30/2021
ms.prod: m365-security
ms.technology: mde
localization_priority: Normal
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.openlocfilehash: e5f62a59b66db83b5c9d191d2f7496b280abbc18
ms.sourcegitcommit: c41e3f48451e2d7b45901faee21b1e1d19a16688
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2021
ms.locfileid: "58824057"
---
# <a name="set-up-and-configure-microsoft-defender-for-endpoint-plan-1-preview"></a>Configurer Microsoft Defender pour Endpoint Plan 1 (prévisualisation)

> [!TIP]
> Si vous avez Microsoft 365 E3 mais pas Microsoft 365 E5, visitez le site pour vous inscrire [https://aka.ms/mdep1trial](https://aka.ms/mdep1trial) au programme d’aperçu !

Cet article explique comment configurer Defender pour Endpoint Plan 1 (prévisualisation). Que vous donnez de l’aide ou que vous le faisiez vous-même, vous pouvez utiliser cet article comme guide tout au long de votre déploiement.  

## <a name="the-setup-and-configuration-process"></a>Processus d’installation et de configuration

:::image type="content" source="images/mde-p1-deploymentflow.png" alt-text="Flux de configuration et de déploiement pour Microsoft Defender pour Endpoint Plan 1":::

Le processus d’installation et de configuration général de Defender pour Endpoint Plan 1 (prévisualisation) est le suivant : <br/><br/>


| Nombre  | Étape  | Description  |
|:---------:|:---------|:---------|
| 1 | [Consultez la configuration requise](#review-the-requirements)  | Répertorie les conditions requises pour les licences, le navigateur, le système d’exploitation et les centres de données   |
| 2 | [Planifier votre déploiement](#plan-your-deployment) | Répertorie plusieurs méthodes de déploiement à prendre en compte et inclut des liens vers d’autres ressources pour vous aider à choisir la méthode à utiliser  |
| 3 | [Configurer votre environnement client](#set-up-your-tenant-environment) | Répertorie les tâches de configuration de votre environnement client |
| 4  | [Attribuer des rôles et des autorisations](#assign-roles-and-permissions) | Répertorie les rôles et autorisations à prendre en compte pour votre équipe de sécurité <br/><br/>**CONSEIL**: dès que des rôles et des autorisations sont attribués, votre équipe de sécurité peut commencer à utiliser Microsoft 365 Defender portail. Pour en savoir plus, [consultez La mise en place.](mde-plan1-getting-started.md) |
| 5  | [Intégration à Defender pour le point de terminaison](#onboard-to-defender-for-endpoint) | Répertorie plusieurs méthodes par système d’exploitation à intégrer à Defender for Endpoint Plan 1 et inclut des liens vers des informations plus détaillées pour chaque méthode  |
| 6  | [Configurer la protection de nouvelle génération](#configure-next-generation-protection) | Décrit comment configurer vos paramètres de protection nouvelle génération dans Microsoft Endpoint Manager  |
| 7  | [Configurer vos fonctionnalités de réduction de la surface d’attaque](#configure-your-attack-surface-reduction-capabilities)        | Répertorie les types de fonctionnalités de réduction de la surface d’attaque que vous pouvez configurer et inclut des procédures avec des liens vers d’autres ressources  |

> [!IMPORTANT]
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, express ou implicite, pour les informations fournies ici. Cet article contient des liens vers du contenu en ligne qui peut décrire certaines fonctionnalités qui ne sont pas incluses dans Defender for Endpoint Plan 1 (prévisualisation).
 
## <a name="review-the-requirements"></a>Consultez la configuration requise

Le tableau suivant répertorie les conditions de base requises pour Defender pour Endpoint Plan 1 (prévisualisation) :<br/><br/>

| Conditions requises | Description |
|:---|:---|
| Conditions d'octroi de licence | Defender for Endpoint Plan 1 (prévisualisation) <br/><br/>*Si vous avez Microsoft 365 E3, vous pouvez rejoindre le programme d’aperçu.* |
| Configuration requise pour le navigateur | Microsoft Edge <br/> Internet Explorer version 11 <br/> Google Chrome |
| Systèmes d’exploitation | Windows 10, version 1709 ou ultérieure <br/>macOS : 11.5 (Big Sur), 10.15.7 (Contrôle), ou 10.14.6 (Mojave) <br/>iOS <br/>Système d’exploitation Android  |
| Datacenter | L’un des emplacements de centre de données suivants : <br/>- Union européenne <br/>- Royaume-Uni <br/>- États-Unis |


## <a name="plan-your-deployment"></a>Planifier votre déploiement

Lorsque vous planifiez votre déploiement, vous pouvez choisir parmi différentes architectures et méthodes de déploiement. Chaque organisation étant unique, vous avez plusieurs options à envisager, comme répertorié dans le tableau suivant : <br/><br/>

| Méthode | Description |
|:---|:---|
| [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (inclus dans Microsoft Endpoint Manager) | Utiliser Intune pour gérer les points de terminaison dans un environnement natif cloud |
| [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) configuration [manager](/mem/configmgr/core/understand/introduction) (inclus dans Microsoft Endpoint Manager) | Utiliser Intune et Configuration Manager pour gérer les points de terminaison et les charges de travail qui couvrent un environnement local et cloud |
| [Gestionnaire de configuration](/mem/configmgr/core/understand/introduction) | Utiliser Configuration Manager pour protéger les points de terminaison locaux avec la puissance basée sur le cloud de Defender for Endpoint |
| Script local téléchargé à partir du portail Microsoft 365 Defender | Utiliser des scripts locaux sur les points de terminaison pour exécuter un pilote ou intégrer seulement quelques appareils |

Pour en savoir plus sur les options de déploiement, voir [Planifier votre defender pour le déploiement de point de terminaison.](deployment-strategy.md) Téléchargez également l’affiche suivante : 

[:::image type="content" source="../../media/defender-endpoint/mde-deployment-strategy.png" alt-text="Miniature de l’affiche stratégie de déploiement":::](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf)

**[Obtenir l’affiche de déploiement](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf)**

> [!TIP]
> Pour plus d’informations sur la planification de votre déploiement, voir [Plan your Microsoft Defender for Endpoint deployment](deployment-strategy.md).

## <a name="set-up-your-tenant-environment"></a>Configurer votre environnement client

La configuration de votre environnement client inclut des tâches, telles que :

- Vérification de vos licences
- Configuration de votre client
- Configuration de vos paramètres proxy (uniquement si nécessaire)
- S’assurer que les capteurs fonctionnent correctement et signaler les données à Defender for Endpoint 

Ces tâches sont incluses dans la phase d’installation de Defender pour Endpoint. Voir [Set up Defender for Endpoint](production-deployment.md).

## <a name="assign-roles-and-permissions"></a>Attribuer des rôles et des autorisations

Pour accéder au portail Microsoft 365 Defender, configurer les paramètres de Defender pour Endpoint ou effectuer des tâches, telles que l’exécution d’actions de réponse sur les menaces détectées, des autorisations appropriées doivent être attribuées. Defender for Endpoint utilise [des rôles intégrés dans Azure Active Directory](/azure/active-directory/roles/permissions-reference). 

Microsoft recommande d’attribuer uniquement aux utilisateurs le niveau d’autorisation dont ils ont besoin pour effectuer leurs tâches. Vous pouvez attribuer des autorisations à l’aide de la gestion des autorisations de base ou du contrôle d’accès basé sur un rôle [](rbac.md) (RBAC). 

- Avec la gestion des autorisations de base, les administrateurs globaux et les administrateurs de sécurité ont un accès total, tandis que les lecteurs de sécurité ont accès en lecture seule.
- Avec le RBAC, vous pouvez définir des autorisations plus granulaires par le biais de rôles plus nombreux. Par exemple, vous pouvez avoir des lecteurs de sécurité, des opérateurs de sécurité, des administrateurs de sécurité, des administrateurs de points de terminaison, etc.


Le tableau suivant décrit les rôles clés à prendre en compte pour Defender for Endpoint dans votre organisation : <br/><br/>

| Role | Description |
|:---|:---|
| Administrateurs globaux (également appelés administrateurs globaux) <br/><br/> *En tant que meilleure pratique, limitez le nombre d’administrateurs globaux.* | Les administrateurs globaux peuvent effectuer toutes sortes de tâches. La personne qui a inscrit votre entreprise à Microsoft 365 ou Microsoft Defender pour Endpoint Plan 1 est un administrateur général par défaut. <br/><br/> Les administrateurs globaux peuvent accéder/modifier les paramètres sur tous les portails Microsoft 365, tels que : <br/>- Le Centre d’administration Microsoft 365 ( [https://admin.microsoft.com](https://admin.microsoft.com) ) <br/>- Microsoft 365 Defender portail ( [https://security.microsoft.com](https://security.microsoft.com) ) <br/>- Microsoft Endpoint Manager centre d’administration ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) )  |
| Administrateurs de sécurité (également appelés administrateurs de sécurité) | Les administrateurs de sécurité peuvent effectuer des tâches d’opérateur de sécurité ainsi que les tâches suivantes : <br/>- Surveiller les stratégies liées à la sécurité <br/>- Gérer les menaces et alertes de sécurité <br/>- Afficher les rapports |
| Opérateur de sécurité | Les opérateurs de sécurité peuvent effectuer des tâches de lecteur de sécurité ainsi que les tâches suivantes : <br/>- Afficher des informations sur les menaces détectées <br/>- Examiner les menaces détectées et y répondre  |
| Lecteur Sécurité | Les lecteurs de sécurité peuvent effectuer les tâches suivantes : <br/>- Afficher les stratégies liées à la sécurité dans Microsoft 365 services <br/>- Afficher les menaces et alertes de sécurité <br/>- Afficher les rapports  |


> [!TIP]
> Pour en savoir plus sur les rôles Azure Active Directory, voir Attribuer des rôles d’administrateur et [non administrateur](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal)aux utilisateurs Azure Active Directory . Et, plus d’informations sur les rôles pour Defender pour le point de terminaison, voir [Contrôle d’accès basé sur les rôles.](prepare-deployment.md#role-based-access-control)

## <a name="onboard-to-defender-for-endpoint"></a>Intégration à Defender pour le point de terminaison

Lorsque vous êtes prêt à intégrer les points de terminaison de votre organisation, vous pouvez choisir parmi plusieurs méthodes, comme répertorié dans le tableau suivant : <br/><br/>

|Système d’exploitation de point de terminaison | Méthodes d’intégration|
|---|---|
| Windows 10 | [Script local (jusqu’à 10 appareils)](configure-endpoints-script.md) <br>  [Stratégie de groupe](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Gestionnaire de périphériques mobiles](configure-endpoints-mdm.md) <br> [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Scripts VDI](configure-endpoints-vdi.md)  |
| macOS | [Scripts locaux](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JamF Pro](mac-install-with-jamf.md) <br> [Gestion des appareils mobiles](mac-install-with-other-mdm.md) |
| iOS |[Basée sur l’application](ios-install.md) |
| Android | [Microsoft Endpoint Manager](android-intune.md) |

Ensuite, configurez vos fonctionnalités de protection et de réduction de la surface d’attaque nouvelle génération.

## <a name="configure-next-generation-protection"></a>Configurer la protection de nouvelle génération

Nous vous recommandons [d’Microsoft Endpoint Manager](/mem) pour gérer les appareils et les paramètres de sécurité de votre organisation, comme illustré dans l’image suivante :
 
:::image type="content" source="../../media/mde-p1/endpoint-policies.png" alt-text="Stratégies de sécurité de point de terminaison dans MEM":::

Pour configurer votre protection nouvelle génération dans Microsoft Endpoint Manager, suivez les étapes suivantes :

1. Go to the Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ) and sign in.

2. Sélectionnez **l’Antivirus de sécurité des** points de  >  terminaison, puis sélectionnez une stratégie existante. (Si vous n’avez pas de stratégie existante, créez-en une.)

3. Définissez ou modifiez vos paramètres de configuration antivirus. Vous avez besoin d’aide ? Reportez-vous aux ressources suivantes : <br/>

   - [Paramètres pour Windows 10 Antivirus Microsoft Defender stratégie dans Microsoft Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-windows)
   - [Configurer Defender pour endpoint sur les fonctionnalités iOS](ios-configure-features.md)

4. Lorsque vous avez terminé de spécifier vos paramètres, choisissez **Révision + enregistrer.**

## <a name="configure-your-attack-surface-reduction-capabilities"></a>Configurer vos fonctionnalités de réduction de la surface d’attaque

La réduction de la surface d’attaque consiste à réduire les lieux et les moyens d’attaque de votre organisation. Defender pour le point de terminaison Plan 1 (prévisualisation) inclut plusieurs fonctionnalités et fonctionnalités pour vous aider à réduire vos surfaces d’attaque sur vos points de terminaison. Ces fonctionnalités sont répertoriées dans le tableau suivant : <br/><br/>

| Fonctionnalité/fonctionnalité | Description |
|:---|:---|
| [Règles de réduction de la surface d’attaque](#attack-surface-reduction-rules) | Configurez les règles de réduction de la surface d’attaque pour limiter les comportements à risque logiciels et contribuer à la sécurité de votre organisation. Les règles de réduction de la surface d’attaque ciblent certains comportements logiciels, tels que<br/>- Lancement de fichiers exécutables et de scripts qui tentent de télécharger ou d’exécuter des fichiers <br/>- Exécution de scripts obscurcis ou suspects <br/>- Effectuer des comportements que les applications n’initient généralement pas pendant le travail quotidien normal <br/><br/>De tels comportements logiciels sont parfois observés dans les applications légitimes. Toutefois, ces comportements sont souvent considérés comme risqués, car ils sont couramment abusés par des personnes malveillantes par le biais de programmes malveillants.  |
| [Atténuation des ransomware](#ransomware-mitigation) | Configurez l’atténuation des ransomware en configurant l’accès contrôlé aux dossiers, ce qui permet de protéger les données précieuses de votre organisation contre les applications malveillantes et les menaces, telles que les ransomware. | 
| [Contrôle des appareils](#device-control) | Configurez les paramètres de contrôle d’appareil pour que votre organisation autorise ou bloque les appareils amovibles (tels que les lecteurs USB). | 
| [Protection du réseau](#network-protection) | Configurer la protection réseau pour empêcher les membres de votre organisation d’utiliser des applications qui accèdent à des domaines dangereux ou à du contenu malveillant sur Internet. |
| [Protection web](#web-protection) | Configurer la protection contre les menaces web pour protéger les appareils de votre organisation contre les sites d’hameçonnage, les sites d’attaque et d’autres sites de faible réputation ou non confiance. Configurer le filtrage de contenu web pour suivre et contrôler l’accès aux sites web en fonction de leurs catégories de contenu (par exemple, Catégorie, Bande passante élevée, Contenu pour adultes ou Responsabilité légale). |
| [Pare-feu réseau](#network-firewall) | Configurez votre pare-feu réseau avec des règles qui déterminent le trafic réseau autorisé à entrer ou à sortir des appareils de votre organisation. |
| [Contrôle d’application](#application-control)  | Configurez les règles de contrôle des applications si vous souhaitez autoriser uniquement les applications et processus de confiance à s’exécuter sur Windows appareils.    |

### <a name="attack-surface-reduction-rules"></a>Règles de réduction de la surface d’attaque

Les règles de réduction de la surface d’attaque sont disponibles sur les appareils exécutant Windows. Nous vous recommandons d’Microsoft Endpoint Manager, comme illustré dans l’image suivante :

:::image type="content" source="../../media/mde-p1/mem-asrpolicies.png" alt-text="Règles de réduction de la surface d’attaque Microsoft Endpoint Manager":::

1. Go to the Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ) and sign in.

2. Choisissez **Réduction de la surface**  >  **d’attaque** du point de terminaison + Créer une  >  **stratégie.**

3. Pour **la plateforme,** **sélectionnez Windows 10 et ultérieures.**

4. For **Profile**, select **Attack surface reduction rules,** and then choose **Create**.

5. Sous **l’onglet Éléments de** base, spécifiez un nom et une description pour la stratégie, puis choisissez **Suivant**.

6. Sous **l’onglet Paramètres de configuration,** développez Règles de réduction **de la surface d’attaque.**

7. Spécifiez les paramètres de chaque règle, puis choisissez **Suivant**. (Pour plus d’informations sur le travail de chaque règle, voir Règles de réduction de [la surface d’attaque.)](attack-surface-reduction.md) 

8. Sous **l’onglet Balises** d’étendue, si votre organisation utilise des balises d’étendue, choisissez **+** Sélectionner des balises d’étendue, puis sélectionnez les balises que vous souhaitez utiliser. Ensuite, choisissez **Suivant**. 
   
   Pour en savoir plus sur les balises d’étendue, voir Utiliser un contrôle d’accès basé sur un rôle [(RBAC)](/mem/intune/fundamentals/scope-tags)et des balises d’étendue pour le service it distribué.

9. Sous **l’onglet Affectations,** spécifiez les utilisateurs et les groupes auxquels votre stratégie doit être appliquée, puis choisissez **Suivant**. (Pour en savoir plus sur les affectations, voir Affecter des profils d’utilisateur et [d’appareil Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

10. Sous **l’onglet Révision + créer,** examinez les paramètres, puis choisissez **Créer.**

> [!TIP]
> Pour en savoir plus sur les règles de réduction de la surface d’attaque, consultez les ressources suivantes :
> - [Utiliser des règles de réduction de la surface d’attaque pour empêcher l’infection des programmes malveillants](attack-surface-reduction.md)
> - [Afficher la liste des règles de réduction de la surface d’attaque](attack-surface-reduction-rules.md)
> - [Personnaliser les règles de réduction de la surface d’attaque](customize-attack-surface-reduction.md)

### <a name="ransomware-mitigation"></a>Atténuation des ransomware

Vous obtenez une atténuation de ransomware via [l’accès](controlled-folders.md#what-is-controlled-folder-access)contrôlé aux dossiers, qui permet uniquement aux applications de confiance d’accéder aux dossiers protégés sur vos points de terminaison. 

Nous vous recommandons d’Microsoft Endpoint Manager pour configurer l’accès contrôlé aux dossiers.

:::image type="content" source="../../media/mde-p1/mem-asrpolicies.png" alt-text="Stratégies de asr dans Microsoft Endpoint Manager":::

1. Go to the Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ) and sign in. 

2. Sélectionnez **Sécurité des points de** terminaison, puis Réduction de la surface **d’attaque.**

3. Choisissez **+ Créer une stratégie.** 

4. Pour **la plateforme,** **sélectionnez Windows 10 et ultérieures,** et pour **Profil,** sélectionnez Règles de réduction **de la surface d’attaque.** Ensuite, choisissez **Créer**. 

5. Sous **l’onglet Éléments de** base, nommez la stratégie et ajoutez une description. Sélectionnez **Suivant**. 

6. Sous **l’onglet Paramètres de configuration,** dans la section Règles de réduction de la **surface** d’attaque, faites défiler vers le bas. Dans la **drop-down Activer la protection** des dossiers, **sélectionnez Activer.** Vous pouvez éventuellement spécifier ces autres paramètres :

   - En plus de la liste des **dossiers** supplémentaires qui doivent être protégés, sélectionnez le menu déroulant, puis ajoutez les dossiers qui doivent être protégés.
   - En plus de la liste des applications qui ont accès aux **dossiers** protégés, sélectionnez le menu déroulant, puis ajoutez les applications qui doivent avoir accès aux dossiers protégés.
   - En plus d’exclure des fichiers et des chemins d’accès des règles de réduction de **la surface** d’attaque, sélectionnez le menu déroulant, puis ajoutez les fichiers et les chemins d’accès qui doivent être exclus des règles de réduction de la surface d’attaque.

   Sélectionnez **Suivant**.

7. Sous **l’onglet Balises** d’étendue, si votre organisation utilise des balises d’étendue, choisissez **+** Sélectionner des balises d’étendue, puis sélectionnez les balises que vous souhaitez utiliser. Ensuite, choisissez **Suivant**. 
   
   Pour en savoir plus sur les balises d’étendue, voir Utiliser un contrôle d’accès basé sur un rôle [(RBAC)](/mem/intune/fundamentals/scope-tags)et des balises d’étendue pour le service it distribué.

8. Sous **l’onglet Affectations,** **sélectionnez Ajouter** tous les utilisateurs et + Ajouter tous les **appareils,** puis choisissez **Suivant**. (Vous pouvez également spécifier des groupes spécifiques d’utilisateurs ou d’appareils.)

9. Sous **l’onglet Révision + créer,** examinez les paramètres de votre stratégie, puis choisissez **Créer.** La stratégie sera appliquée à tous les points de terminaison qui ont été prochainement intégrés à Defender for Endpoint.

### <a name="device-control"></a>Contrôle d’appareil

Vous pouvez configurer Defender pour le point de terminaison pour bloquer ou autoriser les appareils et fichiers amovibles sur les appareils amovibles. Nous vous recommandons d’Microsoft Endpoint Manager pour configurer les paramètres de contrôle de votre appareil.

:::image type="content" source="../../media/mde-p1/mem-admintemplates.png" alt-text="Microsoft Endpoint Manager modèles d’administration":::

1. Go to the Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ) and sign in. 

2. Sélectionnez   >  **profils de configuration des appareils** Créer un  >  **profil.**

3. Pour **la plateforme,** **sélectionnez Windows 10 et ultérieures,** et pour le type de **profil,** sélectionnez **Modèles.** 

   Sous **Nom du modèle,** **sélectionnez Modèles d’administration,** puis **créez.** 

4. Sous **l’onglet Éléments de** base, nommez la stratégie et ajoutez une description. Sélectionnez **Suivant**. 

5. Sous **l’onglet Paramètres de configuration,** **sélectionnez Tous Paramètres**. Ensuite, dans la zone de recherche, tapez pour voir tous `Removable` les paramètres relatifs aux appareils amovibles.

6. Sélectionnez un élément dans la liste, tel que toutes les classes de Stockage **amovibles**: Refuser tout accès, pour ouvrir son volet volant. Le volant de chaque paramètre explique ce qui se produit lorsqu’il est activé, désactivé ou n’est pas configuré. Sélectionnez un paramètre, puis choisissez **OK.** 

7. Répétez l’étape 6 pour chaque paramètre à configurer. Sélectionnez **Suivant**.

8. Sous **l’onglet Balises** d’étendue, si votre organisation utilise des balises d’étendue, choisissez **+** Sélectionner des balises d’étendue, puis sélectionnez les balises que vous souhaitez utiliser. Ensuite, choisissez **Suivant**. 
   
   Pour en savoir plus sur les balises d’étendue, voir Utiliser un contrôle d’accès basé sur un rôle [(RBAC)](/mem/intune/fundamentals/scope-tags)et des balises d’étendue pour le service it distribué.

9. Sous **l’onglet Affectations,** **sélectionnez Ajouter** tous les utilisateurs et + Ajouter tous les **appareils,** puis choisissez **Suivant**. (Vous pouvez également spécifier des groupes spécifiques d’utilisateurs ou d’appareils.)

10. Sous **l’onglet Révision + créer,** examinez les paramètres de votre stratégie, puis choisissez **Créer.** La stratégie sera appliquée à tous les points de terminaison qui ont été prochainement intégrés à Defender for Endpoint.

> [!TIP]
> Pour plus d’informations, voir Comment contrôler des périphériques USB et d’autres supports amovibles à l’aide [de Microsoft Defender pour endpoint](control-usb-devices-using-intune.md).

### <a name="network-protection"></a>Protection réseau

Grâce à la protection du réseau, vous pouvez protéger votre organisation contre les domaines dangereux qui peuvent héberger des tentatives d’hameçonnage, des attaques et d’autres contenus malveillants sur Internet. Nous vous recommandons d’Microsoft Endpoint Manager pour activer la protection réseau.

:::image type="content" source="../../media/mde-p1/mem-endpointprotectionprofile.png" alt-text="Profil de protection des points de terminaison dans Microsoft Endpoint Manager":::

1. Go to the Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ) and sign in. 

2. Sélectionnez   >  **profils de configuration des appareils** Créer un  >  **profil.**

3. Pour **la plateforme,** **sélectionnez Windows 10 et ultérieures,** et pour le type de **profil,** sélectionnez **Modèles.** 

   Sous **Nom du modèle,** **sélectionnez Endpoint Protection,** puis **créez**. 

4. Sous **l’onglet Éléments de** base, nommez la stratégie et ajoutez une description. Sélectionnez **Suivant**. 

5. Sous **l’onglet Paramètres de configuration,** **développez Protection contre les attaques Microsoft Defender,** puis développez Filtrage **réseau.**

   Définissez **la protection réseau** sur **Activer.** (Vous pouvez également choisir **Audit** pour voir comment la protection réseau fonctionne dans votre environnement.)

   Sélectionnez **Suivant**.

6. Sous **l’onglet Affectations,** **sélectionnez Ajouter** tous les utilisateurs et + Ajouter tous les **appareils,** puis choisissez **Suivant**. (Vous pouvez également spécifier des groupes spécifiques d’utilisateurs ou d’appareils.)

7. Sous **l’onglet Règles d’applicabilité,** définissez une règle. Le profil que vous configurez sera appliqué uniquement aux appareils qui répondent aux critères combinés que vous spécifiez. 

   Par exemple, vous pouvez choisir d’affecter la stratégie aux points de terminaison qui exécutent une certaine édition du système d’exploitation uniquement.

   Sélectionnez **Suivant**. 

8. Sous **l’onglet Révision + créer,** examinez les paramètres de votre stratégie, puis choisissez **Créer.** La stratégie sera appliquée à tous les points de terminaison qui ont été prochainement intégrés à Defender for Endpoint.

> [!TIP]
> Vous pouvez utiliser d’autres méthodes, telles que Windows PowerShell ou une stratégie de groupe, pour activer la protection du réseau. Pour en savoir plus, voir [Activer la protection réseau.](enable-network-protection.md)

### <a name="web-protection"></a>Protection Web

Grâce à la protection web, vous pouvez protéger les appareils de votre organisation contre les menaces web et le contenu indésirable. Votre protection web inclut la [protection contre les menaces web](#configure-web-threat-protection) et le filtrage de contenu [web](#configure-web-content-filtering) (aperçu). Configurez les deux ensembles de fonctionnalités. Nous vous recommandons d’Microsoft Endpoint Manager pour configurer vos paramètres de protection web.

#### <a name="configure-web-threat-protection"></a>Configurer la protection contre les menaces web

1. Go to the Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ), and sign in.
 
2. Choisissez **Réduction de la**  >  **surface d’attaque** du point de terminaison de sécurité, puis choisissez + Créer une **stratégie.**

3. Sélectionnez une plateforme, telle que **Windows 10 et ultérieures,** sélectionnez le profil **de protection Web,** puis choisissez **Créer.** 

4. Sous **l’onglet Éléments de** base, spécifiez un nom et une description, puis choisissez **Suivant**.

5. Sous **l’onglet Paramètres de configuration,** développez **Protection Web,** spécifiez les paramètres dans le tableau suivant, puis choisissez **Suivant**. <br/><br/>

   | Setting | Recommandation |
   |:---|:---|
   | **Activer la protection réseau** | Définir sur **Activé**. Empêche les utilisateurs de visiter des sites ou domaines malveillants. <br/><br/>Vous pouvez également définir la protection réseau en **mode Audit** pour voir comment elle fonctionne dans votre environnement. En mode audit, la protection réseau n’empêche pas les utilisateurs de visiter des sites ou des domaines, mais elle fait le suivi des détections en tant qu’événements. |
   | **Exiger SmartScreen pour les Version antérieure de Microsoft Edge** | Définir sur **Oui**. Permet de protéger les utilisateurs contre les tentatives de hameçonnage et les logiciels malveillants potentiels. |
   | **Bloquer l’accès aux sites malveillants** | Définir sur **Oui**. Empêche les utilisateurs de contourner les avertissements concernant les sites potentiellement malveillants. |
   | **Bloquer le téléchargement de fichiers non vérifiées** | Définir sur **Oui**. Empêche les utilisateurs de contourner les avertissements et de télécharger des fichiers non vérifiées. |

6. Sous **l’onglet Balises** d’étendue, si votre organisation utilise des balises d’étendue, choisissez **+** Sélectionner des balises d’étendue, puis sélectionnez les balises que vous souhaitez utiliser. Ensuite, choisissez **Suivant**. 
   
   Pour en savoir plus sur les balises d’étendue, voir Utiliser un contrôle d’accès basé sur un rôle [(RBAC)](/mem/intune/fundamentals/scope-tags)et des balises d’étendue pour le service it distribué.

7. Sous **l’onglet Affectations,** spécifiez les utilisateurs et les appareils pour recevoir la stratégie de protection web, puis choisissez **Suivant**.

8. Sous **l’onglet Révision + créer,** examinez vos paramètres de stratégie, puis choisissez **Créer.**

> [!TIP]
> Pour en savoir plus sur la protection contre les menaces web, voir Protéger votre organisation contre [les menaces web.](web-threat-protection.md)

#### <a name="configure-web-content-filtering"></a>Configurer le filtrage de contenu web

> [!NOTE]
> Le filtrage de contenu Web est actuellement en prévisualisation.

1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com/](https://security.microsoft.com/) ) and sign in.

2. Choisissez **Paramètres**  >  **points de terminaison.**

3. Sous **Règles,** choisissez **filtrage de contenu Web,** puis choisissez + Ajouter une **stratégie**.

4. Dans le **volant Ajouter une** stratégie, sous l’onglet **Général,** spécifiez un nom pour votre stratégie, puis choisissez **Suivant**.

5. Dans les **catégories bloquées,** sélectionnez une ou plusieurs catégories que vous souhaitez bloquer, puis choisissez **Suivant**.

6. Sous **l’onglet** Étendue, sélectionnez les groupes d’appareils que vous souhaitez recevoir cette stratégie, puis choisissez **Suivant**.

7. Sous **l’onglet Résumé,** examinez vos paramètres de stratégie, puis sélectionnez **Enregistrer.**

> [!TIP]
> Pour en savoir plus sur la configuration du filtrage de contenu web, voir [Filtrage de contenu Web.](web-content-filtering.md)

### <a name="network-firewall"></a>Pare-feu réseau

Le pare-feu réseau permet de réduire les risques de menaces de sécurité réseau. Votre équipe de sécurité peut définir des règles qui déterminent le trafic autorisé à circuler vers ou depuis les appareils de votre organisation. Nous vous recommandons d’Microsoft Endpoint Manager pour configurer votre pare-feu réseau. 

:::image type="content" source="../../media/mde-p1/mem-firewallpolicy.png" alt-text="Stratégie de pare-feu dans Microsoft Endpoint Manager":::

Pour configurer les paramètres de pare-feu de base, suivez les étapes suivantes :

1. Go to the Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ), and sign in.

2. Choose **Endpoint security**  >  **Firewall,** and then choose **+ Create Policy**.

3. Sélectionnez une plateforme, telle que **Windows 10 et** ultérieures, sélectionnez le profil pare-feu **Microsoft Defender,** puis choisissez **Créer.** 

4. Sous **l’onglet Éléments de** base, spécifiez un nom et une description, puis choisissez **Suivant**.

5. Développez **le Pare-feu Microsoft Defender,** puis faites défiler vers le bas de la liste.

6. Définissez chacun des paramètres suivants sur **Oui**:

   - **Activer le Pare-feu Microsoft Defender pour les réseaux de domaine** 
   - **Activer le Pare-feu Microsoft Defender pour les réseaux privés**
   - **Activer le Pare-feu Microsoft Defender pour les réseaux publics**
   
   Examinez la liste des paramètres sous chacun des réseaux de domaine, réseaux privés et réseaux publics. Vous pouvez les laisser définies sur **Non** configuré ou les modifier en fonction des besoins de votre organisation.

   Sélectionnez **Suivant**.

7. Sous **l’onglet Balises** d’étendue, si votre organisation utilise des balises d’étendue, choisissez **+** Sélectionner des balises d’étendue, puis sélectionnez les balises que vous souhaitez utiliser. Ensuite, choisissez **Suivant**. 
   
   Pour en savoir plus sur les balises d’étendue, voir Utiliser un contrôle d’accès basé sur un rôle [(RBAC)](/mem/intune/fundamentals/scope-tags)et des balises d’étendue pour le service it distribué.

8. Sous **l’onglet Affectations,** **sélectionnez Ajouter** tous les utilisateurs et + Ajouter tous les **appareils,** puis choisissez **Suivant**. (Vous pouvez également spécifier des groupes spécifiques d’utilisateurs ou d’appareils.)

9. Sous **l’onglet Révision + créer,** examinez vos paramètres de stratégie, puis choisissez **Créer.**

> [!TIP]
> Les paramètres de pare-feu sont détaillés et peuvent sembler complexes. [Reportez-vous aux meilleures pratiques pour configurer Windows Defender pare-feu.](/windows/security/threat-protection/windows-firewall/best-practices-configuring)

### <a name="application-control"></a>Contrôle d’application

Windows Defender Le contrôle d’application (WDAC) permet de protéger vos points de terminaison Windows en permettant uniquement l’utilisation d’applications et de processus fiables. La plupart des organisations ont utilisé un déploiement par phases de WDAC. En d’autres cas, la plupart des organisations ne lancent pas WDAC sur tous Windows points de terminaison au premier abord. En fait, selon que les points de terminaison Windows de votre organisation sont entièrement gérés, légèrement gérés ou « Apportez votre propre appareil », vous pouvez déployer WDAC sur tous les points de terminaison ou sur certains points de terminaison.

Pour vous aider à planifier votre déploiement WDAC, consultez les ressources suivantes :

- [Contrôle d’application pour Windows](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)

- [Windows Defender Décisions de conception de stratégie de contrôle d’application](/windows/security/threat-protection/windows-defender-application-control/understand-windows-defender-application-control-policy-design-decisions)

- [Windows Defender Déploiement du contrôle d’application dans différents scénarios : types d’appareils](/windows/security/threat-protection/windows-defender-application-control/types-of-devices)

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez passé par le processus d’installation et de configuration, l’étape suivante consiste à commencer à utiliser Defender pour Endpoint. 

- [Mise en place de Defender pour Endpoint Plan 1 (prévisualisation)](mde-plan1-getting-started.md)