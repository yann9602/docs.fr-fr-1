---
title: "Implements Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Implements"
  - "Implements"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Implements statement, syntax"
  - "Implements statement"
  - "interface implementation, Implements statement"
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Implements Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie une ou plusieurs interfaces, ou des membres d'interface qui doivent être implémentés dans la définition de classe ou de structure dans laquelle elle apparaît.  
  
## Syntaxe  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## Composants  
 `interfacename`  
 Obligatoire.  Une interface dont les propriétés, procédures et événements doivent être implémentés par des membres correspondants dans la classe ou la structure.  
  
 `interfacemember`  
 Obligatoire.  Le membre d'une interface en cours d'implémentation.  
  
## Notes  
 Une interface est une collection de prototypes représentant les membres \(propriétés, procédures et événements\) que l'interface encapsule.  Les interfaces contiennent uniquement les déclarations des membres ; les classes et les structures implémentent ces membres.  Pour plus d'informations, consultez [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 L'instruction `Implements` doit suivre immédiatement l'instruction `Class` ou `Structure`.  
  
 Lorsque vous implémentez une interface, vous devez implémenter tous les membres déclarés dans l'interface.  L'omission d'un membre est considérée comme une erreur de syntaxe.  Pour implémenter un membre, vous spécifiez le mot clé [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) \(qui est distinct de l'instruction `Implements`\) lorsque vous déclarez le membre dans la classe ou la structure.  Pour plus d'informations, consultez [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Les classes peuvent utiliser des implémentations [Private](../../../visual-basic/language-reference/modifiers/private.md) des propriétés et procédures, mais ces membres sont uniquement accessibles par le casting d'une instance de la classe d'implémentation en une variable déclarée comme étant du type de l'interface.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de l'instruction `Implements` pour implémenter les membres d'une interface.  Il définit une interface nommée `ICustomerInfo` avec un événement, une propriété et une procédure.  La classe `customerInfo` implémente tous les membres définis dans l'interface.  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/implements-statement_1.vb)]  
  
 Notez que la classe `customerInfo` utilise l'instruction `Implements` sur une ligne de code source distincte pour indiquer que la classe implémente tous les membres de l'interface `ICustomerInfo`.  Ensuite, chaque membre de la classe utilise le mot clé `Implements` dans sa déclaration membre pour indiquer qu'il implémente ce membre d'interface.  
  
## Exemple  
 Les deux procédures suivantes illustrent l'utilisation de l'interface implémentée dans l'exemple précédent.  Pour tester l'implémentation, ajoutez ces deux procédures à votre projet et appelez la procédure `testImplements`.  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/implements-statement_2.vb)]  
  
## Voir aussi  
 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)