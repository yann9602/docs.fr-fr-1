---
title: "Error Statement | Microsoft Docs"
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
  - "vb.error"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Error statement, syntax"
  - "Error statement"
  - "Error keyword"
  - "run-time errors, codes"
  - "errors [Visual Basic], simulating"
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Error Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Simule l'occurrence d'une erreur.  
  
## Syntaxe  
  
```  
Error errornumber  
```  
  
## Composants  
 `errornumber`  
 Obligatoire.  Peut être tout numéro d'erreur valide.  
  
## Notes  
 L'instruction `Error` est prise en charge pour des raisons de compatibilité descendante.  Dans un nouveau code \(particulièrement, lors de la création d'objets\), utilisez la méthode `Raise` de l'objet `Err` pour générer des erreurs d'exécution.  
  
 Si `errornumber` est défini, l'instruction `Error` appelle le gestionnaire d'erreurs une fois que les valeurs par défaut suivantes ont été assignées aux propriétés de l'objet `Err` :  
  
|Propriété|Valeur|  
|---------------|------------|  
|`Number`|Valeur spécifiée comme un argument de l'instruction `Error`.  Peut être tout numéro d'erreur valide.|  
|`Source`|Nom du projet Visual Basic en cours.|  
|`Description`|Expression de chaîne correspondant à la valeur de retour de la fonction `Error` pour le `Number` spécifié, si cette chaîne existe.  Si la chaîne n'existe pas, `Description` contient une chaîne de longueur nulle \(""\).|  
|`HelpFile`|Le lecteur, le chemin d'accès et le nom de fichier complets du fichier d'aide Visual Basic approprié.|  
|`HelpContext`|L'ID de contexte du fichier d'aide Visual Basic approprié pour l'erreur correspondant à la propriété `Number`.|  
|`LastDLLError`|Zéro.|  
  
 Si aucun gestionnaire d'erreurs n'existe ou n'est activé, un message d'erreur est créé et affiché à partir des propriétés de l'objet `Err`.  
  
> [!NOTE]
>  Certaines applications hôtes Visual Basic ne peuvent pas créer d'objets.  Consultez la documentation de votre application hôte pour déterminer si cette dernière peut créer des classes et des objets.  
  
## Exemple  
 Cet exemple utilise l'instruction `Error` pour générer l'erreur numéro 11.  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## Configuration requise  
 **Espace de noms :** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly :** bibliothèque Runtime Visual Basic \(dans Microsoft.VisualBasic.dll\)  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>   
 <xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>   
 [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)   
 [Resume Statement](../../../visual-basic/language-reference/statements/resume-statement.md)   
 [Error Messages](../../../visual-basic/language-reference/error-messages/index.md)