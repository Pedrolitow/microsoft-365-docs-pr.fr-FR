<!--THIS FILE IS AUTOMATICALLY GENERATED. MANUAL CHANGES WILL BE OVERWRITTEN.-->
<!--Please contact the Office 365 Endpoints team with any questions.-->
<!--Germany endpoints version 2021102900-->
<!--File generated 2021-10-30 08:00:07.4646-->

## <a name="exchange-online"></a>Exchange Online

ID | Catégorie | ER | Adresses | Ports
-- | -------------------- | -- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------
1 | Optimiser<BR>Obligatoire | Non | `outlook.office.de`<BR>`51.4.64.0/23, 51.5.64.0/23` | **TCP :** 443, 80
3 | Par défaut<BR>Obligatoire | Non | `outlook.office.de` | **TCP :** 143, 25, 587, 993, 995
4  | Par défaut<BR>Obligatoire | Non | `attachments.office365-net.de, autodiscover-s.outlook.de` | **TCP :** 443, 80
5 | Autoriser<BR>Obligatoire | Non | `*.protection.outlook.de`<BR>`51.4.72.0/24, 51.4.80.0/27, 51.5.72.0/24, 51.5.80.0/27, 2a01:4180:4050:400::/64, 2a01:4180:4050:800::/64, 2a01:4180:4051:400::/64, 2a01:4180:4051:800::/64` | **TCP :** 25, 443

## <a name="sharepoint-online-and-onedrive-for-business"></a>Sharepoint Online et OneDrive Entreprise

ID | Catégorie | ER | Adresses | Ports
-- | -------------------- | -- | ------------------------------------------------------------------------------ | ----------------
8  | Optimiser<BR>Obligatoire | Non | `<tenant>.sharepoint.de`<BR>`51.4.66.0/23, 51.5.66.0/23, 2a01:4180:4030::/44` | **TCP :** 443, 80
10 | Par défaut<BR>Obligatoire | Non | `*.wns.windows.com` | **TCP :** 443, 80
11 | Par défaut<BR>Obligatoire | Non | `officeapps.live.com` | **TCP :** 443, 80
12  | Par défaut<BR>Obligatoire | Non | `spoprod-a.akamaihd.net, static.sharepointonline.com` | **TCP :** 443, 80
13 | Par défaut<BR>Obligatoire | Non | `*.search.production.de.azuretrafficmanager.de` | **TCP :** 443
14  | Par défaut<BR>Obligatoire | Non | `officeclient.microsoft.com` | **TCP :** 443, 80
15  | Par défaut<BR>Obligatoire | Non | `mobile.pipe.aria.microsoft.com, ssw.live.com, watson.telemetry.microsoft.com` | **TCP :** 443, 80
16 | Par défaut<BR>Obligatoire | Non | `oneclient.sfx.ms` | **TCP :** 443, 80
17  | Par défaut<BR>Obligatoire | Non | `*.svc.ms` | **TCP :** 443, 80

## <a name="skype-for-business-online-and-microsoft-teams"></a>Skype Entreprise Online et Microsoft Teams

ID | Catégorie | ER | Adresses | Ports
-- | -------------------- | -- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------
6  | Optimiser<BR>Obligatoire | Non | `*.germeetings.skype.de, *.infra.skype.de, *.online.skype.de, *.resources.skype.de`<BR>`51.4.68.0/26, 51.4.68.128/25, 51.5.69.0/26, 51.5.69.128/25, 2a01:4180:4040:1::/64, 2a01:4180:4040:2::/64, 2a01:4180:4040:7::/64, 2a01:4180:4040:8::/64` | **TCP :** 443, 80<BR>**UDP :** 3478
7  | Par défaut<BR>Obligatoire | Non | `*.germeetings.skype.de, *.infra.skype.de, *.online.skype.de, *.resources.skype.de` | **TCP :** 5061, 50000-59999<BR>**UDP :** 50000-59999

## <a name="microsoft-365-common-and-office-online"></a>Services communs Microsoft 365 et Office Online

