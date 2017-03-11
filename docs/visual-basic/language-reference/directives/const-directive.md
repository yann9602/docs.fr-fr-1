---
title: "#Const Directive | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.#Const"
  - "#vb.Const"
  - "#Const"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "#Const directive"
  - "conditional compilation, directives"
  - "Const directive (#Const)"
  - "Visual Basic compiler, compiler directives"
  - "constants, Const directive"
  - "constants, declaring"
  - "Const statement [Visual Basic], directive (#Const)"
  - "declaring constants, #const directive"
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# #Const Directive
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Définit les constantes de compilation conditionnelle de Visual Basic.  
  
## Syntaxe  
  
```  
#Const constname = expression  
```  
  
## Composants  
 `constname`  
 Obligatoire.  Nom de la constante en cours de définition.  
  
 `expression`  
 Obligatoire.  Caractère littéral, autre constante de compilation conditionnelle, ou toute combinaison qui comprend tout ou partie des opérateurs arithmétiques ou logiques à l'exception de `Is`.  
  
## Notes  
 Les constantes de compilation conditionnelle sont toujours privées, c'est\-à\-dire qu'elles appartiennent au fichier dans lequel elles apparaissent.  Vous ne pouvez pas créer de constantes de compilation publiques à l'aide de la directive `#Const` ; vous ne pouvez les créer que dans l'interface utilisateur ou à l'aide de l'option `/define` du compilateur.  
  
 Vous ne pouvez utiliser que des constantes de compilation conditionnelle et des littéraux dans `expression`.  L'utilisation d'une constante standard définie avec `Const` génère une erreur.  À l'inverse, vous ne pouvez utiliser des constantes définies avec le mot clé `#Const` que pour la compilation conditionnelle.  Les constantes peuvent également être non définies. Dans ce cas, elles ont la valeur `Nothing`.  
  
## Exemple  
 Cet exemple utilise la directive `#Const`.  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/visualbasic/const-directive_1.vb)]  
  
## Voir aussi  
 [\/define](../../../visual-basic/reference/command-line-compiler/define.md)   
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)