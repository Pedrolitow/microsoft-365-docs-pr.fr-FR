---
title: Vue d’ensemble de Microsoft Defender pour point de terminaison Plan 1
description: Obtenez une vue d’ensemble de Defender pour point de terminaison Plan 1. Découvrez les fonctionnalités et fonctionnalités incluses dans cet abonnement Endpoint Protection.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.service: microsoft-365-security
ms.subservice: mde
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection:
- m365-security
- tier1
ms.custom: intro-overview
ms.openlocfilehash: 82d6c29609c3c1d2ef6d9c908901ecf4f762606a
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68193144"
---
# <a name="overview-of-microsoft-defender-for-endpoint-plan-1"></a>Vue d’ensemble de Microsoft Defender pour point de terminaison Plan 1

**S’applique à**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender pour point de terminaison est une plateforme de sécurité de point de terminaison d’entreprise conçue pour aider des organisations comme la vôtre à prévenir, détecter, examiner et répondre aux menaces avancées. Nous sommes heureux d’annoncer que Defender pour point de terminaison est désormais disponible dans deux plans : 

- **Defender pour point de terminaison Plan 1**, décrit dans cet article ; Et 
- **[Defender pour point de terminaison Plan 2](microsoft-defender-endpoint.md)**, généralement disponible et anciennement appelé [Defender pour point de terminaison](microsoft-defender-endpoint.md).

Les zones vertes de l’image suivante illustrent ce qui est inclus dans Defender pour point de terminaison Plan 1 :

:::image type="content" source="../../media/mde-p1/mde-p1-overview-diagram.png" alt-text="Éléments inculqués avec Defender pour point de terminaison Plan 1" lightbox="../../media/mde-p1/mde-p1-overview-diagram.png":::

Utilisez ce guide pour :

