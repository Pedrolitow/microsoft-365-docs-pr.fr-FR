---
title: Obtenir des serveurs Microsoft Defender pour entreprises
description: Découvrez comment obtenir Microsoft Defender pour entreprises serveurs, actuellement en préversion.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: none
ms.date: 08/11/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-security-compliance
ms.openlocfilehash: 55e429351a45b461d8a55dfcebe56a17cf6ef35e
ms.sourcegitcommit: 9b10e56b9e83f3a80757fa6108bebd1d80cf4178
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67320321"
---
# <a name="how-to-get-microsoft-defender-for-business-servers-preview"></a>Comment obtenir des serveurs Microsoft Defender pour entreprises (préversion)

Microsoft Defender pour entreprises serveurs (préversion) vous permet d’intégrer un appareil exécutant Windows Server ou Linux Server à Defender entreprise ou Microsoft 365 Business Premium. Lorsque la licence des serveurs Microsoft Defender pour entreprises devient généralement disponible, vous avez besoin d’une licence pour chaque instance de serveur.

Voici comment obtenir Microsoft Defender pour entreprises serveurs (préversion) :

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous. 

2. Activez les paramètres d’aperçu. 

   1. Dans le volet de navigation, sélectionnez **Paramètres Points** \> de **terminaison Fonctionnalités avancées Fonctionnalités** \>  \> **en préversion**. 
   2. Activez le **paramètre, puis** **sélectionnez Enregistrer les préférences**.

3. Activez l’étendue d’application pour Windows Server. 

   1. Accédez à **l’étendue d’application** de **la gestion de la configuration** \> **des paramètres** \>  \> des points de terminaison. 
   2. Sélectionnez **Utiliser MDE pour appliquer les paramètres de configuration de sécurité à partir de MEM**, sélectionnez  **Windows Server**, puis **sélectionnez Enregistrer**.

4. Suivez les instructions relatives à Windows Server et Linux Server dans [les appareils intégrés pour Microsoft Defender pour entreprises](mdb-onboard-devices.md).

> [!IMPORTANT]
> Microsoft Defender pour entreprises serveurs est actuellement en préversion. Lorsqu’il sera mis à la disposition générale, il sera proposé en tant que module complémentaire à Microsoft 365 Business Premium et à la version autonome de Defender for Business. En disponibilité générale, Microsoft Defender pour entreprises serveurs sont facturés à 3 $ par instance de serveur.

## <a name="see-also"></a>Voir aussi

- [Consultez le playbook d’évaluation : Microsoft Defender pour entreprises](trial-playbook-defender-business.md).
- [Utilisez l’Assistant Installation dans Microsoft Defender pour entreprises](mdb-use-wizard.md).
- [Consultez le processus d’installation et de configuration pour Defender Entreprise](mdb-setup-configuration.md).
- [Découvrez comment obtenir de l’aide et du support pour Defender Entreprise](mdb-get-help.md) (au cas où vous ayiez besoin d’aide).