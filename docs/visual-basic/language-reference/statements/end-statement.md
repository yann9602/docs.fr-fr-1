---
title: "End Statement | Microsoft Docs"
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
  - "vb.End"
  - "End"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "execution, ending"
  - "files, closing"
  - "End keyword, End statements"
  - "programs, quitting"
  - "code, exiting"
  - "program termination"
  - "End statement"
  - "execution, stopping"
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# End Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Termine immédiatement l'exécution.  
  
## Syntaxe  
  
```  
End  
```  
  
## Notes  
 Vous pouvez placer l'instruction `End` n'importe où dans une procédure pour forcer l'arrêt de l'exécution de l'application entière.  `End` ferme tous fichiers ouverts avec une instruction `Open` et efface toutes les variables de l'application.  L'application se ferme lorsqu'il n'y a plus aucun programme contenant des références à ses objets et qu'aucun code n'est exécuté.  
  
> [!NOTE]
>  L'instruction `End` met immédiatement fin à l'exécution du code, sans appeler la méthode `Dispose` ou `Finalize` ou tout autre code Visual Basic.  Les références d'objet contenues dans d'autres programmes sont annulées.  Si une instruction `End` est présente dans un bloc `Try` ou `Catch`, le contrôle ne passe pas au bloc `Finally` correspondant.  
  
 L'instruction `Stop` interrompt l'exécution, mais contrairement à `End`, elle ne ferme pas les fichiers et n'efface pas les variables, sauf si elle est placée dans un fichier exécutable \(.exe\) compilé.  
  
 Étant donné que `End` met fin à votre application sans se préoccuper des ressources qui peuvent être ouvertes, vous devez essayer de la fermer correctement avant de l'utiliser.  Par exemple, si votre application contient des formulaires ouverts, vous devez les fermer avant que le contrôle atteigne l'instruction `End`.  
  
 Vous devez utiliser `End` avec parcimonie, et uniquement lorsque vous devez effectuer un arrêt immédiat.  Les méthodes d'arrêt normales d'une procédure \([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) et [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)\) permettent de fermer correctement la procédure, mais également le code appelant.  Par exemple, une application console conserve simplement `Return` de la procédure `Main`.  
  
> [!IMPORTANT]
>  L'instruction `End` appelle la méthode <xref:System.Environment.Exit%2A> de la classe <xref:System.Environment> dans l'espace de noms <xref:System>.  <xref:System.Environment.Exit%2A> nécessite l'autorisation `UnmanagedCode`.  Si vous ne possédez pas cette autorisation, une erreur <xref:System.Security.SecurityException> se produit.  
  
 Lorsqu'elle est suivie d'un mot clé supplémentaire, l'instruction [End \<keyword\> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) représente la fin de la définition de la procédure ou du bloc approprié.  Par exemple, `End Function` met fin à la définition d'une procédure `Function`.  
  
## Exemple  
 L'exemple ci\-dessous utilise l'instruction `End` pour mettre fin à l'exécution d'un code si l'utilisateur le demande.  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## Notes du développeur sur Smart Device  
 Cette instruction n'est pas prise en charge.  
  
## Voir aussi  
 <xref:System.Security.Permissions.SecurityPermissionFlag>   
 [Stop Statement](../../../visual-basic/language-reference/statements/stop-statement.md)   
 [End \<keyword\> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md)