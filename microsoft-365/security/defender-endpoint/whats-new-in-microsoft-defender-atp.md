---
title: Nouveautés dans Microsoft Defender pour point de terminaison
description: Découvrez les fonctionnalités généralement disponibles dans la dernière version de Microsoft Defender pour Endpoint, ainsi que les fonctionnalités de sécurité dans Windows 10 et Windows Server.
keywords: nouveautés de Microsoft Defender pour point de terminaison, ga, généralement disponibles, fonctionnalités, disponibles, nouvelles
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 33bd21cb338d5c792e6241ac61f75712ecc1ad45
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53656066"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint"></a>Nouveautés dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Les fonctionnalités suivantes sont généralement disponibles dans la dernière version de Microsoft Defender pour Endpoint, ainsi que les fonctionnalités de sécurité dans Windows 10 et Windows Server.

Pour plus d’informations sur les fonctionnalités d’aperçu, voir [fonctionnalités d’aperçu.](preview.md)


> [!TIP]
> Flux RSS : recevez une notification lorsque cette page est mise à jour en copiant et en coller l’URL suivante dans votre lecteur de flux :
>
> ```https
> /api/search/rss?search=%22features+are+generally+available+%28GA%29+in+the+latest+release+of+Microsoft+Defender+for+Endpoint%22&locale=en-us&facet=
> ```

## <a name="june-2021"></a>Juin 2021

