---
title: Chiffrement du service avec la clé client
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
- m365solution-mip
- m365initiative-compliance
ms.custom: seo-marvel-apr2020
description: Dans cet article, vous allez découvrir le fonctionnement du chiffrement de service avec la clé client dans Microsoft 365.
ms.openlocfilehash: 21291dc45cd634cd5b6a88c4e58972c17486724f
ms.sourcegitcommit: 94fa3e57fa6505551d84ae7b458150dceff30db7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2021
ms.locfileid: "51394722"
---
# <a name="service-encryption-with-customer-key"></a>Chiffrement du service avec la clé client

Microsoft 365 fournit un chiffrement de base au niveau du volume activé via BitLocker et le Gestionnaire de clés distribuées (DKM). Microsoft 365 offre une couche de chiffrement supplémentaire au niveau de la couche d’application pour votre contenu. Ce contenu inclut les données des fichiers Exchange Online, Skype Entreprise, SharePoint Online, OneDrive Entreprise et Teams. Cette couche de chiffrement ajoutée est appelée chiffrement de service.

## <a name="how-service-encryption-bitlocker-and-customer-key-work-together"></a>Comment le chiffrement de service, BitLocker et la clé client fonctionnent ensemble

Le chiffrement de service garantit que le contenu au repos est chiffré au niveau de la couche service. Vos données sont toujours chiffrées au repos dans le **service Microsoft 365 avec BitLocker et DKM.** Pour plus d’informations, voir « Informations sur la sécurité, la confidentialité et la conformité » et comment [Exchange Online sécurisation vos secrets de messagerie.](exchange-online-secures-email-secrets.md) La clé client offre une protection supplémentaire contre l’affichage des données par des systèmes ou du personnel non autorisés, et complète le chiffrement de disque BitLocker dans les centres de données Microsoft. Le chiffrement de service n’est pas destiné à empêcher le personnel Microsoft d’accéder aux données client. L’objectif principal est d’aider les clients à respecter les obligations réglementaires ou de conformité en matière de contrôle des clés racines. Les clients autorisent explicitement les services O365 à utiliser leurs clés de chiffrement pour fournir des services cloud à valeur ajoutée, tels que eDiscovery, anti-programme malveillant, anti-courrier indésirable, indexation de recherche, etc.

