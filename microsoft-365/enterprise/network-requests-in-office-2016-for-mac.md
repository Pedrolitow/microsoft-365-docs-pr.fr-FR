---
title: Requêtes réseau dans Office pour Mac
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/9/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: Cet article décrit les points de terminaison et les URL que les applications Office pour Mac tentent d’atteindre, ainsi que les services fournis.
ms.openlocfilehash: b777b4ea7e03495cb6389be8fe05e96a26fd9664
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46689933"
---
# <a name="network-requests-in-office-for-mac"></a>Requêtes réseau dans Office pour Mac

Les applications Office pour Mac offrent une expérience d’application native sur la plateforme macOS. Chaque application est conçue pour fonctionner dans divers scénarios, y compris les états dans lesquels aucun accès réseau n’est disponible. Lorsqu’un ordinateur est connecté à un réseau, les applications se connectent automatiquement à une série de services web pour fournir des fonctionnalités améliorées. Les informations suivantes décrivent les points de terminaison et les URL que les applications tentent d’atteindre, ainsi que les services fournis. Ces informations sont utiles pour résoudre les problèmes de configuration réseau et définir des stratégies pour les serveurs proxy réseau. Les détails de cet article sont destinés à compléter l’article url et [plages d’adresses Office 365,](urls-and-ip-address-ranges.md)qui inclut les points de terminaison pour les ordinateurs exécutant Microsoft Windows. Sauf indication, les informations de cet article s’appliquent également à Office 2019 pour Mac et Office 2016 pour Mac, qui sont disponibles sous la mesure d’un achat à prix seul dans un magasin de vente au détail ou via un contrat de licence en volume. 

  
La plupart de cet article présente des tableaux détaillant les URL réseau, le type et la description du service ou de la fonctionnalité fournis par ce point de terminaison. Chacune des applications Office peut différer dans son utilisation des services et des points de terminaison. Les applications suivantes sont définies dans les tableaux ci-dessous :
  
- W : Word
- P : PowerPoint
- X : Excel
- O : Outlook
- N : OneNote
   
Le type d’URL est défini comme suit :
  
- ST : Statique : l’URL est codée en dur dans l’application cliente.
    
- SS : Semi-Static - L’URL est codée dans le cadre d’une page web ou d’un redirecteur.
    
- CS : Service de configuration : l’URL est renvoyée dans le cadre du service de configuration Office.

    
## <a name="office-for-mac-default-configuration"></a>Configuration par défaut d’Office pour Mac

 **Installation et mises à jour**
  
Les points de terminaison réseau suivants sont utilisés pour télécharger le programme d’installation d’Office pour Mac à partir du Réseau de distribution de contenu (CDN) Microsoft.
  
|**URL**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |Le portail d’installation Microsoft 365 permet d’établir un lien vers les packages d’installation les plus récents.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |Emplacement des packages d’installation sur le réseau de distribution de contenu.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |Emplacement des packages d’installation sur le réseau de distribution de contenu.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |Point de terminaison Contrôle de gestion pour la mise à jour automatique Microsoft  <br/> |
   
 **Premier lancement d’application**
  
