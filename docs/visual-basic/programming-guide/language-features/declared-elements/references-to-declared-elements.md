---
title: "Références aux éléments déclarés (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9b3847164b4e577a9265a746b9329218b4af928b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="references-to-declared-elements-visual-basic"></a>Références aux éléments déclarés (Visual Basic)
Lorsque votre code fait référence à un élément déclaré, le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur correspond au nom de la référence à la déclaration appropriée de ce nom. Si plus d’un élément est déclaré avec le même nom, vous pouvez contrôler lequel de ces éléments doit être référencé par *éligible* son nom.  
  
 Le compilateur tente de correspondre à une référence de nom à une déclaration de nom avec la *plus petite portée*. Cela signifie qu’il commence par le code qui effectue la référence et parcourt niveaux successifs d’éléments conteneurs.  
  
 L’exemple suivant montre des références à deux variables portant le même nom. L’exemple déclare deux variables, chacune nommée `totalCount`, à différents niveaux de portée dans le module `container`. Lors de la procédure `showCount` affiche `totalCount` sans qualification, le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur résout la référence à la déclaration avec la plus petite portée, à savoir la déclaration locale à l’intérieur de `showCount`. Lorsqu’il qualifie `totalCount` avec le module conteneur `container`, le compilateur résout la référence à la déclaration avec une portée plus large.  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a>Qualifier un nom d’élément  
 Si vous souhaitez substituer ce processus de recherche et spécifier un nom déclaré dans une portée plus large, vous devez *qualifier* le nom de l’élément conteneur de la portée plus large. Dans certains cas, vous devrez peut-être également qualifier l’élément conteneur.  
  
 Qualifier un moyen de nom précèdent dans votre instruction source avec les informations qui identifient où l’élément cible est défini. Cette information est appelée un *chaîne de qualification*. Il peut inclure un ou plusieurs espaces de noms et un module, classe ou structure.  
  
 La chaîne de qualification sans ambiguïté doit spécifier que le module, classe ou structure qui contient l’élément cible. Le conteneur peut se trouver dans un autre élément conteneur, généralement un espace de noms. Vous devrez peut-être inclure plusieurs éléments conteneurs dans la chaîne de qualification.  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>Pour accéder à un élément déclaré en qualifiant son nom  
  
