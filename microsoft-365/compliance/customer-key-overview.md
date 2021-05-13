---
title: Chiffrement du service avec la clé client
ms.author: krowley
author: kccross
manager: laurawi
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
description: Dans cet article, vous allez découvrir comment fonctionne le chiffrement de service avec la clé client dans Microsoft 365.
ms.openlocfilehash: 3d0c86dbca02a66547f0ade643b745ecfc8f92cd
ms.sourcegitcommit: 94e64afaf12f3d8813099d8ffa46baba65772763
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2021
ms.locfileid: "52344769"
---
# <a name="service-encryption-with-customer-key"></a>Chiffrement du service avec la clé client

Microsoft 365 fournit un chiffrement de base, au niveau du volume, activé par BitLocker et le Gestionnaire de clés distribuées (DKM). Microsoft 365 offre une couche de chiffrement supplémentaire pour votre contenu. Ce contenu inclut des données provenant Exchange Online, Skype Entreprise, SharePoint Online, OneDrive Entreprise et Microsoft Teams.

## <a name="how-service-encryption-bitlocker-and-customer-key-work-together"></a>Comment le chiffrement de service, BitLocker et la clé client fonctionnent ensemble

Vos données sont toujours chiffrées au repos dans le service Microsoft 365 avec BitLocker et DKM. Pour plus d’informations, [voir How Exchange Online secures your email secrets](exchange-online-secures-email-secrets.md). La clé client offre une protection supplémentaire contre l’affichage des données par des systèmes ou du personnel non autorisés et complète BitLocker chiffrement de disque dans les centres de données Microsoft. Le chiffrement de service n’est pas destiné à empêcher le personnel Microsoft d’accéder à vos données. Au lieu de cela, la clé client vous aide à respecter les obligations réglementaires ou de conformité en matière de contrôle des clés racine. Vous autorisez explicitement les services Microsoft 365 à utiliser vos clés de chiffrement pour fournir des services cloud à valeur ajoutée, tels que eDiscovery, anti-programme malveillant, anti-courrier indésirable, indexation de recherche, etc.

