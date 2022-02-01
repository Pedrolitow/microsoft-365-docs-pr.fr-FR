---
title: Autres points de terminaison non inclus dans le service Office 365 ADRESSE IP et URL
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/31/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: ''
description: 'Résumé : Le nouveau service Web de point de terminaison n’inclut pas quelques points de terminaison pour des scénarios spécifiques.'
hideEdit: true
ms.openlocfilehash: 0453efbea7957c3cf859c59da7a2cff7db04b4f0
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2022
ms.locfileid: "62295145"
---
# <a name="other-endpoints-not-included-in-the-office-365-ip-address-and-url-web-service"></a>Autres points de terminaison non inclus dans le service Office 365 ADRESSE IP et URL

Certains points de terminaison réseau ont été publiés précédemment et n’ont pas été inclus dans [l’adresse IP Office 365 et le service Web d’URL](microsoft-365-ip-web-service.md). Le service web publie les points de terminaison réseau requis pour la Office 365 réseau de périmètre d’entreprise. Cette étendue n’inclut actuellement pas :

1. connectivité réseau pouvant être requise d’un centre de données Microsoft vers un réseau client (trafic réseau de serveur hybride entrant) ;
2. connectivité réseau de serveurs sur un réseau client au sein du périmètre d’entreprise (trafic réseau de serveur sortant) ;
3. rares scénarios d’exigences de connectivité réseau de la part d’un utilisateur ;
4. exigences en matière de connectivité de résolution DNS (non répertorié ci-dessous) ;
5. sites approuvés Internet Explorer ou Microsoft Edge.

Hormis le DNS, ces instances sont toutes facultatives pour la plupart des clients, sauf si vous avez besoin du scénario spécifique décrit.

<br>

****

