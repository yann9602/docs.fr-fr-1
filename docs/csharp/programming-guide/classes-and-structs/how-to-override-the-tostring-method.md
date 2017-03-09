---
title: "Comment&#160;: substituer la m&#233;thode ToString (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "héritage (C#), substituer les méthodes OnPaint et ToString"
  - "ToString (méthode), substituer en C#"
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# Comment&#160;: substituer la m&#233;thode ToString (Guide de programmation C#)
Chaque classe ou struct hérite implicitement de la classe <xref:System.Object> en C\#.  Par conséquent, chaque objet en C\# obtient la méthode <xref:System.Object.ToString%2A>, qui retourne une représentation sous forme de chaîne de cet objet.  Par exemple, toutes les variables de type `int` ont une méthode `ToString` qui leur permet de retourner leur contenu sous la forme d'une chaîne :  
  
 [!code-cs[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/how-to-override-the-tost_1.cs)]  
  
 Lorsque vous créez une classe ou une structure personnalisée, vous devez substituer la méthode <xref:System.Object.ToString%2A> afin de fournir des informations sur votre type au code client.  
  
 Pour plus d'informations sur l'utilisation de chaînes de format et d'autres types de mise en forme personnalisée avec la méthode d' `ToString` , consultez [Mise en forme des types](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md).  
  
> [!IMPORTANT]
>  Lors du choix des informations à fournir via cette méthode, demandez\-vous si votre classe ou structure risque d'être utilisée par un code non fiable.  Veillez à vous assurer que vous ne fournissez aucune information qui pourrait être exploitée par un code malveillant.  
  
### Pour substituer la méthode ToString dans votre classe ou struct  
  
1.  Déclarez une méthode `ToString` avec les modificateurs et le type de retour suivants :  
  
    ```c#  
    public override string ToString(){}  
    ```  
  
2.  Implémentez la méthode de telle sorte qu'elle retourne une chaîne.  
  
     L'exemple suivant retourne non seulement le nom de la classe en plus des données spécifiques à une instance particulière de la classe.  
  
     [!code-cs[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/how-to-override-the-tost_2.cs)]  
  
     Vous pouvez tester la méthode `ToString` comme indiqué dans l'exemple de code suivant :  
  
     [!code-cs[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/how-to-override-the-tost_3.cs)]  
  
## Voir aussi  
 <xref:System.IFormattable>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Chaînes](../../../csharp/programming-guide/strings/index.md)   
 [chaîne](../../../csharp/language-reference/keywords/string.md)   
 [new](../../../csharp/language-reference/keywords/new.md)   
 [override](../../../csharp/language-reference/keywords/override.md)   
 [virtuels](../../../csharp/language-reference/keywords/virtual.md)   
 [Mise en forme des types](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md)