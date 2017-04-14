---
title: "Activation et d&#233;sactivation d’IPv6 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Activation et d&#233;sactivation d’IPv6
Pour utiliser le protocole de IPv6, assurez \-vous que vous exécutez une version du système d'exploitation qui prend en charge IPv6 et vérifiez que le système d'exploitation et les classes de mise en réseau sont configurés correctement.  
  
## Étapes de configuration  
 Le tableau suivant répertorie plusieurs paramètres  
  
|Système d'exploitation IPv6\-enabled ?|La mise en réseau classe IPv6\-enabled ?|Description|  
|--------------------------------------------|----------------------------------------------|-----------------|  
|Non|Non|Peut analyser des adresses de IPv6.|  
|Non|Oui|Peut analyser des adresses de IPv6.|  
|Oui|Non|Peut analyser des adresses de IPv6 et résoudre les adresses IPv6 d'utilisation obsolète non marqué de méthodes de résolution de noms.|  
|Oui|Oui|Peut analyser et corriger des adresses de IPv6 à l'aide de les méthodes y compris celles marqué obsolète.|  
  
 Sachez que pour activer la prise en charge de IPv6 pour toutes les classes dans l'espace de noms System.Net, vous devez modifier le fichier de configuration de l'ordinateur ou le fichier de configuration de l'application.  Le fichier de configuration d'une application est prioritaire sur le fichier de configuration de l'ordinateur.  
  
 Pour obtenir un exemple de la modification du fichier de configuration de l'ordinateur, *machine.config*, pour permettre la prise en charge, [Comment : modifiez le fichier de configuration de l'ordinateur pour activer le support Ipv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)Ipv6 consultez.  En outre, assurez \-vous que la prise en charge de IPv6 est activée pour le système d'exploitation.  
  
 Le .NET Framework possède un commutateur de configuration défini dans un fichier de configuration comme suit  
  
```  
<system.net>…  
    <settings>…  
        <ipv6 enabled="true"/>…  
    </settings>…  
</system.net>  
```  
  
 Pour le.NET Framework version 1.1 et antérieure, la valeur du commutateur de configuration d' **ipv6 enabled** spécifie si les membres des adresses de IPv6 de retour de classe d' <xref:System.Net.Dns?displayProperty=fullName> .  
  
 Pour le .NET Framework version 2.0 et ultérieure, si les fenêtres IPv6 prend en charge, puis les membres de la classe d' <xref:System.Net.Dns?displayProperty=fullName> , \(par exemple, la méthode d' <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=fullName> \), retournera des adresses de IPv6 avec une limitation.  Les membres obsolètes du serveur DNS <xref:System.Net.Dns?displayProperty=fullName> \(par exemple, la méthode d' <xref:System.Net.Dns.Resolve%2A?displayProperty=fullName> \) indiqueront et peuvent identifier la valeur dans le fichier de configuration pour la configuration activée par ipv6.  
  
## Voir aussi  
 [Protocole Internet version 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)   
 [Sockets](../../../docs/framework/network-programming/sockets.md)   
 [Schéma des paramètres réseau](../../../docs/framework/configure-apps/file-schema/network/index.md)   
 [\<ipv6\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)