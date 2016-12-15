---
title: "XML entity references are not supported | Microsoft Docs"
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
  - "vbc31180"
  - "bc31180"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31180"
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML entity references are not supported
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une référence d'entité \(par exemple, `©`\) qui n'est pas définie dans la spécification XML 1.0 est incluse en tant que valeur pour un littéral XML.  Seules les références d'entité XML `&`, `"`, `<`, `>` et `'` sont prises en charge dans les littéraux XML.  
  
 **ID d'erreur :** BC31180  
  
### Pour corriger cette erreur  
  
-   Supprimez la référence d'entité non prise en charge.  
  
## Voir aussi  
 [XML Literals and the XML 1.0 Specification](../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)