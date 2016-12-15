---
title: "Mid Statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.MidB"
  - "vb.Mid"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "substrings, Mid statement"
  - "strings [Visual Basic], substrings"
  - "Mid statement"
  - "strings [Visual Basic], replacing"
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Mid Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Remplace un nombre spécifié de caractères d'une variable `String` par les caractères d'une autre chaîne.  
  
## Syntaxe  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## Composants  
 `Target`  
 Obligatoire.  Nom de la variable `String` à modifier.  
  
 `Start`  
 Obligatoire.  Expression `Integer`.  Position de caractère dans `Target` où le remplacement de texte commence.  `Start` utilise un index de base 1.  
  
 `Length`  
 Facultatif.  Expression `Integer`.  Nombre de caractères à remplacer.  Si cette valeur est omise, `String` est utilisé dans son intégralité.  
  
 `StringExpression`  
 Obligatoire.  Expression `String` qui remplace une partie de `Target`.  
  
## Exceptions  
  
|Type d'exception|Condition|  
|----------------------|---------------|  
|<xref:System.ArgumentException>|`Start` \<\= 0 ou `Length` \< 0.|  
  
## Notes  
 Le nombre de caractères remplacé est toujours inférieur ou égal au nombre de caractères dans `Target`.  
  
 Visual Basic possède la fonction <xref:Microsoft.VisualBasic.Strings.Mid%2A> et l'instruction `Mid`.  Ces éléments fonctionnent à la fois sur un nombre spécifié de caractères dans une chaîne, mais la fonction `Mid` retourne les caractères pendant que l'instruction `Mid` remplace les caractères.  Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
>  Dans les précédentes versions de Visual Basic, l'instruction `MidB` remplace une sous\-chaîne en octets, plutôt que des caractères.  Son rôle est d'abord de convertir des chaînes en applications à jeu de caractères codés sur deux octets \(DBCS, Double\-Byte Character Set\).  Toutes les chaînes Visual Basic sont en Unicode, et la fonction `MidB` n'est plus prise en charge.  
  
## Exemple  
 L'exemple suivant utilise l'instruction `Mid` pour remplacer un nombre spécifié de caractères dans une variable chaîne par les caractères d'une autre chaîne.  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## Configuration requise  
 **Espace de noms :** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Module :** `Strings`  
  
 **Assembly :** [!INCLUDE[vbprvbruntime](../../../visual-basic/language-reference/objects/includes/vbprvbruntime_md.md)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>   
 [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md)   
 [Introduction to Strings in Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)