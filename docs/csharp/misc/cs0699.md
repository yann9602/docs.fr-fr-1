---
title: "Erreur du compilateur CS0699 | Microsoft Docs"
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
  - "CS0699"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0699"
ms.assetid: 1dff310b-6b8d-46b4-a649-bbf23282ff1f
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0699
'generic' ne définit pas le paramètre de type 'identifier'  
  
 Un paramètre de type a été utilisé dans une définition générique introuvable dans la liste de déclaration des paramètres de type pour ce générique. Cela peut arriver si le nom utilisé pour le paramètre de type est incohérent.  
  
 L’exemple suivant génère l’erreur CS0699 :  
  
```  
// CS0699.cs class C<T> where U : I   // CS0699 – U is not a valid type parameter { }  
```