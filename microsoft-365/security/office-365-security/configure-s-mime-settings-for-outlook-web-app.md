---
title: Configurer les paramètres S/MIME - Exchange Online pour Outlook sur le web
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: c7dee22c-9b5b-425c-91a9-d093204ff84e
ms.collection:
- M365-security-compliance
description: Brève description de ce que les administrateurs Exchange Online doivent faire pour afficher et configurer les paramètres S/MIME dans Outlook sur le web dans Exchange Online.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a81db5ec933f1d0d6e2944103be53c0169dde62f
ms.sourcegitcommit: a1846b1ee2e4fa397e39c1271c997fc4cf6d5619
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2021
ms.locfileid: "50165678"
---
# <a name="configure-smime-settings-in-exchange-online-for-outlook-on-the-web"></a>Configurer les paramètres S/MIME dans Exchange Online pour Outlook sur le web

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](https://go.microsoft.com/fwlink/?linkid=2148611)
- [Microsoft Defender pour Office 365 plan 1 et plan 2](https://go.microsoft.com/fwlink/?linkid=2148715)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

En tant qu’administrateur d’Exchange Online, vous pouvez configurer Outlook sur le web (anciennement Outlook Web App) pour autoriser l’envoi et la réception de messages protégés par S/MIME. Utilisez les cmdlets **Get-SmimeConfig** et **Set-SmimeConfig** pour afficher et gérer cette fonctionnalité dans Exchange Online PowerShell. Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-SmimeConfig](https://docs.microsoft.com/powershell/module/exchange/get-smimeconfig) et [Set-SmimeConfig](https://docs.microsoft.com/powershell/module/exchange/set-smimeconfig).

## <a name="considerations-for-new-microsoft-edge-chromium-based"></a>Considérations pour le nouveau Microsoft Edge (basé sur Chromium)

Pour utiliser S/MIME dans Outlook sur le web dans le nouveau navigateur web [Microsoft Edge,](https://www.microsoft.com/windows/microsoft-edge) vous (ou un autre administrateur) devez définir et configurer la stratégie de navigateur Microsoft Edge nommée **ExtensionInstallForcelist** pour installer l’extension Microsoft S/MIME dans le nouveau Microsoft Edge. La valeur de stratégie est `maafgiompdekodanheihhgilkjchcakm;https://outlook.office.com/owa/SmimeCrxUpdate.ashx` . Notez également que l’application de cette stratégie nécessite des appareils joints à un domaine ou à Azure AD. L’utilisation de S/MIME dans le nouveau navigateur Microsoft Edge nécessite donc effectivement des appareils joints à un domaine ou à Azure AD.

Pour plus d’informations **sur la stratégie ExtensionInstallForcelist,** voir [ExtensionInstallForcelist](https://docs.microsoft.com/DeployEdge/microsoft-edge-policies#extensioninstallforcelist).

Cette étape est une condition préalable à l’utilisation du nouveau Microsoft Edge . Il ne remplace pas le contrôle S/MIME installé par les utilisateurs. Les utilisateurs sont invités à télécharger et installer le contrôle S/MIME dans Outlook sur le web lors de leur première utilisation de S/MIME. Les utilisateurs peuvent également se rendre de manière proactive sur **S/MIME** dans leurs paramètres Outlook sur le web pour obtenir le lien de téléchargement du contrôle.

## <a name="considerations-for-chrome"></a>Considérations pour Chrome

Pour utiliser S/MIME dans Outlook sur le web dans le navigateur web Google Chrome, vous (ou un autre administrateur) devez définir et configurer la stratégie Chromium nommée **ExtensionInstallForcelist** pour installer l’extension Microsoft S/MIME dans Chrome. La valeur de stratégie est `maafgiompdekodanheihhgilkjchcakm;https://outlook.office.com/owa/SmimeCrxUpdate.ashx` . Notez également que l’application de cette stratégie nécessite des ordinateurs joints à un domaine, de sorte que l’utilisation de S/MIME dans Chrome nécessite effectivement des ordinateurs joints à un domaine.

Pour plus d’informations **sur la stratégie ExtensionInstallForcelist,** voir [ExtensionInstallForcelist](https://cloud.google.com/docs/chrome-enterprise/policies/?policy=ExtensionInstallForcelist).

Cette étape est une condition préalable à l’utilisation de Chrome ; Il ne remplace pas le contrôle S/MIME installé par les utilisateurs. Les utilisateurs sont invités à télécharger et installer le contrôle S/MIME dans Outlook sur le web lors de leur première utilisation de S/MIME. Les utilisateurs peuvent également se rendre de manière proactive sur **S/MIME** dans leurs paramètres Outlook sur le web pour obtenir le lien de téléchargement du contrôle.

## <a name="for-more-information"></a>Pour plus d'informations

[S/MIME pour la signature et le chiffrement des messages](s-mime-for-message-signing-and-encryption.md)
