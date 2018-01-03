---
title: /optioncompare
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 62a9a4bf3428f3ee731e7ecc63be51dbf3076ee4
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="optioncompare"></a>/optioncompare
Spécifie la façon dont sont effectuées les comparaisons de chaînes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez spécifier `/optioncompare` dans un des deux formes : `/optioncompare:binary` pour utiliser des comparaisons de chaînes binaires et `/optioncompare:text` pour utiliser des comparaisons de chaînes de texte. Par défaut, le compilateur utilise `/optioncompare:binary`.  
  
 Dans Microsoft Windows, la page de codes utilisée détermine l’ordre de tri binaire. Un ordre de tri binaire standard est la suivante :  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Les comparaisons de chaînes de texte sont basées sur un ordre de tri de texte respectant la casse déterminé par les paramètres régionaux de votre système. Un ordre de tri de texte par défaut est la suivante :  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a>Pour définir /optioncompare dans l’IDE de Visual Studio  
  
1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet**, cliquez sur **Propriétés**.   
  
2.  Cliquez sur l’onglet **Compiler**.  
  
3.  Modifiez la valeur dans la **Option Compare** boîte.  
  
### <a name="to-set-optioncompare-programmatically"></a>Pour définir /optioncompare par programmation  
  
-   Consultez [Option Compare, instruction](../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `ProjFile.vb` et utilise des comparaisons de chaînes binaires.  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Compare (instruction)](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
