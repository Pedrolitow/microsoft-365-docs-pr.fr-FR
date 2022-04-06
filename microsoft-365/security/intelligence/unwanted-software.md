---
title: Logiciels indésirables
ms.reviewer: ''
description: Découvrez comment les logiciels indésirables modifient vos paramètres par défaut sans votre consentement et ce que vous pouvez faire pour vous protéger.
keywords: sécurité, programmes malveillants, protection, logiciels indésirables, alter, infecter, logiciels indésirables, bundlers de logiciels, modificateurs de navigateur, confidentialité, sécurité, expérience informatique, prévention de l’infection, solution, WDSI, MMPC, Centre de protection Microsoft contre les programmes malveillants , menaces de recherche sur les virus, programmes malveillants de recherche, protection pc, infection par ordinateur, infection virale, descriptions, correction, menaces les plus récentes
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 654730571de934552d983e1135f24a3299567741
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666677"
---
# <a name="unwanted-software"></a>Logiciels indésirables

Les logiciels indésirables sont des programmes qui modifient l’expérience Windows sans votre consentement ou votre contrôle. Cela peut prendre la forme d’une expérience de navigation modifiée, d’un manque de contrôle sur les téléchargements et l’installation, de messages trompeurs ou de modifications non autorisées apportées à Windows paramètres.

## <a name="how-unwanted-software-works"></a>Fonctionnement des logiciels indésirables

Des logiciels indésirables peuvent être introduits lorsqu’un utilisateur recherche et télécharge des applications à partir d’Internet. Certaines applications sont des bundlers logiciels, ce qui signifie qu’elles sont empaquetées avec d’autres applications. Par conséquent, d’autres programmes peuvent être installés par inadvertance lors du téléchargement de l’application d’origine.

Voici quelques indications de logiciels indésirables :

- Il existe des programmes que vous n’avez pas installés et qui peuvent être difficiles à désinstaller

- Les fonctionnalités ou paramètres du navigateur ont changé, et vous ne pouvez pas les afficher ou les modifier

- Il existe des messages excessifs sur l’intégrité de votre appareil ou sur les fichiers et les programmes

- Il existe des publicités qui ne peuvent pas être facilement fermées

Certains indicateurs sont plus difficiles à reconnaître, car ils sont moins perturbateurs, mais sont toujours indésirables. Par exemple, les logiciels indésirables peuvent modifier des pages web pour afficher des publicités spécifiques, surveiller les activités de navigation ou supprimer le contrôle du navigateur.

Microsoft utilise un [critère d’évaluation](criteria.md) complet pour identifier les logiciels indésirables.

## <a name="how-to-protect-against-unwanted-software"></a>Comment se protéger contre les logiciels indésirables

Pour éviter toute infection logicielle indésirable, téléchargez les logiciels uniquement à partir de sites web officiels ou à partir de l’Microsoft Store. Méfiez-vous du téléchargement de logiciels à partir de sites tiers.

Utilisez [Microsoft Edge](/microsoft-edge/deploy/index) lors de la navigation sur Internet. Microsoft Edge inclut des protections supplémentaires qui bloquent efficacement les modificateurs de navigateur qui peuvent modifier les paramètres de votre navigateur. Microsoft Edge bloque également les sites web connus hébergeant des logiciels indésirables à l’aide [de Windows Defender SmartScreen](/microsoft-edge/deploy/index) (également utilisé par Internet Explorer).

Activez [Antivirus Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-in-windows-10) dans Windows 10. Il fournit une protection en temps réel contre les menaces et détecte et supprime les logiciels indésirables connus.

Téléchargez [Microsoft Security Essentials](https://www.microsoft.com/download/details.aspx?id=5201) pour une protection en temps réel dans Windows 7 ou Windows Vista.

Pour obtenir des conseils plus généraux, consultez [prévention de l’infection par les programmes malveillants](prevent-malware-infection.md).

### <a name="what-should-i-do-if-my-device-is-infected"></a>Que dois-je faire si mon appareil est infecté ? 

Si vous pensez avoir des logiciels indésirables, vous pouvez [soumettre des fichiers à des fins d’analyse](https://www.microsoft.com/wdsi/filesubmission).

Certains logiciels indésirables ajoutent des entrées de désinstallation, ce qui signifie que vous pouvez **les supprimer à l’aide de Paramètres**.
1. Sélectionnez le bouton Démarrer
2. Accédez aux **fonctionnalités Paramètres > Apps > Apps &**.
3. Sélectionnez l’application à désinstaller, puis cliquez sur **Désinstaller**.

Si vous n’avez remarqué que récemment des symptômes d’infection logicielle indésirable, envisagez de trier les applications par date d’installation, puis désinstallez les applications les plus récentes que vous n’avez pas installées.

Vous devrez **peut-être également supprimer les modules complémentaires de navigateur** dans vos navigateurs, tels qu’Internet Explorer, Firefox ou Chrome.

En cas d’échec de la suppression des menaces, consultez la [résolution des problèmes de détection et de suppression des programmes malveillants](https://support.microsoft.com/help/4466982/windows-10-troubleshoot-problems-with-detecting-and-removing-malware).