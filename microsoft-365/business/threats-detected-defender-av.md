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
description: Découvrez comment l’antivirus Microsoft Defender protège vos appareils Windows contre les menaces logicielles, telles que les virus, les logiciels malveillants et les logiciels espions.
ms.openlocfilehash: e3c8a1071625bba41af5f3cccd50f8484acac18d
ms.sourcegitcommit: 20d1158c54a5058093eb8aac23d7e4dc68054688
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "49376688"
---
# <a name="threats-detected-by-microsoft-defender-antivirus"></a>Menaces détectées par l’antivirus Microsoft Defender

L’antivirus Microsoft Defender protège vos appareils Windows contre les menaces logicielles, telles que les virus, les logiciels malveillants et les logiciels espions.

- Les virus se propagent généralement en attachant leur code à d’autres fichiers sur votre appareil ou votre réseau et peuvent entraîner un fonctionnement incorrect des programmes infectés.
- Les programmes malveillants incluent des fichiers, des applications et du code malveillants qui peuvent causer des dommages et perturbent l’utilisation normale des appareils. De plus, les logiciels malveillants peuvent autoriser l’accès non autorisé, utiliser les ressources système, voler des mots de passe et des informations de compte, vous empêcher de vous connecter à votre ordinateur et demander des ransomware, et bien plus encore.
- Les logiciels espions collectent des données, telles que l’activité de navigation sur le Web, et envoient les données à des serveurs distants.
 
Pour assurer la protection contre les menaces, l’antivirus Microsoft Defender utilise plusieurs méthodes. Ces méthodes incluent la protection en nuage fournie, la protection en temps réel et les mises à jour de protection dédiées.

- La protection assurée sur le Cloud permet de détecter et de bloquer presque instantanément les menaces nouvelles et émergentes.
- L’analyse permanente utilise la surveillance du comportement des fichiers et des processus, ainsi que d’autres techniques (également connues sous le nom de *protection en temps réel*).
- Les mises à jour dédiées de la protection sont basées sur l’apprentissage automatique, l’analyse des données à grande vue humaine et automatisée, ainsi que la recherche approfondie de la résistance aux menaces. 

Pour en savoir plus sur les programmes malveillants et l’antivirus Microsoft Defender, consultez les articles suivants : 

- [Présentation des programmes malveillants & autres menaces](/windows/security/threat-protection/intelligence/understanding-malware)
- [Comment Microsoft identifie les programmes malveillants et les applications potentiellement indésirables](/windows/security/threat-protection/intelligence/criteria)
- [Protection de nouvelle génération dans Windows 10](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)

## <a name="what-happens-when-a-non-microsoft-antivirus-solution-is-used"></a>Que se passe-t-il lorsqu’une solution antivirus non-Microsoft est utilisée ? 

L’antivirus Microsoft Defender fait partie du système d’exploitation et est activé sur les appareils exécutant Windows 10. Toutefois, si vous utilisez une solution antivirus non-Microsoft et que vous n’utilisez pas [Microsoft Defender pour le point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection), l’antivirus Microsoft Defender passe automatiquement en mode désactivé.  

En mode désactivé, les utilisateurs et les clients peuvent toujours utiliser l’antivirus Microsoft Defender pour les analyses planifiées ou à la demande afin d’identifier les menaces ; Toutefois, l’antivirus Microsoft Defender ne sera plus :

- être utilisé comme application antivirus par défaut.
- Analysez activement les fichiers contre les menaces.
- corriger ou résoudre les menaces.

Si vous désinstallez la solution antivirus non-Microsoft, l’antivirus Microsoft Defender passe automatiquement en mode actif pour protéger vos appareils Windows des menaces.

> [!TIP]
> - Si vous utilisez Microsoft 365, envisagez d’utiliser l’antivirus Microsoft Defender comme solution antivirus principale. L’intégration peut offrir une meilleure protection. Consultez l' [ensemble : antivirus Microsoft Defender et Office 365](/windows/security/threat-protection/microsoft-defender-antivirus/office-365-microsoft-defender-antivirus).
> - Veillez à ce que le logiciel antivirus Microsoft Defender soit à jour, même si vous utilisez une solution antivirus non-Microsoft.

