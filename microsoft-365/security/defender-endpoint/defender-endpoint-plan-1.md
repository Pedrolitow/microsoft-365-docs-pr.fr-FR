---
title: Vue d’ensemble de Microsoft Defender pour Endpoint Plan 1 (prévisualisation)
description: Obtenez une vue d’ensemble de Defender pour Endpoint Plan 1. Découvrez les fonctionnalités incluses dans cet abonnement de protection des points de terminaison.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 10/01/2021
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection: M365-security-compliance
ms.openlocfilehash: 17026088cc10b5ace84cbab31f0a383661e2484b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60204046"
---
# <a name="overview-of-microsoft-defender-for-endpoint-plan-1-preview"></a>Vue d’ensemble de Microsoft Defender pour Endpoint Plan 1 (prévisualisation)

> [!TIP]
> Si vous avez Microsoft 365 E3 ou A3, mais pas Microsoft 365 E5 ou A5, visitez le site pour vous inscrire [https://aka.ms/mdep1trial](https://aka.ms/mdep1trial) au programme d’aperçu !

Microsoft Defender pour point de terminaison est une plateforme de sécurité de point de terminaison d’entreprise conçue pour aider des organisations telles que la vôtre à prévenir, détecter, examiner et répondre aux menaces avancées. Nous sommes heureux d’annoncer que Defender pour Point de terminaison est désormais disponible dans deux plans : 

- **Defender for Endpoint Plan 1**, actuellement en prévisualisation, et décrit dans cet article ; et 
- **[Defender for Endpoint Plan 2](microsoft-defender-endpoint.md)**, généralement disponible, et anciennement [appelé Defender for Endpoint](microsoft-defender-endpoint.md).

L’image suivante illustre ce qui est inclus dans Defender pour Endpoint Plan 1 (prévisualisation) :

:::image type="content" source="../../media/mde-p1/mde-p1-overview-diagram.png" alt-text="Diagramme Defender for Endpoint Plan 1":::

Utilisez ce guide pour :

- [Obtenir une vue d’ensemble de ce qui est inclus dans Defender pour Endpoint Plan 1 (prévisualisation)](#defender-for-endpoint-plan-1-capabilities)
- [Comparer Defender for Endpoint Plan 1 à Plan 2](defender-endpoint-plan-1-2.md)
- [Découvrez comment configurer Defender pour Endpoint Plan 1](mde-p1-setup-configuration.md)
- [Commencer à utiliser le portail Microsoft 365 Defender, où vous pouvez afficher les incidents et les alertes, gérer les appareils et utiliser des rapports sur les menaces détectées](mde-plan1-getting-started.md)
- [Obtenir une vue d’ensemble de la maintenance et des opérations](mde-p1-maintenance-operations.md)

> [!TIP]
> [En savoir plus sur les différences entre Defender pour Endpoint Plan 1 et Plan 2](defender-endpoint-plan-1-2.md).

## <a name="defender-for-endpoint-plan-1-capabilities"></a>Fonctionnalités de Defender for Endpoint Plan 1

Defender pour endpoint Plan 1 (prévisualisation) inclut les fonctionnalités suivantes :

- **[Protection nouvelle génération qui inclut](#next-generation-protection)** une protection antivirus et anti-programme malveillant robuste et de pointe du secteur
- **[Actions de réponse manuelles,](#manual-response-actions)** telles que l’envoi d’un fichier en quarantaine, que votre équipe de sécurité peut prendre sur des appareils ou des fichiers lorsque des menaces sont détectées
- **[Fonctionnalités de réduction de la surface](#attack-surface-reduction)** d’attaque qui renforcent les appareils, empêchent les attaques zero-day et offrent un contrôle granulaire sur l’accès et les comportements des points de terminaison
- **[Configuration et gestion centralisées avec](#centralized-management)** le portail Microsoft 365 Defender et l’intégration avec Microsoft Endpoint Manager
- **[Protection pour une variété de plateformes,](#cross-platform-support)** notamment Windows, macOS, iOS et Android

Les sections suivantes fournissent plus de détails sur ces fonctionnalités. 

> [!IMPORTANT]
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. Ce guide inclut des liens vers du contenu en ligne qui peut décrire ou décrire certaines fonctionnalités qui ne sont pas incluses dans Defender for Endpoint Plan 1 (prévisualisation).

## <a name="next-generation-protection"></a>Protection de nouvelle génération

La protection nouvelle génération inclut une protection antivirus et anti-programme malveillant robuste. Avec la protection nouvelle génération, vous obtenez les droits suivants : 

- Protection antivirus en temps réel, heuristique et basée sur le comportement 
- Protection cloud, qui inclut la détection et le blocage quasi instantanés des menaces nouvelles et émergentes 
- Mises à jour de produits et de protection dédiées, y compris les mises à jour liées Antivirus Microsoft Defender 

Pour plus d’informations, voir [vue d’ensemble de la protection nouvelle génération.](next-generation-protection.md)

## <a name="manual-response-actions"></a>Actions de réponse manuelles

Les actions de réponse manuelles sont des actions que votre équipe de sécurité peut prendre lorsque des menaces sont détectées sur des points de terminaison ou dans des fichiers. Defender pour le point de terminaison inclut certaines [actions](respond-machine-alerts.md) de réponse manuelles qui peuvent être prises sur un appareil détecté comme potentiellement compromis ou qui contient du contenu suspect. Vous pouvez également exécuter des [actions de réponse sur des fichiers](respond-file-alerts.md) détectés comme des menaces. Le tableau suivant récapitule les actions de réponse manuelles disponibles dans Defender for Endpoint Plan 1. <br/><br/>

| Fichier/Périphérique | Opération | Description |
|:---|:---|:---|
| Appareil | Exécuter une analyse antivirus | Démarre une analyse antivirus. Si des menaces sont détectées sur l’appareil, ces menaces sont souvent traitées lors d’une analyse antivirus. |
| Appareil | Isoler l’appareil | Déconnecte un appareil du réseau de votre organisation tout en conservant la connectivité à Defender for Endpoint. Cette action vous permet de surveiller l’appareil et de prendre des mesures supplémentaires si nécessaire. |
| Fichier | Arrêter et mettre en quarantaine |Arrête l’exécution des processus et met en quarantaine les fichiers associés. |
| Fichier | Ajouter un indicateur pour bloquer ou autoriser un fichier | Les indicateurs de blocage empêchent la lecture, l’écriture ou l’exécution de fichiers exécutables portables sur les appareils. <p>Les indicateurs d’autoriser empêchent le blocage ou la correction des fichiers. |

Pour en savoir plus, consultez les articles suivants :

- [Prendre des mesures de réponse sur les appareils](respond-machine-alerts.md) 
- [Prendre des actions de réponse sur des fichiers](respond-file-alerts.md)

## <a name="attack-surface-reduction"></a>Réduction de la surface d'attaque

Les surfaces d’attaque de votre organisation sont tous les endroits où vous êtes vulnérable aux cyberattaques. Avec Defender for Endpoint Plan 1 (prévisualisation), vous pouvez réduire vos surfaces d’attaque en protégeant les appareils et les applications utilisés par votre organisation. Les fonctionnalités de réduction de la surface d’attaque incluses dans Defender for Endpoint Plan 1 (aperçu) sont décrites dans les sections suivantes.

- [Règles de réduction de la surface d’attaque](#attack-surface-reduction-rules)
- [Atténuation des ransomware](#ransomware-mitigation)
- [Contrôle des appareils](#device-control)
- [Protection web](#web-protection)
- [Protection du réseau](#web-protection)
- [Pare-feu réseau](#network-firewall)
- [Contrôle d’application](#application-control)

Pour en savoir plus sur les fonctionnalités de réduction de la surface d’attaque dans Defender pour le point de terminaison, voir Vue d’ensemble de la [réduction de la surface d’attaque.](overview-attack-surface-reduction.md)

### <a name="attack-surface-reduction-rules"></a>Règles de réduction de la surface d’attaque

Les règles de réduction de la surface d’attaque ciblent certains comportements logiciels considérés comme risqués. Ces comportements sont les suivants :

- Lancement de fichiers exécutables et de scripts qui tentent de télécharger ou d’exécuter d’autres fichiers
- Exécution de scripts obscurcis ou suspects
- Comportements de l’initiateur que les applications n’initient généralement pas au cours d’un travail normal

Les applications d’entreprise légitimes peuvent présenter de tels comportements logiciels ; Toutefois, ces comportements sont souvent considérés comme risqués, car ils sont couramment abusés par des personnes malveillantes par le biais de programmes malveillants. Les règles de réduction de la surface d’attaque peuvent limiter les comportements à risque et contribuer à la sécurité de votre organisation.

Pour plus d’informations, voir Utiliser les règles de réduction [de la surface d’attaque pour empêcher l’infection par des programmes malveillants.](attack-surface-reduction.md)

### <a name="ransomware-mitigation"></a>Atténuation des ransomware

Avec l’accès contrôlé aux dossiers, vous obtenez une atténuation des ransomware. L’accès contrôlé aux dossiers permet uniquement aux applications de confiance d’accéder aux dossiers protégés sur vos points de terminaison. Les applications sont ajoutées à la liste des applications de confiance en fonction de leur prévalence et de leur réputation. Votre équipe des opérations de sécurité peut également ajouter ou supprimer des applications de la liste des applications de confiance.

Pour plus d’informations, voir [Protéger les dossiers importants avec un accès contrôlé aux dossiers.](controlled-folders.md)

### <a name="device-control"></a>Contrôle d’appareil

Parfois, les menaces qui pèsent sur les appareils de votre organisation se font sous la forme de fichiers sur des lecteurs amovibles, tels que des lecteurs USB. Defender pour le point de terminaison inclut des fonctionnalités qui permettent d’empêcher les menaces provenant de périphériques non autorisés de compromettre vos appareils. Vous pouvez configurer Defender pour le point de terminaison pour bloquer ou autoriser les appareils et fichiers amovibles sur les appareils amovibles. 

Pour en savoir plus, [consultez Les périphériques USB de contrôle et les supports amovibles.](control-usb-devices-using-intune.md)

### <a name="web-protection"></a>Protection Web

Grâce à la protection web, vous pouvez protéger les appareils de votre organisation contre les menaces web et le contenu indésirable. La protection Web inclut la protection contre les menaces web et le filtrage de contenu web.

- [La protection contre](web-threat-protection.md) les menaces web empêche l’accès aux sites de hameçonnage, aux vecteurs de programmes malveillants, aux sites d’exploitation, aux sites non protégés ou à faible réputation et aux sites que vous bloquez explicitement.
- [Le filtrage de contenu Web](web-content-filtering.md) (prévisualisation) empêche l’accès à certains sites en fonction de leur catégorie. Les catégories peuvent inclure du contenu pour adultes, des sites de divertissement, des sites de responsabilité juridique, etc.

Pour en savoir plus, consultez [la protection web.](web-protection-overview.md)

### <a name="network-protection"></a>Protection réseau

Grâce à la protection réseau, vous pouvez empêcher votre organisation d’accéder à des domaines dangereux qui pourraient héberger des tentatives d’hameçonnage, des attaques et d’autres contenus malveillants sur Internet. 

Pour en savoir plus, [consultez Protéger votre réseau.](network-protection.md)

### <a name="network-firewall"></a>Pare-feu réseau

Grâce à la protection du pare-feu réseau, vous pouvez définir des règles qui déterminent le trafic réseau autorisé à circuler vers ou depuis les appareils de votre organisation. Avec votre pare-feu réseau et la sécurité avancée que vous obtenez avec Defender pour le point de terminaison, vous pouvez :

- Réduire le risque de menaces de sécurité réseau
- Protéger les données sensibles et la propriété intellectuelle
- Étendre votre investissement en matière de sécurité

Pour plus d’informations, [voir Windows Defender Pare-feu avec une sécurité avancée.](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)

### <a name="application-control"></a>Contrôle d’application

Le contrôle d’application protège Windows points de terminaison en exécutant uniquement du code et des applications de confiance dans le noyau système. Votre équipe de sécurité peut définir des règles de contrôle d’application qui considèrent les attributs d’une application, tels que ses certificats de codes, sa réputation, son processus de lancement, etc. Le contrôle d’application est disponible Windows 10 ou ultérieure.

Pour plus d’informations, [voir Contrôle d’application pour Windows](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control).

## <a name="centralized-management"></a>Gestion centralisée

Defender for Endpoint Plan 1 (prévisualisation) inclut le portail Microsoft 365 Defender, qui permet à votre équipe de sécurité d’afficher les informations actuelles sur les menaces détectées, de prendre les mesures appropriées pour atténuer les menaces et de gérer de manière centralisée les paramètres de protection contre les menaces de votre organisation.

Pour plus d’informations, [voir Microsoft 365 Defender portail.](portal-overview.md)

### <a name="role-based-access-control"></a>Contrôle d'accès basé sur les rôles

À l’aide du contrôle d’accès basé sur un rôle (RBAC), votre administrateur de sécurité peut créer des rôles et des groupes pour accorder un accès approprié au portail Microsoft 365 Defender ( [https://security.microsoft.com](https://security.microsoft.com) ). Avec RBAC, vous avez un contrôle fin sur les personnes qui peuvent accéder au centre de sécurité, ainsi que sur ce qu’elles peuvent voir et faire. 

Pour plus d’informations, voir [Gérer l’accès au portail à l’aide du contrôle d’accès basé sur les rôles.](rbac.md)

### <a name="reporting"></a>Rapports

Le portail Microsoft 365 Defender ( ) fournit un accès facile aux informations sur les menaces détectées et les actions à prendre pour [https://security.microsoft.com](https://security.microsoft.com) y remédier. 

- La page **d’accueil** inclut des cartes pour afficher en un coup d’œil les utilisateurs ou appareils à risque, le nombre de menaces détectées et les alertes/incidents qui ont été créés.
- La section **Incidents & alertes** répertorie tous les incidents qui ont été créés suite à des alertes déclenchées. Les alertes et les incidents sont générés lorsque des menaces sont détectées sur plusieurs appareils.
- Le centre **de mise en œuvre répertorie** les actions correctives qui ont été prises. Par exemple, si un fichier est mis en quarantaine ou qu’une URL est bloquée, chaque action est répertoriée dans le centre de actions sous **l’onglet** Historique.
- La section **Rapports** inclut des rapports qui indiquent les menaces détectées et leur état. 

Pour en savoir plus, [consultez La mise en place de Microsoft Defender pour Endpoint Plan 1 (prévisualisation).](mde-plan1-getting-started.md)

### <a name="apis"></a>API

Avec les API Defender for Endpoint, vous pouvez automatiser les flux de travail et les intégrer aux solutions personnalisées de votre organisation. 

Pour en savoir plus, [consultez l’api Defender pour les points de terminaison.](management-apis.md) 

## <a name="cross-platform-support"></a>Prise en charge sur plusieurs plateformes

La plupart des organisations utilisent différents appareils et systèmes d’exploitation. Actuellement, Defender for Endpoint Plan 1 (prévisualisation) prend en charge les systèmes d’exploitation suivants :

- Windows 10, version 1709 ou ultérieure
- macOS : 11.5 (Big Sur), 10.15.7 (Contrôle), ou 10.14.6 (Mojave)
- iOS
- Système d’exploitation Android

## <a name="next-steps"></a>Étapes suivantes

- [Comparer Microsoft Defender pour Endpoint Plan 1 (prévisualisation) à Plan 2](defender-endpoint-plan-1-2.md)
- [Configurer Defender pour Endpoint Plan 1 (prévisualisation)](mde-p1-setup-configuration.md)
- [Mise en place de Defender pour Endpoint Plan 1 (prévisualisation)](mde-plan1-getting-started.md)
- [Gérer Defender pour endpoint Plan 1 (prévisualisation)](mde-p1-maintenance-operations.md)