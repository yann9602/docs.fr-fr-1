---
title: "Sécurisation de la gestion des exceptions"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a028fcdfb6c85e456c8722decdb1bca8fd907a9f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="securing-exception-handling"></a>Sécurisation de la gestion des exceptions
Dans Visual C++ et Visual Basic, une expression de filtre plus haut de la pile s’exécute avant tout **enfin** instruction. Le **catch** bloc associé à ce filtre s’exécute après la **enfin** instruction. Pour plus d’informations, consultez [utilisation d’Exceptions](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md). Cette section examine les implications de sécurité de cet ordre. Prenons l’exemple de pseudo-code suivant qui illustre l’ordre dans les instructions de filtre et **enfin** instructions sont exécutées.  
  
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
  
 Ce code affiche les éléments suivants.  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 Le filtre s’exécute avant le **enfin** instruction, pour les problèmes de sécurité peuvent être introduites par tout ce qui rend à un état de modification où l’exécution d’un autre code pourrait tirer parti. Exemple :  
  
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
  
 Ce pseudocode permet à un filtre en haut de la pile pour exécuter du code arbitraire. Autres exemples d’opérations qui auraient un effet similaire sont l’emprunt d’identité temporaire d’une autre identité, en définissant un indicateur interne qui ignore la vérification de sécurité ou la modification de la culture associée au thread. La solution recommandée consiste à introduire un gestionnaire d’exceptions pour isoler les modifications du code à l’état du thread à partir de blocs de filtre des appelants. Toutefois, il est important que le Gestionnaire d’exceptions soit correctement introduit ou ce problème ne sera pas résolu. L’exemple suivant active la culture d’interface utilisateur, mais n’importe quel type de changement d’état de thread peut être exposée de la même façon.  
  
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
  
 La correction appropriée dans ce cas est d’encapsuler existants **essayez**/**enfin** bloc dans un **essayez**/**catch** bloc. Présentation simplement un **catch-throw** clause dans existants **essayez**/**enfin** bloc ne résout pas le problème, comme illustré dans l’exemple suivant.  
  
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
  
 Cela ne résout pas le problème, car le **enfin** instruction n’a pas été exécuté avant le `FilterFunc` Obtient le contrôle.  
  
 L’exemple suivant résout le problème en vous assurant que le **enfin** clause se soit exécutée avant de proposer une exception des blocs de filtre d’exception appelants.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md)
