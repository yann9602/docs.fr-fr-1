---
title: Valeurs de retour de Main() (Guide de programmation C#) | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
caps.latest.revision: 20
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
ms.openlocfilehash: 846c52b7d5429a23f354dd6a732ddb62563a55bf
ms.lasthandoff: 03/13/2017

---
# <a name="main-return-values-c-programming-guide"></a>Valeurs de retour de Main() (Guide de programmation C#)
La méthode `Main` peut retourner `void` :  
  
 [!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]  
  
 Elle peut également retourner un `int` :  
  
 [!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]  
  
 Si la valeur de retour de `Main` n’est pas utilisée, retourner `void` permet d’avoir un code un peu plus simple. Cependant, retourner un entier permet au programme de communiquer des informations d’état à d’autres programmes ou scripts qui appellent le fichier exécutable. L’exemple suivant montre comment accéder à la valeur de retour de `Main`.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, un fichier de commandes est utilisé pour exécuter un programme et tester la valeur de retour de la fonction `Main`. Quand un programme est exécuté dans Windows, toute valeur retournée par la fonction `Main` est stockée dans une variable d’environnement appelée `ERRORLEVEL`. Un fichier de commandes peut déterminer le résultat de l’exécution en consultant la variable `ERRORLEVEL`. En règle générale, une valeur de retour de zéro indique la réussite de l’exécution. L’exemple suivant est un programme simple qui retourne zéro depuis la fonction `Main`. La valeur zéro indique que le programme a été exécuté correctement. Enregistrez le programme sous le nom MainReturnValTest.cs.  
  
 [!code-cs[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]  
  
## <a name="example"></a>Exemple  
 Comme cet exemple utilise un fichier de commandes, il est préférable de compiler le code à partir d’une invite de commandes. Suivez les instructions de [Guide pratique pour définir des variables d’environnement pour la ligne de commande Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) pour permettre des générations en ligne de commande ou utilisez l’invite de commandes de Visual Studio, disponible à partir du menu **Démarrer** sous **Visual Studio Tools**. À partir de l’invite de commandes, accédez au dossier où vous avez enregistré le programme. La commande suivante compile MainReturnValTest.cs et produit le fichier exécutable MainReturnValTest.exe.  
  
 `csc MainReturnValTest.cs`  
  
 Ensuite, créez un fichier de commandes pour exécuter MainReturnValTest.exe et afficher le résultat. Collez le code suivant dans un fichier texte et enregistrez-le sous le nom `test.bat` dans le dossier qui contient MainReturnValTest.cs et MainReturnValTest.exe. Exécutez le fichier de commandes en tapant `test` à l’invite de commandes.  
  
 Comme le code retourne zéro, le fichier de commandes indique la réussite. Cependant, si vous modifiez MainReturnValTest.cs pour qu’il retourne une valeur différente de zéro puis que vous recompilez le programme, l’exécution suivante du fichier de commandes indiquera un échec.  
  
```  
rem test.bat  
@echo off  
MainReturnValTest  
@if "%ERRORLEVEL%" == "0" goto good  
  
:fail  
    echo Execution Failed  
    echo return value = %ERRORLEVEL%  
    goto end  
  
:good  
    echo Execution succeeded  
    echo Return value = %ERRORLEVEL%  
    goto end  
  
:end  
```  
  
## <a name="sample-output"></a>Résultat de l'exemple  
 `Execution succeeded`  
  
 `Return value = 0`  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Main() et arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/index.md)   
 [Guide pratique pour afficher les arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [Guide pratique pour accéder à des arguments de ligne de commande à l’aide de foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
