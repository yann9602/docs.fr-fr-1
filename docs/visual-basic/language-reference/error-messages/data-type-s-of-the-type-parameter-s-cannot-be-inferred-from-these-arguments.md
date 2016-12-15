---
title: "Data type(s) of the type parameter(s) cannot be inferred from these arguments | Microsoft Docs"
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
  - "bc36644"
  - "bc36647"
  - "vbc36647"
  - "vbc36644"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36644"
  - "BC36647"
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Data type(s) of the type parameter(s) cannot be inferred from these arguments
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Impossible de déduire le ou les types de données du ou des paramètres de type à partir de ces arguments.La spécification explicite du ou des types de données peut permettre de corriger cette erreur.  
  
 Cette erreur se produit en cas d'échec de la résolution de la surcharge.  Elle prend la forme d'un message subordonné qui indique pourquoi un candidat de surcharge particulier a été éliminé.  Ce message d'erreur explique que le compilateur ne peut pas utiliser l'inférence de type afin de rechercher des types de données pour les paramètres de type.  
  
> [!NOTE]
>  Lorsque la spécification d'arguments n'est pas une option \(par exemple, pour les opérateurs de requête dans les expressions de requête\), le message d'erreur apparaît sans la deuxième phrase.  
  
 Le code suivant illustre cette erreur.  
  
```vb#  
Module Module1  
  
    Sub Main()  
  
        '' Not Valid.  
        'OverloadedGenericMethod("Hello", "World")  
  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T)(ByVal x As String,   
                                      ByVal y As InterfaceExample(Of T))  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,   
                                         ByVal y As InterfaceExample(Of R))  
    End Sub  
  
End Module  
  
Interface InterfaceExample(Of T)  
End Interface  
```  
  
 **ID d'erreur :** BC36647 et BC36644  
  
### Pour corriger cette erreur  
  
-   Vous pouvez peut\-être spécifier un type de données pour le ou les paramètres de type au lieu d'avoir recours à l'inférence de type.  
  
## Voir aussi  
 [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)   
 [Generic Procedures in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)   
 [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)