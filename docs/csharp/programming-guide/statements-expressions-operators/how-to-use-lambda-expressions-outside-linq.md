---
title: "Comment&#160;: utiliser des expressions lambda en&#160;dehors de LINQ (Guide de programmation&#160;C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "expressions lambda (C#), en dehors de LINQ"
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: utiliser des expressions lambda en&#160;dehors de LINQ (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les expressions lambda ne sont pas limitées aux requêtes [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)].  Vous pouvez les utiliser partout où une valeur de délégué est attendue, c'est\-à\-dire, partout où une méthode anonyme est utilisée.  L'exemple suivant indique comment utiliser une expression lambda dans un gestionnaire d'événements Windows Forms.  Remarquez que les types des entrées \(<xref:System.Object> et <xref:System.Windows.Forms.MouseEventArgs>\) sont déduits par le compilateur et n'ont pas à être fournis explicitement dans les paramètres d'entrée lambda.  
  
## Exemple  
  
```  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
       this.Click += (s, e) => { MessageBox.Show(((MouseEventArgs)e).Location.ToString());};  
    }  
}  
```  
  
## Voir aussi  
 [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)