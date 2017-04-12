---
title: Espaces de noms dans Visual Basic | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.global
dev_langs:
- VB
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names, avoiding conflicts
- naming conflicts, namespaces
- namespaces, assemblies
- Visual Basic code, namespaces
- fully qualified names
- naming conventions, naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fe94e65ddbb4ebd2f7d26e8750a0a7ef5d3153af
ms.lasthandoff: 03/13/2017

---
# <a name="namespaces-in-visual-basic"></a>Espaces de noms dans Visual Basic
Les espaces de noms permettent d’organiser les objets définis dans un assembly. Les assemblys peuvent contenir plusieurs espaces de noms, qui peuvent à leur tour contenir d’autres espaces de noms. Les espaces de noms permettent d’éviter les ambiguïtés et de simplifier les références quand de grands groupes d’objets, tels que des bibliothèques de classes, sont utilisés.  
  
 Par exemple, le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] définit la <xref:System.Windows.Forms.ListBox>classe dans le <xref:System.Windows.Forms?displayProperty=fullName>espace de noms.</xref:System.Windows.Forms?displayProperty=fullName> </xref:System.Windows.Forms.ListBox> Le fragment de code suivant montre comment déclarer une variable en utilisant le nom qualifié complet de cette classe :  
  
 [!code-vb[VbVbalrApplication n °&6;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## <a name="avoiding-name-collisions"></a>Éviter les collisions de noms  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]espaces de noms de résoudre le problème parfois appelé *contre la pollution de l’espace de noms*, dans lequel le développeur d’une bibliothèque de classes est entravé par l’utilisation de noms similaires dans une autre bibliothèque. Ces conflits avec des éléments existants sont également connus sous le terme de *collisions de noms*.  
  
 Par exemple, si vous créez une classe nommée `ListBox`, vous pouvez l’utiliser dans votre projet sans qualification. Toutefois, si vous souhaitez utiliser le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.Windows.Forms.ListBox>classe dans le même projet, vous devez utiliser une référence qualifiée complète pour rendre la référence unique.</xref:System.Windows.Forms.ListBox> Si la référence n’est pas unique, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] génère une erreur indiquant que le nom est ambigu. L’exemple de code suivant montre comment déclarer ces objets :  
  
 [!code-vb[VbVbalrApplication&#7;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 L’illustration ci-dessous montre deux hiérarchies d’espaces de noms, chacune contenant un objet nommé `ListBox`.  
  
 ![Hiérarchie de Namespace](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")  
  
 Par défaut, chaque fichier exécutable que vous créez à l’aide de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] contient un espace de noms portant le même nom que votre projet. Par exemple, si vous définissez un objet dans un projet nommé `ListBoxProject`, le fichier exécutable, ListBoxProject.exe, contient un espace de noms appelé `ListBoxProject`.  
  
 Plusieurs assemblys peuvent utiliser le même espace de noms. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] les traite alors comme un ensemble unique de noms. Par exemple, vous pouvez définir des classes pour un espace de noms appelé `SomeNameSpace` dans un assembly nommé `Assemb1`, et définir des classes supplémentaires pour le même espace de noms d’un assembly nommé `Assemb2`.  
  
## <a name="fully-qualified-names"></a>Noms qualifiés complets  
 Les noms qualifiés complets sont des références d’objet dont le préfixe est le nom de l’espace de noms dans lequel l’objet est défini. Vous pouvez utiliser les objets définis dans d’autres projets si vous créez une référence à la classe (en choisissant **Ajouter une référence** dans le menu **Projet** ), puis utiliser le nom qualifié complet de l’objet dans votre code. Le fragment de code suivant montre comment utiliser le nom qualifié complet d’un objet provenant de l’espace de noms d’un autre projet :  
  
 [!code-vb[VbVbalrApplication n °&8;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 Les noms qualifiés complets empêchent les conflits de nommage, car ils permettent au compilateur d’identifier l’objet utilisé. Toutefois, les noms peuvent devenir longs et compliqués. Pour contourner ce problème, utilisez l’instruction `Imports` pour définir un *alias*, qui est un nom abrégé utilisable à la place d’un nom qualifié complet. L’exemple de code ci-dessous crée les alias de deux noms qualifiés complets, puis utilise ces alias pour définir deux objets.  
  
 [!code-vb[VbVbalrApplication&#9;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication&#10;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 Si vous utilisez l’instruction `Imports` sans alias, vous pouvez vous servir de tous les noms de l’espace de noms sans qualification, à condition qu’ils soient uniques au sein du projet. Si votre projet contient des instructions `Imports` pour les espaces de noms contenant des éléments de même nom, vous devez fournir un nom qualifié complet quand vous l’utilisez. Imaginons, par exemple, que votre projet contient les deux instructions `Imports` suivantes :  
  
 [!code-vb[VbVbalrApplication&#11;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 Si vous essayez d’utiliser `Class1` sans fournir son nom qualifié complet, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] génère une erreur indiquant que le nom `Class1` est ambigu.  
  
## <a name="namespace-level-statements"></a>Instructions au niveau de l’espace de noms  
 Dans un espace de noms, vous pouvez définir des éléments tels que des modules, des interfaces, des classes, des délégués, des énumérations, des structures et d’autres espaces de noms. Vous ne pouvez pas définir d’éléments tels que des propriétés, des procédures, des variables et des événements au niveau de l’espace de noms. Ces éléments doivent être déclarés dans des conteneurs tels que des modules, des structures ou des classes.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Mot clé Global dans les noms qualifiés complets  
 Si vous avez défini une hiérarchie imbriquée d’espaces de noms, le code à l’intérieur de cette hiérarchie peut ne pas d’accéder à la <xref:System?displayProperty=fullName>espace de noms du .NET Framework.</xref:System?displayProperty=fullName> L’exemple suivant illustre une hiérarchie dans laquelle le `SpecialSpace.System` espace de noms bloque l’accès à <xref:System?displayProperty=fullName>.</xref:System?displayProperty=fullName>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 Par conséquent, le compilateur Visual Basic ne peut pas résoudre correctement la référence à <xref:System.Int32?displayProperty=fullName>, car `SpecialSpace.System` ne définit pas `Int32`.</xref:System.Int32?displayProperty=fullName> Vous pouvez utiliser le mot clé `Global` pour démarrer la chaîne de qualification au niveau le plus externe de la bibliothèque de classes du .NET Framework. Cela vous permet de spécifier le <xref:System?displayProperty=fullName>espace de noms ou un autre espace de noms dans la bibliothèque de classes.</xref:System?displayProperty=fullName> L'exemple suivant illustre ce comportement.  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 Vous pouvez utiliser `Global` pour accéder à d’autres espaces de noms racine, tel que <xref:Microsoft.VisualBasic?displayProperty=fullName>et n’importe quel espace de noms associé à votre projet.</xref:Microsoft.VisualBasic?displayProperty=fullName>  
  
## <a name="global-keyword-in-namespace-statements"></a>Mot clé Global dans les instructions Namespace  
 Vous pouvez également utiliser le `Global` mot clé dans une [Namespace instruction](../../../visual-basic/language-reference/statements/namespace-statement.md). pour définir un espace de noms hors de l’espace de noms racine de votre projet.  
  
 Tous les espaces de noms dans votre projet sont basés sur l’espace de noms racine du projet.  Visual Studio définit le nom de votre projet comme espace de noms racine par défaut pour l’ensemble du code de votre projet. Par exemple, si votre projet est nommé `ConsoleApplication1`, ses éléments de programmation appartiennent à l’espace de noms `ConsoleApplication1`. Si vous déclarez `Namespace Magnetosphere`, les références à `Magnetosphere` dans le projet doivent accéder à `ConsoleApplication1.Magnetosphere`.  
  
 Les exemples suivants utilisent le mot clé `Global` pour déclarer un espace de noms hors de l’espace de noms racine du projet.  
  
 [!code-vb[VbVbalrApplication&#22;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 Dans une déclaration d’espace de noms, `Global` ne peut pas être imbriqué dans un autre espace de noms.  
  
 Vous pouvez utiliser la [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic) pour afficher et modifier les **racine Namespace** du projet.  Pour les nouveaux projets, l’ **espace de noms racine** correspond par défaut au nom du projet. Pour définir `Global` comme espace de noms de premier niveau, effacez l’entrée **Espace de noms racine** pour que la zone soit vide. Quand l’entrée **Espace de noms racine** est effacée, vous n’avez pas besoin de spécifier le mot clé `Global` dans les déclarations d’espace de noms.  
  
 Si une instruction `Namespace` déclare un nom qui est également un espace de noms dans le .NET Framework, l’espace de noms .NET Framework n’est plus disponible si le mot clé `Global` n’est pas utilisé dans un nom qualifié complet. Pour permettre l’accès à cet espace de noms .NET Framework sans utiliser le mot clé `Global` , ajoutez le mot clé `Global` dans l’instruction `Namespace` .  
  
 Dans l’exemple suivant, le mot clé `Global` est utilisé dans la déclaration d’espace de noms `System.Text` .  
  
 Si le `Global` mot clé n’était pas présent dans la déclaration d’espace de noms, <xref:System.Text.StringBuilder>n’est pas accessible sans spécifier `Global.System.Text.StringBuilder`.</xref:System.Text.StringBuilder> Pour un projet nommé `ConsoleApplication1`, les références à `System.Text` accèdent à `ConsoleApplication1.System.Text` si le mot clé `Global` n’est pas utilisé.  
  
 [!code-vb[VbVbalrApplication n °&21;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ListBox></xref:System.Windows.Forms.ListBox>   
 <xref:System.Windows.Forms?displayProperty=fullName></xref:System.Windows.Forms?displayProperty=fullName>   
 [Assemblys et le Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Comment : créer et utiliser des assemblys à l’aide de la ligne de commande](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)   
 [Références et l’instruction Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Instruction Imports (espace de noms et type .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Écriture de code dans les solutions Office](https://msdn.microsoft.com/library/bb608596)
