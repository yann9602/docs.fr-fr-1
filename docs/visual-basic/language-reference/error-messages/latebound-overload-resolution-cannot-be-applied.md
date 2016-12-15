---
title: "Latebound overload resolution cannot be applied to &#39;&lt;procedurename&gt;&#39; because the accessing instance is an interface type | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30933"
  - "bc30933"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "overload resolution, with late-bound argument"
  - "BC30933"
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Latebound overload resolution cannot be applied to &#39;&lt;procedurename&gt;&#39; because the accessing instance is an interface type
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le compilateur essaie de résoudre une référence à une propriété ou une procédure surchargée, mais la référence échoue parce qu'un argument est de type `Object` et l'objet de référence a le type de données d'une interface.  L'argument `Object` oblige le compilateur à résoudre la référence en tant que liaison tardive.  
  
 Dans ces cas, le compilateur résout la surcharge par l'intermédiaire de la classe d'implémentation au lieu de l'interface sous\-jacente.  Si la classe renomme l'une des versions surchargées, le compilateur ne considère pas cette version comme une surcharge car son nom est différent.  Il ignore la version renommée alors qu'elle représente peut\-être le choix correct pour résoudre la référence.  
  
 **ID d'erreur :** BC30933  
  
### Pour corriger cette erreur  
  
-   Utilisez `CType` pour effectuer un cast de l'argument de `Object` dans le type spécifié par la signature de la surcharge que vous souhaitez appeler.  
  
     Notez qu'il ne permet pas d'effectuer un cast de l'objet de référence dans l'interface sous\-jacente.  Vous devez effectuer un cast de l'argument pour éviter cette erreur.  
  
## Exemple  
 L'exemple suivant présente un appel à une procédure `Sub` surchargée qui génère cette erreur au moment de la compilation.  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 Dans l'exemple précédent, si le compilateur a autorisé l'appel à `s1` tel qu'il est écrit, la résolution a lieu par l'intermédiaire de la classe `c1` au lieu de l'interface `i1`.  Cela signifie que le compilateur ne tient pas compte de `s2` car son nom est différent dans `c1`, même s'il représente le choix correct, tel que défini par `i1`.  
  
 Vous pouvez corriger l'erreur en modifiant l'appel à l'une ou l'autre des lignes suivantes du code :  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 Chacune des lignes précédentes du code effectue un cast explicite de la variable `Object` `o1` dans l'un des types de paramètre définis pour les surcharges.  
  
## Voir aussi  
 [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Overload Resolution](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)   
 [CType, fonction](../../../visual-basic/language-reference/functions/ctype-function.md)