Les points de terminaison réseau suivants sont contactés lors du premier lancement d’une application Office. Ces points de terminaison fournissent des fonctionnalités Office améliorées pour les utilisateurs, et les URL sont contactées quel que soit le type de licence (y compris les installations avec licence en volume).
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |Configuration de « flighting » : autorise l’éclairage et l’expérimentation des fonctionnalités.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |Test de configuration réseau « Flighting »  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |Test de configuration réseau « Flighting »  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Service de configuration Office : liste principale des points de terminaison de service.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Téléchargement de télémétrie règles Office : informe le client sur les données et les événements à télécharger vers le service de télémétrie.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |Service de télémétrie OneNote  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Rapports de téléchargement de télémétrie Office : les événements de « cœur » et d’erreur qui se produisent sur le client sont téléchargés vers le service de télémétrie.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Service de modèle Office : fournit aux utilisateurs des modèles de documents en ligne.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Téléchargements de modèles Office : stockage des images de modèle PNG.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Configuration du Windows Store pour les applications Office.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Catalogue des services d’intégration de documents Office (liste des services et points de terminaison) et découverte de domaine d’accueil.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Ressources pour la découverte de domaine d’accueil v2 (15.40 et ultérieures)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Manifestes de mise à jour automatique Microsoft : vérifie si des mises à jour sont disponibles  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Bibliothèque JavaScript Microsoft Ajax  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Configuration et ressources de l’application Wikipedia pour Office.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Configuration et ressources de l’application Bing Map pour Office.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Ressources et configuration de l’application Graph de personnes pour Office.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ST  <br/> |Nouveautés du contenu pour OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ST  <br/> |Nouveau contenu pour OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |Images nouvelles pour OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |Service de support dans l’application.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |Service de détection de compte de messagerie.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |Découverte automatique Outlook  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Point de terminaison Outlook pour le service Microsoft 365.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |Icônes pour les add-ins Outlook.  <br/> |
   
> [!NOTE]
> Le service de configuration Office agit comme un service de découverte automatique pour tous les clients Microsoft Office, pas seulement pour Mac. Les points de terminaison renvoyés dans la réponse sont semi-statiques, car la modification est très rare, mais toujours possible. 
  
 **Connexion**
  
Les points de terminaison réseau suivants sont contactés lors de la signature du stockage en nuage. En fonction de votre type de compte, différents services peuvent être contactés. Par exemple :
  
- **MSA : Compte Microsoft** - généralement utilisé pour les scénarios grand public et commercial 
    
