---
title: Requêtes réseau dans Office pour Mac
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/9/2018
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: Cet article décrit les points de terminaison et LES URL que Office pour Mac applications tentent d’atteindre, ainsi que les services fournis.
ms.openlocfilehash: e42f5c8f9878ebd3e4ac40d77f96aa115c875e54
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68189756"
---
# <a name="network-requests-in-office-for-mac"></a>Requêtes réseau dans Office pour Mac

Office pour Mac applications offrent une expérience d’application native sur la plateforme macOS. Chaque application est conçue pour fonctionner dans divers scénarios, y compris les états lorsqu’aucun accès réseau n’est disponible. Lorsqu’une machine est connectée à un réseau, les applications se connectent automatiquement à une série de services web pour fournir des fonctionnalités améliorées. Les informations suivantes décrivent les points de terminaison et LES URL que les applications tentent d’atteindre, ainsi que les services fournis. Ces informations sont utiles lors de la résolution des problèmes de configuration réseau et de la définition de stratégies pour les serveurs proxy réseau. Les détails de cet article sont destinés à compléter [l’article Office 365 URL et plages d’adresses](urls-and-ip-address-ranges.md), qui inclut des points de terminaison pour les ordinateurs exécutant Microsoft Windows. Sauf indication contraire, les informations contenues dans cet article s’appliquent également à Office 2019 pour Mac et Office 2016 pour Mac, qui sont disponibles en tant qu’achat unique auprès d’un magasin de détail ou par le biais d’un contrat de licence en volume. 

  
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
  
Les points de terminaison réseau suivants sont utilisés pour télécharger le programme d’installation Office pour Mac à partir de Microsoft Content Delivery Network (CDN).
  
|**URL**|**Type**|**Description**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |St  <br/> |Le portail d’installation Microsoft 365 transfère le service de liaison aux derniers packages d’installation.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |Ss  <br/> |Emplacement des packages d’installation sur le réseau de distribution de contenu.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |Ss  <br/> |Emplacement des packages d’installation sur le réseau de distribution de contenu.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |St  <br/> |Point de terminaison du contrôle de gestion pour Microsoft AutoUpdate  <br/> |
   
 **Premier lancement d’application**
  
Les points de terminaison réseau suivants sont contactés lors du premier lancement d’une application Office. Ces points de terminaison fournissent des fonctionnalités Office améliorées pour les utilisateurs, et les URL sont contactées quel que soit le type de licence (y compris les installations de licence en volume).
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |St  <br/> |Configuration « Flighting » : permet l’éclairage et l’expérimentation des fonctionnalités.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |St  <br/> |Test de configuration réseau « flighting »  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |St  <br/> |Test de configuration réseau « flighting »  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |St  <br/> |Service de configuration Office - Liste principale des points de terminaison de service.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |St  <br/> |Téléchargement de la télémétrie des règles Office : informe le client des données et des événements à charger sur le service de télémétrie.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |Cs  <br/> |Service de télémétrie OneNote  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |St  <br/> |Rapports de chargement de télémétrie Office - « Heartbeart » et les événements d’erreur qui se produisent sur le client sont chargés vers le service de télémétrie.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |Cs  <br/> |Service modèle Office : fournit aux utilisateurs des modèles de document en ligne.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |Cs  <br/> |Téléchargements de modèles Office - Stockage d’images de modèle PNG.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |Cs  <br/> |Configuration du Store pour les applications Office.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |Cs  <br/> |Catalogue Office Document Integration Services (liste des services et points de terminaison) et découverte du domaine d’accueil.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |Cs  <br/> |Ressources pour la découverte du domaine d’accueil v2 (15.40 et versions ultérieures)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |St  <br/> |Microsoft AutoUpdate Manifests : vérifie s’il existe des mises à jour disponibles  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |Ss  <br/> |Bibliothèque JavaScript Microsoft Ajax  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |Ss  <br/> |Application Wikipédia pour la configuration et les ressources Office.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |Ss  <br/> |Application Bing Map pour la configuration et les ressources Office.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |Ss  <br/> |Personnes application Graph pour la configuration et les ressources Office.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |St  <br/> |Nouveautés de OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |St  <br/> |Nouveau contenu pour OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |Ss  <br/> |Nouveautés des images pour OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |St  <br/> |Service de support dans l’application.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |St  <br/> |Email service de détection de compte.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |St  <br/> |Découverte automatique d’Outlook  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |St  <br/> |Point de terminaison Outlook pour le service Microsoft 365.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |St  <br/> |Icônes pour les compléments Outlook.  <br/> |
   
