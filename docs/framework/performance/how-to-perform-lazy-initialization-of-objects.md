---
title: "How to: Perform Lazy Initialization of Objects | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "lazy initialization in .NET, how to perform"
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# How to: Perform Lazy Initialization of Objects
La classe <xref:System.Lazy%601?displayProperty=fullName> simplifie l'exécution de l'initialisation tardive et de l'instanciation d'objets.  En initialisant des objets de façon tardive, vous n'avez pas à les créer s'ils ne sont pas nécessaires et vous pouvez différer leur initialisation à leur première utilisation.  Pour plus d'informations, consultez [Lazy Initialization](../../../docs/framework/performance/lazy-initialization.md).  
  
## Exemple  
 L'exemple suivant indique comment initialiser une valeur avec <xref:System.Lazy%601>.  Supposez que la variable tardive ne soit pas exigée, en fonction d'un autre code qui définit la variable `someCondition` sur true ou false.  
  
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
  
## Exemple  
 L'exemple suivant indique comment utiliser la classe <xref:System.Threading.ThreadLocal%601?displayProperty=fullName> pour initialiser un type uniquement visible par l'instance d'objet active sur le thread actuel.  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## Voir aussi  
 <xref:System.Threading.LazyInitializer?displayProperty=fullName>   
 [Lazy Initialization](../../../docs/framework/performance/lazy-initialization.md)