La clé client repose sur le chiffrement de service et vous permet de fournir et de contrôler les clés de chiffrement. Microsoft 365 ces clés pour chiffrer vos données au repos, comme décrit dans les conditions d’utilisation des services en ligne [(OST).](https://www.microsoft.com/licensing/product-licensing/products.aspx) La clé client vous aide à respecter les obligations de conformité, car vous contrôlez les clés de chiffrement Microsoft 365 que vous pouvez utiliser pour chiffrer et déchiffrer des données.
  
La clé client améliore la capacité de votre organisation à répondre aux exigences de conformité qui spécifient des accords clés avec le fournisseur de services cloud. Avec la clé client, vous fournissez et contrôlez les clés de chiffrement racine pour Microsoft 365 données au repos au niveau de l’application. Par conséquent, vous exercez le contrôle sur les clés de votre organisation.

## <a name="customer-key-with-hybrid-deployments"></a>Clé client avec déploiements hybrides

La clé client chiffre uniquement les données au repos dans le cloud. La clé client ne fonctionne pas pour protéger vos boîtes aux lettres et fichiers locaux. Vous pouvez chiffrer vos données sur site à l’aide d’une autre méthode, telle que BitLocker.

## <a name="about-data-encryption-policies"></a>À propos des stratégies de chiffrement de données

Une stratégie de chiffrement de données (DEP) définit la hiérarchie de chiffrement. Cette hiérarchie est utilisée par le service pour chiffrer les données à l’aide de chacune des clés que vous gérez et de la clé de disponibilité protégée par Microsoft. Vous créez des PDP à l’aide des cmdlets PowerShell, puis vous les affectez pour chiffrer les données d’application. Il existe trois types de PDP pris en charge par Microsoft 365 clé client, chaque type de stratégie utilise des cmdlets différentes et fournit une couverture pour un type de données différent. Les DPS que vous pouvez définir sont les suivants :

**PD DEP pour plusieurs charges Microsoft 365 charges de travail** Ces DPS chiffrent les données sur plusieurs charges de travail M365 pour tous les utilisateurs au sein du client. Ces charges de travail sont les suivantes :

- Teams messages de conversation (conversations 1:1, conversations de groupe, conversations de réunion et conversations de canal)
- Teams messages multimédias (images, extraits de code, messages vidéo, messages audio, images Wiki)
- Teams enregistrements d’appels et de réunions stockés dans Teams stockage
- Teams notifications de conversation
- Teams suggestions de conversation par Cortana
- Teams messages d’état
- Informations sur l’utilisateur et le signal Exchange Online
- Exchange Online boîtes aux lettres qui ne sont pas déjà chiffrées par des deps de boîte aux lettres
- Données de correspondance de données exactes MIP (EDM) : (schémas de fichiers de données, packages de règles et sels utilisés pour hachage des données sensibles).
  Pour la correspondance exacte des données MIP (EDM) et Microsoft Teams, le PED à charges de travail multiples chiffre les nouvelles données à partir du moment où vous affectez le dep au client. Par Exchange Online, la clé client chiffre toutes les données existantes et nouvelles.

Les dep multi-charges de travail ne chiffrent pas les types de données suivants. Au lieu de cela, Microsoft 365 utilise d’autres types de chiffrement pour protéger ces données.

- SharePoint et OneDrive Entreprise données.
- Microsoft Teams fichiers et certains enregistrements Teams appels et de réunions enregistrés dans OneDrive Entreprise et SharePoint Online sont chiffrés à l’aide de SharePoint DeP online.
- D Microsoft 365 charges de travail telles que Yammer et planner qui ne sont actuellement pas pris en charge par la clé client.
- Teams Événements en direct et questions&A dans les événements en direct. Par Teams, ce scénario est le seul qui n’est pas chiffré par la clé client à l’aide de PED à charges multiples.

Vous pouvez créer plusieurs dep par client, mais n’attribuer qu’une seule PD DEP à la fois. Lorsque vous affectez le dep, le chiffrement commence automatiquement, mais prend un certain temps en fonction de la taille de votre client.

**DePs pour les boîtes Exchange Online aux lettres** Les DEP de boîtes aux lettres permettent de contrôler plus précisément les boîtes aux lettres individuelles au sein Exchange Online. Utilisez des deP de boîte aux lettres pour chiffrer les données stockées dans des boîtes aux lettres EXO de différents types tels que UserMailbox, MailUser, Group, PublicFolder et Les boîtes aux lettres partagées. Vous pouvez avoir jusqu’à 50 DEP actifs par client et les affecter à des boîtes aux lettres individuelles. Vous pouvez affecter un deP à plusieurs boîtes aux lettres.

Par défaut, vos boîtes aux lettres sont chiffrées à l’aide de clés gérées par Microsoft. Lorsque vous affectez un deP de clé client à une boîte aux lettres :

- Si la boîte aux lettres est chiffrée à l’aide d’une PED multi-charge de travail, le service retente la boîte aux lettres à l’aide de la nouvelle boîte aux lettres à condition qu’un utilisateur ou une opération système accède aux données de la boîte aux lettres.

- Si la boîte aux lettres est déjà chiffrée à l’aide de clés gérées par Microsoft, le service réécrit la boîte aux lettres à l’aide de la nouvelle boîte aux lettres PED tant qu’un utilisateur ou une opération système accède aux données de la boîte aux lettres.

- Si la boîte aux lettres n’est pas encore chiffrée à l’aide du chiffrement par défaut, le service marque la boîte aux lettres pour un déplacement. Le chiffrement a lieu une fois le déplacement terminé. Les déplacements de boîtes aux lettres sont régis en fonction des priorités définies pour toutes les Microsoft 365. Pour plus d’informations, voir les [demandes de déplacement dans le service Microsoft 365.](/exchange/mailbox-migration/office-365-migration-best-practices#move-requests-in-the-office-365-service) Si les boîtes aux lettres ne sont pas chiffrées dans le délai spécifié, contactez Microsoft.

Plus tard, vous pouvez actualiser le deP ou affecter un autre deP à la boîte aux lettres comme décrit dans Gérer la clé client [pour Office 365](customer-key-manage.md). Chaque boîte aux lettres doit avoir les licences appropriées pour se voir attribuer un dep. Pour plus d’informations sur la gestion des licences, [voir Avant de configurer la clé client.](customer-key-set-up.md#before-you-set-up-customer-key)

Les dep peuvent être affectés à une boîte aux lettres partagée, une boîte aux lettres de dossiers publics et une boîte aux lettres de groupe Microsoft 365 pour les locataires qui répondent aux conditions de licence requises pour les boîtes aux lettres utilisateur. Vous n’avez pas besoin de licences distinctes pour les boîtes aux lettres non spécifiques à l’utilisateur pour attribuer la clé client DEP.

Pour les DPS de clé client que vous affectez à des boîtes aux lettres individuelles, vous pouvez demander à Microsoft de purger des DPS spécifiques lorsque vous quittez le service. Pour plus d’informations sur le processus de purge des données et la révocation de clés, voir Révoquer vos clés et démarrer le processus de purge [des données.](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process)

Lorsque vous révoquez l’accès à vos clés dans le cadre de la sortie du service, la clé de disponibilité est supprimée, ce qui entraîne la suppression par chiffrement de vos données. La suppression cryptographique atténue le risque de rémanence des données, ce qui est important pour respecter les obligations de sécurité et de conformité.

**PDN pour SharePoint Online et OneDrive Entreprise** Cette PDV est utilisée pour chiffrer le contenu stocké dans SPO et OneDrive Entreprise, y compris Microsoft Teams fichiers stockés dans SPO. Si vous utilisez la fonctionnalité multigéogé, vous pouvez créer un PD DEP par géo pour votre organisation. Si vous n’utilisez pas la fonctionnalité multigéogé, vous ne pouvez créer qu’un seul dep par client. Reportez-vous aux détails dans [Configurer la clé client.](customer-key-set-up.md)

### <a name="encryption-ciphers-used-by-customer-key"></a>Chiffrements de chiffrement utilisés par la clé client

La clé client utilise différents chiffrements de chiffrement pour chiffrer les clés, comme illustré dans les figures suivantes.

La hiérarchie clé utilisée pour les dep qui chiffrent des données pour plusieurs charges de travail Microsoft 365 est similaire à la hiérarchie utilisée pour les dep pour les boîtes aux lettres Exchange Online individuelles. La seule différence est que la clé de boîte aux lettres est remplacée par la clé Microsoft 365 charge de travail correspondante.

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Chiffrements de chiffrement utilisés pour chiffrer les clés pour Exchange Online et Skype Entreprise

![Chiffrements de chiffrement pour Exchange Online clé client](../media/customerkeyencryptionhierarchiesexchangeskype.png)

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Chiffrements de chiffrement utilisés pour chiffrer les clés pour SharePoint en ligne, OneDrive Entreprise et Teams fichiers

![Chiffrements de chiffrement pour SharePoint client en ligne](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>Articles connexes

- [Configurer la clé client](customer-key-set-up.md)

- [Gérer la clé client](customer-key-manage.md)

- [Echanger ou alterner entre une clé client ou de disponibilité](customer-key-availability-key-roll.md)

- [En savoir plus sur la clé de disponibilité](customer-key-availability-key-understand.md)

- [Référentiel sécurisé client](customer-lockbox-requests.md)

- [Chiffrement de service](office-365-service-encryption.md)