## <a name="what-to-expect-when-threats-are-detected"></a>Ce qu’il faut attendre en cas de détection de menaces

Lorsque des menaces sont détectées par l’antivirus Microsoft Defender, les événements suivants se produisent :

- Les utilisateurs reçoivent [des notifications dans Windows](https://support.microsoft.com/windows/8942c744-6198-fe56-4639-34320cf9444e). 
- Les détections sont répertoriées dans l' [application de sécurité Windows](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) sur la page historique de la **protection** .  
- Si vous avez [sécurisé vos appareils Windows 10](secure-win-10-pcs.md) et [les avez affichés dans Intune](/mem/intune/enrollment/windows-enrollment-methods), vous verrez des détections et des informations sur les menaces dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration 365 de Microsoft</a> sur la page **menaces actives** , à laquelle vous pouvez accéder à partir de la carte **antivirus Microsoft Defender** sur la page d' **Accueil** (ou à partir du volet de navigation en sélectionnant menaces d' **intégrité**  >  **& antivirus**).
    > [!NOTE]
    > La page de la carte **antivirus Microsoft Defender** et **les menaces actives** sont déployées en plusieurs phases, de sorte que vous ne pouvez pas y accéder immédiatement.

Dans la plupart des cas, les utilisateurs n’ont pas besoin d’effectuer d’autres actions. Dès qu’un fichier ou programme malveillant est détecté sur un appareil, l’antivirus Microsoft Defender l’bloque et l’empêche de s’exécuter. De plus, les menaces nouvellement détectées sont ajoutées au moteur antivirus et anti-programme malveillant afin que d’autres appareils et utilisateurs soient également protégés.  

S’il existe une action qu’un utilisateur doit effectuer, telle que l’approbation de la suppression d’un fichier malveillant, il voit que, dans la notification qu’il reçoit. Pour en savoir plus sur les actions que l’antivirus Microsoft Defender prend pour le compte d’un utilisateur, ou les actions que les utilisateurs peuvent avoir besoin de prendre, consultez la rubrique [historique des protections](https://support.microsoft.com/office/f1e5fd95-09b4-46d1-b8c7-1059a1e09708). Pour en savoir plus sur la gestion des menaces détectées en tant que professionnel de l’informatique/administrateur, consultez la rubrique [Review detected Threats et take action](review-threats-take-action.md).

Pour en savoir plus sur les différentes menaces, visitez le <a href="https://www.microsoft.com/wdsi/threats" target="_blank">site des menaces de sécurité Microsoft</a>, où vous pouvez effectuer les actions suivantes : 

- Affichez les informations actuelles sur les principales menaces.
- Affichez les dernières menaces pour une région spécifique.
- Pour plus d’informations sur une menace spécifique, consultez l’Encyclopédie des menaces.

## <a name="related-content"></a>Contenu connexe

[Sécuriser les appareils Windows 10](secure-windows-10-devices.md) (article) \
[Évaluation de l’antivirus Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/evaluate-microsoft-defender-antivirus) (article) \
[Comment activer la protection antivirus en temps réel et sur le Cloud](/mem/intune/user-help/turn-on-defender-windows#turn-on-real-time-and-cloud-delivered-protection) (article) \
[Comment activer et utiliser l’antivirus Microsoft Defender à partir de l’application de sécurité Windows](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-security-center-antivirus) (article) \
[Activation de l’antivirus Microsoft Defender à l’aide de la stratégie de groupe](/mem/intune/user-help/turn-on-defender-windows#turn-on-windows-defender) (article) \
[Mise à jour de vos définitions d’antivirus](/mem/intune/user-help/turn-on-defender-windows#update-your-antivirus-definitions) (article) \
[Procédure d’envoi de programmes malveillants et autres programmes malveillants à Microsoft pour analyse](/microsoft-365/security/office-365-security/submitting-malware-and-non-malware-to-microsoft-for-analysis) (article)