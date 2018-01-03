---
title: "Comment : remplacer une sélection de proxy global"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 970b428343f4e2dec73e7eceec20414cd8bdfbac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-override-a-global-proxy-selection"></a>Comment : remplacer une sélection de proxy global
Cet exemple envoie une **WebRequest** à www.contoso.com qui substitue la sélection de proxy global avec un serveur proxy nommé `alternateproxy` sur le port 80.  
  
## <a name="example"></a>Exemple  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   Références à l’espace de noms **System.Net**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de protocoles d’application](../../../docs/framework/network-programming/using-application-protocols.md)  
 [Accès à Internet via un proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
