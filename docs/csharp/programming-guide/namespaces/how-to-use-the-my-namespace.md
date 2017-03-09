---
title: "Comment&#160;: utiliser l&#39;espace de noms My (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, accès à l'espace de noms My"
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# Comment&#160;: utiliser l&#39;espace de noms My (Guide de programmation C#)
L'espace de noms <xref:Microsoft.VisualBasic.MyServices> \(`My` en Visual Basic\) fournit un accès facile et intuitif à plusieurs classes .NET Framework, ce qui vous permet d'écrire un code qui interagit avec l'ordinateur, l'application, les paramètres, les ressources, etc.  Bien que conçu à l'origine pour être utilisé avec Visual Basic, l'espace de noms `MyServices` peut être utilisé dans les applications C\#.  
  
 Pour plus d'informations sur l'utilisation de l'espace de noms `MyServices` de Visual Basic, consultez [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## Ajout d'une référence  
 Avant de pouvoir utiliser les classes `MyServices` dans votre solution, vous devez ajouter une référence à la bibliothèque Visual Basic.  
  
#### Pour ajouter une référence dans la bibliothèque Visual Basic  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références**, puis cliquez sur **Ajouter une référence**.  
  
2.  Lorsque la boîte de dialogue **Références** apparaît, faites défiler la liste, puis sélectionnez Microsoft.VisualBasic.dll.  
  
     Vous pouvez également souhaiter inclure la ligne suivante dans la section `using` au démarrage de votre programme.  
  
     [!code-cs[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/csharp/Namespaces/Namespaces3.cs#18)]  
  
## Exemple  
 Cet exemple appelle plusieurs méthodes statiques contenues dans l'espace de noms `MyServices`.  Pour que ce code se compile, une référence à Microsoft.VisualBasic.DLL doit être ajoutée au projet.  
  
 [!code-cs[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/csharp/Namespaces/Namespaces3.cs#19)]  
  
 Toutes les classes de l'espace de noms `MyServices` ne peuvent pas être appelées à partir d'une application C\# : par exemple, la classe <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> n'est pas compatible.  Dans ce cas particulier, les méthodes statiques qui font partie de <xref:Microsoft.VisualBasic.FileIO.FileSystem>, également contenues dans VisualBasic.dll, peuvent être utilisées à la place.  Par exemple, voici comment utiliser une de ces méthodes pour dupliquer un répertoire :  
  
 [!code-cs[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/csharp/Namespaces/Namespaces3.cs#20)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Espaces de noms](../../../csharp/programming-guide/namespaces/index.md)   
 [Utilisation d'espaces de noms](../../../csharp/programming-guide/namespaces/using-namespaces.md)