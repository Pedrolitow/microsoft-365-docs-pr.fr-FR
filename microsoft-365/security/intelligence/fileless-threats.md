---
title: Menaces sans fichier
ms.reviewer: ''
description: En savoir plus sur les catégories de menaces sans fichier et de programmes malveillants qui vivent hors du pays
keywords: sans fichier, programmes malveillants sans fichier, vivant hors des terres, lolbins, amsi, surveillance du comportement, analyse de la mémoire, protection du secteur de démarrage, sécurité, programmes malveillants, Windows Defender ATP, antivirus, AV, Microsoft Defender ATP, protection de nouvelle génération
ms.service: microsoft-365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
search.appverid: met150
ms.openlocfilehash: b86ccbfeef82833d3df8597cd1a82cd25f1ab383
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68640409"
---
# <a name="fileless-threats"></a>Menaces sans fichier

Que sont exactement les menaces sans fichier ? Le terme « sans fichier » suggère qu’une menace ne se trouve pas dans un fichier, par exemple une porte dérobée qui réside uniquement dans la mémoire d’un ordinateur. Toutefois, il n’existe aucune définition pour les programmes malveillants sans fichier. Le terme est largement utilisé, et parfois pour décrire les familles de programmes malveillants qui s’appuient sur des fichiers pour fonctionner.

