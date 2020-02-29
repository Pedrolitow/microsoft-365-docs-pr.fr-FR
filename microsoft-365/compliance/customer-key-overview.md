---
title: Chiffrement de service avec clé client dans Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 02/05/2020
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Avec la clé client, vous contrôlez les clés de chiffrement de votre organisation, puis vous configurez Office 365 afin de les utiliser pour chiffrer vos données au repos dans les centres de données de Microsoft.
ms.openlocfilehash: 0910374051073cb67ee4d2a4fac0a88871a2fd73
ms.sourcegitcommit: 004f01fc5d5bdb8aac03d69692d86c38b5e05e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "42333651"
---
# <a name="service-encryption-with-customer-key-in-office-365"></a>Chiffrement de service avec clé client dans Office 365

Office 365 offre une planification, un chiffrement au niveau du volume activé via BitLocker et le gestionnaire de clés distribuées (DKM). Office 365 offre une couche de chiffrement supplémentaire au niveau de l’application pour votre contenu. Ce contenu inclut des données provenant de fichiers Exchange Online, Skype entreprise, SharePoint Online, OneDrive entreprise et Teams. Cette couche de chiffrement ajoutée est appelée chiffrement de service.

## <a name="how-service-encryption-bitlocker-and-customer-key-work-together"></a>Fonctionnement conjoint du chiffrement de service, de BitLocker et de la clé client

Le chiffrement de service garantit que le contenu au repos est chiffré au niveau de la couche d’application. **Vos données sont toujours chiffrées au repos dans le service Office 365 avec BitLocker et DKM**. Pour plus d’informations, consultez les informations relatives à la sécurité, à la confidentialité et à la conformité pour Office 365, ainsi qu’à la [manière dont Exchange Online sécurise vos secrets de messagerie](exchange-online-secures-email-secrets.md). La clé client offre une protection supplémentaire contre l’affichage des données par des systèmes ou du personnel non autorisés et complète le chiffrement de disque BitLocker dans les centres de données Microsoft. Le chiffrement de service n’est pas destiné à empêcher le personnel Microsoft d’accéder aux données client. L’objectif principal est d’aider les clients à respecter les obligations réglementaires ou de conformité pour le contrôle des clés racines. Les clients autorisent explicitement les services O365 à utiliser leurs clés de chiffrement pour fournir des services Cloud à valeur ajoutée, tels que eDiscovery, anti-programme malveillant, le blocage du courrier indésirable, l’indexation de la recherche, etc.

