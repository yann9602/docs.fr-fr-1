---
title: "Comment : contrôler les préfixes Namespace (Visual Basic) (LINQ to XML) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 87db9e5384bee835ca4fde141765eabf9a7cfedb
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a><span data-ttu-id="daa95-102">Comment : contrôler les préfixes d'espaces de noms (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="daa95-102">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="daa95-103">Cette rubrique décrit comment contrôler les préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="daa95-103">This topic describes how you can control namespace prefixes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="daa95-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="daa95-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="daa95-105">Description</span><span class="sxs-lookup"><span data-stu-id="daa95-105">Description</span></span>  
 <span data-ttu-id="daa95-106">Cet exemple déclare deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="daa95-106">This example declares two namespaces.</span></span> <span data-ttu-id="daa95-107">Il spécifie que le `http://www.adventure-works.com` espace de noms comporte le préfixe `aw`et que le `www.fourthcoffee.com` espace de noms a le préfixe `fc`.</span><span class="sxs-lookup"><span data-stu-id="daa95-107">It specifies that the `http://www.adventure-works.com` namespace has the prefix `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="daa95-108">Code</span><span class="sxs-lookup"><span data-stu-id="daa95-108">Code</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="daa95-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="daa95-109">Comments</span></span>  
 <span data-ttu-id="daa95-110">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="daa95-110">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="daa95-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="daa95-111">See Also</span></span>  
 [<span data-ttu-id="daa95-112">Utilisation des espaces de noms XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="daa95-112">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
