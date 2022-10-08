---
title: Détection d’appareils réseau et gestion des vulnérabilités
description: Les recommandations de sécurité et la détection des vulnérabilités sont désormais disponibles pour les systèmes d’exploitation des commutateurs, routeurs, contrôleurs WLAN et pare-feu.
keywords: appareils réseau, détection des vulnérabilités des appareils réseau, systèmes d’exploitation de commutateurs, routeurs, contrôleurs WLAN et pare-feu
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: levinec
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier1
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: b0f614a15957c625bff66a34581ec8477b529778
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68233571"
---
# <a name="network-device-discovery-and-vulnerability-management"></a>Détection d’appareils réseau et gestion des vulnérabilités

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Gestion des vulnérabilités Defender](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

> [!NOTE]
> Le blog \(sur [la découverte des appareils réseau et les évaluations des vulnérabilités](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/network-device-discovery-and-vulnerability-assessments/ba-p/2267548) publié le 13-04/2021\) fournit des insights sur les nouvelles fonctionnalités de **découverte d’appareils réseau** dans Defender pour point de terminaison. Cet article fournit une vue d’ensemble du défi que la **découverte d’appareils réseau** est conçue pour résoudre, ainsi que des informations détaillées sur la prise en main de ces nouvelles fonctionnalités.

Les fonctionnalités de découverte du réseau sont disponibles dans la section **Inventaire des appareils** du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> et des consoles Microsoft 365 Defender.

Un appareil Microsoft Defender pour point de terminaison désigné sera utilisé sur chaque segment réseau pour effectuer des analyses périodiques authentifiées des appareils réseau préconfigurés. Une fois découvertes, les fonctionnalités de gestion des vulnérabilités de Defender pour point de terminaison fournissent des workflows intégrés pour sécuriser les commutateurs détectés, les routeurs, les contrôleurs WLAN, les pare-feu et les passerelles VPN.

Une fois que les appareils réseau sont découverts et classifiés, les administrateurs de sécurité peuvent recevoir les dernières recommandations de sécurité et examiner les vulnérabilités récemment découvertes sur les appareils réseau déployés au sein de leur organisation.

## <a name="approach"></a>Approche

Les appareils réseau ne sont pas gérés en tant que points de terminaison standard, car Defender pour point de terminaison n’a pas de capteur intégré aux appareils réseau eux-mêmes. Ces types d’appareils nécessitent une approche sans agent dans laquelle une analyse à distance obtient les informations nécessaires auprès des appareils. Selon la topologie et les caractéristiques du réseau, un seul appareil ou quelques appareils intégrés à Microsoft Defender pour point de terminaison effectuent des analyses authentifiées des appareils réseau à l’aide de SNMP (en lecture seule).

Il y aura deux types d’appareils à garder à l’esprit :

- **Appareil d’évaluation** : appareil déjà intégré que vous utiliserez pour analyser les appareils réseau.
- **Appareils réseau** : appareils réseau que vous envisagez d’analyser et d’intégrer.

### <a name="vulnerability-management-for-network-devices"></a>Gestion des vulnérabilités pour les appareils réseau

Une fois que les appareils réseau sont découverts et classifiés, les administrateurs de sécurité peuvent recevoir les dernières recommandations de sécurité et examiner les vulnérabilités récemment découvertes sur les appareils réseau déployés au sein de leur organisation.

## <a name="operating-systems-that-are-supported"></a>Systèmes d’exploitation pris en charge

Les systèmes d’exploitation suivants sont actuellement pris en charge :

- Cisco IOS, IOS-XE, NX-OS
- Juniper JUNOS
- HPE ArubaOS, Procurve Switch Software
- Palo Alto Networks PAN-OS

D’autres fournisseurs de mise en réseau et système d’exploitation seront ajoutés au fil du temps, en fonction des données collectées à partir de l’utilisation des clients. Par conséquent, vous êtes invité à configurer tous vos appareils réseau, même s’ils ne sont pas spécifiés dans cette liste.

## <a name="how-to-get-started"></a>Prise en main

La première étape consiste à sélectionner un appareil qui effectuera les analyses réseau authentifiées.

1. Choisissez un appareil intégré Defender pour point de terminaison (client ou serveur) qui dispose d’une connexion réseau au port de gestion pour les appareils réseau que vous envisagez d’analyser.

2. Le trafic SNMP entre l’appareil d’évaluation Defender pour point de terminaison et les périphériques réseau ciblés doit être autorisé (par exemple, par le pare-feu).

3. Déterminez les appareils réseau qui seront évalués pour les vulnérabilités (par exemple, un commutateur Cisco ou un pare-feu Palo Alto Networks).

4. Assurez-vous que SNMP en lecture seule est activé sur tous les appareils réseau configurés pour permettre à l’appareil d’évaluation Defender pour point de terminaison d’interroger les appareils réseau configurés. « Écriture SNMP » n’est pas nécessaire pour la fonctionnalité appropriée de cette fonctionnalité.

5. Obtenez les adresses IP des appareils réseau à analyser (ou les sous-réseaux où ces appareils sont déployés).

6. Obtenez les informations d’identification SNMP des appareils réseau (par exemple : Community String, noAuthNoPriv, authNoPriv, authPriv). Vous devrez fournir les informations d’identification lors de la configuration d’un nouveau travail d’évaluation.

7. Configuration du client proxy : aucune configuration supplémentaire n’est requise autre que les exigences de proxy d’appareil Defender pour point de terminaison.

8. Pour permettre au scanneur réseau d’être authentifié et de fonctionner correctement, il est essentiel d’ajouter les domaines/URL suivants :

    - login.windows.net
    - \*.security.microsoft.com
    - login.microsoftonline.com
    - \*.blob.core.windows.net/networkscannerstable/\*

    > [!NOTE]
    > Toutes les URL ne sont pas spécifiées dans la liste documentée Defender pour point de terminaison de la collecte de données autorisée.

## <a name="permissions"></a>Autorisations

Pour configurer les travaux d’évaluation, l’option d’autorisation utilisateur suivante est requise : **Gérer les paramètres de sécurité dans Defender**. Vous pouvez trouver l’autorisation en accédant à **Paramètres Rôles**\>. Pour plus d’informations, consultez [Créer et gérer des rôles pour le contrôle d’accès en fonction du rôle](user-roles.md).

## <a name="install-the-network-scanner"></a>Installer le scanneur réseau

1. Accédez aux **travaux d’évaluation** des points de terminaison **des paramètres** \>  \> de **sécurité** \> Microsoft 365 (sous **Évaluations réseau**).
    1. Dans le portail Microsoft 365 Defender, accédez à la page Paramètres > Travaux d’évaluation.

2. Téléchargez le scanneur réseau et installez-le sur l’appareil d’évaluation Defender pour point de terminaison désigné.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/assessment-jobs-download-scanner.png" alt-text="Bouton Télécharger le scanneur" lightbox="images/assessment-jobs-download-scanner.png":::

## <a name="network-scanner-installation--registration"></a>Installation du scanneur réseau & inscription

Le processus de connexion peut être effectué sur l’appareil d’évaluation désigné lui-même ou sur tout autre appareil (par exemple, votre appareil client personnel).

> [!NOTE]
> Le compte avec lequel l’utilisateur se connecte et l’appareil utilisé pour terminer le processus de connexion doivent se trouver dans le même locataire que celui avec lequel l’appareil est intégré à Microsoft Defender pour point de terminaison.

Pour terminer le processus d’inscription du scanneur réseau :

1. Copiez et suivez l’URL qui apparaît sur la ligne de commande et utilisez le code d’installation fourni pour terminer le processus d’inscription.

    > [!NOTE]
    > Vous devrez peut-être modifier les paramètres d’invite de commandes pour pouvoir copier l’URL.

2. Entrez le code et connectez-vous à l’aide d’un compte Microsoft disposant de l’autorisation Defender pour point de terminaison appelée « Gérer les paramètres de sécurité dans Defender ».

3. Lorsque vous avez terminé, vous devriez voir un message confirmant que vous êtes connecté.

## <a name="configure-a-new-assessment-job"></a>Configurer un nouveau travail d’évaluation

Dans la page Tâches d’évaluation dans **Paramètres**, **sélectionnez Ajouter un travail d’évaluation réseau**. Suivez le processus de configuration pour choisir les appareils réseau à analyser régulièrement et à ajouter à l’inventaire des appareils.

Pour empêcher la duplication d’appareils dans l’inventaire des appareils réseau, assurez-vous que chaque adresse IP n’est configurée qu’une seule fois sur plusieurs appareils d’évaluation.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/assessment-jobs-add.png" alt-text="Bouton Ajouter une tâche d’évaluation réseau" lightbox="images/assessment-jobs-add.png":::

Ajout d’une étape de travail d’évaluation réseau :

1. Choisissez le nom du travail d’évaluation et l’appareil d’évaluation sur lequel le scanneur réseau a été installé. Cet appareil effectue les analyses périodiques authentifiées.

2. Ajoutez les adresses IP des appareils réseau cibles à analyser (ou les sous-réseaux où ces appareils sont déployés).

3. Ajoutez les informations d’identification SNMP requises des appareils réseau cibles.

4. Enregistrez le travail d’évaluation réseau nouvellement configuré pour démarrer l’analyse réseau périodique.

### <a name="scan-and-add-network-devices"></a>Analyser et ajouter des appareils réseau

Pendant le processus de configuration, vous pouvez effectuer une analyse de test unique pour vérifier que :

- Il existe une connectivité entre l’appareil d’évaluation Defender pour point de terminaison et les appareils réseau cibles configurés.
- Les informations d’identification SNMP configurées sont correctes.

Chaque appareil d’évaluation peut prendre en charge jusqu’à 1 500 analyses d’adresses IP réussies. Par exemple, si vous analysez 10 sous-réseaux différents où seules 100 adresses IP retournent des résultats réussis, vous pouvez analyser 1 400 adresses IP supplémentaires à partir d’autres sous-réseaux sur le même appareil d’évaluation.

S’il existe plusieurs plages d’adresses IP/sous-réseaux à analyser, l’affichage des résultats de l’analyse de test prend plusieurs minutes. Une analyse de test sera disponible pour jusqu’à 1 024 adresses.

Une fois les résultats affichés, vous pouvez choisir les appareils qui seront inclus dans l’analyse périodique. Si vous ignorez l’affichage des résultats de l’analyse, toutes les adresses IP configurées sont ajoutées au travail d’évaluation réseau (quelle que soit la réponse de l’appareil). Les résultats de l’analyse peuvent également être exportés.

## <a name="device-inventory"></a>Inventaire des appareils

Les appareils nouvellement découverts s’affichent sous le nouvel onglet **Appareils réseau** de la page **Inventaire des** appareils. L’ajout d’un travail d’évaluation peut prendre jusqu’à deux heures avant que les appareils soient mis à jour.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/assessment-jobs-device-inventory.png" alt-text="Section Appareils réseau dans l’inventaire des appareils" lightbox="images/assessment-jobs-device-inventory.png":::

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="network-scanner-installation-has-failed"></a>Échec de l’installation du scanneur réseau

Vérifiez que les URL requises sont ajoutées aux domaines autorisés dans vos paramètres de pare-feu. Vérifiez également que les paramètres de proxy sont configurés comme décrit dans [Configurer le proxy d’appareil et les paramètres de connectivité Internet](configure-proxy-internet.md).

### <a name="the-microsoftcomdevicelogin-web-page-did-not-show-up"></a>La page web Microsoft.com/devicelogin n’apparaît pas

Vérifiez que les URL requises sont ajoutées aux domaines autorisés dans votre pare-feu. Vérifiez également que les paramètres de proxy sont configurés comme décrit dans [Configurer le proxy d’appareil et les paramètres de connectivité Internet](configure-proxy-internet.md).

### <a name="network-devices-are-not-shown-in-the-device-inventory-after-several-hours"></a>Les appareils réseau ne sont pas affichés dans l’inventaire des appareils après plusieurs heures

Les résultats de l’analyse doivent être mis à jour quelques heures après l’analyse initiale qui a eu lieu après la configuration du travail d’évaluation.

Si les appareils ne sont toujours pas affichés, vérifiez que le service « MdatpNetworkScanService » s’exécute sur vos appareils d’évaluation, sur lesquels vous avez installé le scanneur réseau, et effectuez une « analyse d’exécution » dans la configuration du travail d’évaluation approprié.

Si vous n’obtenez toujours pas de résultats après 5 minutes, redémarrez le service.

### <a name="devices-last-seen-time-is-longer-than-24-hours"></a>L’heure de la dernière consultation des appareils est supérieure à 24 heures

Vérifiez que le scanneur s’exécute correctement. Accédez ensuite à la définition d’analyse et sélectionnez « Exécuter le test ». Vérifiez les messages d’erreur renvoyés par les adresses IP appropriées.

### <a name="required-defender-vulnerability-management-user-permission"></a>Autorisation d’utilisateur Defender Vulnerability Management requise

L’inscription s’est terminée par une erreur : « Il semble que vous ne disposez pas des autorisations suffisantes pour ajouter un nouvel agent. L’autorisation requise est « Gérer les paramètres de sécurité dans Defender ». »

Appuyez sur n’importe quelle touche pour quitter.

Demandez à votre administrateur système de vous attribuer les autorisations requises. Vous pouvez également demander à un autre membre approprié de vous aider dans le processus de connexion en lui fournissant le code de connexion et le lien.

### <a name="registration-process-fails-using-provided-link-in-the-command-line-in-registration-process"></a>Échec du processus d’inscription à l’aide du lien fourni dans la ligne de commande dans le processus d’inscription

Essayez un autre navigateur ou copiez le lien de connexion et le code sur un autre appareil.

### <a name="text-too-small-or-cant-copy-text-from-command-line"></a>Texte trop petit ou impossible à copier à partir de la ligne de commande

Modifiez les paramètres de ligne de commande sur votre appareil pour autoriser la copie et modifier la taille du texte.

## <a name="related-articles"></a>Articles connexes

- [Inventaire des appareils](machines-view-overview.md)
- [Configurer des fonctionnalités avancées](advanced-features.md)
