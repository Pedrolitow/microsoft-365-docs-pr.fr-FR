---
title: Comment se protéger contre les attaques par hameçonnage
ms.reviewer: ''
description: Découvrez comment fonctionnent les hameçonnages, fournissez des programmes malveillants sur vos appareils et ce que vous pouvez faire pour vous protéger
keywords: sécurité, programmes malveillants, hameçonnage, informations, escroquerie, ingénierie sociale, appât, leurre, protection, tendances, attaque ciblée
ms.service: microsoft-365-security
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
ms.openlocfilehash: dda1cd5d25d75132cb6e04ad5dd7c365c4bb15ed
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67739033"
---
# <a name="how-to-protect-against-phishing-attacks"></a>Comment se protéger contre les attaques par hameçonnage

Les attaques d’hameçonnage tentent de dérober des informations sensibles par le biais de courriels, de sites web, de messages texte ou d'autres formes de communication électronique. Ils essaient de ressembler à des communications officielles d’entreprises ou d’individus légitimes.

Les cybercriminels tentent souvent de voler des noms d’utilisateur, des mots de passe, des détails de carte de crédit, des informations de compte bancaire ou d’autres informations d’identification. Ils utilisent des informations volées à des fins malveillantes, telles que le piratage, l’usurpation d’identité ou le vol d’argent directement à partir de comptes bancaires et de cartes de crédit. L’information peut également être vendue sur les marchés cybercriminels souterrains.

Les attaques d’ingénierie sociale sont conçues pour tirer parti de la prise de décision possible d’un utilisateur. N’oubliez pas et ne fournissez jamais d’informations sensibles ou personnelles par e-mail ou par des sites web inconnus, ou par téléphone. N’oubliez pas que les e-mails de hameçonnage sont conçus pour paraître légitimes.

## <a name="learn-the-signs-of-a-phishing-scam"></a>Découvrir les signes d’une escroquerie par hameçonnage

La meilleure protection est la sensibilisation et l’éducation. N’ouvrez pas de pièces jointes ou de liens dans des e-mails non sollicités, même si les e-mails proviennent d’une source reconnue. Si l’e-mail est inattendu, méfiez-vous de l’ouverture de la pièce jointe et vérifiez l’URL.

Les entreprises doivent éduquer et former leurs employés à se méfier de toute communication qui demande des informations personnelles ou financières. Ils doivent également indiquer aux employés de signaler immédiatement la menace à l’équipe des opérations de sécurité de l’entreprise.

Voici plusieurs signes révélateurs d’une escroquerie par hameçonnage :

* Les liens ou URL fournis dans les e-mails **ne pointent pas vers l’emplacement approprié** ou pointent vers un site tiers non affilié à l’expéditeur de l’e-mail. Par exemple, dans l’image ci-dessous, l’URL fournie ne correspond pas à l’URL vers laquelle vous serez redépointé.

    ![exemple de pointage sur une URL.](../../media/security-intelligence-images/url-hover.png)

* Il y a une **demande d’informations personnelles** telles que des numéros de sécurité sociale ou des informations bancaires ou financières. En règle générale, les communications officielles ne vous demandent pas d’informations personnelles sous la forme d’un e-mail.

* **Les éléments de l’adresse e-mail seront modifiés** afin qu’ils soient suffisamment similaires à une adresse e-mail légitime, mais qu’ils ont ajouté des numéros ou des lettres modifiées.

* Le message est **inattendu et non sollicité**. Si vous recevez soudainement un e-mail d’une entité ou d’une personne avec laquelle vous traitez rarement, considérez ce suspect de courrier électronique.

* Le message ou la pièce jointe vous demande **d’activer des macros, d’ajuster les paramètres de sécurité ou d’installer des applications**. Les e-mails normaux ne vous demandent pas de le faire.

* Le message contient des **erreurs**. Les messages d’entreprise légitimes sont moins susceptibles d’avoir des erreurs typographiques ou grammaticales ou de contenir des informations incorrectes.

* **L’adresse de l’expéditeur ne correspond pas à la signature** du message lui-même. Par exemple, un e-mail est censé être de Marie de Contoso Corp, mais l’adresse de l’expéditeur est john<span></span>@example.com.

* Il existe **plusieurs destinataires** dans le champ « À » et il semble qu’il s’agit d’adresses aléatoires. Les messages d’entreprise sont normalement envoyés directement à des destinataires individuels.

* Le message **d’accueil lui-même ne vous adresse pas personnellement**. Outre les messages qui adressent par erreur une autre personne, les messages d’accueil qui abusent de votre nom ou tirent votre nom directement de votre adresse e-mail ont tendance à être malveillants.

* Le site web semble familier, mais il ya **des incohérences ou des choses qui ne sont pas tout à fait correct**. Les signes d’avertissement incluent des logos obsolètes, des fautes de frappe ou demandent aux utilisateurs de fournir des informations supplémentaires qui ne sont pas demandées par les sites web de connexion légitimes.

