---
title: "&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc36550"
  - "vbc36550"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36550"
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# &#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

La seule façon d'étendre un type de données dans Visual Basic est de définir une méthode d'extension à l'intérieur d'un module standard.  La méthode d'extension peut être une procédure `Sub` ou `Function`.  Toutes les méthodes d'extension doivent être marquées avec l'attribut d'extension, `<Extension()>`, de l'espace de noms <xref:System.Runtime.CompilerServices?displayProperty=fullName>.  Facultativement, un module qui contient une méthode d'extension peut être marqué de la même façon.  Aucune autre utilisation de l'attribut d'extension n'est valide.  
  
 **ID d'erreur :** BC36550  
  
### Pour corriger cette erreur  
  
-   Supprimez l'attribut d'extension.  
  
-   Reconcevez votre extension en tant que méthode, définie dans un module englobant.  
  
## Exemple  
 L'exemple suivant définit une méthode `Print` pour le type de données `String`.  
  
```  
Imports StringUtility  
Imports System.Runtime.CompilerServices  
Namespace StringUtility  
    <Extension()>   
    Module StringExtensions  
        <Extension()>   
        Public Sub Print (ByVal str As String)  
            Console.WriteLine(str)  
        End Sub  
    End Module  
End Namespace  
  
```  
  
## Voir aussi  
 [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [méthodes d'extension.](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)