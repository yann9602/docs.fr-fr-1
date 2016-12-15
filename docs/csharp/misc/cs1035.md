---
title: "Erreur du compilateur&#160;CS1035 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1035"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1035"
ms.assetid: 99125500-62de-421a-b12b-04311c8947c3
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1035
Fin de fichier trouvée, '\*\/' attendu  
  
 Un délimiteur de commentaire ouvrant ne correspondait pas à un délimiteur fermant.  
  
 L’exemple suivant génère l’erreur CS1035 :  
  
```  
// CS1035.cs public class a { public static void Main() { } } /*   // CS1035, needs closing comment  
```