> [!NOTE]
> Le service de configuration Office agit comme un service de découverte automatique pour tous les clients Microsoft Office, pas seulement pour Mac. Les points de terminaison retournés dans la réponse sont semi-statiques, dans la raison que le changement est très peu fréquent, mais toujours possible. 
  
 **Connexion**
  
Les points de terminaison réseau suivants sont contactés lors de la connexion au stockage cloud. Selon le type de votre compte, différents services peuvent être contactés. Par exemple :
  
- **MSA : Compte Microsoft** - généralement utilisé pour les scénarios de consommation et de vente au détail 
    
- **OrgID : Compte d’organisation** - généralement utilisé pour les scénarios commerciaux 
    
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |St  <br/> |Service d’autorisation Windows  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |St  <br/> |Service de connexion Microsoft 365 (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |St  <br/> |Microsoft Account Login Service (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |Cs  <br/> |Microsoft Account Login Service Helper (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |Ss  <br/> |Personnalisation de connexion Microsoft 365 (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |Cs  <br/> |Localisateur de stockage de documents et de lieux  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |Cs  <br/> |Service de document MRU (Most Recently Used)  <br/> |
   
> [!NOTE]
> Pour les licences basées sur les abonnements et les licences de vente au détail, la connexion active le produit et permet l’accès aux ressources cloud telles que OneDrive. Pour les installations de licence en volume, les utilisateurs sont toujours invités à se connecter (par défaut), mais cela n’est requis que pour l’accès aux ressources cloud, car le produit est déjà activé. 
  
 **Activation du produit**
  
Les points de terminaison réseau suivants s’appliquent aux activations d’abonnement Microsoft 365 et de licence de vente au détail. Plus précisément, cela ne s’applique PAS aux installations de licence en volume.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |Cs  <br/> |Service de gestion des licences Office  <br/> |
   
 **Nouveautés du contenu**
  
Les points de terminaison réseau suivants s’appliquent uniquement à l’abonnement Microsoft 365.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |Ss  <br/> |Nouveautés de la page JSON.  <br/> |
   
 **Recherche**
  
Les points de terminaison réseau suivants s’appliquent uniquement à l’abonnement Microsoft 365.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |Cs  <br/> |Service web de recherche  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |Cs  <br/> |Contenu statique du chercheur  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |Cs  <br/> |Fournisseur de contenu de recherche  <br/> |
   
 **Recherche intelligente**
  
Les points de terminaison réseau suivants s’appliquent à la fois aux activations d’abonnement Microsoft 365 et de licences de vente au détail/volume.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |Cs  <br/> |Insights Web Service  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |Cs  <br/> |Bibliothèque JQuery  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |Cs  <br/> |Prise en charge de la bibliothèque JavaScript  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |Cs  <br/> |Fournisseur de contenu Insights  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |Cs  <br/> |Fournisseur de contenu Insights  <br/> |
   
 **Concepteur PowerPoint**
  
Les points de terminaison réseau suivants s’appliquent uniquement à l’abonnement Microsoft 365.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |Cs  <br/> |Service web PowerPoint Designer  <br/> |
   
 **Aide au démarrage de PowerPoint**
  
Les points de terminaison réseau suivants s’appliquent uniquement à l’abonnement Microsoft 365.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |Cs  <br/> |Service web De démarrage rapide PowerPoint  <br/> |
   
 **Envoyer un sourire/un froncement de dents**
  
Les points de terminaison réseau suivants s’appliquent à la fois aux activations d’abonnement Microsoft 365 et de licences de vente au détail/volume.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |Cs  <br/> |Envoyer un service Smile  <br/> |
   
 **Contacter le support technique**
  
Les points de terminaison réseau suivants s’appliquent à la fois aux activations d’abonnement Microsoft 365 et de licences de vente au détail/volume.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |Cs  <br/> |Contacter le service de support technique  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |Cs  <br/> |Service de support dans l’application  <br/> |
   
 **Enregistrer au format PDF**
  
Les points de terminaison réseau suivants s’appliquent à la fois aux activations d’abonnement Microsoft 365 et de licences de vente au détail/volume.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |Cs  <br/> |Service de conversion de documents Word (PDF)  <br/> |
   
 **Applications Office (également appelés compléments)**
  
Les points de terminaison réseau suivants s’appliquent à la fois aux activations d’abonnement Microsoft 365 et de licence de vente au détail/licence en volume lorsque les compléments d’application Office sont approuvés.
  
|**URL**|**Applications**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |Cs  <br/> |Configuration de l’App Store Office  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |Ss  <br/> |Ressources de l’application Wikipédia  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |Ss  <br/> |Ressources de l’application Carte Bing  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |Ss  <br/> |ressources de l’application graphe Personnes  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |Ss  <br/> |Office Redirection Service  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |Ss  <br/> |Bibliothèques JavaScript Office  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |Wx  <br/> |Ss  <br/> |Télémétrie et Reporting Service pour les applications Office  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |Ss  <br/> |Bibliothèque JavaScript Microsoft Ajax  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |Ss  <br/> |Bibliothèque JavaScript Microsoft Ajax  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |Ss  <br/> |Bibliothèques JavaScript Office  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |Ss  <br/> |Ressources de support  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |Ss  <br/> |Ressources de support  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |Ss  <br/> |Ressources de support  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |Ss  <br/> |Bibliothèque JavaScript  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |Ss  <br/> |Rapports d'erreurs  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |Ss  <br/> |Ressources de police  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |Ss  <br/> |Service de télémétrie  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |Ss  <br/> |Rapports de télémétrie  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |Ss  <br/> |Bibliothèque d’éléments multimédias du Microsoft Store  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |Ss  <br/> |Ressources de la page Wikipédia  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |Ss  <br/> |Ressources multimédias Wikipédia  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |Ss  <br/> |Trame de bac à sable Wikipédia  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |Ss  <br/> |Modèles de carte  <br/> |
   
 **Liens fiables**
  
Le point de terminaison réseau suivant s’applique à toutes les applications Office pour l’abonnement Microsoft 365 uniquement.
  
|**URL**|**Type**|**Description**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |Cs  <br/> |Microsoft Safe Link Service  <br/> |
   
 **Rapports sur les incidents**
  
Le point de terminaison réseau suivant s’applique à toutes les applications Office pour les activations d’abonnement Microsoft 365 et de licences de vente au détail/volume. Lorsqu’un processus se bloque de manière inattendue, un rapport est généré et envoyé au service Watson.
  
|**URL**|**Type**|**Description**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |St  <br/> |Service de création de rapports d’erreurs Microsoft  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |St  <br/> |Office Collaborative Insights Service  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>Options de réduction des demandes réseau et du trafic

La configuration par défaut de Office pour Mac offre la meilleure expérience utilisateur, à la fois en termes de fonctionnalités et de mise à jour de l’ordinateur. Dans certains scénarios, vous souhaiterez peut-être empêcher les applications de contacter des points de terminaison réseau. Cette section décrit les options pour ce faire.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>Désactivation des Sign-In cloud et des Add-Ins Office
  
Les clients de licence en volume peuvent avoir des stratégies strictes sur l’enregistrement des documents dans le stockage cloud. La préférence par application suivante peut être définie pour désactiver la connexion MSA/OrgID et l’accès aux compléments Office.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

Si les utilisateurs tentent d’accéder à la fonction Sign-In, ils verront une erreur indiquant qu’une connexion réseau n’est pas présente. Étant donné que cette préférence bloque également l’activation du produit en ligne, elle ne doit être utilisée que pour les installations de licence en volume. Plus précisément, l’utilisation de cette préférence empêchera les applications Office d’accéder aux points de terminaison suivants :
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- Tous les points de terminaison répertoriés dans la section « Connexion » ci-dessus.
    
- Tous les points de terminaison répertoriés dans la section « Recherche intelligente » ci-dessus.
    
- Tous les points de terminaison répertoriés dans la section « Activation du produit » ci-dessus.
    
- Tous les points de terminaison répertoriés dans la section « Applications Office (compléments) » ci-dessus.
    
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

