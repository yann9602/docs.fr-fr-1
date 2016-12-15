---
title: "Erreur du compilateur CS0249 | Microsoft Docs"
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
  - "CS0249"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0249"
ms.assetid: 8bc3572f-d949-4867-b119-6527fb924a4a
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0249
Ne remplacez pas object.Finalize. Au lieu de cela, fournissez un destructeur.  
  
 Utilisez la syntaxe du destructeur pour spécifier les instructions à exécuter quand votre objet est détruit.  
  
 Pour plus d’informations, consultez [Syntaxe de destructeur en C\# et C\+\+](http://msdn.microsoft.com/fr-fr/d7901491-7e89-4b6f-8270-0635aa6581b5).  
  
 L’exemple suivant génère l’erreur CS0249 :  
  
```  
// CS0249.cs class MyClass { protected override void Finalize()   // CS0249 // try the following line instead // ~MyClass() { } public static void Main() { } }  
```