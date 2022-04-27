---
title: Requêtes réseau dans Office pour Mac
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/9/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: Cet article décrit les points de terminaison et LES URL que Office pour Mac applications tentent d’atteindre, ainsi que les services fournis.
ms.openlocfilehash: 477225cf99ead3f5609c8082644293d4ac006603
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091124"
---
# <a name="network-requests-in-office-for-mac"></a>Requêtes réseau dans Office pour Mac

Office pour Mac applications offrent une expérience d’application native sur la plateforme macOS. Chaque application est conçue pour fonctionner dans divers scénarios, y compris les états lorsqu’aucun accès réseau n’est disponible. Lorsqu’une machine est connectée à un réseau, les applications se connectent automatiquement à une série de services web pour fournir des fonctionnalités améliorées. Les informations suivantes décrivent les points de terminaison et LES URL que les applications tentent d’atteindre, ainsi que les services fournis. Ces informations sont utiles lors de la résolution des problèmes de configuration réseau et de la définition de stratégies pour les serveurs proxy réseau. Les détails de cet article sont destinés à compléter [l’article Office 365 url et plages d’adresses](urls-and-ip-address-ranges.md), qui inclut des points de terminaison pour les ordinateurs exécutant Microsoft Windows. Sauf indication contraire, les informations contenues dans cet article s’appliquent également à Office 2019 pour Mac et Office 2016 pour Mac, qui sont disponibles sous forme d’achat unique auprès d’un magasin de détail ou par le biais d’un contrat de licence en volume. 

  
La plupart de cet article est constitué de tableaux détaillant les URL réseau, le type et la description du service ou de la fonctionnalité fournis par ce point de terminaison. Chacune des applications Office peut différer dans son utilisation du service et du point de terminaison. Les applications suivantes sont définies dans les tableaux ci-dessous :
  
- W : Word
- P : PowerPoint
- X : Excel
- O : Outlook
- N : OneNote
   
Le type d’URL est défini comme suit :
  
- ST : statique : l’URL est codée en dur dans l’application cliente.
    
- SS : Semi-Static : l’URL est encodée dans le cadre d’une page web ou d’un redirecteur.
    
- CS : Service de configuration : l’URL est retournée dans le cadre du service de configuration Office.

    
## <a name="office-for-mac-default-configuration"></a>Office pour Mac configuration par défaut

 **Installation et mises à jour**
  
Les points de terminaison réseau suivants sont utilisés pour télécharger le programme d’installation Office pour Mac à partir de Microsoft réseau de distribution de contenu (CDN).
  
|**URL**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |Microsoft 365 service de liaison de transfert du portail d’installation vers les derniers packages d’installation.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |Emplacement des packages d’installation sur le réseau de distribution de contenu.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |Emplacement des packages d’installation sur le réseau de distribution de contenu.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |Point de terminaison du contrôle de gestion pour Microsoft AutoUpdate  <br/> |
   
 **Premier lancement d’application**
  
Les points de terminaison réseau suivants sont contactés lors du premier lancement d’un application Office. Ces points de terminaison offrent des fonctionnalités de Office améliorées pour les utilisateurs, et les URL sont contactées quel que soit le type de licence (y compris les installations de licence en volume).
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |Configuration « Flighting » : permet l’éclairage et l’expérimentation des fonctionnalités.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |Test de configuration réseau « flighting »  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |Test de configuration réseau « flighting »  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office Configuration Service - Liste principale des points de terminaison de service.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office téléchargement des données de télémétrie des règles : informe le client des données et des événements à charger dans le service de télémétrie.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |OneNote service de télémétrie  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office télémétrie Télécharger Rapports : les événements « Heartbeart » et d’erreur qui se produisent sur le client sont chargés vers le service de télémétrie.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office Service de modèle : fournit aux utilisateurs des modèles de document en ligne.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Office téléchargements de modèles - Stockage d’images de modèle PNG.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Configuration du Magasin pour les applications Office.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Office catalogue Document Integration Services (liste des services et points de terminaison) et découverte du domaine d’accueil.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Ressources pour la découverte du domaine d’accueil v2 (15.40 et versions ultérieures)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft AutoUpdate Manifests : vérifie s’il existe des mises à jour disponibles  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Bibliothèque JavaScript Microsoft Ajax  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Application Wikipédia pour Office configuration et ressources.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing application Map pour la configuration et les ressources Office.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Les utilisateurs Graph application pour la configuration et les ressources Office.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ST  <br/> |Nouveautés pour OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ST  <br/> |Nouveau contenu pour OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |Nouveautés des images pour OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |Service de support dans l’application.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |Service de détection de compte de messagerie.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook découverte automatique  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook point de terminaison pour Microsoft 365 service.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |Icônes pour Outlook compléments.  <br/> |
   