* La page qui s’ouvre **n’est pas une page en direct**, mais plutôt une image conçue pour ressembler au site que vous connaissez. Une fenêtre contextuelle peut apparaître pour demander des informations d’identification.

En cas de doute, contactez l’entreprise par des canaux connus pour vérifier si des e-mails suspects sont en fait légitimes.

## <a name="software-solutions-for-organizations"></a>Solutions logicielles pour les organisations

* [Microsoft Edge](/microsoft-edge/deploy/index) et [Protection d'application Windows Defender](/windows/security/microsoft-defender-application-guard/md-app-guard-overview.md) offrent une protection contre la menace croissante d’attaques ciblées à l’aide de la technologie de virtualisation Hyper-V de pointe de Microsoft. Si un site web parcouru est considéré comme non approuvé, le conteneur Hyper-V isole cet appareil du reste de votre réseau, empêchant ainsi l’accès aux données de votre entreprise.

* [Microsoft Exchange Online Protection (EOP) offre une](https://products.office.com/exchange/exchange-email-security-spam-protection) fiabilité et une protection de classe entreprise contre le courrier indésirable et les programmes malveillants, tout en conservant l’accès aux e-mails pendant et après les urgences.  À l’aide de différentes couches de filtrage, EOP peut fournir différents contrôles pour le filtrage du courrier indésirable, tels que les contrôles de courrier en bloc et le courrier indésirable international, qui amélioreront davantage vos services de protection.

* Utilisez [Microsoft Defender pour Office 365](https://products.office.com/exchange/online-email-threat-protection?ocid=cx-blog-mmpc) afin de protéger vos e-mails, fichiers et stockage en ligne contre les programmes malveillants. Il offre une protection holistique dans Microsoft Teams, Word, Excel, PowerPoint, Visio, SharePoint Online et OneDrive Entreprise. En protégeant contre les pièces jointes non sécurisées et en développant la protection contre les liens malveillants, il complète les fonctionnalités de sécurité de Exchange Online Protection pour fournir une meilleure protection zéro jour.

## <a name="what-to-do-if-youve-been-a-victim-of-a-phishing-scam"></a>Que faire si vous avez été victime d’une escroquerie par hameçonnage

Si vous pensez avoir été victime d’une attaque par hameçonnage :

1. Contactez votre administrateur informatique si vous êtes sur un ordinateur professionnel
2. Modifier immédiatement tous les mots de passe associés aux comptes
3. Signaler toute activité frauduleuse à votre banque et à votre société de cartes de crédit

### <a name="reporting-spam"></a>Signalement de courrier indésirable

- **Outlook.com** : Si vous recevez un e-mail suspect qui vous demande des informations personnelles, cochez la case en regard du message dans votre boîte de réception Outlook. Sélectionnez la flèche en regard de **Junk**, puis sélectionnez **Phishing**.

- **Microsoft Office Outlook** : dans le message suspect, sélectionnez **Signaler le message** dans le ruban, puis sélectionnez **Hameçonnage**.

- **Microsoft 365** : Utilisez le [portail soumissions dans Microsoft 365 Defender](/microsoft-365/security/office-365-security/report-junk-email-messages-to-microsoft) pour envoyer l’exemple de courrier indésirable ou de hameçonnage à Microsoft à des fins d’analyse. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](/microsoft-365/security/office-365-security/report-junk-email-messages-to-microsoft).

- **Groupe de travail anti-hameçonnage** : phishing-report@us-cert.gov. Le groupe utilise des rapports générés à partir d’e-mails envoyés pour lutter contre les escroqueries par hameçonnage et les pirates informatiques. Les fournisseurs d’identité, les fournisseurs de sécurité, les institutions financières et les organismes d’application de la loi sont impliqués.

### <a name="if-youre-on-a-suspicious-website"></a>Si vous êtes sur un site web suspect

- **Microsoft Edge** : lorsque vous êtes sur un site suspect, sélectionnez **l’icône** >  Plus (...)**Aide et commentaires** > **sur le site Non sécurisé**. Suivez les instructions de la page web qui s’affiche pour signaler le site web.

- **Internet Explorer** : lorsque vous êtes sur un site suspect, sélectionnez l’icône d’engrenage, pointez sur **Sécurité**, puis sélectionnez **Signaler un site web non sécurisé**. Suivez les instructions de la page web qui s’affiche pour signaler le site web.

## <a name="more-information-about-phishing-attacks"></a>Plus d’informations sur les attaques par hameçonnage

- [Protégez-vous contre le hameçonnage](https://support.microsoft.com/help/4033787/windows-protect-yourself-from-phishing)
- [Tendances en matière d’hameçonnage](phishing-trends.md)
