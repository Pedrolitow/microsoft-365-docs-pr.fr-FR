---
title: À propos de l’empreinte digitale de document
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: ITPro
ms.topic: article
search.appverid: MET150
ms.service: exchange-online
ms.collection: M365-security-compliance
ms.localizationpriority: medium
description: Les professionnels de l'informatique de votre organisation gèrent toutes sortes d'informations sensibles au cours d'une journée typique. La création d'une empreinte numérique de document facilite la protection de ces informations en identifiant les formulaires standard utilisés au sein de votre organisation. Cette rubrique décrit les concepts sous-jacents à l’empreinte digitale de document et explique comment en créer un à l’aide de PowerShell.
ms.openlocfilehash: 1ad29126783b9d824789b06020b8f925be00ffbb
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627622"
---
# <a name="document-fingerprinting"></a>Création d’une empreinte numérique de document

Les professionnels de l'informatique de votre organisation gèrent toutes sortes d'informations sensibles au cours d'une journée typique. Dans le portail de conformité Microsoft Purview, l’empreinte digitale de document vous permet de protéger plus facilement ces informations en identifiant les formulaires standard utilisés dans toute votre organisation. Cette rubrique décrit les concepts sous-jacents à l’empreinte digitale de document et explique comment en créer un à l’aide de PowerShell.

## <a name="basic-scenario-for-document-fingerprinting"></a>Scénario de base de création d’une empreinte numérique de document

L’empreinte digitale de document est une fonctionnalité Protection contre la perte de données Microsoft Purview (DLP) qui convertit un formulaire standard en un type d’informations sensibles, que vous pouvez utiliser dans les règles de vos stratégies DLP. Par exemple, vous pouvez créer une empreinte numérique de document basée sur un modèle de brevet vierge, puis créer une stratégie DLP qui détecte et bloque tous les modèles de brevet sortants comportant des informations sensibles. Si vous le souhaitez, vous pouvez configurer [des conseils de stratégie](use-notifications-and-policy-tips.md) pour informer les expéditeurs qu’ils peuvent envoyer des informations sensibles, et l’expéditeur doit vérifier que les destinataires sont qualifiés pour recevoir les brevets. Ce processus fonctionne avec n'importe quel formulaire texte utilisé dans votre organisation. Voici d'autres exemples de formulaires que vous pouvez télécharger :

- Formulaires officiels
- Formulaires de conformité relatifs à la loi américaine HIPAA (Health Insurance Portability Accountability Act)
- Formulaires d'informations sur les employés pour les services de ressources humaines
- Formulaires personnalisés créés spécialement pour votre organisation

Dans l'idéal, votre organisation a pour habitude professionnelle d'utiliser certains formulaires pour la transmission d'informations sensibles. Une fois que vous avez chargé un formulaire vide à convertir en empreinte digitale de document et configuré une stratégie correspondante, la DLP détecte tous les documents dans le courrier sortant qui correspondent à cette empreinte digitale.

## <a name="how-document-fingerprinting-works"></a>Fonctionnement de l’empreinte numérique de document

Vous avez probablement déjà deviné que les documents n'ont pas d'empreintes digitales réelles, mais le nom contribue à expliquer la fonctionnalité. De la même manière que les empreintes digitales d'une personne répondent à des modèles uniques, les documents répondent à des modèles de mots uniques. Lorsque vous chargez un fichier, DLP identifie le modèle de mot unique dans le document, crée une empreinte digitale de document basée sur ce modèle et utilise cette empreinte digitale de document pour détecter les documents sortants contenant le même modèle. C'est pourquoi le téléchargement d'un formulaire ou d'un modèle permet de créer le type d'empreinte numérique de document le plus efficace. Toute personne qui remplit un formulaire utilise le même ensemble de mots d'origine, puis ajoute ses propres mots au document. Tant que le document sortant n’est pas protégé par mot de passe et contient tout le texte du formulaire d’origine, DLP peut déterminer si le document correspond à l’empreinte digitale du document.