1.  Déterminer l’emplacement dans lequel l’élément a été défini. Il peut s’agir d’un espace de noms, ou même d’une hiérarchie d’espaces de noms. Dans l’espace de noms de niveau le plus bas, l’élément doit être contenu dans un module, classe ou structure.  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2.  Déterminer un chemin d’accès de qualification basé sur l’emplacement de l’élément cible. Démarrer avec l’espace de noms de niveau supérieur, passez à l’espace de noms de niveau le plus bas et se terminer par le module, classe ou structure qui contient l’élément cible. Chaque élément dans le chemin d’accès doit contenir l’élément qui le suit.  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3.  Préparer la chaîne de qualification de l’élément cible. Placez un point (`.`) après chaque élément dans le chemin d’accès. Votre application doit avoir accès à chaque élément dans votre chaîne de qualification.  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  Écrire l’expression ou une instruction d’assignation qui fait référence à l’élément cible de façon normale.  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  Faites précéder le nom de l’élément cible avec la chaîne de qualification. Le nom doit suivre immédiatement le point (`.`) qui suit le module, classe ou structure qui contient l’élément.  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  Le compilateur utilise la chaîne de qualification pour rechercher une déclaration claire et non équivoque à laquelle il peut correspondre à la référence d’élément cible.  
  
 Vous devrez peut-être également qualifier une référence de nom si votre application a accès à plusieurs éléments de programmation qui porte le même nom. Par exemple, le <xref:System.Windows.Forms> et <xref:System.Web.UI.WebControls> contiennent des espaces de noms à la fois un `Label` classe (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> et <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>). Si votre application utilise à la fois, ou si elle définit sa propre `Label` (classe), vous devez distinguer les différents `Label` objets. Inclure l’alias d’espace de noms ou d’importation dans la déclaration de variable. L’exemple suivant utilise l’alias d’importation.  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>Membres d’autres éléments conteneurs  
 Lorsque vous utilisez un membre non partagé d’une autre classe ou structure, vous devez tout d’abord qualifier le nom du membre avec une variable ou une expression qui pointe vers une instance de la classe ou structure. Dans l’exemple suivant, `demoClass` est une instance d’une classe nommée `class1`.  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 Vous ne pouvez pas utiliser le nom de la classe pour qualifier un membre qui n’est pas [partagé](../../../../visual-basic/language-reference/modifiers/shared.md). Vous devez d’abord créer une instance dans une variable objet (dans ce cas `demoClass`) et de le référencer par le nom de variable.  
  
 Si une classe ou une structure a un `Shared` membre, vous pouvez qualifier ce membre avec le nom de classe ou structure, ou avec une variable ou une expression qui pointe vers une instance.  
  
 Un module n’a pas d’instances séparées et tous ses membres sont `Shared` par défaut. Par conséquent, vous qualifiez un membre de module avec le nom du module.  
  
 L’exemple suivant montre des références qualifiées aux procédures de membre de module. L’exemple déclare deux `Sub` procédures, toutes deux nommées `perform`, dans différents modules d’un projet. Chacun d’eux peut être spécifiée sans qualification dans son propre module, mais doit être qualifiée si référencée ailleurs. Étant donné que la dernière référence dans `module3` ne qualifie pas `perform`, le compilateur ne peut pas résoudre cette référence.  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a>Références aux projets  
 Pour utiliser [Public](../../../../visual-basic/language-reference/modifiers/public.md) les éléments définis dans un autre projet, vous devez d’abord définir un *référence* à la bibliothèque d’assembly ou le type de ce projet. Pour définir une référence, cliquez sur **ajouter une référence** sur la **projet** menu, ou encore utiliser le [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) option du compilateur de ligne de commande.  
  
 Par exemple, vous pouvez utiliser le modèle d’objet XML de le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Si vous définissez une référence à la <xref:System.Xml> espace de noms, vous pouvez déclarer et utiliser une de ses classes, telles que <xref:System.Xml.XmlDocument>. L’exemple suivant utilise <xref:System.Xml.XmlDocument>.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>Importation d’éléments conteneurs  
 Vous pouvez utiliser la [Imports, instruction (.NET Namespace et Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) à *importer* les espaces de noms qui contiennent les modules ou classes que vous souhaitez utiliser. Cela vous permet de faire référence aux éléments définis dans un espace de noms importé sans qualifier complètement leurs noms. L’exemple suivant réécrit l’exemple précédent pour importer le <xref:System.Xml> espace de noms.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 En outre, le `Imports` instruction peut définir un *alias d’importation* pour chaque espace de noms importé. Cela peut rendre le code source plus court et plus facile à lire. L’exemple suivant réécrit l’exemple précédent pour utiliser `xD` en tant qu’alias pour la <xref:System.Xml> espace de noms.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 La `Imports` instruction ne rend pas les éléments d’autres projets disponibles à votre application. Autrement dit, il ne prend pas la place de la définition d’une référence. L’importation d’un espace de noms simplement supprime la nécessité de qualifier les noms définis dans cet espace de noms.  
  
 Vous pouvez également utiliser le `Imports` statement pour importer des modules, des classes, des structures et des énumérations. Vous pouvez ensuite utiliser les membres de ces éléments importés sans qualification. Toutefois, vous devez toujours qualifier les membres non partagés de classes et les structures avec une variable ou une expression qui correspond à une instance de la classe ou structure.  
  
## <a name="naming-guidelines"></a>Indications concernant l'attribution d'un nom  
 Lorsque vous définissez deux ou plusieurs éléments de programmation qui ont le même nom, un *ambiguïté de noms* peuvent entraîner lorsque le compilateur tente de résoudre une référence à ce nom. Si plusieurs définitions sont dans la portée, ou si aucune définition n’est dans la portée, la référence est résolue. Pour obtenir un exemple, consultez « Exemple de référence qualifiée » sur cette page d’aide.  
  
 Pour éviter toute ambiguïté, vous pouvez affecter des noms uniques de tous les éléments de. Ensuite, vous pouvez faire référence à n’importe quel élément sans devoir qualifier son nom avec un espace de noms, un module ou une classe. Vous réduisez également le risque de faire référence par erreur à l’élément incorrect.  
  
## <a name="shadowing"></a>Clichés instantanés  
 Lorsque deux éléments de programmation partagent le même nom, un d’eux peut masquer, ou *ombre*, autre. Un élément occulté n’est pas disponible pour la référence ; au lieu de cela, lorsque votre code utilise le nom de l’élément occulté, le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur résout vers l’élément d’occultation. Pour obtenir une explication plus détaillée avec des exemples, consultez [occultation dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Noms d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Caractéristiques d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)  
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Imports (instruction) (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [New (opérateur)](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Public](../../../../visual-basic/language-reference/modifiers/public.md)
