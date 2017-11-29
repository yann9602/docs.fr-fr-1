---
title: "Comment : modifier le fichier de configuration de l’ordinateur pour activer la prise en charge IPv6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
caps.latest.revision: "18"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 696aeb619f14a5ebe9a760cbd78a0d0fa876edc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Comment : modifier le fichier de configuration de l’ordinateur pour activer la prise en charge IPv6
L’exemple de code suivant montre comment modifier le fichier de configuration (*machine.config*) d’un ordinateur pour activer la prise en charge d’IPv6. Le fichier *machine.config* est stocké dans le dossier *%Windir%\Microsoft.NET\Framework*, situé dans le répertoire d’installation de Windows. Il y a un fichier *machine.config* distinct dans les dossiers sous *%Windir%\Microsoft.NET\Framework* pour chaque version de .NET Framework installée sur l’ordinateur (par exemple, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).  
  
 Ces paramètres peuvent également être effectués dans le fichier de configuration de l'application, qui est prioritaire sur le fichier de configuration de votre ordinateur.  
  
 Pour .NET Framework version 1.1 ou antérieure, la valeur du commutateur de configuration **ipv6 enabled** spécifie si les membres de la classe <xref:System.Net.Dns?displayProperty=nameWithType> retournent des adresses IPv6.  
  
 Pour .NET Framework version 2.0 ou ultérieure, si Windows prend en charge le protocole IPv6, tous les membres de la classe <xref:System.Net.Dns?displayProperty=nameWithType> (par exemple, la méthode <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType>) retournent des adresses IPv6 avec une limitation. Les membres obsolètes de la classe <xref:System.Net.Dns?displayProperty=nameWithType> (par exemple, la méthode <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType>) lisent et reconnaissent la valeur dans le fichier de configuration.  
  
> [!NOTE]
>  Pour .NET Framework version 2.0 ou ultérieure, IPv6 est activé par défaut. Pour .NET Framework version 1.1 ou antérieure, IPv6 est désactivé par défaut.  
  
## <a name="example"></a>Exemple  
  
```xml  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>   
    ……………  
    </settings>  
    ………………  
<system.net>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Adressage IPv6](../../../docs/framework/network-programming/ipv6-addressing.md)  
 [Schéma des paramètres réseau](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [\<ipv6>, élément (paramètres réseau)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
