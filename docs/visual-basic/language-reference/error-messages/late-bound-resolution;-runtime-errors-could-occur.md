---
title: "Late bound resolution; runtime errors could occur | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc42017"
  - "BC42017"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42017"
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Late bound resolution; runtime errors could occur
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Un objet est assigné à une variable déclarée comment étant du [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Lorsque vous déclarez une variable comme `Object`, le compilateur doit exécuter une *liaison tardive* qui provoque des opérations supplémentaires au moment de l'exécution.  Il expose également votre application à d'éventuelles erreurs d'exécution.  Par exemple, si vous assignez <xref:System.Windows.Forms.Form> à la variable `Object`, puis vous essayez d'accéder à la propriété <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName>, le runtime lève une exception <xref:System.MemberAccessException> car la classe <xref:System.Windows.Forms.Form> n'expose pas de propriété `NameTable`.  
  
 Si vous déclarez la variable comme étant d'un type spécifique, le compilateur peut exécuter une *liaison anticipée* au moment de la compilation.  Cela entraîne des performances améliorées, un accès contrôlé aux membres du type spécifique et une meilleure lisibilité de votre code.  
  
 Par défaut, ce message est un avertissement.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC42017  
  
### Pour corriger cette erreur  
  
-   Si possible, déclarez la variable comme étant d'un type spécifique.  
  
## Voir aussi  
 [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)   
 [Object Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)