---
title: Techniques et tendances de hameçonnage
ms.reviewer: ''
description: Découvrez comment repérer les techniques de hameçonnage
keywords: sécurité, programmes malveillants, hameçonnage, informations, tentative, ingénierie sociale, loi, leurre, protection, tendances, attaque ciblée, harponnage, whaling
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: fbd86a25b6f1224748225263103e13ca07f93166
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683549"
---
# <a name="phishing-trends-and-techniques"></a>Techniques et tendances de hameçonnage

Les attaques par hameçonnage sont des tentatives qui utilisent souvent une ingénierie sociale ou leurrent du contenu. La communication légitime, généralement le courrier électronique, qui est lié à un site d’hameçonnage est l’une des méthodes les plus courantes utilisées dans les attaques par hameçonnage. Le site d’hameçonnage imite généralement les pages de connexion qui exigent que les utilisateurs entrent les informations d’identification et les informations de compte. Le site de hameçonnage capture ensuite les informations sensibles dès que l’utilisateur les fournit, ce qui permet aux personnes malveillantes d’accéder aux informations.

Voici quelques-unes des techniques de hameçonnage les plus courantes que les personnes malveillantes utiliseront pour essayer de voler des informations ou d’accéder à vos appareils.

## <a name="invoice-phishing"></a>Hameçonnage de facture

Dans cette tentative, l’attaquant tente de vous attirer avec un e-mail indiquant que vous avez une facture en suspens d’un fournisseur ou d’une société connu. Ils vous fournissent ensuite un lien vous permettent d’accéder à votre facture et de la régler. Lorsque vous accédez au site, l’attaquant est autorisé à voler vos informations personnelles et vos fonds.

## <a name="paymentdelivery-scam"></a>Paiement/remise d’une fraude

Vous êtes invité à fournir une carte bancaire ou d’autres informations personnelles afin que vos informations de paiement soient mises à jour avec un fournisseur ou un fournisseur communément connu. La mise à jour est demandée afin que vous pouvez prendre livraison de vos articles commandés. En règle générale, vous êtes peut-être familiarisé avec l’entreprise et vous avez probablement fait des affaires avec elle dans le passé. Toutefois, vous n’avez connaissance d’aucun des éléments que vous avez récemment achetés auprès d’eux.

## <a name="tax-themed-phishing-scams"></a>Tentatives de hameçonnage à base de taxes

Une tentative courante de hameçonnage de l’IRS consiste à recevoir une lettre électronique urgente indiquant que vous devez payer de l’argent à l’IRS. Souvent, l’e-mail menace une action en justice si vous n’accédez pas au site en temps voulu et payez vos taxes. Lorsque vous accédez au site, les personnes malveillantes peuvent voler votre carte bancaire personnelle ou vos informations bancaires et vider vos comptes.

## <a name="downloads"></a>Téléchargements

Un attaquant envoie un e-mail frauduleux vous demandant d’ouvrir ou de télécharger une pièce jointe de document, telle qu’un fichier PDF. La pièce jointe contient souvent un message vous demandant de vous connectez à un autre site, tel que des sites web de messagerie ou de partage de fichiers, pour ouvrir le document. Lorsque vous accédez à ces sites de hameçonnage à l’aide de vos informations d’identification de connexion, l’attaquant a désormais accès à vos informations et peut obtenir des informations personnelles supplémentaires sur vous.

## <a name="phishing-emails-that-deliver-other-threats"></a>E-mails de hameçonnage qui envoient d’autres menaces

Les e-mails de hameçonnage sont souvent efficaces, de sorte que les personnes malveillantes les utilisent parfois pour distribuer des [ransomware](/security/compass/human-operated-ransomware) par le biais de liens ou de pièces jointes dans des e-mails. Lorsqu’il est exécuté, le ransomware chiffre les fichiers et affiche une note de rançon, qui vous demande de payer une somme d’argent pour accéder à vos fichiers.

Nous avons également vu des e-mails de hameçonnage qui ont des liens vers des sites web [d’hameçonnage du support](support-scams.md) technique. Ces sites web utilisent différentes tactiques tactiques pour vous aider à appeler des espions et à payer des « services de support technique » inutiles qui sont censés résoudre les problèmes liés aux appareils, aux plateformes ou aux logiciels.

## <a name="spear-phishing"></a>Hameçonnage

Le harponnage est une attaque ciblée par hameçonnage qui implique du contenu d’hameçonnage hautement personnalisé. En règle générale, les attaquants font des opérations de reconnaissance en sondant les réseaux sociaux et d’autres sources d’informations sur leur cible prévue.

Le harponnage peut impliquer une tentative de connexion à des sites factices et la divulgation d’informations d’identification. Je peux également vous attirer vers l’ouverture de documents en cliquant sur des liens qui installent automatiquement des programmes malveillants. Une fois ce programme malveillant en place, les personnes malveillantes peuvent manipuler à distance l’ordinateur infecté.

Ce programme malveillant sert de point d’entrée pour une attaque plus sophistiquée, appelée menace persistante avancée. Les API sont conçues pour établir un contrôle et voler des données sur de longues périodes. Les attaquants peuvent essayer de déployer des outils de piratage plus ciblés, de se déplacer ultérieurement vers d’autres ordinateurs, de compromettre ou de créer des comptes privilégiés, et d’exfiltrer régulièrement des informations à partir de réseaux compromis.

## <a name="whaling"></a>Whaling

La whaling est une forme de hameçonnage dirigée vers des cadres supérieurs ou supérieurs au sein d’entreprises spécifiques pour accéder à leurs informations d’identification et/ou à leurs informations bancaires. Le contenu de l’e-mail peut être écrit sous la forme d’une obligation légale, d’une réclamation client ou d’un autre problème de direction. Ce type d’attaque peut également entraîner une attaque de l’apts au sein d’une organisation.

## <a name="business-email-compromise"></a>Compromission de la messagerie professionnelle

La compromission de messagerie professionnelle (BEC) est une fraude sophistiquée qui cible les entreprises qui travaillent fréquemment avec des fournisseurs étrangers ou qui font des transferts de virements financiers. L’un des schémas les plus courants utilisés par les personnes malveillantes DUT consiste à accéder au réseau d’une entreprise par le biais d’une attaque par harponnage. L’attaquant crée un domaine similaire à la société qu’il cible, ou usurpe son adresse de messagerie pour escroquer les utilisateurs en leur libérant des informations de compte personnel pour des transferts d’argent.

## <a name="more-information-about-phishing-attacks"></a>Plus d’informations sur les attaques par hameçonnage

Pour plus d’informations sur les dernières attaques par hameçonnage, les techniques et les tendances, vous pouvez lire ces entrées sur le [blog sécurité Microsoft](https://www.microsoft.com/security/blog/product/windows/) :

- [Les hameçonneurs libérent des techniques d’ingénierie sociale simples mais efficaces à l’aide de pièces jointes PDF](https://cloudblogs.microsoft.com/microsoftsecure/2017/01/26/phishers-unleash-simple-but-effective-social-engineering-techniques-using-pdf-attachments/?source=mmpc)
- [Tax themed phishing and malware attacks proliferate during the tax filing season](https://cloudblogs.microsoft.com/microsoftsecure/2017/03/20/tax-themed-phishing-and-malware-attacks-proliferate-during-the-tax-filing-season/?source=mmpc)
- [Le hameçonnage comme les e-mails entraîne une tentative de support technique](https://cloudblogs.microsoft.com/microsoftsecure/2017/08/07/links-in-phishing-like-emails-lead-to-tech-support-scam/?source=mmpc)
