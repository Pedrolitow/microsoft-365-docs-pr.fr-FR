---
title: Menaces détectées par l’antivirus Microsoft Defender
f1.keywords: CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-security
ms.collection:
- m365-security
- tier1
ms.subservice: other
ms.date: 09/15/2022
ms.localizationpriority: medium
search.appverid: MET150
description: Découvrez comment Microsoft Defender Antivirus protège vos appareils Windows contre les menaces logicielles, telles que les virus, les programmes malveillants et les logiciels espions.
ms.openlocfilehash: 35a36a74645477afc9e33da72e6c5e6d9ce17dbe
ms.sourcegitcommit: 0283c436f3ba61a708b52b57a1955f5ea74376a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68097904"
---
# <a name="overview-of-threat-protection-by-microsoft-defender-antivirus"></a>Vue d’ensemble de la protection contre les menaces par Microsoft Defender Antivirus

Microsoft Defender Antivirus protège vos appareils Windows contre les menaces logicielles, telles que les virus, les programmes malveillants et les logiciels espions.

- Les virus se propagent généralement en attachant leur code à d’autres fichiers sur votre appareil ou réseau et peuvent entraîner un fonctionnement incorrect des programmes infectés.
- Les programmes malveillants incluent des fichiers, des applications et du code malveillants qui peuvent endommager et perturber l’utilisation normale des appareils. En outre, les programmes malveillants peuvent autoriser l’accès non autorisé, utiliser des ressources système, voler des mots de passe et des informations de compte, vous verrouiller hors de votre ordinateur et demander une rançon, et bien plus encore.
- Les logiciels espions collectent des données, telles que l’activité de navigation web, et envoient les données aux serveurs distants.
 
Pour assurer la protection contre les menaces, Microsoft Defender Antivirus utilise plusieurs méthodes. Ces méthodes incluent la protection fournie par le cloud, la protection en temps réel et les mises à jour de protection dédiées.

- La protection fournie par le cloud permet de détecter et de bloquer instantanément les menaces nouvelles et émergentes.
- L’analyse always on utilise la surveillance du comportement des fichiers et des processus et d’autres techniques (également appelées *protection en temps réel*).
- Les mises à jour de protection dédiées sont basées sur le Machine Learning, l’analyse du Big Data humaine et automatisée, ainsi que la recherche approfondie sur la résistance aux menaces. 

Pour en savoir plus sur les programmes malveillants et l’antivirus Microsoft Defender, consultez les articles suivants : 

- [Présentation des programmes malveillants & d’autres menaces](/windows/security/threat-protection/intelligence/understanding-malware)
- [Comment Microsoft identifie les programmes malveillants et les applications potentiellement indésirables](/windows/security/threat-protection/intelligence/criteria)
- [Protection de nouvelle génération dans Windows 10](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)

## <a name="what-happens-when-a-non-microsoft-antivirus-solution-is-used"></a>Que se passe-t-il lorsqu’une solution antivirus non Microsoft est utilisée ? 

Microsoft Defender Antivirus fait partie du système d’exploitation et est activé sur les appareils qui exécutent Windows 10. Toutefois, si vous utilisez une solution antivirus non Microsoft et que vous n’utilisez pas [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection), Microsoft Defender Antivirus passe automatiquement en mode désactivé.  

En mode désactivé, les utilisateurs et les clients peuvent toujours utiliser Microsoft Defender Antivirus pour les analyses planifiées ou à la demande afin d’identifier les menaces. Toutefois, Microsoft Defender Antivirus ne sera plus :

- être utilisé comme application antivirus par défaut.
- analyser activement les fichiers à la recherche de menaces.
- corriger ou résoudre les menaces.

Si vous désinstallez la solution antivirus non Microsoft, Microsoft Defender Antivirus passe automatiquement en mode actif pour protéger vos appareils Windows contre les menaces.

> [!TIP]
> - Si vous utilisez Microsoft 365, envisagez d’utiliser Microsoft Defender Antivirus comme solution antivirus principale. L’intégration peut fournir une meilleure protection. Voir [Mieux ensemble : antivirus Microsoft Defender et Office 365](/windows/security/threat-protection/microsoft-defender-antivirus/office-365-microsoft-defender-antivirus).
> - Veillez à maintenir Microsoft Defender Antivirus à jour, même si vous utilisez une solution antivirus non Microsoft.

