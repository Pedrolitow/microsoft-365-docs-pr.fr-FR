---
title: Configurer et configurer Microsoft Defender pour point de terminaison Plan 1
description: Découvrez comment configurer Defender pour point de terminaison Plan 1. Passez en revue les exigences, planifiez votre déploiement et configurez votre environnement.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: e94a0ee04d45e92d5891c73ba3a70ac2f05cd482
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66485954"
---
# <a name="set-up-and-configure-microsoft-defender-for-endpoint-plan-1"></a>Configurer et configurer Microsoft Defender pour point de terminaison Plan 1

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Cet article explique comment configurer Defender pour point de terminaison Plan 1. Que vous ayez de l’aide ou que vous le faisiez vous-même, vous pouvez utiliser cet article comme guide tout au long de votre déploiement.  

## <a name="the-setup-and-configuration-process"></a>Processus d’installation et de configuration

:::image type="content" source="images/mde-p1-deploymentflow.png" alt-text="Flux d’installation et de déploiement pour Microsoft Defender pour point de terminaison Plan 1" lightbox="images/mde-p1-deploymentflow.png":::

Le processus d’installation et de configuration général de Defender pour point de terminaison Plan 1 est le suivant : <br/><br/>


| Nombre  | Étape  | Description  |
|:---------:|:---------|:---------|
| 1 | [Consultez la configuration requise](#review-the-requirements)  | Répertorie les exigences en matière de licences, de navigateur, de système d’exploitation et de centre de données   |
| 2 | [Planifier votre déploiement](#plan-your-deployment) | Répertorie plusieurs méthodes de déploiement à prendre en compte et inclut des liens vers d’autres ressources pour vous aider à déterminer la méthode à utiliser  |
| 3 | [Configurer votre environnement de locataire](#set-up-your-tenant-environment) | Répertorie les tâches de configuration de votre environnement de locataire |
| 4 | [Attribuer des rôles et des autorisations](#assign-roles-and-permissions) | Répertorie les rôles et les autorisations à prendre en compte pour votre équipe de sécurité <br/><br/>**CONSEIL** : Dès que des rôles et des autorisations sont attribués, votre équipe de sécurité peut commencer à utiliser le portail Microsoft 365 Defender. Pour en savoir plus, consultez [Prise en main](mde-plan1-getting-started.md). |
| 5 | [Intégrer à Defender pour point de terminaison](#onboard-to-defender-for-endpoint) | Répertorie plusieurs méthodes par système d’exploitation à intégrer à Defender pour point de terminaison Plan 1 et inclut des liens vers des informations plus détaillées pour chaque méthode  |
| 6  | [Configurer la protection de nouvelle génération](#configure-next-generation-protection) | Décrit comment configurer vos paramètres de protection de nouvelle génération dans Microsoft Endpoint Manager  |
| 7  | [Configurer vos fonctionnalités de réduction de la surface d’attaque](#configure-your-attack-surface-reduction-capabilities)        | Répertorie les types de fonctionnalités de réduction de la surface d’attaque que vous pouvez configurer et inclut des procédures avec des liens vers d’autres ressources  |
 
## <a name="review-the-requirements"></a>Consultez la configuration requise

Le tableau suivant répertorie les exigences de base pour Defender pour point de terminaison Plan 1 :<br/><br/>

| Conditions requises | Description |
|:---|:---|
| Conditions d'octroi de licence | Defender pour point de terminaison Plan 1 (autonome ou dans le cadre de Microsoft 365 E3 ou A3) |
| Configuration requise pour le navigateur | Microsoft Edge <br/> Internet Explorer version 11 <br/> Google Chrome |
| Systèmes d’exploitation | Windows 11 ou Windows 10, version 1709 ou ultérieure <br/>macOS (les trois versions les plus récentes sont prises en charge) <br/>iOS <br/>Système d’exploitation Android <br/><br/>Notez que la version autonome de Defender pour point de terminaison Plan 1 n’inclut pas de licences serveur. Pour intégrer des serveurs, vous avez besoin de Defender pour serveurs Plan 1 ou Plan 2 dans le cadre de l’offre [Defender pour cloud](/azure/defender-for-cloud/defender-for-cloud-introduction) . Pour en savoir plus. Consultez [vue d’ensemble de Microsoft Defender pour serveurs](/azure/defender-for-cloud/defender-for-servers-introduction). |
| Datacenter | L’un des emplacements de centre de données suivants : <br/>- Union européenne <br/>- Royaume-Uni <br/>- États-Unis |


## <a name="plan-your-deployment"></a>Planifier votre déploiement

Lorsque vous planifiez votre déploiement, vous pouvez choisir parmi plusieurs architectures et méthodes de déploiement différentes. Chaque organisation étant unique, vous avez plusieurs options à prendre en compte, comme indiqué dans le tableau suivant : <br/><br/>

| Méthode | Description |
|:---|:---|
| [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (inclus dans Microsoft Endpoint Manager) | Utiliser Intune pour gérer les points de terminaison dans un environnement natif cloud |
| [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) et [Configuration Manager](/mem/configmgr/core/understand/introduction) (inclus dans Microsoft Endpoint Manager) | Utiliser Intune et Configuration Manager pour gérer les points de terminaison et les charges de travail qui s’étendent sur un environnement local et cloud |
| [Configuration Manager](/mem/configmgr/core/understand/introduction) | Utiliser Configuration Manager pour protéger les points de terminaison locaux avec la puissance cloud de Defender pour point de terminaison |
| Script local téléchargé à partir du portail Microsoft 365 Defender | Utiliser des scripts locaux sur des points de terminaison pour exécuter un pilote ou intégrer seulement quelques appareils |

Pour en savoir plus sur vos options de déploiement, consultez [Planifier votre déploiement Defender pour point de terminaison](deployment-strategy.md). Téléchargez l’affiche suivante : 

[:::image type="content" source="../../media/defender-endpoint/mde-deployment-strategy.png" alt-text="Miniature de l’affiche de stratégie de déploiement":::](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)

**[Obtenir l’affiche de déploiement](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)**

> [!TIP]
> Pour plus d’informations sur la planification de votre déploiement, consultez [Planifier votre déploiement Microsoft Defender pour point de terminaison](deployment-strategy.md).

## <a name="set-up-your-tenant-environment"></a>Configurer votre environnement de locataire

La configuration de votre environnement de locataire inclut des tâches, telles que :

- Vérification de vos licences
- Configuration de votre locataire
- Configuration de vos paramètres de proxy (uniquement si nécessaire)
- S’assurer que les capteurs fonctionnent correctement et signaler des données à Defender pour point de terminaison 

Ces tâches sont incluses dans la phase de configuration de Defender pour point de terminaison. Voir [Configurer Defender pour point de terminaison](production-deployment.md).

## <a name="assign-roles-and-permissions"></a>Attribuer des rôles et des autorisations

Pour accéder au portail Microsoft 365 Defender, configurer les paramètres de Defender pour point de terminaison ou effectuer des tâches, telles que l’exécution d’actions de réponse sur les menaces détectées, des autorisations appropriées doivent être attribuées. Defender pour point de terminaison utilise des [rôles intégrés dans Azure Active Directory](/azure/active-directory/roles/permissions-reference). 

Microsoft recommande d’attribuer aux utilisateurs uniquement le niveau d’autorisation dont ils ont besoin pour effectuer leurs tâches. Vous pouvez attribuer des autorisations à l’aide de la gestion des autorisations de base ou du [contrôle d’accès en fonction du rôle](rbac.md) (RBAC). 

- Avec la gestion des autorisations de base, les administrateurs généraux et les administrateurs de sécurité disposent d’un accès complet, tandis que les lecteurs de sécurité accèdent en lecture seule.
- Avec RBAC, vous pouvez définir des autorisations plus précises via plus de rôles. Par exemple, vous pouvez avoir des lecteurs de sécurité, des opérateurs de sécurité, des administrateurs de sécurité, des administrateurs de points de terminaison, etc.


Le tableau suivant décrit les rôles clés à prendre en compte pour Defender pour point de terminaison dans votre organisation : <br/><br/>

| Role | Description |
|:---|:---|
| Administrateurs généraux (également appelés administrateurs généraux) <br/><br/> *Il est recommandé de limiter le nombre d’administrateurs généraux.* | Les administrateurs généraux peuvent effectuer toutes sortes de tâches. La personne qui a inscrit votre entreprise pour Microsoft 365 ou pour Microsoft Defender pour point de terminaison Plan 1 est un administrateur général par défaut. <br/><br/> Les administrateurs généraux sont en mesure d’accéder aux paramètres/de les modifier sur tous les portails Microsoft 365, par exemple : <br/>- Le Centre d'administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) <br/>- Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  |
| Administrateurs de sécurité (également appelés administrateurs de sécurité) | Les administrateurs de sécurité peuvent effectuer des tâches d’opérateur de sécurité ainsi que les tâches suivantes : <br/>- Surveiller les stratégies liées à la sécurité <br/>- Gérer les menaces et les alertes de sécurité <br/>- Afficher les rapports |
| Opérateur de sécurité | Les opérateurs de sécurité peuvent effectuer des tâches de lecteur de sécurité ainsi que les tâches suivantes : <br/>- Afficher des informations sur les menaces détectées <br/>- Examiner et répondre aux menaces détectées  |
| Lecteur Sécurité | Les lecteurs de sécurité peuvent effectuer les tâches suivantes : <br/>- Afficher les stratégies liées à la sécurité dans les services Microsoft 365 <br/>- Afficher les menaces et alertes de sécurité <br/>- Afficher les rapports  |


> [!TIP]
> Pour en savoir plus sur les rôles dans Azure Active Directory, consultez [Attribuer des rôles d’administrateur et de non-administrateur aux utilisateurs avec Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal). Pour plus d’informations sur les rôles pour Defender pour point de terminaison, consultez [contrôle d’accès en fonction du rôle](prepare-deployment.md#role-based-access-control).

## <a name="onboard-to-defender-for-endpoint"></a>Intégrer à Defender pour point de terminaison

Lorsque vous êtes prêt à intégrer les points de terminaison de votre organisation, vous pouvez choisir parmi plusieurs méthodes, comme indiqué dans le tableau suivant : <br/><br/>

|Système d’exploitation de point de terminaison | Méthodes d’intégration|
|---|---|
| Windows 10 | [Script local (jusqu’à 10 appareils)](configure-endpoints-script.md) <br>  [Stratégie de groupe](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobile Gestionnaire de périphériques](configure-endpoints-mdm.md) <br> [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Scripts VDI](configure-endpoints-vdi.md)  |
| macOS | [Scripts locaux](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Gestion des appareils mobiles](mac-install-with-other-mdm.md) |
| iOS |[Basé sur l’application](ios-install.md) |
| Android | [Microsoft Endpoint Manager](android-intune.md) |

Ensuite, procédez à la configuration de vos fonctionnalités de protection et de réduction de la surface d’attaque de nouvelle génération.

## <a name="configure-next-generation-protection"></a>Configurer la protection de nouvelle génération

Nous vous recommandons d’utiliser [Microsoft Endpoint Manager](/mem) pour gérer les appareils et les paramètres de sécurité de votre organisation, comme illustré dans l’image suivante :
 
:::image type="content" source="../../media/mde-p1/endpoint-policies.png" alt-text="Stratégies de sécurité des points de terminaison dans le portail Endpoint Manager Micorosft" lightbox="../../media/mde-p1/endpoint-policies.png":::

Pour configurer votre protection de nouvelle génération dans Microsoft Endpoint Manager, procédez comme suit :

1. Accédez au Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous.

2. Sélectionnez **l’antivirus** **de sécurité** >  de point de terminaison, puis sélectionnez une stratégie existante. (Si vous n’avez pas de stratégie existante, créez une stratégie.)

3. Définissez ou modifiez les paramètres de configuration de votre antivirus. Besoin d’aide ? Reportez-vous aux ressources suivantes : <br/>

   - [Paramètres de Windows 10 stratégie antivirus Microsoft Defender dans Microsoft Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-windows)
   - [Configurer Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

4. Lorsque vous avez terminé de spécifier vos paramètres, **choisissez Vérifier + enregistrer**.

## <a name="configure-your-attack-surface-reduction-capabilities"></a>Configurer vos fonctionnalités de réduction de la surface d’attaque

La réduction de la surface d’attaque consiste à réduire les emplacements et les façons dont votre organisation est ouverte aux attaques. Defender pour point de terminaison Plan 1 inclut plusieurs fonctionnalités et fonctionnalités pour vous aider à réduire vos surfaces d’attaque sur vos points de terminaison. Ces fonctionnalités sont répertoriées dans le tableau suivant : <br/><br/>

| Fonctionnalité/fonctionnalité | Description |
|:---|:---|
| [Règles de réduction de la surface d’attaque](#attack-surface-reduction-rules) | Configurez des règles de réduction de la surface d’attaque pour limiter les comportements à risque basés sur des logiciels et contribuer à la sécurité de votre organisation. Les règles de réduction de la surface d’attaque ciblent certains comportements logiciels, tels que<br/>- Lancement de fichiers exécutables et de scripts qui tentent de télécharger ou d’exécuter des fichiers <br/>- Exécution de scripts masqués ou suspects <br/>- Exécution de comportements que les applications n’initient généralement pas pendant le travail quotidien normal <br/><br/>De tels comportements logiciels sont parfois observés dans les applications légitimes. Toutefois, ces comportements sont souvent considérés comme risqués, car ils sont couramment utilisés par les attaquants par le biais de programmes malveillants.  |
| [Atténuation des ransomwares](#ransomware-mitigation) | Configurez l’atténuation des ransomwares en configurant l’accès contrôlé aux dossiers, ce qui permet de protéger les données précieuses de votre organisation contre les applications malveillantes et les menaces, telles que les ransomware. | 
| [Contrôle des appareils](#device-control) | Configurez les paramètres de contrôle d’appareil pour que votre organisation autorise ou bloque les appareils amovibles (tels que les lecteurs USB). | 
| [Protection du réseau](#network-protection) | Configurez la protection réseau pour empêcher les membres de votre organisation d’utiliser des applications qui accèdent à des domaines dangereux ou à du contenu malveillant sur Internet. |
| [Protection web](#web-protection) | Configurez la protection contre les menaces web pour protéger les appareils de votre organisation contre les sites d’hameçonnage, les sites d’exploitation et d’autres sites non approuvés ou à faible réputation. Configurez le filtrage de contenu web pour suivre et réglementer l’accès aux sites web en fonction de leurs catégories de contenu (par exemple, Loisirs, Bande passante élevée, Contenu pour adultes ou Responsabilité légale). |
| [Pare-feu réseau](#network-firewall) | Configurez votre pare-feu réseau avec des règles qui déterminent le trafic réseau autorisé à entrer ou à sortir des appareils de votre organisation. |
| [Contrôle d’application](#application-control)  | Configurez des règles de contrôle d’application si vous souhaitez autoriser uniquement l’exécution d’applications et de processus approuvés sur vos appareils Windows.    |

### <a name="attack-surface-reduction-rules"></a>Règles de réduction des surfaces d'attaque

Des règles de réduction de la surface d’attaque sont disponibles sur les appareils exécutant Windows. Nous vous recommandons d’utiliser Microsoft Endpoint Manager, comme illustré dans l’image suivante :

:::image type="content" source="../../media/mde-p1/mem-asrpolicies.png" alt-text="Règles de réduction de la surface d’attaque dans le portail Microsoft Endpoint Manager" lightbox="../../media/mde-p1/mem-asrpolicies.png":::

1. Accédez au Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous.

2. Choisissez Réduction de **la surface d’attaque** >  de **sécurité** >  du point de terminaison **+ Créer une stratégie**.

3. Pour **Plateforme**, sélectionnez **Windows 10 et ultérieur**.

4. Pour **Profil**, sélectionnez **Règles de réduction de la surface** d’attaque, puis choisissez **Créer**.

5. Sous l’onglet **De base** , spécifiez un nom et une description pour la stratégie, puis choisissez **Suivant**.

6. Sous l’onglet **Paramètres de configuration** , développez **les règles de réduction de la surface d’attaque**.

7. Spécifiez les paramètres de chaque règle, puis choisissez **Suivant**. (Pour plus d’informations sur ce que fait chaque règle, consultez [les règles de réduction de la surface](attack-surface-reduction.md) d’attaque.) 

8. Sous l’onglet **Balises d’étendue** , si votre organisation utilise des balises d’étendue, **choisissez + Sélectionner des balises d’étendue**, puis sélectionnez les balises que vous souhaitez utiliser. Ensuite, choisissez **Suivant**. 
   
   Pour en savoir plus sur les balises d’étendue, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour le service informatique distribué](/mem/intune/fundamentals/scope-tags).

9. Sous l’onglet **Affectations** , spécifiez les utilisateurs et les groupes auxquels votre stratégie doit être appliquée, puis choisissez **Suivant**. (Pour en savoir plus sur les affectations, consultez [Affecter des profils d’utilisateur et d’appareil dans Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

10. Sous l’onglet **Vérifier + créer** , passez en revue les paramètres, puis choisissez **Créer**.

> [!TIP]
> Pour en savoir plus sur les règles de réduction de la surface d’attaque, consultez les ressources suivantes :
> - [Utiliser des règles de réduction de la surface d’attaque pour empêcher l’infection des programmes malveillants](attack-surface-reduction.md)
> - [Afficher la liste des règles de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md)
> - [Étape 3 du déploiement des règles de réduction de la surface d’attaque : Implémenter des règles ASR](attack-surface-reduction-rules-deployment-implement.md)

### <a name="ransomware-mitigation"></a>Atténuation des ransomwares

Vous bénéficiez de l’atténuation des ransomwares par [le biais d’un accès contrôlé aux dossiers](controlled-folders.md#what-is-controlled-folder-access), ce qui permet uniquement aux applications approuvées d’accéder aux dossiers protégés sur vos points de terminaison. 

Nous vous recommandons d’utiliser Microsoft Endpoint Manager pour configurer l’accès contrôlé aux dossiers.

:::image type="content" source="../../media/mde-p1/mem-asrpolicies.png" alt-text="Stratégies ASR dans le portail Microsoft Endpoint Manager" lightbox="../../media/mde-p1/mem-asrpolicies.png":::

1. Accédez au Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous. 

2. Sélectionnez Sécurité des points **de** terminaison, puis **Réduction de la surface d’attaque**.

3. Choisissez **+ Créer une stratégie**. 

4. Pour **La plateforme**, sélectionnez **Windows 10 et versions ultérieures**, puis, pour **Profil**, sélectionnez **Règles de réduction de la surface d’attaque**. Ensuite, choisissez **Créer**. 

5. Sous l’onglet **De base** , nommez la stratégie et ajoutez une description. Sélectionnez **Suivant**. 

6. Sous l’onglet **Paramètres de configuration** , dans la section **Règles de réduction de la surface d’attaque** , faites défiler vers le bas. Dans la liste **déroulante Activer la protection des dossiers** , sélectionnez **Activer**. Vous pouvez éventuellement spécifier ces autres paramètres :

   - En regard **de la liste des dossiers supplémentaires qui doivent être protégés**, sélectionnez le menu déroulant, puis ajoutez les dossiers qui doivent être protégés.
   - En regard **de La liste des applications qui ont accès à des dossiers protégés**, sélectionnez le menu déroulant, puis ajoutez les applications qui doivent avoir accès à des dossiers protégés.
   - En regard **d’Exclure les fichiers et les chemins des règles de réduction de la surface d’attaque**, sélectionnez le menu déroulant, puis ajoutez les fichiers et les chemins d’accès qui doivent être exclus des règles de réduction de la surface d’attaque.

   Sélectionnez **Suivant**.

7. Sous l’onglet **Balises d’étendue** , si votre organisation utilise des balises d’étendue, **choisissez + Sélectionner des balises d’étendue**, puis sélectionnez les balises que vous souhaitez utiliser. Ensuite, choisissez **Suivant**. 
   
   Pour en savoir plus sur les balises d’étendue, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour le service informatique distribué](/mem/intune/fundamentals/scope-tags).

8. Sous l’onglet **Affectations** , sélectionnez **Ajouter tous les utilisateurs** et **+ Ajouter tous les appareils**, puis choisissez **Suivant**. (Vous pouvez également spécifier des groupes spécifiques d’utilisateurs ou d’appareils.)

9. Sous l’onglet **Vérifier + créer** , passez en revue les paramètres de votre stratégie, puis choisissez **Créer**. La stratégie sera appliquée à tous les points de terminaison qui ont été intégrés à Defender pour point de terminaison sous peu.

### <a name="device-control"></a>Contrôle d’appareil

Vous pouvez configurer Defender pour point de terminaison pour bloquer ou autoriser les appareils et fichiers amovibles sur les appareils amovibles. Nous vous recommandons d’utiliser Microsoft Endpoint Manager pour configurer vos paramètres de contrôle d’appareil.

:::image type="content" source="../../media/mde-p1/mem-admintemplates.png" alt-text="Modèles d’administration Microsoft Endpoint Manager" lightbox="../../media/mde-p1/mem-admintemplates.png":::

1. Accédez au Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous. 

2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.

3. Pour **La plateforme**, sélectionnez **Windows 10 et versions ultérieures**, puis, pour **type de profil**, sélectionnez **Modèles**. 

   Sous **Nom du modèle**, sélectionnez **Modèles d’administration**, puis **choisissez Créer**. 

4. Sous l’onglet **De base** , nommez la stratégie et ajoutez une description. Sélectionnez **Suivant**. 

5. Sous l’onglet **Paramètres de configuration** , sélectionnez **Tous les paramètres**. Ensuite, dans la zone de recherche, tapez `Removable` tous les paramètres relatifs aux appareils amovibles.

6. Sélectionnez un élément dans la liste, tel que **Toutes les classes de stockage amovibles : Refuser tout accès**, pour ouvrir son volet de menu volant. Le menu volant de chaque paramètre explique ce qui se passe quand il est activé, désactivé ou non configuré. Sélectionnez un paramètre, puis choisissez **OK**. 

7. Répétez l’étape 6 pour chaque paramètre que vous souhaitez configurer. Sélectionnez **Suivant**.

8. Sous l’onglet **Balises d’étendue** , si votre organisation utilise des balises d’étendue, **choisissez + Sélectionner des balises d’étendue**, puis sélectionnez les balises que vous souhaitez utiliser. Ensuite, choisissez **Suivant**. 
   
   Pour en savoir plus sur les balises d’étendue, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour le service informatique distribué](/mem/intune/fundamentals/scope-tags).

9. Sous l’onglet **Affectations** , sélectionnez **Ajouter tous les utilisateurs** et **+ Ajouter tous les appareils**, puis choisissez **Suivant**. (Vous pouvez également spécifier des groupes spécifiques d’utilisateurs ou d’appareils.)

10. Sous l’onglet **Vérifier + créer** , passez en revue les paramètres de votre stratégie, puis choisissez **Créer**. La stratégie sera appliquée à tous les points de terminaison qui ont été intégrés à Defender pour point de terminaison sous peu.

> [!TIP]
> Pour plus d’informations, consultez [Comment contrôler des périphériques USB et d’autres supports amovibles à l’aide de Microsoft Defender pour point de terminaison](control-usb-devices-using-intune.md).

### <a name="network-protection"></a>Protection réseau

Grâce à la protection réseau, vous pouvez protéger votre organisation contre les domaines dangereux susceptibles d’héberger des escroqueries, des exploits et d’autres contenus malveillants sur Internet. Nous vous recommandons d’utiliser Microsoft Endpoint Manager pour activer la protection réseau.

:::image type="content" source="../../media/mde-p1/mem-endpointprotectionprofile.png" alt-text="Profil Endpoint Protection dans le portail Microsoft Endpoint Manager" lightbox="../../media/mde-p1/mem-endpointprotectionprofile.png":::

1. Accédez au Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous. 

2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.

3. Pour **La plateforme**, sélectionnez **Windows 10 et versions ultérieures**, puis, pour **type de profil**, sélectionnez **Modèles**. 

   Sous **Nom du modèle**, sélectionnez **Endpoint Protection**, puis **choisissez Créer**. 

4. Sous l’onglet **De base** , nommez la stratégie et ajoutez une description. Sélectionnez **Suivant**. 

5. Sous l’onglet **Paramètres de configuration** , développez **Microsoft Defender Exploit Guard**, puis développez **le filtrage réseau**.

   Définissez **la protection réseau** sur **Activer**. (Vous pouvez également choisir **Audit** pour voir comment la protection réseau fonctionnera dans votre environnement dans un premier temps.)

   Sélectionnez **Suivant**.

6. Sous l’onglet **Affectations** , sélectionnez **Ajouter tous les utilisateurs** et **+ Ajouter tous les appareils**, puis choisissez **Suivant**. (Vous pouvez également spécifier des groupes spécifiques d’utilisateurs ou d’appareils.)

7. Sous l’onglet **Règles d’applicabilité** , configurez une règle. Le profil que vous configurez est appliqué uniquement aux appareils qui répondent aux critères combinés que vous spécifiez. 

   Par exemple, vous pouvez choisir d’affecter la stratégie aux points de terminaison qui exécutent une édition de système d’exploitation spécifique uniquement.

   Sélectionnez **Suivant**. 

8. Sous l’onglet **Vérifier + créer** , passez en revue les paramètres de votre stratégie, puis choisissez **Créer**. La stratégie sera appliquée à tous les points de terminaison qui ont été intégrés à Defender pour point de terminaison sous peu.

> [!TIP]
> Vous pouvez utiliser d’autres méthodes, telles que Windows PowerShell ou stratégie de groupe, pour activer la protection réseau. Pour plus d’informations, consultez [Activer la protection réseau](enable-network-protection.md).

### <a name="web-protection"></a>Protection Web

Avec la protection web, vous pouvez protéger les appareils de votre organisation contre les menaces web et le contenu indésirable. Votre protection web inclut la [protection contre les menaces web](#configure-web-threat-protection) et [le filtrage du contenu web](#configure-web-content-filtering). Configurez les deux ensembles de fonctionnalités. Nous vous recommandons d’utiliser Microsoft Endpoint Manager pour configurer vos paramètres de protection web.

#### <a name="configure-web-threat-protection"></a>Configurer la protection contre les menaces web

1. Accédez au Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous.
 
2. Choisissez **La réduction de la surface d’attaque** de **sécurité** >  des points de terminaison, puis **choisissez + Créer une stratégie**.

3. Sélectionnez une plateforme, telle que **Windows 10 et versions ultérieures**, sélectionnez le profil de **protection web**, puis choisissez **Créer**. 

4. Sous l’onglet **Informations de base** , spécifiez un nom et une description, puis choisissez **Suivant**.

5. Sous l’onglet **Paramètres de configuration** , développez **Protection Web**, spécifiez les paramètres dans le tableau suivant, puis choisissez **Suivant**. <br/><br/>

   | Setting | Recommandation |
   |:---|:---|
   | **Activer la protection réseau** | Défini sur **Activé**. Empêche les utilisateurs de visiter des sites ou domaines malveillants. <br/><br/>Vous pouvez également définir la protection réseau en **mode Audit** pour voir comment elle fonctionnera dans votre environnement. En mode audit, la protection réseau n’empêche pas les utilisateurs de visiter des sites ou des domaines, mais elle effectue le suivi des détections en tant qu’événements. |
   | **Exiger SmartScreen pour Version antérieure de Microsoft Edge** | Défini sur **Oui**. Permet de protéger les utilisateurs contre les tentatives d’hameçonnage et les logiciels malveillants. |
   | **Bloquer l’accès à un site malveillant** | Défini sur **Oui**. Empêche les utilisateurs de contourner les avertissements concernant les sites potentiellement malveillants. |
   | **Bloquer le téléchargement de fichiers non vérifiés** | Défini sur **Oui**. Empêche les utilisateurs de contourner les avertissements et de télécharger des fichiers non vérifiés. |

6. Sous l’onglet **Balises d’étendue** , si votre organisation utilise des balises d’étendue, **choisissez + Sélectionner des balises d’étendue**, puis sélectionnez les balises que vous souhaitez utiliser. Ensuite, choisissez **Suivant**. 
   
   Pour en savoir plus sur les balises d’étendue, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour le service informatique distribué](/mem/intune/fundamentals/scope-tags).

7. Sous l’onglet **Affectations** , spécifiez les utilisateurs et les appareils pour recevoir la stratégie de protection web, puis choisissez **Suivant**.

8. Sous l’onglet **Vérifier + créer** , passez en revue vos paramètres de stratégie, puis choisissez **Créer**.

> [!TIP]
> Pour en savoir plus sur la protection contre les menaces web, consultez [Protéger votre organisation contre les menaces web](web-threat-protection.md).

#### <a name="configure-web-content-filtering"></a>Configurer le filtrage de contenu web

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)), puis connectez-vous.

2. Choisissez **Les points de terminaison des** > **paramètres**.

3. Sous **Règles**, choisissez **filtrage de contenu web**, puis **choisissez + Ajouter une stratégie**.

4. Dans le menu volant **Ajouter une stratégie** , sous l’onglet **Général** , spécifiez un nom pour votre stratégie, puis choisissez **Suivant**.

5. Dans les **catégories bloquées**, sélectionnez une ou plusieurs catégories à bloquer, puis choisissez **Suivant**.

6. Sous l’onglet **Étendue** , sélectionnez les groupes d’appareils que vous souhaitez recevoir cette stratégie, puis choisissez **Suivant**.

7. Sous l’onglet **Résumé** , passez en revue les paramètres de votre stratégie, puis **sélectionnez Enregistrer**.

> [!TIP]
> Pour en savoir plus sur la configuration du filtrage de contenu web, consultez [filtrage de contenu web](web-content-filtering.md).

### <a name="network-firewall"></a>Pare-feu réseau

Le pare-feu réseau permet de réduire le risque de menaces de sécurité réseau. Votre équipe de sécurité peut définir des règles qui déterminent le trafic autorisé à circuler vers ou depuis les appareils de votre organisation. Nous vous recommandons d’utiliser Microsoft Endpoint Manager pour configurer votre pare-feu réseau. 

:::image type="content" source="../../media/mde-p1/mem-firewallpolicy.png" alt-text="Stratégie de pare-feu dans le portail Microsoft Endpoint Manager" lightbox="../../media/mde-p1/mem-firewallpolicy.png":::

Pour configurer les paramètres de pare-feu de base, procédez comme suit :

1. Accédez au Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous.

2. Choisissez **Pare-feu** **de sécurité** >  de point de terminaison, puis **choisissez + Créer une stratégie**.

3. Sélectionnez une plateforme, par exemple **Windows 10 et versions ultérieures**, sélectionnez le profil **Pare-feu Microsoft Defender**, puis choisissez **Créer**. 

4. Sous l’onglet **Informations de base** , spécifiez un nom et une description, puis choisissez **Suivant**.

5. Développez **Pare-feu Microsoft Defender**, puis faites défiler vers le bas de la liste.

6. Définissez chacun des paramètres suivants sur **Oui** :

   - **Activer Pare-feu Microsoft Defender pour les réseaux de domaine** 
   - **Activer Pare-feu Microsoft Defender pour les réseaux privés**
   - **Activer Pare-feu Microsoft Defender pour les réseaux publics**
   
   Passez en revue la liste des paramètres sous chacun des réseaux de domaine, des réseaux privés et des réseaux publics. Vous pouvez les laisser définis sur **Non configurés** ou les modifier en fonction des besoins de votre organisation.

   Sélectionnez **Suivant**.

7. Sous l’onglet **Balises d’étendue** , si votre organisation utilise des balises d’étendue, **choisissez + Sélectionner des balises d’étendue**, puis sélectionnez les balises que vous souhaitez utiliser. Ensuite, choisissez **Suivant**. 
   
   Pour en savoir plus sur les balises d’étendue, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour le service informatique distribué](/mem/intune/fundamentals/scope-tags).

8. Sous l’onglet **Affectations** , sélectionnez **Ajouter tous les utilisateurs** et **+ Ajouter tous les appareils**, puis choisissez **Suivant**. (Vous pouvez également spécifier des groupes spécifiques d’utilisateurs ou d’appareils.)

9. Sous l’onglet **Vérifier + créer** , passez en revue vos paramètres de stratégie, puis choisissez **Créer**.

> [!TIP]
> Les paramètres de pare-feu sont détaillés et peuvent sembler complexes. Reportez-vous aux [meilleures pratiques pour configurer Pare-feu Windows Defender](/windows/security/threat-protection/windows-firewall/best-practices-configuring).

### <a name="application-control"></a>Contrôle d’application

Windows Defender Contrôle d’application (WDAC) permet de protéger vos points de terminaison Windows en autorisant uniquement l’exécution d’applications et de processus approuvés. La plupart des organisations ont utilisé un déploiement par phases de WDAC. Autrement dit, la plupart des organisations ne déploient pas WDAC sur tous les points de terminaison Windows au début. En fait, selon que les points de terminaison Windows de votre organisation sont entièrement gérés, gérés à la légère ou que les points de terminaison « Apportez votre propre appareil », vous pouvez déployer WDAC sur tous ou certains points de terminaison.

Pour vous aider à planifier votre déploiement WDAC, consultez les ressources suivantes :

- [Contrôle d’application pour Windows](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)

- [Windows Defender décisions de conception de stratégie de contrôle d’application](/windows/security/threat-protection/windows-defender-application-control/understand-windows-defender-application-control-policy-design-decisions)

- [Windows Defender déploiement d’Application Control dans différents scénarios : types d’appareils](/windows/security/threat-protection/windows-defender-application-control/types-of-devices)

## <a name="next-steps"></a>Prochaines étapes

Maintenant que vous avez suivi le processus d’installation et de configuration, l’étape suivante consiste à commencer à utiliser Defender pour point de terminaison. 

- [Prise en main de Defender pour point de terminaison Plan 1](mde-plan1-getting-started.md)
