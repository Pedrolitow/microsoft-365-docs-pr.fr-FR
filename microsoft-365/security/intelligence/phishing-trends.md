---
title: Tendances et techniques d’hameçonnage
ms.reviewer: ''
description: En savoir plus sur la détection des techniques de hameçonnage
keywords: sécurité, programmes malveillants, hameçonnage, informations, escroquerie, ingénierie sociale, appât, leurre, protection, tendances, attaque ciblée, harponnage, chasse à la baleine
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
ms.openlocfilehash: c56478f4dbe496f7e2080e9c73d6466df0e2c5d7
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666743"
---
# <a name="phishing-trends-and-techniques"></a>Tendances et techniques d’hameçonnage

Les attaques par hameçonnage sont des escroqueries qui utilisent souvent des appâts d’ingénierie sociale ou du contenu de leurre. La communication légitime, généralement par e-mail, qui établit des liens vers un site de hameçonnage est l’une des méthodes les plus courantes utilisées dans les attaques par hameçonnage. Le site de hameçonnage imite généralement les pages de connexion qui nécessitent que les utilisateurs entrent des informations d’identification et des informations de compte. Le site de hameçonnage capture ensuite les informations sensibles dès que l’utilisateur les fournit, ce qui donne aux attaquants l’accès aux informations.

Voici quelques-unes des techniques de hameçonnage les plus courantes utilisées par les attaquants pour tenter de voler des informations ou d’accéder à vos appareils.

## <a name="invoice-phishing"></a>Hameçonnage de facture

Dans cette escroquerie, l’attaquant tente de vous attirer avec un e-mail indiquant que vous avez une facture en attente d’un fournisseur ou d’une société connu. Ils fournissent ensuite un lien pour vous permettre d’accéder à votre facture et de la payer. Lorsque vous accédez au site, l’attaquant est prêt à voler vos informations personnelles et vos fonds.

## <a name="paymentdelivery-scam"></a>Escroquerie de paiement/remise

Vous êtes invité à fournir une carte de crédit ou d’autres informations personnelles afin que vos informations de paiement puissent être mises à jour avec un fournisseur ou un fournisseur connu. La mise à jour est demandée afin que vous puissiez prendre la livraison de vos articles commandés. En règle générale, vous êtes peut-être familiarisé avec l’entreprise et vous avez probablement fait affaire avec elle par le passé. Toutefois, vous n’êtes au courant d’aucun article que vous avez acheté récemment auprès d’eux.

## <a name="tax-themed-phishing-scams"></a>Hameçonnage sur le thème de l’impôt

Une tentative courante d’hameçonnage IRS reçoit une lettre électronique urgente indiquant que vous devez de l’argent à l’IRS. Souvent, l’e-mail menace une action en justice si vous n’accédez pas au site en temps voulu et payez vos impôts. Lorsque vous accédez au site, les attaquants peuvent voler votre carte de crédit personnelle ou vos informations bancaires et vider vos comptes.

## <a name="downloads"></a>Téléchargements

Un attaquant envoie un e-mail frauduleux vous demandant d’ouvrir ou de télécharger une pièce jointe de document, telle qu’un fichier PDF. La pièce jointe contient souvent un message vous demandant de vous connecter à un autre site, tel que des sites web de partage de fichiers ou d’e-mail, pour ouvrir le document. Lorsque vous accédez à ces sites de hameçonnage à l’aide de vos informations d’identification de connexion, l’attaquant a désormais accès à vos informations et peut obtenir des informations personnelles supplémentaires sur vous.

## <a name="phishing-emails-that-deliver-other-threats"></a>E-mails de hameçonnage qui fournissent d’autres menaces

Les e-mails d’hameçonnage étant souvent efficaces, les attaquants les utilisent parfois pour distribuer des [ransomware](/security/compass/human-operated-ransomware) par le biais de liens ou de pièces jointes dans les e-mails. Lors de l’exécution, le ransomware chiffre les fichiers et affiche une note de rançon, qui vous demande de payer une somme d’argent pour accéder à vos fichiers.

