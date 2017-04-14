---
title: "Comment&#160;: activer un WebRequest pour utiliser un proxy pour communiquer avec Internet | Microsoft Docs"
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
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Comment&#160;: activer un WebRequest pour utiliser un proxy pour communiquer avec Internet
Cet exemple crée une instance globale de proxy qui permettra à tous <xref:System.Net.WebRequest> d'utiliser un proxy pour communiquer avec Internet.  Cet exemple suppose que le serveur proxy est nommé `webproxy` et qu'il communique sur le port 80, le port HTTP standard.  
  
## Exemple  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références à l'espace de noms de **System.Net** .  
  
## Voir aussi  
 [Utilisation de protocoles d’application](../../../docs/framework/network-programming/using-application-protocols.md)   
 [Accès à Internet via un proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)