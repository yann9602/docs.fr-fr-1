---
title: "/optioncompare | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "/optioncompare"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "optioncompare compiler option [Visual Basic]"
  - "-optioncompare compiler option [Visual Basic]"
  - "/optioncompare compiler option [Visual Basic]"
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# /optioncompare
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie la façon dont sont effectuées les comparaisons de chaînes.  
  
## Syntaxe  
  
```  
/optioncompare:{binary | text}  
```  
  
## Notes  
 Vous pouvez spécifier `/optioncompare` sous l'une des deux formes suivantes : `/optioncompare:binary` pour utiliser des comparaisons de chaînes binaires et `/optioncompare:text` pour utiliser des comparaisons de chaînes de texte.  Par défaut, le compilateur utilise `/optioncompare:binary`.  
  
 Sous Microsoft Windows, la page de code en cours d'utilisation détermine le tri binaire.  L'exemple suivant montre un ordre de tri binaire classique.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Les comparaisons de chaîne de texte sont basées selon un tri ne respectant pas la casse du texte, déterminé par les paramètres régionaux de votre système.  L'exemple suivant montre un ordre de tri de texte classique.  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### Pour définir \/optioncompare dans l'IDE de Visual Studio  
  
1.  Sélectionnez un projet dans l'**Explorateur de solutions**.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Cliquez sur l'onglet **Compiler**.  
  
3.  Modifiez la valeur dans la zone **Option Compare**.  
  
### Pour définir \/optioncompare par programme  
  
-   Consultez [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## Exemple  
 Le code suivant compile P`rojFile.vb` et utilise des comparaisons de chaînes binaires :  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [\/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)