- [Obtenir une vue d’ensemble de ce qui est inclus dans Defender pour point de terminaison Plan 1](#defender-for-endpoint-plan-1-capabilities)
- [Comparer Defender for Endpoint Plan 1 à Plan 2](defender-endpoint-plan-1-2.md)
- [Découvrez comment configurer Defender pour point de terminaison Plan 1](mde-p1-setup-configuration.md)
- [Commencez à utiliser le portail Microsoft 365 Defender, où vous pouvez afficher les incidents et les alertes, gérer les appareils et utiliser des rapports sur les menaces détectées](mde-plan1-getting-started.md)
- [Obtenir une vue d’ensemble de la maintenance et des opérations](mde-p1-maintenance-operations.md)

> [!TIP]
> [En savoir plus sur les différences entre Defender pour point de terminaison Plan 1 et Plan 2](defender-endpoint-plan-1-2.md).

## <a name="defender-for-endpoint-plan-1-capabilities"></a>Fonctionnalités de Defender pour point de terminaison Plan 1

Defender pour point de terminaison Plan 1 inclut les fonctionnalités suivantes :

- **[Protection de nouvelle génération](#next-generation-protection)** qui inclut un logiciel anti-programme malveillant et une protection antivirus de pointe
- **[Actions de réponse manuelles](#manual-response-actions)**, telles que l’envoi d’un fichier en quarantaine, que votre équipe de sécurité peut prendre sur des appareils ou des fichiers lorsque des menaces sont détectées
- **[Fonctionnalités de réduction de la surface d’attaque](#attack-surface-reduction)** qui renforcent les appareils, empêchent les attaques zero-day et offrent un contrôle granulaire sur l’accès et les comportements des points de terminaison
- **[Configuration et gestion centralisées](#centralized-management)** avec le portail Microsoft 365 Defender et intégration à Microsoft Endpoint Manager
- **[Protection pour diverses plateformes](#cross-platform-support)**, notamment les appareils Windows, macOS, iOS et Android

Les sections suivantes fournissent plus d’informations sur ces fonctionnalités. 

## <a name="next-generation-protection"></a>Protection de nouvelle génération

La protection de nouvelle génération inclut une protection antivirus et anti-programme malveillant robuste. Avec la protection de nouvelle génération, vous obtenez : 

- Protection antivirus basée sur le comportement, heuristique et en temps réel 
- Protection fournie par le cloud, qui inclut la détection quasi instantanée et le blocage des menaces nouvelles et émergentes 
- Protection dédiée et mises à jour du produit, y compris les mises à jour liées à Microsoft Defender Antivirus 

Pour en savoir plus, consultez [la vue d’ensemble de la protection nouvelle génération](next-generation-protection.md).

## <a name="manual-response-actions"></a>Actions de réponse manuelle

Les actions de réponse manuelle sont des actions que votre équipe de sécurité peut effectuer lorsque des menaces sont détectées sur des points de terminaison ou dans des fichiers. Defender pour point de terminaison inclut certaines [actions de réponse manuelle qui peuvent être effectuées sur un appareil](respond-machine-alerts.md) détecté comme potentiellement compromis ou ayant du contenu suspect. Vous pouvez également exécuter [des actions de réponse sur des fichiers](respond-file-alerts.md) détectés comme des menaces. Le tableau suivant récapitule les actions de réponse manuelles disponibles dans Defender pour point de terminaison Plan 1. <br/><br/>

| Fichier/appareil | Opération | Description |
|:---|:---|:---|
| Device | Exécuter une analyse antivirus | Démarre une analyse antivirus. Si des menaces sont détectées sur l’appareil, ces menaces sont souvent traitées lors d’une analyse antivirus. |
| Device | Isoler l’appareil | Déconnecte un appareil du réseau de votre organisation tout en conservant la connectivité à Defender pour point de terminaison. Cette action vous permet de surveiller l’appareil et de prendre des mesures supplémentaires si nécessaire. |
| File | Arrêter et mettre en quarantaine |Empêche l’exécution des processus et met en quarantaine les fichiers associés. |
| File | Ajouter un indicateur pour bloquer ou autoriser un fichier | Les indicateurs de bloc empêchent la lecture, l’écriture ou l’exécution des fichiers exécutables portables sur les appareils. <p>Les indicateurs d’autorisation empêchent le blocage ou la correction des fichiers. |

Pour en savoir plus, consultez les articles suivants :

- [Effectuer des actions de réponse sur les appareils](respond-machine-alerts.md) 
- [Effectuer des actions de réponse sur des fichiers](respond-file-alerts.md)

## <a name="attack-surface-reduction"></a>Réduction de la surface d'attaque

Les surfaces d’attaque de votre organisation sont tous les endroits où vous êtes vulnérable aux cyberattaques. Avec Defender pour point de terminaison Plan 1, vous pouvez réduire vos surfaces d’attaque en protégeant les appareils et applications utilisés par votre organisation. Les fonctionnalités de réduction de la surface d’attaque incluses dans Defender pour point de terminaison Plan 1 sont décrites dans les sections suivantes.

- [Règles de réduction de la surface d’attaque](#attack-surface-reduction-rules)
- [Atténuation des ransomwares](#ransomware-mitigation)
- [Contrôle des appareils](#device-control)
- [Protection web](#web-protection)
- [Protection du réseau](#web-protection)
- [Pare-feu réseau](#network-firewall)
- [Contrôle d’application](#application-control)

Pour en savoir plus sur les fonctionnalités de réduction de la surface d’attaque dans Defender pour point de terminaison, consultez [Vue d’ensemble de la réduction de la surface d’attaque](overview-attack-surface-reduction.md).

### <a name="attack-surface-reduction-rules"></a>Règles de réduction des surfaces d'attaque

Les règles de réduction de la surface d’attaque ciblent certains comportements logiciels considérés comme risqués. Ces comportements sont les suivants :

- Lancement de fichiers exécutables et de scripts qui tentent de télécharger ou d’exécuter d’autres fichiers
- Exécution de scripts masqués ou suspects
- Lancer des comportements que les applications n’initient généralement pas pendant le travail normal

Les applications métier légitimes peuvent présenter de tels comportements logiciels ; toutefois, ces comportements sont souvent considérés comme risqués, car ils sont couramment abusés par les attaquants par le biais de programmes malveillants. Les règles de réduction de la surface d’attaque peuvent limiter les comportements à risque et contribuer à la sécurité de votre organisation.

Pour plus d’informations, consultez [Utiliser les règles de réduction de la surface d’attaque pour prévenir l’infection des programmes malveillants](attack-surface-reduction.md).

### <a name="ransomware-mitigation"></a>Atténuation des ransomwares

Avec l’accès contrôlé aux dossiers, vous obtenez l’atténuation des ransomwares. L’accès contrôlé aux dossiers permet uniquement aux applications approuvées d’accéder aux dossiers protégés sur vos points de terminaison. Les applications sont ajoutées à la liste des applications approuvées en fonction de leur prévalence et de leur réputation. Votre équipe des opérations de sécurité peut également ajouter ou supprimer des applications de la liste des applications approuvées.

Pour en savoir plus, consultez [Protéger les dossiers importants avec un accès contrôlé aux dossiers](controlled-folders.md).

### <a name="device-control"></a>Contrôle des appareils

Parfois, les menaces pesant sur les appareils de votre organisation se présentent sous la forme de fichiers sur des lecteurs amovibles, tels que des lecteurs USB. Defender pour point de terminaison inclut des fonctionnalités pour empêcher les menaces provenant de périphériques non autorisés de compromettre vos appareils. Vous pouvez configurer Defender pour point de terminaison pour bloquer ou autoriser les appareils et fichiers amovibles sur les appareils amovibles. 

Pour plus d’informations, consultez [Contrôlez les périphériques USB et les supports amovibles](control-usb-devices-using-intune.md).

### <a name="web-protection"></a>Protection Web

Avec la protection web, vous pouvez protéger les appareils de votre organisation contre les menaces web et le contenu indésirable. La protection web inclut la protection contre les menaces web et le filtrage du contenu web.

- [La protection contre les menaces web](web-threat-protection.md) empêche l’accès aux sites de hameçonnage, aux vecteurs de programmes malveillants, aux sites d’exploitation, aux sites non approuvés ou à faible réputation et aux sites que vous bloquez explicitement.
- [Le filtrage de contenu web](web-content-filtering.md) empêche l’accès à certains sites en fonction de leur catégorie. Les catégories peuvent inclure le contenu pour adultes, les sites de loisirs, les sites de responsabilité légale, etc.

Pour plus d’informations, consultez [la protection web](web-protection-overview.md).

### <a name="network-protection"></a>Protection réseau

Grâce à la protection réseau, vous pouvez empêcher votre organisation d’accéder à des domaines dangereux susceptibles d’héberger des escroqueries, des exploits et d’autres contenus malveillants sur Internet. 

Pour plus d’informations, consultez [Protéger votre réseau](network-protection.md).

### <a name="network-firewall"></a>Pare-feu réseau

Avec la protection pare-feu réseau, vous pouvez définir des règles qui déterminent le trafic réseau autorisé à circuler vers ou depuis les appareils de votre organisation. Avec votre pare-feu réseau et une sécurité avancée que vous obtenez avec Defender pour point de terminaison, vous pouvez :

- Réduire le risque de menaces de sécurité réseau
- Protéger les données sensibles et la propriété intellectuelle
- Étendre votre investissement en matière de sécurité

Pour plus d’informations, consultez [Windows Defender Pare-feu avec une sécurité avancée](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).

### <a name="application-control"></a>Contrôle d’application

Le contrôle d’application protège vos points de terminaison Windows en exécutant uniquement des applications et du code approuvés dans le noyau (noyau). Votre équipe de sécurité peut définir des règles de contrôle d’application qui prennent en compte les attributs d’une application, tels que ses certificats de signature de code, sa réputation, son processus de lancement, etc. Le contrôle d’application est disponible dans Windows 10 ou version ultérieure.

Pour plus d’informations, consultez [Contrôle d’application pour Windows](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control).

## <a name="centralized-management"></a>Gestion centralisée

Defender pour point de terminaison Plan 1 inclut le portail Microsoft 365 Defender, qui permet à votre équipe de sécurité d’afficher les informations actuelles sur les menaces détectées, de prendre les mesures appropriées pour atténuer les menaces et de gérer de manière centralisée les paramètres de protection contre les menaces de votre organisation.

Pour en savoir plus, consultez [Microsoft 365 Defender vue d’ensemble du portail](portal-overview.md).

### <a name="role-based-access-control"></a>Contrôle d'accès basé sur les rôles

À l’aide du contrôle d’accès en fonction du rôle (RBAC), votre administrateur de sécurité peut créer des rôles et des groupes pour accorder un accès approprié au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Avec RBAC, vous disposez d’un contrôle précis sur qui peut accéder à Defender pour cloud, et ce qu’ils peuvent voir et faire. 

Pour plus d’informations, consultez [Gérer l’accès au portail à l’aide du contrôle d’accès en fonction du rôle](rbac.md).

### <a name="reporting"></a>Reporting

Le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) permet d’accéder facilement aux informations sur les menaces détectées et les actions permettant de résoudre ces menaces. 

- La page **d’accueil** inclut des cartes permettant d’afficher en un coup d’œil les utilisateurs ou appareils à risque, le nombre de menaces détectées et les alertes/incidents créés.
- La section **Incidents & alertes** répertorie tous les incidents qui ont été créés à la suite d’alertes déclenchées. Les alertes et les incidents sont générés à mesure que des menaces sont détectées sur les appareils.
- Le **Centre d’actions** répertorie les actions de correction qui ont été effectuées. Par exemple, si un fichier est envoyé en quarantaine ou si une URL est bloquée, chaque action est répertoriée dans le centre d’actions de l’onglet **Historique** .
- La section **Rapports** inclut des rapports qui montrent les menaces détectées et leur état. 

Pour en savoir plus, consultez [Prise en main de Microsoft Defender pour point de terminaison Plan 1](mde-plan1-getting-started.md).

### <a name="apis"></a>API

Avec les API Defender pour point de terminaison, vous pouvez automatiser les flux de travail et les intégrer aux solutions personnalisées de votre organisation. 

Pour plus d’informations, consultez [les API Defender pour point de terminaison](management-apis.md). 

## <a name="cross-platform-support"></a>Prise en charge multiplateforme

La plupart des organisations utilisent différents appareils et systèmes d’exploitation. Actuellement, Defender pour point de terminaison Plan 1 prend en charge les systèmes d’exploitation suivants :

- Windows 7 (ESU requis)
- Windows 8.1
- Windows 10, version 1709 ou ultérieure
- Windows 10 Entreprise
- Windows 10 Entreprise LTSC 2016 (ou version ultérieure)](/windows/whats-new/ltsc/)
- Windows 10 Entreprise loT
- macOS (les trois versions les plus récentes sont prises en charge)
- iOS
- Système d’exploitation Android

## <a name="next-steps"></a>Prochaines étapes

- [Comparer Microsoft Defender pour point de terminaison plan 1 à Plan 2](defender-endpoint-plan-1-2.md)
- [Installer et configurer Defender pour Endpoint Plan 1](mde-p1-setup-configuration.md)
- [Prise en main de Defender pour point de terminaison Plan 1](mde-plan1-getting-started.md)
- [Gérer Defender pour point de terminaison Plan 1](mde-p1-maintenance-operations.md)
