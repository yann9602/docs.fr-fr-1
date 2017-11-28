---
title: Guide pratique pour afficher les arguments de ligne de commande (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6ae495eef227c6e4d9fb9ca0d4d0c031163fd52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Guide pratique pour afficher les arguments de ligne de commande (Guide de programmation C#)
Les arguments fournis à un fichier exécutable sur la ligne de commande sont accessibles à `Main` par l’intermédiaire d’un paramètre facultatif. Les arguments sont fournis sous la forme d’un tableau de chaînes. Chaque élément du tableau contient un argument. Les espaces blancs entre arguments sont supprimés. Par exemple, considérez ces appels de ligne de commande d’un fichier exécutable fictif :  
  
|Entrée sur la ligne de commande|Tableau de chaînes passé à Main|  
|----------------------------|-------------------------------------|  
|**executable.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executable.exe un deux**|"un"<br /><br /> "deux"|  
|**executable.exe "un deux" trois**|"un deux"<br /><br /> "trois"|  
  
> [!NOTE]
>  Quand vous exécutez une application dans Visual Studio, vous pouvez spécifier des arguments de ligne de commande dans la [page Déboguer du Concepteur de projets](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Exemple  
 Cet exemple affiche les arguments de ligne de commande passés à une application de ligne de commande. La sortie présentée concerne la première entrée du tableau ci-dessus.  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Génération à partir de la ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [Main() et arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Guide pratique pour accéder à des arguments de ligne de commande à l’aide de foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Valeurs de retour Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
