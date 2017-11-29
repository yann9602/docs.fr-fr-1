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
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="356f8-102">Comment : inscrire un protocole personnalisé à l’aide de WebRequest</span><span class="sxs-lookup"><span data-stu-id="356f8-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="356f8-103">Cet exemple montre comment inscrire une classe spécifique à un protocole qui est définie ailleurs dans du code.</span><span class="sxs-lookup"><span data-stu-id="356f8-103">This example shows how to register a protocol specific classthat is defined elsewhere.</span></span> <span data-ttu-id="356f8-104">Dans cet exemple, `CustomWebRequestCreator` est l’objet implémenté par l’utilisateur qui implémente la méthode **Create** utilisée pour retourner l’objet `CustomWebRequest`.</span><span class="sxs-lookup"><span data-stu-id="356f8-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="356f8-105">L’exemple de code suppose que vous avez écrit le code `CustomWebRequest` qui implémente le protocole personnalisé.</span><span class="sxs-lookup"><span data-stu-id="356f8-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="356f8-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="356f8-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="356f8-107">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="356f8-107">Compiling the Code</span></span>  
 <span data-ttu-id="356f8-108">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="356f8-108">This example requires:</span></span>  
  
 <span data-ttu-id="356f8-109">Références à l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="356f8-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="356f8-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="356f8-110">See Also</span></span>  
 [<span data-ttu-id="356f8-111">Programmation de protocoles enfichables</span><span class="sxs-lookup"><span data-stu-id="356f8-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
