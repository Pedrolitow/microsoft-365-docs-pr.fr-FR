---
title: Référence des paramètres configurables pour le bureau géré Microsoft
description: Définition des catégories pour les paramètres configurables dans le bureau géré Microsoft
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 2c7c7d75fad58cab0cd6d19a16a97667ea3641a1
ms.sourcegitcommit: adaedd1418a3bd6e4875b77fd9e008b47e0b2a51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "48104487"
---
# <a name="configurable-settings-reference---microsoft-managed-desktop"></a>Référence des paramètres configurables-bureau géré Microsoft

Cette rubrique répertorie les catégories de paramètres que les clients peuvent configurer avec le bureau géré Microsoft. Chaque catégorie de paramètres comprend des informations sur les exigences, les meilleures pratiques et la personnalisation de la catégorie de paramètres. 

## <a name="desktop-background-picture"></a>Image d’arrière-plan du Bureau
Vous pouvez personnaliser l’image d’arrière-plan du Bureau pour les appareils de bureau gérés Microsoft dans votre organisation. Vous pouvez l’utiliser pour appliquer une marque de société ou une documentation marketing. 

### <a name="requirements"></a>Configuration requise

Ces conditions doivent être remplies pour une image d’arrière-plan de bureau :
- Format de fichier image-. jpg, JPEG ou. png
- Emplacement des fichiers : héberger sur un emplacement HTTPS sécurisé (https) approuvé. 
- Non autorisé-les emplacements http et de partage de fichiers (UNC) ne sont pas pris en charge. 

### <a name="customize-and-deploy-desktop-background-picture"></a>Personnaliser et déployer une image d’arrière-plan du Bureau

