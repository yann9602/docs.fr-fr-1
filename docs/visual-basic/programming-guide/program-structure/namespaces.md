---
title: "Espaces de noms dans Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.global"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "assemblys [Visual Basic], espaces de noms"
  - "collisions de noms"
  - "Global (mot clé Visual Basic)"
  - "encombrement des espaces de noms"
  - "noms, éviter les conflits"
  - "conflits de noms, espaces de noms"
  - "espaces de noms, assemblys"
  - "code Visual Basic, espaces de noms"
  - "noms qualifiés complets"
  - "conventions de nommage, conflits de noms"
  - "espaces de noms"
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# Espaces de noms dans Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Les espaces de noms permettent d’organiser les objets définis dans un assembly. Les assemblys peuvent contenir plusieurs espaces de noms, qui peuvent à leur tour contenir d’autres espaces de noms. Les espaces de noms permettent d’éviter les ambiguïtés et de simplifier les références quand de grands groupes d’objets, tels que des bibliothèques de classes, sont utilisés.  
  
 Par exemple, [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] définit la classe <xref:System.Windows.Forms.ListBox> dans l’espace de noms <xref:System.Windows.Forms?displayProperty=fullName>. Le fragment de code suivant montre comment déclarer une variable en utilisant le nom qualifié complet de cette classe :  
  
 [!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## Éviter les collisions de noms  
 Les espaces de noms [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] permettent de résoudre un problème parfois appelé *pollution d’espace de noms*, où le développeur d’une bibliothèque de classes est gêné par l’utilisation de noms similaires dans une autre bibliothèque. Ces conflits avec des éléments existants sont également connus sous le terme de *collisions de noms*.  
  
 Par exemple, si vous créez une classe nommée `ListBox`, vous pouvez l’utiliser dans votre projet sans qualification. Toutefois, si vous souhaitez utiliser la classe <xref:System.Windows.Forms.ListBox> de [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] dans le même projet, vous devez utiliser une référence qualifiée complète pour rendre la référence unique. Si la référence n’est pas unique, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] génère une erreur indiquant que le nom est ambigu. L’exemple de code suivant montre comment déclarer ces objets :  
  
 [!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 L’illustration ci\-dessous montre deux hiérarchies d’espaces de noms, chacune contenant un objet nommé `ListBox`.  
  
 ![Hiérarchie d’espace de noms](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.png "vaNamespaceHierarchy")  
  
 Par défaut, chaque fichier exécutable que vous créez à l’aide de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] contient un espace de noms portant le même nom que votre projet. Par exemple, si vous définissez un objet dans un projet nommé `ListBoxProject`, le fichier exécutable, ListBoxProject.exe, contient un espace de noms appelé `ListBoxProject`.  
  
 Plusieurs assemblys peuvent utiliser le même espace de noms.[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] les traite alors comme un ensemble unique de noms. Par exemple, vous pouvez définir des classes pour un espace de noms appelé `SomeNameSpace` dans un assembly nommé `Assemb1`, et définir des classes supplémentaires pour le même espace de noms d’un assembly nommé `Assemb2`.  
  
