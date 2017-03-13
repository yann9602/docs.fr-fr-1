---
title: "Attribute List (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "attribute list"
  - "attributes [Visual Basic], applying"
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Attribute List (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie les attributs à appliquer à un élément de programmation déclaré.  Les attributs multiples sont séparés par des virgules.  La syntaxe pour un attribut est la suivante.  
  
## Syntaxe  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## Composants  
 `attributemodifier`  
 Requis pour les attributs appliqués au début d'un fichier source.  Peut être [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) ou [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).  
  
 `attributename`  
 Obligatoire.  Nom de l'attribut.  
  
 `attributearguments`  
 Facultatif.  Liste d'arguments de position pour cet attribut.  Les arguments multiples sont séparés par des virgules.  
  
 `attributeinitializer`  
 Facultatif.  Liste d'initialiseurs de variable ou de propriété pour cet attribut.  Les initialiseurs multiples sont séparés par des virgules.  
  
## Notes  
 Vous pouvez appliquer un ou plusieurs attributs à quasiment n'importe quel élément de programmation \(types, procédures, propriétés, etc.\).  Les attributs apparaissent dans les métadonnées de votre assembly ; ils peuvent vous aider à annoter votre code ou à spécifier comment utiliser un élément de programmation particulier.  Vous pouvez appliquer des attributs définis par Visual Basic et le .NET Framework et vous pouvez définir vos propres attributs.  
  
 Pour plus d'informations sur le moment où des attributs doivent être utilisés, consultez [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md) .  Pour plus d'informations sur les noms d'attributs, consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## Règles  
  
-   **Positionnement.** Vous pouvez appliquer des attributs à la plupart des éléments de programmation déclarés.  Pour appliquer un ou plusieurs attributs, placez un *bloc d'attributs* au début de la déclaration d'élément.  Chaque entrée dans la liste d'attributs spécifie un attribut que vous souhaitez appliquer, ainsi que le modificateur et les arguments que vous utilisez pour cet appel de l'attribut.  
  
-   **Signes "inférieur à" et "supérieur à".** Si vous fournissez une liste d'attributs, vous devez la placer entre des signes "inférieur à" et "supérieur à" \("`<`" et "`>`"\).  
  
-   **Partie de la déclaration.** L'attribut doit faire partie de la déclaration d'élément, et non d'une instruction séparée.  Vous pouvez utiliser la séquence de continuation de ligne \(" `_`"\) pour étendre l'instruction de déclaration sur plusieurs lignes de code source.  
  
-   **Modificateurs.** Un modificateur d'attribut \(`Assembly` ou `Module`\) est requis sur chaque attribut appliqué à un élément de programmation au début d'un fichier source.  Les modificateurs d'attribut ne sont pas autorisés sur des attributs appliqués aux éléments qui ne sont pas au début d'un fichier source.  
  
-   **Arguments.** Tous les arguments positionnels d'un attribut doivent précéder n'importe quel initialiseur de propriété ou de variable.  
  
## Exemple  
 L'exemple suivant applique l'attribut <xref:System.Runtime.InteropServices.DllImportAttribute> à une définition squelette d'une procédure `Function`.  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> indique que la procédure attribuée représente un point d'entrée dans une bibliothèque de liens dynamiques \(DLL\) non managée.  L'attribut fournit le nom de DLL comme argument positionnel et l'autre information comme initialiseurs de variable.  
  
## Voir aussi  
 [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)   
 [Module \<keyword\>](../../../visual-basic/language-reference/modifiers/module-keyword.md)   
 [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [Procédure : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)