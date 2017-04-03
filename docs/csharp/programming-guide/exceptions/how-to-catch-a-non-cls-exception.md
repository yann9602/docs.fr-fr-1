---
title: Guide pratique pour intercepter une exception non-CLS | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
caps.latest.revision: 8
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3515ecab379a0e910cdd5ba82a4a39b085cc816f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-catch-a-non-cls-exception"></a>Guide pratique pour intercepter une exception non-CLS
Certains langages .NET, y compris C++/CLI, permettent aux objets de lever des exceptions qui ne dérivent pas de <xref:System.Exception>. De telles exceptions sont appelées *exceptions non-CLS* ou *non exceptions*. Dans [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)], vous ne pouvez pas lever d’exceptions non-CLS, mais vous pouvez les intercepter de deux façons :  
  
-   Dans un bloc `catch (Exception e)`, en tant que <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
     Par défaut, un assembly [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] intercepte les exceptions non-CLS comme des exceptions encapsulées. Utilisez cette méthode si vous devez accéder à l’exception d’origine, qui est accessible via la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A>. La procédure située plus loin dans cette rubrique explique comment intercepter les exceptions de cette manière.  
  
-   Dans un bloc catch général (un bloc catch sans type d’exception spécifié) qui est placé après un bloc `catch (Exception)` ou `catch (Exception e)`.  
  
     Utilisez cette méthode lorsque vous souhaitez effectuer une action (comme écrire dans un fichier journal) en réponse à des exceptions non-CLS, et que vous n’avez pas besoin d’accéder aux informations de l’exception. Par défaut, le common language runtime inclut dans un wrapper toutes les exceptions. Pour désactiver ce comportement, ajoutez cet attribut d’assembly à votre code, généralement dans le fichier AssemblyInfo.cs : `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.  
  
### <a name="to-catch-a-non-cls-exception"></a>Comment intercepter une exception non-CLS  
  
1.  Dans un `catch(Exception e) block`, utilisez le mot clé `as` pour tester si `e` peut être casté en une <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
2.  Accédez à l’exception d’origine via la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment intercepter une exception non-CLS levée à partir d’une bibliothèque de classes écrite en C++ /CLR. Notez que dans cet exemple, le code client [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] sait par avance que le type d’exception levé est un <xref:System.String?displayProperty=fullName>. Vous pouvez caster la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> en son type d’origine, tant que celui-ci est accessible à partir de votre code.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>   
 [Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/index.md)
