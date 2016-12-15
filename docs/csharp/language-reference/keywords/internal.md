---
title: "internal (R&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "internal_CSharpKeyword"
  - "internal"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "internal (mot clé C#)"
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# internal (R&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le mot clé d' `internal` est [modificateur d'accès](../../../csharp/language-reference/keywords/access-modifiers.md) pour les types et membres de type.  Les types ou membres internes ne sont accessibles que dans des fichiers figurant dans le même assembly, comme dans l'exemple suivant :  
  
```  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  
  
 Il est possible d'accéder aux types ou aux membres qui ont accès au modificateur `protected internal` à partir de l'assembly actuel ou des types dérivés de la classe contenante.  
  
 Pour comparer le modificateur d'accès `internal` et les autres modificateurs d'accès, consultez [Niveaux d'accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) et [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Pour plus d'informations sur les assemblys, consultez [Assemblys et le Global Assembly Cache](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md).  
  
 L'utilisation de l'accès interne est courante dans un développement basé sur des composants, car elle permet à un groupe de composants de coopérer de manière privée sans s'exposer au reste du code d'application.  Par exemple, une infrastructure pour la génération d'interfaces utilisateur graphiques peut fournir des classes `Control` et `Form` qui coopèrent en utilisant des membres dotés d'un accès interne.  Comme ces membres sont internes, ils ne sont pas exposés au code qui utilise l'infrastructure.  
  
 C'est une erreur que de référencer un type ou un membre avec accès interne en dehors de l'assembly dans lequel il a été défini.  
  
## Exemple  
 Cet exemple met en jeu deux fichiers, `Assembly1.cs` et `Assembly1`\_`a.cs`.  Le premier fichier contient une classe de base interne, `BaseClass`.  Dans le deuxième fichier, une tentative d'instancier `BaseClass` produira une erreur.  
  
```  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## Exemple  
 Dans cet exemple, utilisez les mêmes fichiers que dans l'exemple 1 et changez le niveau d'accessibilité de `BaseClass` en `public`.  Modifiez également le niveau d'accessibilité de l'`IntM` membre en `internal`.  Dans ce cas, vous pouvez instancier la classe, mais vous ne pouvez pas accéder au membre interne.  
  
```  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```  
// Assembly2_a.cs  
// Compile with: /reference:Assembly1.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificateurs d'accès](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Niveaux d'accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [privées](../../../csharp/language-reference/keywords/private.md)   
 [protégés](../../../csharp/language-reference/keywords/protected.md)