- **OrgID : Compte d’organisation** - généralement utilisé pour les scénarios commerciaux 
    
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |Service d’autorisation Windows  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |Service de connexion Microsoft 365 (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Service de connexion de compte Microsoft (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |MSA (Microsoft Account Login Service Helper)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Authentification Microsoft 365 (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Document and Places Storage Locator  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Dernier service de document utilisé (MRU)  <br/> |
   
> [!NOTE]
> Pour les licences basées sur un abonnement et la vente au détail, la signature active le produit et permet d’accéder aux ressources cloud telles que OneDrive. Pour les installations avec licence en volume, les utilisateurs sont toujours invités à se connecter (par défaut), mais cela n’est requis que pour l’accès aux ressources cloud, car le produit est déjà activé. 
  
 **Activation du produit**
  
Les points de terminaison réseau suivants s’appliquent aux activations d’abonnement Et de licence commerciale Microsoft 365. Plus précisément, cela ne s’applique PAS aux installations de licence en volume.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Service de gestion des licences Office  <br/> |
   
 **Nouveautés du contenu**
  
Les points de terminaison réseau suivants s’appliquent uniquement à l’abonnement Microsoft 365.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |Contenu de la page JSON nouveautés.  <br/> |
   
 **Recherche**
  
Les points de terminaison réseau suivants s’appliquent uniquement à l’abonnement Microsoft 365.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Service Web De recherche  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Contenu statique De la recherche  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |Fournisseur de contenu Recherche  <br/> |
   
 **Recherche intelligente**
  
Les points de terminaison réseau suivants s’appliquent aux activations des abonnements Microsoft 365 et des licences en volume ou au détail.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Insights Web Service  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |Bibliothèque JQuery  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |Prise en charge de la bibliothèque JavaScript  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |Fournisseur de contenu Insights  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |Fournisseur de contenu Insights  <br/> |
   
 **Concepteur PowerPoint**
  
Les points de terminaison réseau suivants s’appliquent uniquement à l’abonnement Microsoft 365.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |Service web de PowerPoint Designer  <br/> |
   
 **Aide au démarrage de PowerPoint**
  
Les points de terminaison réseau suivants s’appliquent uniquement à l’abonnement Microsoft 365.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |Service web PowerPoint QuickStarter  <br/> |
   
 **Envoyer un souris/un frown**
  
Les points de terminaison réseau suivants s’appliquent aux activations des abonnements Microsoft 365 et des licences en volume ou au détail.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |Envoyer un service de souris  <br/> |
   
 **Contacter le support technique**
  
Les points de terminaison réseau suivants s’appliquent aux activations des abonnements Microsoft 365 et des licences en volume ou au détail.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |Contacter le service de support technique  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |Service de support dans l’application  <br/> |
   
 **Enregistrer au format PDF**
  
Les points de terminaison réseau suivants s’appliquent aux activations des abonnements Microsoft 365 et des licences en volume ou au détail.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Service de conversion de documents Word (PDF)  <br/> |
   
 **Applications Office (également appelées « add-ins ) »**
  
Les points de terminaison réseau suivants s’appliquent à la fois aux activations d’abonnement Microsoft 365 et aux activations de licence commerciale/en volume lorsque les compléments d’application Office sont fiables.
  
|**URL**|**Applications**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |Configuration de l’App Store Office  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Ressources d’application Wikipedia  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Ressources de l’application Bing Map  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |Ressources de l’application Graphe des personnes  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Office Redirection Service  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |Bibliothèques JavaScript Office  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |Service de télémétrie et de rapports pour les applications Office  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SS  <br/> |Bibliothèque JavaScript Microsoft Ajax  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Bibliothèque JavaScript Microsoft Ajax  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Bibliothèques JavaScript Office  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Ressources de support  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Ressources de support  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |Ressources de support  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |Bibliothèque JavaScript  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |Rapports d'erreurs  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |Ressources de police  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |Service de télémétrie  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Rapports de télémétrie  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |Bibliothèque de biens du Microsoft Store  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SS  <br/> |Ressources de page Wikipedia  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SS  <br/> |Ressources multimédias Wikipedia  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SS  <br/> |Cadre bac à sable Wikipedia  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |Modèles de carte  <br/> |
   
 **Liens fiables**
  
Le point de terminaison réseau suivant s’applique à toutes les applications Office pour l’abonnement Microsoft 365 uniquement.
  
|**URL**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Service de liens sécurisés Microsoft  <br/> |
   
 **Rapports d’incident**
  
Le point de terminaison réseau suivant s’applique à toutes les applications Office pour les activations d’abonnement Microsoft 365 et de licence commerciale/en volume. Lorsqu’un processus se crashe de façon inattendue, un rapport est généré et envoyé au service Watson.
  
|**URL**|**Type (Type)**|**Description**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |Service de rapport d’erreurs Microsoft  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |Service d’informations collaboratives Office  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>Options de réduction des demandes réseau et du trafic

La configuration par défaut d’Office pour Mac offre la meilleure expérience utilisateur, à la fois en termes de fonctionnalités et de maintien à jour de l’ordinateur. Dans certains scénarios, vous pouvez empêcher les applications de contacter les points de terminaison réseau. Cette section présente les options qui s’offrent à vous.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>Désactivation de Cloud Sign-In et d’Office Add-Ins
  
Les clients avec licence en volume peuvent avoir des stratégies strictes concernant l’enregistrement de documents dans un stockage en nuage. Les préférences par application suivantes peuvent être définies pour désactiver la signature MSA/OrgID et l’accès aux applications Office.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

Si les utilisateurs tentent d’accéder Sign-In fonction, une erreur s’est produite lorsqu’une connexion réseau n’est pas présente. Étant donné que cette préférence bloque également l’activation du produit en ligne, elle ne doit être utilisée que pour les installations de licence en volume. Plus précisément, l’utilisation de cette préférence empêche les applications Office d’accéder aux points de terminaison suivants :
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- Tous les points de terminaison répertoriés dans la section « Se connecter » ci-dessus.
    
- Tous les points de terminaison répertoriés dans la section « Recherche intelligente » ci-dessus.
    
- Tous les points de terminaison répertoriés dans la section « Activation de produit » ci-dessus.
    
- Tous les points de terminaison répertoriés dans la section « Applications Office (également appelées applications) » ci-dessus.
    
Pour rétablir toutes les fonctionnalités pour l’utilisateur, définissez la préférence sur « 2 » ou supprimez-la.
  
> [!NOTE]
> Cette préférence nécessite Office pour Mac build 15.25 [160726] ou une ultérieure. 
  
### <a name="telemetry"></a>Télémétrie
  
Office pour Mac renvoie les informations de télémétrie à Microsoft à intervalles réguliers. Les données sont téléchargées vers le point de terminaison « Nexus ». Les données de télémétrie aident l’équipe d’ingénierie à évaluer l’état d’santé et les comportements inattendus de chaque application Office. Il existe deux catégories de télémétrie :
  
- **Heartbeat contient** des informations sur la version et la licence. Ces données sont envoyées immédiatement au lancement de l’application. 
    
- **L’utilisation** contient des informations sur l’utilisation des applications et les erreurs non fatales. Ces données sont envoyées toutes les 60 minutes. 
    
Microsoft prend votre confidentialité très au sérieux. Vous pouvez en savoir plus sur la stratégie de collecte de données de Microsoft sur [https://privacy.microsoft.com](https://privacy.microsoft.com) . Pour empêcher les applications d’envoyer la télémétrie « Utilisation » , la préférence **SendAllTelemetryEnabled** peut être ajustée. La préférence est par application et peut être définie via les profils de configuration macOS ou manuellement à partir de Terminal : 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

La télémétrie pulsation est toujours envoyée et ne peut pas être désactivée.
  
### <a name="crash-reporting"></a>Rapports d’incident
  
Lorsqu’une erreur d’application fatale se produit, l’application se termine et charge inopinément un rapport d’incident vers le service « Watson ». Le rapport d’incident se compose d’une pile d’appels, qui est la liste des étapes que l’application a traitées avant le crash. Ces étapes aident l’équipe d’ingénierie à identifier la fonction exacte qui a échoué et pourquoi.
  
Dans certains cas, le contenu d’un document entraîne le crash de l’application. Si l’application identifie le document comme cause, elle demande à l’utilisateur s’il est possible d’envoyer également le document avec la pile d’appels. Les utilisateurs peuvent faire un choix informé à cette question. Les administrateurs informatiques peuvent avoir des exigences strictes en matière de transmission des documents et décider au nom de l’utilisateur de ne jamais envoyer de documents. La préférence suivante peut être définie pour empêcher l’envoi de documents et pour supprimer l’invite à l’utilisateur :
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> Si **SendAllTelemetryEnabled** est définie sur **FALSE,** tous les rapports d’incident pour ce processus sont désactivés. Pour activer la notification d’incident sans envoyer de télémétrie d’utilisation, vous pouvez définir les préférences suivantes : ```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>Mises à jour
  
Microsoft publie les mises à jour Office pour Mac à intervalles réguliers (généralement une fois par mois). Nous encourageons vivement les utilisateurs et les administrateurs informatiques à maintenir les ordinateurs à jour pour s’assurer que les derniers correctifs de sécurité sont installés. Dans les cas où les administrateurs informatiques souhaitent contrôler et gérer étroitement les mises à jour des ordinateurs, les préférences suivantes peuvent être définies pour empêcher le processus de mise à jour automatique de détecter et d’offrir automatiquement des mises à jour de produit :
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>Blocage des demandes avec un pare-feu/proxy
  
Si votre organisation bloque les demandes d’URL via un pare-feu ou un serveur proxy, assurez-vous de configurer les URL répertoriées dans ce document comme étant autorisées ou de bloquer avec une réponse 40X (par exemple, 403 ou 404). Une réponse 40X permet aux applications Office d’accepter normalement l’impossibilité d’accéder à la ressource et offre une expérience utilisateur plus rapide, plutôt que de simplement abandonner la connexion, ce qui entraîne une nouvelle tentative du client.
  
Si votre serveur proxy nécessite une authentification, une réponse 407 est renvoyée au client. Pour une expérience de qualité, assurez-vous d’utiliser les builds 15.27 ou ultérieures d’Office pour Mac, car elles incluent des correctifs spécifiques pour l’utilisation de serveurs NTLM et Kerberos.
  
  
## <a name="see-also"></a>Voir aussi

[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)

