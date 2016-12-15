---
title: "Type &#39;&lt;typename&gt;&#39; is not defined | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30002"
  - "bc30002"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30002"
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Type &#39;&lt;typename&gt;&#39; is not defined
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'instruction a fait référence à un type qui n'a pas été défini.  Vous pouvez définir un type dans une instruction de déclaration, telle que `Enum`, `Structure`, `Class` ou `Interface`.  
  
 **ID d'erreur :** BC30002  
  
### Pour corriger cette erreur  
  
-   Vérifiez que la définition de type et sa référence utilisent toutes les deux la même orthographe.  
  
-   Vérifiez que la définition de type est accessible à la référence.  Par exemple, si le type se trouve dans un autre module et a été déclaré `Private`, déplacez la définition de type vers le module de référence ou déclarez\-le `Public`.  
  
-   Vérifiez que l'espace de noms du type n'est pas redéfini au sein de votre projet.  Si tel est le cas, utilisez le mot clé `Global` pour qualifier intégralement le nom du type.  Par exemple, si un projet définit un espace de noms nommé `System`, il n'est pas possible d'accéder au type <xref:System.Object?displayProperty=fullName> à moins que celui\-ci ne soit entièrement qualifié avec le mot clé `Global` : `Global.System.Object`.  
  
-   Si le type est défini, mais que la bibliothèque d'objets ou de types dans laquelle il est défini n'est pas inscrite en [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], cliquez sur **Ajouter une référence** dans le menu **Projet**, puis sélectionnez la bibliothèque d'objets ou de types appropriée.  
  
-   Vérifiez que le type se trouve dans un assembly qui fait partie du profil .NET Framework ciblé.  Pour plus d'informations, consultez [Troubleshooting .NET Framework Targeting Errors](/visual-studio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## Voir aussi  
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Gestion des références dans un projet](/visual-studio/ide/managing-references-in-a-project)