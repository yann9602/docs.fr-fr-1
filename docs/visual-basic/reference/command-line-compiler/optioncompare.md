---
title: /optioncompare | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optioncompare
dev_langs:
- VB
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 53dee5bb50e20204725f031e3e04f5c37c5b3f96
ms.lasthandoff: 03/13/2017

---
# <a name="optioncompare"></a>/optioncompare
Spécifie la façon dont sont effectuées les comparaisons de chaînes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez spécifier `/optioncompare` dans une des deux formes : `/optioncompare:binary` pour utiliser des comparaisons de chaînes binaires et `/optioncompare:text` pour utiliser des comparaisons de chaînes de texte. Par défaut, le compilateur utilise `/optioncompare:binary`.  
  
 Dans Microsoft Windows, la page de codes utilisée détermine l’ordre de tri binaire. Un ordre de tri binaire standard est la suivante :  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Les comparaisons de chaînes de texte sont basées sur un ordre de tri de texte respectant la casse déterminé par les paramètres régionaux de votre système. Un ordre de tri de texte par défaut est la suivante :  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a>Pour définir /optioncompare dans l’IDE de Visual Studio  
  
1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Sur le **projet** menu, cliquez sur **propriétés**. Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Cliquez sur l’onglet **Compiler**.  
  
3.  Modifiez la valeur dans la **Option Compare** boîte.  
  
### <a name="to-set-optioncompare-programmatically"></a>Pour définir /optioncompare par programme  
  
-   Consultez la page [Option Compare, instruction](../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="example"></a>Exemple  
 Le code suivant compile P`rojFile.vb` et utilise des comparaisons de chaînes binaires.  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Compare (instruction)](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
