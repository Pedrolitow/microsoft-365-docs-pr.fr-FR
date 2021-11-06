---
title: Champs d’alerte Microsoft Defender pour point de terminaison
description: Comprendre comment les champs d’alerte sont maprés avec les valeurs dans Microsoft Defender pour point de terminaison
keywords: détections, champs de détections, champs, api, champs, pull Detections, api rest, demande, réponse
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 08a280130f7bd7566c0ef3998034998b5eff5ef6
ms.sourcegitcommit: e110f00dc6949a7a1345187375547beeb64225b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2021
ms.locfileid: "60804773"
---
# <a name="microsoft-defender-for-endpoint-alert-fields"></a>Champs d’alerte Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-apiportalmapping-abovefoldlink)

Comprendre les champs de données qui sont exposés dans le cadre de l’API de détections et la façon dont ils sont map Microsoft 365 Defender.

> [!NOTE]
>
> - [Defender for Endpoint Alert](alerts.md) se compose d’une ou de plusieurs détections.
> - **La détection Microsoft Defender ATP est** composée de l’événement suspect qui s’est produit sur l’appareil et de ses détails **d’alerte** associés.
> - L’API d’alerte microsoft Defender pour point de terminaison est la dernière API pour la consommation des alertes et contient une liste détaillée des preuves associées à chaque alerte. Pour plus d’informations, voir [Méthodes et propriétés d’alerte et](alerts.md) Liste des [alertes.](get-alerts.md)

## <a name="detections-api-fields-and-portal-mapping"></a>Champs API détections et mappage de portail

Le tableau suivant répertorie les champs disponibles exposés dans la charge utile de l’API de détections. Il présente des exemples pour les valeurs remplies et une référence sur la façon dont les données sont reflétées sur le portail.

La colonne de champ ArcSight contient le mappage par défaut entre les champs Defender pour point de terminaison et les champs intégrés dans ArcSight. Vous pouvez télécharger le fichier de mappage à partir du portail lorsque vous activez la fonctionnalité d’intégration SIEM et le modifier pour répondre aux besoins de votre organisation. Pour plus d’informations, voir [Enable SIEM integration in Defender for Endpoint](enable-siem-integration.md).

Les numéros de champ correspondent aux numéros dans les images ci-dessous.

