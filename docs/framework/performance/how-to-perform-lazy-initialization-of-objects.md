---
title: Guide pratique pour effectuer une initialisation tardive d'objets
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ab1ae0eae8d78d4b7f14444e78ff5a741fe02d95
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-perform-lazy-initialization-of-objects"></a>Guide pratique pour effectuer une initialisation tardive d'objets
La classe <xref:System.Lazy%601?displayProperty=fullName> simplifie les opérations d’initialisation tardive et d’instanciation des objets. L’initialisation des objets de manière tardive vous évite d’avoir à créer inutilement des objets non nécessaires, ou vous permet de différer l’initialisation des objets jusqu’à ce qu’ils commencent à être utilisés. Pour plus d’informations, consultez [Initialisation tardive](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment initialiser une valeur avec <xref:System.Lazy%601>. Il suppose que la variable tardive peut ne pas être nécessaire, selon que la variable `someCondition` est définie sur true ou false dans un autre code.  
  
```vb  
Dim someCondition As Boolean = False  
  
Sub Main()  
    'Initializing a value with a big computation, computed in parallel  
    Dim _data As Lazy(Of Integer) = New Lazy(Of Integer)(Function()  
                                                             Dim result =  
                                                                 ParallelEnumerable.Range(0, 1000).  
                                                                 Aggregate(Function(x, y)  
                                                                               Return x + y  
                                                                           End Function)  
                                                             Return result  
                                                         End Function)  
  
    '  do work that may or may not set someCondition to True  
    ' ...  
    '  Initialize the data only if needed  
    If someCondition = True Then  
  
        If (_data.Value > 100) Then  
  
            Console.WriteLine("Good data")  
        End If  
    End If  
End Sub  
```  
  
```csharp  
  static bool someCondition = false;    
  //Initializing a value with a big computation, computed in parallel  
  Lazy<int> _data = new Lazy<int>(delegate  
  {  
      return ParallelEnumerable.Range(0, 1000).  
          Select(i => Compute(i)).Aggregate((x,y) => x + y);  
  }, LazyExecutionMode.EnsureSingleThreadSafeExecution);  
  
  // Do some work that may or may not set someCondition to true.  
  //  ...  
  // Initialize the data only if necessary  
  if (someCondition)  
{  
    if (_data.Value > 100)  
      {  
          Console.WriteLine("Good data");  
      }  
}  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la classe <xref:System.Threading.ThreadLocal%601?displayProperty=fullName> pour initialiser un type qui est visible uniquement pour l’instance d’objet qui est exécutée sur le thread actuel.  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)] [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.LazyInitializer?displayProperty=fullName>   
 [Initialisation tardive](../../../docs/framework/performance/lazy-initialization.md)

