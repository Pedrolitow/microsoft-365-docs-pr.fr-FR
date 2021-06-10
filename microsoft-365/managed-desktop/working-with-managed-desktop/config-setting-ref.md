---
title: Référence des paramètres configurables pour Bureau géré Microsoft
description: Définition de catégories pour les paramètres configurables dans Bureau géré Microsoft
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 1245268b6128aa022a972fd0282009573558ec47
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50917703"
---
# <a name="configurable-settings-reference---microsoft-managed-desktop"></a>Référence des paramètres configurables : Bureau géré Microsoft

Cette rubrique répertorie les catégories de paramètres que les clients peuvent configurer avec Bureau géré Microsoft. Chaque catégorie de paramètres inclut des informations sur les conditions requises, les meilleures pratiques et la façon de personnaliser la catégorie de paramètres. 

## <a name="desktop-background-picture"></a>Image d’arrière-plan du bureau
Vous pouvez personnaliser l’image d’arrière-plan du bureau Bureau géré Microsoft appareils de votre organisation. Vous pouvez l’utiliser pour appliquer une marque d’entreprise ou du matériel marketing. 

### <a name="requirements"></a>Conditions requises

Ces conditions doivent être remplies pour une image d’arrière-plan de bureau :
- Format de fichier image : .jpg, jpeg ou .png
- Emplacement du fichier : hôte sur un emplacement http (https) sécurisé approuvé. 
- Non autorisé : les emplacements Http et de partage de fichiers (unc) ne sont pas pris en charge. 

### <a name="customize-and-deploy-desktop-background-picture"></a>Personnaliser et déployer une image d’arrière-plan de bureau

**Pour ajouter une image d’arrière-plan de bureau personnalisée**
1. Connectez-vous [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) et accédez au menu **Appareils**
2. Recherchez la section Bureau géré Microsoft, sélectionnez **Paramètres**.
3. In **Paramètres** workspace, select **Desktop background picture**. 
4. Entrez l’emplacement de l’image que vous souhaitez utiliser. 
5. Sélectionnez **Le déploiement par** étapes pour enregistrer vos modifications et les déployer dans le groupe test. 

## <a name="browser-start-pages"></a>Pages de démarrage du navigateur
Les pages de démarrage du navigateur s’ouvrent dans des onglets individuels lorsque vos utilisateurs Microsoft Edge. Si vous souhaitez faciliter l’ouverture par vos utilisateurs d’un ensemble de sites qu’ils utilisent fréquemment, ajoutez une page de démarrage de navigateur pour chaque site. 

### <a name="requirements"></a>Conditions requises

Vous devez fournir le nom de domaine complet (FQDN) pour les sites intranet ou Internet pour les pages de démarrage de votre navigateur. Si des sites internes sont configurés, faites savoir aux utilisateurs que l’accès à ces sites est autorisé uniquement lorsqu’ils sont connectés au réseau interne lorsqu’ils sont au bureau ou lorsqu’ils sont connectés avec une connexion VPN. 

### <a name="customize-and-deploy-browser-start-pages"></a>Personnaliser et déployer les pages de démarrage du navigateur

**Pour ajouter une page de démarrage de navigateur**
1. Connectez-vous [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) et accédez au menu **Appareils**
2. Recherchez la section Bureau géré Microsoft, sélectionnez **Paramètres**.
3. Dans **Paramètres** de travail, sélectionnez **les pages de démarrage du navigateur.** 
4. Sélectionnez **Ajouter une page de démarrage.**
5. Dans **la page d’accueil Ajouter** un navigateur, entrez l’URL du site que vous souhaitez utiliser, puis sélectionnez Ajouter une page de **démarrage.** 
6. Répétez les étapes 1 à 5 pour les pages de démarrage de navigateur supplémentaires. 
7. Sélectionnez **Le déploiement par** étapes pour enregistrer vos modifications et les déployer dans le groupe test.

## <a name="enterprise-mode-site-list-location"></a>Enterprise de liste des sites en mode d’Enterprise

Si vous avez des sites web et des applications spécifiques qui rencontrent des problèmes de compatibilité avec Microsoft Edge, vous pouvez utiliser la liste des sites en mode Enterprise afin que les sites web s’ouvrent automatiquement à l’aide d’Internet Explorer 11. En outre, si vous savez que vos sites intranet ne fonctionneront pas correctement avec Microsoft Edge, vous pouvez configurer tous les sites intranet pour qu’ils s’ouvrent automatiquement à l’aide d’Internet Explorer 11. L’utilisation du mode Enterprise signifie que vous pouvez continuer à utiliser Microsoft Edge comme navigateur par défaut, tout en vous assurant que vos applications continuent de fonctionner sur Internet Explorer 11. Pour plus d’informations sur les listes des sites en mode entreprise, voir Enterprise Mode d’Enterprise listes des sites en [mode Entreprise.](/internet-explorer/ie11-deploy-guide/what-is-enterprise-mode) 

Vous pouvez spécifier un https:// ou l’emplacement d’un partage interne dans lequel vous avez hébergé votre liste des sites en mode entreprise. 

### <a name="requirements"></a>Conditions requises