> [!IMPORTANT]
> Pour l’instant, DLP peut utiliser l’empreinte digitale de document comme méthode de détection dans Exchange Online uniquement.

L’exemple suivant montre ce qui se passe si vous créez une empreinte numérique de document basée sur un modèle de brevet, mais vous pouvez utiliser n’importe quel formulaire comme base pour la création d’une empreinte numérique de document.

### <a name="example-of-a-patent-document-matching-a-document-fingerprint-of-a-patent-template"></a>Exemple d’un document de brevet correspondant à l’empreinte numérique de document d’un modèle de brevet

![Diagramme de l’empreinte digitale du document.](../media/Document-Fingerprinting-diagram.png)

Le modèle de brevet contient les champs vides « Titre du brevet », « Inventeurs » et « Description » et les descriptions de chacun de ces champs, c’est-à-dire le modèle de mot. Lorsque vous chargez le modèle de brevet d’origine, il se trouve dans l’un des types de fichiers pris en charge et en texte brut. DLP convertit ce modèle de mot en empreinte digitale de document, qui est un petit fichier XML Unicode contenant une valeur de hachage unique représentant le texte d’origine, et l’empreinte digitale est enregistrée en tant que classification des données dans Active Directory. (Par mesure de sécurité, le document d’origine lui-même n’est pas stocké sur le service ; seule la valeur de hachage est stockée et le document d’origine ne peut pas être reconstruit à partir de la valeur de hachage.) L’empreinte digitale du brevet devient alors un type d’informations sensibles que vous pouvez associer à une stratégie DLP. Une fois que vous avez associé l’empreinte digitale à une stratégie DLP, DLP détecte les e-mails sortants contenant des documents qui correspondent à l’empreinte digitale du brevet et les traite en fonction de la stratégie de votre organisation.

Par exemple, vous souhaiterez peut-être configurer une stratégie DLP qui empêche les employés réguliers d’envoyer des messages sortants contenant des brevets. DLP utilisera l’empreinte du brevet pour détecter les brevets et bloquer ces e-mails. Vous pouvez également laisser votre service juridique être en mesure d’envoyer des brevets à d’autres organisations parce qu’il a besoin d’une entreprise pour le faire. Vous pouvez autoriser des services spécifiques à envoyer des informations sensibles en créant des exceptions pour ces départements dans votre stratégie DLP, ou vous pouvez leur permettre de remplacer un conseil de stratégie par une justification métier.

### <a name="supported-file-types"></a>Types de fichiers pris en charge

L’empreinte digitale de document prend en charge les mêmes types de fichiers que ceux pris en charge dans les règles de flux de courrier (également appelées règles de transport). Pour obtenir la liste des types de fichiers pris en charge, consultez [Types de fichiers pris en charge pour l’inspection du contenu des règles de flux de courrier](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection). Une remarque rapide sur les types de fichiers : ni les règles de flux de courrier ni l’empreinte digitale de document ne prennent en charge le type de fichier .dotx, ce qui peut prêter à confusion, car il s’agit d’un fichier modèle dans Word. Lorsque vous voyez le mot « modèle » dans cette rubrique et dans d’autres rubriques relatives à l’empreinte digitale de document, il fait référence à un document que vous avez établi en tant que formulaire standard, et non en tant que type de fichier modèle.

#### <a name="limitations-of-document-fingerprinting"></a>Limites de l’empreinte numérique de document

L’empreinte digitale de document ne détecte pas les informations sensibles dans les cas suivants :

- Si les fichiers sont protégés par mot de passe
- Si les fichiers contiennent uniquement des images
- Si les documents ne contiennent pas l'intégralité du texte du formulaire d'origine utilisé pour créer l'empreinte numérique de document
- Fichiers supérieurs à 10 Mo

