---
title: "#<a name=\"line-c-reference\"></a>line (informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#line'
helpviewer_keywords: '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d2f42915d214349eebff40949482d7f603c0c2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="line-c-reference"></a>#line (référence C#)
`#line` vous permet de modifier le numéro de ligne du compilateur et (éventuellement) la sortie du nom de fichier pour les erreurs et les avertissements. Cet exemple montre comment signaler deux avertissements associés à des numéros de ligne. La directive `#line 200` affecte de force la valeur 200 au numéro de ligne (bien que la valeur par défaut soit #7) et jusqu’à la prochaine directive #line, le nom de fichier indiqué est « Special ». La directive par défaut #line rétablit la numérotation de lignes par défaut, qui compte le nombre de lignes qui ont été renumérotés par la directive précédente.  
  
```csharp
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;    // CS0168 on line 200  
        int j;    // CS0168 on line 201  
#line default  
        char c;   // CS0168 on line 9  
        float f;  // CS0168 on line 10  
#line hidden // numbering not affected  
        string s;   
        double d; // CS0168 on line 13  
    }  
}  
```  
  
## <a name="remarks"></a>Remarques  
 La directive `#line` peut être utilisée dans une étape intermédiaire automatisée du processus de génération. Par exemple, si des lignes ont été supprimées du fichier de code source d’origine, mais que vous voulez que le compilateur continue de générer une sortie sur la base de la numérotation de lignes d’origine du fichier, vous pouvez supprimer les lignes et simuler ensuite la numérotation de lignes d’origine avec `#line`.  
  
 La directive `#line hidden` masque les lignes successives du débogueur, de sorte que quand le développeur parcourt le code, les lignes situées entre une directive `#line hidden` et la directive `#line` suivante (en supposant qu’il ne s’agit pas d’une autre directive `#line hidden`) sont ignorées. Cette option peut aussi être utilisée pour permettre à ASP.NET de différencier le code défini par l’utilisateur du code généré par l’ordinateur. Même si ASP.NET est le principal utilisateur de cette fonctionnalité, il est probable que d’autres générateurs de code source pourront l’utiliser.  
  
 Une directive `#line hidden` n’affecte ni les noms de fichiers ni les numéros de lignes dans les rapports d’erreurs. Autrement dit, si une erreur se produit dans un bloc masqué, le compilateur indique le nom du fichier et le numéro de ligne actuels de l’erreur.  
  
 La directive `#line filename` spécifie le nom de fichier que vous souhaitez voir apparaître dans la sortie du compilateur. Par défaut, le nom réel du fichier de code source est utilisé. Le nom de fichier doit être entre guillemets doubles (" ") et doit être précédé d’un numéro de ligne.  
  
 Un fichier de code source peut contenir un nombre illimité de directives `#line`.  
  
## <a name="example-1"></a>Exemple 1  
 L’exemple suivant montre comment le débogueur ignore les lignes masquées dans le code. Quand vous exécutez l’exemple, celui-ci affiche trois lignes de texte. Or, quand vous définissez un point d’arrêt, comme dans l’exemple, et que vous appuyez sur F10 pour parcourir le code, vous pouvez remarquer que le débogueur ignore la ligne masquée. Vous remarquerez aussi que même si vous définissez un point d’arrêt au niveau de la ligne masquée, le débogueur continuera de l’ignorer.  
  
```csharp
// preprocessor_linehidden.cs  
using System;  
class MainClass   
{  
    static void Main()   
    {  
        Console.WriteLine("Normal line #1."); // Set break point here.  
#line hidden  
        Console.WriteLine("Hidden line.");  
#line default  
        Console.WriteLine("Normal line #2.");  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Directives de préprocesseur C#](../../../csharp/language-reference/preprocessor-directives/index.md)
