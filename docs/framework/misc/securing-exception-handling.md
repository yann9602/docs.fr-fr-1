---
title: "S&#233;curisation de la gestion des exceptions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "sécurité du code, gestion des exceptions"
  - "gestion des exceptions, sécurité"
  - "codage sécurisé, gestion des exceptions"
  - "sécurité (.NET Framework), gestion des exceptions"
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# S&#233;curisation de la gestion des exceptions
En Visual C\+\+ et Visual Basic, une expression de filtre au sommet de la pile s'exécute avant toute instruction **finally**.  Le bloc **catch** associé à ce filtre s'exécute après l'instruction **finally**.  Pour plus d'informations, consultez [Utilisation d'exceptions filtrées par l'utilisateur](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).  Cette section passe en revue les implications en matière de sécurité de cet ordre.  Examinons l'exemple de pseudocode suivant qui illustre l'ordre dans lequel les instructions de filtre et les instructions **finally** sont exécutées.  
  
```cpp  
void Main()   
{  
    try   
    {  
        Sub();  
    }   
    except (Filter())   
    {  
        Console.WriteLine("catch");  
    }  
}  
bool Filter () {  
    Console.WriteLine("filter");  
    return true;  
}  
void Sub()   
{  
    try   
    {  
        Console.WriteLine("throw");  
        throw new Exception();  
    }   
    finally   
    {  
        Console.WriteLine("finally");  
    }  
}                        
```  
  
 Ce code imprime ce qui suit.  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 Le filtre s'exécute avant l'instruction **finally** ; par conséquent, des problèmes de sécurité peuvent être introduits par toute opération effectuant un changement d'état là où l'exécution d'un autre code pourrait en profiter.  Par exemple :  
  
```cpp  
try   
{  
    Alter_Security_State();  
    // This means changing anything (state variables,  
    // switching unmanaged context, impersonation, and   
    // so on) that could be exploited if malicious   
    // code ran before state is restored.  
    Do_some_work();  
}   
finally   
{  
    Restore_Security_State();  
    // This simply restores the state change above.  
}  
```  
  
 Ce pseudocode permet à un filtre plus haut au sommet de la pile d'exécuter du code arbitraire.  Parmi les autres exemples d'opérations aux effets similaires figurent l'emprunt temporaire d'une autre identité, la définition d'un indicateur interne qui ignore la vérification de sécurité ou le changement de la culture associée au thread.  La solution recommandée est d'introduire un gestionnaire d'exceptions pour isoler les changements de code apportés à l'état des threads des blocs de filtre des appelants.  Cependant, il est important que le gestionnaire d'exceptions soit correctement introduit ou ce problème ne sera pas résolu.  L'exemple suivant active la culture de l'interface utilisateur, mais tout type de changement d'état des threads peut être exposé de manière similaire.  
  
```cpp  
YourObject.YourMethod()  
{  
   CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
   try {  
      Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
      // Do something that throws an exception.  
}  
   finally {  
      Thread.CurrentThread.CurrentUICulture = saveCulture;  
   }  
}  
  
```  
  
```vb  
Public Class UserCode  
   Public Shared Sub Main()  
      Try  
         Dim obj As YourObject = new YourObject  
         obj.YourMethod()  
      Catch e As Exception When FilterFunc  
         Console.WriteLine("An error occurred: '{0}'", e)  
         Console.WriteLine("Current Culture: {0}",   
Thread.CurrentThread.CurrentUICulture)  
      End Try  
   End Sub  
  
   Public Function FilterFunc As Boolean  
      Console.WriteLine("Current Culture: {0}", Thread.CurrentThread.CurrentUICulture)  
      Return True  
   End Sub  
  
End Class  
```  
  
 Pour résoudre correctement ce cas, le bloc **try**\/**finally** existant doit être enveloppé dans un bloc **try**\/**catch**.  La simple introduction d'une clause **catch\-throw** dans le bloc **try**\/**finally** existant ne résout pas le problème, comme illustré dans l'exemple suivant.  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
  
    try   
    {  
        Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
        // Do something that throws an exception.  
    }  
    catch { throw; }  
    finally   
    {  
        Thread.CurrentThread.CurrentUICulture = saveCulture;  
    }  
}  
```  
  
 Le problème n'est pas résolu car l'instruction **finally** ne s'est pas exécutée avant que `FilterFunc` prenne le contrôle.  
  
 L'exemple suivant corrige ce problème en garantissant que la clause **finally** se soit exécutée avant de proposer une exception au sommet des blocs de filtre d'exceptions des appelants.  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
    try    
    {  
        try   
        {  
            Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
            // Do something that throws an exception.  
        }  
        finally   
        {  
            Thread.CurrentThread.CurrentUICulture = saveCulture;  
        }  
    }  
    catch { throw; }  
}  
```  
  
## Voir aussi  
 [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md)