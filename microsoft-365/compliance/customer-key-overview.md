---
title: Chiffrement de service avec la clé client Microsoft Purview
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- purview-compliance
- m365solution-mip
- m365initiative-compliance
- tier1
- highpri
ms.custom: seo-marvel-apr2020
description: Dans cet article, vous allez découvrir le fonctionnement du chiffrement de service avec la clé client Microsoft Purview.
ms.openlocfilehash: 9d4e19b322f1dd4672dfdf06fedeef23b1cdadbc
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68641862"
---
# <a name="service-encryption-with-microsoft-purview-customer-key"></a>Chiffrement de service avec la clé client Microsoft Purview

Microsoft 365 fournit un chiffrement de base au niveau du volume activé via BitLocker et Distributed Key Manager (DKM). Microsoft 365 offre une couche de chiffrement supplémentaire pour votre contenu. Ce contenu inclut des données provenant de Exchange Online, Skype Entreprise, SharePoint Online, OneDrive Entreprise et Microsoft Teams.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="how-service-encryption-bitlocker-and-customer-key-work-together"></a>Fonctionnement du chiffrement de service, de BitLocker et de la clé client

Vos données sont toujours chiffrées au repos dans le service Microsoft 365 avec BitLocker et DKM. Pour plus d’informations, consultez [Comment Exchange Online sécurise vos secrets de messagerie](exchange-online-secures-email-secrets.md). La clé client offre une protection supplémentaire contre l’affichage des données par des systèmes ou du personnel non autorisés, et complète le chiffrement de disque BitLocker dans les centres de données Microsoft. Le chiffrement de service n’est pas destiné à empêcher le personnel Microsoft d’accéder à vos données. Au lieu de cela, la clé client vous aide à respecter les obligations réglementaires ou de conformité en matière de contrôle des clés racine. Vous autorisez explicitement les services Microsoft 365 à utiliser vos clés de chiffrement pour fournir des services cloud à valeur ajoutée, tels que eDiscovery, anti-programmes malveillants, anti-courrier indésirable, indexation de recherche, etc.