## <a name="use-powershell-to-create-a-classification-rule-package-based-on-document-fingerprinting"></a>Utiliser PowerShell pour créer un package de règles de classification basé sur l’empreinte digitale de document

Actuellement, vous pouvez créer une empreinte digitale de document uniquement dans [Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

DLP utilise des packages de règles de classification pour détecter le contenu sensible. Pour créer un package de règles de classification basé sur une empreinte digitale de document, utilisez les applets de **commande New-DlpFingerprint** et **New-DlpSensitiveInformationType** . Étant donné que les résultats de **New-DlpFingerprint** ne sont pas stockés en dehors de la règle de classification des données, vous exécutez toujours **New-DlpFingerprint** et **New-DlpSensitiveInformationType** ou **Set-DlpSensitiveInformationType** dans la même session PowerShell. L'exemple suivant crée une empreinte numérique de document à partir du fichier C:\My Documents\Contoso Employee Template.docx. La nouvelle empreinte est stockée en tant que variable pour que vous puissiez l’utiliser avec la cmdlet **New-DlpSensitiveInformationType** dans la même session PowerShell.

```powershell
$Employee_Template = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Employee Template.docx'))
$Employee_Fingerprint = New-DlpFingerprint -FileData $Employee_Template -Description "Contoso Employee Template"
```

À présent, nous allons créer une règle de classification des données nommée « Contoso Employee Confidential » qui utilise l'empreinte numérique de document du fichier C:\My Documents\Contoso Customer Information Form.docx.

```powershell
$Customer_Form = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Customer Information Form.docx'))
$Customer_Fingerprint = New-DlpFingerprint -FileData $Customer_Form -Description "Contoso Customer Information Form"
New-DlpSensitiveInformationType -Name "Contoso Customer Confidential" -Fingerprints $Customer_Fingerprint -Description "Message contains Contoso customer information."
```

Vous pouvez maintenant utiliser l’applet de commande **Get-DlpSensitiveInformationType** pour rechercher tous les packages de règles de classification des données DLP. Dans cet exemple, « Contoso Customer Confidential » fait partie de la liste des packages de règles de classification des données.

Enfin, ajoutez le package de règle de classification des données « Confidentiel client Contoso » à une stratégie DLP dans le portail de conformité Microsoft Purview. Cet exemple montre comment ajouter une règle à une stratégie DLP existante nommée « ConfidentialPolicy ».

```powershell
New-DlpComplianceRule -Name "ContosoConfidentialRule" -Policy "ConfidentialPolicy" -ContentContainsSensitiveInformation @{Name="Contoso Customer Confidential"} -BlockAccess $True
```

Vous pouvez également utiliser le package de règles de classification des données dans les règles de flux de messagerie dans Exchange Online, comme illustré dans l’exemple suivant. Pour exécuter cette commande, vous devez d’abord vous [connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Notez également que la synchronisation du package de règles entre le portail de conformité Microsoft Purview et le centre d’administration Exchange prend du temps.

```powershell
New-TransportRule -Name "Notify :External Recipient Contoso confidential" -NotifySender NotifyOnly -Mode Enforce -SentToScope NotInOrganization -MessageContainsDataClassification @{Name=" Contoso Customer Confidential"}
```

DLP détecte désormais les documents qui correspondent à l’empreinte digitale du document Form.docx client Contoso.

Pour obtenir des informations sur la syntaxe et les paramètres, consultez :

- [New-DlpFingerprint](/powershell/module/exchange/New-DlpFingerprint)
- [New-DlpSensitiveInformationType](/powershell/module/exchange/New-DlpSensitiveInformationType)
- [Remove-DlpSensitiveInformationType](/powershell/module/exchange/Remove-DlpSensitiveInformationType)
- [Set-DlpSensitiveInformationType](/powershell/module/exchange/Set-DlpSensitiveInformationType)
- [Get-DlpSensitiveInformationType](/powershell/module/exchange/Get-DlpSensitiveInformationType)