> [!div class="mx-tableFixed"]
>
> |Étiquette de portail|Nom du champ SIEM|Champ ArcSight|Exemple de valeur|Description|
> |---|---|---|---|---|
> |1|AlertTitle|name|L’Antivirus Microsoft Defender a détecté un programme malveillant de gravité élevée|Valeur disponible pour chaque détection.|
> |2|Severity|deviceSeverity|Élevé|Valeur disponible pour chaque détection.|
> |3|Catégorie|deviceEventCategory|Programme malveillant|Valeur disponible pour chaque détection.|
> |4|Source de détection|sourceServiceName|Antivirus|Antivirus Microsoft Defender ou Defender pour le point de terminaison. Valeur disponible pour chaque détection.|
> |5|MachineName|sourceHostName|desktop-4a5ngd6|Valeur disponible pour chaque détection.|
> |6 |FileName|fileName|Robocopy.exe|Disponible pour les détections associées à un fichier ou un processus.|
> |7 |FilePath|filePath|C:\Windows\System32\Robocopy.exe|Disponible pour les détections associées à un fichier ou un processus.|
> |8 |UserDomain|sourceNtDomain|CONTOSO|Domaine du contexte utilisateur exécutant l’activité, disponible pour defender pour les détections basées sur le comportement des points de terminaison.|
> |9 |UserName|sourceUserName|liz.bean|Contexte utilisateur exécutant l’activité, disponible pour Defender pour les détections basées sur le comportement des points de terminaison.|
> |10|Sha1|fileHash|3da065e07b990034e9db7842167f70b63aa5329|Disponible pour les détections associées à un fichier ou un processus.|
> |11|Sha256|deviceCustomString6|ebf54f745dc81e1958f75e4ca91dd0ab989fc9787bb6b0bf993e2f5|Disponible pour les détections de Microsoft Defender AV.|
> |12 |Md5|deviceCustomString5|db979c04a99b96d370988325bb5a8b21|Disponible pour les détections de Microsoft Defender AV.|
> |13|ThreatName|deviceCustomString1|HackTool:Win32/Contrôletz!dha|Disponible pour les détections de Microsoft Defender AV.|
> |14 |IpAddress|sourceAddress|218.90.204.141|Disponible pour les détections associées aux événements réseau. Par exemple, « Communication vers une destination réseau malveillante ».|
> |15 |Url|requestUrl|down.esales360.cn|Disponible pour les détections associées aux événements réseau. Par exemple, « Communication vers une destination réseau malveillante ».|
> |16|RemediationIsSuccess|deviceCustomNumber2|TRUE|Disponible pour les détections de Microsoft Defender AV. La valeur ArcSight est 1 lorsque TRUE et 0 lorsque FALSE.|
> |17 |WasExecutingWhileDetected|deviceCustomNumber1|FALSE|Disponible pour les détections de Microsoft Defender AV. La valeur ArcSight est 1 lorsque TRUE et 0 lorsque FALSE.|
> |18 |AlertId|externalId|636210704265059241_673569822|Valeur disponible pour chaque détection.|
> |19|LinkToWDATP|flexString1|`https://securitycenter.windows.com/alert/636210704265059241_673569822`|Valeur disponible pour chaque détection.|
> |20|AlertTime|deviceReceiptTime|2017-05-07T01:56:59.3191352Z|Heure à l’heure où l’événement s’est produit. Valeur disponible pour chaque détection.|
> | 21|MachineDomain|sourceDnsDomain|contoso.com|Nom de domaine non pertinent pour les AAD joints. Valeur disponible pour chaque détection.|
> |22|Actor|deviceCustomString4|BORON|Disponible pour les alertes relatives à un groupe d’acteurs connus.|
> |21+5|ComputerDnsName|Aucun mappage|liz-bean.contoso.com|Nom de domaine complet de l’appareil. Valeur disponible pour chaque détection.|
> ||LogOnUsers|sourceUserId|contoso\liz-bean; contoso\ge-hardee|Le domaine et l’utilisateur des utilisateurs d’une logon interactive au moment de l’événement. Remarque : pour les appareils Windows 10 version 1607, les informations de domaine ne seront pas disponibles.|
> ||InternalIPv4List|Aucun mappage|192.168.1.7, 10.1.14.1|Liste des IPS internes IPV4 pour les interfaces réseau actives.|
> ||InternalIPv6List|Aucun mappage|fd30:0000:0000:0001:ff4e:003e:0009:000e, FE80:CD00:0000:0CDE:1257:0000:211E:729C|Liste des IPS internes IPV6 pour les interfaces réseau actives.|
> ||LinkToMTP|Aucun mappage|`https://securitycenter.windows.com/alert/da637370718981685665_16349121`|Valeur disponible pour chaque détection.
> ||IncidentLinkToMTP|Aucun mappage|`"https://securitycenter.windows.com/incidents/byalert?alertId=da637370718981685665_16349121&source=SIEM`|Valeur disponible pour chaque détection.
> ||IncidentLinkToWDATP|Aucun mappage|`https://securitycenter.windows.com/preferences2/integration/incidents/byalert?alertId=da637370718981685665_16349121&source=SIEM`|Valeur disponible pour chaque détection.
> |Champ interne|LastProcessedTimeUtc|Aucun mappage|2017-05-07T01:56:58.9936648Z|Heure à quel moment l’événement est arrivé au niveau du back-end. Ce champ peut être utilisé lors de la définition du paramètre de demande pour la période de récupération des détections.|
> ||Ne fait pas partie du schéma|deviceVendor||Valeur statique dans le mappage ArcSight : « Microsoft ».|
> ||Ne fait pas partie du schéma|deviceProduct||Valeur statique dans le mappage ArcSight : « Microsoft Defender ATP ».|
> ||Ne fait pas partie du schéma|deviceVersion||Valeur statique dans le mappage ArcSight - « 2.0 » utilisé pour identifier les versions de mappage.|

:::image type="content" alt-text="Image de l’alerte avec des nombres." source="images/atp-alert-page.png" lightbox="images/atp-alert-page.png":::

:::image type="content" alt-text="Image du volet d’informations de l’alerte avec des nombres." source="images/atp-siem-mapping13.png":::

:::image type="content" alt-text="Image de la chronologie de l’artefact avec numbers1." source="images/atp-siem-mapping3.png" lightbox="images/atp-siem-mapping3.png":::

:::image type="content" alt-text="Image de la chronologie de l’artefact avec numbers2." source="images/atp-siem-mapping4.png" lightbox="images/atp-siem-mapping4.png":::

:::image type="content" alt-text="Image de l’ordinateur." source="images/atp-mapping6.png" lightbox="images/atp-mapping6.png":::

:::image type="content" alt-text="URL du navigateur d’image." source="images/atp-mapping5.png" lightbox="images/atp-mapping5.png":::

:::image type="content" alt-text="Alerte d’acteur d’image." source="images/atp-mapping7.png" lightbox="images/atp-mapping7.png":::

## <a name="related-topics"></a>Rubriques connexes

- [Activer l’intégration SIEM dans Microsoft Defender pour le point de terminaison](enable-siem-integration.md)
- [Configurer ArcSight pour tirer Microsoft Defender pour les détections de points de terminaison](configure-arcsight.md)
- [Détecter Microsoft Defender pour les points de terminaison à l’aide de l’API REST](pull-alerts-using-rest-api.md)
- [Résoudre des problèmes d’intégration de l’outil SIEM](troubleshoot-siem.md)
