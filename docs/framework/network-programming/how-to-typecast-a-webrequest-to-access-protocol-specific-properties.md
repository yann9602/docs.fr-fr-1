---
title: "Comment : convertir une classe WebRequest pour accéder à des propriétés spécifiques au protocole"
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
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 471b4dc36cdb32ff7e68aa25c5a2036fec7b1293
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a>Comment : convertir une classe WebRequest pour accéder à des propriétés spécifiques au protocole
Cet exemple montre comment effectuer un cast du type d’une classe WebRequest pour accéder à des propriétés spécifiques au protocole.  
  
## <a name="example"></a>Exemple  
  
```csharp  
HttpWebRequest httpreq =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation de protocoles enfichables](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
