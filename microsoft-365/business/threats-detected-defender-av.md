---
title: Menaces détectées par l’antivirus Microsoft Defender
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid: MET150
description: Découvrez comment l’Antivirus Microsoft Defender protège vos appareils Windows contre les menaces logicielles, telles que les virus, les programmes malveillants et les logiciels espions.
ms.openlocfilehash: ce88e4f7b1caf3a98ebd6dc56d66f0d0fc99a9ad
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50912429"
---
# <a name="threats-detected-by-microsoft-defender-antivirus"></a>Menaces détectées par l’antivirus Microsoft Defender

L’Antivirus Microsoft Defender protège vos appareils Windows contre les menaces logicielles, telles que les virus, les programmes malveillants et les logiciels espions.

- Les virus se propagent généralement en attachant leur code à d’autres fichiers sur votre appareil ou votre réseau et peuvent entraîner un mauvais travail des programmes infectés.
- Les programmes malveillants incluent des fichiers malveillants, des applications et du code qui peuvent causer des dommages et interrompre l’utilisation normale des appareils. En outre, les programmes malveillants peuvent autoriser l’accès non autorisé, utiliser des ressources système, voler des mots de passe et des informations de compte, vous verrouiller de votre ordinateur et demander une rançon, et bien plus encore.
- Les logiciels espions collectent des données, telles que l’activité de navigation web, et envoient les données aux serveurs distants.
 
Pour fournir une protection contre les menaces, l’Antivirus Microsoft Defender utilise plusieurs méthodes. Ces méthodes incluent la protection cloud, la protection en temps réel et les mises à jour de protection dédiées.

- La protection fournie par le cloud permet de détecter et de bloquer quasi instantanément les menaces nouvelles et émergentes.
- L’analyse toujours en cours utilise la surveillance du comportement des fichiers et des processus, ainsi que d’autres techniques (également *appelées protection en temps réel).*
- Les mises à jour dédiées à la protection sont basées sur l’apprentissage automatique, l’analyse humaine et automatisée du Big Data et la recherche approfondie de résistance aux menaces. 

Pour en savoir plus sur les programmes malveillants et l’Antivirus Microsoft Defender, consultez les articles suivants : 

- [Comprendre les programmes malveillants & autres menaces](/windows/security/threat-protection/intelligence/understanding-malware)
- [Comment Microsoft identifie les programmes malveillants et les applications potentiellement indésirables](/windows/security/threat-protection/intelligence/criteria)
- [Protection nouvelle génération dans Windows 10](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)

## <a name="what-happens-when-a-non-microsoft-antivirus-solution-is-used"></a>Que se passe-t-il lorsqu’une solution antivirus non Microsoft est utilisée ? 

L’Antivirus Microsoft Defender fait partie du système d’exploitation et est activé sur les appareils exécutant Windows 10. Toutefois, si vous utilisez une solution antivirus non Microsoft et que vous n’utilisez pas [Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)pour le point de terminaison, l’Antivirus Microsoft Defender passe automatiquement en mode désactivé.  

En mode désactivé, les utilisateurs et les clients peuvent toujours utiliser l’Antivirus Microsoft Defender pour les analyses programmées ou à la demande afin d’identifier les menaces . Toutefois, l’Antivirus Microsoft Defender ne :

- être utilisé comme application antivirus par défaut.
- analyser activement les fichiers à la recherche de menaces;
- corriger ou résoudre les menaces.

Si vous désinstallez la solution antivirus non Microsoft, l’Antivirus Microsoft Defender passe automatiquement en mode actif pour protéger vos appareils Windows contre les menaces.

> [!TIP]
> - Si vous utilisez Microsoft 365, envisagez d’utiliser l’Antivirus Microsoft Defender comme solution antivirus principale. L’intégration peut fournir une meilleure protection. Voir [mieux ensemble : Antivirus Microsoft Defender et Office 365](/windows/security/threat-protection/microsoft-defender-antivirus/office-365-microsoft-defender-antivirus).
> - Veillez à maintenir l’Antivirus Microsoft Defender à jour, même si vous utilisez une solution antivirus non Microsoft.

