---
title: Chiffrement de données dans OneDrive Entreprise et SharePoint Online
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 9/20/2021
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 6501b5ef-6bf7-43df-b60d-f65781847d6c
ms.collection:
- purview-compliance
- SPO_Content
- tier2
description: Maîtrisez les notions de base du chiffrement de la sécurité de données dans OneDrive Entreprise et SharePoint Online.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b33bbe22e5bf606bcc71b6308c5fce3e0c68a542
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68621742"
---
# <a name="data-encryption-in-onedrive-for-business-and-sharepoint-online"></a>Chiffrement de données dans OneDrive Entreprise et SharePoint Online

Maîtrisez les notions de base du chiffrement de la sécurité de données dans OneDrive Entreprise et SharePoint Online.
  
[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="security-and-data-encryption-in-office-365"></a>Sécurité et chiffrement des données dans Office 365

Microsoft 365 est un environnement hautement sécurisé qui offre une protection étendue en plusieurs couches : sécurité des centres de données physiques, sécurité réseau, sécurité des accès, sécurité des applications et sécurité des données. Cet article s'intéresse plus particulièrement à l'aspect du chiffrement de la sécurité des données lors de leur transport et de leur stockage pour OneDrive Entreprise et SharePoint Online.
  
Observez le fonctionnement du chiffrement des données dans la vidéo suivante.
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/dea0dec4-4077-4095-9a32-19b94ea2da4b?autoplay=false]
  
## <a name="encryption-of-data-in-transit"></a>Chiffrement des données lors de leur transport

Dans OneDrive Entreprise et SharePoint Online, il existe deux scénarios dans lesquels les données entrent et sortent des centres de données.
  
- **Client communication with the server** Communication to OneDrive for Business across the Internet uses SSL/TLS connections. All SSL connections are established using 2048-bit keys.

- **Data movement between datacenters** The primary reason to move data between datacenters is for geo-replication to enable disaster recovery. For instance, SQL Server transaction logs and blob storage deltas travel along this pipe. While this data is already transmitted by using a private network, it is further protected with best-in-class encryption. 

## <a name="encryption-of-data-at-rest"></a>Chiffrement des données lors de leur stockage

Le chiffrement lors du stockage comprend deux composants : le chiffrement au niveau du disque BitLocker et le chiffrement par fichier du contenu client.
  
BitLocker est déployé pour OneDrive Entreprise et SharePoint Online sur l'ensemble du service. Le chiffrement par fichier est également dans OneDrive Entreprise et SharePoint Online dans Microsoft 365 multilocataire et de nouveaux environnements dédiés basés sur la technologie mutualisée.
  
Alors que BitLocker chiffre toutes les données sur un disque, le chiffrement par fichier va plus loin en ajoutant une clé de chiffrement unique pour chaque fichier. En outre, chaque mise à jour de chaque fichier est chiffrée à l’aide de sa propre clé de chiffrement. Les clés du contenu chiffré sont stockées dans un emplacement physiquement distinct du contenu. Chaque étape de ce chiffrement utilise la méthode AES (Advanced Encryption Standard) avec des clés 256 bits et est conforme à la norme FIPS (Federal Information Processing Standard) 140-2. Le contenu chiffré est réparti sur un certain nombre de conteneurs dans l’ensemble du centre de données, et chaque conteneur possède des informations d’identification uniques. Ces informations sont stockées dans un emplacement physique distinct du contenu ou des clés de contenu.
  
Pour plus d’informations sur la conformité FIPS 140-2, consultez [CONFORMITÉ FIPS 140-2](/previous-versions/sql/sql-server-2008-r2/bb326611(v=sql.105)).
  
File-level encryption at rest takes advantage of blob storage to provide for virtually unlimited storage growth and to enable unprecedented protection. All customer content in OneDrive for Business and SharePoint Online will be migrated to blob storage. Here's how that data is secured:
  
1. All content is encrypted, potentially with multiple keys, and distributed across the datacenter. Each file to be stored is broken into one or more chunks, depending its size. Then, each chunk is encrypted using its own unique key. Updates are handled similarly: the set of changes, or deltas, submitted by a user is broken into chunks, and each is encrypted with its own key.

2. All of these chunks—files, pieces of files, and update deltas—are stored as blobs in our blob store. They also are randomly distributed across multiple blob containers.

3. La « carte » utilisée pour ré-assembler le fichier à partir de ses composants est stockée dans la base de données de contenu.

4. Each blob container has its own unique credentials per access type (read, write, enumerate, and delete). Each set of credentials is held in the secure Key Store and is regularly refreshed.

En d’autres termes, trois types de magasins sont impliqués dans le chiffrement par fichier lors du stockage, chacun doté d’une fonction distincte :
  
- Content is stored as encrypted blobs in the blob store. The key to each chunk of content is encrypted and stored separately in the content database. The content itself holds no clue as to how it can be decrypted.

- The Content Database is a SQL Server database. It holds the map required to locate and reassemble all of the content blobs held in the blob store as well as the keys needed to decrypt those blobs.

Each of these three storage components—the blob store, the Content Database, and the Key Store—is physically separate. The information held in any one of the components is unusable on its own. This provides an unprecedented level of security. Without access to all three it is impossible to retrieve the keys to the chunks, decrypt the keys to make them usable, associate the keys with their corresponding chunks, decrypt any chunk, or reconstruct a document from its constituent chunks.
