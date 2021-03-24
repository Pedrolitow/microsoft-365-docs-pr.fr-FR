---
title: Configurer une collection de certificats virtuelle - Exchange Online
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 04a616e6-197c-490c-ae8c-c8d5f0f0b3dd
description: Les administrateurs peuvent apprendre à créer une collection de certificats virtuelle qui sera utilisée pour valider les certificats S/MIME dans Exchange Online.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2a5dad897ce58b8496551535cc28e03c7a1fa964
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51064518"
---
# <a name="set-up-virtual-certificate-collection-in-exchange-online-to-validate-smime"></a>Configurer une collection de certificats virtuelle dans Exchange Online pour valider S/MIME

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


En tant qu’administrateur, vous devez configurer une collection de certificats virtuelle dans Exchange Online qui sera utilisée pour valider les certificats S/MIME. Cette collection de certificats virtuelle est définie en tant que magasin de certificats avec une extension de nom de fichier SST. Le fichier SST contient tous les certificats racine et intermédiaires utilisés lors de la validation d’un certificat S/MIME.

## <a name="create-and-save-an-sst"></a>Créer et enregistrer un fichier SST

Vous pouvez créer ce fichier de magasin de certificats SST en exportant les certificats à partir d’un ordinateur approuvé à l’aide de la cmdlet **Export-Certificate** dans Windows PowerShell et en spécifiant la valeur _Type_ en tant que SST. Pour obtenir des instructions, [voir Export-Certificate](/powershell/module/pkiclient/export-certificate).

Une fois que vous avez le fichier du magasin de certificats SST, utilisez la syntaxe suivante dans Exchange Online PowerShell pour enregistrer le contenu du fichier SST dans le magasin de certificats virtuel Exchange Online. Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

```PowerShell
Set-SmimeConfig -SMIMECertificateIssuingCA (Get-Content <FileNameAndPath>.sst -Encoding Byte)
```

Cet exemple importe le fichier SST C:\My Documents\Exported Certificate Store.sst.

```PowerShell
Set-SmimeConfig -SMIMECertificateIssuingCA (Get-Content "C:\My Documents\Exported Certificate Store.sst" -Encoding Byte)
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-SmimeConfig](/powershell/module/exchange/set-smimeconfig).

## <a name="ensuring-a-certificate-is-valid"></a>S’assurer de la validité d’un certificat

Dans Exchange Online, seul le SST est utilisé pour la validation de certificat.

## <a name="more-information"></a>Informations supplémentaires

[S/MIME pour la signature et le chiffrement des messages](s-mime-for-message-signing-and-encryption.md)

[Get-SmimeConfig](/powershell/module/exchange/get-smimeconfig)