## <a name="what-to-expect-when-threats-are-detected"></a>À quoi s’attendre lorsque des menaces sont détectées

Lorsque des menaces sont détectées par l’Antivirus Microsoft Defender, les choses suivantes se produisent :

- Les [utilisateurs reçoivent des notifications dans Windows.](https://support.microsoft.com/windows/8942c744-6198-fe56-4639-34320cf9444e) 
- Les détections sont répertoriées dans l’application [Sécurité Windows](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) dans la page Historique **de la** protection.  
- Si vous avez sécurisé vos appareils Windows [10](secure-win-10-pcs.md) et les avez inscrits dans [Intune](/mem/intune/enrollment/windows-enrollment-methods)et que votre organisation compte au moins 800 appareils inscrits, vous verrez les détections de menaces et les informations dans le Centre d’administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365</a> sur la page Menaces et **antivirus,** à laquelle vous pouvez accéder à partir de la carte **antivirus Microsoft Defender** sur la **page** d’accueil (ou dans le volet de navigation en sélectionnant un antivirus & menaces d’état).   >  

    Si votre organisation compte plus de 800 appareils inscrits dans Intune, vous serez invité à afficher les détections et les informations sur les menaces à partir de [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) au lieu de la page Menaces et **antivirus.**
 
    > [!NOTE]
    > La carte **antivirus Microsoft Defender** et la page Menaces et **antivirus** sont déployés par phases, de sorte que vous n’avez peut-être pas un accès immédiat à ces cartes.

Dans la plupart des cas, les utilisateurs n’ont pas besoin de prendre d’autres mesures. Dès qu’un fichier ou un programme malveillant est détecté sur un appareil, l’Antivirus Microsoft Defender le bloque et l’empêche de s’exécute. De plus, les menaces nouvellement détectées sont ajoutées au moteur antivirus et anti-programme malveillant afin que les autres appareils et utilisateurs soient également protégés.  

S’il existe une action qu’un utilisateur doit prendre, par exemple approuver la suppression d’un fichier malveillant, il le verra dans la notification qu’il reçoit. Pour en savoir plus sur les actions que l’Antivirus Microsoft Defender prend pour le compte d’un utilisateur, ou sur les actions que les utilisateurs devront peut-être prendre, consultez l’historique [de la protection.](https://support.microsoft.com/office/f1e5fd95-09b4-46d1-b8c7-1059a1e09708) Pour découvrir comment gérer les détections de menaces en tant que professionnel de l’informatique/administrateur, voir Examiner les menaces détectées [et prendre des mesures.](review-threats-take-action.md)

Pour en savoir plus sur les différentes menaces, visitez le <a href="https://www.microsoft.com/wdsi/threats" target="_blank">site Microsoft Security Intelligence Threats</a>, où vous pouvez effectuer les actions suivantes : 

- Afficher les informations actuelles sur les principales menaces.
- Afficher les dernières menaces pour une région spécifique.
- Recherchez des détails sur une menace spécifique dans la menace.

## <a name="related-content"></a>Contenu connexe

[Sécuriser les appareils Windows 10](secure-windows-10-devices.md) (article)\
[Évaluer l’Antivirus Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/evaluate-microsoft-defender-antivirus) (article)\
[Comment activer la protection](/mem/intune/user-help/turn-on-defender-windows#turn-on-real-time-and-cloud-delivered-protection) antivirus en temps réel et dans le cloud (article)\
[Comment activer et utiliser l’Antivirus Microsoft Defender à partir de l’application Sécurité Windows](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-security-center-antivirus) (article)\
[Comment activer l’Antivirus Microsoft Defender à l’aide de la stratégie de groupe](/mem/intune/user-help/turn-on-defender-windows#turn-on-windows-defender) (article)\
[Comment mettre à jour vos définitions antivirus](/mem/intune/user-help/turn-on-defender-windows#update-your-antivirus-definitions) (article)\
[Comment soumettre des programmes malveillants et non malveillants à Microsoft pour analyse](../security/office-365-security/submitting-malware-and-non-malware-to-microsoft-for-analysis.md) (article)