---
title: "Interpr&#233;tation du tra&#231;age r&#233;seau | Microsoft Docs"
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
helpviewer_keywords: 
  - "TraceMode (attribut)"
  - "données hexadécimales, sortie du traçage réseau"
  - "traçage réseau, analyse"
  - "protocolonly"
  - "texte, sortie du traçage réseau"
  - "includehex"
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Interpr&#233;tation du tra&#231;age r&#233;seau
Lorsque le traçage réseau est activé, vous pouvez utiliser le traçage pour capturer des appels que votre application effectue à différent <xref:System.Net> des membres de classe.  La sortie de ces appels peut être semblable aux exemples suivants.  
  
```  
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61  
```  
  
 Dans l'exemple précédent, \[588\] est l'identificateur unique du thread actuel.  \(4357\) et \(4387\) sont les horodatages qui désigne le nombre de millisecondes qui se sont écoulées depuis que l'application a démarré.  Les données qui suit l'horodatage indiquent l'application écriture et quittant la méthode **Socket.Send**.  L'objet exécute la méthode de **Envoyer** a 33574638 comme identificateur unique.  La trace de sortie de méthode inclut la valeur de retour \(61 dans l'exemple précédent\).  
  
 Les traces réseau peuvent capturer le trafic réseau qui est envoyé ou accepté par votre application à l'aide de protocoles au niveau de l'application tels que le protocole HTTP \(HTTP\).  Ces données peuvent être capturées en tant que texte et, éventuellement, hexadécimales données.  Les données hexadécimales sont disponibles lorsque vous spécifiez **includehex** comme valeur de l'attribut de **tracemode** .  \(Pour plus d'informations sur cet attribut, consultez [Comment : Configurez le traçage réseau](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).\) La trace de l'exemple suivant a été générée à l'aide de **includehex**.  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 Pour omettre des données hexadécimales, spécifiez **protocolonly** comme valeur de l'attribut de **tracemode** .  L'exemple suivant illustre la trace lorsque **protocolonly** est spécifié.  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## Voir aussi  
 [Activation du suivi réseau](../../../docs/framework/network-programming/enabling-network-tracing.md)   
 [Comment : Configurez le traçage réseau](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)   
 [Traçage réseau dans le .NET Framework](../../../docs/framework/network-programming/network-tracing.md)