|Ligne|Objectif|Destination|Type|
|---|---|---|---|
|1|**[Service d’importation](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) pour l’ingestion de fichiers et PST**|Pour plus [d’informations, reportez-vous au service](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) d’importation.|Scénario sortant rare|
|2|**[Assistant Support et récupération de Microsoft pour Office 365](https://diagnostics.office.com/#/)**|<https://autodiscover.outlook.com> <br> <https://officecdn.microsoft.com> <br> <https://api.diagnostics.office.com> <br> <https://apibasic.diagnostics.office.com> <br> <https://autodiscover-s.outlook.com> <br> <https://cloudcheckenabler.azurewebsites.net> <br> <https://login.live.com> <br> <https://login.microsoftonline.com> <br> <https://login.windows.net> <br> <https://o365diagtelemetry.trafficmanager.net> <br> <https://odc.officeapps.live.com> <br> <https://offcatedge.azureedge.net> <br> <https://officeapps.live.com> <br> <https://outlook.office365.com> <br> <https://outlookdiagnostics.azureedge.net>|Trafic serveur sortant|
|3|**Azure AD Connecter (option w/SSO)** <p> WinRM & PowerShell à distance|Environnement STS client (serveur AD FS et proxy AD FS) \| Ports TCP 80 et 443|Trafic serveur entrant|
|4|**STS** tel que les serveurs proxy AD FS (pour les clients fédérés uniquement)|STS client (comme un proxy AD FS) \| Ports TCP 443 ou TCP 49443 avec ClientTLS|Trafic serveur entrant|
|5|**[Intégration de la messagerie unifiée Exchange Online/SBC](/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/configuration-notes-for-session-border-controllers)**|Bidirectionnel entre le contrôleur de frontière de session local et \*le contrôleur .um.outlook.com|Trafic serveur sortant uniquement|
|6 |**Migration de boîtes aux lettres**<p>Lorsque la migration de boîtes aux lettres est lancée à partir [](/exchange/exchange-deployment-assistant) d’un Exchange hybride local vers Office 365, Office 365 se connecte à votre serveur Exchange Web Services (EWS)/Services de réplication de boîtes aux lettres (MRS) publié. Si vous avez besoin des adresses IP NAT utilisées par les serveurs Exchange Online pour limiter les connexions entrantes à partir de plages d’adresses IP sources spécifiques, elles sont répertoriées dans les [plages d’adresses IP & URL Office 365](urls-and-ip-address-ranges.md) sous la zone de service « Exchange Online ». <p> Veillez à ce que l’accès aux points de terminaison EWS publiés tels que OWA ne soit pas impacté en vous assurant que le proxy MRS est résolu en un FQDN distinct et une adresse IP publique avant de restreindre les connexions TCP 443 à partir de plages d’adresses IP sources spécifiques.|Proxy EWS/MRS local client <br> Port TCP 443.|Trafic serveur entrant|
|7 |**[Exchange de](/exchange/exchange-deployment-assistant) coexistence hybride, telles** que le partage de la fonction de libre/occupé.|Serveur Exchange client local|Trafic serveur entrant|
|8 |**[Exchange’authentification](/exchange/exchange-deployment-assistant) proxy hybride**|STS local client|Trafic serveur entrant|
|9 |Utilisé pour configurer Exchange [hybride, à](/exchange/exchange-deployment-assistant) l’aide de l Exchange **[de configuration hybride hybride](/exchange/hybrid-configuration-wizard)** <p> Remarque : ces points de terminaison sont uniquement nécessaires pour configurer Exchange hybride|domains.live.com sur les ports TCP 80 et 443, obligatoire uniquement pour l’Assistant Configuration hybride Exchange 2010 SP3. <p> GCC High, DoD IP addresses: 40.118.209.192/32; 168.62.190.41/32 <p> Produits commerciaux & Cloud de la communauté du secteur public : \*.store.core.windows.net; asl.configure.office.com; tds.configure.office.com; mshybridservice.trafficmanager.net ; <br> aka.ms/hybridwizard; <br> \*shcwreleaseprod.blob.core.windows.net/shcw/;|Trafic serveur sortant uniquement|
|10|Le **service Detect automatique** est utilisé dans les scénarios hybrides [Exchange](/exchange/exchange-deployment-assistant) avec l’authentification moderne hybride [avec Outlook pour iOS et Android](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) <p> `*.acompli.net` <br> `*.outlookmobile.com` <br> `*.outlookmobile.us` <br> `52.125.128.0/20` <br> `52.127.96.0/23`|Serveur Exchange client local sur TCP 443|Trafic serveur entrant|
|11|**Exchange’authentification Azure AD hybride**|*.msappproxy.net|Trafic serveur sortant TCP uniquement|
|12 |Skype Entreprise dans Office 2016 inclut le partage d’écran **vidéo, qui** utilise des ports UDP. Les Skype Entreprise clients de Office 2013 et les antérieures utilisaient RDP sur le port TCP 443.|Le port TCP 443 s’ouvre à 52.112.0.0/14|Versions de clients plus anciens Skype Entreprise dans Office 2013 et versions antérieures|
|13|**Skype Entreprise connectivité de serveur local hybride** à Skype Entreprise Online|13.107.64.0/18, 52.112.0.0/14 <br> Ports UDP 50,000-59,999 <br> Ports TCP 50,000-59,999 ; 5061|Connectivité sortante de serveur local Skype Entreprise|
|14 |**Le réseau PSTN cloud** avec connectivité hybride sur site nécessite une connectivité réseau ouverte aux hôtes locaux. Pour plus d’informations sur les configurations hybrides Skype Entreprise Online|Consultez la rubrique [Planification de la connectivité hybride entre Skype Entreprise Server et Office 365](/skypeforbusiness/hybrid/plan-hybrid-connectivity).|Entrée hybride locale pour Skype Entreprise|
|15 |**Noms de domaine complets d’authentification et d’identité** <p> Le nom de domaine complet `secure.aadcdn.microsoftonline-p.com` doit apparaître dans la zone de sites Internet Explorer ou Edge approuvés de votre client pour fonctionner.||Sites de confiance|
|16|**Noms de domaine complets Microsoft Teams** <p> Si vous utilisez Internet Explorer ou Microsoft Edge, vous devez activer les cookies propriétaires et tiers, et ajouter les noms de domaine complets des équipes à vos sites de confiance. Cela s’ajoute aux noms de domaine complets, aux CDN et à la télémétrie répertoriés à la ligne 14. Reportez-vous à la rubrique [Problèmes connus pour Microsoft Teams](/microsoftteams/known-issues) pour plus d’informations.||Sites de confiance|
|17 |**Noms de domaine complets Sharepoint Online et OneDrive Entreprise** <p> Tous les noms de domaine complets « .sharepoint.com » comportant « \<tenant\> » doivent se trouver dans la zone de sites Internet Explorer ou Edge de confiance de votre client pour fonctionner. Outre les noms de domaine complets, les CDN et la télémétrie répertoriés à la ligne 14, vous devrez également ajouter ces points de terminaison.||Sites de confiance|
|18 |**Yammer**  <br> Yammer est uniquement disponible dans le navigateur et nécessite que l’utilisateur soit authentifié via un proxy. Tous les FQDN Yammer doivent se trouver dans la zone de sites Internet Explorer ou Edge de confiance de votre client pour fonctionner.||Sites de confiance|
|19|Utilisez **[Azure AD Connecter](/azure/active-directory/hybrid/)** pour synchroniser les comptes d’utilisateurs locaux avec Azure AD.|Consultez [Ports et protocoles nécessaires pour l’identité hybride](/azure/active-directory/hybrid/reference-connect-ports), [Résoudre les problèmes de connectivité Azure AD](/azure/active-directory/hybrid/tshoot-connect-connectivity) et [Installation de l’agent Azure AD Connect Health](/azure/active-directory/hybrid/how-to-connect-health-agent-install#outbound-connectivity-to-the-azure-service-endpoints).|Trafic serveur sortant uniquement|
|20|**[Azure AD Connecter](/azure/active-directory/hybrid/)** 21 ViaNet en Chine pour synchroniser les comptes d’utilisateurs locaux avec Azure AD.|\*.digicert.com:80 <BR> \*.entrust.net:80 <BR> \*. chinacloudapi.cn:443 <br> secure.aadcdn.partner.microsoftonline-p.cn:443 <br> \*.partner.microsoftonline.cn:443 <p> Pour plus d’informations, voir [Résoudre les problèmes de connectivité Azure AD](https://docs.azure.cn/zh-cn/active-directory/hybrid/tshoot-connect-connectivity).|Trafic serveur sortant uniquement|
| 21|**Microsoft Stream** (nécessite le jeton Azure AD’utilisateur). <br> Office 365 dans le monde (notamment GCC)|\**.cloudapp.net <br> \*api.microsoftstream.com <br> \**.notification.api.microsoftstream.com <br> amp.azure.net <br> api.microsoftstream.com <br> az416426.vo.msecnd.net <br> s0.assets-yammer.com <br> vortex.data.microsoft.com <br> web.microsoftstream.com <br> Port TCP 443.|Trafic serveur entrant|
|22|Utilisez **le serveur MFA** pour les demandes d’authentification multifacteur, à la fois les nouvelles installations du serveur et sa configuration avec les services de domaine Active Directory (AD DS).|Voir [La mise en Azure AD serveur d’authentification multifacteur](/azure/active-directory/authentication/howto-mfaserver-deploy#plan-your-deployment).|Trafic serveur sortant uniquement|
|23|**Notifications Graph modification microsoft** <p> Les développeurs peuvent utiliser [les notifications de modification](/graph/webhooks?context=graph%2fapi%2f1.0&view=graph-rest-1.0) pour s’abonner à des événements dans microsoft Graph.|Public Cloud: 52.159.23.209, 52.159.17.84, 52.147.213.251, 52.147.213.181, 13.85.192.59, 13.85.192.123, 13.89.108.233, 13.89.104.147, 20.96.21.67, 20.69.245.215, 137.135.11.161, 137.135.11.116, 52.159.107.50, 52.159.107.4, 52.229.38.131, 52.183.67.212, 52.142.114.29, 52.142.115.31, 51.124.75.43, 51.124.73.177, 20.44.210.83, 20.44.210.146, 40.80.232.177, 40.80.232.118, 20.48.12.75, 20.48.11.201, 104.215.13.23, 104.215.6.169, 52.148.24.136, 52.148.27.39, 40.76.162.99, 40.76.162.42 , 40.74.203.28, 40.74.203.27, 13.86.37.15, 52.154.246.238, 20.96.21.98, 20.96.21.115, 137.135.11.222, 137.135.11.250, 52.159.109.205, 52.159.102.72, 52.151.30.78, 52.191.173.85, 51.104.159.213, 51.104.159.181, 51.138.90.7, 51.138.90.52, 52.148.115.48, 52.148.114.238, 40.80.233.14, 40.80.239.196, 20.48.14.35, 20.48.15.147, 104.215.18.55, 104.215.12.254, 20.199.102.157, 20.199.102.73, 13.87.81.123, 13.87.81.35, 20.111.9.46, 20.111.9.77, 13.87.81.133, 13.87.81.141 <p> Microsoft Cloud for US Government : 52.244.33.45, 52.244.35.174, 52.243.157.104, 52.243.157.105, 52.182.25.254, 52.182.25.110, 52.181.25.67, 52.181.25.66, 52.244.111.156, 52.244.111.170, 52.243.147.249, 52.243.148.1 9, 52.182.32.51, 52.182.32.143, 52.181.24.199, 52.181.24.220 <p> Microsoft Cloud Chine géré par 21Vianet : 42.159.72.35, 42.159.72.47, 42.159.180.55, 42.159.180.56, 40.125.138.23, 40.125.136.69, 40.72.155.199, 40.72.155.216 <br> Port TCP 443. <p> Remarque : les développeurs peuvent spécifier des ports différents lors de la création des abonnements.|Trafic serveur entrant|
|24|**Indicateur d’état de la connexion réseau**<p>Utilisé par Windows 10 et 11 pour déterminer si l’ordinateur est connecté à Internet (ne s’applique pas aux clients non Windows client). Lorsque cette URL n’est pas accessible, Windows suppose qu’elle n’est pas connectée à Internet et que M365 Apps for Enterprise ne tente pas de vérifier l’état d’activation, ce qui entraîne l’échec des connexions à Exchange et à d’autres services.|www.mstfconnecttest.com <br> 13.107.4.52<p>Voir également [Gérer les points de terminaison de connexion pour Windows 11 Entreprise](/windows/privacy/manage-windows-11-endpoints) et Gérer les points de terminaison de connexion [pour Windows 10 Entreprise, version 21H2](/windows/privacy/manage-windows-21h2-endpoints).|Trafic serveur sortant uniquement|
|

## <a name="related-topics"></a>Rubriques connexes

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)
  
[Surveiller la connectivité Microsoft 365](./monitor-connectivity.md)
  
[Connectivité des clients](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Réseaux de distribution de contenu](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Plages IP azure et balises de service – Cloud public](https://www.microsoft.com/download/details.aspx?id=56519)

[Plages d’adresses IP azure et balises de service – Cloud pour le gouvernement des États-Unis](https://www.microsoft.com/download/details.aspx?id=57063)

[Plages IP Azure et balises de service – Cloud allemagne](https://www.microsoft.com/download/details.aspx?id=57064)

[Plages IP azure et balises de service : cloud chinois](https://www.microsoft.com/download/details.aspx?id=57062)
  
[Espace d’adresse IP public de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