- [Évaluation des vulnérabilités logicielles d’exportation delta](get-assessment-methods-properties.md#31-methods) API <br> Ajout de la collection d’API Exporter les évaluations des vulnérabilités et des [configurations sécurisées.](get-assessment-methods-properties.md) <br> Contrairement à l’évaluation complète des vulnérabilités logicielles (réponse JSON), qui permet d’obtenir un instantané complet de l’évaluation des vulnérabilités logicielles de votre organisation par appareil, l’appel de l’API d’exportation delta est utilisé pour récupérer uniquement les modifications qui se sont produites entre une date sélectionnée et la date actuelle (l’appel d’API « delta »). Au lieu d’obtenir une exportation complète avec une grande quantité de données à chaque fois, vous obtenez uniquement des informations spécifiques sur les vulnérabilités nouvelles, fixes et mises à jour. L’appel d’API d’exportation delta peut également être utilisé pour calculer différents KPI, tels que « combien de vulnérabilités ont été corrigées » ou « combien de nouvelles vulnérabilités ont été ajoutées à une organisation ».

- [Exporter les évaluations des vulnérabilités et des configurations sécurisées](get-assessment-methods-properties.md) API <br> Ajoute une collection d’API qui Gestion des menaces et des vulnérabilités données par appareil. Il existe différents appels d’API pour obtenir différents types de données : évaluation de la configuration sécurisée, évaluation de l’inventaire logiciel et évaluation des vulnérabilités logicielles. Chaque appel d’API contient les données requises pour les appareils de votre organisation.

- [Activité de correction](get-remediation-methods-properties.md) API <br>  Ajoute une collection d’API avec des réponses qui contiennent des Gestion des menaces et des vulnérabilités de correction qui ont été créées dans votre client. Les types d’informations de réponse incluent une activité de correction par ID, toutes les activités de correction et les périphériques exposés d’une activité de correction.

- [Découverte d’appareils](device-discovery.md) <br> Vous permet de trouver des appareils non utilisés connectés à votre réseau d’entreprise sans avoir besoin d’appliances supplémentaires ou de modifications de processus fastidieuses. À l’aide d’appareils intégrés, vous pouvez rechercher des appareils non utilisés dans votre réseau et évaluer les vulnérabilités et les risques. Vous pouvez ensuite intégrer des appareils découverts afin de réduire les risques associés à l’affichage de points de terminaison non pris en compte dans votre réseau.

   > [!IMPORTANT]
   > La découverte standard sera le mode par défaut pour tous les clients à partir du 19 juillet 2021. Vous pouvez choisir de conserver le mode de base via la page paramètres.

- [Les définitions de groupe d’appareils](/microsoft-365/security/defender-endpoint/machine-groups) peuvent désormais inclure plusieurs valeurs pour chaque condition. Vous pouvez définir plusieurs balises, noms d’appareils et domaines sur la définition d’un seul groupe d’appareils.

## <a name="march-2021"></a>Mars 2021
- [Gérer la protection contre les falsifications à l’aide Centre de sécurité Microsoft Defender](prevent-changes-to-security-settings-with-tamper-protection.md#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal) <br> Vous pouvez gérer les paramètres de protection contre la falsification sur Windows 10, Windows Server 2016 et Windows Server 2019 à l’aide d’une méthode appelée *attachement client.*


## <a name="january-2021"></a>Janvier 2021

- [Windows Virtual Desktop](https://azure.microsoft.com/services/virtual-desktop/) <br> Microsoft Defender for Endpoint ajoute désormais la prise en charge Windows Virtual Desktop.

## <a name="december-2020"></a>Décembre 2020

- [Microsoft Defender pour point de terminaison iOS](microsoft-defender-endpoint-ios.md) <br> Microsoft Defender pour le point de terminaison ajoute désormais la prise en charge d’iOS. Découvrez comment installer, configurer, mettre à jour et utiliser Microsoft Defender pour Endpoint sur iOS.

## <a name="september-2020"></a>Septembre 2020

- [Microsoft Defender pour point de terminaison Android](microsoft-defender-endpoint-android.md) <br> Microsoft Defender pour le point de terminaison ajoute désormais la prise en charge d’Android. Découvrez comment installer, configurer, mettre à jour et utiliser Microsoft Defender pour Endpoint sur Android.
- [Prise en charge des menaces gestion des vulnérabilités macOS](tvm-supported-os.md)<br> Threat and gestion des vulnérabilités for macOS is now in public preview, and will continuously detect vulnerabilities on your macOS devices to help you prioritize remediation by focusing on risk. En savoir plus sur ce [billet de blog Microsoft Tech Community.](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-for-endpoint-adds-depth-and-breadth-to-threat/ba-p/1695824)

## <a name="august-2020"></a>Août 2020

- [Microsoft Defender pour point de terminaison Android](microsoft-defender-endpoint-android.md) <br> Microsoft Defender pour le point de terminaison ajoute désormais la prise en charge d’Android. Découvrez comment installer, configurer et utiliser Microsoft Defender pour Endpoint sur Android.

## <a name="july-2020"></a>Juillet 2020

- [Créer des indicateurs pour les certificats](manage-indicators.md) <br> Créez des indicateurs pour autoriser ou bloquer les certificats.

## <a name="june-2020"></a>Juin 2020

- [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md) <br> Microsoft Defender pour le point de terminaison ajoute désormais la prise en charge de Linux. Découvrez comment installer, configurer, mettre à jour et utiliser Microsoft Defender pour Endpoint sur Linux.

- [Simulateurs d’attaques dans le laboratoire d’évaluation](evaluation-lab.md#threat-simulator-scenarios) <br> Microsoft Defender pour le point de terminaison s’est associé à différentes plateformes de simulation de menaces pour vous donner un accès pratique pour tester les fonctionnalités de la plateforme directement à partir du portail.

## <a name="april-2020"></a>Avril 2020

- [Prise en charge de l& API de gestion des menaces et des vulnérabilités](exposed-apis-list.md) <BR>Exécutez des appels d’API liés à la gestion des menaces et des vulnérabilités, tels que le score d’exposition aux menaces de votre organisation ou le score de sécurité de l’appareil, l’inventaire des vulnérabilités des logiciels et des appareils, la distribution des versions des logiciels, les informations sur les vulnérabilités des appareils, les informations de recommandation de sécurité. & En savoir plus sur ce [billet de blog Microsoft Tech Community.](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/threat-amp-vulnerability-management-apis-are-now-generally/ba-p/1304615)

## <a name="november-december-2019"></a>November-December 2019

- [Microsoft Defender pour point de terminaison macOS](microsoft-defender-endpoint-mac.md) <BR> Microsoft Defender pour le point de terminaison sur macOS apporte la protection nouvelle génération aux appareils Mac. Les principaux composants de la plateforme de sécurité de point de terminaison unifiée seront désormais disponibles pour les appareils Mac, y compris [protection évolutive des points de terminaison](microsoft-defender-endpoint-mac.md).

- [Informations de fin de vie & l’application de gestion des vulnérabilités et de la version de l’application](tvm-security-recommendation.md) <BR>Les applications et les versions d’applications qui ont atteint leur fin de vie sont marquées ou étiquetées en tant que telles. Vous savez donc qu’elles ne seront plus prises en charge et qu’elles peuvent prendre des mesures pour désinstaller ou remplacer. Cela permet de réduire les risques liés à diverses expositions de vulnérabilités dues à des applications non associées.

- [Schémas de & de recherche avancée de gestion des menaces et des vulnérabilités](advanced-hunting-schema-reference.md) <BR>Utilisez les tables gestion des menaces & des vulnérabilités dans le schéma de recherche avancé pour interroger sur l’inventaire logiciel, la base de connaissances sur les vulnérabilités, l’évaluation de la configuration de la sécurité et la base de connaissances sur la configuration de la sécurité.

 - [Contrôles d’accès basés sur les rôles de gestion des & des menaces](user-roles.md#create-roles-and-assign-the-role-to-an-azure-active-directory-group) <BR>Utilisez les nouvelles autorisations pour permettre une flexibilité maximale pour créer des rôles orientés SecOps, des rôles orientés gestion des vulnérabilités de & menaces ou des rôles hybrides afin que seuls les utilisateurs autorisés accèdent à des données spécifiques pour accomplir leur tâche. Vous pouvez également atteindre une granularité encore plus grande en spécifiant si un rôle gestion des menaces & des vulnérabilités peut uniquement afficher les données liées aux vulnérabilités, ou créer et gérer des corrections et des exceptions.

- [Rapport d’intégrité et de conformité des appareils](machine-reports.md) <br/> Le rapport sur l’état et la conformité de l’appareil fournit des informations de haut niveau sur les appareils de votre organisation.

## <a name="october-2019"></a>Octobre 2019

- [Indicateurs pour les adresses IP, url/domaines](manage-indicators.md) <BR> Vous pouvez désormais autoriser ou bloquer des URL/domaines à l’aide de votre propre intelligence des menaces.

- [Spécialistes des menaces Microsoft - Experts à la demande](microsoft-threat-experts.md) <BR> Vous avez maintenant la possibilité de consulter les Spécialistes des menaces Microsoft à partir de plusieurs endroits dans le portail pour vous aider dans le cadre de votre enquête.

- [Applications Azure AD connectées](connected-applications.md)<br> La page Applications connectées fournit des informations sur les applications Azure AD connectées à Microsoft Defender pour endpoint dans votre organisation.

- [Explorateur d’API](api-explorer.md)<br> L’Explorateur d’API facilite la construction et l’application de requêtes API, teste et envoie des demandes pour tout point de terminaison de l’API Microsoft Defender pour endpoint disponible.

## <a name="september-2019"></a>Septembre 2019

- [Paramètres de protection contre la falsification à l’aide d’Intune](prevent-changes-to-security-settings-with-tamper-protection.md) <br/> Vous pouvez désormais activer (ou désactiver) la protection contre les falsifications pour votre organisation dans le Microsoft 365 Device Management Portal (Intune).

- [Réponse en direct](live-response.md) <BR> Obtenir un accès instantané à un appareil à l’aide d’une connexion Shell distante. Faire des investigations approfondies et prendre des mesures de réponse immédiates pour contenir rapidement les menaces identifiées ( en temps réel).

- [Laboratoire d’évaluation](evaluation-lab.md) <BR> Le laboratoire d’évaluation de Microsoft Defender pour points de terminaison est conçu pour éliminer la complexité de la configuration des appareils et de l’environnement afin de pouvoir vous concentrer sur l’évaluation des fonctionnalités de la plateforme, l’exécution de simulations et l’utilisation des fonctionnalités de prévention, de détection et de correction.

- [Windows Server 2008 R2 SP1](configure-server-endpoints.md) <BR> Vous pouvez désormais intégrer Windows Server 2008 R2 SP1.

## <a name="june-2019"></a>Juin 2019

- [Gestion des & des menaces](next-gen-threat-and-vuln-mgt.md) <BR> Nouvelle fonctionnalité intégrée qui utilise une approche basée sur les risques pour la découverte, la hiér doncisation et la correction des vulnérabilités et des mauvaises configurations des points de terminaison.

- [Rapport sur l’état et la conformité de l’appareil](machine-reports.md)  Le rapport sur l’état et la conformité de l’appareil fournit des informations de haut niveau sur les appareils de votre organisation.

## <a name="may-2019"></a>Mai 2019

- [Rapports de protection contre les menaces](threat-protection-reports.md)<BR>Le rapport sur la protection contre les menaces fournit des informations de haut niveau sur les alertes générées dans votre organisation.

- [Spécialistes des menaces Microsoft](microsoft-threat-experts.md)<BR> Spécialistes des menaces Microsoft est le nouveau service de recherche de menace gérée dans Microsoft Defender pour point de terminaison qui fournit une recherche proactive, la hiérquage, ainsi que des informations et un contexte supplémentaires qui permettent aux centres d’opérations de sécurité (SOC) d’identifier et de répondre aux menaces rapidement et avec précision. Il fournit une couche supplémentaire d’expertise et d’optique que les clients Microsoft peuvent utiliser pour renforcer les fonctionnalités d’opérations de sécurité dans le cadre Microsoft 365.

- [Indicateurs](ti-indicator.md) <BR> Les API pour les indicateurs sont désormais généralement disponibles.

- [Interopérabilité](partner-applications.md) <BR> Microsoft Defender pour endpoint prend en charge des applications tierces pour améliorer les fonctionnalités de détection, d’examen et d’intelligence contre les menaces de la plateforme.

## <a name="april-2019"></a>Avril 2019

- [Spécialistes des menaces Microsoft Fonctionnalité de notification d’attaque ciblée](microsoft-threat-experts.md) <BR> Les alertes de notification d’attaque ciblée d’Spécialistes des menaces Microsoft sont adaptées aux organisations pour fournir autant d’informations que possible rapidement, ce qui a pour effet d’attirer l’attention sur les menaces critiques sur leur réseau, notamment la chronologie, l’étendue de la violation et les méthodes d’intrusion.

- [API Microsoft Defender pour point de terminaison](apis-intro.md) <BR> Microsoft Defender pour point de terminaison expose la plupart de ses données et actions par le biais d’un ensemble d’API de programmation. Ces API vous permettront d’automatiser les flux de travail et d’innover en fonction des fonctionnalités de Microsoft Defender for Endpoint.

## <a name="february-2019"></a>Février 2019

- [Incidents](view-incidents-queue.md) <BR> L’incident est une nouvelle entité dans Microsoft Defender pour point de terminaison qui regroupe toutes les alertes pertinentes et les entités associées pour mettre en avant l’ensemble des attaques, offrant ainsi aux analystes une meilleure perspective sur le point de vue des menaces complexes.

- [Intégrer des versions antérieures de Windows](onboard-downlevel.md)<BR> Intégrer des versions de Windows afin qu’ils peuvent envoyer des données de capteur au capteur Microsoft Defender for Endpoint.

## <a name="october-2018"></a>Octobre 2018

- [Règles de réduction de la surface d’attaque](attack-surface-reduction.md)<BR>Toutes les règles de réduction de la surface d’attaque sont désormais Windows Server 2019.

- [Accès contrôlé aux dossiers](enable-controlled-folders.md)<BR> L’accès contrôlé aux dossiers est désormais pris en charge Windows Server 2019.

- [Détection personnalisée](manage-indicators.md)<BR>Avec les détections personnalisées, vous pouvez créer des requêtes personnalisées pour surveiller les événements pour tout type de comportement, comme les menaces suspectes ou émergentes. Pour ce faire, vous pouvez tirer parti de la puissance du repérage avancé via la création de règles de détection personnalisées.

- [Intégration à Azure Defender](configure-server-endpoints.md)<BR> Microsoft Defender pour point de terminaison s’intègre à Azure Defender pour fournir une solution de protection serveur complète. Avec cette intégration, Azure Defender peut tirer parti de la puissance de Microsoft Defender for Endpoint pour fournir une détection améliorée des menaces pour Windows serveurs.

- [Prise en charge du fournisseur de services de sécurité géré (MSSP)](mssp-support.md)<BR> Microsoft Defender pour le point de terminaison ajoute la prise en charge de ce scénario en fournissant l’intégration MSSP. L’intégration permettra aux MSSP d’agir comme suit : accéder au portail Centre de sécurité Microsoft Defender du client MSSP, récupérer des notifications par courrier électronique et récupérer des alertes via les outils de gestion des événements et des informations de sécurité (SIEM).

- [Contrôle d’appareil amovible](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/19/windows-defender-atp-has-protections-for-usb-and-removable-devices/)<BR>Microsoft Defender pour le point de terminaison fournit plusieurs fonctionnalités de surveillance et de contrôle pour éviter les menaces provenant d’appareils amovibles, notamment de nouveaux paramètres permettant d’autoriser ou de bloquer des ID matériels spécifiques.

- [Prise en charge des appareils iOS et Android](configure-endpoints-non-windows.md)<BR> Les appareils iOS et Android sont désormais pris en charge et peuvent être intégrés au service.

- [Analyses de menaces](threat-analytics.md)<BR>
L’analyse des menaces est un ensemble de rapports interactifs publiés par l’équipe de recherche de Microsoft Defender for Endpoint dès que des menaces émergentes et des épidémies sont identifiées. Les rapports aident les équipes en matière d’opérations de sécurité à évaluer l’impact sur leur environnement et fournissent des actions recommandées pour contenir, renforcer la résilience de l’organisation et éviter les menaces spécifiques.

- Nouveauté de Windows 10 version 1809, il existe deux nouvelles règles de réduction de la surface d’attaque :
  - Empêcher Adobe Reader de créer des processus enfants
  - Empêcher Office application de communication de créer des processus enfants.

- [Antivirus Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md)
  - L’interface AMSI (Antimalware Scan Interface) a été étendue pour couvrir Office macros VBA. [Office VBA + AMSI : la part de la partie sur les macros malveillantes](https://cloudblogs.microsoft.com/microsoftsecure/2018/09/12/office-vba-amsi-parting-the-veil-on-malicious-macros/).
  - Antivirus Microsoft Defender, nouveauté de Windows 10 version 1809, peut désormais s’exécuter dans un [bac](https://www.microsoft.com/security/blog/2018/10/26/windows-defender-antivirus-can-now-run-in-a-sandbox) à sable (prévisualisation), ce qui augmente sa sécurité.
  - [Configurez les paramètres de priorité du](configure-advanced-scan-types-microsoft-defender-antivirus.md) processeur pour Antivirus Microsoft Defender analyses.

## <a name="march-2018"></a>Mars 2018

- [Repérage avancé](advanced-hunting-overview.md)

   Interroger des données à l’aide d’une recherche avancée dans Microsoft Defender pour point de terminaison.

- [Règles de réduction de la surface d’attaque](/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard)

  Nouvelles règles de réduction de la surface d’attaque :

  - Utiliser la protection avancée contre les ransomware
  - Bloquer le vol d’informations d’identification Windows sous-système d’autorité de sécurité locale (lsass.exe)
  - Bloquer les créations de processus provenant de commandes PSExec et WMI
  - Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB
  - Bloquer le contenu exécutable du client de messagerie et de la messagerie web

- [Examen et correction automatisés](automated-investigations.md)<BR> Utiliser des enquêtes automatisées pour examiner et corriger les menaces.

    > [!NOTE]
    > Disponible à partir Windows 10 version 1803 ou ultérieure.

- [Accès conditionnel](conditional-access.md) <br> Activez l’accès conditionnel pour mieux protéger les utilisateurs, les appareils et les données.

- [Centre de Community Microsoft Defender pour Community terminaison](community.md)<BR>
    Le Centre d’administration Microsoft Defender pour Community est un endroit où les membres de la communauté peuvent découvrir, collaborer et partager des expériences sur le produit.

- [Accès contrôlé aux dossiers](enable-controlled-folders.md)<BR>
Vous pouvez désormais empêcher les processus nontrus d’écrire dans les secteurs de disque à l’aide de l’accès contrôlé aux dossiers.

- [Intégrer des appareils non Windows](configure-endpoints-non-windows.md)<BR>
    Microsoft Defender pour point de terminaison offre une expérience d’opérations de sécurité centralisée pour les Windows et les plateformes non Windows web. Vous pourrez voir les alertes de différents systèmes d’exploitation pris en charge dans Centre de sécurité Microsoft Defender et mieux protéger le réseau de votre organisation.

- [Contrôle d’accès basé sur un rôle (RBAC)](rbac.md)<BR>
    À l’aide du contrôle d’accès basé sur un rôle (RBAC), vous pouvez créer des rôles et des groupes au sein de votre équipe des opérations de sécurité pour accorder un accès approprié au portail.


- [Antivirus Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md)<BR>
Antivirus Microsoft Defender partage désormais l’état de détection entre Microsoft 365 services et interaérette avec Microsoft Defender pour Endpoint. Pour plus d’informations, voir Utiliser les technologies de nouvelle génération dans Antivirus Microsoft Defender via la [protection cloud.](cloud-protection-microsoft-defender-antivirus.md)

    Bloquer à la première vue peut désormais bloquer les fichiers exécutables non portables (tels que JS, VBS ou macros) ainsi que les fichiers exécutables. Pour plus d’informations, voir [Activer bloquer à la première vue.](configure-block-at-first-sight-microsoft-defender-antivirus.md)
