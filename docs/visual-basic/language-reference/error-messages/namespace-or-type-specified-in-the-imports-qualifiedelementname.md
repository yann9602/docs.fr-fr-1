---
title: "Namespace or type specified in the Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found | Microsoft Docs"
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
  - "bc40056"
  - "vbc40056"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40056"
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Namespace or type specified in the Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'espace de noms ou le type spécifié dans les Imports '\<NomÉlémentQualifié\>' ne contient aucun membre public ou est introuvableVérifiez que l'espace de noms ou le type est défini et qu'il contient au moins un membre public.Vérifiez que le nom d'alias ne contient pas d'autres alias.  
  
 Une instruction `Imports` spécifie un élément conteneur qui soit est introuvable, soit ne définit pas de membres `Public`.  
  
 Un *élément conteneur* peut être un espace de noms, une classe, une structure, un module, une interface ou une énumération.  L'élément conteneur contient des membres, comme des variables, des procédures ou d'autres éléments conteneur.  
  
 L'objectif de l'importation est de permettre à votre code d'accéder à des membres espace de noms ou type sans devoir les qualifier.  Votre projet peut également avoir besoin d'ajouter une référence à l'espace de noms ou au type.  Pour plus d'informations, consultez « Importation d'éléments conteneurs » dans [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Si le compilateur ne trouve pas l'élément conteneur spécifié, il ne peut pas résoudre les références qui l'utilisent.  S'il trouve l'élément mais que celui\-ci n'expose pas de membres `Public`, aucune référence ne peut aboutir.  Dans l'un et l'autre cas, l'importation de l'élément n'a aucun sens.  
  
 Pensez que si vous importez un élément contenant et que vous lui assignez un alias d'importation, vous ne pouvez pas utiliser cet alias pour importer un autre élément.  Le code suivant génère une erreur de compilation.  
  
 `Imports`   `winfrm`   `= System.Windows.Forms`  
  
 `' The following statement is`   `INVALID`   `because it reuses an import alias.`  
  
 `Imports behav =`   `winfrm`  `.Design.Behavior`  
  
 **ID d'erreur :** BC40056  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que l'élément conteneur est accessible à partir de votre projet.  
  
2.  Vérifiez que la spécification de l'élément conteneur ne contient aucun alias d'importation provenant d'une autre importation.  
  
3.  Vérifiez que l'élément conteneur expose au moins un membre `Public`.  
  
## Voir aussi  
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)