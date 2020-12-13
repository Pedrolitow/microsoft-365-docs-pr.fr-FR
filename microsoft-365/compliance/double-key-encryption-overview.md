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
ms.openlocfilehash: 32686e76018d8b6a361ea99e6b00271b9547ed95
ms.sourcegitcommit: 47de4402174c263ae8d70c910ca068a7581d04ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "49663059"
---
# <a name="double-key-encryption-frequently-asked-questions"></a>Forum aux questions sur le chiffrement à double clé

Vous avez une question sur la façon dont le chiffrement à clé double fonctionne ? Recherchez une réponse ici.

## <a name="what-is-double-key-encryption-for-microsoft-365-dke"></a>Qu’est-ce que le chiffrement à double clé pour Microsoft 365 (DKE) ?

Le chiffrement à double clé pour Microsoft 365 permet aux clients de protéger leurs données hautement sensibles afin de répondre à des exigences spécifiques. Elle permet aux clients de maintenir le contrôle total de leurs clés de chiffrement. Il utilise deux clés pour protéger les données ; une clé de votre contrôle et une deuxième clé stockée en toute sécurité dans Microsoft Azure. L’affichage des données protégées avec le chiffrement à double clé nécessite l’accès aux deux clés. Étant donné que Microsoft ne peut accéder qu’à l’une de ces clés, les données protégées restent inaccessibles à Microsoft, garantissant ainsi un contrôle total de la confidentialité et de la sécurité des données.  

Vous pouvez héberger le service de chiffrement à double clé utilisé pour demander votre clé, à l’emplacement de votre choix (serveur de gestion de clés sur site ou dans le Cloud). Vous conservez le service comme vous le feriez pour toute autre application. Le chiffrement à double clé vous permet de contrôler l’accès au service de chiffrement à clé double. Vous pouvez stocker vos données hautement sensibles sur site ou les déplacer vers le Cloud. Vous pouvez être sûr d’empêcher l’accès à des tiers, car vous conservez le contrôle total de votre clé. Le chiffrement à double clé vous permet de stocker vos données et votre clé au même emplacement.

DKE vous aide à respecter les exigences réglementaires selon plusieurs réglementations et normes telles que le règlement général sur la protection des données (RGPD), le HIPAA (Health Insurance Portability and Accountability Act), la loi Gramm-Leach-Bliley Act (GLBA), Loi fédérale sur la localisation des données (loi fédérale locale). 242-FZ, Federal Privacy Act 1988 et la déclaration de confidentialité de la Nouvelle-Zélande (en anglais) 1993.

## <a name="can-i-use-double-key-encryption-with-microsoft-office-built-in-sensitivity-labeling"></a>Puis-je utiliser le chiffrement à clé double avec l’étiquette de sensibilité intégrée de Microsoft Office ?

Vous devez utiliser le client d’étiquetage unifié Azure information protection pour protéger les documents avec le chiffrement à double clé. Actuellement, vous ne pouvez pas utiliser l’étiquette de sensibilité prédéfinie de Microsoft Office.

## <a name="what-microsoft-365-apps-can-i-use-with-dke"></a>Quelles sont les applications Microsoft 365 que je peux utiliser avec DKE ?

Vous pouvez utiliser des étiquettes DKE pour protéger des documents à l’aide des versions de bureau de Word, Excel et PowerPoint sur Windows. Assurez-vous que vous utilisez *. 12711 ou une version ultérieure (versions de bureau de Word, PowerPoint et Excel) sur Windows.

## <a name="how-is-double-key-encryption-different-from-the-existing-hold-your-own-key-hyok-solution"></a>En quoi le chiffrement à double clé est-il différent de la solution de votre propre clé Hold (HYOK) existante ?

Le chiffrement à double clé chiffre vos données à l’aide de deux clés. Votre clé de chiffrement se trouve dans votre contrôle et la deuxième clé est stockée dans Microsoft Azure, ce qui vous permet de déplacer vos données chiffrées dans le Cloud. HYOK protège votre contenu avec une seule clé et la clé est toujours locale.  

## <a name="can-double-key-encrypted-documents-be-shared-externally"></a>Les documents chiffrés à double clé peuvent-ils être partagés en externe ?

Vous pouvez partager des documents chiffrés à deux clés avec des utilisateurs sur un client distinct pour autant que ces utilisateurs :

- Disposer de l’autorisation requise pour accéder à votre clé dans votre service de chiffrement à double clé.

- Disposer de l’autorisation requise pour accéder à votre clé dans Microsoft Azure.

## <a name="what-happens-to-documents-that-are-protected-with-hyok"></a>Qu’arrive-t-il aux documents protégés par HYOK ?

Le déploiement du chiffrement à double clé n’affecte pas votre configuration HYOK existante. Toutefois, nous vous recommandons de commencer à utiliser le chiffrement à double clé en parallèle avec HYOK.

## <a name="can-i-run-double-key-encryption-in-my-non-microsoft-air-gapped-environment"></a>Puis-je exécuter le chiffrement à double clé dans mon environnement non-Microsoft air.

DKE ne prend pas en charge ces environnements, car le service nécessite un accès à Microsoft Azure.

## <a name="where-can-i-store-double-key-encrypted-documents"></a>Où puis-je stocker des documents chiffrés à deux clés ?

Vous pouvez stocker des documents chiffrés à deux clés sur site ou dans le Cloud. Dans le Cloud, vous pouvez déplacer du contenu chiffré vers SharePoint Online et OneDrive entreprise. Étant donné que Microsoft n’a pas accès à votre clé privée, les données chiffrées restent opaques à Microsoft. Cela signifie également que vous ne pouvez pas afficher les documents chiffrés en ligne dans Office Web Apps.

## <a name="what-regions-and-languages-is-double-key-encryption-available-in-is-double-key-encryption-available-worldwide"></a>Dans quelles régions et langues le chiffrement à clé double est-il disponible ? Le chiffrement à clé double est-il disponible dans le monde ?

Les étiquettes DKE sont localisées dans les mêmes langues que les autres étiquettes de confidentialité dans la protection des informations Microsoft. Le chiffrement à double clé est disponible dans le monde entier.

## <a name="can-i-convert-a-non-dke-label-to-a-dke-label"></a>Puis-je convertir une étiquette non DKE en étiquette DKE ?

Non. Vous ne pouvez pas ajouter DKE à une étiquette une fois que vous l’avez créée. Au lieu de cela, vous devez choisir **utiliser le chiffrement à double clé** et fournir l’URL de votre service de chiffrement à double clé lorsque vous créez l’étiquette.

## <a name="how-do-i-roll-my-dke-keys"></a>Comment puis-je lancer mes clés DKE ?

Pour obtenir des instructions sur le laminage (également appelé rotation ou Refrappe) de la clé que vous stockez dans Azure, reportez-vous à la rubrique [Operations for your Azure information protection client Key](https://docs.microsoft.com/azure/information-protection/operations-customer-managed-tenant-key).

Consultez la rubrique [client and Key Settings](double-key-encryption.md#tenant-and-key-settings) pour plus d’informations sur la création d’une nouvelle clé pour le service DKE.

Lorsque vous créez une clé, vous configurez un nom et un GUID. Ensuite, si vous faites pivoter une touche, vous conservez l’ancien enregistrement avec le nom et le GUID, mais ajoutez un nouvel enregistrement avec le même nom, mais un GUID différent. La nouvelle clé est définie comme active afin que l’API de clé publique commence à la renvoyer pour le nouveau chiffrement. Les deux clés sont disponibles pour le déchiffrement afin que le nouveau contenu et l’ancien contenu puissent être déchiffrés.
