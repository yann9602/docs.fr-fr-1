---
title: "Comment : inscrire un protocole personnalisé à l’aide de WebRequest"
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
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4fdb1188aeb7fd754ab21a268070830f55347441
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>Comment : inscrire un protocole personnalisé à l’aide de WebRequest
Cet exemple montre comment inscrire une classe spécifique à un protocole qui est définie ailleurs dans du code. Dans cet exemple, `CustomWebRequestCreator` est l’objet implémenté par l’utilisateur qui implémente la méthode **Create** utilisée pour retourner l’objet `CustomWebRequest`. L’exemple de code suppose que vous avez écrit le code `CustomWebRequest` qui implémente le protocole personnalisé.  
  
## <a name="example"></a>Exemple  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
 Références à l’espace de noms <xref:System.Net>.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation de protocoles enfichables](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