**Pour ajouter une image d’arrière-plan personnalisée du Bureau**
1. Connectez-vous au [Gestionnaire de point de terminaison Microsoft](https://endpoint.microsoft.com/) et accédez au menu **appareils** .
2. Recherchez la section bureau géré Microsoft, puis sélectionnez **paramètres**.
3. Dans l’espace de travail **paramètres** , sélectionnez **image d’arrière-plan du Bureau**. 
4. Entrez l’emplacement de l’image que vous souhaitez utiliser. 
5. Sélectionnez **stage Deployment** pour enregistrer vos modifications et les déployer dans le groupe de test. 

## <a name="browser-start-pages"></a>Pages de démarrage du navigateur
Les pages de démarrage de navigateur s’ouvrent dans des onglets individuels lorsque les utilisateurs démarrent Microsoft Edge. Si vous souhaitez que vos utilisateurs puissent facilement ouvrir un ensemble de sites qu’ils utilisent fréquemment, ajoutez une page de démarrage de navigateur pour chaque site. 

### <a name="requirements"></a>Configuration requise

Vous devez indiquer le nom de domaine complet (FQDN) pour les sites intranet ou Internet pour les pages de démarrage de votre navigateur. Si des sites internes sont configurés, indiquez aux utilisateurs que l’accès à ces sites est uniquement autorisé lorsqu’ils sont connectés au réseau interne au bureau ou lorsqu’ils sont connectés à l’aide d’une connexion VPN. 

### <a name="customize-and-deploy-browser-start-pages"></a>Personnaliser et déployer des pages de démarrage de navigateur

**Pour ajouter une page de démarrage de navigateur**
1. Connectez-vous au [Gestionnaire de point de terminaison Microsoft](https://endpoint.microsoft.com/) et accédez au menu **appareils** .
2. Recherchez la section bureau géré Microsoft, puis sélectionnez **paramètres**.
3. Dans l’espace de travail **paramètres** , sélectionnez **pages de démarrage du navigateur**. 
4. Sélectionnez **Ajouter une page de démarrage**.
5. Dans **Ajouter la page de démarrage du navigateur**, entrez l’URL du site que vous souhaitez utiliser, puis sélectionnez **Ajouter une page de démarrage**. 
6. Répétez les étapes 1-5 pour les pages de démarrage de navigateur supplémentaires. 
7. Sélectionnez **stage Deployment** pour enregistrer vos modifications et les déployer dans le groupe de test.

## <a name="enterprise-mode-site-list-location"></a>Emplacement de la liste de sites en mode entreprise

Si vous avez des sites Web et des applications spécifiques dont vous connaissez qu’il existe des problèmes de compatibilité avec Microsoft Edge, vous pouvez utiliser la liste des sites en mode entreprise pour que les sites Web s’ouvrent automatiquement à l’aide d’Internet Explorer 11. En outre, si vous savez que vos sites intranet ne fonctionnent pas correctement avec Microsoft Edge, vous pouvez configurer tous les sites intranet pour qu’ils s’ouvrent automatiquement à l’aide d’Internet Explorer 11. L’utilisation du mode entreprise signifie que vous pouvez continuer à utiliser Microsoft Edge comme navigateur par défaut, tout en vous assurant que vos applications continuent de fonctionner sur Internet Explorer 11. Pour plus d’informations sur les listes de sites en mode entreprise, consultez la rubrique [Enterprise mode and Enterprise mode site lists](https://docs.microsoft.com/internet-explorer/ie11-deploy-guide/what-is-enterprise-mode). 

Vous pouvez spécifier un emplacement https://ou l’emplacement d’un partage interne où vous avez hébergé votre liste de sites en mode entreprise. 

### <a name="requirements"></a>Configuration requise

Ces exigences doivent être satisfaites pour le fichier de liste de sites en mode entreprise :
- Format de fichier : fichier XML qui répond aux [exigences de fichier](https://docs.microsoft.com/internet-explorer/ie11-deploy-guide/what-is-enterprise-mode#site-list-xml-file)
- Emplacement des fichiers : fichier hôte sur un emplacement https interne. 
- Non autorisé-l’hébergement sur un partage de fichiers interne, comme *//ShareName*, n’est pas autorisé

### <a name="best-practices"></a>Meilleures pratiques

Ces meilleures pratiques sont proposées pour aider les clients à prendre des décisions pour moderniser leur infrastructure informatique :
- **Choisir un nombre limité de sites** : Microsoft Managed Desktop utilise Microsoft Edge comme navigateur favori pour améliorer la sécurité globale pour votre organisation et la convivialité de vos utilisateurs. La plupart des sites de cette liste sont destinés aux applications Web héritées qui ont besoin d’une version plus ancienne d’un navigateur qui n’inclut pas autant de fonctionnalités de sécurité. 
- **Songez** à utiliser un autre site ou une application Web qui ne nécessite pas un navigateur plus ancien. Vous pouvez également mettre à jour le site afin qu’il puisse utiliser des navigateurs plus récents. Les navigateurs plus récents utilisent la technologie la plus récente et contribuent à l’amélioration de la sécurité.

### <a name="customize-and-deploy-enterprise-site-mode-list-location"></a>Personnaliser et déployer l’emplacement de liste en mode site d’entreprise

**Pour ajouter un emplacement de liste en mode site d’entreprise**

1. Connectez-vous au [Gestionnaire de point de terminaison Microsoft](https://endpoint.microsoft.com/) et accédez au menu **appareils** .
2. Recherchez la section bureau géré Microsoft, puis sélectionnez **paramètres**.
3. Dans l’espace de travail **paramètres** , sélectionnez emplacement de la **liste de sites en mode entreprise**. 
4. Entrez l’emplacement https de votre liste de sites. 
5. Sélectionnez **stage Deployment** pour enregistrer vos modifications et les déployer dans le groupe de test.

## <a name="trusted-sites"></a>Sites approuvés

Les sites de confiance vous permettent de personnaliser les zones de sécurité ou d’utiliser un site, pour différents sites. Les zones de sécurité sont les suivantes : 
- Zone 1 – zone Intranet local
- Zone 2 : zone sites de confiance
- Zone 3 – zone Internet
- Zone 4 – zone sites sensibles

### <a name="requirements"></a>Configuration requise

Fournissez le nom de domaine complet (FQDN) pour les sites intranet ou Internet de chaque site approuvé. 

### <a name="customize-and-deploy-trusted-sites"></a>Personnaliser et déployer des sites de confiance

**Pour ajouter un site de confiance**

1. Connectez-vous au [Gestionnaire de point de terminaison Microsoft](https://endpoint.microsoft.com/) et accédez au menu **appareils** .
2. Recherchez la section bureau géré Microsoft, puis sélectionnez **paramètres**.
3. Dans l’espace de travail **paramètres** , sélectionnez **sites de confiance**, puis **Ajouter un site approuvé**. 
4. Sur **Ajouter un site approuvé**, entrez l’URL, choisissez une zone de sécurité, puis sélectionnez **Ajouter un site approuvé**. 
5. Répétez les étapes 1-4 pour chaque site approuvé que vous souhaitez ajouter. 
6. Sélectionnez **stage Deployment** pour enregistrer vos modifications et les déployer dans le groupe de test.

**Pour supprimer un site approuvé**

1. Connectez-vous au [Gestionnaire de point de terminaison Microsoft](https://endpoint.microsoft.com/) et accédez au menu **appareils** .
2. Recherchez la section bureau géré Microsoft, puis sélectionnez **paramètres**.
3. Dans l’espace de travail **paramètres** , sélectionnez **sites de confiance**. 
4. Sélectionnez le site que vous souhaitez supprimer, puis sélectionnez **supprimer**. 
5. Répétez les étapes 1-4 pour chaque site approuvé à supprimer. 
6. Sélectionnez **stage Deployment** pour enregistrer vos modifications et les déployer dans le groupe de test.

## <a name="proxy"></a>Établir
Vous pouvez gérer les paramètres de proxy réseau pour votre organisation. Ajoutez votre serveur proxy et votre numéro de port, puis ajoutez les exceptions de votre site proxy. Microsoft Managed Desktop inclut un ensemble d’exceptions de proxy par défaut qui sont requises pour le fonctionnement du service. La liste d’exclusion par défaut ne peut être modifiée que par le service bureau géré Microsoft.  Pour plus d’informations, consultez la rubrique [Configuration réseau pour Microsoft Managed Desktop](../get-ready/network.md). 

Les exceptions de site proxy que vous ajoutez dans le portail de bureau géré Microsoft sont ajoutées aux exceptions de proxy par défaut fournies avec le service bureau géré Microsoft. 

> [!NOTE]
> La mise à jour de la liste des exceptions de proxy par défaut est toujours prioritaire sur les déploiements des clients. Cela signifie que votre déploiement intermédiaire sera suspendu s’il existe un déploiement pour la liste des exceptions de proxy par défaut.  

### <a name="requirements"></a>Configuration requise

Ces exigences doivent être satisfaites pour les exceptions de serveur proxy et de site proxy :
- Doit être une adresse de serveur et un numéro de port valides
- Les URL doivent être un site http valide 

### <a name="customize-and-deploy-proxies"></a>Personnaliser et déployer des proxys

**Pour ajouter une exception de site proxy individuelle**

1. Connectez-vous au [Gestionnaire de point de terminaison Microsoft](https://endpoint.microsoft.com/) et accédez au menu **appareils** .
2. Recherchez la section bureau géré Microsoft, puis sélectionnez **paramètres**.
3. Dans l’espace de travail **paramètres** , sélectionnez **proxy**. 
4. Entrez l' **adresse** et le **numéro de port** de votre serveur proxy, puis sélectionnez Ajouter une exception de **proxy**. 
5. Entrez l’URL d’un site http valide, puis sélectionnez **Ajouter une exception de proxy**. 
6. Répétez les étapes 1-5 pour chaque site approuvé que vous souhaitez ajouter. 
7. Sélectionnez **stage Deployment** pour enregistrer vos modifications et les déployer dans le groupe de test.

## <a name="additional-resources"></a>Ressources supplémentaires
- [Vue d’ensemble des paramètres configurables](config-setting-overview.md) 
- [Déployer des paramètres configurables](config-setting-deploy.md)
