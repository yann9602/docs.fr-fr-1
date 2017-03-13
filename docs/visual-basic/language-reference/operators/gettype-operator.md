---
title: "GetType Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.GetType"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "GetType operator"
  - "GetType keyword"
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# GetType Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Retourne un objet <xref:System.Type> pour le type spécifié.  L'objet <xref:System.Type> fournit des informations sur le type telles que ses propriétés, méthodes et événements.  
  
## Syntaxe  
  
```  
GetType(typename)  
```  
  
#### Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`typename`|Le nom du type pour lequel vous souhaitez des informations.|  
  
## Notes  
 L'opérateur `GetType` retourne l'objet <xref:System.Type> pour le `typename` spécifié.  Vous pouvez transférer le nom de tout type défini dans `typename`.  Notamment :  
  
-   Type de données Visual Basic, tel que `Boolean` ou `Date`.  
  
-   Toute classe, structure, module ou interface .NET Framework, telle que <xref:System.ArgumentException?displayProperty=fullName> ou <xref:System.Double?displayProperty=fullName>.  
  
-   Toute classe, structure, module ou interface définis par votre application.  
  
-   Tout tableau défini par votre application.  
  
-   Tout délégué défini par votre application.  
  
-   Toute énumération définie par Visual Basic, le .NET Framework ou votre application.  
  
 Si vous souhaitez obtenir l'objet de type d'une variable objet, utilisez la méthode <xref:System.Type.GetType%2A?displayProperty=fullName>.  
  
 L'opérateur `GetType` peut être utile dans les circonstances suivantes :  
  
-   Vous devez accéder aux métadonnées pour un type au moment de l'exécution.  L'objet <xref:System.Type> fournit des métadonnées telles que les membres de type et les informations de déploiement.  Vous en avez besoin, par exemple, pour refléter sur un assembly.  Pour plus d'informations, consultez <xref:System.Reflection?displayProperty=fullName>.  
  
-   Vous souhaitez comparer deux références d'objet pour voir s'ils font référence à des instances du même type.  Si tel est le cas, `GetType` retourne des références au même objet <xref:System.Type>.  
  
## Exemple  
 Voici quelques exemples d'opérateurs `GetType` employés.  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## Voir aussi  
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)