Les [attaques impliquent plusieurs étapes pour des](https://attack.mitre.org/wiki/ATT&CK_Matrix) fonctionnalités telles que l’exécution, la persistance ou le vol d’informations. Certaines parties de la chaîne d’attaque peuvent être sans fichier, tandis que d’autres peuvent impliquer le système de fichiers sous une certaine forme.

Pour plus de clarté, les menaces sans fichier sont regroupées en différentes catégories.

![Diagramme complet des programmes malveillants sans fichier.](../../media/security-intelligence-images/fileless-malware.png)<br>
*Figure 1. Diagramme complet des programmes malveillants sans fichier*

Les menaces sans fichier peuvent être classées par leur point d’entrée, ce qui indique comment les programmes malveillants sans fichier peuvent arriver sur un ordinateur. Ils peuvent arriver par exploit, par le biais d’un matériel compromis ou par l’exécution régulière d’applications et de scripts.

Ensuite, répertoriez la forme du point d’entrée. Par exemple, les exploits peuvent être basés sur des fichiers ou des données réseau, les périphériques PCI sont un type de vecteur matériel, et les scripts et les exécutables sont des sous-catégories du vecteur d’exécution.

Enfin, classifier l’hôte de l’infection. Par exemple, une application Flash peut contenir diverses menaces, telles qu’une attaque, un simple exécutable et un microprogramme malveillant provenant d’un appareil matériel.

La classification vous permet de diviser et de classer les différents types de menaces sans fichier. Certains sont plus dangereux, mais aussi plus difficiles à mettre en œuvre, tandis que d’autres sont plus couramment utilisés malgré (ou précisément à cause) n’étant pas très avancés.

À partir de cette catégorisation, vous pouvez glaner trois principaux types de menaces sans fichier en fonction de la quantité d’empreintes digitales qu’elles peuvent laisser sur les machines infectées.

## <a name="type-i-no-file-activity-performed"></a>Type I : Aucune activité de fichier n’a été effectuée

Un programme malveillant entièrement sans fichier peut être considéré comme un programme malveillant qui ne nécessite jamais l’écriture d’un fichier sur le disque. Comment un tel programme malveillant infecterait-il une machine en premier lieu ? Par exemple, une machine cible reçoit des paquets réseau malveillants qui exploitent la vulnérabilité EternalBlue. La vulnérabilité permet l’installation de la porte dérobée DoublePulsar, qui finit par résider uniquement dans la mémoire du noyau. Dans ce cas, aucun fichier ou aucune donnée n’est écrit sur un fichier.

Un appareil compromis peut également contenir du code malveillant qui se cache dans le microprogramme de l’appareil (tel qu’un BIOS), un périphérique USB (comme l’attaque BadUSB) ou dans le microprogramme d’une carte réseau. Tous ces exemples ne nécessitent pas d’exécution d’un fichier sur le disque et peuvent théoriquement vivre uniquement en mémoire. Le code malveillant survivrait aux redémarrages, aux reformats de disque et aux réinstallations de système d’exploitation.

Les infections de ce type peuvent être particulièrement difficiles à détecter, car la plupart des produits antivirus n’ont pas la possibilité d’inspecter le microprogramme. Dans les cas où un produit a la possibilité d’inspecter et de détecter des microprogrammes malveillants, il existe encore des défis importants associés à la correction des menaces à ce niveau. Ce type de programme malveillant sans fichier nécessite des niveaux élevés de sophistication et dépend souvent de la configuration matérielle ou logicielle particulière. Il ne s’agit pas d’un vecteur d’attaque qui peut être exploité facilement et de manière fiable. Bien que dangereuses, les menaces de ce type sont rares et peu pratiques pour la plupart des attaques.

## <a name="type-ii-indirect-file-activity"></a>Type II : activité de fichier indirect

Il existe d’autres façons que les programmes malveillants puissent obtenir une présence sans fichier sur une machine sans nécessiter d’effort d’ingénierie significatif. Les programmes malveillants sans fichier de ce type n’écrivent pas directement de fichiers sur le système de fichiers, mais ils peuvent finir par utiliser des fichiers indirectement. Par exemple, avec les [attaquants de porte dérobée Poshspy](https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html) , ils ont installé une commande PowerShell malveillante dans le référentiel WMI et configuré un filtre WMI pour exécuter la commande régulièrement.

Il est possible d’effectuer une telle installation par le biais de la ligne de commande sans qu’une porte dérobée soit déjà présente dans le fichier. Le programme malveillant peut être installé et exécuté théoriquement sans jamais toucher au système de fichiers. Toutefois, le référentiel WMI est stocké sur un fichier physique dans une zone de stockage centrale gérée par le Gestionnaire d’objets CIM et contient généralement des données légitimes. Même si la chaîne d’infection utilise techniquement un fichier physique, elle est considérée comme une attaque sans fichier, car le référentiel WMI est un conteneur de données à usage multiple qui ne peut pas être détecté et supprimé.

## <a name="type-iii-files-required-to-operate"></a>Type III : Fichiers requis pour fonctionner

Certains programmes malveillants peuvent avoir une sorte de persistance sans fichier, mais pas sans utiliser des fichiers pour fonctionner. Kovter, par exemple, crée un gestionnaire de verbes ouverts dans le registre pour une extension de fichier aléatoire. L’ouverture d’un fichier avec une telle extension entraîne l’exécution d’un script via l’outil légitime mshta.exe.

![Image de la clé de Registre de Kovter.](../../media/security-intelligence-images/kovter-reg-key.png)<br>
*Figure 2. Clé de Registre de Kovter*

Lorsque le verbe ouvert est appelé, la commande associée à partir du Registre est lancée, ce qui entraîne l’exécution d’un petit script. Ce script lit les données à partir d’une clé de Registre supplémentaire et les exécute, ce qui entraîne le chargement de la charge utile finale. Toutefois, pour déclencher le verbe ouvert en premier lieu, Kovter doit supprimer un fichier avec la même extension ciblée par le verbe (dans l’exemple ci-dessus, l’extension est .bbf5590fd). Il doit également définir une clé d’exécution automatique configurée pour ouvrir ce fichier au démarrage de la machine.

Kovter est considéré comme une menace sans fichier, car le système de fichiers n’est d’aucune utilité pratique. Les fichiers avec des extensions aléatoires contiennent des données indésirables qui ne sont pas utilisables pour vérifier la présence de la menace. Les fichiers qui stockent le Registre sont des conteneurs qui ne peuvent pas être détectés et supprimés si du contenu malveillant est présent.

## <a name="categorizing-fileless-threats-by-infection-host"></a>Catégorisation des menaces sans fichier par hôte d’infection

Après avoir décrit les grandes catégories, nous pouvons maintenant explorer les détails et fournir une répartition des hôtes d’infection. Cette classification complète couvre le panorama de ce que l’on appelle généralement les programmes malveillants sans fichier. Il dirige nos efforts pour rechercher et développer de nouvelles fonctionnalités de protection qui neutralisent les classes d’attaques et garantissent que les programmes malveillants ne prennent pas le dessus dans la course aux armements.

### <a name="exploits"></a>Exploits

**Basé sur un fichier** (type III : exécutable, Flash, Java, documents) : un fichier initial peut exploiter le système d’exploitation, le navigateur, le moteur Java, le moteur Flash, etc. pour exécuter un code shell et fournir une charge utile en mémoire. Bien que la charge utile soit sans fichier, le vecteur d’entrée initial est un fichier.

**Basé sur le réseau** (type I) : une communication réseau qui tire parti d’une vulnérabilité sur la machine cible peut obtenir l’exécution du code dans le contexte d’une application ou du noyau. WannaCry, par exemple, exploite une vulnérabilité précédemment corrigée dans le protocole SMB pour fournir une porte dérobée dans la mémoire du noyau.

### <a name="hardware"></a>Matériel

**Basé sur l’appareil** (type I : carte réseau, disque dur) : les appareils tels que les disques durs et les cartes réseau nécessitent des puces et des logiciels dédiés pour fonctionner. Les logiciels résidant et en cours d’exécution dans le chipset d’un appareil sont appelés microprogrammes. Bien qu’il s’agit d’une tâche complexe, le microprogramme peut être infecté par des programmes malveillants, comme [l’a fait le groupe d’espionnage Equation](https://www.kaspersky.com/blog/equation-hdd-malware/7623/).

**Basé sur le processeur** (type I) : les processeurs modernes sont complexes et peuvent inclure des sous-systèmes exécutant le microprogramme à des fins de gestion. Ce microprogramme peut être vulnérable au détournement et permettre l’exécution de code malveillant qui fonctionnerait à partir du processeur. En décembre 2017, deux chercheurs ont signalé une vulnérabilité qui peut permettre aux attaquants d’exécuter du code à l’intérieur du [moteur de gestion (ME)](https://en.wikipedia.org/wiki/Intel_Management_Engine) présent dans n’importe quel processeur moderne d’Intel. Pendant ce temps, le groupe d’attaquants PLATINUM a été observé pour avoir la possibilité d’utiliser la [technologie de gestion active (AMT)](https://en.wikipedia.org/wiki/Intel_Active_Management_Technology) d’Intel pour effectuer des [communications réseau invisibles](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/07/platinum-continues-to-evolve-find-ways-to-maintain-invisibility/), en contournant le système d’exploitation installé. ME et AMT sont essentiellement des micro-ordinateurs autonomes qui vivent à l’intérieur du processeur et qui fonctionnent à un niveau très faible. Étant donné que l’objectif de ces technologies est de fournir une gestion à distance, elles ont un accès direct au matériel, sont indépendantes du système d’exploitation et peuvent s’exécuter même si l’ordinateur est désactivé.

En plus d’être vulnérables au niveau du microprogramme, les processeurs peuvent être fabriqués avec des portes dérobées insérées directement dans le circuit matériel. Cette attaque a été [recherchée et prouvée possible](https://www.emsec.rub.de/media/crypto/veroeffentlichungen/2015/03/19/beckerStealthyExtended.pdf) dans le passé. Il a été signalé que certains modèles de processeurs x86 contiennent un cœur d’UC de type RISC incorporé secondaire qui peut [fournir efficacement une porte dérobée](https://www.theregister.co.uk/2018/08/10/via_c3_x86_processor_backdoor/) par le biais de laquelle les applications régulières peuvent obtenir une exécution privilégiée.

**Usb (** type I) : les périphériques USB de toutes sortes peuvent être reprogrammés avec un microprogramme malveillant capable d’interagir avec le système d’exploitation de manière néfaste. Par exemple, la [technique BadUSB](https://arstechnica.com/information-technology/2014/07/this-thumbdrive-hacks-computers-badusb-exploit-makes-devices-turn-evil/) permet à une clé USB reprogrammée d’agir comme un clavier qui envoie des commandes aux machines via des séquences de touches, ou comme une carte réseau qui peut rediriger le trafic à volonté.

**BioS** (type I) : un BIOS est un microprogramme qui s’exécute à l’intérieur d’un chipset. Il s’exécute lorsqu’une machine est sous tension, initialise le matériel, puis transfère le contrôle au secteur de démarrage. Le BIOS est un composant important qui fonctionne à un niveau faible et s’exécute avant le secteur de démarrage. Il est possible de reprogrammer le microprogramme DU BIOS avec du code malveillant, comme cela s’est produit dans le passé avec le [rootkit Mebromi](https://www.webroot.com/blog/2011/09/13/mebromi-the-first-bios-rootkit-in-the-wild/).

**Basé sur l’hyperviseur** (type I) : les processeurs modernes fournissent une prise en charge de l’hyperviseur matériel, ce qui permet au système d’exploitation de créer des machines virtuelles robustes. Une machine virtuelle s’exécute dans un environnement confiné et simulé, et n’est en théorie pas au courant de l’émulation. Un programme malveillant qui prend le contrôle d’une machine peut implémenter un petit hyperviseur pour se cacher en dehors du domaine du système d’exploitation en cours d’exécution. Des programmes malveillants de ce type ont été theorisés dans le passé, et finalement de vrais rootkits d’hyperviseur [ont été observés](http://seclists.org/fulldisclosure/2017/Jun/29), bien que peu soient connus à ce jour.

### <a name="execution-and-injection"></a>Exécution et injection

**Basé sur des fichiers** (type III : exécutables, DLL, fichiers LNK, tâches planifiées) : il s’agit du vecteur d’exécution standard. Un exécutable simple peut être lancé en tant que programme malveillant de première étape pour exécuter une charge utile supplémentaire en mémoire, ou être injecté dans d’autres processus en cours d’exécution légitimes.

**Basé sur des macros** (type III : documents Office) : le [langage VBA](/office/vba/Library-Reference/Concepts/getting-started-with-vba-in-office) est un outil flexible et puissant conçu pour automatiser les tâches de modification et ajouter des fonctionnalités dynamiques aux documents. Par conséquent, il peut être abusé par les attaquants pour effectuer des opérations malveillantes telles que le décodage, l’exécution ou l’injection d’une charge utile exécutable, ou même l’implémentation d’un ransomware entier, comme dans [le cas de qkG](https://blog.trendmicro.com/trendlabs-security-intelligence/qkg-filecoder-self-replicating-document-encrypting-ransomware/). Les macros sont exécutées dans le contexte d’un processus Office (par exemple, Winword.exe) et implémentées dans un langage de script. Il n’existe aucun fichier exécutable binaire qu’un antivirus peut inspecter. Bien que les applications Office nécessitent le consentement explicite de l’utilisateur pour exécuter des macros à partir d’un document, les attaquants utilisent des techniques d’ingénierie sociale pour inciter les utilisateurs à autoriser l’exécution de macros.

**Basé sur un script** (type II : fichier, service, registre, référentiel WMI, interpréteur de commandes) : les langages de script JavaScript, VBScript et PowerShell sont disponibles par défaut sur les plateformes Windows. Les scripts présentent les mêmes avantages que les macros, ils sont des fichiers textuels (et non des exécutables binaires) et s’exécutent dans le contexte de l’interpréteur (comme wscript.exe, powershell.exe), qui est un composant propre et légitime. Les scripts sont polyvalents et peuvent être exécutés à partir d’un fichier (en double-cliquant dessus) ou exécutés directement sur la ligne de commande d’un interpréteur. L’exécution sur la ligne de commande permet aux programmes malveillants d’encoder des scripts malveillants en tant que services de démarrage automatique à l’intérieur [des clés de Registre d’exécution automatique](https://www.gdatasoftware.com/blog/2014/07/23947-poweliks-the-persistent-malware-without-a-file) en tant [qu’abonnements aux événements WMI](https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html) à partir du référentiel WMI. En outre, un attaquant qui a obtenu l’accès à une machine infectée peut entrer le script à l’invite de commandes.

**Sur disque** (type II : enregistrement de démarrage) : l’enregistrement de démarrage est le premier secteur d’un disque ou d’un volume et contient le code exécutable requis pour démarrer le processus de démarrage du système d’exploitation. Les menaces comme [Petya](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/27/new-ransomware-old-techniques-petya-adds-worm-capabilities/?source=mmpc) sont capables d’infecter l’enregistrement de démarrage en le remplaçant par du code malveillant. Lorsque l’ordinateur est démarré, le programme malveillant prend immédiatement le contrôle. L’enregistrement de démarrage se trouve en dehors du système de fichiers, mais il est accessible par le système d’exploitation. Les produits antivirus modernes ont la possibilité de les analyser et de les restaurer.

## <a name="defeating-fileless-malware"></a>Échec des programmes malveillants sans fichier

Chez Microsoft, nous surveillons activement le paysage de la sécurité pour identifier les nouvelles tendances en matière de menaces et développer des solutions pour atténuer les classes de menaces. Nous instrumentons des protections durables qui sont efficaces contre un large éventail de menaces. Grâce à l’interface d’analyse anti-programme malveillant (AMSI), à la surveillance du comportement, à l’analyse de la mémoire et à la protection du secteur de démarrage, [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint) pouvez inspecter les menaces sans fichier, même avec une obfuscation importante. Les technologies de Machine Learning dans le cloud nous permettent de mettre à l’échelle ces protections contre les menaces nouvelles et émergentes.

Pour en savoir plus, consultez : [Hors de vue, mais pas invisible : vaincre les programmes malveillants sans fichier avec la surveillance du comportement, AMSI et av de la prochaine génération](https://cloudblogs.microsoft.com/microsoftsecure/2018/09/27/out-of-sight-but-not-invisible-defeating-fileless-malware-with-behavior-monitoring-amsi-and-next-gen-av/)

## <a name="additional-resources-and-information"></a>Ressources et informations supplémentaires

Découvrez comment [déployer des fonctionnalités de protection contre les menaces dans Microsoft 365 E5](/microsoft-365/solutions/deploy-threat-protection).
