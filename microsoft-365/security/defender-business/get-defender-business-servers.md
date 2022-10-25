---
title: Obtenir des serveurs Microsoft Defender pour entreprises
description: Découvrez comment obtenir Microsoft Defender pour entreprises serveurs, actuellement en préversion.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.service: microsoft-365-security
ms.subservice: mdb
ms.localizationpriority: none
ms.date: 08/11/2022
ms.collection:
- SMB
- m365-security
- tier1
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.openlocfilehash: 111b3e7cd4de996b6c263312acf4368d872e7a50
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68687565"
---
# <a name="how-to-get-microsoft-defender-for-business-servers-preview"></a>Comment obtenir des serveurs Microsoft Defender pour entreprises (préversion)

> [!IMPORTANT]
> Si vous envisagez d’intégrer une instance de Windows Server ou Linux Server, vous aurez besoin d’une licence supplémentaire, telle que Microsoft Defender pour entreprises serveurs (préversion). Vous pouvez également utiliser [Microsoft Defender pour les serveurs](/azure/defender-for-cloud/defender-for-servers-introduction). Toutefois, votre expérience Defender entreprise peut changer lorsque vous ajoutez un plan d’entreprise, tel que Defender pour les serveurs Plan 1 ou Plan 2. Pour plus d’informations, consultez [Que se passe-t-il si j’ai une combinaison d’abonnements de sécurité de point de terminaison Microsoft ?](mdb-faq.yml#what-happens-if-i-have-a-mix-of-microsoft-endpoint-security-subscriptions) et [Intégrer des appareils à Microsoft Defender pour entreprises](mdb-onboard-devices.md).

Microsoft Defender pour entreprises serveurs (préversion) vous permet d’intégrer un appareil exécutant Windows Server ou Linux Server à Defender for Business ou Microsoft 365 Business Premium. Lorsque la licence des serveurs Microsoft Defender pour entreprises devient en disponibilité générale, vous avez besoin d’une licence pour chaque instance de serveur.

**Voici comment obtenir Microsoft Defender pour entreprises serveurs (préversion)** :

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous. 

2. Activer les paramètres d’aperçu. 

   1. Dans le volet de navigation, sélectionnez **Paramètres Points** \> **de terminaison** **Fonctionnalités avancées** \> \> **Fonctionnalités en préversion**. 
   2. Définissez le paramètre sur **Activé**, puis sélectionnez **Enregistrer les préférences**.

3. Activez l’étendue d’application pour Windows Server. 

   1. Accédez à **Paramètres Points** \> **de terminaison** \> **Gestion de la configuration** \> **Étendue de l’application**. 
   2. Sélectionnez **Utiliser MDE pour appliquer les paramètres de configuration de sécurité à partir de MEM**, sélectionnez  **Windows Server**, puis **sélectionnez Enregistrer**.

4. Suivez les instructions pour Windows Server et Linux Server dans [Intégrer des appareils à Microsoft Defender pour entreprises](mdb-onboard-devices.md).

> [!IMPORTANT]
> Microsoft Defender pour entreprises serveurs est actuellement en préversion. Lorsqu’il devient en disponibilité générale, il est proposé en tant que module complémentaire pour Microsoft 365 Business Premium et la version autonome de Defender pour Les Entreprises. En disponibilité générale, Microsoft Defender pour entreprises serveurs sont facturés à 3 $ par instance de serveur.

## <a name="see-also"></a>Voir aussi

- [Consultez le guide de l’utilisateur d’évaluation : Microsoft Defender pour entreprises](trial-playbook-defender-business.md).
- [Utilisez l’Assistant Installation dans Microsoft Defender pour entreprises](mdb-use-wizard.md).
- [Consultez le processus d’installation et de configuration de Defender pour Entreprise](mdb-setup-configuration.md).
- [Découvrez comment obtenir de l’aide et du support pour Defender pour les entreprises](mdb-get-help.md) (au cas où vous en avez besoin).