La clé client est basée sur le chiffrement de service et vous permet de fournir et de contrôler des clés de chiffrement. Office 365 utilise ensuite ces clés pour chiffrer vos données au repos, comme décrit dans les [services en ligne (OST)](https://www.microsoft.com/licensing/product-licensing/products.aspx). La clé client vous permet de respecter les obligations de conformité, car vous contrôlez les clés de chiffrement qu’Office 365 utilise pour chiffrer et déchiffrer les données.
  
La clé client améliore la capacité de votre organisation à répondre aux exigences des exigences de conformité qui spécifient des dispositions clés avec le fournisseur de services Cloud. La clé client vous permet de fournir et de contrôler les clés de chiffrement racines pour vos données Office 365 au niveau de l’application. Par conséquent, vous exercez le contrôle sur les clés de votre organisation. Si vous décidez de quitter le service, vous révoquez l’accès aux clés racines de votre organisation. Pour tous les services Office 365, la révocation de l’accès aux clés est la première étape sur le chemin d’accès à la suppression des données. En révoquant l’accès aux clés, les données ne sont pas lisibles pour le service.

## <a name="customer-key-encrypts-data-at-rest-in-office-365"></a>La clé client chiffre les données au repos dans Office 365

À l’aide de clés que vous fournissez, la clé client pour Office 365 chiffre les éléments suivants :

- Fichiers SharePoint Online, OneDrive entreprise et Teams.
- Fichiers téléchargés vers OneDrive entreprise.
- Contenu de boîte aux lettres Exchange Online, y compris le contenu de corps de courrier électronique, les entrées de calendrier et le contenu des pièces jointes.
- Conversations textuelles de Skype entreprise.

Nous n’offrons actuellement pas le contrôle par le client des clés de chiffrement pour la diffusion de réunion Skype et les téléchargements de contenu de réunion Skype. Au lieu de cela, ce contenu est chiffré avec tout autre contenu dans Office 365.

### <a name="customer-key-with-hybrid-deployments"></a>Clé client avec déploiements hybrides

La clé client chiffre uniquement les données au repos dans le Cloud. La clé client ne fonctionne pas pour protéger vos boîtes aux lettres et fichiers locaux. Vous pouvez chiffrer vos données locales à l’aide d’une autre méthode, telle que BitLocker.

## <a name="about-the-data-encryption-policy-dep"></a>À propos de la stratégie de chiffrement des données (DEP)

Une stratégie de chiffrement de données définit la hiérarchie de chiffrement pour chiffrer les données à l’aide de chacune des clés que vous fournissez, ainsi que la clé de disponibilité protégée par Microsoft. Vous créez DEPs à l’aide d’applets de commande PowerShell, qui sont différentes pour chaque service, et vous les attribuez pour chiffrer les données d’application. Par exemple :

**Exchange Online et Skype entreprise** Vous pouvez créer jusqu’à 50 DEPs par client. Vous associez DEPs à vos clés de client dans le coffre de clés Azure, puis vous affectez DEPs à des boîtes aux lettres individuelles. Lorsque vous affectez une DEP à une boîte aux lettres :

- la boîte aux lettres est marquée pour un déplacement de boîte aux lettres. En fonction des priorités dans Office 365, comme décrit ici, [déplacez les demandes dans le service office 365](https://docs.microsoft.com/exchange/mailbox-migration/office-365-migration-best-practices#move-requests-in-the-office-365-service).

- Le chiffrement a lieu lorsque la boîte aux lettres est déplacée. Autorisez 72 heures pour que la boîte aux lettres soit chiffrée avec la nouvelle DEP. Si les boîtes aux lettres ne sont pas chiffrées après avoir attendu 72 heures après l’heure à laquelle vous avez attribué la DEP, contactez Microsoft.

Par la suite, vous pouvez actualiser la DEP ou affecter une autre DEP à la boîte aux lettres, comme décrit dans [Manage Customer Key for Office 365](customer-key-manage.md). Chaque boîte aux lettres doit disposer des licences appropriées pour affecter une DEP. Pour plus d’informations sur les licences, reportez-vous à avant la configuration de la [clé client](customer-key-set-up.md#before-you-set-up-customer-key).

**Fichiers SharePoint Online, OneDrive entreprise et teams** Si vous utilisez la fonctionnalité multigéographique, vous pouvez créer jusqu’à une DEP par zone géographique pour votre organisation. Vous pouvez utiliser différentes clés de client pour chaque région. Si vous n’utilisez pas la fonctionnalité multigéographique, vous ne pouvez créer qu’une seule DEP par client. Lorsque vous affectez la DEP, le chiffrement démarre automatiquement, mais peut prendre un certain temps. Reportez-vous aux détails de la rubrique [set up Customer Key for Office 365](customer-key-set-up.md).

## <a name="leaving-the-service"></a>Quitter le service

La clé client vous aide à respecter les obligations de conformité en vous permettant de révoquer vos clés lorsque vous quittez le service Office 365. Lorsque vous révoquez vos clés dans le cadre de la cessation du service, la clé de disponibilité est supprimée, ce qui entraîne la suppression chiffrée de vos données. La suppression du chiffrement réduit le risque de remanence de données qui est important pour la réunion des obligations de sécurité et de conformité. Pour plus d’informations sur le processus de purge des données et la révocation de clés, voir [révoquer vos clés et démarrer le processus de chemin de purge des données](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process).

### <a name="encryption-ciphers-used-by-customer-key"></a>Chiffrements de chiffrement utilisés par la clé client

La clé client utilise un grand nombre de chiffrements de chiffrement pour chiffrer les clés, comme indiqué dans les figures suivantes.

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Chiffrements de chiffrement utilisés pour chiffrer les clés pour Exchange Online et Skype entreprise

![Chiffrements de chiffrement pour la clé client Exchange Online](../media/customerkeyencryptionhierarchiesexchangeskype.png)

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Chiffrements de chiffrement utilisés pour chiffrer les clés pour SharePoint Online, OneDrive entreprise et les fichiers teams

![Chiffrements de chiffrement pour la clé client SharePoint Online](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>Articles connexes

- [Configurer la clé client pour Office 365](customer-key-set-up.md)

- [Gérer la clé client pour Office 365](customer-key-manage.md)

- [Faire pivoter ou faire pivoter une clé client ou une clé de disponibilité](customer-key-availability-key-roll.md)

- [En savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md)

- [Référentiel sécurisé du client dans Office 365](customer-lockbox-requests.md)

- [Chiffrement du service Office 365](office-365-service-encryption.md)