La clé client repose sur le chiffrement de service et vous permet de fournir et de contrôler les clés de chiffrement. Microsoft 365 utilise ensuite ces clés pour chiffrer vos données au repos, comme décrit dans les conditions d’utilisation des services en ligne [(OST).](https://www.microsoft.com/licensing/product-licensing/products.aspx) La clé client vous aide à respecter les obligations de conformité, car vous contrôlez les clés de chiffrement que Microsoft 365 utilise pour chiffrer et déchiffrer des données.
  
La clé client améliore la capacité de votre organisation à répondre aux exigences de conformité qui spécifient des accords clés avec le fournisseur de services cloud. Avec la clé client, vous fournissez et contrôlez les clés de chiffrement racine pour vos données Microsoft 365 au repos au niveau de l’application. Par conséquent, vous exercez le contrôle sur les clés de votre organisation. Si vous décidez de quitter le service, vous révoquez l’accès aux clés racine de votre organisation. Pour tous les services Microsoft 365, la révocation de l’accès aux clés est la première étape du chemin vers la suppression des données. En révoquer l’accès aux clés, les données sont illisibles pour le service.

## <a name="customer-key-encrypts-data-at-rest-in-office-365"></a>La clé client chiffre les données au repos dans Office 365

À l’aide des clés que vous fournissez, la clé client au niveau de l’application chiffre :

- Fichiers SharePoint Online, OneDrive Entreprise et Teams.
- Fichiers téléchargés vers OneDrive Entreprise.
- Contenu de boîte aux lettres Exchange Online, y compris le contenu du corps du message électronique, les entrées de calendrier et le contenu des pièces jointes d’e-mail.
- Conversations texte à partir de Skype Entreprise.

Nous n’offrons pas actuellement au client le contrôle des clés de chiffrement pour les téléchargements de contenu de diffusion de réunion Skype et de réunion Skype. Au lieu de cela, ce contenu est chiffré avec tout le reste du contenu dans Office 365.

### <a name="customer-key-with-hybrid-deployments"></a>Clé client avec déploiements hybrides

La clé client chiffre uniquement les données au repos dans le cloud. La clé client ne fonctionne pas pour protéger vos boîtes aux lettres et fichiers locaux. Vous pouvez chiffrer vos données sur site à l’aide d’une autre méthode, telle que BitLocker.

## <a name="about-the-data-encryption-policy-dep"></a>À propos de la stratégie de chiffrement de données (DEP)

Une stratégie de chiffrement de données définit la hiérarchie de chiffrement pour chiffrer les données à l’aide de chacune des clés que vous fournissez, ainsi que de la clé de disponibilité protégée par Microsoft. Vous créez des PDP à l’aide d’cmdlets PowerShell, qui sont différentes pour chaque service, et vous affectez ces dep pour chiffrer les données d’application. Par exemple :

**Exchange Online et Skype Entreprise** Vous pouvez créer jusqu’à 50 DEP par client. Vous associez des dep à vos clés client dans Azure Key Vault, puis vous affectez des DPS à des boîtes aux lettres individuelles. Lorsque vous affectez un deP à une boîte aux lettres :

- la boîte aux lettres est marquée pour un déplacement de boîte aux lettres. Basé sur les priorités dans Microsoft 365 comme décrit ici Déplacer [des demandes dans le service Microsoft 365](/exchange/mailbox-migration/office-365-migration-best-practices#move-requests-in-the-office-365-service).

- Le chiffrement a lieu pendant le déplacement de la boîte aux lettres. Autorisez 72 heures pour que la boîte aux lettres soit chiffrée avec le nouveau PED. Si les boîtes aux lettres ne sont pas chiffrées après avoir attendu 72 heures à partir du moment où vous avez affecté le PED, contactez Microsoft.

Par la suite, vous pouvez actualiser le deP ou affecter un autre deP à la boîte aux lettres comme décrit dans Gérer la clé client pour [Office 365](customer-key-manage.md). Chaque boîte aux lettres doit avoir les licences appropriées pour attribuer un dep. Pour plus d’informations sur la gestion des licences, [voir Avant de configurer la clé client.](customer-key-set-up.md#before-you-set-up-customer-key)

> [!NOTE]
> Le PD DEP peut être appliqué à une boîte aux lettres partagée, une boîte aux lettres de dossiers publics et une boîte aux lettres de groupe Microsoft 365 pour les clients qui répondent aux exigences de licence pour les boîtes aux lettres utilisateur, même si certains de ces types de boîtes aux lettres ne peuvent pas être une licence attribuée (boîte aux lettres de dossiers publics et boîte aux lettres de groupe Microsoft 365) ou avoir besoin d’une licence pour augmenter le stockage (boîte aux lettres partagée).

**Fichiers SharePoint Online, OneDrive Entreprise et Teams** Si vous utilisez la fonctionnalité multigéogé, vous pouvez créer jusqu’à un dep par géo pour votre organisation. Vous pouvez utiliser différentes clés client pour chaque géo. Si vous n’utilisez pas la fonctionnalité multigéogé, vous ne pouvez créer qu’une seule PD DEP par client. Lorsque vous affectez le dep, le chiffrement commence automatiquement, mais peut prendre un certain temps. Reportez-vous aux détails dans [Configurer la clé client.](customer-key-set-up.md)

## <a name="leaving-the-service"></a>Quitter le service

La clé client vous aide à respecter les obligations de conformité en vous permettant de révoquer vos clés lorsque vous quittez le service Microsoft 365. Lorsque vous révoquez vos clés dans le cadre de la sortie du service, la clé de disponibilité est supprimée, ce qui entraîne la suppression de vos données par chiffrement. La suppression de chiffrement atténue le risque de rémanence des données, ce qui est important pour respecter les obligations de sécurité et de conformité. Pour plus d’informations sur le processus de purge des données et la révocation de clés, voir Révoquer vos clés et démarrer le processus de chemin d’accès [de la purge des données.](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process)

### <a name="encryption-ciphers-used-by-customer-key"></a>Chiffrements de chiffrement utilisés par la clé client

La clé client utilise une variété de chiffrements de chiffrement pour chiffrer les clés, comme illustré dans les figures suivantes.

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Chiffrements de chiffrement utilisés pour chiffrer les clés pour Exchange Online et Skype Entreprise

![Chiffrements de chiffrement pour la clé client Exchange Online](../media/customerkeyencryptionhierarchiesexchangeskype.png)

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Chiffrements de chiffrement utilisés pour chiffrer les clés pour les fichiers SharePoint Online, OneDrive Entreprise et Teams

![Chiffrements de chiffrement pour la clé client SharePoint Online](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>Articles connexes

- [Configurer la clé client](customer-key-set-up.md)

- [Gérer la clé client](customer-key-manage.md)

- [Echanger ou alterner entre une clé client ou de disponibilité](customer-key-availability-key-roll.md)

- [En savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md)

- [Référentiel sécurisé client](customer-lockbox-requests.md)

- [Chiffrement de service](office-365-service-encryption.md)