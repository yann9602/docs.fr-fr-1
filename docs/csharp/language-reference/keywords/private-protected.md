---
title: "privés protégés (référence c#)"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: 5f7abd2569d5bad5af64161042e4e5d21e741c8c
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="private-protected-c-reference"></a>privés protégés (référence c#)
Le `private protected` combinaison de mots clés est un modificateur d’accès du membre. Un membre protégé privé est accessible par les types dérivés de la classe conteneur, mais uniquement au sein de son assembly conteneur. Pour obtenir une comparaison de `private protected` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md). 
   
## <a name="example"></a>Exemple  
 Un membre privé protégé d’une classe de base est accessible à partir des types dérivés de l’assembly conteneur uniquement si le type statique de la variable est le type de classe dérivée. Prenons l’exemple de l’extrait de code suivant :  
  
 ```
 // Assembly1.cs  
 // Compile with: /target:library  
 public class BaseClass
 {
     private protected int myValue = 0;
 }
 
 public class DerivedClass1 : BaseClass
 {
     void Access()
     {
         BaseClass baseObject = new BaseClass();
 
         // Error CS1540, because myValue can only be accessed by
         // classes derived from BaseClass.
         // baseObject.myValue = 5;  
 
         // OK, accessed through the current derived class instance
         myValue = 5;
     }
 }
```  
  
```  
 // Assembly2.cs  
 // Compile with: /reference:Assembly1.dll  
 class DerivedClass2 : BaseClass
 {
     void Access()
     {
         // Error CS0122, because myValue can only be
         // accessed by types in Assembly1
         // myValue = 10;
     }
 }
```  
 Cet exemple contient deux fichiers : `Assembly1.cs` et `Assembly2.cs`. Le premier fichier contient une classe de base publique, `BaseClass`et un type dérivé, `DerivedClass1`. `BaseClass`possède un membre privé protégé, `myValue`, qui `DerivedClass1` tente d’accéder de deux manières. La première tentative d’accès `myValue` via une instance de `BaseClass` génère une erreur. Toutefois, la tentative de l’utiliser comme un membre hérité dans `DerivedClass1` réussira.
Dans le deuxième fichier, une tentative d’accès `myValue` qu’un membre hérité de `DerivedClass2` génère une erreur, car il est accessible uniquement par les types dérivés dans Assembly1. 

 Les membres de struct ne peut pas être `private protected` car le struct ne peut pas être hérité.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)   
 [Problèmes de sécurité pour les mots clés virtuels internes](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))
