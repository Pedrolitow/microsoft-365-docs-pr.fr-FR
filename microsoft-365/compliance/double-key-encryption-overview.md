---
title: Vue d’ensemble du chiffrement à double clé et FAQ
description: Questions fréquemment posées sur le chiffrement à double clé pour Microsoft 365.
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 12/11/2020
ms.topic: conceptual
ms.service: information-protection
audience: Admin
ms.reviewer: esaggese
localization_priority: Normal
ms.collection:
- M365-security-compliance
ms.openlocfilehash: df6d0e98eae9c66d1fc366014f94ff6aeb479e4b36a7f0825982872ce416b6f4
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53842302"
---
# <a name="double-key-encryption-frequently-asked-questions"></a>Double key Encryption frequently asked questions

Vous avez une question sur le fonctionnement du chiffrement à double clé ? Recherchez une réponse ici.

## <a name="what-is-double-key-encryption-for-microsoft-365-dke"></a>Qu’est-ce que le chiffrement à double clé pour Microsoft 365 (DKE) ?

Le chiffrement à double clé Microsoft 365 permet aux clients de protéger leurs données hautement sensibles afin de répondre à des exigences spécialisées. Il permet aux clients de garder un contrôle total sur leurs clés de chiffrement. Il utilise deux clés pour protéger les données ; une clé dans votre contrôle et une seconde clé stockée en toute sécurité dans Microsoft Azure. L’affichage des données protégées par le chiffrement à double clé nécessite l’accès aux deux clés. Étant donné que Microsoft ne peut accéder qu’à l’une de ces clés, les données protégées restent inaccessibles à Microsoft, ce qui garantit que vous avez un contrôle total sur la confidentialité et la sécurité de vos données.  

Vous pouvez héberger le service de chiffrement à double clé utilisé pour demander votre clé, à l’emplacement de votre choix (serveur de gestion de clés local ou dans le cloud). Vous maintenez le service comme vous le feriez pour n’importe quelle autre application. Le chiffrement à double clé vous permet de contrôler l’accès au service de chiffrement à double clé. Vous pouvez stocker vos données hautement sensibles en local ou les déplacer vers le cloud. Vous pouvez être certain d’empêcher l’accès de tiers, car vous conservez un contrôle total de votre clé. Le chiffrement à double clé vous permet de stocker vos données et clé au même emplacement.

Le DKE vous aide à répondre aux exigences réglementaires dans le cadre de plusieurs réglementations et normes telles que le Règlement général sur la protection des données (R GDPR), la loi HIPAA (Health Insurance Portability and Accountability Act), la loi Gramm-Leach-Bliley Act (GLBA), la loi russe sur la localisation des données ( Loi fédérale ndlr). 242-FZ, australia’s Federal Privacy Act 1988, and New Zealand’s Privacy Act 1993.

## <a name="can-i-use-double-key-encryption-with-microsoft-office-built-in-sensitivity-labeling"></a>Puis-je utiliser le chiffrement à double clé Microsoft Office l’étiquetage de sensibilité intégré ?

Vous devez utiliser le client d’étiquetage unifié Azure Information Protection pour protéger les documents avec le chiffrement à double clé. Actuellement, vous ne pouvez pas utiliser Microsoft Office l’étiquetage de sensibilité intégré.

## <a name="what-microsoft-365-apps-can-i-use-with-dke"></a>Quelles Microsoft 365 Apps puis-je utiliser avec DKE ?

Vous pouvez utiliser des étiquettes DKE pour protéger les documents à l’aide des versions de bureau de Word, Excel et PowerPoint sur Windows. Assurez-vous que vous utilisez *.12711 ou version ultérieure (versions de bureau de Word, PowerPoint et Excel) sur Windows.

## <a name="how-is-double-key-encryption-different-from-the-existing-hold-your-own-key-hyok-solution"></a>En quoi le chiffrement à double clé est-il différent de la solution HYOK (Hold your own key) existante ?