> [!NOTE]
> Le service de configuration Office agit comme un service de découverte automatique pour tous les clients Microsoft Office, et pas seulement pour Mac. Les points de terminaison retournés dans la réponse sont semi-statiques, dans la raison que le changement est très peu fréquent, mais toujours possible. 
  
 **Connexion**
  
Les points de terminaison réseau suivants sont contactés lors de la connexion au stockage cloud. Selon le type de votre compte, différents services peuvent être contactés. Par exemple :
  
- **MSA : Compte Microsoft** - généralement utilisé pour les scénarios de consommation et de vente au détail 
    
- **OrgID : Compte d’organisation** - généralement utilisé pour les scénarios commerciaux 
    
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |service d’autorisation Windows  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft 365 Login Service (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft Account Login Service (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Microsoft Account Login Service Helper (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Microsoft 365 Login Branding (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Document et emplacements Stockage Localisateur  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Service de document MRU (Most Recently Used)  <br/> |
   
> [!NOTE]
> Pour les licences basées sur les abonnements et les licences de vente au détail, la connexion active le produit et permet l’accès aux ressources cloud telles que OneDrive. Pour les installations de licence en volume, les utilisateurs sont toujours invités à se connecter (par défaut), mais cela n’est requis que pour l’accès aux ressources cloud, car le produit est déjà activé. 
  
 **Activation du produit**
  
Les points de terminaison réseau suivants s’appliquent aux activations d’abonnement Microsoft 365 et de licence de vente au détail. Plus précisément, cela ne s’applique PAS aux installations de licence en volume.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Service de gestion des licences Office  <br/> |
   
 **Nouveautés du contenu**
  
Les points de terminaison réseau suivants s’appliquent uniquement à Microsoft 365 Abonnement.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |Nouveautés de la page JSON.  <br/> |
   
 **Recherche**
  
Les points de terminaison réseau suivants s’appliquent uniquement à Microsoft 365 Abonnement.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Service web de recherche  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Contenu statique du chercheur  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |Fournisseur de contenu de recherche  <br/> |
   
 **Recherche intelligente**
  
Les points de terminaison réseau suivants s’appliquent à la fois aux activations d’abonnement Microsoft 365 et de licence de vente au détail/en volume.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |service web Informations  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |Bibliothèque JQuery  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |Prise en charge de la bibliothèque JavaScript  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |fournisseur de contenu Informations  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |fournisseur de contenu Informations  <br/> |
   
 **Concepteur PowerPoint**
  
Les points de terminaison réseau suivants s’appliquent uniquement à Microsoft 365 Abonnement.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |service web PowerPoint Designer  <br/> |
   
 **Aide au démarrage de PowerPoint**
  
Les points de terminaison réseau suivants s’appliquent uniquement à Microsoft 365 Abonnement.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint service web QuickStarter  <br/> |
   
 **Envoyer un sourire/un froncement de dents**
  
Les points de terminaison réseau suivants s’appliquent à la fois aux activations d’abonnement Microsoft 365 et de licence de vente au détail/en volume.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |Envoyer un service Smile  <br/> |
   
 **Contacter le support**
  
Les points de terminaison réseau suivants s’appliquent à la fois aux activations d’abonnement Microsoft 365 et de licence de vente au détail/en volume.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |Contacter le service de support technique  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |Service de support dans l’application  <br/> |
   
 **Enregistrer au format PDF**
  
Les points de terminaison réseau suivants s’appliquent à la fois aux activations d’abonnement Microsoft 365 et de licence de vente au détail/en volume.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Service de conversion de documents Word (PDF)  <br/> |
   
 **Office Apps (également appelés compléments)**
  
Les points de terminaison réseau suivants s’appliquent aux activations d’abonnement Microsoft 365 et de licence de vente au détail/en volume lorsque Office compléments d’application sont approuvés.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |configuration du magasin application Office  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Ressources de l’application Wikipédia  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing mappage des ressources d’application  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |Personnes Graph ressources d’application  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |service de redirection Office  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |bibliothèques JavaScript Office  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |Télémétrie et Reporting Service pour les applications Office  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SS  <br/> |Bibliothèque JavaScript Microsoft Ajax  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Bibliothèque JavaScript Microsoft Ajax  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |bibliothèques JavaScript Office  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Ressources de support  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Ressources de support  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |Ressources de support  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |Bibliothèque JavaScript  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |Rapports d'erreurs  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |Ressources de police  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |Service de télémétrie  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Rapports de télémétrie  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |bibliothèque de ressources Microsoft Store  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SS  <br/> |Ressources de la page Wikipédia  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SS  <br/> |Ressources multimédias Wikipédia  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SS  <br/> |Trame de bac à sable Wikipédia  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |Modèles de carte  <br/> |
   
 **Liens fiables**
  
Le point de terminaison réseau suivant s’applique à toutes les applications Office pour Microsoft 365 Abonnement uniquement.
  
|**URL**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Service Microsoft Coffre Link  <br/> |
   
 **Rapports sur les incidents**
  
Le point de terminaison réseau suivant s’applique à toutes les applications Office pour les activations d’abonnement Microsoft 365 et de licence de vente au détail/volume. Lorsqu’un processus se bloque de manière inattendue, un rapport est généré et envoyé au service Watson.
  
|**URL**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |Service de création de rapports d’erreurs Microsoft  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |Office Collaborative Informations Service  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>Options de réduction des demandes réseau et du trafic

La configuration par défaut de Office pour Mac offre la meilleure expérience utilisateur, à la fois en termes de fonctionnalités et de mise à jour de l’ordinateur. Dans certains scénarios, vous souhaiterez peut-être empêcher les applications de contacter des points de terminaison réseau. Cette section décrit les options pour ce faire.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>Désactivation des Sign-In et des Office Add-Ins cloud
  
Les clients de licence en volume peuvent avoir des stratégies strictes sur l’enregistrement des documents dans le stockage cloud. La préférence par application suivante peut être définie pour désactiver la connexion MSA/OrgID et l’accès aux compléments Office.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

Si les utilisateurs tentent d’accéder à la fonction Sign-In, ils verront une erreur indiquant qu’une connexion réseau n’est pas présente. Étant donné que cette préférence bloque également l’activation du produit en ligne, elle ne doit être utilisée que pour les installations de licence en volume. Plus précisément, l’utilisation de cette préférence empêchera Office applications d’accéder aux points de terminaison suivants :
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- Tous les points de terminaison répertoriés dans la section « Connexion » ci-dessus.
    
- Tous les points de terminaison répertoriés dans la section « Recherche intelligente » ci-dessus.
    
- Tous les points de terminaison répertoriés dans la section « Activation du produit » ci-dessus.
    
- Tous les points de terminaison répertoriés dans la section « Office Apps (compléments) » ci-dessus.
    
Pour rétablir toutes les fonctionnalités de l’utilisateur, définissez la préférence sur « 2 » ou supprimez-la.
  
> [!NOTE]
> Cette préférence nécessite Office pour Mac build 15.25 [160726] ou ultérieure. 
  
### <a name="telemetry"></a>Télémétrie
  
Office pour Mac renvoie des informations de télémétrie à Microsoft à intervalles réguliers. Les données sont chargées vers le point de terminaison « Nexus ». Les données de télémétrie aident l’équipe d’ingénierie à évaluer l’intégrité et les comportements inattendus de chaque application Office. Il existe deux catégories de télémétrie :
  
- **Heartbeat** contient les informations de version et de licence. Ces données sont envoyées immédiatement au lancement de l’application. 
    
- **L’utilisation** contient des informations sur la façon dont les applications sont utilisées et les erreurs non irrécupérables. Ces données sont envoyées toutes les 60 minutes. 
    
Microsoft prend votre vie privée très au sérieux. Pour plus d’informations sur la stratégie de collecte de données de Microsoft, consultez [https://privacy.microsoft.com](https://privacy.microsoft.com). Pour empêcher les applications d’envoyer des données de télémétrie « Utilisation », la préférence **SendAllTelemetryEnabled** peut être ajustée. La préférence est par application et peut être définie via des profils de configuration macOS ou manuellement à partir du terminal : 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

La télémétrie de pulsation est toujours envoyée et ne peut pas être désactivée.
  
### <a name="crash-reporting"></a>Rapports sur les incidents
  
Lorsqu’une erreur d’application irrécupérable se produit, l’application se termine de façon inattendue et charge un rapport d’incident dans le service « Watson ». Le rapport d’incident se compose d’une pile d’appels, qui est la liste des étapes traitées par l’application avant l’incident. Ces étapes aident l’équipe d’ingénierie à identifier la fonction exacte qui a échoué et pourquoi.
  
Dans certains cas, le contenu d’un document entraîne le blocage de l’application. Si l’application identifie le document comme cause, elle demande à l’utilisateur s’il est possible d’envoyer également le document avec la pile des appels. Les utilisateurs peuvent faire un choix éclairé à cette question. Les administrateurs informatiques peuvent avoir des exigences strictes concernant la transmission de documents et prendre la décision au nom de l’utilisateur de ne jamais envoyer de documents. La préférence suivante peut être définie pour empêcher l’envoi de documents et pour supprimer l’invite à l’utilisateur :
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> Si **SendAllTelemetryEnabled** a la valeur **FALSE**, tous les rapports d’incident pour ce processus sont désactivés. Pour activer la création de rapports d’incidents sans envoyer de données de télémétrie d’utilisation, vous pouvez définir la préférence suivante : ```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>Mises à jour
  
Microsoft publie Office pour Mac mises à jour à intervalles réguliers (généralement une fois par mois). Nous encourageons vivement les utilisateurs et les administrateurs informatiques à maintenir les machines à jour pour garantir l’installation des derniers correctifs de sécurité. Dans les cas où les administrateurs informatiques souhaitent contrôler et gérer étroitement les mises à jour de l’ordinateur, la préférence suivante peut être définie pour empêcher le processus de mise à jour automatique de détecter et d’offrir automatiquement des mises à jour de produit :
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>Blocage des demandes avec un pare-feu/proxy
  
Si votre organisation bloque les requêtes adressées aux URL via un pare-feu ou un serveur proxy, veillez à configurer les URL répertoriées dans ce document comme étant autorisées ou bloquées avec une réponse 40X (par exemple, 403 ou 404). Une réponse 40X permet aux applications Office d’accepter de manière appropriée l’incapacité d’accéder à la ressource, et fournit une expérience utilisateur plus rapide, que de simplement supprimer la connexion, ce qui entraîne à son tour le client à réessayer.
  
Si votre serveur proxy nécessite une authentification, une réponse 407 est retournée au client. Pour une expérience optimale, assurez-vous que vous utilisez Office pour Mac builds 15.27 ou ultérieures, car elles incluent des correctifs spécifiques pour l’utilisation des serveurs NTLM et Kerberos.
  
  
## <a name="see-also"></a>Voir aussi

[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)

