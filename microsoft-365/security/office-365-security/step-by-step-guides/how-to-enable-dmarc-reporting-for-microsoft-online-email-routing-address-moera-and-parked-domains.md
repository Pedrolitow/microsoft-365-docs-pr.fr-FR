---
title: Comment activer la création de rapports DMARC pour Microsoft Online Email l’adresse de routage (MOERA) et les domaines parqués
description: Étapes de configuration de DMARC pour MOERA et les domaines parqués.
search.product: ''
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-guidance-templates
- m365-security
- tier3
ms.topic: how-to
ms.subservice: mdo
search.appverid: met150
ms.openlocfilehash: 73b5c3aa284d16ec57156d2e0fe8c39f5d54619e
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68229193"
---
# <a name="how-to-enable-dmarc-reporting-for-microsoft-online-email-routing-address-moera-and-parked-domains"></a>Comment activer la création de rapports DMARC pour Microsoft Online Email l’adresse de routage (MOERA) et les domaines parqués

La meilleure pratique pour la protection de la sécurité des e-mails de domaine consiste à vous protéger contre l’usurpation à l’aide de l’authentification, de la création de rapports et de la conformité (DMARC) basée sur le domaine. Si vous n’avez pas encore activé DMARC pour vos domaines, il doit s’agir de la première étape, détaillée ici : [Authentification de message basée sur un domaine, création de rapports et conformité (DMARC)](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)

Ce guide est conçu pour vous aider à configurer DMARC pour les domaines non couverts par l’article DMARC principal. Ces domaines incluent des domaines que vous n’utilisez pas pour l’e-mail, mais qui peuvent être exploités par des attaquants s’ils restent non protégés :

- Votre `onmicrosoft.com` domaine, également appelé domaine MoERA (Microsoft Online Email Routing Address).
- Domaines personnalisés parqués que vous n’utilisez pas encore pour l’e-mail.

## <a name="what-youll-need"></a>Ce dont vous aurez besoin

- Centre d'administration Microsoft 365 et l’accès à votre fournisseur DNS hébergeant vos domaines.
- Autorisations suffisantes en tant que Administration globales pour apporter les modifications appropriées dans le Centre d'administration Microsoft 365.
- 10 minutes pour effectuer les étapes décrites dans cet article.

## <a name="activate-dmarc-for-moera-domain"></a>Activer DMARC pour le domaine MOERA

1. Ouvrez le Centre d’administration Microsoft 365 à <https://admin.microsoft.com>.
1. Dans le volet de navigation de gauche, sélectionnez **Afficher tout**.
1. Développez **Paramètres** et appuyez sur **Domaines**.
1. Sélectionnez votre domaine de locataire (par exemple, contoso.onmicrosoft.com).
1. Dans la page qui se charge, sélectionnez **enregistrements DNS**.
1. Sélectionnez **+ Ajouter un enregistrement**.
1. Un menu volant s’affiche à droite. Vérifiez que le type sélectionné est **TXT (Text).**
1. Ajouter `_dmarc` en tant que **nom TXT**.
1. Ajoutez votre valeur DMARC spécifique.
1. Appuyez sur **Enregistrer**.

## <a name="active-dmarc-for-parked-domains"></a>DMARC actif pour les domaines parqués

1. Vérifiez si SPF est déjà configuré pour votre domaine parqué. Pour obtenir des instructions, consultez [Configurer SPF pour empêcher l’usurpation d’identité - Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing#how-to-handle-subdomains)
1. Contactez votre fournisseur de domaine DNS.
1. Demandez à ajouter cet enregistrement Txt DMARC avec vos adresses e-mail appropriées : `v=DMARC1; p=reject; rua=mailto:d@rua.contoso.com;ruf=mailto:d@ruf.contoso.com`.

## <a name="next-steps"></a>Étapes suivantes

Attendez que les modifications DNS soient propagées et essayez d’usurper les domaines configurés. Vérifiez si la tentative est bloquée en fonction de l’enregistrement DMARC et si vous recevez un rapport DMARC.

## <a name="more-information"></a>Informations supplémentaires

[Configurer SPF pour empêcher l’usurpation d’identité - Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing)

[Utiliser DMARC pour valider l’e-mail, les étapes de configuration - Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)