## <a name="what-to-expect-when-threats-are-detected"></a>À quoi s’attendre quand des menaces sont détectées

Lorsque des menaces sont détectées par Microsoft Defender Antivirus, les événements suivants se produisent :

- Les [utilisateurs reçoivent des notifications dans Windows](https://support.microsoft.com/windows/8942c744-6198-fe56-4639-34320cf9444e). 
- Les détections sont répertoriées dans [l’application Sécurité Windows](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) dans la page **Historique de la protection**.  
- Si vous avez [sécurisé vos appareils Windows 10](../admin/setup/secure-win-10-pcs.md) et [que vous les avez inscrits dans Intune](/mem/intune/enrollment/windows-enrollment-methods) et que votre organisation compte 800 appareils ou moins inscrits, vous verrez des détections de menaces et des insights dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a> sur la page **Menaces et antivirus**, à laquelle vous pouvez accéder à partir de la **page Menaces et antivirus. Microsoft Defender carte Antivirus** sur la page **d’accueil** (ou dans le volet de **navigation en sélectionnant** > **Menaces pour l’intégrité & antivirus**).

    Si votre organisation compte plus de 800 appareils inscrits dans Intune, vous êtes invité à afficher les détections de menaces et les insights de [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) au lieu de la page **Menaces et antivirus**.
 
    > [!NOTE]
    > La **Microsoft Defender carte antivirus**, les **menaces et** la page antivirus sont déployées par phases. Vous n’avez donc peut-être pas accès immédiatement à celles-ci.

Dans la plupart des cas, les utilisateurs n’ont pas besoin d’effectuer d’autres actions. Dès qu’un fichier ou un programme malveillant est détecté sur un appareil, Microsoft Defender Antivirus le bloque et l’empêche de s’exécuter. De plus, les menaces nouvellement détectées sont ajoutées au moteur antivirus et anti-programme malveillant afin que d’autres appareils et utilisateurs soient également protégés.  

S’il existe une action qu’un utilisateur doit entreprendre, par exemple approuver la suppression d’un fichier malveillant, il le voit dans la notification qu’il reçoit. Pour en savoir plus sur les actions qu’Microsoft Defender Antivirus prend au nom d’un utilisateur, ou sur les actions que les utilisateurs peuvent avoir besoin d’effectuer, consultez [l’historique de protection](https://support.microsoft.com/office/f1e5fd95-09b4-46d1-b8c7-1059a1e09708). Pour savoir comment gérer les détections de menaces en tant que professionnel de l’informatique/administrateur, consultez [Examiner les menaces détectées et prendre des mesures](m365bp-review-threats-take-action.md).

Pour en savoir plus sur les différentes menaces, visitez le <a href="https://www.microsoft.com/wdsi/threats" target="_blank">site Renseignement de sécurité Microsoft Menaces</a>, où vous pouvez effectuer les actions suivantes : 

- Affichez les informations actuelles sur les principales menaces.
- Affichez les dernières menaces pour une région spécifique.
- Recherchez des détails sur une menace spécifique dans l’encyclopédie des menaces.

## <a name="related-content"></a>Contenu associé

[Sécuriser les appareils Windows](/misc/m365bp-secure-windows-devices) (article)\
[Évaluer Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/evaluate-microsoft-defender-antivirus) (article)\
[Comment activer la protection antivirus en temps réel et fournie par le cloud](/mem/intune/user-help/turn-on-defender-windows#turn-on-real-time-and-cloud-delivered-protection) (article)\
[Comment activer et utiliser Microsoft Defender Antivirus à partir de l’application Sécurité Windows](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-security-center-antivirus) (article)\
[Comment activer Microsoft Defender Antivirus à l’aide de stratégie de groupe](/mem/intune/user-help/turn-on-defender-windows#turn-on-windows-defender) (article)\
[Comment mettre à jour vos définitions antivirus](/mem/intune/user-help/turn-on-defender-windows#update-your-antivirus-definitions) (article)\
[Comment envoyer des programmes malveillants et non malveillants à Microsoft à des fins d’analyse](/microsoft-365/security/office-365-security/submitting-malware-and-non-malware-to-microsoft-for-analysis) (article)