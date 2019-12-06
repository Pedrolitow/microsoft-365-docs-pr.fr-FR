---
title: Configurer les paramètres S/MIME dans Exchange Online pour Outlook sur le Web
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: c7dee22c-9b5b-425c-91a9-d093204ff84e
ms.collection:
- M365-security-compliance
description: Brève description des administrateurs Exchange Online à faire pour afficher et configurer les paramètres S/MIME dans Outlook sur le Web dans Exchange Online.
ms.openlocfilehash: 759e48544e9c9dedca15500edb56e9111987bf93
ms.sourcegitcommit: ba223b4fd069fc6fd09c2a2e34c770a18bc7b2a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "39866336"
---
# <a name="configure-smime-settings-in-exchange-online-for-outlook-on-the-web"></a>Configurer les paramètres S/MIME dans Exchange Online pour Outlook sur le Web

En tant qu’administrateur d’Exchange Online, vous pouvez configurer Outlook sur le Web (anciennement Outlook Web App) pour permettre l’envoi et la réception de messages protégés par S/MIME. Utilisez les cmdlets **Get-SmimeConfig** et **Set-SmimeConfig** pour afficher et gérer cette fonctionnalité dans Exchange Online PowerShell. Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554).

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-SmimeConfig](https://docs.microsoft.com/powershell/module/exchange/encryption-and-certificates/get-smimeconfig) et [Set-SmimeConfig](https://docs.microsoft.com/powershell/module/exchange/encryption-and-certificates/set-smimeconfig).

## <a name="considerations-for-chrome"></a>Considérations relatives au chrome

Pour utiliser S/MIME dans Outlook sur le Web dans le navigateur Web Google Chrome, vous (ou un autre administrateur) devez définir et configurer la stratégie de chrome nommée **ExtensionInstallForcelist** pour installer l’extension S/MIME Microsoft dans Chrome. La valeur de la `maafgiompdekodanheihhgilkjchcakm;https://outlook.office.com/owa/SmimeCrxUpdate.ashx`stratégie est. Et notez que l’application de cette stratégie nécessite des ordinateurs associés à un domaine, de sorte que l’utilisation de S/MIME dans Chrome requiert effectivement des ordinateurs liés à un domaine.

Pour plus d’informations sur la stratégie **ExtensionInstallForcelist** , voir [ExtensionInstallForcelist](https://dev.chromium.org/administrators/policy-list-3#ExtensionInstallForcelist).

Cette étape est requise pour utiliser Chrome ; il ne remplace pas le contrôle S/MIME qui est installé par les utilisateurs. Les utilisateurs sont invités à télécharger et à installer le contrôle S/MIME dans Outlook sur le Web lors de leur première utilisation de S/MIME. Ou, les utilisateurs peuvent accéder de manière proactive à **S/MIME** dans leurs paramètres Outlook sur le Web pour obtenir le lien de téléchargement pour le contrôle.

## <a name="for-more-information"></a>Pour plus d’informations

[S/MIME pour la signature et le chiffrement des messages](s-mime-for-message-signing-and-encryption.md)