Nous avons également vu des e-mails de hameçonnage qui ont des liens vers des sites web [de support technique escroquerie](support-scams.md) . Ces sites web utilisent différentes tactiques de peur pour vous inciter à appeler des lignes d’assistance et de payer pour les « services de support technique » inutiles qui soi-disant résoudre les problèmes d’appareil, de plateforme ou de logiciels dérivés.

## <a name="spear-phishing"></a>Hameçonnage

Le harponnage est une attaque par hameçonnage ciblée qui implique un contenu d’leurre hautement personnalisé. Les attaquants effectuent généralement un travail de reconnaissance en interrogeant les médias sociaux et d’autres sources d’informations sur leur cible prévue.

L’hameçonnage par lance peut impliquer de vous inciter à vous connecter à de faux sites et à divulguer des informations d’identification. Je peux également vous inciter à ouvrir des documents en cliquant sur les liens qui installent automatiquement les programmes malveillants. Avec ce programme malveillant en place, les attaquants peuvent manipuler à distance l’ordinateur infecté.

Le programme malveillant implanté sert de point d’entrée pour une attaque plus sophistiquée, connue sous le nom de menace persistante avancée (APT). Les API sont conçues pour établir le contrôle et voler des données sur des périodes prolongées. Les attaquants peuvent essayer de déployer des outils de piratage plus secrètes, de se déplacer latéralement vers d’autres ordinateurs, de compromettre ou de créer des comptes privilégiés, et d’exfiltrer régulièrement des informations à partir de réseaux compromis.

## <a name="whaling"></a>Baleinière

La chasse à la baleine est une forme de hameçonnage destinée aux cadres supérieurs ou de haut niveau au sein d’entreprises spécifiques pour accéder à leurs informations d’identification et/ou à leurs informations bancaires. Le contenu de l’e-mail peut être écrit sous la forme d’une assignation légale, d’une plainte du client ou d’un autre problème de direction. Ce type d’attaque peut également entraîner une attaque APT au sein d’une organisation.

## <a name="business-email-compromise"></a>Compromission de la messagerie professionnelle

La compromission par e-mail d’entreprise (BEC) est une escroquerie sophistiquée qui cible les entreprises qui travaillent fréquemment avec des fournisseurs étrangers ou effectuent des transferts bancaires d’argent. L’un des schémas les plus courants utilisés par les attaquants bec implique d’accéder au réseau d’une entreprise par le biais d’une attaque par hameçonnage par lance. L’attaquant crée un domaine similaire à l’entreprise qu’il cible, ou usurpe son adresse e-mail pour arnaquer les utilisateurs en publiant des informations de compte personnel pour les transferts d’argent.

## <a name="more-information-about-phishing-attacks"></a>Plus d’informations sur les attaques par hameçonnage

Pour plus d’informations sur les dernières attaques par hameçonnage, les techniques et les tendances, vous pouvez lire ces entrées sur le [blog Microsoft Security](https://www.microsoft.com/security/blog/product/windows/) :

- [Les hameçonneurs libèrent des techniques d’ingénierie sociale simples mais efficaces à l’aide de pièces jointes PDF](https://cloudblogs.microsoft.com/microsoftsecure/2017/01/26/phishers-unleash-simple-but-effective-social-engineering-techniques-using-pdf-attachments/?source=mmpc)
- [Les attaques de hameçonnage et de programmes malveillants à thème fiscal prolifèrent pendant la saison des déclarations de revenus](https://cloudblogs.microsoft.com/microsoftsecure/2017/03/20/tax-themed-phishing-and-malware-attacks-proliferate-during-the-tax-filing-season/?source=mmpc)
- [Le hameçonnage comme les e-mails entraîne une arnaque de support technique](https://cloudblogs.microsoft.com/microsoftsecure/2017/08/07/links-in-phishing-like-emails-lead-to-tech-support-scam/?source=mmpc)