La clé client repose sur le chiffrement de service et vous permet de fournir et de contrôler les clés de chiffrement. Microsoft 365 utilise ensuite ces clés pour chiffrer vos données au repos, comme décrit dans les conditions des [services en ligne (OST).](https://www.microsoft.com/licensing/product-licensing/products.aspx) La clé client vous aide à respecter les obligations de conformité, car vous contrôlez les clés de chiffrement utilisées par Microsoft 365 pour chiffrer et déchiffrer les données.
  
La clé client améliore la capacité de votre organisation à répondre aux exigences de conformité qui spécifient des arrangements clés avec le fournisseur de services cloud. Avec la clé client, vous fournissez et contrôlez les clés de chiffrement racine pour vos données Microsoft 365 au repos au niveau de l’application. Par conséquent, vous contrôlez les clés de votre organisation.

## <a name="customer-key-with-hybrid-deployments"></a>Clé client avec déploiements hybrides

La clé client chiffre uniquement les données au repos dans le cloud. La clé client ne fonctionne pas pour protéger vos boîtes aux lettres et fichiers locaux. Vous pouvez chiffrer vos données locales à l’aide d’une autre méthode, telle que BitLocker.

## <a name="about-data-encryption-policies"></a>À propos des stratégies de chiffrement des données

Une stratégie de chiffrement des données (DEP) définit la hiérarchie de chiffrement. Cette hiérarchie est utilisée par le service pour chiffrer les données à l’aide de chacune des clés que vous gérez et de la clé de disponibilité protégée par Microsoft. Vous créez des dep à l’aide d’applets de commande PowerShell, puis affectez ces DEP pour chiffrer les données d’application. Il existe trois types de dep pris en charge par customer key, chaque type de stratégie utilise des applets de commande différentes et fournit une couverture pour un type de données différent. Les dep que vous pouvez définir sont les suivantes :

**DEP pour plusieurs charges de travail Microsoft 365** Ces DEP chiffrent les données sur plusieurs charges de travail M365 pour tous les utilisateurs au sein du locataire. Ces charges de travail sont les suivantes :

- Messages de conversation Teams (conversations 1:1, conversations de groupe, conversations de réunion et conversations de canal)
- Messages multimédias Teams (images, extraits de code, messages vidéo, messages audio, images wiki)
- Enregistrements d’appels et de réunions Teams stockés dans le stockage Teams
- Notifications de conversation Teams
- Suggestions de conversation Teams par Cortana
- Messages d’état Teams
- Informations sur l’utilisateur et le signal pour Exchange Online
- Exchange Online boîtes aux lettres qui ne sont pas déjà chiffrées par des dep de boîte aux lettres
- Protection des données Microsoft Purview :

  - Données de correspondance de données exactes (EDM), y compris les schémas de fichier de données, les packages de règles et les sels utilisés pour hacher les données sensibles. Pour EDM et Microsoft Teams, le DEP multi-charge de travail chiffre les nouvelles données à partir du moment où vous affectez le DEP au locataire. Pour Exchange Online, customer key chiffre toutes les données existantes et nouvelles.

  - Configuration des étiquettes pour les étiquettes de confidentialité

Les DEP multi-charges de travail ne chiffrent pas les types de données suivants. Au lieu de cela, Microsoft 365 utilise d’autres types de chiffrement pour protéger ces données.

- Données SharePoint et OneDrive Entreprise.
- Les fichiers Microsoft Teams et certains enregistrements d’appels et de réunions Teams enregistrés dans OneDrive Entreprise et SharePoint Online sont chiffrés à l’aide du dep SharePoint Online.
- D’autres charges de travail Microsoft 365 telles que Yammer et Planner qui ne sont actuellement pas prises en charge par la clé client.
- Données d’événements en direct Teams.

Vous pouvez créer plusieurs DEP par locataire, mais n’attribuer qu’un seul DEP à la fois. Lorsque vous attribuez le dep, le chiffrement commence automatiquement, mais prend un certain temps en fonction de la taille de votre locataire.

**Les DEP pour les boîtes aux lettres Exchange Online offrent** un contrôle plus précis sur les boîtes aux lettres individuelles dans Exchange Online. Utilisez des dep de boîte aux lettres pour chiffrer les données stockées dans des boîtes aux lettres EXO de différents types, telles que UserMailbox, MailUser, Group, PublicFolder et Shared mailboxes. Vous pouvez avoir jusqu’à 50 DEP actifs par locataire et les affecter à des boîtes aux lettres individuelles. Vous pouvez affecter un DEP à plusieurs boîtes aux lettres.

Par défaut, vos boîtes aux lettres sont chiffrées à l’aide de clés gérées par Microsoft. Lorsque vous affectez un DEP de clé client à une boîte aux lettres :

- Si la boîte aux lettres est chiffrée à l’aide d’un DEP multi-charge de travail, le service réapprape la boîte aux lettres à l’aide de la nouvelle boîte aux lettres DEP tant qu’un utilisateur ou une opération système accède aux données de la boîte aux lettres.

- Si la boîte aux lettres est déjà chiffrée à l’aide de clés gérées par Microsoft, le service réapprape la boîte aux lettres à l’aide du nouveau DEP de boîte aux lettres tant qu’un utilisateur ou une opération système accède aux données de la boîte aux lettres.

- Si la boîte aux lettres n’est pas encore chiffrée à l’aide du chiffrement par défaut, le service marque la boîte aux lettres pour un déplacement. Le chiffrement a lieu une fois le déplacement terminé. Les déplacements de boîte aux lettres sont régis en fonction des priorités définies pour l’ensemble de Microsoft 365. Pour plus d’informations, consultez [Déplacer les demandes dans le service Microsoft 365](/exchange/mailbox-migration/office-365-migration-best-practices#move-requests-in-the-microsoft-365-or-office-365-service). Si les boîtes aux lettres ne sont pas chiffrées dans le délai spécifié, contactez Microsoft.

Par la suite, vous pouvez actualiser le dep ou affecter un autre DEP à la boîte aux lettres, comme décrit dans [Gérer la clé client pour Office 365](customer-key-manage.md). Chaque boîte aux lettres doit disposer de licences appropriées pour re être affectée à un DEP. Pour plus d’informations sur les licences, consultez [Avant de configurer la clé client](customer-key-set-up.md#before-you-set-up-customer-key).

Les dep peuvent être affectés à une boîte aux lettres partagée, une boîte aux lettres de dossiers public et une boîte aux lettres de groupe Microsoft 365 pour les locataires qui répondent aux exigences de licence pour les boîtes aux lettres utilisateur. Vous n’avez pas besoin de licences distinctes pour les boîtes aux lettres non spécifiques à l’utilisateur pour attribuer un DEP de clé client.

Pour les DEP de clé client que vous affectez à des boîtes aux lettres individuelles, vous pouvez demander à Microsoft de purger des DEP spécifiques lorsque vous quittez le service. Pour plus d’informations sur le processus de vidage des données et la révocation de clés, consultez [Révoquer vos clés et démarrer le processus de chemin de vidage des données](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process).

Lorsque vous révoquez l’accès à vos clés dans le cadre de la sortie du service, la clé de disponibilité est supprimée, ce qui entraîne la suppression du chiffrement de vos données. La suppression de chiffrement atténue le risque de rémanence des données, ce qui est important pour respecter les obligations de sécurité et de conformité.

**DEP pour SharePoint Online et OneDrive Entreprise** Ce DEP est utilisé pour chiffrer le contenu stocké dans SPO et OneDrive Entreprise, y compris les fichiers Microsoft Teams stockés dans SPO. Si vous utilisez la fonctionnalité multigéographique, vous pouvez créer un DEP par géo pour votre organisation. Si vous n’utilisez pas la fonctionnalité multigéographique, vous ne pouvez créer qu’un seul DEP par locataire. Reportez-vous aux détails de [la configuration de la clé client](customer-key-set-up.md).

### <a name="encryption-ciphers-used-by-customer-key"></a>Chiffrement des chiffrements utilisés par la clé client

La clé client utilise différents chiffrements de chiffrement pour chiffrer les clés, comme indiqué dans les figures suivantes.

La hiérarchie de clés utilisée pour les DEP qui chiffrent des données pour plusieurs charges de travail Microsoft 365 est similaire à la hiérarchie utilisée pour les dep pour les boîtes aux lettres Exchange Online individuelles. La seule différence est que la clé de boîte aux lettres est remplacée par la clé de charge de travail Microsoft 365 correspondante.

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Chiffrements utilisés pour chiffrer des clés pour Exchange Online et Skype Entreprise

![Chiffrement des chiffrements pour Exchange Online clé client.](../media/customerkeyencryptionhierarchiesexchangeskype.png)

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Chiffrements utilisés pour chiffrer les clés pour les fichiers SharePoint Online, OneDrive Entreprise et Teams

![Chiffrement des chiffrements pour la clé client SharePoint Online.](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>Articles connexes

- [Configurer la clé client](customer-key-set-up.md)

- [Gérer la clé client](customer-key-manage.md)

- [Echanger ou alterner entre une clé client ou de disponibilité](customer-key-availability-key-roll.md)

- [En savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md)

- [Référentiel sécurisé client](customer-lockbox-requests.md)

- [Chiffrement de service](office-365-service-encryption.md)