Le chiffrement à double clé chiffre vos données avec deux clés. Votre clé de chiffrement est dans votre contrôle et la deuxième clé est stockée dans Microsoft Azure, ce qui vous permet de déplacer vos données chiffrées vers le cloud. HYOK protège votre contenu avec une seule clé et la clé est toujours en local.  

## <a name="can-double-key-encrypted-documents-be-shared-externally"></a>Les documents chiffrés à double clé peuvent-ils être partagés en externe ?

Vous pouvez partager des documents chiffrés à double clé avec des utilisateurs sur un client distinct tant que ces utilisateurs :

- Avoir l’autorisation requise pour accéder à votre clé dans votre service de chiffrement à double clé.

- Avoir l’autorisation requise pour accéder à votre clé dans Microsoft Azure.

## <a name="what-happens-to-documents-that-are-protected-with-hyok"></a>Qu’advient-il des documents protégés avec HYOK ?

Le déploiement du chiffrement à double clé n’affectera pas votre configuration HYOK existante. Toutefois, nous vous recommandons de commencer à utiliser le chiffrement à double clé en parallèle avec HYOK.

## <a name="can-i-run-double-key-encryption-in-my-non-microsoft-air-gapped-environment"></a>Puis-je exécuter le chiffrement à double clé dans mon environnement non-Microsoft ?

DKE ne prend pas en charge ces environnements, car le service nécessite l’accès Microsoft Azure.

## <a name="where-can-i-store-double-key-encrypted-documents"></a>Où puis-je stocker les documents chiffrés à double clé ?

Vous pouvez stocker des documents chiffrés à double clé en local ou dans le cloud. Dans le cloud, vous pouvez déplacer le contenu chiffré vers SharePoint Online et OneDrive Entreprise. Étant donné que Microsoft n’a pas accès à votre clé privée, les données chiffrées restent opaques pour Microsoft. Cela signifie également que vous ne pouvez pas afficher les documents chiffrés en ligne dans Office Web Apps.

## <a name="what-regions-and-languages-is-double-key-encryption-available-in-is-double-key-encryption-available-worldwide"></a>Dans quelles régions et langues le chiffrement à double clé est-il disponible ? Le chiffrement à double clé est-il disponible dans le monde entier ?

Les étiquettes DKE sont localisées dans les mêmes langues que les autres étiquettes de niveau de Protection des données Microsoft. Le chiffrement à double clé est disponible dans le monde entier.

## <a name="can-i-convert-a-non-dke-label-to-a-dke-label"></a>Puis-je convertir une étiquette non DKE en étiquette DKE ?

Non. Vous ne pouvez pas ajouter DKE à une étiquette après l’avoir créé. Au lieu de cela, vous devez choisir Utiliser le chiffrement **à double** clé et fournir l’URL de votre service de chiffrement à double clé lorsque vous créez l’étiquette.

## <a name="how-do-i-roll-my-dke-keys"></a>Comment faire pour déployer mes clés DKE ?

Pour obtenir des instructions sur le déploiement (également appelé rotation ou rekeying) de la clé que vous stockez dans Azure, voir Opérations pour votre clé de [client Azure Information Protection.](/azure/information-protection/operations-customer-managed-tenant-key)

Pour [plus d’informations](double-key-encryption.md#tenant-and-key-settings) sur la création d’une clé pour le service DKE, voir paramètres de client et de clé.

Lorsque vous créez une clé, vous définissez un nom et un GUID. Ensuite, si vous faites pivoter une clé, vous conservez l’ancien enregistrement avec le nom et le GUID, mais ajoutez un nouvel enregistrement avec le même nom mais un GUID différent. La nouvelle clé est définie comme étant active afin que l’API de clé publique commence à la renvoyer pour le nouveau chiffrement. Les deux clés sont disponibles pour le déchiffrement afin que le nouveau contenu et l’ancien contenu soient déchiffrés.