ID | Catégorie | ER | Adresses | Ports
-- | ------------------- | -- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------
18  | Autoriser<BR>Obligatoire | Non | `*.online.office.de`<BR>`51.4.144.200/32, 51.5.149.3/32, 51.18.16.0/23` | **TCP :** 443
19 | Par défaut<BR>Obligatoire | Non | `*.cdn.office.net` | **TCP :** 443
20 | Autoriser<BR>Obligatoire | Non | `adminwebservice.microsoftonline.de, becws.microsoftonline.de, companymanager.microsoftonline.de, device.login.microsoftonline.de, directoryprovisioning.cloudapi.de, graph.cloudapi.de, graph.microsoft.de, login.microsoftonline.de, logincert.microsoftonline.de, pas.cloudapi.de, passwordreset.activedirectory.microsoftazure.de, provisioningapi.microsoftonline.de, syncservice.microsoftonline.de`<BR>`51.4.2.10/32, 51.4.71.61/32, 51.4.136.38/31, 51.4.136.40/31, 51.4.136.42/32, 51.4.146.38/32, 51.4.146.206/32, 51.5.16.7/32, 51.5.71.22/32, 51.5.136.32/30, 51.5.136.36/32, 51.5.145.29/32, 51.5.145.122/32` | **TCP :** 443, 80
22 | Par défaut<BR>Obligatoire | Non | `*.msauth.net, *.msauthimages.de, *.msftauth.net, *.msftauthimages.de, secure.aadcdn.microsoftonline-p.com, secure.aadcdn.microsoftonline-p.de` | **TCP :** 443, 80
25 | Par défaut<BR>Obligatoire | Non | `*.de.msods.nsatc.net, *.office.de.akadns.net, *.windows.de.nsatc.net, officehome.msocdn.de, shellprod.msocdn.com` | **TCP :** 443, 80
26 | Par défaut<BR>Obligatoire | Non | `*.d-trust.net` | **TCP :** 443, 80
27 | Autoriser<BR>Obligatoire | Non | `*.onmicrosoft.de, *.osi.office.de, office.de, portal.office.de, www.office.de`<BR>`51.4.70.0/24, 51.4.71.0/24, 51.4.226.115/32, 51.4.227.178/32, 51.4.230.178/32, 51.5.70.0/24, 51.5.71.0/24, 51.5.147.48/32, 51.5.242.163/32, 51.5.245.67/32, 2a01:4180:2001::2/128, 2a01:4180:2001::92/128, 2a01:4180:2001::234/128, 2a01:4180:2001::3b8/128, 2a01:4180:2401::5/128, 2a01:4180:2401::11f/128, 2a01:4180:2401::33b/128, 2a01:4180:2401::55b/128` | **TCP :** 443, 80
28 | Par défaut<BR>Obligatoire | Non | `*.cloudfront.net, prod.msocdn.de, r1.res.office365.com, shellprod.msocdn.de` | **TCP :** 443, 80
29 | Autoriser<BR>Obligatoire | Non | `excelcs.osi.office.de, excelps.osi.office.de, ols.osi.office.de, omexdiagnostics.osi.office.de, pptcs.osi.office.de, pptps.osi.office.de, wordcs.osi.office.de, wordps.osi.office.de`<BR>`51.4.144.41/32, 51.4.144.174/32, 51.4.145.38/32, 51.4.147.81/32, 51.4.147.233/32, 51.4.148.12/32, 51.4.150.145/32, 51.5.147.242/32, 51.5.149.100/32, 51.5.149.119/32, 51.5.149.123/32, 51.5.149.180/32, 51.5.149.186/32, 51.18.0.0/21` | **TCP :** 443, 80
30 | Par défaut<BR>Obligatoire | Non | `sharepoint.de` | **TCP :** 443, 80
31 | Par défaut<BR>Obligatoire | Non | `o15.officeredir.microsoft.com, odc.officeapps.live.com, odcsm.officeapps.live.com, office.microsoft.com, office15client.microsoft.com, officeimg.vo.msecnd.net, roaming.officeapps.live.com` | **TCP :** 443, 80
33 | Par défaut<BR>Obligatoire | Non | `res.delve.office.com` | **TCP :** 443
34 | Par défaut<BR>Obligatoire | Non | `lpcres.delve.office.com` | **TCP :** 443
35 | Par défaut<BR>Obligatoire | Non | `*.office.de` | **TCP :** 443, 80
