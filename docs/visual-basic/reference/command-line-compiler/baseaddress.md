---
title: "/baseaddress | Microsoft Docs"
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
  - "/baseaddress"
  - "baseaddress"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-baseaddress compiler option [Visual Basic]"
  - "/baseaddress compiler option [Visual Basic]"
  - "baseaddress compiler option [Visual Basic]"
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /baseaddress
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie une adresse de base par défaut lors de la création d'une DLL.  
  
## Syntaxe  
  
```  
/baseaddress:address  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`address`|Obligatoire.  Adresse de base de la DLL.  Cette adresse doit être spécifiée sous la forme d'un nombre hexadécimal.|  
  
## Notes  
 L'adresse de base par défaut d'une DLL est définie par le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].  
  
 Sachez que le dernier chiffre de cette adresse est arrondi.  Par exemple, si vous indiquez 0x11110001, ce nombre est arrondi à 0x11110000.  
  
 Pour terminer la procédure de signature d'une DLL, utilisez l'option `–R` de l'outil Strong Name \(Sn.exe\).  
  
 Cette option est ignorée si la cible n'est pas une DLL.  
  
||  
|-|  
|Pour définir \/baseaddress dans l'IDE de Visual Studio|  
|1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l'onglet **Compiler**.<br />3.  Cliquez sur **Avancé**.<br />4.  Modifiez la valeur dans la zone **Adresse de base de la DLL :**. **Note:**      La zone **Adresse de base de la DLL :** est en lecture seule sauf si la cible est une DLL.|  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)