## Noms qualifiés complets  
 Les noms qualifiés complets sont des références d’objet dont le préfixe est le nom de l’espace de noms dans lequel l’objet est défini. Vous pouvez utiliser les objets définis dans d’autres projets si vous créez une référence à la classe \(en choisissant **Ajouter une référence** dans le menu **Projet**\), puis utiliser le nom qualifié complet de l’objet dans votre code. Le fragment de code suivant montre comment utiliser le nom qualifié complet d’un objet provenant de l’espace de noms d’un autre projet :  
  
 [!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 Les noms qualifiés complets empêchent les conflits de nommage, car ils permettent au compilateur d’identifier l’objet utilisé. Toutefois, les noms peuvent devenir longs et compliqués. Pour contourner ce problème, utilisez l’instruction `Imports` pour définir un *alias*, qui est un nom abrégé utilisable à la place d’un nom qualifié complet. L’exemple de code ci\-dessous crée les alias de deux noms qualifiés complets, puis utilise ces alias pour définir deux objets.  
  
 [!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 Si vous utilisez l’instruction `Imports` sans alias, vous pouvez vous servir de tous les noms de l’espace de noms sans qualification, à condition qu’ils soient uniques au sein du projet. Si votre projet contient des instructions `Imports` pour les espaces de noms contenant des éléments de même nom, vous devez fournir un nom qualifié complet quand vous l’utilisez. Imaginons, par exemple, que votre projet contient les deux instructions `Imports` suivantes :  
  
 [!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 Si vous essayez d’utiliser `Class1` sans fournir son nom qualifié complet, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] génère une erreur indiquant que le nom `Class1` est ambigu.  
  
## Instructions au niveau de l’espace de noms  
 Dans un espace de noms, vous pouvez définir des éléments tels que des modules, des interfaces, des classes, des délégués, des énumérations, des structures et d’autres espaces de noms. Vous ne pouvez pas définir d’éléments tels que des propriétés, des procédures, des variables et des événements au niveau de l’espace de noms. Ces éléments doivent être déclarés dans des conteneurs tels que des modules, des structures ou des classes.  
  
## Mot clé Global dans les noms qualifiés complets  
 Si vous avez défini une hiérarchie imbriquée d’espaces de noms, le code à l’intérieur de cette hiérarchie peut ne pas avoir accès à l’espace de noms <xref:System?displayProperty=fullName> de .NET Framework. L’exemple suivant illustre une hiérarchie dans laquelle l’espace de noms `SpecialSpace.System` bloque l’accès à <xref:System?displayProperty=fullName>.  
  
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
  
 Le compilateur Visual Basic ne peut donc pas résoudre la référence à <xref:System.Int32?displayProperty=fullName>, car `SpecialSpace.System` ne définit pas `Int32`. Vous pouvez utiliser le mot clé `Global` pour démarrer la chaîne de qualification au niveau le plus externe de la bibliothèque de classes du .NET Framework. Cela vous permet de spécifier l’espace de noms <xref:System?displayProperty=fullName> ou un autre espace de noms dans la bibliothèque de classes. L'exemple suivant illustre ce comportement.  
  
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
  
 Utilisez aussi `Global` pour accéder à d’autres espaces de noms à la racine, tels que <xref:Microsoft.VisualBasic?displayProperty=fullName>, et aux espaces de noms associés à votre projet.  
  
## Mot clé Global dans les instructions Namespace  
 Vous pouvez également utiliser le mot clé `Global` dans une [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md) pour définir un espace de noms hors de l’espace de noms racine de votre projet.  
  
 Tous les espaces de noms dans votre projet sont basés sur l’espace de noms racine du projet.  Visual Studio définit le nom de votre projet comme espace de noms racine par défaut pour l’ensemble du code de votre projet. Par exemple, si votre projet est nommé `ConsoleApplication1`, ses éléments de programmation appartiennent à l’espace de noms `ConsoleApplication1`. Si vous déclarez `Namespace Magnetosphere`, les références à `Magnetosphere` dans le projet doivent accéder à `ConsoleApplication1.Magnetosphere`.  
  
 Les exemples suivants utilisent le mot clé `Global` pour déclarer un espace de noms hors de l’espace de noms racine du projet.  
  
 [!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 Dans une déclaration d’espace de noms, `Global` ne peut pas être imbriqué dans un autre espace de noms.  
  
 Vous pouvez utiliser la [Page Application, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic) pour afficher et modifier l’**espace de noms racine** du projet.  Pour les nouveaux projets, l’**espace de noms racine** correspond par défaut au nom du projet. Pour définir `Global` comme espace de noms de premier niveau, effacez l’entrée **Espace de noms racine** pour que la zone soit vide. Quand l’entrée **Espace de noms racine** est effacée, vous n’avez pas besoin de spécifier le mot clé `Global` dans les déclarations d’espace de noms.  
  
 Si une instruction `Namespace` déclare un nom qui est également un espace de noms dans le .NET Framework, l’espace de noms .NET Framework n’est plus disponible si le mot clé `Global` n’est pas utilisé dans un nom qualifié complet. Pour permettre l’accès à cet espace de noms .NET Framework sans utiliser le mot clé `Global`, ajoutez le mot clé `Global` dans l’instruction `Namespace`.  
  
 Dans l’exemple suivant, le mot clé `Global` est utilisé dans la déclaration d’espace de noms `System.Text`.  
  
 En l’absence du mot clé `Global` dans la déclaration d’espace de noms, l’accès à <xref:System.Text.StringBuilder> n’est pas possible sans spécifier `Global.System.Text.StringBuilder`. Pour un projet nommé `ConsoleApplication1`, les références à `System.Text` accèdent à `ConsoleApplication1.System.Text` si le mot clé `Global` n’est pas utilisé.  
  
 [!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## Voir aussi  
 <xref:System.Windows.Forms.ListBox>   
 <xref:System.Windows.Forms?displayProperty=fullName>   
 [Assemblys et le Global Assembly Cache](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Comment : créer et utiliser des assemblys à l’aide de la ligne de commande](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md)   
 [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Écriture de code dans les solutions Office](/office-dev/office-dev/writing-code-in-office-solutions)