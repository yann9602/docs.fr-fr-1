---
title: Guide pratique pour activer un WebRequest pour utiliser un proxy pour communiquer avec Internet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
caps.latest.revision: 9
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a42b9f947f4c3d59c3e17a892e4db405e2bc8b64
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Guide pratique pour activer un WebRequest pour utiliser un proxy pour communiquer avec Internet
Cet exemple crée une instance proxy globale qui permet à tout <xref:System.Net.WebRequest> d’utiliser un proxy pour communiquer avec Internet. L’exemple suppose que le serveur proxy est nommé `webproxy` et qu’il communique sur le port 80, le port HTTP standard.  
  
## <a name="example"></a>Exemple  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   Références à l’espace de noms **System.Net**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de protocoles d’application](../../../docs/framework/network-programming/using-application-protocols.md)   
 [Accès à Internet via un proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)