Ces conditions doivent être remplies pour le fichier de liste des sites en mode Entreprise :
- Format de fichier : fichier XML qui répond aux exigences [de fichier](/internet-explorer/ie11-deploy-guide/what-is-enterprise-mode#site-list-xml-file)
- Emplacement du fichier : fichier hôte sur un emplacement https interne. 
- Non autorisé - L’hébergement sur un partage de fichiers interne, comme *//sharename,* n’est pas autorisé.

### <a name="best-practices"></a>Meilleures pratiques

Ces meilleures pratiques sont proposées pour aider les clients à prendre des décisions pour moderniser leur infrastructure informatique :
- **Choisissez un nombre limité** de sites : Bureau géré Microsoft utilise Microsoft Edge comme navigateur préféré pour améliorer la sécurité globale de votre organisation et la convivialité pour vos utilisateurs. La plupart des sites de cette liste sont pour les applications web héritées qui ont besoin d’une version antérieure d’un navigateur qui n’inclura pas autant de fonctionnalités de sécurité. 
- **Envisagez une autre solution** : envisagez un autre site ou une application web qui ne nécessite pas de navigateur plus ancien. Vous pouvez également mettre à jour le site afin qu’il puisse utiliser des navigateurs plus récents. Les navigateurs plus récents utilisent la dernière technologie et contribuent à améliorer la sécurité.

### <a name="customize-and-deploy-enterprise-site-mode-list-location"></a>Personnaliser et déployer un Enterprise de liste en mode site

**Pour ajouter un emplacement de liste en mode site d’entreprise**

1. Connectez-vous [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) et accédez au menu **Appareils**
2. Recherchez la section Bureau géré Microsoft, sélectionnez **Paramètres**.
3. Dans **Paramètres** espace de travail, sélectionnez **Enterprise’emplacement de la liste des sites en mode d’accès.** 
4. Entrez l’emplacement https de votre liste des sites. 
5. Sélectionnez **Le déploiement par** étapes pour enregistrer vos modifications et les déployer dans le groupe test.

## <a name="trusted-sites"></a>Sites approuvés

Les sites de confiance vous permettent de personnaliser les zones de sécurité, ou l’emplacement où un site peut être utilisé, pour différents sites. Les zones de sécurité sont les suivantes : 
- Zone 1 – Zone Intranet local
- Zone 2 : zone Sites de confiance
- Zone 3 – Zone Internet
- Zone 4 : zone Sites restreints

### <a name="requirements"></a>Conditions requises

Fournissez le nom de domaine complet (FQDN) pour les sites intranet ou Internet pour chaque site approuvé. 

### <a name="customize-and-deploy-trusted-sites"></a>Personnaliser et déployer des sites de confiance

**Pour ajouter un site approuvé**

1. Connectez-vous [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) et accédez au menu **Appareils**
2. Recherchez la section Bureau géré Microsoft, sélectionnez **Paramètres**.
3. Dans **Paramètres** de travail, sélectionnez **Sites** de confiance, puis **Ajoutez un site approuvé.** 
4. Sur **Ajouter un site approuvé,** entrez l’URL, choisissez une zone de sécurité, puis **sélectionnez Ajouter un site approuvé.** 
5. Répétez les étapes 1 à 4 pour chaque site approuvé que vous souhaitez ajouter. 
6. Sélectionnez **Le déploiement par** étapes pour enregistrer vos modifications et les déployer dans le groupe test.

**Pour supprimer un site approuvé**

1. Connectez-vous [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) et accédez au menu **Appareils**
2. Recherchez la section Bureau géré Microsoft, sélectionnez **Paramètres**.
3. Dans **Paramètres** de travail, sélectionnez **Sites de confiance.** 
4. Sélectionnez le site à supprimer, puis sélectionnez **Supprimer.** 
5. Répétez les étapes 1 à 4 pour chaque site approuvé à supprimer. 
6. Sélectionnez **Le déploiement par** étapes pour enregistrer vos modifications et les déployer dans le groupe test.

## <a name="proxy"></a>Proxy
Vous pouvez gérer les paramètres de proxy réseau pour votre organisation. Ajoutez votre serveur proxy et votre numéro de port, puis ajoutez vos exceptions de site proxy. Bureau géré Microsoft inclut un ensemble d’exceptions de proxy par défaut qui sont requises pour que le service fonctionne. La liste d’exclusions par défaut peut uniquement être modifiée par Bureau géré Microsoft service.  Pour plus d’informations, [voir Configuration réseau pour Bureau géré Microsoft](../get-ready/network.md). 

Les exceptions de site proxy que vous ajoutez au portail Bureau géré Microsoft sont ajoutées aux exceptions de proxy par défaut incluses dans Bureau géré Microsoft service. 

> [!NOTE]
> La mise à jour de la liste des exceptions de proxy par défaut est toujours prioritaire sur les déploiements des clients. Cela signifie que votre déploiement intermédiaire sera suspendu s’il existe un déploiement pour la liste d’exceptions de proxy par défaut.  

### <a name="requirements"></a>Conditions requises

Ces conditions doivent être remplies pour les exceptions de serveur proxy et de site proxy :
- Doit être une adresse de serveur et un numéro de port valides
- Les URL doivent être un site http valide 

### <a name="customize-and-deploy-proxies"></a>Personnaliser et déployer des proxies

**Pour ajouter une exception de site proxy individuel**

1. Connectez-vous [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) et accédez au menu **Appareils**
2. Recherchez la section Bureau géré Microsoft, sélectionnez **Paramètres**.
3. Dans **Paramètres** de travail, sélectionnez **Proxy**. 
4. Entrez le **numéro d’adresse** **et de port** de votre serveur proxy, puis sélectionnez Ajouter une exception de **proxy.** 
5. Entrez l’URL d’un site http valide, puis sélectionnez **Ajouter une exception de proxy.** 
6. Répétez les étapes 1 à 5 pour chaque site approuvé que vous souhaitez ajouter. 
7. Sélectionnez **Le déploiement par** étapes pour enregistrer vos modifications et les déployer dans le groupe test.

## <a name="additional-resources"></a>Ressources supplémentaires
- [Vue d’ensemble des paramètres configurables](config-setting-overview.md) 
- [Déployer des paramètres configurables](config-setting-deploy.md)