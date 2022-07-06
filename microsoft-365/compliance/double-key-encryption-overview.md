---
title: Vue d’ensemble du chiffrement à deux clés et FAQ
description: Forum aux questions sur le chiffrement à double clé.
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 02/28/2022
ms.topic: conceptual
ms.service: information-protection
audience: Admin
ms.reviewer: esaggese
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.openlocfilehash: c42104ccb74aba71b143d1ee31b0ed5893d9396f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641831"
---
# <a name="double-key-encryption-frequently-asked-questions"></a>Questions fréquentes sur le chiffrement à double clé

Vous avez une question sur le fonctionnement du chiffrement à double clé ? Recherchez une réponse ici.

## <a name="what-is-double-key-encryption-dke"></a>Qu’est-ce que le chiffrement à double clé (DKE) ?

Double Key Encryption permet aux clients de protéger leurs données hautement sensibles pour répondre à des exigences spécialisées. Il vous aide à maintenir le contrôle total de leurs clés de chiffrement. Il utilise deux clés pour protéger les données ; une clé dans votre contrôle et une deuxième clé stockée en toute sécurité dans Microsoft Azure. L’affichage des données protégées par le chiffrement à double clé nécessite l’accès aux deux clés. Étant donné que Microsoft ne peut accéder qu’à l’une de ces clés, les données protégées restent inaccessibles à Microsoft, ce qui garantit un contrôle total sur la confidentialité et la sécurité de vos données.  

Vous pouvez héberger le service de chiffrement à double clé utilisé pour demander votre clé, à l’emplacement de votre choix (serveur d’administration de clés local ou dans le cloud). Vous gérez le service comme vous le feriez pour toute autre application. Double Key Encryption vous permet de contrôler l’accès au service Double Key Encryption. Vous pouvez stocker vos données hautement sensibles localement ou les déplacer vers le cloud. Vous pouvez être sûr d’empêcher l’accès tiers, car vous conservez le contrôle total de votre clé. Double Key Encryption vous permet de stocker vos données et votre clé au même emplacement.

DKE vous aide à répondre aux exigences réglementaires de plusieurs réglementations et normes telles que le Règlement général sur la protection des données (RGPD), la Loi HIPAA (Health Insurance Portability and Accountability Act), la Loi Gramm-Leach-Bliley (GLBA), la loi russe sur la localisation des données – Loi fédérale n° . 242-FZ, loi fédérale de 1988 sur la protection des renseignements personnels de l’Australie et loi de 1993 sur la protection des renseignements personnels de la Nouvelle-Zélande.

## <a name="can-i-use-double-key-encryption-with-microsoft-office-built-in-sensitivity-labeling"></a>Puis-je utiliser le chiffrement à double clé avec l’étiquetage de confidentialité intégré à Microsoft Office ?

Vous devez utiliser azure Information Protection client d’étiquetage unifié pour protéger les documents avec le chiffrement à double clé. Actuellement, vous ne pouvez pas utiliser l’étiquetage de confidentialité intégré à Microsoft Office.

## <a name="what-microsoft-365-apps-can-i-use-with-dke"></a>Quels Microsoft 365 Apps puis-je utiliser avec DKE ?

Vous pouvez utiliser des étiquettes DKE pour protéger les documents à l’aide des versions de bureau de Word, Excel et PowerPoint sur Windows. Vérifiez que vous utilisez *.12711 ou version ultérieure (versions de bureau de Word, PowerPoint et Excel) sur Windows.

## <a name="how-is-double-key-encryption-different-from-the-existing-hold-your-own-key-hyok-solution"></a>En quoi le chiffrement à double clé diffère-t-il de la solution HYOK (Hold Your Own Key) existante ?

Double Key Encryption chiffre vos données avec deux clés. Votre clé de chiffrement se trouve dans votre contrôle et la deuxième clé est stockée dans Microsoft Azure, ce qui vous permet de déplacer vos données chiffrées vers le cloud. HYOK protège votre contenu avec une seule clé et la clé est toujours locale.  

## <a name="can-double-key-encrypted-documents-be-shared-externally"></a>Les documents chiffrés à double clé peuvent-ils être partagés en externe ?

Vous pouvez partager des documents chiffrés à double clé avec des utilisateurs sur un locataire distinct tant que ces utilisateurs :

- Disposez de l’autorisation requise pour accéder à votre clé dans votre service de chiffrement à double clé.

- Disposez de l’autorisation requise pour accéder à votre clé dans Microsoft Azure.

## <a name="what-happens-to-documents-that-are-protected-with-hyok"></a>Qu’advient-il des documents protégés par HYOK ?

Le déploiement du chiffrement à double clé n’affecte pas votre configuration HYOK existante. Toutefois, nous vous recommandons de commencer à utiliser le chiffrement à double clé en parallèle avec HYOK.

## <a name="can-i-run-double-key-encryption-in-my-non-microsoft-air-gapped-environment"></a>Puis-je exécuter le chiffrement à double clé dans mon environnement non géré par l’air microsoft ?

DKE ne prend pas en charge ces environnements, car le service nécessite l’accès à Microsoft Azure.

## <a name="where-can-i-store-double-key-encrypted-documents"></a>Où puis-je stocker des documents chiffrés à double clé ?

Vous pouvez stocker des documents chiffrés à double clé localement ou dans le cloud. Dans le cloud, vous pouvez déplacer du contenu chiffré vers SharePoint Online et OneDrive Entreprise. Étant donné que Microsoft n’a pas accès à votre clé privée, les données chiffrées restent opaques pour Microsoft. Cela signifie également que vous ne pouvez pas afficher les documents chiffrés en ligne dans Office Web Apps.

## <a name="what-regions-and-languages-is-double-key-encryption-available-in-is-double-key-encryption-available-worldwide"></a>Dans quelles régions et langues double chiffrement à clé est-il disponible ? Double Key Encryption est-il disponible dans le monde entier ?

Les étiquettes DKE sont localisées dans les mêmes langues que les autres étiquettes de confidentialité dans Protection des données Microsoft Purview. Double Key Encryption est disponible dans le monde entier.

## <a name="can-i-convert-a-non-dke-label-to-a-dke-label"></a>Puis-je convertir une étiquette non DKE en étiquette DKE ?

Non. Vous ne pouvez pas ajouter DKE à une étiquette après l’avoir créée. Au lieu de cela, vous devez choisir **Utiliser le chiffrement à double clé** et fournir l’URL de votre service Double Key Encryption lorsque vous créez l’étiquette.

## <a name="how-do-i-roll-my-dke-keys"></a>Comment faire rouler mes clés DKE ?

Pour obtenir des instructions sur le déploiement (également appelé rotation ou rekeying) de la clé que vous stockez dans Azure, consultez [Opérations pour votre clé de locataire Azure Information Protection](/azure/information-protection/operations-customer-managed-tenant-key).

Pour plus d’informations sur la création d’une clé pour le service DKE, consultez les [paramètres du locataire et](double-key-encryption.md#tenant-and-key-settings) de la clé.

Lorsque vous créez une clé, vous configurez un nom et un GUID. Ensuite, si vous faites pivoter une clé, vous conservez l’ancien enregistrement avec le nom et le GUID, mais ajoutez un nouvel enregistrement portant le même nom mais un GUID différent. La nouvelle clé est définie comme active afin que l’API de clé publique commence à la retourner pour le nouveau chiffrement. Les deux clés sont disponibles pour le déchiffrement afin que le nouveau contenu et l’ancien contenu puissent être déchiffrés.
