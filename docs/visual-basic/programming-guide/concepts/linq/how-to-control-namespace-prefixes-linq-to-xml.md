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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9b559b54ffaa53b2ae5cd3b6c6d2d4db3ebe0a04
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a>Comment : contrôler les préfixes d'espaces de noms (Visual Basic) (LINQ to XML)
Cette rubrique décrit comment contrôler les préfixes d'espaces de noms.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 Cet exemple déclare deux espaces de noms. Il spécifie que le `http://www.adventure-works.com` espace de noms comporte le préfixe `aw`et que le `www.fourthcoffee.com` espace de noms a le préfixe `fc`.  
  
### <a name="code"></a>Code  
  
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
  
### <a name="comments"></a>Commentaires  
 Cet exemple génère la sortie suivante :  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des espaces de noms XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
