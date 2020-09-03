---
title: Calculatrice d’espace d’adressage pour les sous-réseaux de la passerelle Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/01/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
description: 'Résumé : calculez l’espace d’adressage d’un sous-réseau de passerelle Azure avec C3, Python ou PowerShell.'
ms.openlocfilehash: 5e119f1ddefb5877886042b835ffdd093a34f0f8
ms.sourcegitcommit: c029834c8a914b4e072de847fc4c3a3dde7790c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "47332788"
---
# <a name="address-space-calculator-for-azure-gateway-subnets"></a>Calculatrice d’espace d’adressage pour les sous-réseaux de la passerelle Azure

Un réseau virtuel (VNet) dans les services d’infrastructure Azure qui est connecté à d’autres réseaux doit disposer d’un sous-réseau de passerelle. Les meilleures pratiques pour la définition de ce sous-réseau sont les suivantes :

- La longueur du préfixe du sous-réseau de passerelle peut avoir une longueur de préfixe de 29 (par exemple, 10.119.255.248/29), mais la recommandation actuelle consiste à utiliser une longueur de préfixe de 27 (par exemple, 10.119.255.224/27).
- Lors de la définition de l’espace d’adressage du sous-réseau de passerelle, utilisez la toute dernière partie de l’espace d’adressage de réseau virtuel.

Pour la deuxième recommandation, vous pouvez déterminer l’espace d’adressage du sous-réseau de passerelle en définissant le bit utilisé pour le sous-réseau de passerelle sur 0 et les bits de variable restants dans l’espace d’adressage de réseau virtuel sur 1. Pour calculer rapidement l’espace d’adressage de sous-réseau de passerelle sans avoir à convertir au format binaire et revenir au format décimal, vous pouvez utiliser une application de console écrite en C# ou python ou avec un bloc de commandes PowerShell.

Cet article contient des blocs de code C#, Python et PowerShell qui recueillent cinq entiers (les valeurs de w.x.y. z/n pour le préfixe d’adresse de réseau virtuel et la longueur de préfixe de sous-réseau de passerelle) et calcule l’espace d’adressage de sous-réseau de passerelle.

## <a name="c-code-block"></a>Bloc de code C#

Utilisez ce bloc de code pour créer une application console en C#.

```c#
using System; 
using System.Collections.Generic; 
using System.Linq; 
using System.Text; 
using System.Threading.Tasks; 
 
namespace ConsoleApplication1 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            // Declare variables. 
            const long wOctet = 16777216;  
            const long xOctet = 65536; 
            const long yOctet = 256; 
            double D; 
            int w, x, y, z, vnetPrefLen, gwPrefLen; 
            long d, w2, x2, y2, z2; 
             
 
            // Get the five values needed from the keyboard. 
            Console.WriteLine("**************************************************************************"); 
            Console.WriteLine("*** Gateway subnet address space calculator for Azure virtual networks ***");             
            Console.WriteLine("**************************************************************************");  
            Console.WriteLine(); 
            Console.WriteLine("Please supply your virtual network address space in the form of w.x.y.z/n."); 
            Console.WriteLine(); 
            Console.WriteLine("w="); 
            w = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine("x="); 
            x = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine("y="); 
            y = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine("z="); 
            z = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine("n="); 
            vnetPrefLen = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine(); 
            Console.WriteLine("Now supply the prefix length of your gateway subnet:"); 
            gwPrefLen = Convert.ToInt32(Console.ReadLine()); 
            Console.WriteLine(); 
 
            // Perform the calculation. 
            D = w * wOctet + x * xOctet + y * yOctet + z; 
            for (int i = vnetPrefLen + 1; i < gwPrefLen + 1; i++) 
            { 
                D = D + Math.Pow(2, 32 - i); 
            } 
            d = Convert.ToInt64(D); 
            w2 = d / wOctet; 
            x2 = (d - w2 * wOctet) / xOctet;  
            y2 = (d - w2 * wOctet - x2 * xOctet) / yOctet; 
            z2 = d - w2 * wOctet - x2 * xOctet - y2 * yOctet; 
             
            // Display the result.             
            Console.WriteLine("**************************************************************************");  
            Console.WriteLine("For the Azure virtual address space {0}.{1}.{2}.{3}/{4}", w, x, y, z, vnetPrefLen); 
            Console.WriteLine("and gateway prefix length of {0}, the gateway subnet address space is:", gwPrefLen); 
            Console.WriteLine(); 
            Console.WriteLine("{0}.{1}.{2}.{3}/{4}", w2, x2, y2, z2, gwPrefLen); 
            Console.WriteLine(); 
            Console.WriteLine("Press ENTER to quit."); 
            Console.ReadLine(); 
        } 
    } 
} 
```

## <a name="python-code-block"></a>Bloc de code python

Utilisez ce bloc de code pour créer une application console dans Python.

```python
import math 
# Collect the values of w.x.y.z/n for your VNet address space and g, the prefix length of your gateway subnet 
print("**************************************************************************")  
print("*** Gateway subnet address space calculator for Azure virtual networks ***")  
print("**************************************************************************\n")   
print("Please supply your virtual network address space in the form of w.x.y.z/n.");  
w=int(input("w = ")) 
x=int(input("x = ")) 
y=int(input("y = ")) 
z=int(input("z = ")) 
n=int(input("n = ")) 
print("")  
g=int(input("Now supply the prefix length of your gateway subnet: ")) 
print("")  
 
# Calculate  
wOctet = 16777216  
xOctet = 65536  
yOctet = 256  
D = w * wOctet + x * xOctet + y * yOctet + z 
for index in range(n + 1,g + 1): 
    D += 2**(32 - index)  
 
w2 = math.floor(D / wOctet)  
x2 = math.floor((D - w2 * wOctet) / xOctet) 
y2 = math.floor((D - w2 * wOctet - x2 * xOctet) / yOctet) 
z2 = D - w2 * wOctet - x2 * xOctet - y2 * yOctet  
 
# Display the result  
gwAddrPref= "Your gateway address prefix is: " + str(w2) + "." + str(x2) + "." + str(y2) + "." + str(z2) + "/" + str(g)  
print(gwAddrPref) 
```


## <a name="powershell-command-block"></a>Bloc de commandes PowerShell

Renseignez les valeurs et exécutez le bloc de commandes résultant dans une fenêtre PowerShell ou dans PowerShell ISE.

```powershell
# Specify the values of w.x.y.z/n for your VNet address space and g, the prefix length of your gateway subnet: 
$w= 
$x= 
$y= 
$z= 
$n= 
$g= 
# Calculate 
$wOctet = 16777216 
$xOctet = 65536 
$yOctet = 256 
[long]$D = $w * $wOctet + $x * $xOctet + $y * $yOctet + $z; 
for ($i = $n + 1; $i -lt $g + 1; $i++) 
{ 
$D = $D + [math]::pow(2, 32 - $i) 
} 
$w2 = [math]::floor($D / $wOctet) 
$x2 = [math]::floor( ($D - $w2 * $wOctet) / $xOctet ) 
$y2 = [math]::floor( ($D - $w2 * $wOctet - $x2 * $xOctet) / $yOctet ) 
$z2 = $D - $w2 * $wOctet - $x2 * $xOctet - $y2 * $yOctet 
# Display the result 
$dx= [string]$w2 + "." + [string]$x2 + "." + [string]$y2 + "." + [string]$z2 + "/" + [string]$g 
Write-Host "Your gateway address prefix is: " $dx
```
    
## <a name="related-topics"></a>Voir aussi

[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

