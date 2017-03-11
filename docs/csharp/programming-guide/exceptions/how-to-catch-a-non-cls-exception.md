---
title: "Comment&#160;: intercepter une exception non-CLS | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "exceptions (C#), non-CLS"
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
caps.latest.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 8
---
# Comment&#160;: intercepter une exception non-CLS
Certains langages .NET, y compris C\+\+\/CLI, permettent aux objets de lever des exceptions qui ne dérivent pas de <xref:System.Exception>.  De telles exceptions sont appelées *exceptions non conformes CLS* ou *objets autres que les exceptions*.  Dans [!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)], vous ne pouvez pas lever d'exceptions non\-CLS, mais vous pouvez les intercepter de deux façons :  
  
-   Dans un bloc `catch (Exception e)` tel que <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
     Par défaut, un assembly [!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)] intercepte les exceptions non\-CLS comme des exceptions encapsulées.  Utilisez cette méthode si vous avez besoin d'accès à l'exception d'origine, accessible par l'intermédiaire de la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A>.  La procédure fournie plus loin dans cette rubrique explique comment intercepter des exceptions de cette manière.  
  
-   Dans un bloc catch général \(un bloc catch sans type d'exception spécifié\) qui est placé après un bloc `catch (Exception)` ou `catch (Exception e)`.  
  
     Utilisez cette méthode lorsque vous voulez exécuter une action \(comme écrire dans un fichier journal\) en réponse à exceptions non conformes CLS et que vous n'avez pas besoin d'accéder aux informations sur les exceptions.  Par défaut, le Common Language Runtime encapsule toutes les exceptions.  Pour désactiver ce comportement, ajoutez cet attribut de niveau assembly à votre code, en principe dans le fichier AssemblyInfo.cs : `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.  
  
### Pour intercepter une exception non conforme CLS  
  
1.  Dans un `catch(Exception e) block`, utilisez le mot clé `as` pour tester s'il est possible d'effectuer un cast de `e` en <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
2.  Accédez à l'exception d'origine via la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A>.  
  
## Exemple  
 L'exemple suivant montre comment intercepter une exception non conforme CLS levée à partir d'une bibliothèque de classes écrite en C\+\+\/CLR.  Notez que, dans cet exemple, le code client [!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)] sait par avance que le type de l'exception levée est un <xref:System.String?displayProperty=fullName>.  Vous pouvez effectuer un cast sur la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> pour la rétablir dans son type d'origine pour autant que ce type soit accessible à partir de votre code.  
  
```  
// Class library written in C++/CLR.  
   ThrowNonCLS.Class1 myClass = new ThrowNonCLS.Class1();  
  
   try  
   {  
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();   
   }  
  
   catch (Exception e)  
   {  
    RuntimeWrappedException rwe = e as RuntimeWrappedException;  
    if (rwe != null)      
    {  
      String s = rwe.WrappedException as String;  
      if (s != null)  
      {  
        Console.WriteLine(s);  
      }  
    }  
    else  
    {  
       // Handle other System.Exception types.  
    }  
   }             
```  
  
## Voir aussi  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>   
 [Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)