---
title: "Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class | Microsoft Docs"
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
  - "vbc30310"
  - "bc30310"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30310"
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

La classe `System.MarshalByRefObject` active des applications qui prennent en charge l'accès distant à des objets au\-delà des limites de domaine d'application.  Les types doivent hériter de la classe `MarshalByRejectObject` lorsque le type est utilisé au\-delà des limites de domaine d'application.  L'état de l'objet ne doit pas être copié car les membres de l'objet ne peuvent pas être utilisés en dehors du domaine d'application dans lequel ils ont été créés.  
  
 **ID d'erreur :** BC30310  
  
### Pour corriger cette erreur  
  
1.  Vérifiez la référence afin de vous assurer que le membre auquel il est fait référence est valide.  
  
2.  Qualifiez de manière explicite le membre à l'aide du mot clé `Me`.  
  
## Voir aussi  
 <xref:System.MarshalByRefObject>   
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)